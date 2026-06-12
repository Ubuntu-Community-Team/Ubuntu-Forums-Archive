---
title: "Ubuntu fails to start as /home partition is full after docker installation"
date: 2022-08-04
forum: New to Ubuntu
---

### Post by jankosattler on 2022-08-04
Hello community,

  I recently cannot start my Ubuntu system anymore as my separate /home partition is completely filled up. 

  What happened?  
I tried to install the software ncbi/pgap with a docker container, I used the software docker for the first time. During the installation process, the installation stopped with the message that there was no more disk space available. After I restarted the system I could not boot linux anymore. Initially, I vaguely remember, there was an error message about no disk space. But now, 4 weeks later, the message shown is  “[Failed] Failed to start Manage, Install and Generate Color Profile”, or “[Failed] Failed to start Modem Manager” or “…Hostname service” or “…Login service”, interchangeably, eventually ending up on a black screen with a flashing dash.  

What have I tried to solve the problem?
- I started the “Advanced options for Ubuntu” to do an automated clean up. However, this process initially always cancelled due to not enough disk space available. In the meantime (4 weeks later), the program starts, but does not remove any files.
  [FONT=Calibri]- [/FONT]I booted linux from a live USB stick. This automatically also mounted the linux partitions on my hard disk. There I could see the following partitioning:[INDENT][FONT=&amp]o   [/FONT]Partition A: 30 GB completely full (that is likely my /home partition)
  [FONT=&amp]o   [/FONT]Partition B: 119 GB (my swab) 
 [FONT=&amp]o   [/FONT]Partition C: 11 TB, ~7TB available (that should be my root)  [FONT=&amp]
o   [/FONT]3,5 TB unallocated
[/INDENT]
   [FONT=Calibri]- [/FONT]I tried gparted in order to allocate more disk space from the root to the /home partition. However, I was not able to do that as (as far as I understood) the partition was at the beginning of the disk and the unallocated disk space at the end.
  [FONT=Calibri]- [/FONT]I searched the /home partition for “docker” files. I found some, but nothing extraordinary large. I also could not delete them as I did not have the permission.
  [FONT=Calibri]- [/FONT]I did not know which other files I could delete without damaging the system in the /home partition to make more space. The /home folder within this partition, however, seemed to be completely empty.

  How can you help me?  [FONT=Calibri]
-          [/FONT]Firstly, I would need to get my linux system back running. Do you have any tips for me?
  [FONT=Calibri]-          [/FONT]Are there any specific locations where docker might have stored the large data that filled up the partition, so that I can remove these?
  [FONT=Calibri]-          [/FONT]In order to avoid this problem in the future; is there any way to tell docker to use the root partition for installation instead of using the /home partition?

     I will be very grateful for tips!     
Best wishes,  Janko

---

### Post by Tadaen_Sylvermane on 2022-08-04
If the /home is what is causing the problem then load up a live boot, mount the home partition and scan it. I believe

```
du -hcs /mounted/home/*
``` will scan the files and tell you where the heavy hitters are. If you can't afford to lose them then move them to external storage. 

In the future I'd highly recommend an LVM disk layout. It is so nice to be able to expand a volume as needed without worrying about where it is on the disk. LVM is my saving grace these days.

---

### Post by grahammechanical on 2022-08-04
> [FONT=&amp]o   [/FONT]Partition A: 30 GB completely full (that is likely my /home partition)
  [FONT=&amp]o   [/FONT]Partition B: 119 GB (my swab) 
 [FONT=&amp]o   [/FONT]Partition C: 11 TB, ~7TB available (that should be my root)  [FONT=&amp]
o   [/FONT]3,5 TB unallocated

Are you sure? It is very unusual to have a 30GB /home and a 11 TB /root. The other way around would be more usual. Do you really have a 119GB swap partition? Is that not excessive?

We use GParted from a Ubuntu live session. If you want to enlarge partition A then you may need to move the partitions to the right of partition A further to the right by first moving partition C into unallocated space. This will create unallocated space between partition B and partition C. Now move partition B into the unallocated space and you should have unallocated space between partition A and partition B. You can now expand partition A into the unallocated space.

Regards

---

### Post by Impavidus on 2022-08-04
As noted by grahammechanical, your partitioning is a bit peculiar. We normally use about 30GB root partition (but some people may want a bit more), 4GB swap (unless there's a swap file) and the rest /home or whatever we like. 30GB /home is a bit small, even for me, and I'm on a 320GB hard drive. How do you put 4TB of data in a root partition?

A full /home partition leads to login failure, but shouldn't lead to boot failure. So have a careful look at the contents of those partitions from the live disk. The root partition will have directories like /boot, /home, /etc, /usr, /lost+found and some others. On the home partition you should find /lost+found and /username, for every user created on the system. There's no /home directory on the /home partition, but if you have a /home partition, the /home directory on the root partition will be empty.

To delete files on the root partition, you may need your root privileges. You have those on the live disk; just use sudo. Be careful not to remove stuff you need. Deleting some cache (look at /var/cache/apt/archives) or old logs (look at /var/log) is generally safe, at least as a temporary measure, so you can boot your installed system and login. Nothing in your /home partition is critical for the system, but it may be critical for you.

---

### Post by jankosattler on 2022-09-14
Thank you all for your help and sorry that I didn't find the time to reply earlier!

You were correct about the partitions, I mixed up the /home and the /root.

Eventually the tip from grahammechanical worked for me. Like this I could reallocate the disk space and extend the /root partition. And immidiately Ubuntu went back to work ;-)

Haven't found out the origin of the problem yet (why docker flooded my /root partition)...I will just keep my fingers off docker for now!

---

