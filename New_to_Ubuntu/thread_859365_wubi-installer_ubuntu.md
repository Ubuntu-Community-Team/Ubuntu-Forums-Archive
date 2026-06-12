---
title: "wubi-installer ubuntu"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by texas.chef94 on 2008-07-14
Ubuntu loaded via the installer and I have encountered no difficulty but at boot when the choice is windows or ubuntu and I choose ubuntu a warning flashes to the effect that there is a unrecognized partition table for 81 I believe is what I am seeing and I can use windows fdisk tool to rebuild.
Is this critical or can I live with it. 

Allen

---

### Post by avtolle on 2008-07-14
Here is a link to the Wubi Guide: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) 

You are likely going to be able to live with it, but take a look at the link and see if there's a better answer.

---

### Post by smo0th on 2008-07-17
> **texas.chef94 said:**
> Ubuntu loaded via the installer and I have encountered no difficulty but at boot when the choice is windows or ubuntu and I choose ubuntu a warning flashes to the effect that there is a unrecognized partition table for 81 I believe is what I am seeing and I can use windows fdisk tool to rebuild.
Is this critical or can I live with it. 

Allen

restart into wind0ze and type ```
chkdsk /f d:
``` in cmd, assuming that drive d is where you have your wubi installation. Reboot and you should be able to use ubuntu again :)

---

