---
title: "WARNING: The partition is misaligned by 3072 - Risk to lose data?!"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by Kocho on 2014-09-11
Hello Ubuntu Community

I know I know I know... many posts about this.
I read many, specially this one: [http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
And I see this one: [http://support.wdc.com/product/download.asp?groupid=805](http://support.wdc.com/product/download.asp?groupid=805) - I am yet to try because I dont have windows 7 nearby

The problem: 
1. I had a problematic disk with two partitions
2. I purchased new. It happened to be WD Green 1TB
3. I formatted the whole 1TB as a single partition as NTFS so I can have Widows access to it if I need it. 
4. I was not aware of the AF that WD has
5. I moved most of the files from the problematic disk to 1TB. Around ~300GB of data.
6. I deleted one of the partitions from the problematic disk and it is a free space now.
7. I did reboot then
8. Now 1TB is sort of unusable. I mean I cannot mount the partition. 
8.1 I thought that this could be due to the deleted partition (point 6). 
9. I then fiercely googled, and I see this actually deeper problem which tells me point 8.1 is not really the reason?
10. sudo fdisk -lu output is below. The problematic disk is temporary powered off.
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3293b480


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   101140479    50569216   83  Linux
/dev/sda2       101142526   312576704   105717089+   f  W95 Ext'd (LBA)
/dev/sda5       118720413   312576704    96928146    7  HPFS/NTFS/exFAT
/dev/sda6       101142528   118718463     8787968   82  Linux swap / Solaris


Partition table entries are not in disk order


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2052474d


This doesn't look like a partition table
Probably you selected the wrong device.


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not start on physical sector boundary.
/dev/sdb2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not start on physical sector boundary.
/dev/sdb3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not start on physical sector boundary.
/dev/sdb4      2642411520  2642463409       25945    0  Empty


Partition table entries are not in disk order


Disk /dev/mapper/cryptswap1: 8998 MB, 8998879232 bytes
255 heads, 63 sectors/track, 1094 cylinders, total 17575936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f62669f




Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

11. I cannot mount the "1TB" partitions that are in the image attached. Even though I see on few places that other users tell that I can use the data but SLOW. I cannot mount! :(

12. What do I do please to save the data? What do you suggest because I cannot see them at the moment.

13. I have ubuntu 12.04.

14. I can go to windows with these: [http://support.wdc.com/product/download.asp?groupid=805](http://support.wdc.com/product/download.asp?groupid=805) if that is the only help?

15. Is there something smarter to do?


Thank you very much!

---

### Post by Kocho on 2014-09-11
NTFS signature is missing...perhaps that is why I cannot mount.

Attach.

I am in wonders because I copied the ~300GB data and now I cannot access them. I think when copying, it was sdc, now it is sdb...that shouldnt be a problem?

---

### Post by Kocho on 2014-09-11
sudo parted -l
```

Model: ATA Maxtor 6V160E0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  51.8GB  51.8GB  primary   ext4         boot
 2      51.8GB  160GB   108GB   extended               lba
 6      51.8GB  60.8GB  8999MB  logical
 5      60.8GB  160GB   99.3GB  logical   ntfs




Model: ATA WDC WD10EZRX-00D (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB  ntfs




Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 8999MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  8999MB  8999MB  linux-swap(v1)

```

---

### Post by Kocho on 2014-09-11
```

sudo ntfsfix /dev/sdb
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb was processed successfully.

```


Still cant mount...gparted closed, then opened, same error :( jeez

---

### Post by Kocho on 2014-09-11
I formatted the disk thru disk utility. I picked ntfs and thats how I did it.

Here are other outputs I ran in meantime

```

ls /dev/sdb*
/dev/sdb  /dev/sdb1  /dev/sdb2


sudo mount -t ntfs /dev/sdb2 /media/1TB
NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?




sudo mount -t ntfs /dev/sdb1 /media/1TB
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?




sudo parted -l /dev/sdb unit s print
Model: ATA Maxtor 6V160E0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  51.8GB  51.8GB  primary   ext4         boot
 2      51.8GB  160GB   108GB   extended               lba
 6      51.8GB  60.8GB  8999MB  logical
 5      60.8GB  160GB   99.3GB  logical   ntfs




Model: ATA WDC WD10EZRX-00D (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB  ntfs




Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 8999MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  8999MB  8999MB  linux-swap(v1)




sudo mount -t ntfs-3g /dev/sdb2 /media/1TB
NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
maximus@maxpc:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/1TB




sudo mount -t ntfs-3g /dev/sdb1 /media/1TB
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

---

### Post by Kocho on 2014-09-11
:( I mean how these things happen :) :(

```

sudo ntfsfix /dev/sdb1
[sudo] password for maximus: 
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.




sudo ntfsfix /dev/sdb2
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.

```

---

### Post by mastablasta on 2014-09-11
this
```

Volume is corrupt. You should run chkdsk
```

would be the first thing I would do when encountering issues on NTFS.

```
chkdsk /r
```


furthermore the misalignment causes slowdown in disk performance. so it is good to have the partitions aligned properly. Linux (newer versions)does this automatically I believe. in windows XP a utility is ran I am not sure how it's done in Win7 or 8. this is on WD drives. Seagate uses different technique.

unless you are dual booting you do not need NTFS partitions in fact it is better to use ext4 instead.

---

### Post by Kocho on 2014-09-11
As far as I can see it happened somehow that I have NTFS problem and mis-alignment...2 in 1 :)

> **mastablasta said:**
> this
```

Volume is corrupt. You should run chkdsk
```

would be the first thing I would do when encountering issues on NTFS.

```
chkdsk /r
```


Thank you. Can you please confirm whether this is safe because I would like to save the data ?
So I need windows boot CD now?

In meantime this is what I compiled

Shall I run?
sudo fsck /dev/sdb
or
sudo fsck /dev/sdb1
or
sudo fsck /dev/sdb2




Shall I run check from gparted? no?




Now I turned on the problematic disk, and the WD Green one with 1TB is sdc


```

sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 0.8.1


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************


Exact type match not found for type code 7000; assigning type code for
'Linux filesystem'
Exact type match not found for type code 4300; assigning type code for
'Linux filesystem'
Exact type match not found for type code 7200; assigning type code for
'Linux filesystem'


Warning! Secondary partition table overlaps the last partition by
1818302407 blocks!
You will need to delete this partition or resize it in another utility.

```

> **mastablasta said:**
> 
furthermore the misalignment causes slowdown in disk performance. so it is good to have the partitions aligned properly. Linux (newer versions)does this automatically I believe. in windows XP a utility is ran I am not sure how it's done in Win7 or 8. this is on WD drives. Seagate uses different technique.

unless you are dual booting you do not need NTFS partitions in fact it is better to use ext4 instead.

Thanks. So I want to save the data. I need to fix the volume and then eventually copy the files elsewhere or create a partition. I have Ubuntu 12.04 as I said. Is it creating properly aligned partitions? Seems not? maybe with gparted then?

---

### Post by oldfred on 2014-09-11
Do not use gdisk nor convert to gpt unless that is what you want. Whether MBR(msdos) or gpt(GUID) has nothing to do with format of partitions or partition alignment. And changing could add to issues. I do suggest gpt for new drives as it also has a backup partition table, but if ever thinking of installing Windows then you have to have a newer system as Windows only boots from gpt with UEFI. If external that is not an issue unless you also want to connect to an old XP system as gpt is not recognized by XP, all newer Windows read data on NTFS formatted partitions on gpt  whether BIOS or UEFI.

Some info on alignment. But all new partition tools align correctly.
 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

But now you see to have newer partition table issues. If formatted NTFS you have to run chkdsk as ntfsfix only can do minor fixes. You cannot run fsck or e2fsck on anything but the ext2, ext3 or ext4 family of formats. Other Linux formats also have separate file check tools.

---

### Post by mastablasta on 2014-09-11
yes windows boot disk with chkdsk install should do it. chkdsk repairs data and solves some file system issues.

fsck is used on Linux partitions only.

yeah the idea is to repair the file system, realign partitions and then save the data. or save the data first and then realign the partitions.

it might be the error is made by failing drive. you could try ultimate boot cd or similar to run smart tools if they can find anything. if the drive is failing the issue is a lot harder to fix. but you might still be able to get read only access.

my bro said "wd green is more like wd sh...". although the two I have work quite nicely. while his failed quite fast. maybe it's time for some backup religion :-D

---

### Post by Kocho on 2014-09-11
Thank you **oldfred** & **mastablasta**

To be honest, I went to a PC with Win7. This is the outcome for the record:

1. At boot, chkdsk automatically activated itself, fixed the ntfs and I could see all files.
2. Then I moved the file elsewhere.
3. I did format to ntfs again with 4096bytes
4. copied the files back
5. the ntfs problem seems gone
```

sudo parted /dev/sdc print
Model: ATA WDC WD10EZRX-00D (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB  ntfs

```
6. I still have the same picture from the disk utility :) 
6.1 Similar picture from gparted attached
7. I cannot access the files :) because I cannot mount 
8. Seems misaligned.
9. I have a backup of the files. Thats a big plus
10. What do you recommend please? How do I align it without formatting the disk because I will have to copy the files agin. Not a big deal, but ideally I want to save that time.
11. I know I can format the drive with ext4 - how do I access it from windows then? Is it with [http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)
12. How do I safely (and properly format) the drive with ext4 and have it aligned because the ntfs format failed?


I think and hope this is the last :)

Thanks

---

### Post by oldfred on 2014-09-11
NTFS should be fine. 
Better to use NTFS if dual booting than some of the utilities in Windows to try to read ext4.

Did you review post #4 in this?
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

Disk Utility may give false messages.
Post this to see sectors:
 sudo parted /dev/sdc unit s print

And if all start of partitions are divisible by 8 then it is ok.

This also is not correct, it should be msdos(MBR) or gpt:
Partition Table: loop

Did you convert to dynamic partitions? Those do not work with Linux. They must be basic.

---

### Post by Kocho on 2014-09-11
> **oldfred said:**
> NTFS should be fine. 
Better to use NTFS if dual booting than some of the utilities in Windows to try to read ext4.

Did you review post #4 in this?
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)


No! I apologize. I will do that now.
If you have something to help with in meantime, please do.
I am thankful

I need NTFS so I can move files back and forth between the computers...and etc.
I already use it for quite some time with the other two discs. Even the problematic disc is still alive and well working.

> **oldfred said:**
> 
Disk Utility may give false messages.
Post this to see sectors:
 sudo parted /dev/sdc unit s print

And if all start of partitions are divisible by 8 then it is ok.

This also is not correct, it should be msdos(MBR) or gpt:
Partition Table: loop

Did you convert to dynamic partitions? Those do not work with Linux. They must be basic.

Yes it is basic. I think basic is by default and I didnt convert to dynamic

loop looks incorrect, yes.

```

sudo parted /dev/sdc unit s print
Model: ATA WDC WD10EZRX-00D (scsi)
Disk /dev/sdc: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End          Size         File system  Flags
 1      0s     1953525167s  1953525168s  ntfs

```

---

### Post by Kocho on 2014-09-11
Yet I have a single partition when I connect the driver to a windows 7 computer
Also gparted shows single 1TB partition (the whole drive)

```

sudo fdisk -lu /dev/sdc


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x6e697373


This doesn't look like a partition table
Probably you selected the wrong device.


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  1936269394  3772285809   918008208    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sdc2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/sdc3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/sdc4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.


Partition table entries are not in disk order



```

---

### Post by oldfred on 2014-09-11
I think you have what is just a formatted drive, that does not have any partitions. That would then be seen as loop.
You do not normally format a drive. That is like a super large floppy drive or DVD.

Drives need to be partitioned, and each partition formatted to use it.

There is no way to convert  a formatted drive to one with partitions as you have data in the first sector where partition table is. That is why partition table looks funny as it is just you data and partition tools are trying to convert random data to partition format.

---

### Post by Kocho on 2014-09-11
Thank you.

Strange - Windows 7 on another computer can see the files properly. I loaded hirens, win xp mini, also sees the files.

I decided to waste no more time. I re-created msdos partition table and re-formatted - all with gparted. Now looks ok.


Thank you again

---

