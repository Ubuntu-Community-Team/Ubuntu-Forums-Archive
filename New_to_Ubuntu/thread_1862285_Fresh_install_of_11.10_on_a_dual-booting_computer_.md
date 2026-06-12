---
title: "Fresh install of 11.10 on a dual-booting computer - partition question."
date: 2011-10-16
forum: New to Ubuntu
---

### Post by altheablue on 2011-10-16
Hello all.
I'm running Ubuntu 11.10 Beta, dual booting with Windows Vista. 

I have two (silly) questions. First, is there an option that I'm missing to simply upgrade the 11.10 beta to the official release? It doesn't seem to happen through updates. 

Second, if I do a fresh install of 11.10 (which I know most people say is better), would someone verify for me that the partition it needs to go onto is dev/sda5 (see below)? I'm not brand new to Ubuntu, but I am new to (and scared of! ;)) partitioning and managing partitions.  

This is the output of ```
sudo fdisk -lu
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   309399551   154699744+   7  HPFS/NTFS/exFAT
/dev/sda2       309399552   606660607   148630528    5  Extended
/dev/sda3       606662595   625137344     9237375    7  HPFS/NTFS/exFAT
/dev/sda5       309401600   601151487   145874944   83  Linux
/dev/sda6       601153536   606660607     2753536   82  Linux swap / Solaris

Much appreciation if anyone can answer my silly questions. :)

---

### Post by TeoBigusGeekus on 2011-10-16
> **altheablue said:**
> Hello all.
I'm running Ubuntu 11.10 Beta, dual booting with Windows Vista. 

I have two (silly) questions. First, is there an option that I'm missing to simply upgrade the 11.10 beta to the official release? It doesn't seem to happen through updates. 

Second, if I do a fresh install of 11.10 (which I know most people say is better), would someone verify for me that the partition it needs to go onto is dev/sda5 (see below)? I'm not brand new to Ubuntu, but I am new to (and scared of! ;)) partitioning and managing partitions.  

This is the output of ```
sudo fdisk -lu
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   309399551   154699744+   7  HPFS/NTFS/exFAT
/dev/sda2       309399552   606660607   148630528    5  Extended
/dev/sda3       606662595   625137344     9237375    7  HPFS/NTFS/exFAT
/dev/sda5       309401600   601151487   145874944   83  Linux
/dev/sda6       601153536   606660607     2753536   82  Linux swap / Solaris

Much appreciation if anyone can answer my silly questions. :)

Yeap! sda5 is the partition you need to use.
When you reach the partitioner, select manual partitioning (or something else, or I'll do it myself, or whatever it's called).
Select sda5, right click it and select ext4 as its file system, / as its mount point. Choose also to format the partition.
Then select sda6, right click it and select swap as its file system.
That's it.

EDIT: There are no silly questions. Happy linuxing.

---

### Post by gsmanners on 2011-10-16
11.10 beta to 11.10 release is as easy as:

```
sudo apt-get update
sudo apt-get upgrade
```

And, yeah. /dev/sda5 appears to be your old root partition.

---

### Post by altheablue on 2011-10-16
> **TeoBigusGeekus said:**
> Yeap! sda5 is the partition you need to use.
When you reach the partitioner, select manual partitioning (or something else, or I'll do it myself, or whatever it's called).
Select sda5, right click it and select ext4 as its file system, / as its mount point. Choose also to format the partition.
Then select sda6, right click it and select swap as its file system.
That's it.

EDIT: There are no silly questions. Happy linuxing.

Thank you! That is what I needed to know.

Btw, I like your signature. I use Autodesk Revit. :)

---

### Post by altheablue on 2011-10-16
> **gsmanners said:**
> 11.10 beta to 11.10 release is as easy as:

```
sudo apt-get update
sudo apt-get upgrade
```

And, yeah. /dev/sda5 appears to be your old root partition.

Thanks. I have done that. Honestly, I don't know how to tell if I'm running the official install already, except that some packages that the officlal were slated to remove are still on my system. (If that makes any sense.) :)

---

### Post by TeoBigusGeekus on 2011-10-16
> **altheablue said:**
> I use Autodesk Revit. :)

Try Archicad - it's better.;)

---

### Post by altheablue on 2011-10-16
> **TeoBigusGeekus said:**
> Try Archicad - it's better.;)

Haha, I've heard that before! I've never used it, but I don't think my work will go for it. :/ ;)

---

