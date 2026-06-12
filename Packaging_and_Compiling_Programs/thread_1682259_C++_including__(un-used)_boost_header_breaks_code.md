---
title: "C++ including  (un-used) boost header breaks code?"
date: 2011-02-05
forum: Packaging and Compiling Programs
---

### Post by cthulhu_54 on 2011-02-05
Hi!
I'm trying to implement the boost thread functions to my code, but it wont compile, not even with a simple "hello world, I'm a thread"-function in it.

however, the "hello world" function compiles by it self (so I have the right libs and *.so), but if there is other code in the main-function it stops compiling.

it finaly got to the point where I uncommented everyting that have anything with boost to do, and I got that to compile/not-compile when I comment/uncomment this line:

```
#include <boost/thread/thread.hpp>
```

does that make sense?

Any reply would be greatly appreciated.

---

### Post by SevenMachines on 2011-02-05
Can you post code, compile command and error. Including/un--including that header shouldnt break anything. As long as libboost1.42-dev or equivalent is actually installed and on the system or manually included paths of course

---

### Post by cthulhu_54 on 2011-02-07
Hi!
Thank you for replying, and after spending some 12 hours trying to understand this I think I've resolved at least that issue. Turns out the answer to my question is Yes, it does break my code!

I sat and copy pasted different parts of my code to see what was causing the trouble, and it was two other include headers that f:ed me so badly. Excluding them makes boost threads compile!

The headers in question were the ones form the book Numerical Recipes by William H press (3ed), which is somewhat of the bible in computational physics, and numerical methods, (well, not forgetting Leslie Lamport.)

So should I report this issue some where?

---

### Post by SevenMachines on 2011-02-07
> **cthulhu_54 said:**
> So should I report this issue some where? If its a bug in ubuntu packages, report it to launchpad, else report upstream if you think its a bug. Since i dont have a copy of the book i dont know whats causing the problem and if its a bug or not

---

### Post by MadCow108 on 2011-02-07
what exactly happens?
a linker error or compile error?
are you using gcc 4.5?
there is a linking "bug" with boost in gcc 4.5 caused by new linking flag defaults in ubuntu. But that threads is affected is new to me.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=602959](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=602959)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=593876](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=593876)

---

