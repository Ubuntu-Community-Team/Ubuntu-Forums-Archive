---
title: "Shared memory, IPC, and C++"
date: 2006-07-14
forum: Programming Talk
---

### Post by nebc on 2006-07-14
I currently have a program in C++ that takes images from a webcamera and then does a bunch of fancy calculations on them. However, these calculations are expensive and I need to be able to break them up into separate processes and put them across multiple CPUs (possibly across a network so the whole thing needs to be as platform independent as possible).  I've done some basic research into this issue and have come across ACE and the Apache Portable Runtime projects as potential solutions.

All I really want to do is make the images I'm getting from the webcamera accessible as read-only memory to multiple processes.  

Has something like this already been solved and if so, where?  I've poked around but not found anything.  Any advice on what I should do/where I should look would be greatly appreciated.

-NebC

---

### Post by LordHunter317 on 2006-07-14
Networking will require special (read: different) handling from the local machine.

Instead of using processes, I'd just use POSIX threads and then all your memory within the process is shared.

---

### Post by thumper on 2006-07-14
If you are wanting to distribute bits of it, then your problem fits the grid computing domain.  Take a look at [ICE](http://www.zeroc.com).

---

