cmake_minimum_required(VERSION 3.8)

set(CMAKE_TOOLCHAIN_FILE "common/intros/cmake/config-stm32f4discovery-gcc.cmake")
set(CMAKE_BUILD_TYPE     "Release")

project(test)

find_package(startup REQUIRED)
find_package(device  REQUIRED)
find_package(intros  REQUIRED)

add_executable(test
	src/main.c
)

target_include_directories(test
	PRIVATE
	include
)

target_link_libraries(test
	PRIVATE
	startup
	device::nosys
	intros::kernel
)

setup_target(test)
