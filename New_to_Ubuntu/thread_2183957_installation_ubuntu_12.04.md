---
title: "installation ubuntu 12.04"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by swipisnt on 2013-10-27
hello there. just simple question what does it mean istall along with win 7 and inside win7? i make new ext2 partition  and have option inside win7. or just go to the 'Something Else' and choose ext2 partition and install ubuntu? coz i want to have both win and ubuntu.
Thank you

---

### Post by tomearp on 2013-10-27
Hello,

If I try and install Ubuntu onto a machine that is already running Windows 7 then I am presented with the following screen: [http://i.imgur.com/PxIV7SS.png](http://i.imgur.com/PxIV7SS.png)

The first option will install Ubuntu and configure the machine to dual-boot.
The second option will **delete the contents of the hard disk** and install **only** Ubuntu.

It sounds like you want the first option. If you select the first option you will then be presented with a screen (see here: [http://i.imgur.com/q9z1y6i.png](http://i.imgur.com/q9z1y6i.png)) where you can choose which hard disk to install Ubuntu on. If you have a separate, second hard disk that you want to install on you can select it here. Or if you want to install it onto the same physical disk as your Windows 7 installation you can resize the existing partition to make some space for Ubuntu.

Hope this helps :)

---

### Post by Impavidus on 2013-10-27
Installing inside Windows means wubi. Don't use it, it will be discontinued. The easiest way to instal is to use windows tools to shrink the windows partition, leaving the disk space unallocated (or just take an empty drive), boot from the Ubuntu live disk and click "install alongside". I recommend you use ext4 instead of ext2. It's more modern and reliable. If you already made a Linux partition, use manual partitioning ("sometihng else").

---

### Post by fantab on 2013-10-27
> **swipisnt said:**
> hello there. just simple question what does it mean istall along with win 7 and inside win7? i make new ext2 partition  and have option inside win7. or just go to the 'Something Else' and choose ext2 partition and install ubuntu? coz i want to have both win and ubuntu.

You've already make 2 ext2 partitions. Yes, you are right, you must choose "Something Else" and install ubuntu to the parition. When installing reformat the ext2 partition as ext4.

Before you install Ubuntu make a *Windows Repair Disc*, if you haven't already.

---

### Post by swipisnt on 2013-10-27
anyway thanks for help now. i fakt up my bootable system and cant start up my win7 (lol) even i cant install win7 with installation dvd(cant find hard drive). good that i can boot ubuntus from usb :)

---

### Post by fantab on 2013-10-27
These things happen. They've happened to most of us. This is how we all learn.

Try to rescue all your Important DATA with Ubuntu USB. Once all important data is safe, you can re-install both windows and ubuntu. 
Let us know if you run into more trouble or if you need more help.

---

### Post by swipisnt on 2013-10-27
everything good now. first i cant install windows from installation dvd disk coz HDD was gone (somehow). but i install ubuntus full and then win7. everything allrigh now. i have just 1 question (for now) i have 600gb free space (1partition) then i installed ubuntu it makes 2 x 300gb and one of them i can see in my computer (in win7) other can see just in disk management. so that secret partition is for ubuntu OS? :)
 thank you guys!

---

### Post by fantab on 2013-10-27
Windows CANNOT see Linux partitions. While Linux/Ubuntu can read and write to Windows partition.
A word of _Caution_: Don't use Windows tools to manage Linux partitions and vice versa. Windows Partitions MUST be managed with Window's tools and Linux partitions with Linux tools.

Glad you got your machine up and running.

---

### Post by swipisnt on 2013-10-27
thank you for answer.

---

