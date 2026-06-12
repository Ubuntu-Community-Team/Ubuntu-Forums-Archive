---
title: "shared hdd for dual boot"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by natman on 2013-05-18
Hi I have a 160 gb hard disk and a 500gb hard disk ( currently unformatted, its brand new ), and i want to dual boot win7 with ubuntu ( win7 is currently on the 160gb disk ). My question is this, i would like the 500gb to be shared by both OS's, how should i format it? ext3/4 ntfs, fat32? which is best

Also i was thinking of the following break down:
80 for win 7
20 for \
60 for \home

Would that allow me plenty of space to install loads of programs in Ubuntu?

---

### Post by Paqman on 2013-05-18
A shared data partition should be NTFS. Both systems can read & write to that fine.

20GB for your root partition is plenty, go forth and install!

---

### Post by oldfred on 2013-05-18
If not already dual booting, I might put Ubuntu on the 500GB drive. Then Windows still has it boot loader on its drive and can be directly booted if you have issues with the Ubuntu drive and vice-versa. I prefer that each drive be bootable without any other drive. But data can be on any drive.

If installing to a second drive you do have to use manual install or Something Else. Then you can specify partitions and importantly specify which drive has grub2's boot loader in the MBR. Then in BIOS you change to boot from Ubuntu drive.

 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
      
 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by ajgreeny on 2013-05-18
If you are going to put all your data files (docs, music, videos, photos etc, etc) on the shared partition that should be NTFS as Paqman says.  If you want a separate /home partition as you suggest, but it is not going to have data files on it, 60GB is far too large, and you would probably manage with no more than 4GB or 5GB which must be a Linux filesystem, eg ext4.

 The shared partition, NTFS, can not hold your /home partition as it is not possible to have the Linux permissions needed for /home on an NTFS filesystem.

So your root partition of 20GB is fine, your /home of 60GB too large, and the Win7 I can not help with, as I have not used windows since XP, and now do not use it at all.  The rest can be the shared NTFS data partition.

Oldfred is, quite simply, the best person I know of to advise you on these things and I fully agree with his comment about keeping the OSs on separate physical disks as it makes the bootloader less of a problem if something should go wrong.

---

### Post by Paqman on 2013-05-18
> **ajgreeny said:**
> If you want a separate /home partition as you suggest, but it is not going to have data files on it, 60GB is far too large, and you would probably manage with no more than 4GB or 5GB which must be a Linux filesystem, eg ext4.


Depends, there is some stuff that goes in /home that isn't just data and that can chew up space. Virtual machines and software installed into Wine leap to mind. You'll also might want some data, such as your 5GB of Ubuntu One space, to stay on your /home partition. Having a nice big /home can't hurt and gives a lot of flexibility.

---

### Post by ajgreeny on 2013-05-18
> **Paqman said:**
> Depends, there is some stuff that goes in /home that isn't just data and that can chew up space. Virtual machines and software installed into Wine leap to mind. You'll also might want some data, such as your 5GB of Ubuntu One space, to stay on your /home partition. Having a nice big /home can't hurt and gives a lot of flexibility.

I have no doubt that you are right about this, but as I don't use either I did not even consider such things.

Good call!

---

### Post by BigZ1981 on 2013-05-18
> **Paqman said:**
> Depends, there is some stuff that goes in /home that isn't just data and that can chew up space. Virtual machines and software installed into Wine leap to mind. You'll also might want some data, such as your 5GB of Ubuntu One space, to stay on your /home partition. Having a nice big /home can't hurt and gives a lot of flexibility.
How well does Wine work with Windows programs?  I'm looking to drop my dual boot & just stick with kubuntu, but there are still some things I run that are only available in Windows, like SW:TOR & emulators which are holding all my saves.

---

