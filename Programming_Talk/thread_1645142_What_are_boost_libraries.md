---
title: "What are boost libraries"
date: 2010-12-14
forum: Programming Talk
---

### Post by c2tarun on 2010-12-14
hi friends,
Can anyone please tell me about boost libraries?
I tried to google it but could not understand is use.

---

### Post by talonmies on 2010-12-14
Boost is a collection of extensions to the C++ standard libraries that provide a lot of additional functionality not currently in the C++ standard - container types, algorithms, portable sockets and other network facility, portable threading, and portable filesystem access, to name but a few.

Most, but not quite all, boost libraries are implemented using C++ templating, so there mostly no external linkage necessary to use Boost.

---

### Post by dwhitney67 on 2010-12-14
> **c2tarun said:**
> ... but could not understand is use.

Boost is definitely not something that a beginner (novice) C++ programmer will need, much less understand.  There are many facets of Boost that I have never used, and probably never will, for lack of a need and/or because I don't understand the poor documentation either.

Some of the features of Boost will be adopted into the C++ standard (C++0x) that is due out sometime during our lifetime (perhaps 2011?).  Hopefully by then there will be ample documentation and examples.

---

### Post by nvteighen on 2010-12-14
Boost predates the (current) C++ '98 Standard, so it includes features that now may seem somewhat useless... but this is because this library was written with a language in mind that's not exactly how C++ looks like now.

As dwhitney67 said, most of the Boost library won't be very useful for a beginner, so don't worry too much. It has some advantages, like e.g. the fact that it's template-based makes the library be very portable (but very slow to compile "against"...).

---

