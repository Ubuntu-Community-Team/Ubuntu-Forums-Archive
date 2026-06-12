---
title: "Disk partition"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by tapasray on 2008-11-08
I am trying to turn my Acer Aspire laptop, running Windows XP, into a dual-boot machine by install 8.10. But the disk partitioning issue stumps me. 

My 80 GB hard drive has two partitions in Windows. C shows 38.2/35.5 GB capacity with 24.2/22.5 GB used and 14/13 GB free. D shows 38.7/36 GB capacity with 13.5/12.5 GB used and 25.2/23.4 GB used. I suppose the missing capacity is being used as virtual memory. The file system is FAT32 for both drives.

I want to repartition the disk in such a way that I can store my documents at a single location and work on them in either OS according to need. I believe music (and videos, which I don't have) should be stored on a separate partition. When I reach the disk partition stage in the 8.10 installation, it shows three existing drives, dev/sd0 (about 5 GB), and dev/sd1 and sd2, with capacities and usages corresponding to C and D. I cannot determine what the new partition table should look like, and how I can ensure that each file/folder I already have on C and D goes to exactly that new partitions to which I want it to go.

I would appreciate some help with this.

---

### Post by brandoncolorado on 2008-11-08
I believe this is going to be pretty tough.  Move your windows installation onto one partition.  Setup Linux on the second partition.  Give Linux access to your Windows files for your music and other media.  You could use Gparted to help with this on the Ubuntu liveCD.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by tapasray on 2008-11-08
Thanks! I'm going to try this.



> **brandoncolorado said:**
> I believe this is going to be pretty tough.  Move your windows installation onto one partition.  Setup Linux on the second partition.  Give Linux access to your Windows files for your music and other media.  You could use Gparted to help with this on the Ubuntu liveCD.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by maybeway36 on 2008-11-08
You could just resize C and D and make a new partition in the free space for Ubuntu.

---

### Post by handydan918 on 2008-11-08
+1 for just resizing and installing Ubu to the freespace.
BUT.

ALWAYS backup your data before doing ANY partitioning operation. 99% of the installations go without a hitch, but there are thousands of installations per day, so it' always pretty close to "your turn".

---

### Post by mc4man on 2008-11-09
Glad you got moving forward, would be interested to know what you think of kde4.x, I found it 'interesting' to say the least.

---

### Post by tapasray on 2008-11-09
Yes, I should consider that too. Thanks for the suggestion.


> **brandoncolorado said:**
> I believe this is going to be pretty tough.  Move your windows installation onto one partition.  Setup Linux on the second partition.  Give Linux access to your Windows files for your music and other media.  You could use Gparted to help with this on the Ubuntu liveCD.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

> **maybeway36 said:**
> You could just resize C and D and make a new partition in the free space for Ubuntu.

Yes, I have more or less everything that matters, backed up. 


> **handydan918 said:**
> +1 for just resizing and installing Ubu to the freespace.
BUT.

ALWAYS backup your data before doing ANY partitioning operation. 99% of the installations go without a hitch, but there are thousands of installations per day, so it' always pretty close to "your turn".

Thanks. I do hope it won't be so interesting that I have to start over with Ubuntu. Will let you know once I get it running.


> **mc4man said:**
> Glad you got moving forward, would be interested to know what you think of kde4.x, I found it 'interesting' to say the least.

brandoncolorado and others, 

I have completed the repartitioning with Gparted. Now I have three partitions instead of two (C and D), all three set for the DOS mount point and fat32 file system. This is the new configuration:

/dev/sda
    /dev/sda1      3.142 mb
    /dev/sda2    27.2   mb
    /dev/sda3    32.5   mb
    /dev/sda4    17.1   mb

I am assuming sda1 is the Windows virtual memory. sda2 and sda4 are the shrunken versions of C and D, respectively. I want to allocate sda3 to Intrepid (8.10). 

1. I am not sure this is a correct configuration, because somewhere in the literature I found a partition allocated for "swap space" that should be double the memory. I am not sure which memory - the RAM, which in my machine is 512 mb, or the virtual memory. In any case, I was unable to create an additional partition for this swap space. Gparted said I could not have more than 4 partitions.

2. When I click "Forward" with the above configuration(sda1, 2, 3 and 4), I get this message: "No root file system defined. Please correct this from the partition menu". I do not know what to do now! The "Help" link in the installer screen does not work!


  
> **brandoncolorado said:**
> I believe this is going to be pretty tough.  Move your windows installation onto one partition.  Setup Linux on the second partition.  Give Linux access to your Windows files for your music and other media.  You could use Gparted to help with this on the Ubuntu liveCD.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by handydan918 on 2008-11-09
> **tapasray said:**
> brandoncolorado and others, 

I have completed the repartitioning with Gparted. Now I have three partitions instead of two (C and D), all three set for the DOS mount point and fat32 file system. This is the new configuration:

/dev/sda
    /dev/sda1      3.142 mb
    /dev/sda2    27.2   mb
    /dev/sda3    32.5   mb
    /dev/sda4    17.1   mb

I am assuming sda1 is the Windows virtual memory. sda2 and sda4 are the shrunken versions of C and D, respectively. I want to allocate sda3 to Intrepid (8.10). 

1. I am not sure this is a correct configuration, because somewhere in the literature I found a partition allocated for "swap space" that should be double the memory. I am not sure which memory - the RAM, which in my machine is 512 mb, or the virtual memory. In any case, I was unable to create an additional partition for this swap space. Gparted said I could not have more than 4 partitions.

Correct. You will need to undo  (delete) some of these partitions to get the setup you need. > 

2. When I click "Forward" with the above configuration(sda1, 2, 3 and 4), I get this message: "No root file system defined. Please correct this from the partition menu". I do not know what to do now! The "Help" link in the installer screen does not work!
You have not told the partitioner where the root file system is going to live. You should probably give it 10-12 GB and make a separate partition for /home.

How much swap is the subject of some debate. If you have 2 gigs or more of ram, you'll likely never use swap, so you could make it a small amount, or none at all. If you are running 256-512 ram, then double that for swap. 

You have another problem, tho, if I understand correctly. You have formatted all the partitions to fat32? You will need either ext2, ext3, or Reiserfs filesystems for Linux. (Recommend ext3).

---

### Post by tapasray on 2008-11-09
Thanks! I'm going to do as you have advised.


> **handydan918 said:**
> Correct. You will need to undo  (delete) some of these partitions to get the setup you need. 
You have not told the partitioner where the root file system is going to live. You should probably give it 10-12 GB and make a separate partition for /home.

How much swap is the subject of some debate. If you have 2 gigs or more of ram, you'll likely never use swap, so you could make it a small amount, or none at all. If you are running 256-512 ram, then double that for swap. 

You have another problem, tho, if I understand correctly. You have formatted all the partitions to fat32? You will need either ext2, ext3, or Reiserfs filesystems for Linux. (Recommend ext3).

---

