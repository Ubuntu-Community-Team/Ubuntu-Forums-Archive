---
title: "How to do a partition install?"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by linux12 on 2012-05-26
I was trying to us the partition menu from the live cd to install ubuntu outside of Windows so it will run faster (right?) but when I click on the install button, I get a message saying that I didn't specify a root file system or something like that, and to correct it from the partition menu. But aren't I in the partition menu? there was no options like that... should I even bother, or should I just stick to running it in Windows? I don't know how big a difference it will make. Oh yeah, one last thing: I'm trying to install 12.04 LTS.

---

### Post by TheFu on 2012-05-26
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) might help.

You didn't say how much storage you have available, so I'll assume you have lots of free storage on the HDD. You probably need to shrink your Windows partition before getting started, then create an "Extended partition" and 2-3 "Logical partitions" inside that.  Linux runs inside logical partitions just fine and there isn't really any limit to how many you can have.
* Logical partition 1: "/" - 10GB for apps
* Logical partition 2: "swap" - 1-2GB, no more.
* Logical partition 3: "/home" - whatever you want - 10-20GB is usually plenty if you don't keep audio/video media

Logical partitions will usually be named /dev/sda5 - /dev/sda99

Windows can access NTFS storage inside a "Logical partition" just fine, but I don't think Windows can boot from a Logical partition.

---

### Post by Frogs Hair on 2012-05-26
You may want to look at this and there are tutorials for other versions of Windows as well. [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

---

### Post by linux12 on 2012-05-26
Great! I'll look that up!

---

### Post by Curtis6767 on 2012-05-26
> **linux12 said:**
> I was trying to us the partition menu from the live cd to install ubuntu outside of Windows so it will run faster (right?) but when I click on the install button, I get a message saying that I didn't specify a root file system or something like that, and to correct it from the partition menu. But aren't I in the partition menu? there was no options like that...** should I even bother, or should I just stick to running it in Windows? **I don't know how big a difference it will make. Oh yeah, one last thing: I'm trying to install 12.04 LTS.

If you did a WUBI install, which seems to be the case, then the first thing you need to do is go to your Windows install and then to  add/remove programs and then delete Ubuntu from there.

Then reboot and you should go straight to Windows. 

At that point, you'd want to put the Ubuntu disk in your CD tray and reboot, which should take you straight to Ubuntu install process and just follow the instructions in this link:  [http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)

GL

---

