---
title: "How to do the partitioning during 1st installation of 12.04"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Toporagno on 2012-05-01
Hello everybody,
I'm totally new to Linux and I want to install Ubuntu 12.04 LTS on my pc that runs XP from a live CD.
My HD is formatted in 4 NTFS partitions C (primary partition where XP reside) D (logical partition used to store my documents) E (primary partition where I put the programs) and F which is empty (primary partition of 166GB).
I've read that would be a good thing to do some similar partitioning for Linux (swap, / , ,/boot,/home). Can I do it during the installation from the live CD or I have to take some steps before? and in that case what I should do?
Thanks in advance for any help.

---

### Post by oldfred on 2012-05-01
Welcome to the forums.

With MBR you only can have 4 primary partitions, but one primary can be converted to an extended and hold many logical partitions. Windows only boots from primary, but Linux boots from logical. Windows also reads data from NTFS partitions that are logical also.

Unless you have an old system with a BIOS boot limit of 137GB, you should not need a separate /boot.

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Toporagno on 2012-05-01
Many thanks oldfred!
I'll go and dig those articles you pointed out.
P.S. Should I put SOLVED in this post?

---

### Post by strask on 2012-05-01
> **Toporagno said:**
> P.S. Should I put SOLVED in this post?

If you are happy with the solution, then by all means mark it as solved from the thread tools menu at the top of the page. :)

---

### Post by Toporagno on 2012-05-03
Ok so I went and read all the articles which where very useful. I decided to move my documents from D to F (you can only have 1 extended partition), then I partitioned D (extended partition) as suggested by oldfred in 3 logical partition (I don't really need the swap partition as I have 3Gb of memory but as mentioned that would speed up the install) 25GB for root, 2 GB for swap and the remaining for home (I didn't formatted them). I did this in the XP console Computer management.
Then I launched the Ubuntu installation, it presented me 3 options: install alongside XP, erase XP and install Ubuntu instead and other which lets you organize the disk space. I chose the last one which leaded me to the partition manager, clicked on the different partitions I had created, clicked on change and set the mountpoint and the formatting. It was very easy and straightforward and now I'm running a dual boot machine with XP and Ubuntu.
Thanks oldfred! :KS

---

### Post by oldfred on 2012-05-03
You are welcome, glad you got it working.

---

