---
title: "cmake reports gcc is broken. Where do I start?"
date: 2013-05-16
forum: Packaging and Compiling Programs
---

### Post by jmborr on 2013-05-16
I am trying to compile a project but cmake stops right at the beginning with the message that gcc is broken (see below). I am ignoramus when it comes to cmake, so any help where to get me starting debugging this problem is very very welcome.

Ubuntu 12.04.2
gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) **4.6.3 ** (I checked that my gcc compiles a 'hello world' code)
cmake version** 2.8.7**

cmake command:
[FONT=Arial Black]cmake -G "Unix Makefiles" -DCMAKE_BUILD_TYPE=Debug ../Mantid[/FONT]

Output to terminal:
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Could not determine Eclipse version, assuming at least 3.6 (Helios). Adjust CMAKE_ECLIPSE_VERSION if this is wrong.
-- Check for working C compiler: /usr/bin/gcc-4.6
-- Check for working C compiler: /usr/bin/gcc-4.6 -- **broken**
CMake Error at /usr/share/cmake-2.8/Modules/CMakeTestCCompiler.cmake:52 (MESSAGE):
**The C compiler "/usr/bin/gcc-4.6" is not able to compile a simple testprogram.**

It fails with the following output:

Change Dir: /home/jmborr/devel/mantidproject/mantid/Code/debug/CMakeFiles/CMakeTmp

Run Build Command:/usr/bin/make "cmTryCompileExec/fast"

/usr/bin/make -f CMakeFiles/cmTryCompileExec.dir/build.make CMakeFiles/cmTryCompileExec.dir/build

make[1]: Entering directory `/home/jmborr/devel/mantidproject/mantid/Code/debug/CMakeFiles/CMakeTmp'

/usr/bin/cmake -E cmake_progress_report /home/jmborr/devel/mantidproject/mantid/Code/debug/CMakeFiles/CMakeTmp/CMakeFiles 1

Building C object CMakeFiles/cmTryCompileExec.dir/testCCompiler.c.o

/usr/bin/gcc-4.6 /usr/include -o CMakeFiles/cmTryCompileExec.dir/testCCompiler.c.o -c /home/jmborr/devel/mantidproject/mantid/Code/debug/CMakeFiles/CMakeTmp/testCCompiler.c

**gcc-4.6: warning: /usr/include: linker input file unused because linking not done**

Linking C executable cmTryCompileExec

/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTryCompileExec.dir/link.txt --verbose=1

/usr/bin/gcc-4.6 /usr/include /usr/lib CMakeFiles/cmTryCompileExec.dir/testCCompiler.c.o -o cmTryCompileExec -rdynamic
[B]
/usr/bin/ld: cannot find /usr/include: File format not recognized

/usr/bin/ld: cannot find /usr/lib: File format not recognized[/B]

collect2: ld returned 1 exit status

make[1]: Leaving directory

---

### Post by jmborr on 2013-05-16
So I found out that the problem is constrained to my user account. The program compiles from any other account

---

