---
title: "Installing MCMC++ on 32 and 64 bit Ubuntu 8.10"
date: 2009-03-26
forum: Packaging and Compiling Programs
---

### Post by bademeister on 2009-03-26
Hey,

yesterday I tried to install an C++ library for Markov chain Monte Carlo (MCMC) simulations called mcmc++ found here [http://darwin.eeb.uconn.edu/mcmc++/mcmc++.html]("http://darwin.eeb.uconn.edu/mcmc++/mcmc++.html"). I ran into a few problems which took me a while to figure out, so I thought I post it here in case somebody has the same difficulties. I am by no means a C++ expert, so what I so might be plain wrong, proceed at your own risk ;)

after unzipping and running configure 
```
./configure
```
and then 
```
make
```
the compiler gives an error stating
```
lot.cpp:52: error: ‘CHAR_BIT’ was not declared in this scope

```
To take care of this, add
```
#include <limits.h>
``` 
to src/lot.cpp

On a 64 bit  system the next problem is that the line
```
BOOST_STATIC_ASSERT(sizeof(long) * CHAR_BIT == 32); // 32 bit longs required

```
throws an error (this explicitly checks for a 32bit environment, just ignore on 32bit).
I have added the option -m32 to the CXXFLAGS in all the makefiles (in src/ test/ and the base directory). Furthermore i needed to install libc6-dev-i386, otherwise the compiler would complain that gnu/stubs-32.h was missing.

The next thing I ran into was that the compiler complained about the "main" function being missing from all the *.cpp files in the test/ directory:
```
g++  -g -O2 -L../src  -o DataTableTest  DataTableTest.o -lmcmc++ -lstdc++ -lboost_unit_test_framework 
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
```

Apparently from boost 1.34 on, the two constants "BOOST_TEST_DYN_LINK" and "BOOST_TEST_MAIN" need to be defined when defining testcases which are linking dynamic libraries. After including these in all *test.cpp files:
```
#define BOOST_TEST_MAIN
#define BOOST_TEST_DYN_LINK
``` 
make ran through.

One more thing, if you want to install it using checkinstall, you need to give the --fstrans=no option.

Cheers
Paul

---

### Post by spamalot on 2009-03-26
Glad that you solved it. I gave up on that one a while ago and created my own framework instead:

[http://sites.google.com/site/erwannrogard/cpp-software](http://sites.google.com/site/erwannrogard/cpp-software)

I will be adding more and more realistic models overtime, starting with survival analysis, very soon. Happy to help if you have an interest.

---

