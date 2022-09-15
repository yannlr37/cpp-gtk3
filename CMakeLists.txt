cmake_minimum_required(VERSION 2.8)

project( GtkApp )

find_package( PkgConfig REQUIRED )
pkg_check_modules(GTK3 REQUIRED gtkmm-3.0)

include_directories( ${GTK3_INCLUDE_DIRS} )
link_directories( ${GTK3_LIBRARY_DIRS} )

add_definitions( ${GTK3_CFLAGS_OTHER} )

file(GLOB all_SRCS
	"${PROJECT_SOURCE_DIR}/sources/*.hpp"
	"${PROJECT_SOURCE_DIR}/sources/*.cpp"
)

add_executable( GtkApp main.cpp ${all_SRCS} )

target_link_libraries( GtkApp ${CMAKE_THREAD_LIBS_INIT} ${GTK3_LIBRARIES} )
