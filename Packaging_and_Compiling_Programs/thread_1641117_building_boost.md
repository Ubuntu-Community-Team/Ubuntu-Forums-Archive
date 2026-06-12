---
title: "building boost"
date: 2010-12-08
forum: Packaging and Compiling Programs
---

### Post by nearlymagicman on 2010-12-08
Well,

i want to start a project in c++ which will require some Parts of the boost library but unfortunatly my Ubuntu denies me any kind of building the boost libraries.

First i thought it might be a good idea ('cause i actually work on two computers) to build boost on my USB-Stick so i won't have to change my #include paths everytim i change my Computer, but bjam just throws error after error.
Next step was to bjam it in the ("normal") directory /usr/local/boost but it is failing there as well! I don't know why and the official guide isn't any help.

```
failed common.copy /usr/local/lib/libboost_math_tr1.so.1.45.0..
      ...failed common.copy /usr/local/lib/libboost_math_tr1f.so.1.45.0...
...skipped <p/usr/local/lib>libboost_math_tr1f.so for lack of <p/usr/local/lib>libboost_math_tr1f.so.1.45.0...
...failed common.copy /usr/local/lib/libboost_math_c99.so.1.45.0...
...skipped <p/usr/local/lib>libboost_math_c99.so for lack of <p/usr/local/lib>libboost_math_c99.so.1.45.0...
...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.4.3/release/threading-multi/object/enum.o...
.failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.4.3/release/threading-multi/object/function.o...
and so on....
```

I hope any of you have expierenced this problem and is able to help me, because i am clueless. Last time i installed it on an Windows OS and it worked perfectly fine!

---

### Post by SevenMachines on 2010-12-09
Hi.In general i'd say that unless you specifically need the newest boost libraries then just install the repository ones
$ sudo apt-get install libboost-dev

For your build errors, well i dont really use bjam and i dont generally install to /usr/local often but at a guess 'failed common.copy' to /usr/local looks like you dont have permissions to copy there, are you root? maybe something like
$ sudo bjam install

---

