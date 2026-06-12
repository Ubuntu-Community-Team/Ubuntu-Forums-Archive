---
title: "fdisk in Oneiric - sectors and cylinders"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-08-24
Just discovered something interesting when asking someone to post the output of fdisk -lu and not fdisk -l in Lucid.

In Natty and before, fdisk -l gave you output in cylinders, which is about as much use as a chocolate teapot.

> **"man fdisk in Natty"]-l     List the partition tables for the  specified  devices  and  then
              exit.   If no devices are given, those mentioned in /proc/parti&#8208 said:**
> 

But in the version that comes in Oneiric, it has changed to defaulting to output in sectors.

[quote="man fdisk in Oneiric"]-u[=unit]
              When listing partition tables, show sizes  in  'sectors'  or  in
              'cylinders'.   The  default  is  to  show sizes in sectors.  For
              backward compatibility, it is possible to use the option without
              the <units> argument -- then the default is used.  Note that the
              optional <unit> argument cannot be separated from the -u  option
              by a space, the correct form is for example '-u=cylinders'.


I discovered this when doing a "sudo fdisk -l" in Oneiric to check and saw that the output was in sectors, not cylinders. Perhaps the fdisk devs got tired of chocolate-flavoured tea all over their desks. :)

---

### Post by srs5694 on 2011-08-24
This has been in the pipeline for a while. My Gentoo system, which now has util-linux 2.19.1 (vs. 2.17.2-9 for my Ubuntu 11.04 system) has been acting this way for a few months. As you say, it's a big improvement.

---

### Post by rbrick49 on 2011-08-24
here you go
ron@ornary:~$ fdisk -l
ron@ornary:~$ sudo fdisk -l
[sudo] password for ron: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000a614

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1026047      512000   83  Linux
/dev/sda2         1026048   488396799   243685376   8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000753ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1936748543   968373248   83  Linux
/dev/sdb2      1936750590  1953523711     8386561    5  Extended
/dev/sdb5      1936750592  1953523711     8386560   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044059

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1936748543   968373248   83  Linux
/dev/sdc2      1936750590  1953523711     8386561    5  Extended
/dev/sdc5      1936750592  1953523711     8386560   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca918

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   982091630   491044791+  83  Linux
/dev/sdd2       982091774  1953523711   485715969    5  Extended
/dev/sdd5      1936750592  1953523711     8386560   82  Linux swap / Solaris
/dev/sdd6       982091776  1919975423   468941824   83  Linux
/dev/sdd7      1919977472  1936748543     8385536   82  Linux swap / Solaris

---

### Post by coffeecat on 2011-08-24
> **srs5694 said:**
> This has been in the pipeline for a while. My Gentoo system, which now has util-linux 2.19.1 (vs. 2.17.2-9 for my Ubuntu 11.04 system) has been acting this way for a few months. As you say, it's a big improvement.

Just to confirm - the version of util-linux in Oneiric is also 2.19.1. (2.19.1-2ubuntu3 at the moment.)

---

