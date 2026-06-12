---
title: "Error compiling libXdamage-1.1"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Nasa01 on 2008-09-23
Hi

I'm trying to compile libXdamage-1.1 (and I've tried libXdemage-1.1.1) to give libGL.so access to 'XDamageAdd'.

first I ran the configure script:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for X... yes
checking for XDAMAGE... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating xdamage.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

To me it seemed fine.
Then I typed make, and this is where I get stuck... The compilation stops and gives me this error:

make  all-recursive
make[1]: Entering directory `/home/Nasa/cern/libXdamage-1.1.1'
Making all in src
make[2]: Entering directory `/home/Nasa/cern/libXdamage-1.1.1/src'
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include/X11/extensions   -I/usr/pkg/include    -g -O2 -MT Xdamage.lo -MD -MP -MF ".deps/Xdamage.Tpo" -c -o Xdamage.lo Xdamage.c; \
        then mv -f ".deps/Xdamage.Tpo" ".deps/Xdamage.Plo"; else rm -f ".deps/Xdamage.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include/X11/extensions -I/usr/pkg/include -g -O2 -MT Xdamage.lo -MD -MP -MF .deps/Xdamage.Tpo -c Xdamage.c  -fPIC -DPIC -o .libs/Xdamage.o
Xdamage.c: In function 'XDamageAdd':
Xdamage.c:372: error: 'xDamageAddReq' undeclared (first use in this function)
Xdamage.c:372: error: (Each undeclared identifier is reported only once
Xdamage.c:372: error: for each function it appears in.)
Xdamage.c:372: error: 'req' undeclared (first use in this function)
Xdamage.c:377: error: 'sz_xDamageAddReq' undeclared (first use in this function)
Xdamage.c:377: error: expected expression before ')' token
Xdamage.c:377: error: 'X_DamageAdd' undeclared (first use in this function)
make[2]: *** [Xdamage.lo] Error 1
make[2]: Leaving directory `/home/Nasa/cern/libXdamage-1.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/Nasa/cern/libXdamage-1.1.1'
make: *** [all] Error 2

What is wrong and how can I fix this?

---

### Post by nowshining on 2008-09-23
it should be in the repos - open up a terminal and enter: sudo apt-get install libxdamage1

---

