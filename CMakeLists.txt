cmake_minimum_required (VERSION 2.6)

project (libavHM)

# Common packages required
find_package(SDL REQUIRED)
find_package(SDL_image REQUIRED)
find_package(Threads REQUIRED)

add_subdirectory(wrapper_hm)

set(filenames
	main.c
libavcodec/allcodecs.c
libavutil/audioconvert.c
libavutil/pixdesc.c
)

include_directories(. ${SDL_INCLUDE_DIR} wrapper_hm/src/Lib)

add_executable(hevc ${filenames})

target_link_libraries(hevc ${SDL_LIBRARY} LibWrapper TLibDecoder TLibVideoIO TLibCommon libmd5)
