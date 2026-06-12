---
title: "Error: Unknown Filesystem Grub rescue help"
date: 2013-05-28
forum: New to Ubuntu
---

### Post by thechad90000 on 2013-05-28
I am trying to install Windows 7 over my Ubuntu 13.04 install. I went into disk utility in Ubuntu and tried to format the hard drive to NTFS. I went to install Windows 7 but it said that it wasn't an NTFS hard drive. Now I tried going back into Ubuntu but it says "Error: unknown filesystem. grub rescue> _"

If anyone has any idea what I can do to just install Windows 7 from this point, I would be very grateful.

---

### Post by deadflowr on 2013-05-28
How many partitions do you have?

From what I understand.

You had an Ubuntu 13.04 partition, which became
An NTFS partition for Win7.
What other partitions are there?

If you have another Ubuntu on the machine then follow this
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

See if that helps fix the grub issues.

---

### Post by The musmula on 2013-05-28
if you formated your ubuntu partition then you`ve got a probelem, see ur pc thinks that there is no OS because u deleted the ubuntu entry in the master boot record.

what u need to do, if u formated a partition with a os on it, is: install a new os, but remove everything left :(

---

### Post by thechad90000 on 2013-05-28
There are no other partitions. I have an Ubuntu Live CD but other than that I have no other operating systems installed. I would like to just clean everything off of the computer and install Windows 7 solely at this point.

---

### Post by deadflowr on 2013-05-28
Boot the live CD on select the "Try Ubuntu" option.
This will boot a live session.
Then open the dash and type GParted and hit enter.
Gparted will open up and the select the partition and remove it, hit apply for the changes to take place.
If done right the disk will say unallocated.
Then try booting into the win7 install disk.
And let the win7 disk do what it does.

---

