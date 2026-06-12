---
title: "fsck.vfat questions"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by PGScooter on 2008-08-15
Hi, I have an external fat32 hd and ran sudo vfat -av

```

dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
  Not automatically fixing this.
Boot sector contents:
System ID "mkdosfs"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     16384 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
  50305536 bytes per FAT (= 98253 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 100627456 (sector 196538)
  12576265 data clusters (206049525760 bytes)
63 sectors/track, 255 heads
         0 hidden sectors
 402637032 sectors total
FATs differ but appear to be intact. Using first FAT.
/diff from other drive/data1.dta
  Contains a free cluster (8984241). Assuming EOF.
/diff from other drive/data1.dta
  File size is 57597426 bytes, cluster chain length is 1638400 bytes.
  Truncating file to 1638400 bytes.
/diff from other drive/data2.dta
  Contains a free cluster (8988475). Assuming EOF.
/diff from other drive/data2.dta
  File size is 64106465 bytes, cluster chain length is 13139968 bytes.
  Truncating file to 13139968 bytes.

```

Regarding:
"There are differences between boot sector and its backup."
Is there anyway to see what these differences are? I do not know whether to choose the boot sector or its backup, can I make a backup of one and then overwrite it with the other?

are my data1.dta and data2.dta files corrupted then or will they be fine?

Thank you

---

### Post by PGScooter on 2008-08-16
bump

---

### Post by unutbu on 2008-08-16
I think TestDisk may be able to fix the boot sector problem. See [http://www.cgsecurity.org/wiki/Advanced_FAT_Repair#Recover_the_FAT32_boot_sector](http://www.cgsecurity.org/wiki/Advanced_FAT_Repair#Recover_the_FAT32_boot_sector)

To install testdisk on Ubuntu,```

sudo apt-get install testdisk
```

To burn a LiveCD with TestDisk included:
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

The TestDisk homepage:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by PGScooter on 2008-08-17
unutbu, I will check those out.

But actually fsck.vfat can fix the boot sector problem. I just don't know whether to copy from the backup or to the backup... How do I decide? Can I make a backup of the one that I will replace? thanks

---

### Post by figure002 on 2012-06-20
I would like to know the answer to PGScooter's question as well.

---

### Post by oldos2er on 2012-06-20
Please start a new thread; this one's four years old.

---

