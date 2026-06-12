---
title: "Yet another pthread linker problemer"
date: 2014-02-21
forum: Programming Talk
---

### Post by hurra on 2014-02-21
Hello experts

I want to try google test framework for c++ on ubuntu. I'm trying to build a very simple test (stripped down from one of the samples supplied by google from gtest). 

My build line and output looks like:
g++  -o "HelloUnitTest" ./src/HelloUnitTest.o  ./Test/TestMain.o -pthread -lgtest -lgtest_main
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgtest.so: undefined reference to `pthread_key_create'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgtest.so: undefined reference to `pthread_getspecific'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgtest.so: undefined reference to `pthread_key_delete'
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/libgtest.so: undefined reference to `pthread_setspecific'
collect2: error: ld returned 1 exit status

I have read all posts I could find about this, and tried lpthread vs pthread, linking libraries before and after the object files, linking libpthread as a static library, and many others. 

Any idea what I can be doing wrong?

ps. running on ubuntu 13.10, 64 bits

---

### Post by spjackson on 2014-02-22
I can't seem to get the .so to work either. If you force use of the static library
```

g++  -o "HelloUnitTest" ./src/HelloUnitTest.o  ./Test/TestMain.o -pthread -l:libgtest.a -l:libgtest_main.a

```
then that seems to work.

---

### Post by hurra on 2014-02-24
Brilliant :) Thanks, that solved by problem. Any explanation why this is?

---

