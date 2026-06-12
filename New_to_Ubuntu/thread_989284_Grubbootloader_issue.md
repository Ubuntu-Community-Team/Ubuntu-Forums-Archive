---
title: "Grub/bootloader issue"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by netbloke on 2008-11-21
Hi everyone

I am an extreme novice when it comes to linux.

I have an old computer that I am swapping to using a solid state drive. I have ubuntu installed on the solid state drive, I did so by using another computer and doing a dual boot.

The problem is when I swapped the drive to computer I wanted it on, it does not have the bootloader set up, it has no idea to look at the solid state drive to load ubuntu.

How do I set up Grub to load this?

Any help would be most appreciated. I have searched high and low and cannot work out what I need to do exactly.

---

### Post by Keen101 on 2008-11-21
we'll it could actually be two problems in one.

1. your hard drive partition might not have the "bootable flag" set.

2. ..and Grub might be installed on your other system.

I recommend using the Gparted live-CD to set you "bootable flag", so the hard drive can read any bootloaders you will install. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

as for installing GRUB, just use the Super Grub Disk to restore Grub. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I think that should fix it just fine.

---

### Post by Michael.Godawski on 2008-11-21
Perhaps this tutorial matches your issue:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you have any questions regarding the "what to do" ask :)

---

### Post by netbloke on 2008-11-21
Thanks Kenn and Micheal!

Your suggestion Micheal was what I needed. It took a little fiddling but it appears I am up and running quite ok.

Just need to work out how to speed thing sup a little now.

All this machine is suppose to do is surf the net and play MP3s.

---

