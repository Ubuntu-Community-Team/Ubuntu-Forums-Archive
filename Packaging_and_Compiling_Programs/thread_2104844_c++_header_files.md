---
title: "c++ header files"
date: 2013-01-14
forum: Packaging and Compiling Programs
---

### Post by linuxonbute on 2013-01-14
Just realized this should have been in a different area of Development and Programming
I am trying to do some c++ programming. I had a problem and posted here. This solved the problem I had but it was pointed out that I was using the wrong header files. e.g 
I had #include <time.h> where I should have had #include <ctime.h>
and several others.
I am a real beginner with c generally and more so with c++
I have been trying to use SDL as well so I guess I have been trying to run before I can walk so I decided to potter around with some simple coding first but I am stuck.
Problem is as follows:
```

g++ -o graph6 graph6c.cpp `pkg-config --cflags --libs sdl`

```
worked and the program would run but that was with the wrong headers so altering the includes to have ctime.h and cstdlib.h 
caused the compile to fail as the headers could not be found.
I do have g++ at /usr/bin but do not have the headers anywhere.
I ran updatedb as root and then locate ctime.h
but it is not on my system.
Running 12.04 with all updates.
I have tried to find them to install them through the package manager but cannot seem to do so.
Can someone please explain how I can overcome this problem please?
tia

---

### Post by steeldriver on 2013-01-14
The modern C++ standard include files don't have the .h suffix - try 

```
#include <ctime>
```and so on instead - they should be located somewhere like /usr/include/c++/4.6/ctime etc.

---

### Post by avidwan on 2013-01-14
hello....!!!!!!!!Respected experts...

I am new in this forum..

i want to create a website for  c, C++ and [java programming]("http://www.programmingpad.com/") source code..

---

### Post by linuxonbute on 2013-01-14
Well shows I really am new at this.
It compiled fine with that simple change.
I have not found that mentioned anywhere I searched!
Thanks so much.

---

### Post by PGScooter on 2013-01-15
> **avidwan said:**
> hello....!!!!!!!!Respected experts...

I am new in this forum..

i want to create a website for  c, C++ and [java programming]("http://www.programmingpad.com/") source code..

Hi avidwan, welcome to the forum!

You should start a new topic if you have questions.

---

