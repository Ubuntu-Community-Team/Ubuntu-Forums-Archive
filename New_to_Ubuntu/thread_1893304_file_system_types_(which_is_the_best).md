---
title: "file system types (which is the best?)"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by Shmook on 2011-12-10
Up until now I've stuck with Ext3 or 4 -- but lately, after hearing about alternatives (XFS, btrfs, reiserfs)I'm curious if these are better choices. 

Also I'm wondering if the particular distro makes a difference in which filesystem type is preferred. I've been reading up on these but everything I've found seems either a bit vague, or way over my head; what I've deduced is that some types are better for smaller file types (databases etc.), and all are journaling systems.

So can anyone please sum up the main differences between say: ext4, reiserFS, XFS, JFS & btrfs? Or, just tell me if it's worth looking into? 

I'm about to reinstall all the distros I run after a mishap with my HDD. I run Lubuntu, ArchBang, Puppy, Debian-kFreeBSD, winXP, Slitaz, and will be trying out ZevenOS and Frugalware this time around. 

Does the distro make a difference in the desired FS type? 
Does it make any difference if the partition is Logical or Primary?
Thanks in advance!

---

### Post by Dlambert on 2011-12-10
I also had this question, so one day I tried installing sabayon 7 using Btrfs, and I ran into a ton of problems, so I ended up going back to ext4, just because it works. 
 
 
 
> 
Linux is a very different operating system according to the Microsoft operating system. Linux has a very Complicated history with different hardware platform. Linux has different types of file systems that are very different from another operating system in the world.
Linux support number of file system because Linux Works on VFS (Virtual File System) that is known as abstraction Layer between the kernel and the program in user space that issues on the file system Commands. VFS program runs inside the Kernel . The VFS avoids the duplication of the code in the Internal Layer.
EXT2…
***Ext2 was the standard file system for linux until the introduction of ext3.It was introduced with the 1.0 kernel in 1993.Ext2 is flexible,can handle file system up to 4 TB,and supports long filenames up to 1012 characters,it has sparse super blocks feature which increase file system performance*.**
EXT3
[B]Ext3 (Extended 3 file system) provides all the features of ext2,and also features journaling and backward compatibility with ext2.The backward compatibility enables you to still run kernals that are only ext2-aware with ext3 partitions.we can also use all of the ext2 file system tuning,repair and recovery tools with ext3 also you can upgrade an ext2 file system to an ext3 file system without losing any of your data.
Ext3’s journaling feature speeds up the amount of time it takes to bring the file system back to a sane state if it’s not been cleanly unmounted (that is,in the event of a power outage or a system crash). [/B]

---

### Post by hansdown on 2011-12-10
Hi, Shmook.

It's best to use the file system, of the particular version you are running.

---

### Post by Shmook on 2011-12-10
@dlambert: yes I've run into similar trouble, like GRUB2 not recognizing...I think it was btrfs in that particular case. And thanks for the info.

@hansdown; yes, very informative, thank you. As I said, I'm about to reinstall all OS's which is why I'm asking this question.

---

### Post by hansdown on 2011-12-10
> **Shmook said:**
> @dlambert: yes I've run into similar trouble, like GRUB2 not recognizing...I think it was btrfs in that particular case. And thanks for the info.

@hansdown; yes, very informative, thank you. As I said, I'm about to reinstall all OS's which is why I'm asking this question.

You should be good to go, buddy.

---

### Post by Dlambert on 2011-12-10
> **Shmook said:**
> @dlambert: yes I've run into similar trouble, like GRUB2 not recognizing...I think it was btrfs in that particular case. And thanks for the info.
 
@hansdown; yes, very informative, thank you. As I said, I'm about to reinstall all OS's which is why I'm asking this question.
 
Yeah, I would just stick with the default of each OS, because after all, they chose that one for some reason right?

---

### Post by killermist on 2011-12-10
ext3 and 4 are good default choices since they support just about all the features needed in any "standard" filesystem.
I tend to use xfs for external drives, partly because it is marginally more efficient at storing files of variable size and because it seems to make no effort to enforce a super-user restricted space (because I'm using it as a user and want to be able to use that last Mb if I need).
Some filesystems are less processor efficient (xfs in some cases) to make some gains in on-disk efficiency and some are very processor efficient (jfs in most cases) at some (arguably trivial) loss in usable disk space.

ReiserFS had (is?) notable for being extraordinarily efficient at storing small files, but (last I checked, which truthfully was years ago) had issues of losing the entire filesystem content randomly (very infrequent type randomly).

If you have ANY doubts, ext3 and alternately ext4 are the most safe and/or most supported filesystems.  You can ALMOST NEVER go wrong in choosing ext3 or 4.
I personally have had little/no difficulty with xfs, and only once has reiserfs dump a filesystem on me (which annoyed me to no end at the time).

---

### Post by Shmook on 2011-12-10
@killermist - Thanks very much for that info; just over the years, learning more about different distros and such I'm now wondering if I'd missed out on perhaps faster performance by always choosing ext3/4. Maybe I'll give xfs or jfs a try on one of these installs tonight, and reformat the partition if I run into trouble. 

@hansdown - well that's the thing -- while installing some distros (I can't recall which particular ones now, I'm an admitted distro-hopper), they would offer a drop-down list of fs's while formatting the "/" partition prior to installation. Some of these would have reiser4 or xfs first on the list, before any of the ext's -- that's why I figured maybe some distros thought a non-ext format was preferable. Thanks though.

---

### Post by hansdown on 2011-12-10
> **Shmook said:**
> @killermist - Thanks very much for that info; just over the years, learning more about different distros and such I'm now wondering if I'd missed out on perhaps faster performance by always choosing ext3/4. Maybe I'll give xfs or jfs a try on one of these installs tonight, and reformat the partition if I run into trouble. 

@hansdown - well that's the thing -- while installing some distros (I can't recall which particular ones now, I'm an admitted distro-hopper), they would offer a drop-down list of fs's while formatting the "/" partition prior to installation. Some of these would have reiser4 or xfs first on the list, before any of the ext's -- that's why I figured maybe some distros thought a non-ext format was preferable. Thanks though.

True.

Keep in mind, that every file system is **very** different.

That is why, upgrades go awry.

---

### Post by idoitprone on 2011-12-10
> **Shmook said:**
> @killermist - Thanks very much for that info; just over the years, learning more about different distros and such I'm now wondering if I'd missed out on perhaps faster performance by always choosing ext3/4. Maybe I'll give xfs or jfs a try on one of these installs tonight, and reformat the partition if I run into trouble. 

@hansdown - well that's the thing -- while installing some distros (I can't recall which particular ones now, I'm an admitted distro-hopper), they would offer a drop-down list of fs's while formatting the "/" partition prior to installation. Some of these would have reiser4 or xfs first on the list, before any of the ext's -- that's why I figured maybe some distros thought a non-ext format was preferable. Thanks though.

Fedora is going with the brtfs route since it is one of the fastest filesystem with feature to prevent data loss  there is and oracle is behind it, but there isnt a fsck, so once it go wrong there is no way to repair it The author and maintainer of the ext filesystem, tso called, "ext 3 and 4 a step in the right direction, but brtfs is the way of future." I forgot where i read the exact quote so I cannot guarantee the integrity of the based on my bad memory

Reiserfs is a good filesystem with features that brtfs copied, but the head of the company, Reiser is in jail for murder and the project is in dismay.

---

### Post by killermist on 2011-12-10
Another FS of note, but not directly available in Linux (yet) is ZFS.  It is available in moderately recent versions of FreeBSD (including FreeNAS) and in Solaris, I think.

It can create gigantic filesystems.  From Wikipedia:
```
Capacity

ZFS is a 128-bit file system, so it can address 1.84 × 1019 times more data than 64-bit
 systems such as NTFS. The limitations of ZFS are designed to be so large that they would
 never be encountered. This was assured by surpassing physical rather than theoretical 
limitations&#8212;there simply is not enough usable matter on the planet Earth to support a 
maximized ZFS filesystem. Some theoretical limits in ZFS are:

    * 248 &#8212; Number of entries in any individual directory[27]
    * 16 exabytes (16×1018 bytes) &#8212; Maximum size of a single file
    * 16 exabytes &#8212; Maximum size of any attribute
    * 256 zettabytes (278 bytes) &#8212; Maximum size of any zpool
    * 256 &#8212; Number of attributes of a file (actually constrained to 248 for the 
           number of files in a ZFS file system)
    * 264 &#8212; Number of devices in any zpool
    * 264 &#8212; Number of zpools in a system
    * 264 &#8212; Number of file systems in a zpool

```
It also offers in-built deduplication, which really helps people like me that periodically lose track of where they put files, creating lots of copies of periodically used files.

---

### Post by eX_xi on 2011-12-10
I tried brtfs some time ago. There were no major problems just that it was very slow at that time, so it's probably best to wait and stay with ext4, at least for now ...

---

