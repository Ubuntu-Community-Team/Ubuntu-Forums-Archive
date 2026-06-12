---
title: "Raid0 and dmraid"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by WhyCantEveryOSBePerfect on 2008-09-27
Hey there.  When I boot to my ubuntu live cd and get dmraid (I'm trying to install a dual boot setup, but stupid RAID makes things difficult), I run:
sudo dmraid -ay
and I get this:

ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_diihdeefba_RAID0" already active
RAID set "isw_diihdeefba_RAID01" already active
RAID set "isw_diihdeefba_RAID02" already active
RAID set "isw_diihdeefba_RAID03" already active
ubuntu@ubuntu:~$

I know I only have 2 disks.  What does this mean?

Also, if I run sudo dmraid -ay, then try and install from my cd, I get to the partitioner eventually, and it looks like this:

Device                               Type M.P.   Size       Used
/dev/mapper/isw_diihdeefba_RAID0
   /dev/mapper/isw_diihdeefba_RAID0  ntfs        14690 MB   unknown
   /dev/mapper/isw_diihdeefba_RAID0  ntfs        363920 MB  unknown
   free space                                    21474 MB 
/dev/mapper/isw_diihdeefba_RAID01
   /dev/mapper/isw_diihdeefba_RAID01 ntfs        14690 MB   6000 MB
/dev/mapper/isw_diihdeefba_RAID02
   /dev/mapper/isw_diihdeefba_RAID02 ntfs        363920 MB  90600 MB
/dev/mapper/isw_diihdeefba_RAID03

Or, if I try to make an ext3 root partition (I was going to leave out swap for now, I have 4GB RAM) on the free space from within the installer partitioner, it looks like this:

Device                               Type M.P.   Size       Used
/dev/mapper/isw_diihdeefba_RAID0
   /dev/mapper/isw_diihdeefba_RAID0  ntfs        14690 MB   unknown
   /dev/mapper/isw_diihdeefba_RAID0  ntfs        363920 MB  unknown
   /dev/mapper/isw_diihdeefba_RAID0  ext3 /      21467 MB
/dev/mapper/isw_diihdeefba_RAID01
   /dev/mapper/isw_diihdeefba_RAID01 ntfs        14690 MB   6000 MB
/dev/mapper/isw_diihdeefba_RAID02
   /dev/mapper/isw_diihdeefba_RAID02 ntfs        363920 MB  90600 MB
/dev/mapper/isw_diihdeefba_RAID03

Can anyone tell me what's going on?  I do not have 4 hard drive disks.  I know I have 2 partitions already from windows vista(regular and a backup), but I don't understand what's going on here.  Thanks!

---

### Post by WhyCantEveryOSBePerfect on 2008-09-27
I don't know why but the spacing I made so it looks like a table doesn't show up in these forums.  the "Device Type M.P. Used"  part is the labels at the top of the partition table on the cd installer. And M.P. = mount point.

---

