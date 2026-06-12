---
title: "makeunder chroot and multi cpu"
date: 2011-03-23
forum: Packaging and Compiling Programs
---

### Post by MikeKle on 2011-03-23
I have made a chroot environment like it suggested here "https://help.ubuntu.com/community/BasicChroot" and everything works fine, except that "make" command does not utilise all 4 cores from my cpu, and "make -j 5" does not make the trick too... I have /proc  binded, and under chroot the /proc/cpuinfo is correct. 

Compiling some heavy stuff on one core takes nights... while without chroot I was able to make it in few hours... 

What have I missed?

---

