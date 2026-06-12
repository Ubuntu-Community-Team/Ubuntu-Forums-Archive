---
title: "Dual Installation with Windows XP"
date: 2014-09-17
forum: New to Ubuntu
---

### Post by Mike_Bermingham on 2014-09-17
Hi I'm a complete novice when it comes to Ubuntu.  I'm trying to install Ubuntu v14 alongside win xp and have got to the window where it asks you to allocate drive space for bot windows and ubuntu; which I have done but it won't highlight install now and I don't know why.
I am installing it on a Compaq NX9010 with Celeron 2.5Ghz, 2gb RAM, 160GB Hard drive,

---

### Post by grahammechanical on 2014-09-17
How many partitions are on the hard disk? The boot system (BIOS) on your machine must be like the one on my machine. There is a 4 primary partition limit. Which means that we cannot have more than 4 partitions unless we use a work-around.

We need to take one of those primary partitions and turn it into a special primary partition called an Extended partition. Then inside the extended partition we can create as many Logical partitions as we like.

First, we need to know how many partitions and what they are used for. Which of the install options did you choose? Install alongside? Or Something Else?

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Regards

---

### Post by Mike_Bermingham on 2014-09-17
Hi grahammechanical
I'm installing alongside and as far as I am aware it has only one partition but with the installation I assume there will be two.
Although I haven't done anything since my original question, the installation has moved on and the options changed from Quit/back/install to Quit/back/continue with the continue greyed out!
Many thanks for your help so far much appreciated

---

### Post by yancek on 2014-09-17
You need to check to see how many paritions you actually have.  You can do this from the Ubuntu medium by opening a terminal; hold down the Ctrl+Alt+t keys simultaneously and when the terminal opens type:  sudo fdisk -l(Lower Case Letter L in the command).  That will show the number of partitions available and you can post it here if you want.

I'm not sure what you mean by allocate drive space for windows as it is already installed?  Your partitions for windows may be taking up the whole drive and you might need to shrink the windows partition to create space.  You can get this information from the terminal again, open it and type:  parted
You will get a prompt and just type:  print free
You can post that output here if you don't understand it.

---

### Post by Rob Sayer on 2014-09-17
> **Mike_Bermingham said:**
> Hi grahammechanical
I'm installing alongside and as far as I am aware it has only one partition but with the installation I assume there will be two...

Read post #2 again.

And I'd recommend Xubuntu 14.04.  Ubuntu with the Unity desktop is meant for computers powerful enough to run Windows 7 or 8.  Even if you're talking about a dual core Celeron ... and I suspect it's single core ... I wouldn't run unity on that machine.  I won't run it on my i3 based 4Gb laptop.  I tried it and it's too slow.

---

### Post by jimmy-frydkaer on 2014-09-17
Depending on how old your Windows install is you might want to de-fragment the entire disk before attempting to install an additional OS such as Ubuntu.

I second what Rob Sayer said. Ubuntu, with Unity is way to heavy for your hardware. Go for Lubuntu or Xubuntu. Forget about Kubuntu and Ubuntu GNOME your hardware isn't strong enough.

---

### Post by Vladlenin5000 on 2014-09-17
So... How exactly someone assert outright "(...) Unity is way to**o** heavy for your hardware" without knowing the graphics subsystem? The CPU and RAM are fine - far from ideal but will do the job just fine if helped by a good graphics card from 7-8 years ago!

---

### Post by Mike_Bermingham on 2014-09-17
Hi yancek
Below is the information produced;
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1*512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90e890e8

    Device Boot         Start              End            Blocks       Id       System
/dev/sda1   *              63    312560639    156280288+      7       HPFS/NTFS/exFAT

Hope that gives you the information your asking for
Many thanks for your help
Kind regards

---

### Post by yancek on 2014-09-17
It looks like you have on partition for xp but it is taking up the entire disk so you will need to shrink it so that you have free/unallocated space on which to install Ubuntu.  Go to the link below and scroll down to the Table of Contents.  Section 6.B explains how to resize a partition with GParted.  It's on the Ubuntu medium so open a terminal and just type?  sudo gparted

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by whitesmith on 2014-09-17
> **Rob Sayer said:**
> Read post #2 again.

And I'd recommend Xubuntu 14.04.  Ubuntu with the Unity desktop is meant for computers powerful enough to run Windows 7 or 8.  Even if you're talking about a dual core Celeron ... and I suspect it's single core ... I wouldn't run unity on that machine.  I won't run it on my i3 based 4Gb laptop.  I tried it and it's too slow.

And that's only half the problem.. XP is no longer supported, meaning that every hacker in the world has a painted a big, bright target on it. What I would--and did--do is install Xubuntu, giving it the entire disk. Then I installed a virtual machine for Windows 7. If a virus manages to  enter the Win subsystem, it can't reach Unix because the Host and Guest OSes are physically separate. Yes, somebody could introduce malware into Windows but it will be trapped, and pose little if any threat to Linux. Just make sure you install as much memory as possible in your box and you'll be good to go.

---

### Post by mastablasta on 2014-09-18
> **yancek said:**
> It looks like you have on partition for xp but it is taking up the entire disk so you will need to shrink it so that you have free/unallocated space on which to install Ubuntu.  Go to the link below and scroll down to the Table of Contents.  Section 6.B explains how to resize a partition with GParted.  It's on the Ubuntu medium so open a terminal and just type?  sudo gparted

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

before partitioning you should defragment the disk at least 2 times (second time will be faster) and do a check disk afterwards.

best way is to use windows disk manager to create empty disk space (unformatted) at the end of the disk.

---

### Post by Mike_Bermingham on 2014-09-18
hi as I stated I am a newbie, but what you've said makes a lot of sense so I going to follow what you've said but how to I format the Hard Drive and partition it only for Xubuntu, then create a windows 7 virtual machine.  Details, details as much as possible and a very big thank you in anticipation. 
Best regards

---

### Post by yancek on 2014-09-18
You can partition and format the drive during the installation.  After installation, you should be able to download VirtualBox software and install it and then install windows inside VirtualBox.  You can use other virutal software so you don't need VirtualBox specifically .

---

