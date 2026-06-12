---
title: "How to Update GCC?"
date: 2005-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by bigblop on 2005-03-28
I currently have gcc version 3.3.4.  I have read that the latest version is 3.4.3 at:

[http://www.gnu.org/software/gcc/](http://www.gnu.org/software/gcc/)

I have found a installtion guide at:
[http://gcc.gnu.org/install/](http://gcc.gnu.org/install/)

But that contains 6 rather comprehensive steps. Is it really necessary to understand all this just to upgrade gcc?

Is there some simpler way to upgrade and still get all the necessary files??

---

### Post by oracledarren on 2005-03-28
Upgrade to Hoary that currently is running version 4

---

### Post by bigblop on 2005-03-28
Well I would like to stay with Warty, and would also like to know in general how to update the gcc compiler

---

### Post by jdong on 2005-03-28
GCC 3.4.x and 4.x break C++ ABI (binary compatibility) which means a complete system recompile....

Changing a system-wide compiler is no joking matter -- it's a TON more serious than changing the kernel or X server!!


You can "slot" a GCC 3.4 install -- I think "gcc-3.4" is in Universe for Warty and Hoary.

---

