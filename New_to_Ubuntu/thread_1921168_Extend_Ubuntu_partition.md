---
title: "Extend Ubuntu partition"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by crova on 2012-02-06
Hi all,
I have this situation on the disk ( you can see in the pic ):

64GB ext4 
537MB swap

319GB free
116GB NTFS ( with Data )



In the 64GB partition is installed Ubuntu 11.10, but I need more space. I want to add some extra space ( 100GB ) from the 319 GB free.
Can I do this safely for my ubuntu's data and in case, how??
thanks in advance for the help

---

### Post by Elfy on 2012-02-06
If it was me I would do this - AFTER making sure I had backups of things I did not want to lose.

Boot livecd
Delete swap
Resize root into the unallocated space
Create new swap

Then - run sudo blkid - note the new UUID for swap
Mount / 
Edit /etc/fstab to the new UUID for swap

---

### Post by tersogar on 2012-02-06
Yes, that´s achievable but always is recommended to backup your data. You need to boot from the live cd or usb and use gparted to extend the partition to your needs.

---

### Post by grahammechanical on 2012-02-06
I have four versions of Ubuntu on my hard disk. The other month I resized and moved partitions affecting three of my Ubuntu installs without it breaking any of the operating systems.

The partition manager will warn you about loosing data and not being able to boot. It has to give that warning but it is only a warning of what could happen. It is not a promise of what will happen.

If your valuable data is backed up then you can always re-install if things go wrong. I have only had to re-install because of my own mistakes.

Regards.

---

### Post by crova on 2012-02-07
Thank you all!
I came up with another idea, but need your suggestions :D..
Because I don't have a /home partition ( as you can see in the pic there is only / as mount point ), can I create a /home in the free space and copy here the "actual" home?
Is this easy to do? Is it better than resizing the whole partition?

---

### Post by plucky on 2012-02-07
> **crova said:**
> Thank you all!
I came up with another idea, but need your suggestions :D..
Because I don't have a /home partition ( as you can see in the pic there is only / as mount point ), can I create a /home in the free space and copy here the "actual" home?
Is this easy to do? Is it better than resizing the whole partition?

See [Psychocats Separate Home](http://www.psychocats.net/ubuntu/separatehome)

Or

[Moving Home](https://help.ubuntu.com/community/Partitioning/Home/Moving)

The first link worked for me a long time ago,but I haven't tried doing it lately as I have a separate home partition.

Good Luck

---

