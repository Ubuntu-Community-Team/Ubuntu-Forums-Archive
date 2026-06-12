---
title: "windows D drive not mounting after installing ubuntu"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by stelmo on 2008-10-23
Hi

I am a very new user to ubuntu and i have a question. 

I have a desktop with two internal hard drives. I installed ubuntu on the C drive which had windows. I did a full installation, no partition - full installation,  if understand deleting windows as I did not need windows anymore (i really do not like it). 

Now Ubuntu is working fine but i had another drive (so D drive) full of data which i can't seem to see in ubuntu. Do i need to do something to mount it??? i really need to access this internal hard drive. 

When i type sudo fdisk -l in terminal i have roughly this (sorry don't have info in front of me): 

/dev/sda  boot linux
/dev/sda2 - extended
/dev/sda5/ - linux/solaris 

what do i do to mount or access the other drive or is it lost?? 

thank you

---

### Post by Elfy on 2008-10-23
We do need to see the result of that command - but if it only has 3 drives shown like that then it would appear that there is not ntfs drives.

In the meantime I wouldn't use the pc at all as it might be possible to get the information back, but everytime you write to the hdd it minimises the possiblities.

---

### Post by seshomaru samma on 2008-10-23
In order to help you we need the exact output of sudo fdisk -l

---

### Post by Bölvaður on 2008-10-23
Do not panic.

With that said, you probably did.. but please, it is all under control.
What you need is a data recovery cd. Some one will hopefully give you a link or you can search on the internet your self :) It is always suggested to take backup of all your data that you dont want to lose, because there is always the chance that something goes up.
What I belief what happened to your data is that you accidentally chose to install ubuntu on the whole hard disk or hard disk_**s**_.

But I guess there is always the chance that the "D:" is still there somewhere.

---

### Post by bodhi.zazen on 2008-10-23
I know with a new OS there is a ton of terminology. May I suggest you take a look at this link ?

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

The terms C:\ and D:\ are not has helpful.

Use :

```
sudo fdisk -l
``` to list your partitions. Please show us (copy - paste) the entire output.

---

### Post by stelmo on 2008-10-23
here si the info after sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4190f8e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9636    77401138+  83  Linux
/dev/sda2            9637        9729      747022+   5  Extended
/dev/sda5            9637        9729      746991   82  Linux swap / Solaris
guest@desktop:~$ 

let me know and thank you.

---

### Post by bodhi.zazen on 2008-10-23
From what you have posted, I do not see your second hard drive.

Check to see the cables are properly connected.

---

### Post by Duck2006 on 2008-10-23
What type of internal hard drive is it? eg: ide pata sata raid ect.

---

