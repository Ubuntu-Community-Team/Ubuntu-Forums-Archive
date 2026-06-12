---
title: "Unallocated in GParted"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by Shadius on 2012-05-29
Hey everybody :)

I wanted to see how my HDDs looked in GParted so I opened it up and it shows my /dev/sda, which Windows XP Home Edition SP3 is installed on, as unallocated. Why? Is something wrong here? It shows my /dev/sdb HDD which has Ubuntu 12.04 on it just fine. So what's the problem here and how do I fix it?

---

### Post by plucky on 2012-05-30
> **Shadius said:**
> Hey everybody :)

I wanted to see how my HDDs looked in GParted so I opened it up and it shows my /dev/sda, which Windows XP Home Edition SP3 is installed on, as unallocated. Why? Is something wrong here? It shows my /dev/sdb HDD which has Ubuntu 12.04 on it just fine. So what's the problem here and how do I fix it?
 
It could that it thinks the partition is dirty as XP didn't do a clean shutdown.Boot the Live CD and see if gparted shows the same.

Or boot XP and run a DSKCHK on the XP partition.

Good Luck

---

### Post by coffeecat on 2012-05-30
The most common reason for Gparted showing a whole drive as unallocated is an illegal entry in the partition table. Often with these an operating system will still from bootup and run, but it confuses the parted backend. The usual problems are the last sector of an extended partition recorded as being physically outside the hard drive, overlapping partitions, or a primary partition inside an extended partition (which is impossible). Apps which can cause these problems are testdisk (which can produce the first) or some 3rd party Windows partitioning tools which seem to be quite cavalier with the partition table.

So that we can see what the recorded contents of the partition table for /dev/sda is, open a terminal in Ubuntu and post the output of this command:

```
sudo fdisk -lu
```

Please post the output between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by Shadius on 2012-05-30
> **coffeecat said:**
> The most common reason for Gparted showing a whole drive as unallocated is an illegal entry in the partition table. Often with these an operating system will still from bootup and run, but it confuses the parted backend. The usual problems are the last sector of an extended partition recorded as being physically outside the hard drive, overlapping partitions, or a primary partition inside an extended partition (which is impossible). Apps which can cause these problems are testdisk (which can produce the first) or some 3rd party Windows partitioning tools which seem to be quite cavalier with the partition table.

So that we can see what the recorded contents of the partition table for /dev/sda is, open a terminal in Ubuntu and post the output of this command:

```
sudo fdisk -lu
```

Please post the output between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

Here you go coffeecat
```
shadius@shadius-5410US:~$ sudo fdisk -lu
[sudo] password for shadius: 
omitting empty partition (5)

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    68750639    34375288+   7  HPFS/NTFS/exFAT
/dev/sda2        68742135    78155279     4706572+   f  W95 Ext'd (LBA)
/dev/sda5        69975423    78155279     4089928+   b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003daca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   154300415    77149184   83  Linux
/dev/sdb2       154302462   156301311      999425    5  Extended
/dev/sdb5       154302464   156301311      999424   82  Linux swap / Solaris
shadius@shadius-5410US:~$ 

```

I also viewed the information of the drive by right clickingi on it and selecting **Information** and noticed that there is a warning about overlapping partitions, as you can see by my screenshot.

---

### Post by coffeecat on 2012-05-30
Indeed. Here are the overlapping partitions:

> **Shadius said:**
> ```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    [COLOR="Red"]68750639[/COLOR]    34375288+   7  HPFS/NTFS/exFAT
/dev/sda2        [COLOR="Red"]68742135[/COLOR]    78155279     4706572+   f  W95 Ext'd (LBA)
/dev/sda5        69975423    78155279     4089928+   b  W95 FAT32
```

I've highlighted the problem figures in red. My guess is that it's the start sector of the extended partition sda2 which is wrong because the start sector of the logical sda5 partition does not overlap the end sector of sda1. (Logical partitions are contained within an extended partition.) But that's only a guess.

This should be easy to fix. Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fixparts *should* repair this anomaly automatically, but make sure you understand what is going on before you launch fixparts and then you should be OK. Also - be sure to make a backup of your current partition table with sfdisk as described in that link before you proceed. As you can see, there are versions of fixparts for Linux and for Windows, so you have a choice. Just be sure to download and run fixparts and not gdisk - hence Rod Smith's warning. I have been invloved in a thread where I recommended fixparts and the OP downloaded and ran gdisk and converted a small hole into a very big one! This is why I always repeat Rod's warning.

---

### Post by Shadius on 2012-05-30
> **coffeecat said:**
> Indeed. Here are the overlapping partitions:



I've highlighted the problem figures in red. My guess is that it's the start sector of the extended partition sda2 which is wrong because the start sector of the logical sda5 partition does not overlap the end sector of sda1. (Logical partitions are contained within an extended partition.) But that's only a guess.

This should be easy to fix. Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fixparts *should* repair this anomaly automatically, but make sure you understand what is going on before you launch fixparts and then you should be OK. Also - be sure to make a backup of your current partition table with sfdisk as described in that link before you proceed. As you can see, there are versions of fixparts for Linux and for Windows, so you have a choice. Just be sure to download and run fixparts and not gdisk - hence Rod Smith's warning. I have been invloved in a thread where I recommended fixparts and the OP downloaded and ran gdisk and converted a small hole into a very big one! This is why I always repeat Rod's warning.

Thank you very much. Looks like I've got some reading to do!

---

