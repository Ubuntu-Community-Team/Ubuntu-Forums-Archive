---
title: "Mograso-modelling tool in ubuntu 10"
date: 2010-05-25
forum: Packaging and Compiling Programs
---

### Post by austinvishal on 2010-05-25
im  not able to make the make check and make output are shown below
vishal@ubuntu:~/Desktop/mograso-1.0.1$ make check
Making check in src
make[1]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src'
Making check in besselAmosOctave
make[2]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave'
make[2]: Nothing to be done for `check'.
make[2]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave'
Making check in common
make[2]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make wronskian besselp1
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
g++ -g -O2 -O1 -o wronskian testWronskian.o ./libcommon.a ../besselAmosOctave/libbessel.a -lpthread -lxml2
source='testBesselP1.cpp' object='testBesselP1.o' libtool=no \
depfile='.deps/testBesselP1.Po' tmpdepfile='.deps/testBesselP1.TPo' \
depmode=gcc3 /bin/bash ../../depcomp \
g++ -DHAVE_CONFIG_H -I. -I. -I../.. -O1 -I/usr/include/libxml2 -g -O2 -O1 -c -o testBesselP1.o `test -f 'testBesselP1.cpp' || echo './'`testBesselP1.cpp
g++ -g -O2 -O1 -o besselp1 testBesselP1.o ./libcommon.a ../besselAmosOctave/libbessel.a -lpthread -lxml2
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make check-TESTS
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
FAIL: wronskian
PASS: besselp1
===================
1 of 2 tests failed
===================
make[3]: *** [check-TESTS] Error 1
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make[2]: *** [check-am] Error 2
make[2]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src'
make: *** [check-recursive] Error 1


make output

vishal@ubuntu:~/Desktop/mograso-1.0.1$ make
make all-recursive
make[1]: Entering directory `/home/vishal/Desktop/mograso-1.0.1'
Making all in src
make[2]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src'
Making all in besselAmosOctave
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/besselAmosOctave'
Making all in common
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/common'
Making all in MoGraSoTK
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoTK'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoTK'
Making all in MoGraSoUITK
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoUITK'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSoUITK'
Making all in MoGraSo
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSo'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src/MoGraSo'
make[3]: Entering directory `/home/vishal/Desktop/mograso-1.0.1/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src'
make[2]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1/src'
make[2]: Entering directory `/home/vishal/Desktop/mograso-1.0.1'
make[2]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1'
make[1]: Leaving directory `/home/vishal/Desktop/mograso-1.0.1'

---

