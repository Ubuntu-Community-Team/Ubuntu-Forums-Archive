---
title: "alternatives to /swapfile ?"
date: 2019-10-25
forum: New to Ubuntu
---

### Post by hk42 on 2019-10-25
Hi
I'm thinking of a symlink to my huge (4GB) W10's pagefile.sys on a NTFS emmc partition.
Any warning before I break my system ? :P

---

### Post by TheFu on 2019-10-25
Good luck with that.  I wouldn't do it.  They aren't compatible and I'd have zero idea how Windows might use the pagefile for fastboot needs.

You can setup a swap partition or a swap logical volume, if you like.  You can mix and match any of those 3 options too or just not have a swap file, though some of the recent kernels really dislike not having any swap available.   If memory runs out on any Unix system, it will crash.

---

### Post by hk42 on 2019-10-25
I tried and it doesn't work.:(
It says that permissions of 0777 should be 0600
That the head of the file is not OK
So I copied the original swapfile to the NTFS partition
and then it said that there was gaps in the file.
Error messages were in French so excuse my poor translation.

---

### Post by TheFu on 2019-10-25
There are a number of issues in attempting this.
[LIST]
[*]swapfile Unix permissions are key to security of Unix systems; that file could contain anything in RAM, so root:root 600 permissions are mandatory for security.
[*]hibernation use by either Windows and/or Linux would break it
[*]mkswap on Linux/Unix formats swap in a specific way, almost certainly incompatible with Windows.
[*]Windows can't read EXT4 file systems, nor native mkswap objects
[*]Windows 8+ fast-boot or fast startup or whatever MSFT is calling it this month.
[/LIST]

I really didn't think you'd try it, but good on you for following through and seeing for yourself.  
Nobody knows this stuff intuitively and gaining the level necessary to understand some of these deeper questions takes years of multidisciplinary knowledge.

Help out the community.  Please mark the thread as "SOLVED" using the Thread Tools button near the top.

---

### Post by hk42 on 2019-10-25
Thinking of it the swapfile should not  be fragmented and that may be 
what the "gaps" were about.
This installation is on a diskless device .
So saving space is important and hibernation is disabled in W10.
Swapfiles are new to me I thought that mkswap only applied to partitions.
As usual a look at the man page was useful.

---

