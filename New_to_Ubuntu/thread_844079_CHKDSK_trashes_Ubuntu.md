---
title: "CHKDSK trashes Ubuntu"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by sisyphus10 on 2008-06-29
I posted earlier today about getting the latest NVidia driver loaded into Ubuntu 8.04. After finally getting that resolved, I had to reboot my computer. It has Vista Ultimate installed and Ubunta was intalled on it via WUBI. As part of the boot sequence going into Vista, unusually a CHKDSK was performed, and several errors said to be corrected.

A little later, I rebooted once again to get into Ubuntu, but it would not start up. Instead I got a message telling me to type in Help and I would get a list of all commands. Very helpful (NOT!) None of them seemed appropriate. So I rebooted and this time tried the Ubunta (recover) mode. Same thing.

I am very reluctant to have to start all over since it took 30 hours just to get to the point where I had a reasonable screen resolution. I am more inclined at this stage of having wasted an enormous amount of time even getting the OS in apparent working order, to simply uninstall it and revert to Vista. However, I would be most interested to learn if there is any simple way of recovering the Ubuntu installation to what it was...

---

### Post by 3rdalbum on 2008-06-29
Vista's CHKDSK has damaged the file that contains your Ubuntu installation. Any disk-checking utility can damage any file, as I've found out several times, but of course your Ubuntu installation is a big file and therefore attracts a slightly greater chance of it being damaged by CHKDSK.

Why not install Ubuntu into a real partition? That way it can't be damaged by anything that Vista does. You'll probably find that things are more inclined to "just work", and that the system goes a little faster.

---

### Post by Gone fishing on 2008-06-29
This seems odd as CHKDSK should only change your Windows partitions, however, it seems that either the Linux partitions have been removed? or grub on the mbr has been damaged.

So boot up on the ubuntu live cd go to system > Administration > Partition editor and just see if the Linux partitions are there. If they are then follow these instructions to repair grub:

[http://ubuntuforums.org/showthread.php?t=799763](http://ubuntuforums.org/showthread.php?t=799763)

---

### Post by TWO on 2008-06-29
Yeah, +1 for installing Ubuntu under it's own partition. Much less hassle!

---

### Post by sisyphus10 on 2008-06-29
Thanks for all those replies. The funny thing was that I had installed Ubuntu on a totally different drive to my C:\ system drive. So I was totally surprised that Chkdsk, which as far as I am aware only checked C:\ drive, should have had any effect on the F:\ drive where Ubuntu is located...

I should have been more clear, though. I am sure it is not a corrupt Grub. When I boot the computer, I am presented with the usual choice of Windows or Ubuntu. I choose the latter. I get the usual choice of Ubuntu, Ubuntu (Recover) etc. I choose Ubuntu and the first splash screen appears. But after that, I get the message about typing Help.

---

### Post by Gone fishing on 2008-06-29
Sorry my mistake - WUBI Ubuntu inside windows in a file - Like the old BeOS personal addition installer. OK yes I'd install Ubuntu properly on its own partitions.

Use gparted to make some space then allow Ubuntu to install into the free space.

---

### Post by hyper_ch on 2008-06-29
if you like Ubuntu, why don't you do a real install?

---

### Post by nowshining on 2008-06-29
if it took u 30hrs then the second time should be less since this time u'll know what to do and where to go, etc...

---

