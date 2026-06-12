---
title: "Partition sizes/tools?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by 625 on 2008-06-01
Hey folks.

I'm going to give a new Linux installation a shot, and in doing so I'm going to create some partitions. What I'm wondering is how big they should be; I heard that it's handy to have separate partitions for /home and for the rest of the filesystem, but how big do I want each to be?

I'd be partitioning a 600 GB SATA volume, so I'm not anticipating being choked for space or anything, but as things stand it's currently carved up between my present Linux install and a huge chunk of NTFS space since most of the bigger files I run are games I'd presumably play through Windows.

Furthermore, is there a program a la PartitionMagic that I can use to reallocate/create these partitions without losing data or doing anything to make Windows mad, or am I stuck reformatting the volume entirely?

---

### Post by subzero316 on 2008-06-01
> Hey folks.

I'm going to give a new Linux installation a shot, and in doing so I'm going to create some partitions. What I'm wondering is how big they should be; I heard that it's handy to have separate partitions for /home and for the rest of the filesystem, but how big do I want each to be?

I'd be partitioning a 600 GB SATA volume, so I'm not anticipating being choked for space or anything, but as things stand it's currently carved up between my present Linux install and a huge chunk of NTFS space since most of the bigger files I run are games I'd presumably play through Windows.

How Much Space is left apart from your ntfs occuupied area???
basically i suggest you have a min of 15 gb for root for swap 1-2gb is enough. For home depend on your usage(depends on the amount of music movies and documents you want to have in the linux partition


> Furthermore, is there a program a la PartitionMagic that I can use to reallocate/create these partitions without losing data or doing anything to make Windows mad, or am I stuck reformatting the volume entirely?


Try GTPARTED it`ll help you with that

---

### Post by kk0sse54 on 2008-06-01
Don't worry about the tools Gparted is included in the LiveCD ready to go

---

