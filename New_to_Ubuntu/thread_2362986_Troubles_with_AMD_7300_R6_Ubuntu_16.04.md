---
title: "Troubles with AMD 7300 R6 Ubuntu 16.04"
date: 2017-06-04
forum: New to Ubuntu
---

### Post by zcodereaction on 2017-06-04
Hello everyone I have a problem with my graphic card. I'm new Installing ubuntu, I had LMDE and it works perfect my driver package and I played some games on it. I checked some forums 'bout supported devices for my graphic card:

Processor    AMD A10-7300 Radeon R6, 10 Compute Cores 4C+6G, 1896 Mhz, 4 Core(s), 4 Logical Processor(s)

but I founded some troubles with the package "fglrx" installing with Ubuntu with crashes on restart. instead "Xorg" packages is installed with the fglrx binaries.
and I checked a new software called AMDGPUPRO that supports a lot of devices including mine, and I installed that sw and everything ends well, when It says is necessary to restart just don't showed my UI and I must reinstalled Ubuntu.

there's any way to solve this, I mean an another package to install it, I need it because the graphic card driver includes the sound driver, please help me :(

---

### Post by wildmanne39 on 2017-06-04
The fglrx driver does not work in releases past 14.04.1 it can not be installed properly.

If you installed it or changed x.org then that could be the blank screen issue and not the bug that is in the driver.

AMD is working hard on the new driver, it is included in Ubuntu 16.04 AMDGP, I have the AMD 8700 it works good, but it causes my system to freeze at random times, sometimes it is at boot. I run my laptop in virtualbox, but not all amd cards freeze some work very well. 

You can use it with the parameter nomodeset but then the graphic size can not be adjusted, at least I never found a way.

---

