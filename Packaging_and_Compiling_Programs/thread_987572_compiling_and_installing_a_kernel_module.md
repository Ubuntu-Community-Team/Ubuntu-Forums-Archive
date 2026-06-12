---
title: "compiling and installing a kernel module"
date: 2008-11-19
forum: Packaging and Compiling Programs
---

### Post by 999alfred on 2008-11-19
I had long been a Slackware user, but switched over to Ubuntu a couple od years ago and all had been fairly smooth until I installed 8.04. Then I had a problem.

The hard drive DMA was no longer working and the system got really slow on accessing disks. using hsparm -d1 <device> gave a not supported error. I did some research and found this difference in the config file for 2.6.24
# CONFIG_BLK_DEV_VIA82CXXX is not set
while the previous 2.6.17 has
CONFIG_BLK_DEV_VIA82CXXX=m
and since I have a VIA KT333CE chipset I need that module to use the chipset IDE DMA .

I have never built anything like this under Ubuntu. So how is the easiest way to build and install only the needed module under Ubuntu?

tj

---

### Post by kcode on 2008-11-27
> **999alfred said:**
> 
I have never built anything like this under Ubuntu. So how is the easiest way to build and install only the needed module under Ubuntu?



Hope this thread helps you.
[http://ubuntuforums.org/showthread.php?t=933477]("http://ubuntuforums.org/showthread.php?t=933477")

---

