---
title: "fdisk -l seems to show HD as being way bigger than it is."
date: 2017-08-12
forum: New to Ubuntu
---

### Post by bvz on 2017-08-12
Here is the output of sudo fdisk -l:

```
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xba4c49ad

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    718847    716800   350M  7 HPFS/NTFS/exFAT
/dev/sda2          718848 439900159 439181312 209.4G  7 HPFS/NTFS/exFAT
/dev/sda3       439902206 976771071 536868866   256G  5 Extended
/dev/sda5       951613440 976771071  25157632    12G 82 Linux swap / Solaris
/dev/sda6       439902208 951613439 511711232   244G 83 Linux

Partition table entries are not in disk order.
```

The thing that confuses me is that this is a 500GB SSD (465.8 GB according to fdisk).  But based on what I am looking at, it seems to show three, roughly 200GB - 250GB partitions (sda2, sda3, sda6).

How is that possible?  Or am I completely misreading this output?

---

### Post by spjackson on 2017-08-12
sda3 is an [extended partition]("https://en.wikipedia.org/wiki/Disk_partitioning#Extended_partition") It contains the logical partitions sda5 and sda6. You cannot mount sda3 directly.

---

### Post by Impavidus on 2017-08-12
Also, there's the difference between GB and GiB. Your hard drive is 500 GB, which equals 465.8 GiB.

---

### Post by vocx on 2017-08-12
> **bvz said:**
> Here is the output of sudo fdisk -l:
...
How is that possible?  Or am I completely misreading this output?
Correct, you are misreading the output.

> **spjackson said:**
> sda3 is an [extended partition]("https://en.wikipedia.org/wiki/Disk_partitioning#Extended_partition") It contains the logical partitions sda5 and sda6. You cannot mount sda3 directly.
Correct. An extended partition is just a box used to contain more partitions. So, the size of the box should equal the sum of the sizes of the partitions inside it.

Extended partitions surged many years ago because of limitations of the old hard drives. Extended partitions are not something specific to Linux, they are also used in Windows. However, in Windows they are usually never mentioned. Instead, the system only deals with the inner partitions directly as drive D:, E:, F:, etc.

So, an advantage of using Linux is that you learn a bit more about computer hardware and things like that. Regular Windows users rarely know any of this, even if they use their machine daily.

> **Impavidus said:**
> Also, there's the difference between GB and GiB. Your hard drive is 500 GB, which equals 465.8 GiB.

See here for an explanation on the difference between gigabyte (powers of 10), and gibibyte (powers of 2).
[https://ubuntuforums.org/showthread.php?t=2367647&p=13672122#post13672122](https://ubuntuforums.org/showthread.php?t=2367647&p=13672122#post13672122)

---

### Post by bvz on 2017-08-13
Brilliant! Thanks so much everyone. This has been very helpful.

---

