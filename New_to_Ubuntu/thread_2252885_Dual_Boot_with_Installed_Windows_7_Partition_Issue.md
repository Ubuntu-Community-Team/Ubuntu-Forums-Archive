---
title: "Dual Boot with Installed Windows 7 Partition Issue"
date: 2014-11-15
forum: New to Ubuntu
---

### Post by Chris_Paunescu on 2014-11-15
Hello,
Im trying to install Ubuntu 14.04 while keeping my Windows 7 OS. I have found many threads that lead to the installation. I have everything that's needed, I downloaded the ISO, etc etc.
I followed this installation instructions:

[http://www.linuxbsdos.com/2014/05/30/dual-boot-ubuntu-14-04-and-windows-7-on-a-pc-with-uefi-firmware/](http://www.linuxbsdos.com/2014/05/30/dual-boot-ubuntu-14-04-and-windows-7-on-a-pc-with-uefi-firmware/)

Now, my problem is that when I choose Something Else in the Installation Type (while installing Ubuntu), the next screen shows my HD being all free. It does not see the Windows 7 partition.
I have a 512GB HD and 2 paritions (1-100MB for UEFI and 1 500GB for the Windows OS).
I followed the directions from the link, and I resized my drive to have 2-256GB partitions (plus that 100MB UEFI). 2 partitions for Windows (UEFI+256GB) which is installed already and 1 for the new Ubuntu (256GB).
The second 256GB partition is unallocated, free, available, while the other 256GB+100MB is for Windows 7.

Why doesn't Ubuntu Installation see Windows 7 partition? Why does it see only 1 big 512GB drive?
Anyone could help me please? I need to have both OSs.
Thanks...

---

### Post by oldfred on 2014-11-15
Are you sure Windows 7 is installed in UEFI boot mode?

Post this from live installer's terminal:
sudo parted -l

If Windows 7 is in UEFI boot mode it has other partitions also. In BIOS boot mode it normally has 100MB boot and main install. If drive is gpt then Windows only boots in UEFI mode.
If drive is MBR(msdos) then Windows only boots in BIOS boot mode, even if your hardware is newer and will boot in UEFI mode.

---

