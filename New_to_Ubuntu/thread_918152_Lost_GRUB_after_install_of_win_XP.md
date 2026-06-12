---
title: "Lost GRUB after install of win XP"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by jamelb on 2008-09-12
So here we go i installed xp on some free space. I have two hard drives and my linux is on the same hard drive as the linux. the linux is the 1st partition on hard drive /dev/hdd1. I can not seem to figure out how to make grub work again. grrrrrrrr

---

### Post by WRDN on 2008-09-12
Follow [this]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows") guide to reinstall GRUB.

---

### Post by aomlives on 2008-09-12
First of all I think something's not right in your sentence, there's too many linux.

I guess what you have to do is follow the instructions in one of the many guides available for this situation, like this one:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

I don't know whether you have any specific problems trying to make this work...

---

### Post by jamelb on 2008-09-12
i followed the guide and it still does not work my linux is not on my 1st drive and i think that is the issue

---

### Post by SuperSonic4 on 2008-09-12
If XP and Linux are on different hdds then it's best to just change at BIOS

If they're on the same disc follow a guide to reinstalling grub

---

### Post by jamelb on 2008-09-12
grub> root (hd1,0)

grub> setup (hd1)

Error 17: Cannot mount selected partition

grub>

---

### Post by handydan918 on 2008-09-12
> **jamelb said:**
> So here we go i installed xp on some free space. I have two hard drives and my linux is on the same hard drive as the linux.
Well, that could be more clear...> 
 the linux is the 1st partition on hard drive /dev/hdd1. I can not seem to figure out how to make grub work again. grrrrrrrr

Even if grub works, windows probably won't. Windows wants to be the first O/S on the first partition on the first disk.  It really is easiest to install windows and then install almost anything else afterward. 
Billy's little O/S has control issues.

---

### Post by caljohnsmith on 2008-09-13
> **handydan918 said:**
> Well, that could be more clear...

Even if grub works, windows probably won't. Windows wants to be the first O/S on the first partition on the first disk.  It really is easiest to install windows and then install almost anything else afterward. 
Billy's little O/S has control issues.
Windows XP can actually be quite happy on any primary partition, not just the first one. And if you go through a little bit of trouble, you can even install Windows to a logical partition and get it booting, but I wouldn't recommend it as it is unnecessary hassle. I certainly agree though that "Billy's little O/S has control issues." :)

Jamelb, which HDD boots on start up? How about booting up your Live CD, and posting the output of the following:
```
sudo fdisk -lu
```
Use the above output to figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Lastly, please post the output of:
```
sudo grub
grub> find /boot/grub/stage1
grub> quit
```

---

