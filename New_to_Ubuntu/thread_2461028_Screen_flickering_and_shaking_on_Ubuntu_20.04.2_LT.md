---
title: "Screen flickering and shaking on Ubuntu 20.04.2 LTS"
date: 2021-04-23
forum: New to Ubuntu
---

### Post by eagleshadowgudu1240 on 2021-04-23
I have installed successfully Ubuntu 20.04.2 on my system. But afters using some days, the screen started shaking or flickering or flashing sometimes. Also in some applications some letters were partially visible Like the pic i have posted in which B and G are partially visible. My monitor is all ok as i have tested with my other system. So anyone who solved this type of problem please give any solution, so i can overcome from this issue. Thanks in advance.

---

### Post by wowotiel on 2021-04-23
See thread Graphics issues even after fresh 20.04 install: [https://ubuntuforums.org/showthread.php?t=2460766&page=3](https://ubuntuforums.org/showthread.php?t=2460766&page=3)
And:
I have found out that there is already an bugrapport:
After upgrade to 5.8.0-49/5.8.0-50 with Intel graphics (gen7, Haswell/Ivy Bridge) a lot of glitches render screen unusable
[https://bugs.launchpad.net/ubuntu/+s...8/+bug/1924624]("https://bugs.launchpad.net/ubuntu/+source/linux-meta-hwe-5.8/+bug/1924624")
It looks that it is corrected in kernel 5.8.0-51 which is not released yet.
As said: Kernel 5.8.0-48 and all of the kernels from the 5.4 serie does work good.

---

### Post by broadwaylion2 on 2021-04-24
Yes, I experienced this. I thought it was damage to an on-board video driver cause by my unplugging a VGA monitor without powering down. I took the monitor to my shop and when that worked ok, I put a new video card on the computer and now it works just fine. : )
The reason why I put Ubuntu on this machine was because I could not load windows (for whatever reason--Other forums said that my motherboard was too old) Ubuntu is working just fine. Now I have to learn how to use it. ": )

---

