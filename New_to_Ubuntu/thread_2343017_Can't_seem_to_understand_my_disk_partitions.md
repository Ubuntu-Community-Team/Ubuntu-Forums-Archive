---
title: "Can't seem to understand my disk partitions"
date: 2016-11-12
forum: New to Ubuntu
---

### Post by jcasado94 on 2016-11-12
Hi.

First of all, all this might sound very newbie, but I never got too deep into Linux partition systems... Well, that's why I'm in this forum.

I've just installed Ubuntu alongside Windows in another partition, entirely in the SDD. Despite, in Windows I am using another disk (D:, in there), which is a RAID0 with 1.8TiB (theoretically, as I didn't do it myself, it just came like that when I bought the computer a while ago). I'd like to use a partition of that disk in my Ubuntu SO, if possible in my Home directory (which now, as I said, is in the SDD). Nevermind, here's how my partitions look like from my newly-installed Ubuntu using "sudo fdisk -lu":

```

Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 111,8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xfd1d4a38

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048   1026047   1024000  500M  7 HPFS/NTFS/exFAT
/dev/sda2         1028160 150111359 149083200 71,1G  7 HPFS/NTFS/exFAT
/dev/sda3       150112256 158900223   8787968  4,2G 82 Linux swap / Solaris
/dev/sda4       158902270 234440703  75538434   36G  5 Extended
/dev/sda5       158902272 188196863  29294592   14G 83 Linux
/dev/sda6       188198912 234440703  46241792 22,1G 83 Linux


Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x11afdeff

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1          63 3907037183 3907037121  1,8T 42 SFS



Disk /dev/sdc: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/mapper/isw_ebgeedjade_Volume1: 1,8 TiB, 2000404348928 bytes, 3907039744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 16384 bytes / 32768 bytes
Disklabel type: dos
Disk identifier: 0x11afdeff

Device                                   Boot Start        End    Sectors  Size Id Type
/dev/mapper/isw_ebgeedjade_Volume1-part1         63 3907037183 3907037121  1,8T 42 SFS

```


So, the SDD looks pretty neat to me, but then the other disk - I guess, the 3 last disks, somehow - looks quite messy. I just don't seem to understand how that disk is partitioned... Still, I tried to mount (with ntfs-3g) with the /dev/mapper/isw_ebgeedjade_Volume1-p1 (actually it's named like that...), the /dev/sdb1 and /dev/sdc, and it just says the following - replacing '/dev/sdb1' with the other ones, accordingly -,

```

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

I also attach some screenshots of GParted showing more or less the same...

I don't know which information you might need to understand my partition system in order to help me; I hope you can tell me which are my options in order to use that disk in Ubuntu, as, as I said, I have not a single clue about how this partition is mounted right now...



Thank you for your time,

Josep.

---

### Post by TheFu on 2016-11-12
Both disks appear to be fully allocated with just a trivial amount of storage left unused - like 2MB.

There are many different ways to organize storage.  The trivial, simple ways and the professional, more complex, but much more capable, ways.  Your system has a mix. It is using LVM.  [https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)) provides an overview.  LVM uses PVs (Physical volumes), VGs (Volume Groups), and LVs (Logical Volumes) to organize and "partition" the storage.  LVs are basically partitions. 

Please post the command and output from **sudo parted -l** , **sudo lvs**, **sudo vgs**, **sudo pvs**, and **lsblk** using "code tags."  The output from **df -h** would be nice too.

If RAID and/or encryption is involved, we might need some other commands. I don't see anything that says *encryption*, yet.

No idea what SFS as a partition type means.  Could be part of RAID (or attempted RAID) config. There are 3 types of RAID - hardware RAID, software RAID and "Fake RAID."  I know of great reasons to use HW-RAID and SW-RAID.  I can't come up with a technical reason of ever use Fake-RAID.

Lots to know about these things. Most of us learn "just enough" to get to a needed/wanted solution.

---

### Post by jcasado94 on 2016-11-12
Hi, Thank you for your reply.

The disks are not actually fully allocated, I have around 400Gb from the 1.8Tb, so that looks weird. 
I'll be posting the outputs for the commands tomorrow. Thank you again! 

Josep.

---

### Post by TheFu on 2016-11-12
That's LVM.  It is a layer between the partitioning and file system to make things really flexible.  For example, I ran out of allocated storage on a disk this morning, but because I'd left some extra space unused inside the VG, increasing the LV size and the file system size inside the LV was trivial ... the system was running when I did this. ZERO downtime.  Can't do that with a file system directly on a partition.

BTW, there are lots and lots of LVM commands to get information.  pvdisplay, vgdisplay, lvdisplay are some more.  There's a nice image in the wikipedia article that shows how these things relate to each other.

---

### Post by oldfred on 2016-11-12
Its not really LVM, but SFS or dynamic partitions which is a Windows proprietary partitioning scheme. I have seen it called similar to LVM.
It used to be that Linux would not recognized SFS at all, but they must be working on trying to make it work.

Best to convert from SFS/dynamic partitions to standard basic partitions.
       SFS converting:
[URL="http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html"]http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html
[/URL]
 Also used testdisk if less than 4 dynamic partitions
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418) 

      
 [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from) 
    [URL="http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html"]
[/URL]

---

