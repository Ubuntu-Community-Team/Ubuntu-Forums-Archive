---
title: "Partitions and using GParted...??"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by BlueAZ on 2012-08-19
Hi,     I've learned a lot in this forum, thanks to all those who kindly answer questions!  Now I'd like some guidance with partitioning and using GParted.

I'm running Oneiric on a Phenom Quadcore / 320 Gb HD.  I have a second HD with W-XP, but it won't boot anymore.  'File system check' says it's NOT clean. Must have a virus or something.  I can still access files there thru Ubuntu.

But I've got a copy of W-7, & I'd like to install it on the 320 Gb HD, along with Ubuntu.  I opened GParted using my Live CD and was able to make the partition containing Ubuntu 11.10 smaller.  But it made my sdb6 partition huge.  Then I went back & made that partition smaller.  Now I have some unalocated space.  But it's in between Ubuntu & the sdb6 partition.  I'm also concerned that I've made the Ubuntu partition too small, but can't seem to enlarge it.

It doesn't seem right to install Windows in between Ubuntu and sdb6.  I'm attaching a shot of what GParted shows now.  I'd like to know how best to arrange my partitions (& how) to install W-7 alongside Ubuntu.

Thanks!  ):P

---

### Post by oldfred on 2012-08-19
Windows will only install to a primary partition formatted NTFS with the boot flag.

You can move the start of the extended partition right and in effect move the unallocated out of the extended partition. Then you can create a new primary partition sda3 which will work for Windows. Partitions do not have to be in order on drive, although some tools may tell you they are not in order.

Gparted will make a XP compatible NTFS. Vista/7 have a different partition boot sector but Windows 7 should install & reformat. If any issues reformat again from the Windows 7 install disk.

---

