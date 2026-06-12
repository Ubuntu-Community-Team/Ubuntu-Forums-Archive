---
title: "Severe problem help pls"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by clementchiew on 2013-06-21
ok, i messed up big time. I am a beginner and I have no idea how Linux  works. So I have drives A and B, with A partitioned into 1 and 2, and  installed Ubuntu into 1. so I decided to format drive B (which had my  windows 7) and let 2 be alone (holding Vista). After formatting B, I  booted Ubuntu from my cd ( I installed with it) and wiped out 1 (the one  holding Ubuntu). I used Gpart. and then, I installed Ubuntu into B(used  to be windows 7). After the installation, I cant boot anything at all. I  get the black white screen with grub saying "partition not found" and  then a command expecting "grub rescue> " I need help seriously, I  cant even access my vista now.

---

### Post by TheFu on 2013-06-21
I'm having a hard time following everything and don't feel like making a chart.
Please do this: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and post the results so that someone might be able to help.
If you are impatient, you might attempt a fix with [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) first.

---

### Post by mlentink on 2013-06-21
There are no such things as 'A' and 'B' drives. It might help if you booted up with the Ubuntu-cd, start up GParted and make pictures. But the above advice about running the boot-info script comes first

I certainly do not hope so, but if I understand you correctly you just effectively wiped your disk. And i suppose you don't have backups?

---

### Post by Impavidus on 2013-06-21
Most likely your bios is set to boot from the drive you call A, but by deleting Ubuntu from that drive you broke grub. You installed Ubuntu on drive B, so that should have a valid bootloader now. Get into the bios of your computer and try booting your computer from drive B. If everything went OK during install, you should get a grub menu allowing you to choose between your new Ubuntu installation and Win Vista.

---

