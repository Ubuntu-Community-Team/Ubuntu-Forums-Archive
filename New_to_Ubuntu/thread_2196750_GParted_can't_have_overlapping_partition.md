---
title: "GParted can't have overlapping partition"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by sauravbhaumik on 2013-12-31
Hello

In my laptop, I have ubuntu (linux mint) dual boot with windows 7.  I want to delete my linux mint and install ubuntu 13.10 in the same partition. I booted into a live cd and proceeded to the installation process, but it can't detect my partition table.

From my linux mint, I give the outputs of the following commands.

```
saurav@mathematics ~ $ sudo gparted
[sudo] password for saurav: 
======================
libparted : 2.3
======================
Can't have overlapping partitions.

```

```

saurav@mathematics ~ $ sudo testdisk /list
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Please wait...
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition			Start        End    Size in sectors
 1 E extended LBA             0  31 33 60800 254 63  976766080
 2 * HPFS - NTFS           1492 110 27  1505  46 13     204800 [System Reserved]
 3 P HPFS - NTFS           1505  46 14 31338  74 16  479268912
Space conflict between the following two partitions
 1 E extended LBA             0  31 33 60800 254 63  976766080
 2 * HPFS - NTFS           1492 110 27  1505  46 13     204800 [System Reserved]
 5 L HPFS - NTFS              0  32 33  1492 110 26   23973888 [Recovery]
   X extended             31338 105 62 46212   1 61  238944258
 6 L Linux                31338 106  1 46212   1 61  238944256
   X extended             46212  33 31 46455  29 38    3903551
 7 L Linux Swap           46212  34 31 46455  29 38    3903488
   X extended             46456   0  1 60800 254 63  230452425
 8 L HPFS - NTFS          46456   1  1 60800 254 63  230452362 [Data]

```

```

sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2588644

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1985   976768064   488383040    f  W95 Ext'd (LBA)
/dev/sda2   *    23975936    24180735      102400    7  HPFS/NTFS
/dev/sda3        24180736   503449647   239634456    7  HPFS/NTFS
/dev/sda5            2048    23975935    11986944    7  HPFS/NTFS
/dev/sda6       503451648   742395903   119472128   83  Linux
/dev/sda7       742397952   746301439     1951744   82  Linux swap / Solaris
/dev/sda8       746315703   976768064   115226181    7  HPFS/NTFS

```

Please tell me how to fix this problem. Thanks in advance.

---

### Post by r-ehl on 2013-12-31
A great tutorital can be found here: [https://www.linux.com/learn/docs/ldp/681-Partition#fdisk_partitioning](https://www.linux.com/learn/docs/ldp/681-Partition#fdisk_partitioning)
I hope it will help you

---

### Post by The Cog on 2013-12-31
That partition table is screwed. Make a full backup before you try anything.

By my understanding, the rules are that:
* partitions 1-4 must never overlap
* partitions 5 upwards must not overlap, and must be inside whichever of partitions 1-4 is the extended partition.

Looking at the fdisk output above, none of partitions 2-8 actually overelap each other, so there is currently no danger of overwriting each other. 
But physical partitions 2 and 3 both overlap the extended partition (1). 
After partition 1 which covers the whole disk, the other partitions (in disk order) are 5, 2, 3, 6, 7, 8.

I'm not sure, but there may be a danger that any attempt to repartition could think that there is a big unused chunk inside the extended partition, and try to put other partitions there overwriting 2 and 3.

I am not surprised that gparted doesn't like it, and I'm not sure if any partitioning tools or installers would be reliable with this disk. You might try using the Ubuntu installer to overwrite the existing linux partitions (without repartitioning). But I would look for advice from others here first.

---

### Post by sauravbhaumik on 2013-12-31
Thanks for your replies. I have meanwhile deleted some partitions through windows 7, including the ubuntu partition. I though it would take care of the partition table somehow. But the problem still persists. 

Here is a snapshot of the disk utility from live usb.

[ATTACH=CONFIG]249054[/ATTACH]

Here is the output of fdisk -lu.
```

sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2588644

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1985   976768064   488383040    f  W95 Ext'd (LBA)
/dev/sda2   *    23975936    24180735      102400    7  HPFS/NTFS/exFAT
/dev/sda3        24180736   503449647   239634456    7  HPFS/NTFS/exFAT
/dev/sda5            2048    23975935    11986944    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8039 MB, 8039300608 bytes
248 heads, 62 sectors/track, 1021 cylinders, total 15701759 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009a291

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15698895     7849417    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

```

In windows 7 computer manager, I can see that there are only three existing partitions now, namely the sda2,3,5. They are all logical drives. There should be no sda1.

Could anybody please give me some ideas?

---

### Post by sauravbhaumik on 2013-12-31
I have another observation to make. I have a desktop also, which has win xp and ubuntu 11 in dual boot. In my ubuntu 11 in the desktop, the gparted works fine, and does not complain about overlapping. However, there ARE overlappings, as fdisk -lu says:

```
saurav@reflexion:~$ sudo fdisk -lu
[sudo] password for saurav: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63488879    31744408+   c  W95 FAT32 (LBA)
/dev/sda2        63488880   123379199    29945160   83  Linux
/dev/sda3       123379326   125467629     1044152   82  Linux swap / Solaris
/dev/sda4       125467650   625142447   249837399    f  W95 Ext'd (LBA)
/dev/sda5       187783848   379230389    95723271    7  HPFS/NTFS
/dev/sda6       379236352   625139711   122951680    7  HPFS/NTFS
/dev/sda7       125467776   187783784    31158004+   7  HPFS/NTFS

Partition table entries are not in disk order

```

Note that much as in the laptop case, the sda4 covers a great portion of the hard drive, and sda7,5,6 overlap with it. But that does not cause a problem.

Any ideas?

---

### Post by The Cog on 2013-12-31
In this second case, the primary partitions 1-4 don't overlap each other. sda4 is the extended partition that acts as the container for all the logical partitions (5 upwards). And all the logical partitions (5-7) all exist inside sda4 without overlapping each other. 

This is a clean setup with 4 primary partitions, one of which (called the extended partition) is the container for all the logical partitions. 

Some of the start of the extended partition (I don't know how much without searching) is where the table of all the extended partition locations is listed, so the first logical partition inside the extended partition cannot be located right at the start. You can see in this case there is quite a gap leaving room for the extended partition table (187783848 - 125467650 = 62316198 sectors).

---

### Post by oldfred on 2013-12-31
Windows only boots from primary partitions. So those must be primary. But you cannot have overlapping primary inside the extended.

Back up partition table. And then try fix parts. It does not work on overlapping where actual partitions overlap but can change logical to primary or primary to logical if all logicals can be together in one extended.

       First backup partition table, use your drive for sdX or sda, sdb etc. Copy to external device
sudo sfdisk -d /dev/sdX > parts.txt

      
 To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by sauravbhaumik on 2013-12-31
> **oldfred said:**
> Windows only boots from primary partitions. So those must be primary. But you cannot have overlapping primary inside the extended.


Hi Oldfred. Here is the print screen from my windows 7. It shows that all the three available partitions are logical. 

[ATTACH=CONFIG]249070[/ATTACH]

---

### Post by The Cog on 2014-01-01
Assuming that's the same drive that you posted in post #4 then all that proves is that the windows tool cannot be trusted to tell you the truth. No surprises there, really. I guess they've taken short-cuts in the code by assuming the partition table is correct, which is isn't in this case.

If I were to try to correct the partition table (from post #4), I would probably just change the type of partition 1 to be NTFS and change its start/end sectors to be those of the current partition 5. This would leave you with 3 primary partitions and no extended partition. Then you can add an extended partition (4) with the normal Ubuntu installer to install Ubuntu into. Whether this would work, I don't know, so make very sure you have backups before starting.

@oldfred: Does what I suggest sound reasonable to you? Which partition editor would you suggest?

---

### Post by oldfred on 2014-01-01
Often with overlapping type issue many partition tools do not work.
Options are fixparts which I think is the easiest, testdisk, or manually editing the sfdisk text file and restoring the edited version.

---

### Post by sauravbhaumik on 2014-01-03
> **The Cog said:**
> Assuming that's the same drive that you posted in post #4 then all that proves is that the windows tool cannot be trusted to tell you the truth. No surprises there, really. I guess they've taken short-cuts in the code by assuming the partition table is correct, which is isn't in this case.

If I were to try to correct the partition table (from post #4), I would probably just change the type of partition 1 to be NTFS and change its start/end sectors to be those of the current partition 5. This would leave you with 3 primary partitions and no extended partition. Then you can add an extended partition (4) with the normal Ubuntu installer to install Ubuntu into. Whether this would work, I don't know, so make very sure you have backups before starting.

@oldfred: Does what I suggest sound reasonable to you? Which partition editor would you suggest?

To The Cog and Oldfred

Thanks for your idea. I have a little doubt. In windows 7 the computer manager shows that all the three partitions (i.e. partitions 2,3,5) are all logical. I am worried that if I change the start/end sectors of partition 1 to be those of partition 5, the windows may not boot.

So I think I should change the start/end sectors of partition 1 to be those of that partition from which Windows 7 boots (is it partition 2 ?). Please advise.

---

### Post by The Cog on 2014-01-04
You would also have to change the type of partition 1 to 7.

I would guess the odds are better than 50/50 for it working but I'm not really confident. You should be really sure you can restore to the present state if things go wrong. 

You can use dd to backup and restore the boot partition to/from a file. To create an image of the boot partition (the first 512 ytes of sda):
```
sudo dd if=/dev/sda of=image-file-name bs=512 count=1
```
and the image should be 512 bytes long. To write the image back swap input and output filenames:
```
sudo dd if=image-file-name of=/dev/sda bs=512 count=1
```
Actually you don't need to specify the block size and count when writing back because the image is already the right size.

It occurs to me that the existing GRUB bootloader will be wanting to use info from partition 6 (which I gather you have deleted). The grub bootloader needs stuff from the linux /boot/grub folder. Unless you can replace the existing grub, it may not boot  even now. I would suggest using something like testdisk to replace the existing grub bootloader to complete the removal of the old linux install.

---

### Post by oldfred on 2014-01-04
Did you try fixparts. As that may let you change logical to primary or vice versa. 
Was first partition always FAT or did it somehow get changed from NTFS?

---

### Post by sauravbhaumik on 2014-01-08
> **oldfred said:**
> Did you try fixparts. As that may let you change logical to primary or vice versa. 
Was first partition always FAT or did it somehow get changed from NTFS?

No partition was FAT. 

Thanks, I will try fixparts.

---

