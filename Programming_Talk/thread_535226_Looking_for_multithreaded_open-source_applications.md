---
title: "Looking for multithreaded open-source applications."
date: 2007-08-26
forum: Programming Talk
---

### Post by zvirack on 2007-08-26
Hi,
I am looking for open-source multithreaded applications that use locks for a study i am doing. Any mentioning of such applications for *nix/Windows would be appreciated.

---

### Post by angustia on 2007-08-26
use this:

cat /proc/$(pidof MYPROGRAM)/status | grep Threads


replace MIPROGRAM with the name of any program running in your system

that will tell you the number of threads of that process

now, to know how many mutexes... i don't know, just look at the source code

---

### Post by Ramses de Norre on 2007-08-26
Eclipse, Firefox, Thunderbird, ...

---

