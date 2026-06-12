---
title: "is g++ removed from ubuntu 8.04"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Hirashgeff on 2008-06-04
i cant find g++ in my new system why is that
even in package manager
Help Me please

---

### Post by SteveNorman on 2008-06-04
```
sudo aptidute install g++

sudo apt-get build-essentials
```

what are you typing to compile? it should be there

gcc filname.c for c files
g++ filename.cpp for c++ files

---

### Post by stchman on 2008-06-04
> **Hirashgeff said:**
> i cant find g++ in my new system why is that
even in package manager
Help Me please

g++ is installed by default in Ubuntu.  You will need to install build-essential as the header files are not installed.

---

