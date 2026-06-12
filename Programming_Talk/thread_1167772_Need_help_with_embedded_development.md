---
title: "Need help with embedded development"
date: 2009-05-23
forum: Programming Talk
---

### Post by Mad Fish on 2009-05-23
I have trouble with my multi-threaded network application (HTTP file server) when I try to run it on my router (ASUS WL-500gP, running OpenWrt Kamikaze 8.09).
It just segfaults for unknown reason on operator new() call. In ubuntu and windows the same code worked perfectly.

I'm looking for people, that are experienced with embedded development.
Is it uClibc problem?

Need help!!

---

### Post by jpkotta on 2009-05-23
I've never played with OpenWrt, but I have done some uClinux stuff.  What I remember from it was that there is no fork() and it's easy to smash the stack.  There is some linker option that sets the size of the stack (it must be set before run time).

[http://docs.blackfin.uclinux.org/doku.php?id=uclinux-dist:debugging_applications#stack_checking](http://docs.blackfin.uclinux.org/doku.php?id=uclinux-dist:debugging_applications#stack_checking)

---

### Post by Mad Fish on 2009-05-23
I've tried to play with stack sizes with "ulimit -s", and by setting stack sizes for threads with pthread_attr_setstacksize(). Nothing helpes. Crashes are unpredictable.

---

