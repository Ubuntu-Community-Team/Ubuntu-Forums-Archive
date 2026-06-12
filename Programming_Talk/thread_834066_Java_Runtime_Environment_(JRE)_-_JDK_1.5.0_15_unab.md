---
title: "Java Runtime Environment (JRE) - JDK 1.5.0_15 unable to determine DST changes"
date: 2008-06-19
forum: Programming Talk
---

### Post by i_am_the_reason on 2008-06-19
Hi,

We are having a strange problem with one of a dev-env boxes that runs on following version of Linux and JRE. The problem is JRE is unable to determine the DST changes as per the set rules, but the system time does changes the moment DST comes into effect and reset when DST ends. We tried to upgrade the DST rules using **tzupdater** but that too didnt work.

[B]Linux 2.6.9-22.ELsmp #1 SMP Sat Oct 8 21:32:36 BST 2005 x86_64 x86_64 x86_64 GNU/LInux

java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_15-b04, mixed mode)


Hardware details are as follows[/B]
Systemboard: Super Micro X6DVL-EG2
Dual Intel Xeon 3Ghz single core
CPU family 15, model 4, stepping 10

Memory: DDR2 ECC/REG 4GB

Hard Drive:
Seagate 250GB(mirror) - 3ware 8006-2LP raid controller

OS: centos 4.1 Kernel: 2.6.9-22.ELsmp

Any help is this regards would be great.

Thanks,
Siddharth

---

