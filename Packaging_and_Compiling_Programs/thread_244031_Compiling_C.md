---
title: "Compiling C"
date: 2006-08-25
forum: Packaging and Compiling Programs
---

### Post by epq on 2006-08-25
I have just recently installed Ubuntu, but have been programming in C on Linux for some years in college.
I thought C came naturally on Linux but I just wrote a basic programme and on trying to compile it, gcc -o test test.c, was informed that the gcc command is not contained in bash.
Is there something I need to do to activate it?
I searched Add/Remove Applications and found nothing obvious.
Thanks

---

### Post by MrHorus on 2006-08-26
Yes.

```
apt-get install build-essential
```

---

