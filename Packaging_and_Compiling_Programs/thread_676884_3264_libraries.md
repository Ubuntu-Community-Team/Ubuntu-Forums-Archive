---
title: "32/64 libraries"
date: 2008-01-24
forum: Packaging and Compiling Programs
---

### Post by spamalot on 2008-01-24
Hi All,

I am trying to install mcmc++ ([http://darwin.eeb.uconn.edu/mcmc++/mcmc++-1.2.tar.gz](http://darwin.eeb.uconn.edu/mcmc++/mcmc++-1.2.tar.gz)) using ./configure and make (see error below). The culprit is the following line of code in file lot.cpp:52

namespace lot_conditions {
BOOST_STATIC_ASSERT(sizeof(long) * CHAR_BIT == 32); 
}

I suspect this has to do with 64bits. Please help. (also posted at X86_64 yesterday, where's the best place to post this?).

er@ubuntu:/usr/local/mcmc++$ sudo make
Making all in src
make[1]: Entering directory `/usr/local/mcmc++/src'
if g++ -DPACKAGE_NAME=\"mcmc++\" -DPACKAGE_TARNAME=\"mcmc++\" -DPACKAGE_VERSION=\"1.2\" -DPACKAGE_STRING=\"mcmc++\ 1.2\" -DPACKAGE_BUGREPORT=\"kent@darwin.eeb.uconn.edu\" -DPACKAGE=\"mcmc++\" -DVERSION=\"1.2\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FLOOR=1 -DHAVE_POW=1 -DHAVE_SQRT=1 -DHAVE_EXPM1=1 -DHAVE_ISNAN=1 -I. -I/home/er/Documents/downloads/software/mcmc++-1.2/src -I.. -DNDEBUG -I/usr/local/boost_1_34_1 -g -O2 -MT libmcmc___a-lot.o -MD -MP -MF ".deps/libmcmc___a-lot.Tpo" -c -o libmcmc___a-lot.o `test -f 'lot.cpp' || echo '/home/er/Documents/downloads/software/mcmc++-1.2/src/'`lot.cpp; \
then mv -f ".deps/libmcmc___a-lot.Tpo" ".deps/libmcmc___a-lot.Po"; else rm -f ".deps/libmcmc___a-lot.Tpo"; exit 1; fi
/home/er/Documents/downloads/software/mcmc++-1.2/src/lot.cpp:52: error: invalid application of ‘sizeof’ to incomplete type ‘boost::STATIC_ASSERTION_FAILURE<false>’ 
make[1]: *** [libmcmc___a-lot.o] Error 1
make[1]: Leaving directory `/usr/local/mcmc++/src'
make: *** [all-recursive] Error 1

---

### Post by geraldm on 2008-01-26
try adding a header to the file lot.cpp: ?
#include <sys/types.h>

Gerald

---

### Post by bademeister on 2009-03-25
Dear spamalot,

did you resolve the problem? I am having the same one, running ubuntu 8.10, 64-bit. 

thanks
bademeister

---

### Post by bademeister on 2009-03-26
Ok, so I finally figured it out (there were a few more problems...) and posted the solution [here]("http://ubuntuforums.org/showthread.php?t=1106877").

---

