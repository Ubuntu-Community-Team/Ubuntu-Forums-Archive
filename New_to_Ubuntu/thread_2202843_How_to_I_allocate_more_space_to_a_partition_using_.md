---
title: "How to I allocate more space to a partition using GParted?"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by vladimirvilimaitis on 2014-01-31
Currently, I have 130 GB of unallocated space on my HDD. How do I alloce it to my /dev/sda5 partition, on which my Lubuntu OS is located? Right clicking on unallocated space only allows me to choose New option, while Risize/Move is grayed out, and right clicking on /dev/sda5 only gives me and option of unmounting it.

---

### Post by dargaud2 on 2014-01-31
Yes, the partition must be unmounted. So if your system is on it, you must boot some other way. Also the partition and the unallocated space must be next to each other (partition first ?). There are some liveCD with just Gparted and a few other tools on it. So boot from such a liveCD, select the partition and chose the [Extend] option. Once it's done, the partition will be checked on reboot. Note that some type of filesystems may be easier to extend than others, I've only ever done this with FAT, NTFS and ext2/3/4.

---

### Post by deadflowr on 2014-01-31
What's the current disk layout?

---

### Post by vladimirvilimaitis on 2014-01-31
dargaud2 - okay, will try to do this using the LiveCD USB, thanks.

deadflowr - 130 GB is unallocated, /dev/sda3, extended, is 102GB. /dev/sda3 consists of /dev/sda5, ext4, which is 99GB, and /dev/sda6, linux-swap, which is 2 GB.
I wish I could screenshot but I don't know how.

---

### Post by deadflowr on 2014-01-31
Try posting either of these commands
```
sudo fdisk -l
```
or
```
sudo parted -l
```
That should show what the layout is.
Give us a better understanding.

Is /dev/sda5 the partition that you have the current system running on?
If so, then you probably need to run a livecd, so that it isn't mounted.

---

