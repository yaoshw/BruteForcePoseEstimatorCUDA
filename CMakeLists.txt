cmake_minimum_required(VERSION 3.5)
project(Cudartographer)

set(CMAKE_CXX_STANDARD 14)
set(CUDA_NVCC_FLAGS ${CUDA_NVCC_FLAGS}  "-Xcompiler;-fPIC;")

find_package(CUDA QUIET REQUIRED)
add_definitions("-Wno-deprecated-gpu-targets")

include_directories(/home/yaoshw/software/eigen-3.4.0/install/include/eigen3)
#find_package(Eigen3 REQUIRED)
#include_directories(${EIGEN3_INCLUDE_DIR}) #需要把要使用的高版本的eigen放在前面，以防止后面的库首先找到依赖的低版本的eigen
#message(STATUS "Eigen found in ${EIGEN3_INCLUDE_DIR}")#有时EIGEN3_INCLUDE_DIRS不加S才能找到，区别在于上面的list语句
cuda_add_executable(Cudartographer main.cpp utils.cu)
target_link_libraries(Cudartographer ${CUDA_LIBRARIES})