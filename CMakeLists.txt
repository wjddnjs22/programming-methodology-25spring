cmake_minimum_required(VERSION 3.14)
project(programming-methodology-25spring-3)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 테스트용 파일 추가
add_executable(test_calculator test_calculator.cpp Calculator.cpp)

# googletest 직접 추가한 경우
add_subdirectory(${CMAKE_SOURCE_DIR}/build/_deps/googletest-src)

# include 경로 추가
target_include_directories(test_calculator PRIVATE
    ${CMAKE_SOURCE_DIR}/build/_deps/googletest-src/googletest/include
    ${CMAKE_SOURCE_DIR}/build/_deps/googletest-src/googlemock/include
)

# gtest 라이브러리 연결
target_link_libraries(test_calculator gtest gtest_main)

# 테스트 등록 (ctest에서 사용할 수 있게)
enable_testing()
add_test(NAME CalculatorTest COMMAND test_calculator)
