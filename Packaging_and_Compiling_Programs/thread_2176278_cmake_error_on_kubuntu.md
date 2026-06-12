---
title: "cmake error on kubuntu"
date: 2013-09-23
forum: Packaging and Compiling Programs
---

### Post by braindeadave on 2013-09-23
Hi Guys, 

Getting the following error when running Cmake on kubuntu 13.04. Any pointers? 

```

david@david-PC:~/Development$ cmake kdepim -DCMAKE_INSTALL_PREFIX=/usr/local -DLIB_SUFFIX=64 -DCMAKE_BUILD_TYPE=debugfull
-- The C compiler identification is GNU 4.7.3
-- The CXX compiler identification is GNU 4.7.3
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Found Git: /usr/bin/git (found version "1.8.1.2") 
-- Found git: /usr/bin/git
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - not found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found
-- Found Qt-Version 5.0.1 (using /usr/bin/qmake)
-- Looking for include file pthread.h
-- Looking for include file pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
-- Found Automoc4: /usr/bin/automoc4  
-- Found Perl: /usr/bin/perl (found version "5.14.2") 
-- Found Phonon: /usr/include (Required is at least version "4.3.80") 
-- Performing Test _OFFT_IS_64BIT
-- Performing Test _OFFT_IS_64BIT - Success
-- Performing Test HAVE_FPIE_SUPPORT                                                                                                                                 
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
QT_QT_INCLUDE_DIR
   used as include directory in directory /home/david/Development/CMakeFiles/CMakeTmp

CMake Error: Internal CMake error, TryCompile configure of cmake failed

CMake Error at /usr/share/kde4/apps/cmake/modules/FindKDE4Internal.cmake:1297 (message):
  Qt compiled without support for -fvisibility=hidden.  This will break
  plugins and linking of some applications.  Please fix your Qt installation
  (try passing --reduce-exports to configure).
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindKDE4.cmake:95 (find_package)
  CMakeLists.txt:112 (find_package)


-- Configuring incomplete, errors occurred!
david@david-PC:~/Development$ 


```

---

