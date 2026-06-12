---
title: "What 12.04 Libraries for C++ development using FLTK"
date: 2012-06-26
forum: Programming Talk
---

### Post by UncleRoy on 2012-06-26
I have fresh installed ubuntu 12.04.

What  Software Libraries are needed to make FLTK code  work properly ?
Ubuntu Software Centre offered no FLTK only FLUID.  This offered no extra libraries needed as it did in 11.10.

Thanks in advance.

---

### Post by MG&amp;TL on 2012-06-26
As far as I know, USC only offers graphical apps now.
If you want libraries:

```
apt-cache search fltk
```

should give you a list of packages relevant to fltk.

---

### Post by MadCow108 on 2012-06-26
libfltk1.3-dev or libfltk1.1-dev will probably give you everything you need

---

