---
title: "Need to merge two partitions on ubuntu 11.10"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by vijaybirur on 2012-06-25
I am very very new to linux.
I was using Win7 on a partition. Inorder to install Ubuntu 11.10, i shrinked this partition and installed Ubuntu 11.10.
But the space for Ubuntu has become less. Hence I took some more space (25GB) from another partition.

I dont know how to increase the size of the partition where ubuntu is installed.
I also dont know which partition has the ubuntu.
Any help is greatly appreciated.
Please guide me through steps so that I can perform the merging without any error.

Following is the report of "sudo fdisk -l" command


vijaybirur@vijaybirur-Satellite-Pro-S300:~$ sudo fdisk -l
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x33293328

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61448624    30724281    7  HPFS/NTFS/exFAT
/dev/sda2       470270745   488392064     9060660   1c  Hidden W95 FAT32 (LBA)
/dev/sda3        61448686   470270744   204411029+   f  W95 Ext'd (LBA)
/dev/sda5        61448688   163846934    51199123+   7  HPFS/NTFS/exFAT
/dev/sda6       163846998   238687643    37420323    7  HPFS/NTFS/exFAT
/dev/sda7       266245308   315807743    24781218    7  HPFS/NTFS/exFAT
/dev/sda8       368643618   470270744    50813563+   7  HPFS/NTFS/exFAT
/dev/sda9       238688256   260231167    10771456   83  Linux
/dev/sda10      260233216   266244095     3005440   82  Linux swap / Solaris
/dev/sda11      315809792   368642047    26416128   83  Linux

Please help me.
I have attached the screenshot of the gparted which showed the partitions.

Please provide me all the steps.

---

### Post by oldfred on 2012-06-25
You do not have a lot of room to work around. NTFS partitions work best with 30% free space, slows with 20% free and just about stops at 10% free. 

Almost all your free space is your new partition but it is not adjacent to / (root) partition so you have to move swap and sda7 right, but have to delete new partition to do that. 

Another choice would be just to move /home to the new partition. But your new partition is ext2 and you really should be using ext4 or at least ext3 to have the journal which allows repairs if you get corruption from an abnormal shutdown or power failure.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by vijaybirur on 2012-06-26
Hi, Thanks a lot for your reply.
However, I have absolutely no knowledge on the terminologies used in Linux space.

I am a Windows developer and now I am greatly inclined towards working on Linux but I have not used any Linux OS.
Somehow, I installed Ubuntu 11.10 by looking at the screenshots of article.

I request you to kindly tell me which is the root partition.

Also tell me the steps with each command to be executed.

---

### Post by Cheesemill on 2012-06-26
First of all make sure that you have a full backup of all of your data as any operation involving moving partitions contains an element of risk, if you make a mistake you can easily lose a lot of data.

Next step would be to boot from a Ubuntu Live CD, you can't move partitions around from your current installation as the partitions are in use.

Once you are running gparted from the Live CD you will need to make sure all the partitions are unmounted, first right click on  sda10 and select Swapoff and then  right click on any other partitions with a key symbol next to them and select Unmount (you will need to unmount sda3 last).

You now need to delete sda11 so that it is unallocated space.

You will now be able to first move sda7 all the way to the right, then sda10 and then finally resize sda9 (your root partition) to take up the available free space.

All in all this operation could well take several hours.

Please post back if you are unsure about anything and remember to have a backup first.

---

