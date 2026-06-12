---
title: "Partitioning questions"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by seaworthy4life on 2008-08-26
> 
Partition       Filesystem Mountpoint Size           Used           Unused  

/dev/sda1/      ext3                  14.65 GiB     270.65 MiB    14.38 GiB
unallocated     unallocated           45.39 GiB      
/dev/sda2/      ext3           /      13.84 GiB       9.92 GiB     3.92 GiB
/dev/sda3/      extended             666.76 MiB
   /dev/sda5/   linux-swap           666.76 MiB



This is my gparted listing.  What I want to do is increase the size of sda2 to take up some of the preceding unallocated space.  However, in order to unmount sda2, do I need to access a konsole prior to booting up ubuntu in order to do that?  I try to resize it through gparted, it tells me that it cannot unmount /dev/sda2 at /.  "Most likely other partitions are mounted at this mountpoint."  The thing is that sda2 is the only real partition with any substance on it.  sda1 was formally ntfs and split with just filesystem a slapped onto it.  Does the above quote refer to the extended and swap partitions?

If so, how do I go about expanding the size of sda2 back into the vast, unallocated turf.  I think I remember somewhere that if you want to increase the size of a partition, it must be with space that is logically below it.  Is there any way to fix this to make the ubuntu partition bigger, sda2?

---

### Post by tangibleorange on 2008-08-26
> **seaworthy4life said:**
> This is my gparted listing.  What I want to do is increase the size of sda2 to take up some of the preceding unallocated space.  However, in order to unmount sda2, do I need to access a konsole prior to booting up ubuntu in order to do that?  I try to resize it through gparted, it tells me that it cannot unmount /dev/sda2 at /.  "Most likely other partitions are mounted at this mountpoint."  The thing is that sda2 is the only real partition with any substance on it.  sda1 was formally ntfs and split with just filesystem a slapped onto it.  Does the above quote refer to the extended and swap partitions?

If so, how do I go about expanding the size of sda2 back into the vast, unallocated turf.  I think I remember somewhere that if you want to increase the size of a partition, it must be with space that is logically below it.  Is there any way to fix this to make the ubuntu partition bigger, sda2?

you need to do it from a live CD - the problem is that you're trying to resize the partition that your root filesystem is on. it will be fine if you use gparted from an ubuntu live CD. simply edit the /dev/sda2 and drag it over the unallocated space.

---

