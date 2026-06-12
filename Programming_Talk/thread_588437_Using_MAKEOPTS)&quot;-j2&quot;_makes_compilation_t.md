---
title: "Using MAKEOPTS)&quot;-j2&quot; makes compilation time shorter ?"
date: 2007-10-23
forum: Programming Talk
---

### Post by FredB on 2007-10-23
I was browsing the gentoo manual and I saw something about a strange optimization flag.

Besides -O2 which I try to use for my compilations, I learn about MAKEOPTS flag.

Is this flag make compilation time for big project shorter ?

If I understand well, I have to do a export MAKEOPTS="-j2" for a single core CPU ?

Any feedback ?

Thanks a lot !

---

### Post by CRAY-4 on 2009-11-15
i believe that is right, im doing j3 sine i have dual core

---

### Post by slavik on 2009-11-15
for make -j specifies the number of max concurrent jobs that make will try to use. Usually should 1 more than the number of cores (to completely fill the ready queue). Although I have seen compilation fail where -j >1 was involved.

---

