---
title: "installing 14.04 alongside 12.04?"
date: 2016-03-09
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2016-03-09
This computer has a 128 GiB SSD (sda), divided into three roughly equal EXT4 partitions with 12.04 fall-back in sda1.

It also has a 1T HDD (sdb) which I had thought that had home on it. When I backed /home up Sunday night, I found that home was still in sda1. (What can I say? Clearly didn't get it right two years ago! In those two years, it never occurred to me to check.)

Each of the two 500 Gib partitions of sdb have a lost and found file, but I am unable to see what each contains. In fact, when I attempt to open each, I get this message:
> You do not have the permissions necessary to view the contents of "lost+found". I seem to remember that these are system directories that it needs to keep track of various things and maybe best described as "not user-serviceable", at least not for me. My question is how did they get there? Was this part of the partitioning process or did Ubuntu set them up when it first encountered them? Or what?

I want to rename each of these partitions so as to identify them for which computer they are holding backup snapshots of. So if I use gparted to relabel them, do I need to be concerned about the lost+found files? I assume that they will survive the relabeling, but just want to avoid problems.

Finally, since sba1 holds the current install of 12.04 fall-back, I am thinking that I will install 14.04 Ubuntu Mate in sda2 with /home on sdb1 and run that in for awhile before removing 12.04 from sda1. Do you foresee any issues that I need to provide for?

---

### Post by yancek on 2016-03-09
An explanation of lost+found directories on Linux at the links below.

[http://unix.stackexchange.com/questions/18154/what-is-the-purpose-of-the-lostfound-folder-in-linux-and-unix](http://unix.stackexchange.com/questions/18154/what-is-the-purpose-of-the-lostfound-folder-in-linux-and-unix)

[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

The permissions message means you need to be root to access, use sudo.

Installing 14.04 on sda2 and /home on sdb1 should work as long as there is not data currently on those partitions you need.

---

