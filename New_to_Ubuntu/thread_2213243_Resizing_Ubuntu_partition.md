---
title: "Resizing Ubuntu partition"
date: 2014-03-25
forum: New to Ubuntu
---

### Post by ray9 on 2014-03-25
When I installed Ubuntu I let it take the entire disk, 500 GB.  I found out that that wasn't such a good idea as if I want to install another OS I have to resize the partition.  So I booted up the Ububtu disk to "Try Ubuntu", launched gparted and slid the partition to left about half way and got an "unallocated" space.  That isn't what I wanted.  I wanted "free space".  What can I do to shrink the Ubuntu partition?

Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      476721160 5171844 447326548   2% /
none                   4       0         4   0% /sys/fs/cgroup
udev             1852684       4   1852680   1% /dev
tmpfs             379044     888    378156   1% /run
none                5120       0      5120   0% /run/lock
none             1895208     160   1895048   1% /run/shm
none              102400      20    102380   1% /run/user


NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   462G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   3.8G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom


I know very little about partitioning.

---

### Post by oldfred on 2014-03-25
Unallocated is free space. If it is unallocated, you then can create new partition(s) in that unallocated space. But all within the partition rules of 4 primary partitions or 3 primary and one extended which then can have an unlimited number of logical partitions. 
If unallocated is not next to an existing extended partition you do have to move partitions around and then expand extended to included the unallocated inside the extended to let you create more logical partitions.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


 Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by ray9 on 2014-03-25
First, let me say thanks for the reply.  My "unallocated" partition is the last entry.  It is next to the Linux swap partition.  Somehow it is only one meg.  So I didn't do that right.  I was trying to shrink the drive at least in half.  Now I can't resize it again.

---

### Post by ray9 on 2014-03-25
Mark as resolved.  I got it resized.  The mistake I was making was not clicking the the green "check arrow" at the top.  Thank you for the help.

---

