---
title: "Boot error"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by Geunor on 2013-03-08
I have an Advent Modena M201 without Windows 7 Home Premium and partitioned the Hard Drive to install Ububtu. Have forgotten which version of Ubuntu though, sorry. It has been working fine for about 6 months, maybe more. 

But I have turned on the laptop to be greeted with the following message:

error: unknown filesystem.
grub rescue>

I don't have a live CD. I do have another laptop with Windows and Linux but it doesn't have a CD/DVD writer.

I will need a step by step as I have no idea about all the code sorry. 

Thank you for your time and help.

---

### Post by cortman on 2013-03-08
You should create a bootable USB drive with Boot-Repair.
In Windows on your other laptop, download and install [Linux LiveUSB Creator]("http://www.linuxliveusb.com/"). Create a bootable USB drive with it per instructions [here]("https://help.ubuntu.com/community/Boot-Repair") and/or [here]("http://ubuntuforums.org/showthread.php?p=10871917#post10871917") and use Boot repair to fix grub.
Hope this helps.

---

