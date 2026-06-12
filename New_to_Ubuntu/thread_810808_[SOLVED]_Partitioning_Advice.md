---
title: "[SOLVED] Partitioning Advice"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by njd4k on 2008-05-28
So thanks in part to the helpful advice I've found here, I decided to forsake Wubi and set up a proper dual-boot system. But without thinking everything through I partitioned my hard drive in half in the installer, so my 80 GB drive looks something like

[LIST=1]
[*]40 GB Win XP NTFS
[*]38 GB Ubuntu ext3
[*]2 GB swap
[/LIST]

I already know how to use GParted a little from deleting an old partition with some Dell crapware on it, but I'm a little unsure how to proceed. What I want is a drive that looks like 

[LIST=1]
[*]15 GB Win XP NTFS
[*]13 GB Ubuntu ext3
[*]2 GB swap
[*]50 GB FAT32 shared
[/LIST]

What I am thinking of doing is:

[LIST=1]
[*]Shrink the NTFS and ext3 partitions to described sizes
[*]That leaves 50 GB unallocated in middle of drive
[*]copy the ext3 and swap partitions to unallocated space in first partition
[*]delete the extended partition
[*]that should create 50 GB continuous unallocated space, which I can then format
[/LIST]

Does that sound reasonable?

If I copy a partition in GParted into unallocated space, will that bring everything (that is, my Ubuntu installation) with it? Then it looks like I could delete the extended partition and merge the bits of unallocated space.

Or does copying a partition merely replicate the file system, not the contents?

I am trying to figure out if I can effectively resize and move my Ubuntu partition, or if I'll have to delete it, then resize XP/NTFS, then reinstall Ubuntu.

What do you think? Sorry for being such a noob.

---

### Post by Duck2006 on 2008-05-28
This may help with your partitioning.

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by zvacet on 2008-05-28
[Here]("http://users.bigpond.net.au/hermanzone/p3.htm")

---

