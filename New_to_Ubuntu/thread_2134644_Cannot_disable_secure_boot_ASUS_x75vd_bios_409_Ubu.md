---
title: "Cannot disable secure boot ASUS x75vd bios 409 Ubuntu 12.10 UEFI mode"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by Nzo99 on 2013-04-11
Hey guys, this is my first post here thus i'm sorry in advance if I do something totally wrong. 

My problem: I'm trying to install ubuntu 12.10 64-bit on a 64-bit Windows 8 laptop (ASUS X75VD) which I upgraded from WIN7 when I got it initially. I'm using a live usb that I created using Lili USB creator and boot from it to then install ubuntu onto my hard drive. It is a UEFI motherboard and I cannot for the life of me get access to the important settings in BIOS like secure boot, fastboot, and legacy mode. Now that being said, when I try to boot from my liveusb I can only do so in legacy mode (not uefi). When I try to boot from uefi, it just skips over it and goes to the next boot priority (even if I only set up my BIOS to boot from the USB - it just redirects to the BIOS setup page). 

I found these possible problems while searching over 10hours online to remedy my problem:
-Update BIOS to newest version: done and still no visible options to disable secure boot, etc..
-Set master, user, and admin password in BIOS to enable those 'hidden' options: done and still no luck.
-Install in legacy mode (which I was able to do) onto the same partition as windows8 (since 12.10 is uefi compatible) and run boot-repair: done and boot-repair will not allow me to run the recommended repair. It says that I have attempted to install a version of ubuntu that is not uefi-compatible (the install was confirmed to have been done in legacy mode) and to choose one that was (even though 12.10 is suppose to be uefi compatible-but since I installed it in legacy mode I'm assuming it's not capable to install grub when trying to boot two completely different firmware: BIOS vs UEFI).

Anyways, if anyone has ANY possible suggestions on how to either access the secure boot options inside my BIOS that are hidden OR recommend how to install inside legacy mode and somehow format the partitions so that it would be possible to run both side by side?

Thanks in advance!

---

