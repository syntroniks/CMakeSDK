cmake_minimum_required (VERSION 3.12)

if(DEFINED ENV{SOS_SDK_PATH})
	set(SOS_SDK_PATH $ENV{SOS_SDK_PATH})
endif()

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
set(CMAKE_TOOLCHAIN_FILE ${CMAKE_MODULE_PATH}/sos-toolchain.cmake)
include(sos-sdk)

set(SOS_NAME sos)
project(CMakeSDK CXX C)

add_library(sdk INTERFACE)

target_sources(sdk
	INTERFACE
	${CMAKE_CURRENT_SOURCE_DIR}/cmake/sos-sdk.cmake
	)

if(SOS_IS_LINK)
	set(CMAKE_DEST cmake)
else()
	set(CMAKE_DEST ../cmake)
endif()

install(DIRECTORY cmake/ DESTINATION ${CMAKE_DEST})


