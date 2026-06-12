---
title: "Autotools problem"
date: 2012-11-29
forum: Programming Talk
---

### Post by vanangamudi on 2012-11-29
here is my source tree

[FONT=Courier New]projectroot/
     |
     +-configure.ac
     |
     +-build/ 
     |      |
     |      +-build-aux/
     +-lib/
     |       |
     |       +-shaderutils.h
     |       +-shaderutils.c
     |       +-Makefile.am
     +-helloworld/
              | |
| +----triangle.c 
| +----Makefile.am
|
|[/FONT]

and here are the Makefile.am and configure.ac

FILE: configure.ac
```

AC_INIT([triangle], [1.0], [selva.developer@gmail.com])
AC_CONFIG_AUX_DIR([build/build-aux])
AM_INIT_AUTOMAKE([foreign -Wall -Werror])
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_RANLIB
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES( [Makefile
                                            lib/Makefile
                                            helloworld/Makefile]
                                         )
AC_OUTPUT

```FILE: Makefile.am
```

SUBDIRS = helloworld lib

```FILE: helloworld/Makefile.am
```

AM_CFLAGS = -I$(srcdir)/lib
LDADD = ../lib/libshaderutils.a
bin_PROGRAMS = triangle
triangle_SOURCES = triangle.c

```FILE: lib/Makefile.am
```

lib_LIBRARIES = libshaderutils.a 
libshaderutils_a_SOURCES = shaderutils.c shaderutils.h
include_HEADERS = shaderutils.h

```and when I run the autotools the following error is thrown
```

$ cd /media/arulmozhi/programming/experiments/opengl/
arulmozhi@koparakesari:/media/arulmozhi/programming/experiments/opengl
$ autoreconf -i
arulmozhi@koparakesari:/media/arulmozhi/programming/experiments/opengl
$ cd build/
arulmozhi@koparakesari:/media/arulmozhi/programming/experiments/opengl/build
$ ../configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
configure: creating ./config.status
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating helloworld/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
arulmozhi@koparakesari:/media/arulmozhi/programming/experiments/opengl/build
$ make
make  all-recursive
make[1]: Entering directory `/media/arulmozhi/programming/experiments/opengl/build'
Making all in helloworld
make[2]: Entering directory `/media/arulmozhi/programming/experiments/opengl/build/helloworld'
**make[2]: *** No rule to make target `../lib/libshaderutils.a', needed by `triangle'.  Stop.**
make[2]: Leaving directory `/media/arulmozhi/programming/experiments/opengl/build/helloworld'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/arulmozhi/programming/experiments/opengl/build'
make: *** [all] Error 2
arulmozhi@koparakesari:/media/arulmozhi/programming/experiments/opengl/build
$ 

```where did I go wrong. "No rule to make target libshaderutils.a"  why is this happening

---

