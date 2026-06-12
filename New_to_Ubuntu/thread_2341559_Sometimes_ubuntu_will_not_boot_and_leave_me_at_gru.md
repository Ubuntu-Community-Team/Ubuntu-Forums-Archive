---
title: "Sometimes ubuntu will not boot and leave me at grub&gt;"
date: 2016-10-29
forum: New to Ubuntu
---

### Post by sparshy on 2016-10-29
I have windows 10 dual boot with ubuntu. There are in all three hard drives (2 ssd and 1 sata)
1. windows 10 installed on /dev/nvme0n1
2. ubuntu installed on /dev/nvme1n1
3. sata is just for storage

The problem is sometimes ubuntu will not start and leave me at grub prompt (grub>) I believe this is when the ssd is not detected by the bios too (Only one ssd is detected by bios)
The weird thing is that whenever i restart from windows i am able to see both ssds in bios.

[http://paste2.org/HXApPIBt](http://paste2.org/HXApPIBt)

Thanks

---

### Post by leunam12 on 2016-10-29
Is it an MSI motherboard? sometimes their firmware has problems detecting SATA devices.
Another thing to check is if you have fastboot and/or secureboot enabled, if tou do, disable them and see if that fixes it.

---

### Post by sparshy on 2016-10-29
No its not MSI, its Alienware 15r2. Yes I have disabled fastboot from windows 10 and secure boot for UEFI. So here are few more observations. 

**Config**
/dev/nvme0n1 (SAMSUNG PM951 NVMe SSD) 256GB - Windows 10 installed
/dev/nvme1n1 (SAMSUNG PM951 NVMe SSD) 256GB - Ubuntu installed, I did manual partitioning and installed bootloader to /dev/nvme0n1p1(windows boot loader)
/dev/sda SATA 1 TB harddrive

1. There is an option** SATA operation** in BIOS. It has two options RAID and AHCI. In RAID mode ubuntu can't see any of the nvme, In AHCI it can see all three drives, but in AHCI after installation, If i reboot ubuntu it lands up in grub> with BIOS. I read it somewhere that we are prompted with grub> prompt when grub.cfg file is not found, which makes sense because its on /dev/nvme1(the second ssd) and the drive is not detected by BIOS. However when I restart from windows 10 BIOS detects all three drives. Its weird. Windows is always able to detect all three drives. So my only way to boot into ubuntu for now is start windows first then restart and i am prompted with grub options to boot with ubuntu. This is not I want :(

2. If I switch to RAID and **LOAD LEGACY OPTION ROM** in bios (although laegacy options are enabled the **BOOT LIST OPTION** is UEFI) then ubuntu is able to detect both drives, but again after installation the problem is same, BIOS doesnt detect the second ssd and I am left with grub> prompt.

Here are the screenshots
[https://postimg.org/image/ve3hg1et1/](https://postimg.org/image/ve3hg1et1/)  >> LOAD LEGACY OPTION ROM
[https://postimg.org/image/8qo89vz91/](https://postimg.org/image/8qo89vz91/) >> RAID OPTION



I have spent hours trying to figure this out to no avail.
Thanks

---

### Post by oldfred on 2016-10-29
It would probably make sense that RAID would hide the second drive as then it is in RAID and just a copy of first drive, even though that is not how you currently have it configured.
Best to use AHCI and figure out issue(s).

Some systems have had to have Legacy ROM loaded even when booting in UEFI mode. That to me makes no sense as Legacy ROM is supposed to be just for BIOS emulation and someday they will probably remove that legacy ROM and legacy boot. 

       Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[URL="http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr"]http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr

[/URL]
 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers) 

[URL="http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr"]
[/URL]

---

### Post by sparshy on 2016-10-30
Well I was earlier trying with Ubuntu 16.04, I again tried with Ubuntu 16.10 which has Kernel 4.8 and surprisingly it cant even detect the SATA drive in RADI mode, leave the SSDs!!!

---

### Post by oldfred on 2016-10-30
RAID mode is really on supported in the Server install version. But you must really have RAID with two identical drives, identical partitions, and configuration.

---

