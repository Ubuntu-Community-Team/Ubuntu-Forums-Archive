---
title: "a little help in cross compiling"
date: 2008-06-18
forum: Programming Talk
---

### Post by koda on 2008-06-18
hi all!
i need a cross compiler for a reseach/project activity at school, 
and i wanted to go into the details of the process, so i followed this guide
[http://dev.gentoo.org/~vapier/CROSS-COMPILE-GUTS](http://dev.gentoo.org/~vapier/CROSS-COMPILE-GUTS)

however when it came to the glibc the (in)famous error about the -mlong-double-128

I even tried to recompile the gcc with the configuration flag --with-long-double enabled, but this has sorted no effect :(

any ideas of what could resolve this problem?
thanks a lot!
Koda

---

### Post by Lau_of_DK on 2008-06-18
> **koda said:**
> 
any ideas of what could resolve this problem?
thanks a lot!
Koda

This might be totally useless advice, depending on how far you are in your project:

If its still a possibility, switch to Qt4.~ - Its very easily crosscompiled with MinGW and their own little qmake. Has always compiled without a hitch for me on both Linux and Windows.

/Lau

---

