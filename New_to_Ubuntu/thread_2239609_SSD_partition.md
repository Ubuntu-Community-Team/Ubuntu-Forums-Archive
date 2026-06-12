---
title: "SSD partition"
date: 2014-08-14
forum: New to Ubuntu
---

### Post by datino on 2014-08-14
Hi, I'm new to Ubuntu and to this forum,

I have an 120GB SSD (C: ) with Windows 8 installed. I tried to install Ubuntu via USB live creator but I allocated too much space to Ubuntu (90GB) leaving just a few to Windows 8 (3GB) so I quit the installation but it was probably too late.
From Windows 8 I found the partition and deleted it but now the situation looks like this

 [ATTACH=CONFIG]255491[/ATTACH]

and looks like my SSD total space is 30 GB (???). I can't extend the volume. I would like to install Ubuntu (btw how much space should I allocate for Ubuntu?) and having at the same time the possibility of booting with Windows 8 correctly.

What do you suggest?

Thanks
Andrea

---

### Post by oldfred on 2014-08-14
It looks like the unallocated it in an extended partition?
And extended partition is one of the 4 allowed primary partitions but it can hold an unlimited number of logical partitions. Windows only boots from primary partitions, but Ubuntu will work from logical partitions without issue.

I usually suggest 20 to 25GB for / (root) when you have a separate /home or data partition(s) on another drive. You also need a swap partition but it does not have to be on SSD as if you have what most new systems have in at least 4GB of RAM you may never or rarely use swap. 

You can use gparted on Ubuntu live installer to shrink the extended partition. But I would use Windows to resize the Windows system partition and immediately reboot so it can update to its new size.
Make sure you have fastboot or the always on hibernation off in Windows.

       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html


[/URL]

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

