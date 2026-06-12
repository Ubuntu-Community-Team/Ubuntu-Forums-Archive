---
title: "libtool not detected"
date: 2010-03-16
forum: Packaging and Compiling Programs
---

### Post by sanpoonam on 2010-03-16
I m trying to install a modified NS2 package.

While trying to install it, the following error occurs 
```
poonam@poonam-desktop:~/bftsim/src/P2$ make
make  all-recursive
make[1]: Entering directory `/home/poonam/bftsim/src/P2'
Making all in eventLoop
make[2]: Entering directory `/home/poonam/bftsim/src/P2/eventLoop'
make[3]: Entering directory `/home/poonam/bftsim/src/P2'
make[3]: Leaving directory `/home/poonam/bftsim/src/P2'
if @LIBTOOL@ --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/include -I../p2core -I../../../EXECS/include -I../../ns/common -I../../ns -I../../tclcl -I../../otcl -I../../include  -DBOOST_DATE_TIME_POSIX_TIME_STD_CONFIG -g -O2 -MT libp2eventLoop_la-loop.lo -MD -MP -MF ".deps/libp2eventLoop_la-loop.Tpo" -c -o libp2eventLoop_la-loop.lo `test -f 'loop.C' || echo './'`loop.C; \
    then mv -f ".deps/libp2eventLoop_la-loop.Tpo" ".deps/libp2eventLoop_la-loop.Plo"; else rm -f ".deps/libp2eventLoop_la-loop.Tpo"; exit 1; fi
/bin/sh: @LIBTOOL@: not found
make[2]: *** [libp2eventLoop_la-loop.lo] Error 1
make[2]: Leaving directory `/home/poonam/bftsim/src/P2/eventLoop'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/poonam/bftsim/src/P2'
make: *** [all] Error 2

```It seemed at first that libtool package was not installed, so I checked in synaptic package manager, but following packages were already installed
```
libtool        : 2.2.6a-4
libtld7        : 2.2.6a-4
libtld7-dev  : 2.2.6a-4
```I found the following line in the makefile, which seems to be the root of problems
```
LIBTOOL = @LIBTOOL@
```What does this @LIBTOOL@ mean? Does it refer to some environment variable?

---

### Post by gmargo on 2010-03-16
Either something went wrong with the configure, or you didn't run the ./setup script.  Follow the steps in the ../compile script.  I was able to compile bftsim-v2.tar.gz (from [http://bftsim.mpi-sws.org/](http://bftsim.mpi-sws.org/)) on 8.04 Hardy.

The LIBTOOL line in src/P2/Makefile reads:
```

LIBTOOL = $(SHELL) $(top_builddir)/libtool

```

---

### Post by sanpoonam on 2010-03-19
thanks a million...
This problem bugged me many more makefiles. Now I've managed to install it in ubuntu 9.10.

---

