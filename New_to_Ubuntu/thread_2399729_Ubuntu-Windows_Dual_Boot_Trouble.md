---
title: "Ubuntu-Windows Dual Boot Trouble"
date: 2018-08-29
forum: New to Ubuntu
---

### Post by fredo478 on 2018-08-29
I just installed Ubuntu on my Lenovo laptop along with Windows 10, but now speed of both OSes is extremely slow. How can i find out what the problem is? 

My laptop config: 
RAM-8GB
HDD-1 TB
Nvidia Graphics-2 GB 

Thank you in advance.

---

### Post by oldfred on 2018-08-29
It would make booting Windows a bit longer as fast start up/hibernation must be off. Installing Ubuntu would not make Windows slow. Unless you made the NTFS partition so small that Windows does not have any working room. It likes 30% free space inside the C: "drive". 

Have you installed the correct nVidia driver in Ubuntu? From Ubuntu repository?
If you install incorrect one or different one, you must purge old one first or you will have issues.

This is more for boot issues, but may show something:
 Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

