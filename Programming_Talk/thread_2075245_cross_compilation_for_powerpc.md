---
title: "cross compilation for powerpc"
date: 2012-10-23
forum: Programming Talk
---

### Post by IAMTubby on 2012-10-23
Hey,
I have a few question regarding cross compilation. I have a small idea about some questions(3,5) and I have mentioned possible answers along with the questions. But I would like to get confirmation.

**Firstly,**
Is there a resource which I can read up, something slightly detailed, rather than error logs of problems people have faced. I am willing to put in the effort to learn it thoroughly.

**Secondly,** 
I just got something cross compiled working. As much as I'm happy for doing it on my own, I'm also tensed if anything would go wrong, and I would realize that it wasn't cross compiled properly. Anyways here's the thing, I cross compiled binutils for powerpc, by setting some environment variables and doing a --prefix=$HOME/local. Now in local I have 4 subfolders called **bin, lib, powerpc-linux and share**. Now how do I proceed to put binutils on the powerpc machine ? Do I like, have to take some of these libraries and put in the powerpc ? Not able to figure out. Ideally, I would have thought that cross compilation would give me an executable which is in the powerpc format and I just have to put it in the /usr/bin of the powerpc machine. 

**Third,** 
When we do a 
```
./configure CC=/opt/app_toolchain-4.2/usr/bin/ppc_4xx-gcc
```, are we going and rewriting the CC mentioned in the original Makefile ?
OR, In other words, telling to use this CC/compiler instead of what is mentioned in the Makefile ?

**Fourth,**
Who writes these cross compilers, say the ppc_4xx-gcc? Is it something which I can get from the open source community and put  anywhere in my application or does the ppc_4xx-gcc itself vary from application to application. 

**Fifth,**
How do I know **what** environment variables to set in the first place, and second **what's the path** to these ?
For eg, how do I come to know that I have to set AR=  and second, how do I come to know I have to set AR=/projects/app-trunk/app_toolchain/usr/bin/ppc_4xx-ar 
**Is it from ./configure --help(what environment variables to set) and the makefile log ?(what is the actual path)**

Thanks.
I'm sorry for posting long questions. I want to understand this well and am willing to put in the effort. Plus the momentum of getting something working(as of now).

---

### Post by Bachstelze on 2012-10-23
1. Not that I know of, but wherever you got your cross-compiler from would be a good place to start looking/asking.

2. If it works, it means it was compiled properly. ;) What you have under your $PREFIX is what would be copied into /usr/local (or wherever the default install location is) on the target system. So if you want to make it look as if you insalled it on the target system directly, just copy everything into the proper location.

3. When you specify a value for a make macro on the command-line, it is used instead of whatever the Makefile sets it to. You are not really rewriting the Makefile, just telling it to use this value for CC instead of what it would normally use.

4. ppc_4x-gcc is just a "special" version of gcc that will create a PPC binary instead of a x86 one. You can compile any C program with it, just type

```
ppc_4x-gcc -o foo foo.c
```

instead of just gcc.

5. This is probably program- and build-system-dependent. Bottom-line is if it compiles fine and runs on the target system, you can be satisfied that the compilation went fine. If you get some error message, then you will have to investigate...

---

### Post by mevun on 2012-10-23
1.  There doesn't seem to be a good recent resource for learning this stuff, but I really wish there was.

I think one step you need to learn is how most/all open-source C/C++ programs work.  Meaning you need to know about libraries (static and dynamic), the tools that build libraries, the include header files, the compilation and linking steps.  Then at runtime, you need to know how to specify where libraries are found (for dynamic-linked executables).  If you are cross-compiling a project that uses the "autoconf" tool for building, then you need to know about that tool to properly setup cross-compilation.

I have recently been cross-compiling an open source C++ library for the openwrt linux for a MIPS processor.  It has taken me about a week to build the library and I did not get a chance to really study these things I just mentioned.  In particular, I have very little knowledge about the "autoconf" and its "configure" script.  So I more-or-less muddled through the steps with lots of googling, although I have some knowledge about the things I mentioned above.  Now I am waiting to receive some hardware to test the output.

2. You definitely need to copy the executable binary files to the powerpc platform.  You need to copy the library files if you generated a dynamic-linked executable.  Try the "file" command on your file(s) in binutil directory.  For example:
```

ubuntu:/usr/bin$ file lpr
lpr: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), 
dynamically linked (uses shared libs), for GNU/Linux 2.6.24,
BuildID[sha1]=0xaf4e3b598cb922f4caa6ca62970593a938d5ceb3, stripped

```This shows that the file "lpr" is a dynamically-linked program with symbols stripped.

3. Normally, the "configure" script re-generates the Makefile.  So it is quite possible that specifying CC=cross-compile-cc does replace something in the Makefile.  Note: I am disagreeing with Bachstelze's answer, but I'm not really confident of my answer either.

4. The ppc_4x_gcc is the Gnu C compiler that will generate machine code suitable for the PowerPC cpu (4th generation?) which would be the "target".  Plain "gcc" is the Gnu C compiler which generates machine code suitable for the machine it is executing on (i.e. the host).

5. Knowing what environment variables and such to use is highly dependent on knowing your build system.  If you don't already know, "ar" is the archiver and generates static libraries.  I think you use static libraries if you want to build statically-linked executables.  That could matter if you are targeting a small-memory machine so that your final executable contains the minimum amount of code necessary.

---

### Post by IAMTubby on 2012-10-28
**A)**Thanks a lot Bachstelze, mevun for your wonderful replies. However, I  would like to get a general how-to-approach while cross compiling for a  PowerPC. I would start with something like this :

1)Download any source version (please see B here as well)
2)extract it
3)do a make without any changes to get errors, but at least you get the makefile log
3)Do ./configure --help to know what environment variables to set
4)Have a look at the makefile log and keep doing a Ctrl+f and find the  path to all the environment variables you get in step4 from the makefile  log.
5)Add all of these paths manually along with ./configure as ./configure CC=/some/new/path/to_the_gcc_capable_of_cross_compiling
6)Should work 

> **Bachstelze said:**
> 
This is probably program- and build-system-dependent.
> **mevun said:**
> 
. Knowing what environment variables and such to use is highly dependent  on knowing your build system. .
But you say that what environment variables is program- and build-system-dependent. How then do I find out what to set ? Are these mentioned in a file or something ?


**B)**Theoretically, is it possible to cross compile any version to PowerPC, ie, debian, red hat etc ?

**C)**> **Bachstelze said:**
> Do yourself a favor and download a precompiled PPC one (from e.g. Debian).
[http://packages.debian.org/squeeze/powerpc/binutils/download](http://packages.debian.org/squeeze/powerpc/binutils/download)
  C1)I keep getting stuck, when I do a sudo dpkg -i binutils_2.20.1-16_powerpc.deb
  It says
  ```
 
  Errors were encountered while processing: binutils_2.20.1-16_powerpc.deb
  
```  These are the details of my OS and kernel
  ```
Description:    Ubuntu 11.10
  Release:    11.10
  Codename:    oneiric
```  ```
3.0.0-12-generic
``` 
  C2)When I do sudo ar vx binutils_2.20.1-16_powerpc.deb, I get 3 files called   
  control.tar.gz, data.tar.gz and debian-binary. How do I proceed ?
  ```

  Description : Red Hat Enterprise Linux Server release 5.4(Tikanga)
  
```

**D)**Is there any other common repository for finding cross compiled versions for PowerPC. If it's not there, I would like to put my successful attempts in a forum and contribute. But will this be useful to people, as in will they be able to use it out of the box ? (I have a cross compiled executable called powerpc-linux-gprof which just works out of the box. I would like to share this and all my future attempts with powerpc users if they need it)

**E)**May I ask one more thing, not directly related to this thread?
You give me a .deb (from the link above) and say it's cross compiled for powerPC, so does it mean that .tar.bz2 is basically an archived version of source code, whereas .deb contains precompiled binaries ?



PS : I as a beginner, and for most beginners I talk to, one of the most challenging parts about getting into the wonderful open-source world is installation and compiling from source. I understand this will become fun over time, when you do some tweaks and can get things working. But for now, may I start a thread at [http://ubuntuforums.org/showthread.php?p=12322173#post12322173](http://ubuntuforums.org/showthread.php?p=12322173#post12322173) . As this thread grows, it will be of greatthelp to beginners like me. I

---

### Post by Bachstelze on 2012-10-28
> **IAMTubby said:**
> 
**B)**Theoretically, is it possible to cross compile any version to PowerPC, ie, debian, red hat etc ?

I have no idea what you mean here.

> **C)**
  C1)I keep getting stuck, when I do a sudo dpkg -i binutils_2.20.1-16_powerpc.deb
  It says
  ```
 
  Errors were encountered while processing: binutils_2.20.1-16_powerpc.deb
  
```  These are the details of my OS and kernel
  ```
Description:    Ubuntu 11.10
  Release:    11.10
  Codename:    oneiric
```  ```
3.0.0-12-generic
``` 


The .deb is for powerpc, so of course you do not install it on your x86 system. What you do is that you extract it (dpkg -x, *without* sudo!) to get the files that are in it without installing it. Then you copy the relevant files (executables, etc.) over to your PPC system.

---

### Post by mevun on 2012-10-29
> **IAMTubby said:**
> **A)**Thanks a lot Bachstelze, mevun for your wonderful replies. However, I  would like to get a general how-to-approach while cross compiling for a  PowerPC. I would start with something like this :

1)Download any source version (please see B here as well)
2)extract it
3)do a make without any changes to get errors, but at least you get the makefile log
3)Do ./configure --help to know what environment variables to set
4)Have a look at the makefile log and keep doing a Ctrl+f and find the  path to all the environment variables you get in step4 from the makefile  log.
5)Add all of these paths manually along with ./configure as ./configure CC=/some/new/path/to_the_gcc_capable_of_cross_compiling
6)Should work 



But you say that what environment variables is program- and build-system-dependent. How then do I find out what to set ? Are these mentioned in a file or something ?


. . .


I'll just address the above points..

I think that "any source" should realistically be limited to:
1. C/C++ source code
2. Proven to be built with Gnu C/C++ compiler and libraries for native desktop Linux.
3. Proven to be built with autoconf tools for native desktop Linux.
4. Does not include any kernel code (i.e. is not intended for a kernel  module).
5. Target uses a modern Linux kernel executing on a CPU with MMU (memory management unit).   Just means that the target Linux is same kernel as desktop Linux only with a different CPU.

If your code meets the above criteria, then your "build" environment will be typical of modern desktop Linux and you are also targeting a modern Linux.  As such, the environment variables likely to require defining for cross-compile are things like:  CFLAGS, LDFLAGS, LD_LIBRARY_PATH.  These more or less correspond to specifying the "header include" path and the "library path".  I am not even sure if you need the last one which is more often used at run-time, but I also see configure scripts that seem to use it.

As a counter-example, the cross-compilation I am doing relies on a build system that uses STAGING_DIR as an environment variable.  Of course, I am building for a system that does not meet the no. 2 criteria above.  It uses a special version of the C library called uClib which is optimized for embedded systems.

So I think the steps you outline should more-or-less work, but I am not sure if you simply made a typo for your step 3.  Running "configure" will generate a "config.log" file typically.  So then you look inside that to fix your errors.  I agree you will likely iterate to fix issues as you find them.

---

