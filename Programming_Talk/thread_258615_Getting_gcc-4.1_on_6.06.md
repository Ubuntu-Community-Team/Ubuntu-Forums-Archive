---
title: "Getting gcc-4.1 on 6.06"
date: 2006-09-16
forum: Programming Talk
---

### Post by AntonioFabio82 on 2006-09-16
Hi all.
As the topic: how can I get the gcc-4.1 suite on ubuntu-6.06?
I can't get gcc compilation from sources 'out of the box', so I was wondering if someone has some hints before playing with ./configure options...

Specifically, I need the 4.1 version of the fortran compiler 'cause some serious bugs were fixed only in the 4.1 series.

---

### Post by X.Cyclop on 2006-09-16
```
sudo apt-get install build-essential gfortran-4.0
``` :wink:

---

### Post by AntonioFabio82 on 2006-09-17
> **X.Cyclop said:**
> ```
sudo apt-get install build-essential gfortran-4.0
``` :wink:

I already have build-essential and the full gcc-4.0 suite. This doesn't help in 'automatic' compilation of the 4.1 gcc version

---

