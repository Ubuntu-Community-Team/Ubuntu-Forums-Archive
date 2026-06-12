---
title: "Compiling BFTsim"
date: 2013-01-27
forum: Packaging and Compiling Programs
---

### Post by vinzenzo on 2013-01-27
Hi,

I am trying to install BFTsim found here:

[http://bftsim.mpi-sws.org/]("http://bftsim.mpi-sws.org/")

but when I am trying to run the compile script, I get all kinds of errors.. after installing some packages I am now stuck with:

```
make[1]: Leaving directory `/home/takis/Simulators/bftsim/src/P2'
rm: cannot remove `config.cache': No such file or directory
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking dependency style of g++... (cached) gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking dependency style of gcc... (cached) gcc3
checking for flex... no
checking for lex... no
checking for bison... no
checking for byacc... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
configure: error: cannot run /bin/bash ./config.sub
make  all-recursive
make[1]: Entering directory `/home/takis/Simulators/bftsim/src/P2'
Making all in eventLoop
make[2]: Entering directory `/home/takis/Simulators/bftsim/src/P2/eventLoop'
if /bin/sh ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/include -I../p2core -I../../../EXECS/include -I../../ns/common -I../../ns -I../../tclcl -I../../otcl -I../../include  -DBOOST_DATE_TIME_POSIX_TIME_STD_CONFIG -g -O2 -MT libp2eventLoop_la-loop.lo -MD -MP -MF ".deps/libp2eventLoop_la-loop.Tpo" -c -o libp2eventLoop_la-loop.lo `test -f 'loop.C' || echo './'`loop.C; \
        then mv -f ".deps/libp2eventLoop_la-loop.Tpo" ".deps/libp2eventLoop_la-loop.Plo"; else rm -f ".deps/libp2eventLoop_la-loop.Tpo"; exit 1; fi
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include -I../p2core -I../../../EXECS/include -I../../ns/common -I../../ns -I../../tclcl -I../../otcl -I../../include -DBOOST_DATE_TIME_POSIX_TIME_STD_CONFIG -g -O2 -MT libp2eventLoop_la-loop.lo -MD -MP -MF .deps/libp2eventLoop_la-loop.Tpo -c loop.C  -fPIC -DPIC -o .libs/libp2eventLoop_la-loop.o
loop.C:13:22: fatal error: iostream.h: No such file or directory
compilation terminated.
make[2]: *** [libp2eventLoop_la-loop.lo] Error 1
make[2]: Leaving directory `/home/takis/Simulators/bftsim/src/P2/eventLoop'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/takis/Simulators/bftsim/src/P2'
make: *** [all] Error 2

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Error: Unable to compile "P2"

```

any ideas?

---

### Post by MadCow108 on 2013-01-28
this particular error can be fixed by replacing 
#include <iostream.h>
with
#include <iostream>
in loop.C

but expect more issues, that iostream.h is used indicates it is very old software. iostream.h should not be used since 1998.

---

