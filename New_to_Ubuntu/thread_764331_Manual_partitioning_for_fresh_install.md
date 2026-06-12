---
title: "Manual partitioning for fresh install"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by paker on 2008-04-23
As I learned from other threads,I partitioned a 150 GB hard disk into 3. First, 10 GB for (primary) (at the beginning) (/). Second, 4 GB for (swap)(primary) (at the end). Third, the the rest for (/home) (logical extension) (at the beginning), in this sequence.

But I got an error message saying the "/home" partition could not be created. What wrong did I do?

---

### Post by tamoneya on 2008-04-23
What did you select for the filesystem? is it a logical partition or a extended partition? Are there any other partitions on this drive? Post the contents of ```
sudo fdisk -l
```

---

### Post by Moop on 2008-04-23
A logical partition is contained in a extended partition. Extended partitions don't have file systems. You need to create a logical partition inside your extended partition.

---

### Post by paker on 2008-04-23
Since I didn't know what I was doing, I gave up and used the entire hard disk (formatted the whole hard disk). But I would like to know what wrong I did. I intend to replace the 150 GB PATA hard disk with a 500 GB SATA HD that I already have. 

What I did was, as far as I can remember,
10 GB, ext3, primary,
the rest, ext3, logical extension
4 GB, swap, primary

If I missed something, please let me know. Thanks.

Originally, the hard disk was used for ubuntu 7.10. I always used the entire disk for ubuntu installation, guided installation. But I learned recently that I had better have a separate /home partition. I was practsing manual partition for the first time.

---

### Post by rouge568 on 2008-04-23
I would keep at it until you get it right - it took me about 5 times to get it right my first time, and it was very worth it. The sheer security from knowing that even if you screw up you system, your data is safe is very comforting.

---

### Post by paker on 2008-04-23
> **Moop said:**
> A logical partition is contained in a extended partition. Extended partitions don't have file systems. You need to create a logical partition inside your extended partition.

Should I have done it this way then?

First, delete existing partition and create a new partition table. Now I have entire 150 GB.

Second, create (primary) (ext3) (/)

Third, create (extended) (ext3) (/home)

Fourth, create (primary) (swap).

Did I get it right this time?

---

### Post by Miljet on 2008-04-23
You still seem to be missing the point that an extended partition doesn't/can't contain files. It only contains logical partitions. Therefore you need to create one or more logical partitions within the extended partition for your home directory (or whatever you want to put there.

---

### Post by Moop on 2008-04-23
You can create one large extended partition to hold all your partitions if you wanted to. Swap is normallycreated inside a extended partition and not as a primary partition. Ubuntu doesn't require any partitions to be primary partitions. You have lots of choices. 

I'd say:
1. 10gb primary partition for /
2. extended partition that uses all the remaining space.
3. 2gb swap inside extended
4. the rest of the free space in the extended partition for /home

---

### Post by Paqman on 2008-04-23
You also don't *need* an extended partition is you've only got three partitions. You can have up to four primary partitions on a drive.

However, it's a good idea to include one, as it allows you to bust the four-partitions limit if you want to at a later date.

So what you need is:

hda1 10GB ext3 / (primary)
hda2 (extended partition)
hda3 XGB ext3 /home (logical) << contained within the extended part.
hda4 4Gb swap (primary)

Your swap seems a little large, btw. For PCs with a decent ammount of RAM (ie: over 1GB) you only need to make it equal to your RAM at the most.

---

### Post by paker on 2008-04-23
Thank you all. I would have never figured it out by myself. That's exactly what I will do when I swap out the hard drive.

[**problem solved**]

---

