---
title: "Change partition XP vs. Ubuntu"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by roy18 on 2014-06-19
I loaded Ubuntu about two weeks ago (with a 16 GB partition). I am ready to move more fully to Ubuntu, but would like to keep XP. I'd like to change the XP partition to 20 GB. I have found instructions for using Gparted, but find them difficult to follow. I wonder if there are any alternatives.

Thanks,

Roy

---

### Post by LastDino on 2014-06-19
Don't resize your windows partitions using Gparted, use your WIndows partitioning tool to do that. 

But first, post your out put of

```
sudo fdisk -l 
```

Or post screen shot of gparted window when its open.

On side note: If I was in your place, I would scrap XP (Unless, you've used some method to receive upgrades). Or at least go W7.

---

### Post by sudodus on 2014-06-19
Welcome to the Ubuntu Forums :-)

- I suggest that you use Windows ***XP without connection to the internet***, because it does not get any security updates.

- Please ***backup*** your computer or at least all important files (documents, pictures, video clips, mailbox files etc) because editing partitions is risky.

- Boot into XP and first remove all files that are not necessary. Then defragment your Windows partition. Finally shrink it to the desired size (from within Windows).

- Boot into an Ubuntu install disk and use ***gparted*** to use the unallocated space (freed from Windows) to edit the partitions. Either make a new partition (in this case I suggest an extended partition unless there is already an extended partition), or grow an adjacent partition to include the unallocated space.

- Warning: if you move the head end (left side in the graphic representation) of the root or boot partition of Ubuntu, the bootloader will be confused and must be reinstalled. This is possible but it is a complication.

-o-

Gparted has a graphical user interface, and is rather easy, when you start using it. But a good backup gives you peace of mind.

---

### Post by grahammechanical on 2014-06-19
If you installed Ubuntu then you are already in a position to move to Ubuntu, more fully or not. How did you install Ubuntu? Did you use Wubi.exe?

If you have installed Ubuntu into it own partition and not inside XP using Wubi.exe then you need to shrink the Ubuntu partition using gparted to create unallocated space that the XP partition can be expanded into.

After shrinking the Ubuntu partition make sure that Ubuntu still loads. Not much we can do if it does not load except re-install. So, back up your data. Then use Windows utilities to defrag Windows. do this at least twice. Make sure Windows loads. Back up any data and use a Windows utility to resize the XP partition.

There is no easier way. You will survive.

Regards.

---

### Post by sudodus on 2014-06-19
*LastDino & grahammechanical 	*

Good idea to ask for ```
sudo fdisk -l
``` and for wubi before doing anything else :-)

I could add: Please post the output of the command ```
df
```

---

### Post by roy18 on 2014-06-19
Thanks for all the speedy help. I am starting to wonder if I don't want to just eliminate XP.I have done the file purge, defrag, and backup. Here are the requested data:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      176714       88326   de  Dell Utility
/dev/sda2   *      176715   124795520    62309403    7  HPFS/NTFS/exFAT
/dev/sda3       124796926   156301311    15752193    5  Extended
/dev/sda5       124796928   154470399    14836736   83  Linux
/dev/sda6       154472448   156301311      914432   82  Linux swap / Solaris

```
```
roy@roy-Vostro-1000:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda5       14472568 11939060   1775288  88% /
none                   4        0         4   0% /sys/fs/cgroup
udev              432904        4    432900   1% /dev
tmpfs              88736     1296     87440   2% /run
none                5120        0      5120   0% /run/lock
none              443672       80    443592   1% /run/shm
none              102400       44    102356   1% /run/user
roy@roy-Vostro-1000:~$
```

---

### Post by sudodus on 2014-06-19
It looks good, a real dual boot (no wubi). So it is time for you to decide if you want to

- keep the dual boot and shrink the Windows partition
or
- remove Windows.

In both cases, the easiest move is to use the space made available into a partition (the fourth primary partition). Then you need not touch the extended partition and the partitions inside it.

But the root partition is actually a bit small, so if you can stand the extra work to reinstall Ubuntu (or maybe select another flavour depending on your computer specs and your preferences), your final system will be much better. In that case remove all partitions belonging to Ubuntu and get a clean unallocated space for your Ubuntu system.

Anyway, boot into the Ubuntu install drive and use gparted to edit the partitions.

---

### Post by roy18 on 2014-06-19
Thanks Sudodus,

If I did a system restore (in XP) to a date before I loaded Ubuntu, what would happen to Ubuntu and the partition I did when I loaded Ubuntu?

---

### Post by sudodus on 2014-06-19
It depends what kind of system restore it is.

- A Windows restore to a restore point will restore files and directories, but will not go outside the partition. This might not work well, if you have decreased the size of the partition too much.

- A restore of some backup system on the drive or partition level might overwrite the whole partition table and drive surface including Ubuntu.

---

### Post by roy18 on 2014-06-20
OK, thanks again, all.

I thought about it, and thought about it some more, and decided "in for a penny, ..." Which means, I decided to get rid of the XP (I have the re-boot disk, so I can go back) and run only Ubuntu. Mostly, the decision was based on me not having a ton of extra hard drive space.

I did this by just reinstalling Ubuntu from the origianl DVD I used to try Ubuntu two weeks ago. Clicking on the "get rid of everything" option.

Roy

---

### Post by sudodus on 2014-06-20
I think it was a good decision. Good luck :-)

If you feel that your problem in this thread is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

Welcome back with a new thread with a good descriptive title if you need help with a new problem.

---

### Post by roy18 on 2014-06-21
> **sudodus said:**
> I think it was a good decision. Good luck :-)

If you feel that your problem in this thread is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

Welcome back with a new thread with a good descriptive title if you need help with a new problem.


Will do. Thanks.

One last note: in addition to backing up your files before doing a total Ubuntu install, remember to backup bookmarks.

Roy

---

