---
title: "Paritioning Naming Confusion"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by mapes12 on 2008-05-30
Here's the output from querying my partitions from the command line. They are all in the same physical drive:
> mark@ubuntu-laptop:~$ sudo sfdisk -l
[sudo] password for mark:

Disk /dev/sda: 2432 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   1282    1283-  10305666   83  Linux
/dev/sda2       2325    2431     107     859477+   5  Extended
/dev/sda3       1283    2324    1042    8369865   83  Linux
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       2325+   2431     107-    859446   82  Linux swap / Solaris
mark@ubuntu-laptop:~$ 

But when I load gparted liveCD the GUI lists the partitions as hda1 etc. and it does not see the sda4 partition. With regard to the latter I have no idea how it got there. I created sda3 (via gparted but in gparted it came up as hda3) to move my /home partition onto but cannot figure out where this sda4 empty partition has come from??

So why does the command line list the partitions as sda* and gparted hda*?

---

### Post by shifty_powers on 2008-05-30
i think you can ignore it. it is 0 blocks anyways. maybe it is the primary partition that the other extended partitions are based in? (my knowledge of this is a bit rusty...)

as for sda and hda they are interchangeable, and nothing to worry about ;)

---

### Post by indytim on 2008-05-30
Just a wag... is it your extended partition?

IndyTim

---

### Post by crashcoredump on 2008-05-30
```
jayzao@Penguin:~$ sudo sfdisk -l
[sudo] password for jayzao: 

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  18661   18662- 149902483+  83  Linux
/dev/sda2      18662   19456     795    6385837+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      18662+  19456     795-   6385806   82  Linux swap / Solaris
jayzao@Penguin:~$ 
```

That is odd? I have some marked in the same manner.
But they are 0 blocks so I don't think they matter.

---

### Post by Duck2006 on 2008-05-30
When you run gparted how do the partitions show up, you may just be able to delete them.

---

### Post by lswest on 2008-05-30
I just checked, and sfdisk -l shows my extended partition as 0 blocks, and that will be what yours is too.  fdisk -l ignores it.

---

### Post by mapes12 on 2008-05-30
It makes the sda4 thing disappear but the sda* issue remains:

> mark@ubuntu-laptop:~$ sudo fdisk -l
[sudo] password for mark:

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x663c5122

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1283    10305666   83  Linux
/dev/sda2            2326        2432      859477+   5  Extended
/dev/sda3            1284        2325     8369865   83  Linux
/dev/sda5            2326        2432      859446   82  Linux swap / Solaris

Partition table entries are not in disk order
mark@ubuntu-laptop:~$ 


---

### Post by mapes12 on 2008-05-30
I've attached a screenshot of gparted for comparing against the Terminal output. Thanks

---

### Post by indytim on 2008-05-30
Is your HD sata or ata ?  Generally the sd<ltr> designation is deployed to sata drives and the hd<ltr> for the ata.  This naming convention may have gone away with recent ops version, not sure.

IndyTim

---

### Post by mapes12 on 2008-05-31
> Is your HD sata or ata ? Generally the sd<ltr> designation is deployed to sata drives and the hd<ltr> for the ata. This naming convention may have gone away with recent ops version, not sure.


The machine is an old PIII with an IDE drive. Definitely not a modern SATA.

---

