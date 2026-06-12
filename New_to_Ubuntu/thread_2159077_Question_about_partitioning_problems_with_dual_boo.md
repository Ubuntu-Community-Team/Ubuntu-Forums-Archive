---
title: "Question about partitioning problems with dual booting Ubuntu w/ Windows 7"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by uahsan3 on 2013-07-01
Hey everybody,

I recently (successfully) dual-booted Ubuntu 12.04 with Windows 7. I have Windows 7 on C:\ and I also have D:\. I shrunk D:\ to create a space of about 300GB. I installed Ubuntu on it. I had some problems with something completely unrelated and I uninstalled Ubuntu, intending to re-install it later. 

Now, I started to re-install Ubuntu (I thought this time, I'll work with Ubuntu 13.04). When I checked out my Disk Management in Windows, it showed my previously unallocated partitions as 2 healthy primary partitions (obviously). I deleted one of them (the smaller one), and it got automatically merged in the second one. When I deleted the second one, it became "free space" alongside my D:\ - the box that shows in green in Disk Management. I was under the impression that I will just delete this box, and I will get the black box "Unallocated" one. When I deleted it, there was this warning message that said "This is an extended partition ...etc". I went ahead with it and this error message came up "Unable to delete this partition due to low disk space. I was unable to convert this "free space" into "unallocated". 

Sigh. I thought I'd try out Ubuntu anyway and booted into the LiveCD and chose "Install Ubuntu" and there came the option to "Install Alongside WIndows" and I clicked it... and it just ran. It installed itself, without showing me WHERE it was installing! 

(I think it installed in my external hard drive!)

Anyway, now I am in Live session, having GParted open in front of me. This is what I'm seeing. See attached. 

Please help me out. I'm new to this whole partition thing. 

Thank you

---

### Post by oldfred on 2013-07-01
I do not like auto install as I never know where it will install. I prefer to partition in advance and then use manual install or Something Else to choose / (root). Since swap exists it finds it automatically and I use separate /mnt/data partitions for all data so do not use separate /home.

You are showing NTFS partitions with very little space left. It is my understanding that NTFS works best if 30% is free. And at 10% free you just about cannot run a defrag as there is no working room. And system will be slow as it has fragmentation and has to write to lots of places.

All versions are similar for installing, so examples work for just about every version.
       Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by UltimateCat on 2013-07-02
Looking at the attachment you posted; I would do this if it were my system:-

-Leave dev/sda1 and dev/sda2 alone.

2. Click on and highlight dev/sda3 and delete that partition.
3. Click on and highlight dev/sda5 and delete that partition.
4. Click on and highlight the 'unallocated' partition and while it's highlighted go up to 'new' and create a new partition for your Ubuntu distribution about 20 GB.
5. Click on and highlight the rest of the unallocated or free space and make a 'new' partitiion 'swap'( swap should be in the drop down menu within G-parted) 

That should solve the problem.

The only other way is to re-install Ubuntu and choose to manually manipulate the partitions using the partition mgr that the installer comes with-

---

### Post by fantab on 2013-07-02
To delete an Extended partition you must first delete all the Logical Partitions it contains. In other words make sure the size of unallocated space after Extended partitition is equal to the size of the Extended partitition.
An EXTENDED Partititon is Primary Partition which 'contains' Logical Partitions.

After creating an Extended Partition:
30GB Logical Ext4 Mountpoint=/
2-4GB Logical SWAP
All the remaining GB Logical Ext4 Mountpoint=/home

When Installing Ubuntu choose 'Something Else' optition when the dialog asks you about the 'Installation Type'.

Good Luck...

---

