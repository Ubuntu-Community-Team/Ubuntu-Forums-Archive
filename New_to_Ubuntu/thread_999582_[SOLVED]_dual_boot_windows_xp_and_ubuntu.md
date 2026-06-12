---
title: "[SOLVED] dual boot windows xp and ubuntu"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by djyoung4 on 2008-12-02
I have been reading up on having a dual boot system of windows xp and ubuntu.  I already have a ubuntu live CD 8.10 and have read a bunch of things about setting it up.  I have a hpdv2000 laptop with AMD Turion 64x2 and 1GB RAM.  was just wondering if anybody had a similar setup and if they have tried dual booting and if so how it went.  I have seen that it might not work on some computers so any advice or insight to this would be great.

---

### Post by nhasian on 2008-12-02
i have a dv6500 and dv9500.  its a different architecture but you shouldnt have any problems either as its a standard hp laptop.

---

### Post by werDZiPiLE on 2008-12-02
try

[http://wubi-installer.org/](http://wubi-installer.org/)

download it. run it. and it installs everything. restart and it will already be configured as a dual-boot.

---

### Post by utnubuuser on 2008-12-02
hello werDZiPile

If you go that route,  does Wubi install ubuntu in it's own partition, or as file in Windows?

---

### Post by bumanie on 2008-12-02
> **utnubuuser said:**
> hello werDZiPile

If you go that route,  does Wubi install ubuntu in it's own partition, or as file in Windows?

It is viewed as a windows file, however there is a way of transferring it to its own partition later and then removing it from windows. Look [here]("http://lubi.sourceforge.net/lvpm.html") for more information.

---

### Post by djyoung4 on 2008-12-02
does Wubi run ubuntu like in a virtual machine because I have played around with virtual machines and I always have problems with resources being eaten up too fast and my comp comes almost to a stand still.  The Live CD i have runs slow too but that is only because it is running off a cd which is understandable.

---

### Post by Paqman on 2008-12-02
> **djyoung4 said:**
> does Wubi run ubuntu like in a virtual machine

No, it just creates virtual partition to install Ubuntu into, instead of a real partition. That virtual partition looks like a file on the Windows partition. When Ubuntu boots, only Ubuntu runs, it doesn't require any part of Windows to be running, so it will use the same resources as Ubuntu installed the traditional way.

---

