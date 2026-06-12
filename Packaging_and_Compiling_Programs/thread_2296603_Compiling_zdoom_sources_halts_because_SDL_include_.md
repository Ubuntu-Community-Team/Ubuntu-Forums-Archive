---
title: "Compiling zdoom sources halts because SDL include folder is NOTFOUND"
date: 2015-09-27
forum: Packaging and Compiling Programs
---

### Post by Stubkan on 2015-09-27
Hi,

I have put ubuntu mate on my samsung slate 7 tablet, taking windows 7 off because it gives minecraft a big fps boost...  It is running Ubuntu MATE 1.8.2 - Ubuntu 15.04

I want other games on it, and WINE had bricked the tablet when I tried to install it, so I've stuck to native linux apps for now...  I'm trying to put zdoom on and am following this guide here;

**[http://zdoom.org/wiki/Compile_ZDoom_on_Linux](http://zdoom.org/wiki/Compile_ZDoom_on_Linux)**

I made it all the way down to the compiling bit - and it halts with this output
[INDENT][I]CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
SDL_INCLUDE_DIR
   used as include directory in directory /home/stubkan/zdoom_build/zdoom/src
   used as include directory in directory /home/stubkan/zdoom_build/zdoom/src
   used as include directory in directory /home/stubkan/zdoom_build/zdoom/output_sdl

-- Configuring incomplete, errors occurred![/I]
[/INDENT]


I think SDL is already installed as I had run the necessary apt-get installs at the beginning.  It is hopefully some small error that can be rectified.

Can anyone be of assistance?

---

### Post by steeldriver on 2015-09-27
Hello and welcome to the forums

Can you post the entire cmake command output (between [CODE] formatting tags please)?

I notice that the listed dependencies don't include pkg-config (although it's possible one of the other packages installs it as a sub-dependency)

---

### Post by Stubkan on 2015-09-27
I'll list the terminal output here, also link the cmake output and error logs as well.

Output of make command :
```

stubkan@stub-slate:~$ cd $HOME/zdoom_build/zdoom/build && \
> if [ "$(uname -m)" = "x86_64" ]; then
> FMODFOLDER="fmodapi42636linux64"
> FMODFILE="libfmodex64-4.26.36"
> else
> FMODFOLDER="fmodapi42636linux"
> FMODFILE="libfmodex-4.26.36"
> fi && \
> make clean ; \
> cmake -DCMAKE_BUILD_TYPE=Release \
> -DFMOD_LIBRARY=$HOME/zdoom_build/zdoom/$FMODFOLDER/api/lib/$FMODFILE.so \
> -DFMOD_INCLUDE_DIR=$HOME/zdoom_build/zdoom/$FMODFOLDER/api/inc .. && \
> make
-- Using system zlib
-- Using system jpeg library
-- Using system bzip2 library
-- /usr/include
-- /usr/include
-- /home/stubkan/zdoom_build/zdoom/lzma/C
CMake Warning (dev) at CMakeLists.txt:14 (get_target_property):
  Policy CMP0026 is not set: Disallow use of the LOCATION target property.
  Run "cmake --help-policy CMP0026" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.

  The LOCATION property should not be read from target "zipdir".  Use the
  target name directly with add_custom_command, or use the generator
  expression $<TARGET_FILE>, as appropriate.

Call Stack (most recent call first):
  wadsrc/CMakeLists.txt:3 (add_pk3)
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Found Xcursor at /usr/lib/x86_64-linux-gnu/libXcursor.so
-- Could NOT find SDL (missing:  SDL_LIBRARY SDL_INCLUDE_DIR) 
CMake Error at src/CMakeLists.txt:197 (message):
  SDL is required for building.


-- FMOD include files found at /home/stubkan/zdoom_build/zdoom/fmodapi42636linux64/api/inc
-- FMOD library found at /home/stubkan/zdoom_build/zdoom/fmodapi42636linux64/api/lib/libfmodex64-4.26.36.so
-- Selected assembler: /usr/bin/as
CMake Warning (dev) at src/CMakeLists.txt:493 (get_target_property):
  Policy CMP0026 is not set: Disallow use of the LOCATION target property.
  Run "cmake --help-policy CMP0026" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.

  The LOCATION property should not be read from target "updaterevision".  Use
  the target name directly with add_custom_command, or use the generator
  expression $<TARGET_FILE>, as appropriate.

This warning is for project developers.  Use -Wno-dev to suppress it.

-- Fluid synth libs: /usr/lib/x86_64-linux-gnu/libfluidsynth.so
CMake Warning (dev) at src/CMakeLists.txt:578 (get_target_property):
  Policy CMP0026 is not set: Disallow use of the LOCATION target property.
  Run "cmake --help-policy CMP0026" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.

  The LOCATION property should not be read from target "lemon".  Use the
  target name directly with add_custom_command, or use the generator
  expression $<TARGET_FILE>, as appropriate.

This warning is for project developers.  Use -Wno-dev to suppress it.

CMake Warning (dev) at src/CMakeLists.txt:579 (get_target_property):
  Policy CMP0026 is not set: Disallow use of the LOCATION target property.
  Run "cmake --help-policy CMP0026" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.

  The LOCATION property should not be read from target "re2c".  Use the
  target name directly with add_custom_command, or use the generator
  expression $<TARGET_FILE>, as appropriate.

This warning is for project developers.  Use -Wno-dev to suppress it.

CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
SDL_INCLUDE_DIR
   used as include directory in directory /home/stubkan/zdoom_build/zdoom/src
   used as include directory in directory /home/stubkan/zdoom_build/zdoom/src
   used as include directory in directory /home/stubkan/zdoom_build/zdoom/output_sdl

-- Configuring incomplete, errors occurred!
See also "/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeOutput.log".
See also "/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeError.log".
stubkan@stub-slate:~/zdoom_build/zdoom/build$ 


```

Contents of CMakeError.log
```

Determining if the function itoa exists failed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec3717190625/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec3717190625.dir/build.make CMakeFiles/cmTryCompileExec3717190625.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec3717190625.dir/CheckFunctionExists.c.o
/usr/bin/cc   -Wall -Wno-pointer-sign -Wno-uninitialized -DCHECK_FUNCTION_EXISTS=itoa   -o CMakeFiles/cmTryCompileExec3717190625.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
Linking C executable cmTryCompileExec3717190625
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec3717190625.dir/link.txt --verbose=1
/usr/bin/cc    -Wall -Wno-pointer-sign -Wno-uninitialized -DCHECK_FUNCTION_EXISTS=itoa    CMakeFiles/cmTryCompileExec3717190625.dir/CheckFunctionExists.c.o  -o cmTryCompileExec3717190625 -rdynamic 
CMakeFiles/cmTryCompileExec3717190625.dir/CheckFunctionExists.c.o: In function `main':
CheckFunctionExists.c:(.text+0x15): undefined reference to `itoa'
collect2: error: ld returned 1 exit status
CMakeFiles/cmTryCompileExec3717190625.dir/build.make:88: recipe for target 'cmTryCompileExec3717190625' failed
make[1]: *** [cmTryCompileExec3717190625] Error 1
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
Makefile:118: recipe for target 'cmTryCompileExec3717190625/fast' failed
make: *** [cmTryCompileExec3717190625/fast] Error 2


Determining if the pthread_create exist failed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec677940785/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec677940785.dir/build.make CMakeFiles/cmTryCompileExec677940785.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec677940785.dir/CheckSymbolExists.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec677940785.dir/CheckSymbolExists.c.o   -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CheckSymbolExists.c
Linking C executable cmTryCompileExec677940785
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec677940785.dir/link.txt --verbose=1
/usr/bin/cc        CMakeFiles/cmTryCompileExec677940785.dir/CheckSymbolExists.c.o  -o cmTryCompileExec677940785 -rdynamic 
CMakeFiles/cmTryCompileExec677940785.dir/CheckSymbolExists.c.o: In function `main':
CheckSymbolExists.c:(.text+0x16): undefined reference to `pthread_create'
collect2: error: ld returned 1 exit status
CMakeFiles/cmTryCompileExec677940785.dir/build.make:88: recipe for target 'cmTryCompileExec677940785' failed
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
make[1]: *** [cmTryCompileExec677940785] Error 1
Makefile:118: recipe for target 'cmTryCompileExec677940785/fast' failed
make: *** [cmTryCompileExec677940785/fast] Error 2

File /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CheckSymbolExists.c:
/* */
#include <pthread.h>

int main(int argc, char** argv)
{
  (void)argv;
#ifndef pthread_create
  return ((int*)(&pthread_create))[argc];
#else
  (void)argc;
  return 0;
#endif
}

Determining if the function pthread_create exists in the pthreads failed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec1534741524/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec1534741524.dir/build.make CMakeFiles/cmTryCompileExec1534741524.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec1534741524.dir/CheckFunctionExists.c.o
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=pthread_create   -o CMakeFiles/cmTryCompileExec1534741524.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
Linking C executable cmTryCompileExec1534741524
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec1534741524.dir/link.txt --verbose=1
/usr/bin/cc    -DCHECK_FUNCTION_EXISTS=pthread_create    CMakeFiles/cmTryCompileExec1534741524.dir/CheckFunctionExists.c.o  -o cmTryCompileExec1534741524 -rdynamic -lpthreads 
/usr/bin/ld: cannot find -lpthreads
collect2: error: ld returned 1 exit status
CMakeFiles/cmTryCompileExec1534741524.dir/build.make:88: recipe for target 'cmTryCompileExec1534741524' failed
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
make[1]: *** [cmTryCompileExec1534741524] Error 1
Makefile:118: recipe for target 'cmTryCompileExec1534741524/fast' failed
make: *** [cmTryCompileExec1534741524/fast] Error 2


Determining if the function filelength exists failed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec2878758375/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec2878758375.dir/build.make CMakeFiles/cmTryCompileExec2878758375.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec2878758375.dir/CheckFunctionExists.c.o
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=filelength   -o CMakeFiles/cmTryCompileExec2878758375.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
Linking C executable cmTryCompileExec2878758375
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec2878758375.dir/link.txt --verbose=1
/usr/bin/cc    -DCHECK_FUNCTION_EXISTS=filelength    CMakeFiles/cmTryCompileExec2878758375.dir/CheckFunctionExists.c.o  -o cmTryCompileExec2878758375 -rdynamic 
CMakeFiles/cmTryCompileExec2878758375.dir/CheckFunctionExists.c.o: In function `main':
CheckFunctionExists.c:(.text+0x15): undefined reference to `filelength'
collect2: error: ld returned 1 exit status
CMakeFiles/cmTryCompileExec2878758375.dir/build.make:88: recipe for target 'cmTryCompileExec2878758375' failed
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
make[1]: *** [cmTryCompileExec2878758375] Error 1
Makefile:118: recipe for target 'cmTryCompileExec2878758375/fast' failed
make: *** [cmTryCompileExec2878758375/fast] Error 2


Determining if the function strupr exists failed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec1567186133/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec1567186133.dir/build.make CMakeFiles/cmTryCompileExec1567186133.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec1567186133.dir/CheckFunctionExists.c.o
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=strupr   -o CMakeFiles/cmTryCompileExec1567186133.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
Linking C executable cmTryCompileExec1567186133
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec1567186133.dir/link.txt --verbose=1
/usr/bin/cc    -DCHECK_FUNCTION_EXISTS=strupr    CMakeFiles/cmTryCompileExec1567186133.dir/CheckFunctionExists.c.o  -o cmTryCompileExec1567186133 -rdynamic 
CMakeFiles/cmTryCompileExec1567186133.dir/CheckFunctionExists.c.o: In function `main':
CheckFunctionExists.c:(.text+0x15): undefined reference to `strupr'
collect2: error: ld returned 1 exit status
CMakeFiles/cmTryCompileExec1567186133.dir/build.make:88: recipe for target 'cmTryCompileExec1567186133' failed
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
make[1]: *** [cmTryCompileExec1567186133] Error 1
Makefile:118: recipe for target 'cmTryCompileExec1567186133/fast' failed
make: *** [cmTryCompileExec1567186133/fast] Error 2


Determining if the function stricmp exists failed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec2294081251/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec2294081251.dir/build.make CMakeFiles/cmTryCompileExec2294081251.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec2294081251.dir/CheckFunctionExists.c.o
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=stricmp   -o CMakeFiles/cmTryCompileExec2294081251.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
Linking C executable cmTryCompileExec2294081251
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec2294081251.dir/link.txt --verbose=1
/usr/bin/cc    -DCHECK_FUNCTION_EXISTS=stricmp    CMakeFiles/cmTryCompileExec2294081251.dir/CheckFunctionExists.c.o  -o cmTryCompileExec2294081251 -rdynamic 
CMakeFiles/cmTryCompileExec2294081251.dir/CheckFunctionExists.c.o: In function `main':
CheckFunctionExists.c:(.text+0x15): undefined reference to `stricmp'
collect2: error: ld returned 1 exit status
CMakeFiles/cmTryCompileExec2294081251.dir/build.make:88: recipe for target 'cmTryCompileExec2294081251' failed
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
make[1]: *** [cmTryCompileExec2294081251] Error 1
Makefile:118: recipe for target 'cmTryCompileExec2294081251/fast' failed
make: *** [cmTryCompileExec2294081251/fast] Error 2


Determining if the function strnicmp exists failed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec1976760323/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec1976760323.dir/build.make CMakeFiles/cmTryCompileExec1976760323.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec1976760323.dir/CheckFunctionExists.c.o
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=strnicmp   -o CMakeFiles/cmTryCompileExec1976760323.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
Linking C executable cmTryCompileExec1976760323
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec1976760323.dir/link.txt --verbose=1
/usr/bin/cc    -DCHECK_FUNCTION_EXISTS=strnicmp    CMakeFiles/cmTryCompileExec1976760323.dir/CheckFunctionExists.c.o  -o cmTryCompileExec1976760323 -rdynamic 
CMakeFiles/cmTryCompileExec1976760323.dir/CheckFunctionExists.c.o: In function `main':
CheckFunctionExists.c:(.text+0x15): undefined reference to `strnicmp'
collect2: error: ld returned 1 exit status
CMakeFiles/cmTryCompileExec1976760323.dir/build.make:88: recipe for target 'cmTryCompileExec1976760323' failed
make[1]: *** [cmTryCompileExec1976760323] Error 1
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
Makefile:118: recipe for target 'cmTryCompileExec1976760323/fast' failed
make: *** [cmTryCompileExec1976760323/fast] Error 2


```

Also the contents of CMakeOutput.log ...  This file is like greek to me!
```

The system is: Linux - 3.19.0-28-generic - x86_64
Compiling the C compiler identification source file "CMakeCCompilerId.c" succeeded.
Compiler: /usr/bin/cc 
Build flags: 
Id flags: 

The output was:
0


Compilation of the C compiler identification source "CMakeCCompilerId.c" produced "a.out"

The C compiler identification is GNU, found in "/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/3.0.2/CompilerIdC/a.out"

Compiling the CXX compiler identification source file "CMakeCXXCompilerId.cpp" succeeded.
Compiler: /usr/bin/c++ 
Build flags: 
Id flags: 

The output was:
0


Compilation of the CXX compiler identification source "CMakeCXXCompilerId.cpp" produced "a.out"

The CXX compiler identification is GNU, found in "/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/3.0.2/CompilerIdCXX/a.out"

Determining if the C compiler works passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec1123937982/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec1123937982.dir/build.make CMakeFiles/cmTryCompileExec1123937982.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec1123937982.dir/testCCompiler.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec1123937982.dir/testCCompiler.c.o   -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/testCCompiler.c
Linking C executable cmTryCompileExec1123937982
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec1123937982.dir/link.txt --verbose=1
/usr/bin/cc       CMakeFiles/cmTryCompileExec1123937982.dir/testCCompiler.c.o  -o cmTryCompileExec1123937982 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Detecting C compiler ABI info compiled with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec3687973195/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec3687973195.dir/build.make CMakeFiles/cmTryCompileExec3687973195.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec3687973195.dir/CMakeCCompilerABI.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec3687973195.dir/CMakeCCompilerABI.c.o   -c /usr/share/cmake-3.0/Modules/CMakeCCompilerABI.c
Linking C executable cmTryCompileExec3687973195
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec3687973195.dir/link.txt --verbose=1
/usr/bin/cc     -v CMakeFiles/cmTryCompileExec3687973195.dir/CMakeCCompilerABI.c.o  -o cmTryCompileExec3687973195 -rdynamic  
Using built-in specs.
COLLECT_GCC=/usr/bin/cc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.9.2-10ubuntu13' --with-bugurl=file:///usr/share/doc/gcc-4.9/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.9 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.9 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.9-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) 
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-v' '-o' 'cmTryCompileExec3687973195' '-rdynamic' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.9/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/4.9/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper -plugin-opt=-fresolution=/tmp/ccYMo7XI.res -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s --sysroot=/ --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu --as-needed -export-dynamic -dynamic-linker /lib64/ld-linux-x86-64.so.2 -z relro -o cmTryCompileExec3687973195 /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.9/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.9 -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../.. CMakeFiles/cmTryCompileExec3687973195.dir/CMakeCCompilerABI.c.o -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/x86_64-linux-gnu/4.9/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crtn.o
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Parsed C implicit link information from above output:
  link line regex: [^( *|.*[/\])(ld|([^/\]+-)?ld|collect2)[^/\]*( |$)]
  ignore line: [Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp]
  ignore line: []
  ignore line: [Run Build Command:"/usr/bin/make" "cmTryCompileExec3687973195/fast"]
  ignore line: [/usr/bin/make -f CMakeFiles/cmTryCompileExec3687973195.dir/build.make CMakeFiles/cmTryCompileExec3687973195.dir/build]
  ignore line: [make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp']
  ignore line: [/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1]
  ignore line: [Building C object CMakeFiles/cmTryCompileExec3687973195.dir/CMakeCCompilerABI.c.o]
  ignore line: [/usr/bin/cc    -o CMakeFiles/cmTryCompileExec3687973195.dir/CMakeCCompilerABI.c.o   -c /usr/share/cmake-3.0/Modules/CMakeCCompilerABI.c]
  ignore line: [Linking C executable cmTryCompileExec3687973195]
  ignore line: [/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec3687973195.dir/link.txt --verbose=1]
  ignore line: [/usr/bin/cc     -v CMakeFiles/cmTryCompileExec3687973195.dir/CMakeCCompilerABI.c.o  -o cmTryCompileExec3687973195 -rdynamic  ]
  ignore line: [Using built-in specs.]
  ignore line: [COLLECT_GCC=/usr/bin/cc]
  ignore line: [COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper]
  ignore line: [Target: x86_64-linux-gnu]
  ignore line: [Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.9.2-10ubuntu13' --with-bugurl=file:///usr/share/doc/gcc-4.9/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.9 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.9 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.9-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu]
  ignore line: [Thread model: posix]
  ignore line: [gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) ]
  ignore line: [COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/]
  ignore line: [LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../:/lib/:/usr/lib/]
  ignore line: [COLLECT_GCC_OPTIONS='-v' '-o' 'cmTryCompileExec3687973195' '-rdynamic' '-mtune=generic' '-march=x86-64']
  link line: [ /usr/lib/gcc/x86_64-linux-gnu/4.9/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/4.9/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper -plugin-opt=-fresolution=/tmp/ccYMo7XI.res -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s --sysroot=/ --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu --as-needed -export-dynamic -dynamic-linker /lib64/ld-linux-x86-64.so.2 -z relro -o cmTryCompileExec3687973195 /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.9/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.9 -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../.. CMakeFiles/cmTryCompileExec3687973195.dir/CMakeCCompilerABI.c.o -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/x86_64-linux-gnu/4.9/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crtn.o]
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/collect2] ==> ignore
    arg [-plugin] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/liblto_plugin.so] ==> ignore
    arg [-plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper] ==> ignore
    arg [-plugin-opt=-fresolution=/tmp/ccYMo7XI.res] ==> ignore
    arg [-plugin-opt=-pass-through=-lgcc] ==> ignore
    arg [-plugin-opt=-pass-through=-lgcc_s] ==> ignore
    arg [-plugin-opt=-pass-through=-lc] ==> ignore
    arg [-plugin-opt=-pass-through=-lgcc] ==> ignore
    arg [-plugin-opt=-pass-through=-lgcc_s] ==> ignore
    arg [--sysroot=/] ==> ignore
    arg [--build-id] ==> ignore
    arg [--eh-frame-hdr] ==> ignore
    arg [-m] ==> ignore
    arg [elf_x86_64] ==> ignore
    arg [--hash-style=gnu] ==> ignore
    arg [--as-needed] ==> ignore
    arg [-export-dynamic] ==> ignore
    arg [-dynamic-linker] ==> ignore
    arg [/lib64/ld-linux-x86-64.so.2] ==> ignore
    arg [-zrelro] ==> ignore
    arg [-o] ==> ignore
    arg [cmTryCompileExec3687973195] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crt1.o] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crti.o] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/crtbegin.o] ==> ignore
    arg [-L/usr/lib/gcc/x86_64-linux-gnu/4.9] ==> dir [/usr/lib/gcc/x86_64-linux-gnu/4.9]
    arg [-L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu] ==> dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu]
    arg [-L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib] ==> dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib]
    arg [-L/lib/x86_64-linux-gnu] ==> dir [/lib/x86_64-linux-gnu]
    arg [-L/lib/../lib] ==> dir [/lib/../lib]
    arg [-L/usr/lib/x86_64-linux-gnu] ==> dir [/usr/lib/x86_64-linux-gnu]
    arg [-L/usr/lib/../lib] ==> dir [/usr/lib/../lib]
    arg [-L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../..] ==> dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../..]
    arg [CMakeFiles/cmTryCompileExec3687973195.dir/CMakeCCompilerABI.c.o] ==> ignore
    arg [-lgcc] ==> lib [gcc]
    arg [--as-needed] ==> ignore
    arg [-lgcc_s] ==> lib [gcc_s]
    arg [--no-as-needed] ==> ignore
    arg [-lc] ==> lib [c]
    arg [-lgcc] ==> lib [gcc]
    arg [--as-needed] ==> ignore
    arg [-lgcc_s] ==> lib [gcc_s]
    arg [--no-as-needed] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/crtend.o] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crtn.o] ==> ignore
  remove lib [gcc]
  remove lib [gcc_s]
  remove lib [gcc]
  remove lib [gcc_s]
  collapse library dir [/usr/lib/gcc/x86_64-linux-gnu/4.9] ==> [/usr/lib/gcc/x86_64-linux-gnu/4.9]
  collapse library dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu] ==> [/usr/lib/x86_64-linux-gnu]
  collapse library dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib] ==> [/usr/lib]
  collapse library dir [/lib/x86_64-linux-gnu] ==> [/lib/x86_64-linux-gnu]
  collapse library dir [/lib/../lib] ==> [/lib]
  collapse library dir [/usr/lib/x86_64-linux-gnu] ==> [/usr/lib/x86_64-linux-gnu]
  collapse library dir [/usr/lib/../lib] ==> [/usr/lib]
  collapse library dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../..] ==> [/usr/lib]
  implicit libs: [c]
  implicit dirs: [/usr/lib/gcc/x86_64-linux-gnu/4.9;/usr/lib/x86_64-linux-gnu;/usr/lib;/lib/x86_64-linux-gnu;/lib]
  implicit fwks: []


Determining if the CXX compiler works passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec1884556068/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec1884556068.dir/build.make CMakeFiles/cmTryCompileExec1884556068.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building CXX object CMakeFiles/cmTryCompileExec1884556068.dir/testCXXCompiler.cxx.o
/usr/bin/c++     -o CMakeFiles/cmTryCompileExec1884556068.dir/testCXXCompiler.cxx.o -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/testCXXCompiler.cxx
Linking CXX executable cmTryCompileExec1884556068
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec1884556068.dir/link.txt --verbose=1
/usr/bin/c++        CMakeFiles/cmTryCompileExec1884556068.dir/testCXXCompiler.cxx.o  -o cmTryCompileExec1884556068 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Detecting CXX compiler ABI info compiled with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec4131038978/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec4131038978.dir/build.make CMakeFiles/cmTryCompileExec4131038978.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building CXX object CMakeFiles/cmTryCompileExec4131038978.dir/CMakeCXXCompilerABI.cpp.o
/usr/bin/c++     -o CMakeFiles/cmTryCompileExec4131038978.dir/CMakeCXXCompilerABI.cpp.o -c /usr/share/cmake-3.0/Modules/CMakeCXXCompilerABI.cpp
Linking CXX executable cmTryCompileExec4131038978
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec4131038978.dir/link.txt --verbose=1
/usr/bin/c++      -v CMakeFiles/cmTryCompileExec4131038978.dir/CMakeCXXCompilerABI.cpp.o  -o cmTryCompileExec4131038978 -rdynamic  
Using built-in specs.
COLLECT_GCC=/usr/bin/c++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.9.2-10ubuntu13' --with-bugurl=file:///usr/share/doc/gcc-4.9/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.9 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.9 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.9-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) 
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-v' '-o' 'cmTryCompileExec4131038978' '-rdynamic' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.9/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/4.9/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper -plugin-opt=-fresolution=/tmp/cc8qvN9Z.res -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lgcc --sysroot=/ --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu --as-needed -export-dynamic -dynamic-linker /lib64/ld-linux-x86-64.so.2 -z relro -o cmTryCompileExec4131038978 /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.9/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.9 -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../.. CMakeFiles/cmTryCompileExec4131038978.dir/CMakeCXXCompilerABI.cpp.o -lstdc++ -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc /usr/lib/gcc/x86_64-linux-gnu/4.9/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crtn.o
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Parsed CXX implicit link information from above output:
  link line regex: [^( *|.*[/\])(ld|([^/\]+-)?ld|collect2)[^/\]*( |$)]
  ignore line: [Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp]
  ignore line: []
  ignore line: [Run Build Command:"/usr/bin/make" "cmTryCompileExec4131038978/fast"]
  ignore line: [/usr/bin/make -f CMakeFiles/cmTryCompileExec4131038978.dir/build.make CMakeFiles/cmTryCompileExec4131038978.dir/build]
  ignore line: [make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp']
  ignore line: [/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1]
  ignore line: [Building CXX object CMakeFiles/cmTryCompileExec4131038978.dir/CMakeCXXCompilerABI.cpp.o]
  ignore line: [/usr/bin/c++     -o CMakeFiles/cmTryCompileExec4131038978.dir/CMakeCXXCompilerABI.cpp.o -c /usr/share/cmake-3.0/Modules/CMakeCXXCompilerABI.cpp]
  ignore line: [Linking CXX executable cmTryCompileExec4131038978]
  ignore line: [/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec4131038978.dir/link.txt --verbose=1]
  ignore line: [/usr/bin/c++      -v CMakeFiles/cmTryCompileExec4131038978.dir/CMakeCXXCompilerABI.cpp.o  -o cmTryCompileExec4131038978 -rdynamic  ]
  ignore line: [Using built-in specs.]
  ignore line: [COLLECT_GCC=/usr/bin/c++]
  ignore line: [COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper]
  ignore line: [Target: x86_64-linux-gnu]
  ignore line: [Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.9.2-10ubuntu13' --with-bugurl=file:///usr/share/doc/gcc-4.9/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.9 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.9 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.9-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.9-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu]
  ignore line: [Thread model: posix]
  ignore line: [gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) ]
  ignore line: [COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/]
  ignore line: [LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.9/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../:/lib/:/usr/lib/]
  ignore line: [COLLECT_GCC_OPTIONS='-v' '-o' 'cmTryCompileExec4131038978' '-rdynamic' '-shared-libgcc' '-mtune=generic' '-march=x86-64']
  link line: [ /usr/lib/gcc/x86_64-linux-gnu/4.9/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/4.9/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper -plugin-opt=-fresolution=/tmp/cc8qvN9Z.res -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lgcc --sysroot=/ --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu --as-needed -export-dynamic -dynamic-linker /lib64/ld-linux-x86-64.so.2 -z relro -o cmTryCompileExec4131038978 /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.9/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.9 -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../.. CMakeFiles/cmTryCompileExec4131038978.dir/CMakeCXXCompilerABI.cpp.o -lstdc++ -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc /usr/lib/gcc/x86_64-linux-gnu/4.9/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crtn.o]
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/collect2] ==> ignore
    arg [-plugin] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/liblto_plugin.so] ==> ignore
    arg [-plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/4.9/lto-wrapper] ==> ignore
    arg [-plugin-opt=-fresolution=/tmp/cc8qvN9Z.res] ==> ignore
    arg [-plugin-opt=-pass-through=-lgcc_s] ==> ignore
    arg [-plugin-opt=-pass-through=-lgcc] ==> ignore
    arg [-plugin-opt=-pass-through=-lc] ==> ignore
    arg [-plugin-opt=-pass-through=-lgcc_s] ==> ignore
    arg [-plugin-opt=-pass-through=-lgcc] ==> ignore
    arg [--sysroot=/] ==> ignore
    arg [--build-id] ==> ignore
    arg [--eh-frame-hdr] ==> ignore
    arg [-m] ==> ignore
    arg [elf_x86_64] ==> ignore
    arg [--hash-style=gnu] ==> ignore
    arg [--as-needed] ==> ignore
    arg [-export-dynamic] ==> ignore
    arg [-dynamic-linker] ==> ignore
    arg [/lib64/ld-linux-x86-64.so.2] ==> ignore
    arg [-zrelro] ==> ignore
    arg [-o] ==> ignore
    arg [cmTryCompileExec4131038978] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crt1.o] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crti.o] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/crtbegin.o] ==> ignore
    arg [-L/usr/lib/gcc/x86_64-linux-gnu/4.9] ==> dir [/usr/lib/gcc/x86_64-linux-gnu/4.9]
    arg [-L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu] ==> dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu]
    arg [-L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib] ==> dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib]
    arg [-L/lib/x86_64-linux-gnu] ==> dir [/lib/x86_64-linux-gnu]
    arg [-L/lib/../lib] ==> dir [/lib/../lib]
    arg [-L/usr/lib/x86_64-linux-gnu] ==> dir [/usr/lib/x86_64-linux-gnu]
    arg [-L/usr/lib/../lib] ==> dir [/usr/lib/../lib]
    arg [-L/usr/lib/gcc/x86_64-linux-gnu/4.9/../../..] ==> dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../..]
    arg [CMakeFiles/cmTryCompileExec4131038978.dir/CMakeCXXCompilerABI.cpp.o] ==> ignore
    arg [-lstdc++] ==> lib [stdc++]
    arg [-lm] ==> lib [m]
    arg [-lgcc_s] ==> lib [gcc_s]
    arg [-lgcc] ==> lib [gcc]
    arg [-lc] ==> lib [c]
    arg [-lgcc_s] ==> lib [gcc_s]
    arg [-lgcc] ==> lib [gcc]
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/crtend.o] ==> ignore
    arg [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crtn.o] ==> ignore
  remove lib [gcc_s]
  remove lib [gcc]
  remove lib [gcc_s]
  remove lib [gcc]
  collapse library dir [/usr/lib/gcc/x86_64-linux-gnu/4.9] ==> [/usr/lib/gcc/x86_64-linux-gnu/4.9]
  collapse library dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu] ==> [/usr/lib/x86_64-linux-gnu]
  collapse library dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../../lib] ==> [/usr/lib]
  collapse library dir [/lib/x86_64-linux-gnu] ==> [/lib/x86_64-linux-gnu]
  collapse library dir [/lib/../lib] ==> [/lib]
  collapse library dir [/usr/lib/x86_64-linux-gnu] ==> [/usr/lib/x86_64-linux-gnu]
  collapse library dir [/usr/lib/../lib] ==> [/usr/lib]
  collapse library dir [/usr/lib/gcc/x86_64-linux-gnu/4.9/../../..] ==> [/usr/lib]
  implicit libs: [stdc++;m;c]
  implicit dirs: [/usr/lib/gcc/x86_64-linux-gnu/4.9;/usr/lib/x86_64-linux-gnu;/usr/lib;/lib/x86_64-linux-gnu;/lib]
  implicit fwks: []


Determining if the function BZ2_bzCompressInit exists in the /usr/lib/x86_64-linux-gnu/libbz2.so passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec349076450/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec349076450.dir/build.make CMakeFiles/cmTryCompileExec349076450.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec349076450.dir/CheckFunctionExists.c.o
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=BZ2_bzCompressInit   -o CMakeFiles/cmTryCompileExec349076450.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
Linking C executable cmTryCompileExec349076450
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec349076450.dir/link.txt --verbose=1
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=BZ2_bzCompressInit    CMakeFiles/cmTryCompileExec349076450.dir/CheckFunctionExists.c.o  -o cmTryCompileExec349076450 -rdynamic -lbz2 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Performing C++ SOURCE FILE Test HAVE_NO_ARRAY_BOUNDS succeded with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec2136847903/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec2136847903.dir/build.make CMakeFiles/cmTryCompileExec2136847903.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building CXX object CMakeFiles/cmTryCompileExec2136847903.dir/src.cxx.o
/usr/bin/c++    -Wall -Wextra -fomit-frame-pointer -DHAVE_NO_ARRAY_BOUNDS   -Wno-array-bounds -o CMakeFiles/cmTryCompileExec2136847903.dir/src.cxx.o -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/src.cxx
Linking CXX executable cmTryCompileExec2136847903
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec2136847903.dir/link.txt --verbose=1
/usr/bin/c++     -Wall -Wextra -fomit-frame-pointer -DHAVE_NO_ARRAY_BOUNDS    CMakeFiles/cmTryCompileExec2136847903.dir/src.cxx.o  -o cmTryCompileExec2136847903 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'

Source file was:
int main() { return 0; }
Performing C++ SOURCE FILE Test __LIBGME_TEST_VISIBILITY succeded with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec928569329/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec928569329.dir/build.make CMakeFiles/cmTryCompileExec928569329.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building CXX object CMakeFiles/cmTryCompileExec928569329.dir/src.cxx.o
/usr/bin/c++    -Wall -Wextra -fomit-frame-pointer -Wno-array-bounds -D__LIBGME_TEST_VISIBILITY   -fvisibility=hidden -o CMakeFiles/cmTryCompileExec928569329.dir/src.cxx.o -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/src.cxx
Linking CXX executable cmTryCompileExec928569329
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec928569329.dir/link.txt --verbose=1
/usr/bin/c++     -Wall -Wextra -fomit-frame-pointer -Wno-array-bounds -D__LIBGME_TEST_VISIBILITY    CMakeFiles/cmTryCompileExec928569329.dir/src.cxx.o  -o cmTryCompileExec928569329 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'

Source file was:
int main() { return 0; }
Determining if the function strdup exists passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec384279901/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec384279901.dir/build.make CMakeFiles/cmTryCompileExec384279901.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec384279901.dir/CheckFunctionExists.c.o
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=strdup   -o CMakeFiles/cmTryCompileExec384279901.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
<command-line>:0:23: warning: conflicting types for built-in function ‘strdup’
/usr/share/cmake-3.0/Modules/CheckFunctionExists.c:3:6: note: in expansion of macro ‘CHECK_FUNCTION_EXISTS’
 char CHECK_FUNCTION_EXISTS();
      ^
Linking C executable cmTryCompileExec384279901
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec384279901.dir/link.txt --verbose=1
/usr/bin/cc    -DCHECK_FUNCTION_EXISTS=strdup    CMakeFiles/cmTryCompileExec384279901.dir/CheckFunctionExists.c.o  -o cmTryCompileExec384279901 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Determining if the function strndup exists passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec2113558391/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec2113558391.dir/build.make CMakeFiles/cmTryCompileExec2113558391.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec2113558391.dir/CheckFunctionExists.c.o
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=strndup   -o CMakeFiles/cmTryCompileExec2113558391.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
<command-line>:0:23: warning: conflicting types for built-in function ‘strndup’
/usr/share/cmake-3.0/Modules/CheckFunctionExists.c:3:6: note: in expansion of macro ‘CHECK_FUNCTION_EXISTS’
 char CHECK_FUNCTION_EXISTS();
      ^
Linking C executable cmTryCompileExec2113558391
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec2113558391.dir/link.txt --verbose=1
/usr/bin/cc    -DCHECK_FUNCTION_EXISTS=strndup    CMakeFiles/cmTryCompileExec2113558391.dir/CheckFunctionExists.c.o  -o cmTryCompileExec2113558391 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Determining if the include file sys/types.h exists passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec423999802/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec423999802.dir/build.make CMakeFiles/cmTryCompileExec423999802.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec423999802.dir/CheckIncludeFile.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec423999802.dir/CheckIncludeFile.c.o   -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CheckIncludeFile.c
Linking C executable cmTryCompileExec423999802
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec423999802.dir/link.txt --verbose=1
/usr/bin/cc        CMakeFiles/cmTryCompileExec423999802.dir/CheckIncludeFile.c.o  -o cmTryCompileExec423999802 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Determining if the include file stdint.h exists passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec2220371522/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec2220371522.dir/build.make CMakeFiles/cmTryCompileExec2220371522.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec2220371522.dir/CheckIncludeFile.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec2220371522.dir/CheckIncludeFile.c.o   -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CheckIncludeFile.c
Linking C executable cmTryCompileExec2220371522
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec2220371522.dir/link.txt --verbose=1
/usr/bin/cc        CMakeFiles/cmTryCompileExec2220371522.dir/CheckIncludeFile.c.o  -o cmTryCompileExec2220371522 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Determining if the include file stddef.h exists passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec682456550/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec682456550.dir/build.make CMakeFiles/cmTryCompileExec682456550.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec682456550.dir/CheckIncludeFile.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec682456550.dir/CheckIncludeFile.c.o   -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CheckIncludeFile.c
Linking C executable cmTryCompileExec682456550
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec682456550.dir/link.txt --verbose=1
/usr/bin/cc        CMakeFiles/cmTryCompileExec682456550.dir/CheckIncludeFile.c.o  -o cmTryCompileExec682456550 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Determining size of char passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec3024057089/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec3024057089.dir/build.make CMakeFiles/cmTryCompileExec3024057089.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec3024057089.dir/SIZEOF_CHAR.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec3024057089.dir/SIZEOF_CHAR.c.o   -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CheckTypeSize/SIZEOF_CHAR.c
Linking C executable cmTryCompileExec3024057089
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec3024057089.dir/link.txt --verbose=1
/usr/bin/cc        CMakeFiles/cmTryCompileExec3024057089.dir/SIZEOF_CHAR.c.o  -o cmTryCompileExec3024057089 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Determining size of short passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec775898891/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec775898891.dir/build.make CMakeFiles/cmTryCompileExec775898891.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec775898891.dir/SIZEOF_SHORT.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec775898891.dir/SIZEOF_SHORT.c.o   -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CheckTypeSize/SIZEOF_SHORT.c
Linking C executable cmTryCompileExec775898891
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec775898891.dir/link.txt --verbose=1
/usr/bin/cc        CMakeFiles/cmTryCompileExec775898891.dir/SIZEOF_SHORT.c.o  -o cmTryCompileExec775898891 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Determining size of int passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec2460286403/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec2460286403.dir/build.make CMakeFiles/cmTryCompileExec2460286403.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec2460286403.dir/SIZEOF_INT.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec2460286403.dir/SIZEOF_INT.c.o   -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CheckTypeSize/SIZEOF_INT.c
Linking C executable cmTryCompileExec2460286403
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec2460286403.dir/link.txt --verbose=1
/usr/bin/cc        CMakeFiles/cmTryCompileExec2460286403.dir/SIZEOF_INT.c.o  -o cmTryCompileExec2460286403 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Determining size of long passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec339178686/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec339178686.dir/build.make CMakeFiles/cmTryCompileExec339178686.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec339178686.dir/SIZEOF_LONG.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec339178686.dir/SIZEOF_LONG.c.o   -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CheckTypeSize/SIZEOF_LONG.c
Linking C executable cmTryCompileExec339178686
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec339178686.dir/link.txt --verbose=1
/usr/bin/cc        CMakeFiles/cmTryCompileExec339178686.dir/SIZEOF_LONG.c.o  -o cmTryCompileExec339178686 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Performing C++ SOURCE FILE Test DUMB_CAN_USE_SSE succeded with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec1218925236/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec1218925236.dir/build.make CMakeFiles/cmTryCompileExec1218925236.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building CXX object CMakeFiles/cmTryCompileExec1218925236.dir/src.cxx.o
/usr/bin/c++    -DDUMB_CAN_USE_SSE   -msse -o CMakeFiles/cmTryCompileExec1218925236.dir/src.cxx.o -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/src.cxx
Linking CXX executable cmTryCompileExec1218925236
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec1218925236.dir/link.txt --verbose=1
/usr/bin/c++     -DDUMB_CAN_USE_SSE    CMakeFiles/cmTryCompileExec1218925236.dir/src.cxx.o  -o cmTryCompileExec1218925236 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'

Source file was:
int main() { return 0; }
Determining if files pthread.h exist passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec2106084855/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec2106084855.dir/build.make CMakeFiles/cmTryCompileExec2106084855.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec2106084855.dir/CheckIncludeFiles.c.o
/usr/bin/cc    -o CMakeFiles/cmTryCompileExec2106084855.dir/CheckIncludeFiles.c.o   -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CheckIncludeFiles.c
Linking C executable cmTryCompileExec2106084855
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec2106084855.dir/link.txt --verbose=1
/usr/bin/cc        CMakeFiles/cmTryCompileExec2106084855.dir/CheckIncludeFiles.c.o  -o cmTryCompileExec2106084855 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Determining if the function pthread_create exists in the pthread passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec3912388379/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec3912388379.dir/build.make CMakeFiles/cmTryCompileExec3912388379.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec3912388379.dir/CheckFunctionExists.c.o
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=pthread_create   -o CMakeFiles/cmTryCompileExec3912388379.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
Linking C executable cmTryCompileExec3912388379
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec3912388379.dir/link.txt --verbose=1
/usr/bin/cc    -DCHECK_FUNCTION_EXISTS=pthread_create    CMakeFiles/cmTryCompileExec3912388379.dir/CheckFunctionExists.c.o  -o cmTryCompileExec3912388379 -rdynamic -lpthread 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Determining if the function clock_gettime exists in the rt passed with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec3077212944/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec3077212944.dir/build.make CMakeFiles/cmTryCompileExec3077212944.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec3077212944.dir/CheckFunctionExists.c.o
/usr/bin/cc   -DCHECK_FUNCTION_EXISTS=clock_gettime   -o CMakeFiles/cmTryCompileExec3077212944.dir/CheckFunctionExists.c.o   -c /usr/share/cmake-3.0/Modules/CheckFunctionExists.c
Linking C executable cmTryCompileExec3077212944
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec3077212944.dir/link.txt --verbose=1
/usr/bin/cc    -DCHECK_FUNCTION_EXISTS=clock_gettime    CMakeFiles/cmTryCompileExec3077212944.dir/CheckFunctionExists.c.o  -o cmTryCompileExec3077212944 -rdynamic -lrt 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'


Performing C++ SOURCE FILE Test HAS_VA_COPY succeded with the following output:
Change Dir: /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTryCompileExec2388072673/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec2388072673.dir/build.make CMakeFiles/cmTryCompileExec2388072673.dir/build
make[1]: Entering directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building CXX object CMakeFiles/cmTryCompileExec2388072673.dir/src.cxx.o
/usr/bin/c++    -Wall -Wextra -Wno-unused -Wno-unused-parameter -Wno-missing-field-initializers   -DHAS_VA_COPY   -o CMakeFiles/cmTryCompileExec2388072673.dir/src.cxx.o -c /home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp/src.cxx
Linking CXX executable cmTryCompileExec2388072673
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec2388072673.dir/link.txt --verbose=1
/usr/bin/c++   -Wall -Wextra -Wno-unused -Wno-unused-parameter -Wno-missing-field-initializers   -DHAS_VA_COPY    CMakeFiles/cmTryCompileExec2388072673.dir/src.cxx.o  -o cmTryCompileExec2388072673 -rdynamic 
make[1]: Leaving directory '/home/stubkan/zdoom_build/zdoom/build/CMakeFiles/CMakeTmp'

Source file was:
#include <stdarg.h>
    int main() { va_list list1, list2; va_copy(list1, list2); return 0; }

```

I hope that helps!  Oh also, I checked :

pkg-config is already the newest version.
pkg-config set to manually installed.

---

