# CMakeLists.txt

# Older versions of CMake are likely to work just fine but, since
# I don't know where to cut off I just use the version I'm using
cmake_minimum_required(VERSION "3.17")

# name of this example project
project(Projet)
#add_subdirectory(Data)
#set(Data "/Users/rubis/opencv/Projet/Data/Bibliotheque")

file(GLOB CSV_FILES "${CMAKE_CURRENT_SOURCE_DIR}/Users/rubis/opencv/Projet/Data/Bibliotheque/*.csv")


#add_custom_target(csva_files SOURCES ${CSV_FILES})


# set OpenCV_DIR variable equal to the path to the cmake
# files within the previously installed opencv program
set(OpenCV_DIR /Users/rubis/opencv/install/lib/cmake/opencv4)

# Tell compiler to use C++ 14 features which is needed because
# Clang version is often behind in the XCode installation
set(CMAKE_CXX_STANDARD 17)

# configure the necessary common CMake environment variables
# needed to include and link the OpenCV program into this
# demo project, namely OpenCV_INCLUDE_DIRS and OpenCV_LIBS
find_package( OpenCV REQUIRED )

# tell the build to include the headers from OpenCV
include_directories( ${OpenCV_INCLUDE_DIRS} )

# specify the executable target to be built
add_executable(Projet ./Source/main.cpp ./Source/traitement.cpp ./Source/Bibliotheques.cpp ./header/traitement.hpp ./header/Bibliotheques.hpp ${CSV_FILES})

# tell it to link the executable target against OpenCV
target_link_libraries(Projet ${OpenCV_LIBS} )

