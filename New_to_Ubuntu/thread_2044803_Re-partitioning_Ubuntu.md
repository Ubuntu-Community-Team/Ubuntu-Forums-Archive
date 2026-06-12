---
title: "Re-partitioning Ubuntu"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by ub07 on 2012-08-20
Currently I have only Ubuntu installed on my computer. I want to install another OS alongside Ubuntu, and this is going to mean that I have to shrink a partition to make room for the other OS. Here is my output of fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   306819071   153408512   83  Linux
/dev/sda2       306821118   312580095     2879489    5  Extended
/dev/sda5       306821120   312580095     2879488   82  Linux swap / Solaris

```


My question is what is that small partition labeled "Extended"? Also, I notice that there is no boot partition. Will there be a conflict if I create a boot partition for the other OS?

Thanks in advance.

---

### Post by Wim Sturkenboom on 2012-08-20
In a partitioning scheme you can have up to 4 *primary* partitions. If you need more partitions, one of them needs to be an *extended* partition in which you can fit *logical* partitions.

So the extended partition is a container for logical partitions. Nowadays automatic partitioning seems to create only one primary and place all the other partitions as logical partitions in the extended partition.

If you delete sda2 (the extended partition), you will also delete sda5 (the logical partition inside it).

===

It's not a problem that you don't have a boot partition; the boot information is now simply in the /boot directory.

===

Last note:
unless you use hibernate / suspend to ram, you can share the swap partition between different distros.

---

### Post by black veils on 2012-08-20
so you delete sda2 and sda5, shrink sda1, then use your new linux install media to do the rest. you want to create an ext4 partition for the system (which includes everything), then a swap partition (at the end i suppose).

you will have a choice somewhere of where to put grub, i am not sure what you do with that considering your current setup.

and i just remembered, this needs to be done with bootable media (so no systems or swap partitions are mounted), you may need to right-click** swap off** during your live media session, before altering.

[COLOR=DarkRed]*and like [Wim Sturkenboom]("http://ubuntuforums.org/member.php?u=5214") signiture suggests, make backups of all your data before editing partitions.*[/COLOR]

---

### Post by ame82 on 2012-08-20
hi
i did a mistake when i installed ubuntu , that i made one partion ext3 as home then i made 1 gb swap, and now i want to expand my home partion , and relocate swap in the begining as i want to install vbox and install wind7 
how can i do that without crashing the system
what is the best ext type i can use eg(ext3,4 or 2)
thanks

---

### Post by Wim Sturkenboom on 2012-08-20
@ame82

please start your own thread; this will eventually get confusing

---

### Post by ub07 on 2012-08-20
> **black veils said:**
> so you delete sda2 and sda5, shrink sda1, then use your new linux install media to do the rest. you want to create an ext4 partition for the system (which includes everything), then a swap partition (at the end i suppose).

you will have a choice somewhere of where to put grub, i am not sure what you do with that considering your current setup.

and i just remembered, this needs to be done with bootable media (so no systems or swap partitions are mounted), you may need to right-click** swap off** during your live media session, before altering.

[COLOR=DarkRed]*and like [Wim Sturkenboom]("http://ubuntuforums.org/member.php?u=5214") signiture suggests, make backups of all your data before editing partitions.*[/COLOR]

Thanks. So it is ok to delete sda2?

This is the default partitioning scheme of Ubuntu (I didn't do anything custom). I suspect that boot was placed on the primary partition. That is what worries me about creating a special boot partition because then I will have /boot as a directory in the Ubuntu partition as well as a separate /boot partition.

---

### Post by ub07 on 2012-08-20
> **Wim Sturkenboom said:**
> In a partitioning scheme you can have up to 4 *primary* partitions. If you need more partitions, one of them needs to be an *extended* partition in which you can fit *logical* partitions.

So the extended partition is a container for logical partitions. Nowadays automatic partitioning seems to create only one primary and place all the other partitions as logical partitions in the extended partition.

If you delete sda2 (the extended partition), you will also delete sda5 (the logical partition inside it).


Thanks for replying! How do you know that sda5 is inside of sda 2?

> **Wim Sturkenboom said:**
> 
It's not a problem that you don't have a boot partition; the boot information is now simply in the /boot directory.

But will there be a conflict between the boot partition that I create and the boot directory inside the Ubuntu partition?

> **Wim Sturkenboom said:**
> 
Last note:
unless you use hibernate / suspend to ram, you can share the swap partition between different distros.

Thanks, I did not know that.

---

### Post by ub07 on 2012-08-20
> **Wim Sturkenboom said:**
> In a partitioning scheme you can have up to 4 *primary* partitions. If you need more partitions, one of them needs to be an *extended* partition in which you can fit *logical* partitions.


Can you point me to some resource where I can read up on this? Because I'm now worried about exceeding the 4 primary partitions. I'm not sure how to connect a logical partition to a primary extended partition.

---

### Post by ub07 on 2012-08-20
I have another computer where I am running Kubuntu, but I have many partitions between Windows and Kubuntu:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbdc35f75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    41945087    20971520   27  Hidden NTFS WinRE
/dev/sda2   *    41945088    42149887      102400    7  HPFS/NTFS/exFAT
/dev/sda3        42149888   430429544   194139828+   7  HPFS/NTFS/exFAT
/dev/sda4       430429606   976771071   273170733    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       430429608   536201504    52885948+   b  W95 FAT32
/dev/sda6       536203264   536494079      145408   83  Linux
/dev/sda7       536496128   731805695    97654784   83  Linux
/dev/sda8       731807744   953094143   110643200   83  Linux
/dev/sda9       953096192   976771071    11837440   82  Linux swap / Solaris


```

How do I tell which of these are logical?

---

### Post by black veils on 2012-08-20
> **ub07 said:**
> I have another computer where I am running Kubuntu, but I have many partitions between Windows and Kubuntu:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbdc35f75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    41945087    20971520   27  Hidden NTFS WinRE
/dev/sda2   *    41945088    42149887      102400    7  HPFS/NTFS/exFAT
/dev/sda3        42149888   430429544   194139828+   7  HPFS/NTFS/exFAT
/dev/sda4       430429606   976771071   273170733    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       430429608   536201504    52885948+   b  W95 FAT32
/dev/sda6       536203264   536494079      145408   83  Linux
/dev/sda7       536496128   731805695    97654784   83  Linux
/dev/sda8       731807744   953094143   110643200   83  Linux
/dev/sda9       953096192   976771071    11837440   82  Linux swap / Solaris


```How do I tell which of these are logical?


**sda1** to **sda4** are primary

**sda5** onwards are logical

---

### Post by oldfred on 2012-08-20
Primary partitions are sda1 thru sda4. The extended can be any one (and only one) of the primary partitions and is used just as a container for logical partitions.

Logical partitions start at sda5 and you essentially can have an unlimited number of logical partitions.

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

