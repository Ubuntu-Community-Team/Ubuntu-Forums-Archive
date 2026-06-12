---
title: "How can I clean or decrease swap space ?"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by realmadridfan on 2012-01-14
Hello guys , First of all my English is not that good so I hope that you understand what I am going to write , I am a new Ubuntu user . My problem is that I almost have no disk space available to use , and I want to add some of swap partition space to Ubuntu disk space , How can I do this ??

Thanks in advance

---

### Post by Double.J on 2012-01-14
> **realmadridfan said:**
> Hello guys , First of all my English is not that good so I hope that you understand what I am going to write , I am a new Ubuntu user . My problem is that I almost have no disk space available to use , and I want to add some of swap partition space to Ubuntu disk space , How can I do this ??

Thanks in advance

Hi there, 

To adjust partitions on your primary hard drive, you should really do it from the live cd.

Just boot it up, select try no install and boot gparted from the desktop.

in gparted you can resize your partitions - if you are going to do anything involving your root or other system mounted partitions, be sure to back up everything first!

Depending on whether the live cd uses the Hdd's swap, you may need to right click the swap partition and click swapoff ot modify it.

A couple of things to note - swap by default is unlikely to be very large - despite traditional recommendations that it be twice your ram, with such high ram levels nowadays, 2 GB is common.

Don't forget that linux makes use of your swap space even while you're well within your amount of physical RAM to get the best performance from your system, and hibernate needs swap space to copy your RAM to to function - no swap, no hibernate.

I'd suggest that unless you've set up an very large swap partition by accident, more space could be freed by deleting unnecessary files, or tarballing ones that you need to hang on to, but never access. :)

---

