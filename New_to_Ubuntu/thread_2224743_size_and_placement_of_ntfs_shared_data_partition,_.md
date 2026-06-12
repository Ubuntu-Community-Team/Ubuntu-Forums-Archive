---
title: "size and placement of ntfs shared data partition, dual boot"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by andrea b on 2014-05-17
Recently survived a two week XP / Trusty dual boot ... *learning experience* with the help this forum.  Starting again from scratch.  Installed Win 7 (gah! but I need it.) Preparing to partition now with Gparted per [this ]("http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html")tutorial, and hoping to create a shared ntfs data partition per [this]("http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony") one. 

The machine in question is a Thinkpad X60 with 120 GB HD, and without the pesky ThinkVantage Rescue and Recovery partition that seemed to complicate installation.  The HD is plenty large enough for my needs.  I'll be using Win7 primarily for collaboration on Word projects and work related stuff.  Data is well backed up, and I tend to keep large files, photos and videos on an external backup. 

My question: What is the proper placement for the shared ntfs data partition?  In fact, what is the optimal order / sequence of partitions?  I'm assuming there is one ... 

Also, any wisdom about partition *sizes *would be helpful ... I have done my reading, but... partitioning nonetheless makes me tense!)

Thanks!

---

### Post by Mark Phelps on 2014-05-17
Presuming your hard disk has ONLY Win7 on it at present, it is most likely partitioned using one of two schemes.

First, if you did not create partitions yourself, Win7 will create two partitions: a small 100MB "boot" partition (in which it stores the boot loader files), and a larger OS partition (the remainder of the drive).

Second, if you created your own NTFS partition, Win7 will not automatically create the "boot" partition and will install everything into that one partition.

Either way, you should shrink the OS partition using ONLY the Win7 Disk Management tool. Do NOT use GParted to do this as using that risks corrupting the Win7 filesystem and rendering it unbootable.

I would recommend having the shared NTFS data partition immediately following your Win7 OS partition.

As to size, I would recommend using no less than 40GB for the Win7 OS partition, more if you can spare it. That would leave around 80GB for other uses.

Also if you plan to install Trusty on this same machine, be sure to create an Extended partition to hold the Trusty root partition and swap partition.

---

### Post by andrea b on 2014-05-17
> **Mark Phelps said:**
> Presuming your hard disk has ONLY Win7 on it at present, it is most likely partitioned using one of two schemes.

First, if you did not create partitions yourself, Win7 will create two partitions: a small 100MB "boot" partition (in which it stores the boot loader files), and a larger OS partition (the remainder of the drive).

Second, if you created your own NTFS partition, Win7 will not automatically create the "boot" partition and will install everything into that one partition.

Either way, you should shrink the OS partition using ONLY the Win7 Disk Management tool. Do NOT use GParted to do this as using that risks corrupting the Win7 filesystem and rendering it unbootable.

I would recommend having the shared NTFS data partition immediately following your Win7 OS partition.

As to size, I would recommend using no less than 40GB for the Win7 OS partition, more if you can spare it. That would leave around 80GB for other uses.

Also if you plan to install Trusty on this same machine, be sure to create an Extended partition to hold the Trusty root partition and swap partition.

Thanks - this is how I was thinking as well ... I see that you can repair boot issues on the Win 7 partition after using GParted, but (as I've heard frequently on this forum), 'best to use Windows tools for Windows, and Linux for Linux'.  

Another question, then: the Disk Management tool in Win7 is in the GUI ... used on the working / mounted partition ... ? Or does one use the Win7 install disc?  or a command prompt? (something I haven't done in Windows since MS DOS). 

Noting too: I can't seem to run ```
diskmgmt.msc
``` from the 'search' box - only from the GUI.  (can't be found by search box). 

Thanks!

---

### Post by andrea b on 2014-05-21
All's well; unfortunately, Win7's Disk Management would not allow me to shrink the Win 7 partition to my desired size (by around 23 GiB) so I did end up using Gparted.  However, both OSs boot fine, and everything looks good ... so far. 

Thanks so much for your counsel!

---

### Post by mcduck on 2014-05-21
What comes to optimal order, in most cases there really isn't much of a noticeable difference but if it's an actual hard drive and not an SSD, there are two basic rules to partition order &  performance:

- partitions close to each other are quicker if you need to access both. (less time used moving read head between different tracks far apart on the disk). So placing shared partition between Windows and Linux partitions would give low access time in both operating systems, and you'll want to keep most used partitions as close as possible to each other. (so if you have a separate data partiton and a swap partiton for Linux, you'd need to consider if you are spending more time accessing data or swapping. Hopefully accessing data, so it should be closer to root partition than swap is).

- data closer to disk's outer edge is faster to access since there are more sectors per track (more data read per each rotation of the disk, and less time used to moving read head between tracks) so partitions at the end of partiton table will have slightly better performance than the ones at the beginning).

Anyway, the differences are small enough that unless you are doing some heavy audio or video recording or other tasks that require high transfer rates, you shouldn't worry about it as the difference in normal desktop use is too small to be noticeable.

---

### Post by andrea b on 2014-05-21
Thanks, mcduck, for your very informative post. I've had quite the learning experience with this little project (as seen in [this convoluted thread]("http://ubuntuforums.org/showthread.php?t=2221397")).  It's a heady thing, escaping microsoft...or trying to put as much distance between me and it as I can, anyway.  Well worth the effort.    And this is a great community!

---

