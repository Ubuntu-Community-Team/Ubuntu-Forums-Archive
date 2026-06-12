---
title: "[SOLVED] NFTS Partition not found while Installing Ubuntu"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Life.exe on 2008-10-27
This is my first time installing Ubuntu and first post, earlier today I formatted my hd and re-installed windows with plans to also dual-boot with Linux. As you should know when you create the new partition during the installation of windows the partition occupies almost all the space (It saved me 8g i don't know why and don't care). My first step was done, so I went to install Ubuntu using the burned disk I had created earlier following the guide ([https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)). For the Ubuntu install process i followed the guide ([http://www.psychocats.net/ubuntu/dualboot#notes](http://www.psychocats.net/ubuntu/dualboot#notes)) I followed steps 1-3 with ease however when i reached step 4 of the installation process ("Dealing with Partitioning" in the guide) it said that i should have 4 options available, but i only had 3 options displaying, the Guided - resize option was left out.

Main Problem
When i tried to manually create the partitions i did not have an option to create a NFTS partition for windows. My plan was to have 10g NFTS, 20g ExT3, 2g Swap, and what ever memory was left for Fat32...what am i doing wrong?

---

### Post by ashmew2 on 2008-10-28
By your post I understand that your main problem is that you are not able to make an NTFS partiton ( it is greyed out ) , So when you boot into the live cd , go to Applications > Accessories > Terminal and type in :

```
sudo apt-get install gparted ntfsprogs
```

Press Enter.
Now start up the install process and see if you are able to create an NTFS drive. If you are still not able to do that , quit the installation.
Open up the terminal and type :

```
sudo gparted 
```

You can modify your partitions here. After you have Saved/Applied changes , start the install process again and i think you should be fine!

---

### Post by bumanie on 2008-10-28
Post the output of (ie and copy and paste the output)> sudo fdisk -luYou can do this from within ubuntu or from the ubuntu live cd - go to Applications --> Accessories --> Terminal

---

### Post by Life.exe on 2008-10-28
Thanks for your help ashmew2 however this has not fixed my problem. Although i did find out new information. When i was in the gparted app. there was a warning sign beside my hd saying:

Error: This software has detected that the disk has at least 43 bad sectors

This is not the full warning statement as it is too long form me to type out right now and i can not copy and past it. It suggests that i make a back up, (done that a long time ago) and to run chkdsk /f /r, (think i have done that, i did the my computer-right click c:-tools-Error checking).

As for bumanie this is the information you asked for:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03250325

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   120085874    60042906    7  HPFS/NTFS

---

### Post by tarps87 on 2008-10-28
> **Life.exe said:**
> 
Main Problem
When i tried to manually create the partitions i did not have an option to create a NFTS partition for windows. My plan was to have 10g NFTS, 20g ExT3, 2g Swap, and what ever memory was left for Fat32...what am i doing wrong?

To do this you would have to reformat you hard drive, if you are going to do this I would suggest reinstalling windows, during the installation create a 10GB partition and tell in to install to it (if you post what version of windows you are using I can tell you how to in more detail)
Once you have done this, install Ubuntu use the manual option create the 2GB swap and 20GB ext3 partition and set the mount point to /
I do not remember if you can format a partition to fat32 during the install but I know it can be done after.
Why do you want a fat32 partition?
If it is for transferring between windows and Ubuntu, Ubuntu can read and write to a ntfs partition and there are programs that will allow windows to read and write to a ext3 partition.

---

### Post by Life.exe on 2008-10-28
I am using windows xp When i formated my hd eariler to install windows it never gave me an option to select the size of the ntfs partition, i may be wrong because i cant remember too well. It would be very nice of you if you could further help by explain in further detail like you said. I want the Fat32 partition so windows can easily read from it with out the help of additional programs to support windows handicap >.<

I also am curious about the warning that gparted notified me of

Error: This software has detected that the disk has at least 43 bad sectors

can some one further explain this, is it fixable?

I am currently at school right now so i can not attempt anything yet.

---

### Post by ashmew2 on 2008-10-28
I wouldnt recommend making a shared Ext3 partition between Win and Lin because ive tried that and i still cant access any of my 12 partitions from Windows ( all are ext3) ;)

---

