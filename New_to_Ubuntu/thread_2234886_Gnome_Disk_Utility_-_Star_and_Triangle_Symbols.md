---
title: "Gnome Disk Utility - Star and Triangle Symbols"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-07-17
The gnome disk utility uses several symbols.  I believe the triangle symbol shown in a partition means that the partition is mounted.

What is the star symbol that is often next to the triangle symbol?

---

### Post by Jonor on 2014-07-18
Good question, not easy to Google quickly. 
My guess is the star represents the booted filesystem where there is more than one partition or disk present containing bootable filesystems ?

---

### Post by KAWill70 on 2014-07-18
> **Jonor said:**
> Good question, not easy to Google quickly. My guess is the star represents the booted filesystem where there is more than one partition or disk present containing bootable filesystems.
Thanks for the reply.  I came to pretty much the same conclusion.

The Star appears to be showing the partitions associated with the Linux program currently running.  That might include Swap, Root, and Home.

I tried Mounting other available partitions and then the Triangle symbol only would appear on those partitions.  It's not clear if you can Unmount any of the active partitions with only the Star symbol remaining.

---

### Post by at_first_light on 2014-07-18
I'm not sure what the star means. If you see a play icon (triangle) on a partition it means it's currently mounted. If you click on the partition the bottom menu will show a stop icon (square) that when clicked will unmount the partition.

---

### Post by grahammechanical on 2014-07-18
My guess is that we will only ever see two star symbols on partitions on any disk. One star will be on the swap partition and the other star will be on the partition that Ubuntu is loaded from. But that we will see as many triangles on as many partitions as are mounted.

triangles = mounted partitions. stars = partitions being used by the Linux OS.

---

### Post by Jonor on 2014-07-18
Here there is Ubuntu Gnome 14.04 installed as a FAT boot partition, an EXT4 root and a swap so there are 3 stars.
Unmounting the boot partition leaves a star without a triangle.
I should reword my guess to : the star represents the booted filesystem where there is more than one bootable filesystem.
I.E. more or less what GM says :p
The second Ubuntu Gnome 14.04 on another drive has no stars from this boot but a triangle when i mount it.
Boot to that drive and the stars move over to it. The fact that my present system always names the booted drive sda makes this a little less obvious.

---

