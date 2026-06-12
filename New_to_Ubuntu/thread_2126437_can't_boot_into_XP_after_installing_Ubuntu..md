---
title: "can't boot into XP after installing Ubuntu."
date: 2013-03-17
forum: New to Ubuntu
---

### Post by jim3008 on 2013-03-17
yesterday, i decide to just dive into Ubuntu without knowing much about it.  i've installed and dual boot Ubuntu 12.10 on my Window XP netbook (1.66ghz and 1gb ram) with a USB thumb drive.  everything installed "fine" and Ubuntu seems to do "mostly" what i expect it to do.  though, some programs that i use daily just doesn't work on Ubuntu (or i'm too lazy and not tech savy enough to get ~10 programs working correctly on Ubuntu).

So I restart my computer to select XP from the boot menu. it loads for couple seconds with the XP logo then BSOD.  i've tried to google my answer and looked into "boot repair", but i just end up more confused.  So what do I do?

Thanks
Jim

sudo fdisk -l
> Disk /dev/sda: 160.0 GB, 160041885696 bytes255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74c23cf5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   259275635   129637786+   7  HPFS/NTFS/exFAT
/dev/sda2       288720180   312576704    11928262+  1c  Hidden W95 FAT32 (LBA)
/dev/sda3       259276798   288718847    14721025    5  Extended
/dev/sda5       286646272   288718847     1036288   82  Linux swap / Solaris
/dev/sda6       259276800   286646271    13684736   83  Linux


Partition table entries are not in disk order


Disk /dev/sdb: 4007 MB, 4007624704 bytes
32 heads, 63 sectors/track, 3882 cylinders, total 7827392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0564453d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7826111     3913024+   b  W95 FAT32




---

### Post by oldfred on 2013-03-17
You may need to run chkdsk from your XP install disk.

But post the link to BootInfo report from Boot-Repair. Boot-Repair will not fix most XP issues and you need the Windows repairCD for that.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

