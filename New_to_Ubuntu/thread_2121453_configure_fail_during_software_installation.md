---
title: "configure fail during software installation"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by littlewenwen on 2013-03-01
Dear All

The ubuntu version I am using is 12.10. I am trying to install a program id3lib (from [http://id3lib.sourceforge.net);](http://id3lib.sourceforge.net);) I have downloaded the source code and unpacked; however when I tried to configure, I got the following message (sorry, it is very long); and I could not make the "make" command work. I believe something must be wrong during the configure, but I don't know what is wrong. Can someone help me and point out what is wrong during the configure? how to make the installation successful ?

Thank you very much.


```
ll@litt:~/Downloads/id3lib-3.8.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
ll@litt:~/Downloads/id3lib-3.8.3$ 
```

---

### Post by Mr. Shannon on 2013-03-01
First, is there a reason why the version of libid3 in the repositories will not work for you?  Installing from source should always be a last resort as it will not be updated later on by the package manager and is often difficult to remove.

Second, it seems to be failing a lot of checks for compilers.  You probably need to install build-essential with:

```
sudo apt-get install build-essential
```

---

### Post by littlewenwen on 2013-03-02
Thank you very much for helping me. I didn't realize that there is libid3 in the repositories (I just checked; yes, libid3 is actually already installed; silly me). 

Actually I am still learning linux and i want to take this chance to know more about linux. May I ask what is "build-essential"? Does it mean that, once "build-essential" is installed, I have no more problems in my future software installation? Thank you for educating me.

---

### Post by Mr. Shannon on 2013-03-02
If you install all you software from the repositories using apt-get or the software center then you will not need "build-essential", unless you are a programmer.  "build-essential" is a package that will pull in the basic tools needed to compile Debian packages (it also installs gcc, g++, and make which are needed to compile C and C++ code such as libid3).  It will not make it so that all software will compile.  When compiling from source you must meet all required build and run dependencies.  Since the package manager is not involved in the compilation process it cannot add these automatically.  So you have to install all dependencies manually, usually with apt-get.  To get information on "build-essential" you can run in a terminal:
```
apt-cache show build-essential
```

However, as stated earlier, unless absolutely necessary you should install software with the built in package management system.  That is apt-get on the command line or the Software Center if you prefer a graphical interface.

---

### Post by littlewenwen on 2013-03-02
Thank you very much for your instructions.

---

