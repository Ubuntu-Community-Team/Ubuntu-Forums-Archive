---
title: "Confused with partitions on which ubuntu is installed"
date: 2016-03-12
forum: New to Ubuntu
---

### Post by rev3 on 2016-03-12
Hello forum! I am very new to Ubuntu forums and this is my first post. Please excuse me if I am not in line with the existing methodology of forums.

My problem is, 
I installed Ubuntu 14.04 and upon deleting 
I am using Dell studio laptop with 320GB HDD and 3 GB RAM
My partitions in Windows 7 are
1. OEM partition
2. RECOVERY
3. Windows 7
These three are primary as per Windows 7 and 
4. Extended partition

My extended partition has 4 logical drives along with 61GB free space.

I installed Ubuntu 14.04 on that free 61 GB space (58GB for / and 3GB for swap) and the installation went well. Now I have a dual boot choice by which I can log into either windows or linux.
I logged into Windows7 and in disk management the things I can see are as below
OEM, RECOVERY, Windows (OS), Ubuntu, swap all these 5 are primary partitions (as per their dark blue color which indicates primary partition according to windows).
My extended partition has the same 4 logical volumes.

Now I shrink one of my 4 logical volumes and created some free space (say 10GB). I now created a new 5th simple volume of that free (10GB) space. As soon as my 5th logical volume is created, my linux and swap which are outside of the extended partition are now inside the extended partition with green color on it (stating it as free space). Also upon reboot, I cannot see the dual boot menu. I lost my GRUB. What should I do to make my Ubuntu installation stable? I don't want my installation volume to jump like that upon creation of new logical drive ion extended partition. In future I cannot create a new logical drive if my Ubuntu installation drive jumps like that. Help me!

---

### Post by oldfred on 2016-03-12
Are you attempting to use Windows to create partitions?
Do not do that.
Windows does not correctly see Linux partitions. On major updates or where it rewrites partition table it conviently forgets to write the Linux partition. It is still there but not in partition table. Usually testdisk or parted rescue can restore entry and have working partition, grub usually has to be re-installed.

Best to use gparted if adding partitions.
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by rev3 on 2016-03-12
Thanks OldFred for your assistance.
What I did is, I installed Ubuntu from live USB. During the installation I selected the unallocated space and selected the volume type (primary/logical) and the file system and mount point. I did the same for swap area. I tried the installation by selecting the volume as primary and logical also. Until now I would have tried atleast 10 times with the installation and still I am encountering the same problem (upon creating a new simple volume in extended partition my Ubuntu partition is jumping). I dont want this kind of jump.

One more information which might or might not come into consideration.
A month ago during my first time installation of Ubuntu; I made space for 60GB in my extended partition in windows7 (the volume is free space, I did not create it as a simple volume). Then I installed Ubuntu using live USB and selected that 60 GB unallocated space for installation. This installation worked as accordingly by creating both Ubuntu and swap volumes as logical drives in extended partition. Later a few days ago I deleted those volumes in windows7 diak management (since I wanted them as primary partitions. At the time of deletion I did not have much knowledge on parimary and extended partitions. I now regret my action :(). After deletion I reinstalled Ubuntu. From then onwards this problem of jumping arised. I stated this by thinking that it might add some idea in resolving my issue.

---

### Post by grahammechanical on 2016-03-12
> I dont want this kind of jump.

You may have to live with it. When we have a BIOS boot system with MSDOS partitioning we also have a 4 primary partition limit. And so sda1; sda2; sda3 & sda4 are reserved labels for those possible primary partitions.

You have 3 primary partitions already in use. And Ubuntu needs at least 2 partitions. How do we get around this? We make one of the allocated 4 primary partitions a special primary partition called Extended partition. And inside that extended partition we create as many Logical partitions as we need. But the numbering labels do not follow what we would call logical order. It is logical from the stand point of the partitioning scheme.

I will use my set up as an example.

It has 2 primary partitions - sda1 = Ubuntu 16.04. sda2 = Extended partition. Inside the extended partition there is the swap partition = sda5. What happened to sda3 & sda4. They are labels reserved for when I create 2 more primary partitions.

Also inside the extended partition are another 2 logical partitions. sda6 = data partition & sda7 = and other installation of 16.04. In the past I have used all 4 primary partitions and several logical partitions. As we delete partitions and re-install the labels are changed accordingly.

If I create 2 more primary partitions I would not be surprised if the label for the extended partition changed from sda2 to sda4 and the new primary partitions became sda2 & sda3 and not sda8 & sda9.

You are already using 3 of the 4 allocated primary partitions. You cannot put Ubuntu & swap on primary partitions outside of the extended partition. They can only go into logical partitions inside the extended partition. 

Regards.

---

### Post by rev3 on 2016-03-12
Dear grahammechanical, thanks for your reply.
I am not bothered about the numbering of the partitions but I am bothering about the physical existence of the partitions (primary or logical). I support your sentence "[COLOR=#000000]You cannot put Ubuntu & swap on primary partitions outside of the extended partition. They can only go into logical partitions inside the extended partition.[/COLOR]" This is what I want actually! To present the Ubuntu and swap area in logical drives instead of primary. How can I attain this?

---

### Post by yancek on 2016-03-12
You can determine whether you have primary or logical drives by running:  sudo fdisk -l(Lower Case Letter L in the command).  Any partition numbered 5 and higher is a logical partition.  1-4 would be primary.  I have a system with windows 7 and a number of Linux systems on two hard drives.  There are over 20 partitions between the two drives.  If I go to windows 7 Disk Management, 20 of them show as Primary partitions which of course, is not possible.  As oldfred said, windows doesn't identify Linux partitions correctly.

---

### Post by rev3 on 2016-03-12
Okay yancek :) I agree with that since the same is with my case in windows7
but where I stuck is that when I extend some space and create a new simple volume in windows7, the shown primary partition of Ubuntu jumps into extended partition and it shows as free space and also eating my grub! How do I prevent that? In future if extend my logical drive and create another volume , I should not get that Ubuntu partition jumped which results in my grub loss and mainly my Ubuntu data loss. I am worried about that! Please help me.

---

### Post by oldfred on 2016-03-12
From Post #2
> Are you attempting to use Windows to create partitions?
Do not do that.

---

### Post by rev3 on 2016-03-13
Hello oldfred, what you said is right. After a little research I understood (convinced) that I should not use Windows to create partitions in my scenario as the Ubuntu partitions are not correctly seen by Windows. So I need to use Gparted to further create logical drives in extended partition. I installed gparted and tried to create and delete partitions successfully without any 'jumping', unlike in Windows partitioning. Another reply by grahammechanical also states the same around the other way.

thank you for your assistance :)
problem solved

---

