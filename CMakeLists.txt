cmake_minimum_required(VERSION 2.8)

project(wav-rnnoise)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")
set(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE)
#set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_BUILD_TYPE RelWithDebInfo)
#set(INTTYPES_FORMAT "C99")
SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g -ggdb") 
SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")

include_directories(inc src)
set(RNNOISE_SRC_
	src/rnnoise_16k/celt_lpc.cpp
	src/rnnoise_16k/denoise16.c
	src/rnnoise_16k/kiss_fft.c
	src/rnnoise_16k/pitch.cpp
	src/rnnoise_16k/rnn.c
	src/rnnoise_16k/rnn_data.c
)
message("${RNNOISE_SRC_}")

add_executable(rnnoise src/main.c ${RNNOISE_SRC_})
LINK_LIBRARIES(m)

