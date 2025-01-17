# Copyright (c) 2016-2019 Memgraph Ltd. [https://memgraph.com]
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

cmake_minimum_required(VERSION 3.4)
project(mgclient VERSION 0.1)
include(CTest)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 14)
set(C_STANDARD_REQUIRED ON)
set(CXX_STANDARD_REQUIRED ON)

# Set default build type to 'Release'
if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release")
endif()
message(STATUS "CMake build type: ${CMAKE_BUILD_TYPE}")

# Set default instalation directory to '/usr'
if(CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
    # '/usr' is a special case, for more details see:
    # https://cmake.org/cmake/help/latest/module/GNUInstallDirs.html#special-cases
    set(CMAKE_INSTALL_PREFIX "/usr")
endif()

add_subdirectory(src)

if(BUILD_TESTING)
    add_subdirectory(tests)
endif()
