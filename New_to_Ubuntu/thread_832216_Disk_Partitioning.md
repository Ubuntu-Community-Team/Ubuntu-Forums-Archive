---
title: "Disk Partitioning"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Dave2081 on 2008-06-17
Hello,
I've got both vista and ubuntu installed on my computer and they are both running just fine. However, I accidentally made the swap disk space too big when I first installed ubuntu. So I shrunk the disk space in gPanel(?) I think, in ubuntu, and I am now trying to put that space back onto my ntsf drive that has vista. but I can't get that unallocated space to do anything. the only option is create a simple volume (in vista), but even that errors out at the end. did I just ruin that amount of space on my hard drive?
thanks for any help,
dave

---

### Post by logos34 on 2008-06-17
Unless the swap is contiguous to the ntfs partition, you can't directly add it to windows.

You didn't ruin anything.  You just have to move things around a bit (like chinese checkers) to do it

Post a screenshot of Gparted, or failing that, the output of 

sudo fdisk -l

(tell us what order the partitions are in on the disk)

---

