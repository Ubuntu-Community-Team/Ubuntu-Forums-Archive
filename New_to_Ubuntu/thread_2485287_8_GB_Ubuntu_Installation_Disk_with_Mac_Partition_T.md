---
title: "8 GB Ubuntu Installation Disk with Mac Partition Table"
date: 2023-03-25
forum: New to Ubuntu
---

### Post by bhubunt on 2023-03-25
This is a left-over question from another thread. It concerns an 8GB stick with an 18.08 Ubuntu installation software package on it. 

Previously this strange reading came up during a live session, but the same reading also appears on a stable Ubuntu 20.04 OS.

Thoughts welcome.

```
 Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? ignore                                                     
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 31,0GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      6150kB  8673kB  2523kB               EFI


```

---

### Post by TheFu on 2023-03-25
Ubuntu ISO files have been using a hybri-Mac/PC partition scheme for over a decade. It helps support booting on UEFI and legacy systems ... and perhaps on Mac hardware.

---

### Post by MAFoElffen on 2023-03-25
Kingston USB thumb drives, with less than 32GB of storage, come (by default) with an MSDOS partition table, and formatted to Fat32.

I have no (sure) idea how it could have been replaced with an Apple Partition table. 

Most image USB creation uilitiies do not replace the partition table, but rather use whatever is already there. I would suggest that you use GParted > Device > New Partition Table > Select "MSDOS"... Then create a new partition, formatted to Fat32... Then reburn the live image.

That should resolve any future problems that might arise from that.

---

### Post by TheFu on 2023-03-25
I use 
```
sudo cp /path/to/ubuntu-xx.yy.iso  /dev/sdz

```to create installation media for Ubuntu all-the-time onto flash storage. No need to think or lookup fancy programs or waste space with those tools.  Anyway, the result is a hybrid partition table on the flash storage. Works for thumb-drives and SDHC/micrSD cards.
It creates a funky partition setup.  I think this is one:
```
Disk /dev/sdc: 7.5 GiB, 8022654976 bytes, 15669248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x36c74be4

Device     Boot   Start      End  Sectors  Size Id Type
/dev/sdc1  *          0  2747135  2747136  1.3G  0 Empty
/dev/sdc2          4264    12263     8000  3.9M ef EFI (FAT-12/16/32)
/dev/sdc3       2748416 15669247 12920832  6.2G 83 Linux
```
Note how sdc1 overlaps the other partitions?  I think that's an Ubuntu 20.04 image.

---

### Post by bhubunt on 2023-03-27
> **MAFoElffen said:**
> Kingston USB thumb drives, with less than 32GB of storage, come (by default) with an MSDOS partition table, and formatted to Fat32.

I have no (sure) idea how it could have been replaced with an Apple Partition table. 



Just curious: what are some possibilities?

---

### Post by MAFoElffen on 2023-03-27
Possibilities? For a start, that depends on "the utility" that you wrote the LiveUSB with. Another would be the model of the USB thumb drive and what OS('es) it said it supported. The list of possibilities are many.

---

### Post by bhubunt on 2023-03-27
> **MAFoElffen said:**
> Possibilities? For a start, that depends on "the utility" that you wrote the LiveUSB with. Another would be the model of the USB thumb drive and what OS('es) it said it supported. The list of possibilities are many.

The model of the USB is a Kingston DT50. 

 I did not make the Live USB. 

Do you mean with "utility" something like a Mac computer?

---

### Post by TheFu on 2023-03-27
> **bhubunt said:**
> Just curious: what are some possibilities?

The big 3 are 
[LIST]
[*]MSDOS / MBR
[*]GPT
[*]Apple-something.
[/LIST]

UNIX flavors can have different ones too.

BTW, there was no "18.08" Ubuntu.

---

### Post by bhubunt on 2023-03-28
typo: Ubuntu 18.04 

So either the live disk was made on a Mac or the live disk was later accessed by a Mac, so that the partition table was changed?

---

### Post by The Cog on 2023-03-28
Look at the sizes of the partitions (first post). They are 4096B and 2523kB. There is no installer there. 
My guess is that the stick has been re-partitioned by the mac, overwriting whatever partitioning was there before.

---

### Post by bhubunt on 2023-03-28
> **The Cog said:**
> 
My guess is that the stick has been re-partitioned by the mac, overwriting whatever partitioning was there before.

A valuable insight.

---

### Post by TheFu on 2023-03-28
> **bhubunt said:**
> typo: Ubuntu 18.04 

So either the live disk was made on a Mac or the live disk was later accessed by a Mac, so that the partition table was changed?

If you used 'dd' (or any of the other "burning from ISO" tools to copy the ubuntu-xyz.iso file to the USB flash drive, you get a hybrid partition table. The way the ISO was mastered is what determined this.  ISOs are read-only, except during the mastering process which is controlled by Canonical release managers. It is nothing you did.

---

### Post by bhubunt on 2023-03-28
> **The Cog said:**
> 

Look at the sizes of the partitions (first post). They are 4096B and 2523kB. There is no installer there. 
My guess is that the stick has been re-partitioned by the mac, overwriting whatever partitioning was there before.

Thanks, The Cog. That is very convincing as an explanation indeed.

---

