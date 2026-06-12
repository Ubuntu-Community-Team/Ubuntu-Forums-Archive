---
title: "make: *** [main.o] Error 1"
date: 2014-01-06
forum: Packaging and Compiling Programs
---

### Post by ajitnair90 on 2014-01-06
I am using a third party software to compile. When i bulid i am getting this error. the console showed as below

21:16:21 **** Incremental Build of configuration Debug for project d ****
make all 
Building file: ../main.C
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0-std=c++11 -MMD -MP -MF"main.d" -MT"main.d" -o "main.o" "../main.C"
g++: error: argument to '-fmessage-length=' should be a non-negative integer
make: *** [main.o] Error 1

should i configure anything to run  wiithout this error??

---

### Post by kajoky on 2014-01-07
It looks like there should be a space between -fmessage-length=0 and -std=c++11

---

