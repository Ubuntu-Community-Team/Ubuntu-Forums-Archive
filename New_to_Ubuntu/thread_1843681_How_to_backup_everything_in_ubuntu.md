---
title: "How to backup everything in ubuntu?"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by jayi on 2011-09-13
Hi, right now I have a dual boot with Windows XP and Ubuntu 11.04. I installed Windows XP first and then Ubuntu 11.04.

Anyway, I realized I have not used Windows XP in many months so I just want to get rid of it and reinstall only Ubuntu 11.04 on my computer.

My questions are...

1) Is there some easy way to get rid of Windows XP and just give the free space to Ubuntu?
2) Otherwise, is there some easy way to backup all of my files, settings, and packages I installed for Ubuntu onto a USB drive? I don't need to backup Windows XP files.

---

### Post by oscarivera9 on 2011-09-13
Let me try to help you here.  First I'll need some information so here we go:
1.  How big is your current hard drive & how many partitions do you have?
2. How big is the external hard drive that you'll be using for the backup?

---

### Post by jayi on 2011-09-13
> **oscarivera9 said:**
> Let me try to help you here.  First I'll need some information so here we go:
1.  How big is your current hard drive & how many partitions do you have?
2. How big is the external hard drive that you'll be using for the backup?

1. Ok, when I click disk utility it says:

503 GB NTFS
497 GB Extended (493 GB ext4 and 4.3 GB swap space)

For the Ubuntu partition, I think I use less than 4 GB of space, everything else is free:

```
jay@desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            473871560   3623584 446176708   1% /
```2. My USB drive has 7.4 gigs of space.

---

### Post by oscarivera9 on 2011-09-13
You have two options, the first is to use GParted to do two things:
1. Delete the NTFS partition
2. Grow the Ext. 4 partition to fill up the drive
The only thing that worries me here is that apparently your Ubuntu partition is sda5, so I'm wondering if you have any other partitions besides the NTFS, Ext. 4 and Swap.

Second option is to use something like Deja Dup to backup everything onto your flash drive and then do a fresh install of Ubuntu.

I would personally go with the first choice but be ready to let the computer take its time doing that task.  It might take GParted more than a couple of hours.
Maybe you might want to wait a bit to see what someone else thinks about this but using GParted is probably the easiest way to go about it.  If you don't have GParted, you can get it through the Software Center.

---

