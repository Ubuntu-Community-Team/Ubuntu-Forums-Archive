---
title: "e2label:No such file or directory while trying to open /dev/sda1"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-01
I was reinstalling from 12.04 alternate cd, but it stopped at 97% with unable to install grub, so I I cleaned the old version of 12.04 off my system and using partedmagic formatted and erased the drive.

Upon running 11.10 live cd, opened gparted and got the following error message

> 
e2label:No such file or directory while trying to open /dev/sda1
Couldn't find valid file system superblock.

Couldn't find valid file system superblock.

dumpe2fs 1.41.14 (22-Dec-2010)
dumpe2fs:no such file or directory while trying to open /
dev/sda1

Unable to read the contents of this file system!
Because of this some operations may be unavailable

The cause might be a missing software package.
the following list of software packages is required for ext4
file system support: e2fsprogs v1.41+
What do I need to do to fix this error? And why would 12.04's install be unable to install grub?

---

### Post by jtarin on 2012-06-01
Is this disk devoted to Ubuntu solely? It would help to see a BootInfo script

---

### Post by Senior_Buckethead on 2012-06-01
Yeah, I think I formatted the drive before partitioning it, so it spat up an error. In gparted I deleted the formatted partition and then restarted and ran install, which ran without a hitch.
Problem solved.

---

