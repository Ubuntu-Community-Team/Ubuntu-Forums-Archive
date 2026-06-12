---
title: "How to format a drive previously formatted and installed Ubuntu Studio 12.04"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by loneTiger on 2014-06-10
How to format a drive previously which was formatted to ext4 and installed Ubuntu Studio 12.04 via live DVD. 

I am unable to format the drive from Windows 7 ( main Os on that machine). I would like to reclaim the drive for Windows Os use for HardDisk space (running out of HDD). 

I don't want to install Ubuntu on it right now.

[B]How do I reformat it quickly with out Ubuntu getting installed and reclaim the Drive to Windows 7 OS?

[/B]Also Is there a way to run hard disk checks/Tests for Bad sectors, Health etc. on the hard drive? like from the live CD/DVD? like S.M.A.R.T. tests ? or something better?

Thanks in advance.

John Bandaru

---

### Post by nknwn on 2014-06-10
Create a live CD with **GParted** [http://gparted.org/](http://gparted.org/)

Boot to this CD and use Gparted to "resize, copy, and move partitions without data loss"
You can use GParted to format the drive in NTFS or FAT to let Windows use it.

When you have completed the above.
Boot back to Windows and use **chkdsk** to check your disk for errors

---

