---
title: "Failed attempt to resize partition"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by livia2 on 2013-09-07
Hi all,
I'm new to linux and wanted to give it a try by using Ubuntu. I decided to resize the NTFS partition where windows 7 is installed, so I can install Ubuntu on the remaining space.
After resizing the partition with gparted, I got a warning message I cannot recall (my bad). 
To check if everything was OK, I restarted the computer and booted up Windows 7, but I wasn't able to do so since windows says there is some kind of error in the system.
I booted back to Ubuntu (using a USB key) and went back to gparted to give some extra free space to the NTFS partition by resizing it (just in case that was the issue). But when I try to do so, I get the following message:

```

[TABLE]
[TR]
[TD="colspan: 2"]**Grow /dev/sda2 from 163.66 GiB to 193.19 GiB**  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] calibrate /dev/sda2  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sda2
start: 411648
end: 343640063
size: 343228416 (163.66 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] check file system on /dev/sda2 for errors and (if possible) fix them  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***ntfsresize -P -i -f -v /dev/sda2***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]ntfsresize v2011.4.12 (libntfs-3g)
Failed to read last sector (884609016): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
ERROR(22): Opening '/dev/sda2' as NTFS failed: Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong partition? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
if the disk was incorrectly repartitioned (see the ntfsresize FAQ).[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

```
I checked this message on the internet and found something to my problem:

[http://ubuntuforums.org/showthread.php?t=1924454](http://ubuntuforums.org/showthread.php?t=1924454)

but I'm not sure how to proceed from there. If I run the command **fdisk -l**, I get the following:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x914c7580

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       21391   171614208    7  HPFS/NTFS
/dev/sda3           55090       58876    30404608    f  W95 Ext'd (LBA)
/dev/sda4           58876       60802    15471640   12  Compaq diagnostics

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3999 MB, 3999694848 bytes
255 heads, 63 sectors/track, 486 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b8b4567

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         319     2558976    0  Empty
Partition 1 has different physical/logical endings:
     phys=(1023, 63, 32) logical=(318, 147, 21)
Partition 1 does not end on cylinder boundary.
/dev/sdb2               1           4       24930   ef  EFI (FAT-12/16/32)
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 254, 63) logical=(0, 3, 24)
Partition 2 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(3, 29, 50)

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb1'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb1: 2620 MB, 2620391424 bytes
255 heads, 63 sectors/track, 318 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b8b4567

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           1         319     2558976    0  Empty
Partition 1 has different physical/logical endings:
     phys=(1023, 63, 32) logical=(318, 147, 21)
Partition 1 does not end on cylinder boundary.
/dev/sdb1p2               1           4       24930   ef  EFI (FAT-12/16/32)
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 254, 63) logical=(0, 3, 24)
Partition 2 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(3, 29, 50)

Disk /dev/mapper/live-rw: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/live-osimg-min: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
```

Any help would be much appreciated!

---

### Post by oldfred on 2013-09-07
Use Windows disk tools to change the size of Windows's NTFS partition and reboot immediately as Windows has to run chkdsk. And once chkdsk flag is set, Linux will not mount NTFS partition to prevent damage that chkdsk might not then be able to fix. Boot Windows into recovery and run chkdsk.

You also are showing gpt data on drive. Was drive gpt before and you installed Windows yourself. Windows converts a gpt drive to MBR but does not remove backup gpt partition table. The backup table is one of the advantages of gpt, but Windows only boots from gpt with UEFI so only new computers use it with Windows. You need to remove backup table with fixparts.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by livia2 on 2013-09-07
thanks for the prompt reply.

So to be sure, should I run the two commands?
```
dd if=/dev/sda of=/dev/USB/mbr.bin bs=512 count=1
sudo sfdisk -d /dev/sda > parts.txt
```

---

### Post by oldfred on 2013-09-07
I do not think you need mbr.bin. That includes boot loader. But it cannot hurt to have it. Just if you restore it after changes it undoes changes and may create more issues.
 The partition table (only) is more easily recovered from parts.txt or can be edited if necessary to fix errors.

---

### Post by livia2 on 2013-09-07
sfdisk gives the following warning:
```
sfdisk -d /dev/sda > parts.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

---

### Post by oldfred on 2013-09-07
Old tool that gives a really old warning. Drives have not actually used cylinders since hard drives went over 8GB years ago. Back then you have to manually entry CHS values for cylinders, head, sectors into BIOS.
Now newer issue with SSD & 4K drives are 8 sector boundaries but all the current partition tools do that correctly.

---

### Post by livia2 on 2013-09-10
I have finally been able to rescue the data!! 
I used iCare data recovery Software. There is a free of charge version that lets you recover 2GB.
I installed windows and  iCare data recovery Software on the partition that was intended for linux, and from there I accessed the broken partition

For the time being, I'll stay wide away from linux...

---

