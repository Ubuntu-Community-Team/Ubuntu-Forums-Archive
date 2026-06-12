---
title: "Error while downloading and installing"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by ssb08 on 2012-02-01
i was try to download Ubuntu 11.04 using Wubi software ...in the middle it start showing error drive missing .. i tried to try again /continue but it wont work .. so i  cancel that ... then it completed downloading but it didnt show me start/restart message ..after that when i restarted my laptop then it took some time to boot and after while start showing 
Gave up waiting time for root devices:
-BOOt args(cat/proc/cmdline)
-check root delays
-check root
-missing modules(cat/proc/modules;is/dev)

ALERT! /dev/disk/by-vvid/7ecb-2581 does not exit . droping  to shell ..

I am very first time user of ubuntu ..please help me out

---

### Post by bcbc on 2012-02-01
The 'no disk' problem is probably this: [https://bugs.launchpad.net/bugs/365881](https://bugs.launchpad.net/bugs/365881)

You can click through the message, or try to remove external drives/peripherals (printers, mmc cards) etc. before installing.

I'd try again and this time, don't cancel halfway through rather than try and figure out what went wrong.

---

