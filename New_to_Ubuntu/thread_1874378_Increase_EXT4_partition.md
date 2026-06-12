---
title: "Increase EXT4 partition?"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by d4m1r on 2011-11-03
Hey guys, I wondering if it is possible to resize a NTFS partition within Ubuntu to add some of it to my 11.04 install (EXT4)? Basically, I have a 1TB internal sata harddrive that I only allocated 20GB for my linux partition and I'd like to increase it to 50GB just in case. Would adding more GB's to my Ubuntu partition cause any issues?

Note - the drive is 60% full on the NTFS side so I'd only edit the partition size if it wouldn't put any of my data at risk (can't move files on/off either) and would still be recognizable by my other OS (Windows 7 which formatted it originally).

If it's possible, a link to an applicable guide would be great, thanks!

---

### Post by dave0109 on 2011-11-03
I know little about this area, but I was in a similar position recently.  The problem is/was, when shrinking the size of the NTFS partition, this left me with some free space in between the 2 partitions.  I couldn't see how to add the free space to the existing ext3 area.  It may be possible, but I didn't risk it.

So, I booted up with the Ubuntu LiveCD, then connected a USB hard disc, mounted the existing Ubuntu partition and backed up the /home directory to the USB disc.  I only did /home because I was going to do a fresh install of 11.10, rather than upgrade to it.  However a backup of the whole system should also work.

I then deleted the Ubuntu partition, resized the NTFS partition, then recreated a new partition with all the free space.  I installed 11.10 to this new partition, then after it was done, I mounted the partition and restored /home.

It's one option, but you need to be careful and comfortable with messing about in partitions.  One wrong move and you could lose everything.

Hopefully someone else will come along with an answer as to how to do it better.

---

### Post by d4m1r on 2011-11-03
^Thats but that is exactly what I want to avoid :lol:

Is there any way to add space to my EXT4 partition without having to move files around/unmount/back it up?

---

### Post by dave0109 on 2011-11-04
Certainly using something like gparted, you can increase the size, if you can add it on the end.  It's the adding to the beginning that I'm not sure about.  Maybe the gparted website/community can help.  [http://gparted-forum.surf4.info/index.php](http://gparted-forum.surf4.info/index.php)

---

### Post by kurt18947 on 2011-11-04
I have resized/imaged/copied/moved  NTFS partitions with a partition/boot manager I use.  Google terabyteunlimited and see bootitbm.  I haven't tried manipulating ext* partitions with it, I don't think it will format ext*.  it's also a nice workaround for the 4 primary partition limit and GRUB issues.  You put the GRUB files for each partition IN the partition, not in the drive root or MBR.

---

### Post by Paqman on 2011-11-04
d4m1r, you should be able to make any changes to either your NTFS or EXT4 partitions by booting up into a LiveCD or USB and running the partition editor (called Gparted)

Gparted can shrink, expand and move partitions around no problem. Just be aware of a couple of things:
[LIST]
[*]Moving partitions can be quite slow, don't turn it off just because it's taking a while.
[*]If any partitions show as locked, right click on your swap partition and "swapoff"
[*]Its always best to have a backup before messing with partitions.
[/LIST]

---

### Post by mikechant on 2011-11-04
Just to make it quite explicit, yes you can expand ext2/3/4 file systems at the 'front' as well as the 'back', but it will take a lot longer because all the data has to be moved, and if your data is at all valuable you really should back it up first since there's always the possibility of (e.g.) a power outage or other crash, which can easily leave the partition corrupt if the data move is part way through.

Note that not all file system types can be expanded at the 'front'.


One possible minor obstacle is if the free space you are trying to expand into was part of a primary partition but the ext4 partition you are trying to expand is a logical partition.
The only difference this makes is that you need to move the start of the expanded partition (the 'dummy' partition that acts as a container for one or more logical partitions) down to the beginning of the free space before it (a very quick operation) before you can expand the ext4 partition.

If you want more detailed advice, post your current partition table layout by using the terminal command
> fdisk -l
(that's lowercase L not number 1)
and posting the output.

---

### Post by d4m1r on 2011-11-04
Thanks for the info guys! I've heard Gparted mentioned several times but never knew what it was used for....fdisk info (sudo has to be used to output anything to the console FYI):

```
Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbedc4845

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60801   488280064    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x287ee2b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      119052   956279808    7  HPFS/NTFS
/dev/sdb2          119052      121602    20480001    5  Extended
/dev/sdb5          119052      121602    20480000   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd3f0a486

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976759808    7  HPFS/NTFS
```Basically, I have 3 drives; 500GB internal what I installed Windows 7 on initially (NTFS), 1TB estata HDD that has no OS on it (storage, NTFS), and another 1TB internal that I formatted 980GB of in Windows 7 for storage (NTFS), and then partitioned the unallocated space (20GB) during my linux install.

I'd like to shirk that 980GB down to 950GB, without having to reformat it or without losing any data on it and keeping it NTFS so that any Windows PC could read it. About 600GB/980GB is used so I don't have anywhere to move the files...Also, since my Ubuntu partition is only 20GB, it shouldn't take too long to move everything eh?

And finally, can I run gparted while logged in or should I grab my 11.04 live CD and boot from it? :|

---

### Post by dave0109 on 2011-11-05
You can run gparted from your running system, but because your partitions are mounted and being used, you won't be able to do anything with them... it's just sometimes useful to run it and have a look, without doing anything, or to modify any Windows partitions.

For the resizing of your ext4 partition, you'll need to boot into the LiveCD/USB.

---

### Post by mikechant on 2011-11-05
So it looks like what you need to do is defrag sdb1 several times in windows - this will probably take a long time!
Then use the Windows 7 disk utility to shrink sdb1 by 30GB (don't know the details because I don't have Windows 7) - but do not use gparted for this.

Then use gparted from a LiveCD/USB to move the start of sdb2 down to the beinging of the free space.

Then use Gparted to move the start of sdb5 down to match the start of sdb2.

---

### Post by d4m1r on 2011-11-05
> **mikechant said:**
> So it looks like what you need to do is defrag sdb1 several times in windows - this will probably take a long time!
Then use the Windows 7 disk utility to shrink sdb1 by 30GB (don't know the details because I don't have Windows 7) - but do not use gparted for this.

Then use gparted from a LiveCD/USB to move the start of sdb2 down to the beinging of the free space.

Then use Gparted to move the start of sdb5 down to match the start of sdb2.


Thanks for the advice but it looks I'll hold off on this unless I really have to. That will take a really, really, long time (especially defraging a 1TB HDD several times). Why didn't I set more space to begin with ](*,)

---

### Post by mikechant on 2011-11-07
You could try shrinking without the defrag; Windows will just say no if it can't manage without the defrag, no harm done.

---

### Post by d4m1r on 2011-11-07
> **mikechant said:**
> You could try shrinking without the defrag; Windows will just say no if it can't manage without the defrag, no harm done.

Yah, I just don't want to risk it (plus it will take a long time to move so much data). Under Windows, it is easy to resize a NTFS partition but I was unsure about the 2nd part of the issue, which is added this newly unallocated space to my EXT4 (ubuntu) partition.

To avoid all the hassles, I will just watch what I leave stored on this partition (12/20 GB free ATM) and will install 12.04 LTS with at least 100-250GB of space when it is released.

---

