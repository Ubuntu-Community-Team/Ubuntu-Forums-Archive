---
title: "Install windows 10 on ubuntu 15.10"
date: 2015-11-19
forum: New to Ubuntu
---

### Post by roni6 on 2015-11-19
Hi everyone,
I want to install Windows 10, on PC that right now working with Ubuntu 15.10 (all the guides that I found talking about install Ubuntu aftet windows...)
I understood that I have to separate the hard drive to 2 parts, how should I do it?
The instilling files (for windows) on disk-on-key (bootable)

Thanks!!

---

### Post by erfahren on 2015-11-19
GParted is available in the repos - you can use it to shrink your Ubuntu partition to create new unallocated space on the drive (use the Windows installer to format the partition space) - you should also have a small partition for the Linux swap (at least equal to the amount of RAM in the pc) - once you have Windows installed you will need a bootable drive with Ubuntu on it to reinstall the GRUB bootloader (it would be included with the 15.10 install on your drive but the boot menu wouldn't show up since it's the only OS - you can press the shift key while booting to get its menu to show up and pause now if you want - but Windows will wipe GRUB's boot sector on your drive.) 

(In short, also having a bootable flash drive with a Ubuntu installer setup beforehand would be helpful for you to reinstall GRUB.) 

while using GParted take note of the partition layout and labels (/dev/hda1, /dev/hda2 for example) so you know where Ubuntu is installed.

There are lots of guides to reinstall the GRUB bootloader online. gl

---

### Post by yancek on 2015-11-19
Are you using UEFI with GPT partitioning and is Ubuntu installed using UEFI?  If you don't know you can boot the Ubuntu install medium and from a terminal run:  sudo gparted
That will show the partitions and you should be able to see if one is labelled EFI.  If you have UEFI/GPT with Ubuntu, you must install windows the same.  Check the link below for detailed information.  Use GParted which is on the install medium to shrink the current Ubuntu partition as it won't work run from an installed system.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by rdb3 on 2015-11-19
I saw this video (Dual boot Ubuntu 14.04 and Windows 7 with Ubuntu installed first)
  which you may find helpful....

[https://www.youtube.com/watch?v=WnRp0qguq80](https://www.youtube.com/watch?v=WnRp0qguq80)

---

### Post by oldfred on 2015-11-19
Post this and we should be able to tell how you have installed to your system.
sudo parted -l

If you have the ESP - efi system partition and gpt then you have UEFI. If you have MBR(msdos) with extended partition and logical partition then you have BIOS.

You have to install Windows in same boot mode and how you boot Windows installer is how it will install. If newer hardware that is UEFI, it will offer both BIOS & UEFI boot options for installer.

If BIOS with MBR, Windows has to have a primary NTFS formatted partition with the boot flag. It only boots in BIOS mode from MBR. Or enough unallocated space and available primary partitions. It normally installs  to two primary partitions but will use one if set up in advance.
You still must turn off fast start up in Windows to dual boot without issues.

---

