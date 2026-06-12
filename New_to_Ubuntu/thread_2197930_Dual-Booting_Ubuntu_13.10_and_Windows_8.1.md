---
title: "Dual-Booting Ubuntu 13.10 and Windows 8.1"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by sabeekpradhan on 2014-01-06
Hey everyone! I have a Windows 8.1 Laptop (Asus SonicMaster) that came pre-installed with Windows 8 and which I've since upgraded to 8.1. It runs UEFI Firmware, although I've disabled Secure Boot and Fast Boot. I installed Ubuntu 13.10 onto my laptop using the LiveUSB method, and when I was unable to boot into the Ubuntu on my machine, I launched boot repair from the LiveUSB as outlined here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI). However, when I tried to launch boot repair, I got the following error message: "EFI detected. Please use Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")) which contains an EFI-compatible version of this software." and the system aborted the attempt. I tried to download the new UEFI compatible boot repair onto another USB by following the link given in the error message, but when I plugged that USB in, the system wouldn't even let me open the LiveUSB Ubuntu. How do I finally fix my boot, get GRUB working, and be able to boot into either Windows or Ubuntu?

Thanks a ton!

---

### Post by oldfred on 2014-01-06
Did you not install the 64 bit version of Ubuntu. The 32 bit version only boots in BIOS mode.
If you have 64 bit version of Ubuntu installer you should just be able to boot in UEFI mode and add Boot-Repair.

If you go into UEFI menu, do you have an ubuntu entry. Or did you install in BIOS mode?

---

