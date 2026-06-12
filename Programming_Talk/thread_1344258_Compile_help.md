---
title: "Compile help"
date: 2009-12-02
forum: Programming Talk
---

### Post by Cardale on 2009-12-02
I am trying to compile something, but I can't and I don't know what or how to do what ever I should do.

checking for sys/wait.h that is POSIX.1 compatible... no
checking fcntl.h usability... no
checking fcntl.h presence... no
checking for fcntl.h... no


Any idea?

---

### Post by dwhitney67 on 2009-12-02
It appears that you have not installed any development tools on your system; hence run the following:
```

sudo apt-get install build-essential

```
You can find additional help in the stickies of this forum.

---

### Post by Cardale on 2009-12-02
I already have it installed and I get this error.

How do I make my distro posix1 compatible.

build another way get this

gcc: unrecognized option '-qversion'
gcc: no input files

---

### Post by dwhitney67 on 2009-12-02
Linux, and that implies Ubuntu, is a POSIX-compliant OS.

Please verify the following if you can, and report back the output of each command:
```

gcc --version

```
```

ls -l /usr/include/fcntl.h

```

---

### Post by Cardale on 2009-12-02
gcc (Ubuntu 4.4.1-4ubuntu8) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

-rw-r--r-- 1 root root 7474 2009-10-07 02:09 /usr/include/fcntl.h

ahh that is probably it....it doesn't have permision... :o ?

Is my compiler not pointed to the right file????

---

### Post by dwhitney67 on 2009-12-02
> **Cardale said:**
> gcc (Ubuntu 4.4.1-4ubuntu8) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

-rw-r--r-- 1 root root 7474 2009-10-07 02:09 /usr/include/fcntl.h

ahh that is probably it....it doesn't have permision... :o ?

Permissions are fine; don't muck with them.


How are you trying to build your s/w package?  Please indicate where you obtained the package, and how you are building it.

---

### Post by Cardale on 2009-12-02
This is the file 

[http://www.nwnx.org/uploads/media/linnwnx2-2.5.3-rc1.tar.gz](http://www.nwnx.org/uploads/media/linnwnx2-2.5.3-rc1.tar.gz)

I am just following there read me.

This is the page incase you want to look before you download the file
[http://www.nwnx.org/index.php?id=nwnx2](http://www.nwnx.org/index.php?id=nwnx2)

---

### Post by Cardale on 2009-12-02
This is another version I tried supposedly easier

[http://www.bfme.uni.cc/globaldomain/nwnx_easy.tar.gz](http://www.bfme.uni.cc/globaldomain/nwnx_easy.tar.gz)

---

### Post by dwhitney67 on 2009-12-02
I downloaded the tar-ball.  I attempted to build it as follows:
```

./configure
make clean
make

```
The configure stage...
```

./configure
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for fcntl.h... yes
checking for netinet/in.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for sys/ioctl.h... yes
checking for sys/mman.h... yes
checking for sys/socket.h... yes
checking for sys/time.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... (cached) yes
checking for size_t... yes
checking for stdlib.h... (cached) yes
checking for working malloc... yes
checking for bzero... yes
checking for getspnam... yes
checking for inflateEnd in -lz... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating db/Makefile
config.status: creating mnx/Makefile
config.status: creating functions/Makefile
config.status: creating hashset/Makefile
config.status: creating config.h
config.status: config.h is unchanged

```
The compilation failed; reasons...
```

 make
g++  -mcpu=i386   -c -o nwnx2lib.o nwnx2lib.cpp
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
nwnx2lib.cpp: In function ‘void Configure()’:
nwnx2lib.cpp:362: warning: deprecated conversion from string constant to ‘char*’
nwnx2lib.cpp:369: warning: deprecated conversion from string constant to ‘char*’
nwnx2lib.cpp:374: error: ‘atoi’ was not declared in this scope
nwnx2lib.cpp:379: error: ‘atoi’ was not declared in this scope
nwnx2lib.cpp: In function ‘void Log(int, const char*, ...)’:
nwnx2lib.cpp:446: warning: format not a string literal and no format arguments
nwnx2lib.cpp:452: warning: format not a string literal and no format arguments
nwnx2lib.cpp: In constructor ‘startstop::startstop()’:
nwnx2lib.cpp:477: warning: format ‘%p’ expects type ‘void*’, but argument 2 has type ‘long unsigned int’
nwnx2lib.cpp:477: warning: format ‘%p’ expects type ‘void*’, but argument 3 has type ‘long unsigned int’
make: *** [nwnx2lib.o] Error 1

```
It would appear that this s/w package is outdated and/or just poorly developed.  Is there not a newer version?

---

### Post by Cardale on 2009-12-02
Here is one from source forge

[http://sourceforge.net/projects/apsnwnx/files/APS_NWNX%20Linux/Linux%20NWNX%202.5.3-rc1/linnwnx2-2.5.3-rc1.tar.gz/download]("http://sourceforge.net/projects/apsnwnx/files/APS_NWNX%20Linux/Linux%20NWNX%202.5.3-rc1/linnwnx2-2.5.3-rc1.tar.gz/download")

but it is the same version number i believe.

---

### Post by Cardale on 2009-12-02
```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by FULL-PACKAGE-NAME configure VERSION, which was
generated by GNU Autoconf 2.64.  Invocation command line was

  $ ./configure --prefix=/home/myusername/Games/nwn --enable-debug

## --------- ##
## Platform. ##
## --------- ##

hostname = computer-domain
uname -m = x86_64
uname -r = 2.6.31-14-generic
uname -s = Linux
uname -v = #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/X11R6/bin


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2266: checking for gcc
configure:2282: found /usr/bin/gcc
configure:2293: result: gcc
configure:2522: checking for C compiler version
configure:2531: gcc --version >&5
gcc (Ubuntu 4.4.1-4ubuntu8) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2542: $? = 0
configure:2531: gcc -v >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu8' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
configure:2542: $? = 0
configure:2531: gcc -V >&5
gcc: '-V' option must have argument
configure:2542: $? = 1
configure:2531: gcc -qversion >&5
gcc: unrecognized option '-qversion'
gcc: no input files
configure:2542: $? = 1
configure:2564: checking for C compiler default output file name
configure:2586: gcc  -g -mcpu=i386  -g  conftest.c  >&5
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
conftest.c:1: error: CPU you selected does not support x86-64 instruction set
configure:2590: $? = 1
configure:2627: result: 
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "FULL-PACKAGE-NAME"
| #define PACKAGE_TARNAME "full-package-name"
| #define PACKAGE_VERSION "VERSION"
| #define PACKAGE_STRING "FULL-PACKAGE-NAME VERSION"
| #define PACKAGE_BUGREPORT "BUG-REPORT-ADDRESS"
| #define PACKAGE_URL ""
| /* end confdefs.h.  */
| #include <stdio.h>
| int
| main ()
| {
| FILE *f = fopen ("conftest.out", "w");
|  return ferror (f) || fclose (f) != 0;
| 
|   ;
|   return 0;
| }
configure:2633: error: in `/home/kinggoddard/Downloads/linnwnx2':
configure:2637: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_prog_ac_ct_CC=gcc

## ----------------- ##
## Output variables. ##
## ----------------- ##

CC='gcc'
CFLAGS=''
CPP=''
CPPFLAGS='-g -mcpu=i386 '
CXX=''
CXXFLAGS=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
EXTRAPLUGINDIRS=''
GREP=''
LDFLAGS='-g '
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
OBJEXT=''
PACKAGE_BUGREPORT='BUG-REPORT-ADDRESS'
PACKAGE_NAME='FULL-PACKAGE-NAME'
PACKAGE_STRING='FULL-PACKAGE-NAME VERSION'
PACKAGE_TARNAME='full-package-name'
PACKAGE_URL=''
PACKAGE_VERSION='VERSION'
PATH_SEPARATOR=':'
SHELL='/bin/bash'
ac_ct_CC='gcc'
ac_ct_CXX=''
bindir='${exec_prefix}/bin'
build_alias=''
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host_alias=''
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='/home/myusername/Games/nwn'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME "FULL-PACKAGE-NAME"
#define PACKAGE_TARNAME "full-package-name"
#define PACKAGE_VERSION "VERSION"
#define PACKAGE_STRING "FULL-PACKAGE-NAME VERSION"
#define PACKAGE_BUGREPORT "BUG-REPORT-ADDRESS"
#define PACKAGE_URL ""

configure: exit 77
```

---

### Post by dwhitney67 on 2009-12-03
Try following these steps:
```

autoconf
./configure
make clean
make

```
If you do not have autoconf on your system:
```

sudo apt-get install autoconf

```
Btw, as I mentioned in my other post, even if you make it successfully through the 'configure' stage, the code will still *not* compile.  Of course, feel free to fix the compile errors; they do not seem that difficult to do.

P.S.  The package appears to be released in 2004.  GCC has undergone many changes since then.

---

### Post by Firenux on 2009-12-04
The Sourceforge version is woefully out of date, the plugins don't even work any more with the software this is designed to interface with. Conversely, the nwnx_easy package is very recent (latest version I released only a month ago). This software is under active development by a small number of people, but unfortunately the coding (especially some of the older code) isn't quite standards compliant and fails when compiling under GCC 4.4. GCC 4.3 works perfectly.

I'm not actually the one who made any of this: the nwnx_easy package is simply designed to be well-documented (a goal which is only partially achieved at the moment due to time constraints) and easy to compile (which it is if you're using the compatible GCC 4.3). The only alternative currently is to get the whole lot from SVN, apply a couple of patch files to address some issues currently lurking at head and then cross your fingers with ./configure and make (confusingly, make install is useless for some of the package, and moves the files somewhere that may not exist for other parts... it's a mess). With nwnx_easy, you just check the README to see if you've got the required packages, then run install.sh which checks for the required packages and then automagically builds it.

But the code is a bit fail in places, and that's one of the things I'm working on along with more documentation for the next tarball release.

---

### Post by Cardale on 2009-12-05
How do I setup 32bit and 64bit programming environments?  I want to do this as cleanly as possibly.  I guess one of the reasons besides the newer version of gcc is I am using a 64bit os.

---

