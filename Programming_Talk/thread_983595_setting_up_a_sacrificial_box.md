---
title: "setting up a sacrificial box"
date: 2008-11-15
forum: Programming Talk
---

### Post by swappo1 on 2008-11-15
Hello,

I am setting up a sacrificial computer to learn how to build drivers in linux.  I am using the online version of Linux Device Drivers, 3rd edition from O'reilly.  

The computer I have is an old pentium II with a 10 gig HDD and 64 MB of RAM.  I was looking into using DSL but it only uses kernel version 2.4 and I need version 2.6.  I've heard DSL-N uses kernel version 2.6.  Has anybody ever used this?  I need something small, although the only thing I will be doing on this machine is driver programming.  I will need gcc and gedit and probably some other tools I am not yet aware of.

Any ideas as to which distro I should use?  I will also have to download a "mainline" kernel from kernel.org.  I would appreciate any advice anybody has in helping me get started.

---

### Post by iponeverything on 2008-11-15
Ubuntu 8.10 server should install fine. 

Just add the development packages that you need. You can pull the kernel from kernel.org.  Though I would grab the source with apt-get.

---

