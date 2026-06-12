---
title: "Cross-compile from Windows to Ubuntu"
date: 2013-02-14
forum: Packaging and Compiling Programs
---

### Post by eSPiYa on 2013-02-14
I'm using linux for more than 5 years now, most of the time is using Debian, and Ubuntu desktop on my laptop(currently dead) for testing/compiling.

Having a Windows 7 workstation at work and Windows 8 for gaming and development at home, don't have enough disk-space to make a virtual Ubuntu; is it possible to cross-compile and create DEB package from a Windows machine to an Ubuntu server?

Currently, my server on Amazon(AWS) has only 512mb RAM(free-tier) and building the latest Mono Framework(3.0.3) takes more than 2 hours and sometimes it freezes.

I'm still not a hardcore Ubuntu user, so please bear with me. Thanks!

---

### Post by coldraven on 2013-02-14
if you have the money it might be easier to buy another hard drive.
The you could dual boot or just run Ubuntu in Wubi* or VirtualBox**.

*I don't know anything about Wubi, I have never used it.
**VirtualBox is easy to use, even I can do it :)

---

### Post by tgalati4 on 2013-02-14
How did your laptop die?  I don't know of a method to cross-compile.  Sounds like you need an external disk with an Ubuntu install on it that you can take back and forth.  Find another laptop or repair yours.  I couldn't go that long without a real linux installation.  That's like being on a cruise ship without power.  For 6 days.  In poop.

---

### Post by eSPiYa on 2013-04-16
> **coldraven said:**
> if you have the money it might be easier to buy another hard drive.
The you could dual boot or just run Ubuntu in Wubi* or VirtualBox**.

*I don't know anything about Wubi, I have never used it.
**VirtualBox is easy to use, even I can do it :)
I did this before, when I still have too much disk space; but as of now I can't and money is a little bit an issue.

> **tgalati4 said:**
> How did your laptop die?  I don't know of a method to cross-compile.  Sounds like you need an external disk with an Ubuntu install on it that you can take back and forth.  Find another laptop or repair yours.  I couldn't go that long without a real linux installation.  That's like being on a cruise ship without power.  For 6 days.  In poop.
Most probably a motherboard issue. It is an old Compaq laptop, and can't spare more resources just for a compiler.

I saw several tools for cross-compiling from Linux to Windows, and thought there's already a way to do the other way around through Cygwin or any similar emulator without consuming too much resources. Having a virtual-Ubuntu server always end up sparing 8GB of precious disk space, purchasing extra HDD is luxury right now because of the price; aftermath of flood somewhere in south-east asia(I think it is Thailand).

---

