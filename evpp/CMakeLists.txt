
file(GLOB evpp_SRCS *.cc */*.cc *.h */*.h)

message(STATUS "evpp_SRCS : " ${evpp_SRCS})

include_directories(${PROJECT_SOURCE_DIR})

add_library(evpp SHARED ${evpp_SRCS})
add_library(evpp_static STATIC ${evpp_SRCS})

if (UNIX)
target_link_libraries(evpp        event glog pthread)
target_link_libraries(evpp_static event glog pthread)
else(UNIX)
target_link_libraries(evpp        event libglog_static)
target_link_libraries(evpp_static event libglog_static)
endif(UNIX)

