---
title: "Triple Boot Help Please"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by Image0fman on 2012-09-26
Hello All, 

I currently have a dual-boot system handled by GRUB. Windows 7 and BT5. I have posted a picture taken in gparted of my partition table. I would like to take space from the Windows partition and add it to the BT5 partition. Then I think I would have to create a Logical Volume in the extended BT partition and Install Ubuntu there. Not really to sure what do and would like some tips/help before I screw things up, I currently love my setup but need that Ubuntu partition to play with all the mainstream apps created for it. 


Oh and can anyone tell me what that 1.50MB partition is between windows and bt? I tried extending it but it was being weird. 
Thanks

---

### Post by oldfred on 2012-09-26
Attach screen shot from gparted with the paperclip icon in the edit panel above your message. If editing message, you have to go Advanced to get full edit panel.

Also post this from terminal

sudo fdisk -lu

Mount all partitions so they also are included:
df -h

---

### Post by Image0fman on 2012-09-26
oops forgot to attach my screen. I'm not near the computer atm so I can't post that output just yet

---

### Post by oldfred on 2012-09-26
Partitions now use 1MB as the rounding. It used to round at a smaller number and you did not see the unallocated between partitions. 

You can shrink Windows, but use Windows tools to do that unless it is XP. You then can move the extended partition left with gparted and add logical partitions to the extended partition.

But I do not like large / (root) partitions, especially if multi-booting. If dual booting with Windows, a shared NTFS data partition is often useful. If dual booting with Linux you can use the NTFS or may want a Linux formated data partition. Then / can be small as data is in other partitions. 

I aggressively move data to other partitions. My root is 25GB with about 9GB used including /home. I still have my shared NTFS from when using XP with Firefox, Thunderbird profiles & all photos for use with Picasa. Most new data now goes into a shared data partition.

---

### Post by Image0fman on 2012-09-26
> **oldfred said:**
> Partitions now use 1MB as the rounding. It used to round at a smaller number and you did not see the unallocated between partitions. 

You can shrink Windows, but use Windows tools to do that unless it is XP. You then can move the extended partition left with gparted and add logical partitions to the extended partition.

But I do not like large / (root) partitions, especially if multi-booting. If dual booting with Windows, a shared NTFS data partition is often useful. If dual booting with Linux you can use the NTFS or may want a Linux formated data partition. Then / can be small as data is in other partitions. 

I aggressively move data to other partitions. My root is 25GB with about 9GB used including /home. I still have my shared NTFS from when using XP with Firefox, Thunderbird profiles & all photos for use with Picasa. Most new data now goes into a shared data partition.


Thanks for the info, gunna try some stuff out later tn. So you keep all the profile specific stuff on a shared partiton for "syncing" amongst your different OS partitions?  Pretty Neat.

---

### Post by oldfred on 2012-09-26
I only share "data" not system settings, although sometimes I may copy some from one install to another. My system settings in /home are less than .5GB, so pretty small now a days.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

---

### Post by Image0fman on 2012-09-26
> **oldfred said:**
> I only share "data" not system settings, although sometimes I may copy some from one install to another. My system settings in /home are less than .5GB, so pretty small now a days.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)


Wow, thanks for the links. Its been a crazy day, haven't time to try out the triple boot ninja stuff yet. Wull update tomorrow. Thanks!

---

### Post by Image0fman on 2012-09-27
Update: I successfully created and moved over a logical partiton for my 3rd OS. Haven't installed anything yet. but here's a screen for anyone interested.. Also I am a heavy bt user and have used debian and mint alot in the past.. not sure if I want to go for ubuntu or a derivative of it..


@oldfred I mite do a similar setup such as yours once I get that 3rd OS on there, I know it will be risky and more work, but I like to live dangerously..

---

### Post by oldfred on 2012-09-27
I do have a couple of installs on my sdc, but now boot from sdd, my SSD which has 12.04 & 12.10 on it. I mount a shared NTFS data partition and a Linux formated data partition from sdc and kept swap on sdc, so those are all that are mounted.

---

### Post by Image0fman on 2012-09-28
> **oldfred said:**
> I do have a couple of installs on my sdc, but now boot from sdd, my SSD which has 12.04 & 12.10 on it. I mount a shared NTFS data partition and a Linux formated data partition from sdc and kept swap on sdc, so those are all that are mounted.


WOW, that is awesome. I look like small potatoes compared to that partition table. So under sdc3 u got a bunch of logical volumes I see? I can theoretically do that same... Gunna need a bigger disk =0

---

