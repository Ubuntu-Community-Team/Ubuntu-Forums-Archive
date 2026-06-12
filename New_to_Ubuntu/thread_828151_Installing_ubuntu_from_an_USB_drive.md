---
title: "Installing ubuntu from an USB drive"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Edgewalker_001 on 2008-06-13
Is there a way to transfer the installation program to an USB drive and install from there instead of from a CD?

I'm asking because I have a computer that is currently lacking a DVD drive, and I want to switch from windows XP to Ubuntu

---

### Post by daberger on 2008-06-13
the easiest way to switch from xp to ubuntu is with wubi (just google it) but yes there is a way to install it from a usb drive unfortunately you would need another computer with a cd drive.

---

### Post by Edgewalker_001 on 2008-06-13
If other computers is the problem then I don't have one XD

I've got three other computers, all fully equipped with DVD drives/burners and two of them are running ubuntu

---

### Post by hyper_ch on 2008-06-13
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by jimv on 2008-06-13
Why, yes there is way.  I installed on my laptop with a USB stick with the help of this guide:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by KingTermite on 2008-06-13
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

USB drive version of linux and tutorials/helpers on making usb persistent versions of Ubuntu and many other linux distros as well.

---

### Post by Edgewalker_001 on 2008-06-13
Well, I downloaded the boot image, but how do I find out which device my USB stick is mapped to?

---

### Post by jimv on 2008-06-13
> **Edgewalker_001 said:**
> Well, I downloaded the boot image, but how do I find out which device my USB stick is mapped to?

I'd go into a terminal and type "sudo fdisk -l".  This will show all of the partitions on all of your disks.  It'll will likely be the disk with just 1 partition...probably /dev/sdb or something like that.

---

