---
title: "Is it too late to make a /home partition?"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by vasa1 on 2011-09-10
I'm dual-booting Win 7 and Ubuntu 11.04. Since I'm pretty new to Linux, I let Ubuntu handle the installation "alongside".

I now have this:
```

**fdisk -l**
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x768837b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6375    51096576    7  HPFS/NTFS
/dev/sda3            6375       32508   209920000    7  HPFS/NTFS
/dev/sda4           32509       60802   227264513    5  Extended
/dev/sda5           32509       60284   223109120   83  Linux
/dev/sda6           60284       60802     4154368   82  Linux swap / Solaris
aes@aes-Inspiron-1545:~$ 


**parted -l**Model: ATA WDC WD5000BPVT-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   52.4GB  52.3GB  primary   ntfs
 3      52.4GB  267GB   215GB   primary   ntfs
 4      267GB   500GB   233GB   extended
 5      267GB   496GB   228GB   logical   ext4
 6      496GB   500GB   4254MB  logical   linux-swap(v1)

```

But, as I'm reading more and more, it appears that a separate /home partition is strongly advised. (I do back up my data separately in any case).

My understanding is that I have the space to have a lot more stuff but I would appreciate any pointers as to whether I can **now** have a separate home partition. I'm reading the community documentation available here: [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes) but haven't come across any information on how to create a /home partition after Ubuntu has already created in sda5 (?)

At the moment, I'm clueless :(

I'm sorry the text in quotes is messed up but I can't find a way to post a snapshot so that the figures don't run together. Okay! Using the code tags worked :)

---

### Post by 2F4U on 2011-09-10
Maybe this tutorial is what you are looking for

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by saltmarshlamb on 2011-09-10
Be aware that tute is no longer supported by the writer as it sometimes didn't work.

To be honest if you are backing up your data I'd not worry about having your home seperate. I've not done so for a few years now.

I use a seperate drive and partition for some of my data and just mount it in fstab.

---

### Post by vasa1 on 2011-09-10
Hi!

I just have come across a bunch of links including the one 2F4U linked to.

I'll go through them.

saltmarshlamb, I don't have a separate drive. Just the one so I'll look more into this.

Thanks for the replies :)

---

### Post by pricen2 on 2011-09-10
Another guide you could follow is in the community added documentation:

[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

I've not followed it but whilst it doesn't cover resizing/creating partitions it does cover moving /home in a manner where by if it doesn't work you can easily reverse it.

---

### Post by 2F4U on 2011-09-10
Two other posts:

[http://www.ehow.com/how_6182851_create-partition-after-install-ubuntu.html](http://www.ehow.com/how_6182851_create-partition-after-install-ubuntu.html)
[http://www.linuxquestions.org/questions/linux-desktop-74/move-home-to-partition-after-install-871764/](http://www.linuxquestions.org/questions/linux-desktop-74/move-home-to-partition-after-install-871764/)

The method is basically the same as the one I already posted.

---

### Post by YesWeCan on 2011-09-10
How you copy files is very important. You'll want to preserve attributes like date, time, owner, permissions and you'll want to copy hidden files. For example you should not use drag & drop in a file browser. The command line method using rsync is good:

sudo rsync -vax /source_directory/ /destination_directory/

If you are lucky, your sda5 will be less than half full. GParted will show you this. If so you can first shrink sda5 to half size and then make a new partition of type ext4 in the gap, sda7. Copy home files to sda7 then delete them on sda5, before resizing both. Dont reduce sda5 below 10GB and whenever you shrink an OS partition make sure you leave at least 1GB unused. Finally, add a mount entry to fstab.

Messing with partitions is dangerous so back up all vital files first.

---

### Post by vasa1 on 2011-09-10
Pricen, thanks for the link to the community documentation. That is very well organized. And 2F4U thanks for the additional links.

And, as YesWeCan mentioned, the rsync method seems to be favored over the earlier find|cpio.
 
Looks like I've got a lot on my plate to read. Once I feel confident, I'll post a plan of action for you guys to look over!

---

### Post by pdlethbridge on 2011-09-10
I have all my important data on CD but I store it also on Ubuntu cloud. I use several flavors of Ubuntu but as the days go by I find myself using only 1 or 2 of them

---

