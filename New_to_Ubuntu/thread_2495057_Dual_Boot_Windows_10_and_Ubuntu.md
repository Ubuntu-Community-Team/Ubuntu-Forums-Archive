---
title: "Dual Boot Windows 10 and Ubuntu"
date: 2024-02-06
forum: New to Ubuntu
---

### Post by cannsagbazar on 2024-02-06
[B]After installing Ubuntu 20.04.06 LTS as a dual boot, even after selecting the Windows 10 option from the GRUB menu, Ubuntu still boots up.

[/B][COLOR=#000000]BootInfo Summary:

[/COLOR][https://paste.ubuntu.com/p/7vDvmZz8xw/](https://paste.ubuntu.com/p/7vDvmZz8xw/)[B]



[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293393&stc=1[/IMG]

[/B]

---

### Post by yancek on 2024-02-06
The information you posted will not help so you need to post a lot more detail.  The simplest thing to do to get the most information possible is to boot Ubuntu, go to the site at the link below and download an run the boot repair software.  Use the 2nd option described on that page and do NOT try to make any repairs but select the Create BootInfo Summary option and post the link you are given when it finishes here.  That will allow members here to see detailed information on your computer which should help to recommend solutions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do you know the difference between an EFI install and a Legacy/CSM install?
Do you know if windows 10 is an EFI install?
Did you boot Ubuntu in EFI mode before installing?
When you check partitions, do you have an EFI partition under /boot/efi from Ubuntu?
Does this partition have directories named 'Microsoft' and 'ubuntu'?
When you are booted into Ubuntu, when you navigate to the /boot/grub/grub.cfg file, do you see an entry for window?

There are more questions but running boot repair should answer the above and more.

---

### Post by cannsagbazar on 2024-02-06
Thank you for your interest. I uploaded the link.

---

### Post by oldfred on 2024-02-06
You have old BIOS/MBR installs.
You must have installed Windows yourself as Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012 and release of Windows 8.

But you installed grub to PBR partition boot sector or BS boot sector of sda1 which is your Windows BIOS boot partition.
You should never install grub to a partition only to a drive. With newer UEFI, installer knows to use ESP - efi system partition on the drive.
And install of grub to NTFS PBR, breaks Windows as it has essential boot info in its PBR.

[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
Also check for /boot/grub in addition to /Boot 

Because you are using old MBR/BIOS boot, you only have one MBR for boot loader. 
Grub only boots working Windows. So when Windows breaks you may have to install a Windows boot loader to MBR, repair Windows and then restore grub to MBR. With UEFI all systems are directly bootable from UEFI boot menu.
So you need to have two flash drives. An Ubuntu installer with its repair tools and a Windows repair/recovery flash drive that you can make from Windows or a Windows installer with repair tools.

You also need good backups of both Windows & Ubuntu.

---

