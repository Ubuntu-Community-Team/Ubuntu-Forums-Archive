---
title: "GParted on dual boot (Ubuntu/Win7) - help resizing partitions?"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by taptwo on 2012-02-07
Hi all,

I have a netbook with win7/ubuntu dual boot setup, with a third partition for data. Surprise surprise, my W7 volume is getting short on disk space, and I want to add a few GB, and want to make sure I do so without rendering either or both OSes incapable of booting.

Here is the current setup:

[COLOR="red"][SIZE="4"]**|**[/SIZE][/COLOR] /dev/sda1 20GB (W7) [COLOR="red"][SIZE="4"]**|**[/SIZE][/COLOR] /dev/sda2 15GB (ubuntu) [COLOR="Red"][SIZE="4"]**|**[/SIZE][/COLOR] /dev/sda3 24GB (data) [COLOR="red"][SIZE="4"]**|**[/SIZE][/COLOR] swap 2gb [COLOR="red"][SIZE="4"]**|**[/SIZE][/COLOR]

I want to remove 3-4GB from sda3 (data) and add it to sda1 (W7). However because of my setup, this will wind up changing the start point of my sd2 (ubuntu) partition, and my understanding is that may render it unbootable.

Any advice on this? I am relatively new to Ubuntu and its ability to change partition sizes... thanks!

Using GParted as the title suggests.

---

### Post by taptwo on 2012-02-07
PS if this should be in a different forum, mods please move it. I put it here because I don't know enough of the rest of the lingo to choose an appropriate forum :popcorn:

---

### Post by oklokl on 2012-02-07
Is not a good idea
 Will ruin

Hard
 Backup data
 New building


Upgrading HDD
Change
Purchase recommendations
External HDD

---

### Post by Mark Phelps on 2012-02-07
I know a way you CAN do this -- but it involves some work on your part, including burning CDs, but the approach is the least likely to cause any damage.

In my own experience, MS Windows utilities are BEST at handling MS Windows filesystems, and Linux utilities are BEST at handling Linux filesystems.  So, you will need to use more than just GParted.

If you're interested, read on ...

Go to the Partition Wizard website, download an install their free version in MS Windows.  Use that to resize sda3 FROM THE LEFT (I'm presuming that sda3 is formatted NTFS).  This will open up space to the left of sda3.

Boot into an Ubuntu desktop CD and use either Disk Utility or GParted to move sda2 TO THE RIGHT.  This will open up space to the left of sda2.

Boot into Win7 and use the Disk Managment utility to expand the Win7 OS partition (sda1) to the right to fill the new unallocated space.

Yes ... that's more work than bashing around with GParted, but I've found that using the right tools helps to minimize damage.

---

### Post by taptwo on 2012-02-07
Interesting solution. I figured I would have to boot Ubuntu from an external source, but I hadn't considered using a different utility for the W7 partition. I will think about it - thanks!

---

