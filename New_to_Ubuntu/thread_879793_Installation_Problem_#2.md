---
title: "Installation Problem #2"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by luangwa on 2008-08-04
I have two hard drives and want to install Ubuntu on the free space of the second.  

Previously I had installed Ubuntu 7.04 and then I tried upgrading to 7.10 with disastrous results. I wanted a clean install so I removed the dual boot system using a Win98 SE startup disk and the fdisk/mbr. I used Partition Magic in Windows to view the second hard drive and found the faulty install had set up a ubuntu, nfts, partition on the drive and a swapfile partition.  was left with 4 partitions (1 nfts - with window files, a swapfile, a linux etx3, and ubuntu ext2. I reformatted each partition to nfts using Partition Magic and was able to merge the former linux partitions but now I was left with two partitions, one 30GB nfts and the other as 30 GB unallocated. 
When I read I thought everything would be fine and tried to install 8.04 only only to get "too small a space". I moved the slider bar to increase the size but I still received the same error message.

How can I correct this? The second drive is a 60Gb drive in which half is filled with files I want to keep. I would like to install Ubuntu 8.04 on the other 30GB. How can I accomplish this?

---

### Post by phidia on 2008-08-04
Maybe you got the "too small a space" message because gparted didn't register the changes. It's probably not a good idea to try to make mulitple changes in gparted.
Anyway I like cfdisk for making & deleting partitions. 
cfdisk is a commandline tool but it's quick and fairly easy to use.
Before you use that tool enter "sudo fdisk -l" and be familar with your specific set up.
There is also the Ubuntu wiki [here]("https://help.ubuntu.com/community/forum/installation/Partitioning") on partitioning although that mostly focuses on gparted.

---

### Post by luangwa on 2008-08-04
Thanks for your help. Can I do this just using the CD? How does ubuntu identify the drives & partitions? As you can tell I'm green as grass.

---

