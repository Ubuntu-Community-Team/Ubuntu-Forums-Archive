---
title: "passphrase is needed to access encrypted data on ScanDisk SSD i100 24GB"
date: 2015-07-22
forum: New to Ubuntu
---

### Post by houmingc on 2015-07-22
I am using ASUS ZenBook UX31A. I format and reinstall ubuntu instead.
On the left side bar, when i click the Harddisk.
Message below appear.

The passphrase is needed to access encrypted data on ScanDisk SSD i100 24GB
I do not remember the password. What remedy should i resort to ?
[h=1][/h]

---

### Post by Vladlenin5000 on 2015-07-22
The whole point of encryption is: No password/passphrase, no data.

---

### Post by houmingc on 2015-07-22
Can reformat the SSD ?

---

### Post by lisati on 2015-07-22
> **houmingc said:**
> Can reformat the SSD ?

It should be possible to reformat, but you are likely to lose any data that you haven't made a backup of.

---

### Post by houmingc on 2015-07-23
How to reformat the SSD?
ubuntu boot is currently in normal HDD, not inside SSD and this causes some boot problem.
Since i have remove window and install ubuntu, might as well make it complete.

---

### Post by houmingc on 2015-07-25
I am using ASUS ZenBook UX31A. I format and reinstall ubuntu instead.
 On the left side bar, when i click the SSD Harddisk.
 Message below appear.
 The passphrase is needed to access encrypted data on ScanDisk SSD i100 24GB



I can't remember the SSD ScanDisk passphrase when i enter it during purchase of my laptop.

The OS is initially window 8.1. When i do a GParted. 

/dev/sda1   fat32     /boot/efi

/dev/sda2   ext2       /boot

/dev/sda3   lvm pv   ubuntu-kylin-vg



I suspect, ASUS is confused, which boot to execute, also window 8.1 boot is still inside. How to verify?
What is efi stand for?

---

### Post by Geoffrey_Arndt on 2015-07-25
EFI = extensible firmware interface.   Some hardware will list it as UEFI = unified extensible firmware interface.

EFI/UEFI is what has replaced the traditional PC BIOS that used MS-MBR disk partitioning protocol.   MS-MBR = Microsoft Master Boot Record (a disk/data mgmt protocol).

It's well worth the time to read thru the pages in below link so your chance of installing (and using) Ubuntu correctly are much improved.

It also wouldn't hurt to go to youtube and watch a few videos on Ubuntu installs, and then watch a few (3-5) for the partitioning program (gparted).

[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI


[/URL]

---

### Post by NoWayWin8 on 2015-07-27
In GParted - did you look on the menu bar under GParted > Devices and see if it lists another drive there besides /dev/sda?

---

### Post by HermanAB on 2015-07-27
All you can do is to take a head-ache tablet and try to remember the passphrase.  Tylenol3 is best for improving memory in the short term, but even a common cold remedy will help you and may save the day.

---

