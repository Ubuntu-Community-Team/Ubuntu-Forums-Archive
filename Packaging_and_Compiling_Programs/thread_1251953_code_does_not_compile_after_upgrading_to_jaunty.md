---
title: "code does not compile after upgrading to jaunty"
date: 2009-08-28
forum: Packaging and Compiling Programs
---

### Post by gozkil on 2009-08-28
Hi,

Last week I upgraded to jaunty, and until now I thought everything went fine.

I wanted to compile some c++ code using Netbeans. Under intrepid, and previously under hardy and gutsy, the code used to compile without errors. Now it complains about some invalid use of member X in static member function.

The source of error seems to be artoolkitplus library, which I tried to download and recompile but I got the same error. 

So, right now, I can not compile any of my projects that use artoolkitplus.
 
Any help is greatly appreciated!


/usr/bin/make -f nbproject/Makefile-Release.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/ali/NetBeansProjects/opencv artkp deneme 01'
make[1]: Warning: File `main.cpp' has modification time 9.3e+03 s in the future
mkdir -p build/Release/GNU-Linux-x86
g++ `pkg-config --libs --cflags opencv ARToolkitPlus`    -c -O2 -o build/Release/GNU-Linux-x86/main.o main.cpp
/usr/local/include/ARToolKitPlus/TrackerImpl.h: In static member function ‘static bool ARToolKitPlus::TrackerImpl<__PATTERN_SIZE_X, __PATTERN_SIZE_Y, __PATTERN_SAMPLE_NUM, __MAX_LOAD_PATTERNS, __MAX_IMAGE_PATTERNS>::calcCameraMatrix(const char*, int, int, ARFloat, ARFloat, ARFloat*)’:
In file included from /usr/local/include/ARToolKitPlus/TrackerImpl.h:693,
                 from /usr/local/include/ARToolKitPlus/TrackerSingleMarkerImpl.h:48,
                 from main.cpp:17:
/usr/local/include/ARToolKitPlus/TrackerImpl.h:636: error: invalid use of member ‘ARToolKitPlus::TrackerImpl<__PATTERN_SIZE_X, __PATTERN_SIZE_Y, __PATTERN_SAMPLE_NUM, __MAX_LOAD_PATTERNS, __MAX_IMAGE_PATTERNS>::screenWidth’ in static member function
/usr/include/c++/4.3/../../src/TrackerImpl.cxx:449: error: from this location
/usr/local/include/ARToolKitPlus/TrackerImpl.h:636: error: invalid use of member ‘ARToolKitPlus::TrackerImpl<__PATTERN_SIZE_X, __PATTERN_SIZE_Y, __PATTERN_SAMPLE_NUM, __MAX_LOAD_PATTERNS, __MAX_IMAGE_PATTERNS>::screenHeight’ in static member function
/usr/include/c++/4.3/../../src/TrackerImpl.cxx:449: error: from this location
main.cpp: In member function ‘virtual void MyLogger::artLog(const char*)’:
main.cpp:29: warning: format not a string literal and no format arguments
make[1]: *** [build/Release/GNU-Linux-x86/main.o] Error 1
make[1]: Leaving directory `/home/ali/NetBeansProjects/opencv artkp deneme 01'
make: *** [.build-impl] Error 2
BUILD FAILED (exit value 2, total time: 7s)

---

