---
title: "GParted does not recognize disk partitions"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by mevets on 2013-10-13
I am trying to install Ubuntu. When run the installer, it cannot see my Win partition, separate data NTFS partition, or any others. This may be because I had Ubuntu on the machine previously and I deleted my /home partition from Windows to allow for more space. Is there any way to make it try to rescan for a patition map that was lost?

[IMG]http://i.imgur.com/sMIDRTS.png[/IMG]

Will update post with pic of partitions from Windows install...

[IMG]http://i.imgur.com/YNANF4B.png[/IMG]

---

### Post by fantab on 2013-10-14
Boot Ubuntu DVD/USB and "Try Ubuntu without Installing'. Open the Terminal [ctrl+alt+T] and post the output of the following command:
```
sudo parted -l
```

Ubuntu installer will NOT install to NTFS partitions. You will either need 'Unallocated' space or a partition formatted with Linux File system.

First of all run 'chdsk' on your HDD from Windows: [HOW TO]("http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/using-windows-7-how-do-i-run-chkdsk/a68b3e4d-1a42-e011-9767-d8d385dcbb12").

---

### Post by oldfred on 2013-10-14
Your c: drive/partition does not have much room. Generally Windows like 30% free space and at less than 10% free it may run extremely slow and defrag will take forever as there is no working room.

Use Windows tools on the NTFS partitions, but do not create new partitions nor delete non-Windows partitions with Windows tools. It does not see Linux partitions correctly and often messes up partition table.

---

### Post by coffeecat on 2013-10-14
The fact that Gparted reports "unallocated" and Windows Disk Management shows four healthy partitions for the same hard drive suggests a partition table irregularity that is confusing Gparted but not Disk Management - worryingly, because I wouldn't use the term "healthy " when there's a partition table irregularity. 

Where were you intending to install Ubuntu? Before you try anything else I suggest you run and post the output of this terminal command from the live Ubuntu session:

```
sudo fdisk -lu
```

Hopefully, it will show us what the irregularity is.

---

### Post by mevets on 2013-10-14
Yes, I was planning on installing Ubuntu and that is why I am asking this question.

The output from sudo fdisk -lu:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1254fee7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   136938059    68365606    7  HPFS/NTFS/exFAT
/dev/sda3       136927230   976768064   419920417+   5  Extended
/dev/sda5       136927232   156459007     9765888   83  Linux
/dev/sda6       156461056   976766975   410152960    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8019 MB, 8019509248 bytes
251 heads, 44 sectors/track, 1418 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00068971

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15663103     7830528    b  W95 FAT32
```

---

### Post by oldfred on 2013-10-14
Usually it says overlapping partitions, or maybe that is from bootinfoscript and parted?

/dev/sda2          206848   [COLOR=#ff0000]136938059[/COLOR]    68365606    7  HPFS/NTFS/exFAT
/dev/sda3       [COLOR=#ff0000]136927230[/COLOR]   976768064   419920417+   5  Extended

the end of sda2 is after the start of sda3.

You need to shrink sda2 by the amount of the overlap.

---

### Post by mevets on 2013-10-15
I see the problem. If I can ask, how do # of blocks translate to MBs so I know how much to shrink the C Drive?

---

### Post by mevets on 2013-10-15
Thanks! I shrunk my C drive by 11 mb and gParted can now see my partitions.

[IMG]http://i.imgur.com/1fxkhRN.png[/IMG]

---

