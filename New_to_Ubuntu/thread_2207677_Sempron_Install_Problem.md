---
title: "Sempron Install Problem"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by paul105 on 2014-02-24
As an absolute newbie I'm wondering if there are any known problems with Ubuntu 12.04 and the Sempron processor?
I'm trying to run 12.04 (32 bit version) on my machine and keep having problems:
The most serious is that I'm trying to do an install of 12.04 beside an existing Windows XP/Home installation.  When I go to the install utility it only offers me two (2) choices:  #1  Completely replace and delete XP   -or-  #2  Something else.
I've tried following the instructions for both a bootable DVD and also a bootable USB drive.  I get the same results with both.
I *really *want to retain my XP as well as Ubuntu since I have and run a couple important programs which I don't believe are compatible with Ubuntu.
Am I doing something wrong or is there some other issue?
Would I be wise to try another version?  I've got access either to an old DVD with version 8.?? (Heron) on it or I could download 13.01 and try that.
Please advise.

---

### Post by zvacet on 2014-02-25
You can dual boot your Xp with Ubuntu 12.04 just fine.Do not hesitate to click on [link]("http://askubuntu.com/questions/148881/dual-boot-windows-xp-and-ubuntu-12-04"). ;)

---

### Post by grahammechanical on 2014-02-25
Here is the problem. On machines as old as yours and mine we are only allowed 4 primary partitions. That is why the installer will not install Ubuntu unless you overwrite XP (Use the Entire Disk) or modify the partitions using the Something Else option.

You need to

1) defrag the disk more than once using a Windows utility and make sure that XP loads after each defrag.

2) using a Windows utility resize one of the partitions to create space for Ubuntu

3) using a Windows utility remove one of those Windows partitions so that you only have 3 primary partitions.

Then the Ubuntu installer may give you the option to Install Alongside. It will use the free/unallocated space to create a special primary partition called an Extended partition and in that Extended partition it will create two Logical partitions, one for Ubuntu and one for Swap.

The version of Ubuntu is irrelevant. This is the fact of life for hard disks using the Master Boot Record partitioning scheme.

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Regards.

---

### Post by paul105 on 2014-02-25
I guess I don't understand disk partitions very well.  I thought I only had one, but from what you're saying it sounds like that assumption is wrong.
In XP I've only got one active user, but a while ago I had an XP problem where I created a new user (the one I use now) and wasn't able to delete the old user.  Did I inadvertently create new partitions then?  If so how do I determine which partition(s) are the ones I need and which ones are idle and therefore could be deleted?  Or does it sound like I'm understanding what you said correctly?  If I'm still not getting it, *please* feel free to correct me.
Thank-You for the assistance.

---

### Post by paul105 on 2014-02-25
Hmmm . . . don't understand the stuff in the link yet, but tomorrow I expect to have more time to really concentrate on what I'm reading.  That should clear things for me.
Thank-you for the assistance.

---

