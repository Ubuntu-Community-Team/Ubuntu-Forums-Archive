---
title: "Partitions issue"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by EB0V on 2012-05-23
Hi! 

Is it possible to merge the file system partition with another empty partition from within ubuntu? without being forced to format or re-install Ubuntu?

---

### Post by coffeecat on 2012-05-23
You would need to delete the empty partition and then resize the partition you want to keep into the freed space. If this is your Ubuntu root partition, you cannot do this from within Ubuntu. You would need to use a live CD. Also, the space freed by the empty partition would need to be contiguous with (adjacent to) the partition you want to enlarge.

Perhaps you could post a screenshot of an open Gparted window (or Disk Utility window) so that we can see exactly what you want to do.

---

### Post by Jose Catre-Vandis on 2012-05-23
Yes and no ;)

Best thing to do it to run a Live CD with gparted on it, run that, delete the "empty partition" and expand the file system partition.

This advice is for Linux partitions. If you want to do this with a Windows (7) partition, boot into Windows and use the tool in there to do it.

Back up data/install first if not comfortable with this type of thing.

---

### Post by EB0V on 2012-05-23
Thanks! Actually I think they're not adjacent, there is a SWAP partition in between.

[IMG]http://i46.tinypic.com/f0q9zn.png[/IMG]

---

### Post by EB0V on 2012-05-23
So Live CD it is! Thanks guys!

---

### Post by coffeecat on 2012-05-23
> **EB0V said:**
> Thanks! Actually I think they're not adjacent, there is a SWAP partition in between.

There is no swap partition showing in your screenshot. Which partitions do you want to merge?

---

### Post by EB0V on 2012-05-23
> **coffeecat said:**
> There is no swap partition showing in your screenshot. Which partitions do you want to merge?
sda5 and sda6, actually the SWAP partition is the one highlighted I don't why it doesn't show on Gparted but it does show on Disk Utility!

---

### Post by EB0V on 2012-05-23
Here's a screenshot of Disk Utility 

[IMG]http://i48.tinypic.com/30wxh5v.png[/IMG]

---

### Post by coffeecat on 2012-05-23
> **EB0V said:**
> sda5 and sda6, actually the SWAP partition is the one highlighted I don't why it doesn't show on Gparted but it does show on Disk Utility!

There's also another discrepancy between disk utility and Gparted. Gparted is showing an ext4 partition of 5.72GiB (sda6). Disk Utility shows free space of 6.1GB instead. I suggest you post the output of this terminal command so we can be sure what your partition table is like:

```
sudo fdisk -lu
```

If you highlight the output, you can right-click -> copy in order to paste it into your post. Please enclose the output between [noparse]```
 and 
```[/noparse] tags otherwise you will lose formatting.

---

### Post by EB0V on 2012-05-23
Here it is:

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x99f3445e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   215541759   107667456    7  HPFS/NTFS/exFAT
/dev/sda3       215543806   256499711    20477953    5  Extended
/dev/sda4       256501760   625139711   184318976    7  HPFS/NTFS/exFAT
/dev/sda5       215543808   240453631    12454912   83  Linux
/dev/sda6       244493298   256493789     6000246   83  Linux


```

---

### Post by coffeecat on 2012-05-23
The output of fdisk agrees with Gparted, not Disk Utility. You have 2 logical ext4 partitions in your extended partition with 1.93GiB (2.1GB) of unused space between them. The discrepancy between the figures between Gparted and Disk Utility is because Gparted reports in Gibibytes (GiB) and Disk Utility in Gigabytes (GB).

1 GiB = 1024x1024x1024 bytes.
1 GB = 1000x1000x1000 bytes.

(For the purposes of this post. There are some who use Gigabyte to mean 1024x1024x1024 bytes. Let's not get into that old argument.)

---

### Post by EB0V on 2012-05-23
Alright! So what should I do? Still use a live CD to enlarge the system partition and to create a swap partition?

---

### Post by coffeecat on 2012-05-23
Partition sda6 appears to be empty, so you could delete that. But there's an exclamation mark by sda5 and no figures in the used/unused columns, which means there is a problem with it. Is that your Ubuntu root partition? Can you still boot into it?

---

### Post by EB0V on 2012-05-23
Yes! I'm using it right now!

---

### Post by coffeecat on 2012-05-23
> **EB0V said:**
> Yes! I'm using it right now!

You need to be cautious about that partition. If that was my system, I would check the partition from gparted. From Gparted in the live CD session, right-click on sda5 and choose "Check" to do a filesystem check. Only if this completes successfully would I then attempt to enlarge sda5 into the space freed by deleting sda6.

Huge warning. As you've been advised before, backup everything of importance before manipulating those partitions. Resizing partitions has the potential for something going wrong. What with the warning that Gparted is giving you, this might just be more likely in your situation.

---

### Post by EB0V on 2012-05-23
You were right, there is something wrong with that partition. I tried to restart the system to check if everything is in order but it wouldn't load. Not even GRUB! (Hopefully I use Ubuntu One for the backup).

---

### Post by EB0V on 2012-05-23
I have this message :

```

error: no such partition.
grub rescure> _

```

---

### Post by coffeecat on 2012-05-23
> **EB0V said:**
> I have this message :

```

error: no such partition.
grub rescure> _

```

Yes - I'm afraid something's gone seriously wrong with that partition. The error you are seeing is from grub code in the extended mbr (also called embedding area) which is between the partition table and the first partition. It can't find sda5.

Another thought - what with the discrepancies between the information from Gparted and Disk Utility (are you sure you didn't do any partition work between getting the two screenshots?) you need to exclude hard drive problems. You can do this from Disk Utility in the live CD session. Look for SMART status in Disk Utility and for self-tests.

---

### Post by EB0V on 2012-05-23
Actually, I had 4 SWAP partitions (I guess they got created everytime I tried to upgrade to next Ubuntu distribution) so I wanted to get rid of them and I deleted three of them. That's where the free space comes from.

[IMG]http://s15.postimage.org/5r4a4ak6j/Selection_016.png[/IMG]

So now, I guess I just do a clean installation of Ubuntu after formatting all these extra partitions to avoid any complications in the future, right?

---

### Post by coffeecat on 2012-05-23
If you create the partition layout you want with Gparted and then choose "something else" at the partitioning stage of the installer, you can ensure that Ubuntu gets installed to the partitions you want and no extra swap partitions will be created. In the "something else" option, simply designate your ext4 partition as '/' (=root). You don't have to worry about the swap partition. If you have already created it before starting the installation, the installer will detect it automatically.

You can create your partition layout from within "something else" if you wish. I simply prefer to do it with Gparted before starting the installer. The choice is yours.

I do strongly suggest that you run a SMART test from Disk Utility first. You have experienced some odd things that are not quite explainable.

---

### Post by EB0V on 2012-05-23
I figured it would be easier to just do a clean installation of Ubuntu instead, since I couldn't run disk utility. My drive needed to be cleaned up anyway.

Coffeecat! Thanks again for your time and advice, I appreciate it man!

---

