---
title: "Compiling gizmod - &quot;CMake will not be able to correctly generate this project.&quot;"
date: 2012-10-03
forum: Packaging and Compiling Programs
---

### Post by insanity54 on 2012-10-03
Hello,

I'm trying to get gizmod installed so I can use a Griffin Powermate on my 10.04 system. The ubuntu repos contain gizmod 3.4 which is broken. I need 3.5 so I'm compiling from source.

I'm following the instructions [here]("http://sourceforge.net/apps/mediawiki/gizmod/index.php?title=Compile_from_Source#Obtaining_Gizmo_Daemon") to compile. I get to the step which uses cmake:

```
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr -DSYSCONF_INSTALL_DIR=/etc ../../gizmod
```

and this results in the following errors:
```
-- The C compiler identification is unknown
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- broken
CMake Error at /usr/share/cmake-2.8/Modules/CMakeTestCCompiler.cmake:52 (MESSAGE):
  The C compiler "/usr/bin/gcc" is not able to compile a simple test program.

  It fails with the following output:

   Change Dir: /home/chris/tmp/gizmod-3.5/build/CMakeFiles/CMakeTmp

  

  Run Build Command:/usr/bin/make "cmTryCompileExec/fast"

  /usr/bin/make -f CMakeFiles/cmTryCompileExec.dir/build.make
  CMakeFiles/cmTryCompileExec.dir/build

  make[1]: Entering directory
  `/home/chris/tmp/gizmod-3.5/build/CMakeFiles/CMakeTmp'

  /usr/bin/cmake -E cmake_progress_report
  /home/chris/tmp/gizmod-3.5/build/CMakeFiles/CMakeTmp/CMakeFiles 1

  Building C object CMakeFiles/cmTryCompileExec.dir/testCCompiler.c.o

  /usr/bin/gcc -o CMakeFiles/cmTryCompileExec.dir/testCCompiler.c.o -c
  /home/chris/tmp/gizmod-3.5/build/CMakeFiles/CMakeTmp/testCCompiler.c

  gcc: error trying to exec 'cc1': execvp: No such file or directory

  make[1]: Leaving directory
  `/home/chris/tmp/gizmod-3.5/build/CMakeFiles/CMakeTmp'

  make[1]: *** [CMakeFiles/cmTryCompileExec.dir/testCCompiler.c.o] Error 1

  make: *** [cmTryCompileExec/fast] Error 2

  

  

  CMake will not be able to correctly generate this project.
Call Stack (most recent call first):
  CMakeLists.txt:24 (project)


-- Configuring incomplete, errors occurred!

```

This output is Greek to me. What is causing cmake to fail?

---

### Post by drmrgd on 2012-10-03
Do you have gcc installed and working correctly.  Right at the top of the list of errors, it seems that something is not quite right with gcc:

> -- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- broken

You might try to install (if you don't already have it!), the build-essential package that has a bunch of utilities and tools for compiling programs:

```
sudo apt-get install build-essential
```

---

### Post by insanity54 on 2012-10-03
I tried re-installing build-essential

```
sudo apt-get --purge remove build-essential && sudo apt-get install build-essential
```

still getting the same error.

---

### Post by drmrgd on 2012-10-03
I'm not entirely sure what's missing.  I did some quick searches on the other string that seems to stick out:

> gcc: error trying to exec 'cc1': execvp: No such file or directory

It seems the general consensus is GCC looking for the cc1 library but not being able to find it due to a PATH issue.  I'm not where even close to a C guru, and I'm not entirely sure how to fix it.  I think if you can get around that error, then you should be in the clear, though.  I've found a ton of threads on forums (some of them were on this forum as well), but haven't found the exact workaround.  You might try this on the Gizmo SourceForge page too to see if one of the developers has a suggestion.  Sorry I couldn't help more!

---

### Post by insanity54 on 2012-10-04
You threw me a bone which is what I needed, thank you.

Yeah it's some sort of path issue:

```
whereis cc1
```
outputs:
```
cc1:
```
The system must not know where to look for it?

cc1 is on my system though:
```
locate cc1 | grep "/cc1$"
```
outputs:

```
/home/chris/arduino-1.0/hardware/tools/avr/lib/gcc/avr/4.3.2/cc1
/usr/lib/gcc/avr/4.3.4/cc1
/usr/lib/gcc/x86_64-linux-gnu/4.4/cc1

```

So it's on my system but gcc doesn't recognize it. I'm spent at the moment, taking a break from this, and maybe pursuing another route. [This]("http://screamingroot.org/node/5") looks promising. I already got it to scroll up and down on pages.

---

