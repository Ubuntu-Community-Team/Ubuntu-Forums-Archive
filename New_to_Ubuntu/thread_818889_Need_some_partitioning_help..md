---
title: "Need some partitioning help."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by arcarsenal on 2008-06-04
Alright, so I installed Ubuntu about a week ago. I have a 160 GB HD on my computer and when I partitioned upon install, I pretty much just split it half and half (which I immediately realized I didn't want to do). It only left me about 6 GB of free space on Windows and I've got 70+ GB on Ubuntu. 

For the time being, I've decided that I want to go back to using XP predominantly until I really have the time to learn Ubuntu 110%, and that being said, I absolutely need to fix my partition to that I can throw about 50 GB back this way before I start running way too low on disk space. 

I've heard people say to use Partition Magic.. I just want to make sure I know EVERYTHING I need to do in order to fix this because I cannot afford to mess anything up and screw up my system. Thanks in advance!

---

### Post by jimrz on 2008-06-04
probably the simplest way would be to shrink your ubuntu partion, I would suggest using the [[COLOR="Sienna"]**_gparted "live" cd_**[/COLOR]]("http://gparted.sourceforge.net/download.php") rather than Partition Magic or even your ubuntu "live" cd as it is better than either, then creating a FAT32 partition in the newly open space and use it to keep all your data/media/whatever files. An added bonus to this method is that both xp and ubuntu can read/write FAT32 natively, so you will have access no matter which side you are booted to without any hassels.

---

### Post by arcarsenal on 2008-06-04
> **jimrz said:**
> probably the simplest way would be to shrink your ubuntu partion, I would suggest using the [[COLOR="Sienna"]**_gparted "live" cd_**[/COLOR]]("http://gparted.sourceforge.net/download.php") rather than Partition Magic or even your ubuntu "live" cd as it is better than either, then creating a FAT32 partition in the newly open space and use it to keep all your data/media/whatever files. An added bonus to this method is that both xp and ubuntu can read/write FAT32 natively, so you will have access no matter which side you are booted to without any hassels.

Thanks for responding. So does that mean there's going to be my current XP partition, a smaller Ubuntu partition and then a 3rd partition with the space I take away from Ubuntu or is the extra space I'm taking from Ubuntu just going to be added back on to my XP partition?

---

### Post by bumanie on 2008-06-04
You will have to shrink the ubuntu partition first and then there will b e some unallocated space which you can then extend the xp partition into. Be aware that as the partitions have filesystems on them, the whole thing may take a number of hours. You will need either the ubuntu live cd or the dedicated gparted cd to do this as partitioning can't be done on disks that are mounted.

---

### Post by jimrz on 2008-06-04
> **arcarsenal said:**
> Thanks for responding. So does that mean there's going to be my current XP partition, a smaller Ubuntu partition and then a 3rd partition with the space I take away from Ubuntu or is the extra space I'm taking from Ubuntu just going to be added back on to my XP partition?

after re-sizing (do not change the starting point of the partition, but rather shrink it from the end back towards the beginning) your ubuntu partition you will have your current xp partition + the "swap" partition created when you installed ubuntu + a smaller ubuntu partition + some newly unallocated space. use the unallocated to create a new partition (call it "data" or whatever you like) and format it to FAT32 file system. Then, when you reboot you will want to move as much of your data files as you can to this partition, thus freeing up some space in your overly crowded xp partition. this process should not have any adverse effect on your current grub and, as I said earlier, will allow you to read/write your new partition from either xp or ubuntu.

---

