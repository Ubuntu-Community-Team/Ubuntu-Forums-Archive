---
title: "Minimize disk activity"
date: 2008-08-24
forum: Philippine Team
---

### Post by Recursion_1209 on 2008-08-24
I am trying to minimize disk activity of my laptop to try spinning down the hd. This should in effect cool down the laptop as the place where the HD is located becomes hot.

I have three partitions in my laptop:

/sda1 - Home dir
/sda2 - Ubuntu file system
/sda5 - Data files

I have gkrellm to monitor temperature and disk acitivity. Before, I see that it was doing writes on sda1 and sda2 every 5 seconds. I tried doing some of the tutorials and change the commit parameter in fstab/grub to 60 (changed also the journal to write back and set my partitions to noatime.  Now, the disk is getting written to every 60 seconds even idle.

My HD won't spin down because of this. I am wondering if this is because of ext3 journalling? Would changing the filesystem from ext3 to ext2 fix this?

---

