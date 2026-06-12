---
title: "Installation problem"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by manna on 2008-08-06
i'm facing a weird problem installing ubuntu 7.04 as well as 7.1 and even kubuntu 7.1 in my system. its configuration is-
[*]Pentium Dual Core E2140 (1.6 GHz)
[*]Intel DG965RY Motherboard
[*]1 GB Twinmos RAM
[*]250 GB SAMSUNG SATA2 HDD (SP2504)
[*]LiteOn DVD-ROM

After booting from the live cd, when i click start installation, the process begins as expected until it hangs when the partition editor is started. it hangs at exactly 46 percent completion. i even tried with another sony dvdrom but same thing happened. what could be the problem?? pls find an answer somebody.

---

### Post by bobnutfield on 2008-08-06
I am not sure why it fails on partitioning, but I have seen this problem before when another OS was formerly on the drive.  I have experienced it in the past, and I solved it by running the live cd, or using a live version of Gparted, and formatting the partition to ext3 prior to attempting to install.

---

