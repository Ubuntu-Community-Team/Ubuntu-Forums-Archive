---
title: "How to partition the hard disk when Ubuntu occupies all the hard disk space"
date: 2019-07-14
forum: New to Ubuntu
---

### Post by nhftk91 on 2019-07-14
I recently installed the Ubuntu operating system on any area of the hard disk. Now I want to divide the hard disk space partitioned to install WIN10 operating system together with Ubuntu DABEL BOOT
I tried to divide the area and I got an error message

---

### Post by Impavidus on 2019-07-14
I can't see exactly what you're doing (and I can't read Hebrew, but it's interesting to see that the entire layout of the desktop is mirrored). Do you realise that you can't change the partition of the currently running system? To change it, you have to boot from a live disk.

Make sure you've got backups of all important files. Partitioning and installing Windows are high-risk operations. You could easily loose all contents of your hard drive.

---

### Post by yancek on 2019-07-14
After using a 'live' disk/usb with GParted to shrink the Ubuntu partitions to create unallocated space, you should be able to install windows.  windows 10 has a 'Custom' install option which you should see immediately after the EULA and should allow you to select the unallocated space on which to install windows.  You may need to create an ntfs partition with GParted and mark it as active before installing.  Also, is your Ubuntu UEFI?  The link below is to the Ubuntu documentation on dual booting with windows 10 and it would be good to read before trying to install.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldrocker99 on 2019-07-14
It is **ALWAYS** better to install Windows FIRST, before Ubuntu. GRUB can handle booting Windows, but Window's bootloader can't handle any variety of Linux.

Backup your data, install Windows, **then** install Ubuntu.

Also, I see no reason not to use Legacy over UEFI. Every time I have installed under UEFI, grub has failed to install, resulting in an unbootable system.

---

### Post by oldfred on 2019-07-14
Microsoft has required vendors to use UEFI/gpt for all new systems since release of Windows 8 in 2012. In beginning both vendor's UEFI & Linux distributions has issues with UEFI and getting it to work or work well.
A few systems still have issues, but most work if UEFI updated & running a current version of Ubuntu. Some need boot parameters and/or UEFI settings.

I see no reason to not use UEFI. But some like oldrocker99 still like BIOS with MBR.

Note that for both Ubuntu & Windows how you boot install media UEFI or BIOS is then how it installs. And then system needs to be set to boot in that mode.

Windows only installs & once installed boots from gpt partitioned drives with UEFI.
Windows only installs to MBR and must have a primary NTFS partition with boot flag. You have the 4 primary partition limit. Default BIOS mode installs of Windows will normally use two primary partitions, one Boot and one the main or c: drive.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

