---
title: "Can't find dependency [PTHREAD] for target"
date: 2013-01-19
forum: Programming Talk
---

### Post by JStrongs on 2013-01-19
Hello all, 

I'm trying to compile the helloworld from Aldebaran helloworld example with cmake, and I'm getting an error, because Cmake seems that doesn't find the PTHREAD library brought by ALCOMMON. 

I'm using CMake 2.8.7 and aldebaran sdk 1.8.16 and Ubuntu 11.04.

Anybody knows how to solve this issue? I'm stacked at this point since two weeks ago!


Thanks a lot, I attach the cmake output.

PD: pthread/thread libraries are installed.

Thanks!




he C compiler identification is GNU

The CXX compiler identification is GNU

Check for working C compiler: /usr/bin/gcc

Check for working C compiler: /usr/bin/gcc -- works

Detecting C compiler ABI info

Detecting C compiler ABI info - done

Check for working CXX compiler: /usr/bin/c++

Check for working CXX compiler: /usr/bin/c++ -- works

Detecting CXX compiler ABI info

Detecting CXX compiler ABI info - done

SDK Extra folders (SDK_EXTRA_DIRS) is /home/jesus/Documents/NAO/aldebaran-cpp-sdk-1.8.16-linux-i386

SDK: /home/jesus/Documents/NAO/aldebaran-cpp-sdk-1.8.16-linux-i386

SDK: /home/jesus/Documents/NAO/aldebaran-cpp-sdk-1.8.16-linux-i386

LIBFIND: [PTHREAD] pthread NOT FOUND

CMake Error at /home/jesus/Documents/NAO/aldebaran-cpp-sdk-1.8.16-linux-i386/lib/cmake/uselib.cmake:57 (message):

BINLIB: use_lib: Can't find dependency [PTHREAD] for target helloworld

brought by ALCOMMON.

Call Stack (most recent call first):

/home/jesus/Documents/NAO/aldebaran-cpp-sdk-1.8.16-linux-i386/lib/cmake/uselib.cmake:126 (_use_lib_compute_depends)

/home/jesus/Documents/NAO/aldebaran-cpp-sdk-1.8.16-linux-i386/lib/cmake/uselib.cmake:105 (_use_lib)

CMakeLists.txt:18 (use_lib)

---

### Post by bird1500 on 2013-01-19
Maybe no need to search:
target_link_libraries(app pthread)

---

### Post by JStrongs on 2013-01-21
IT didn't work....  I modified the CMakeList file adding the function but the same error raised :(

---

