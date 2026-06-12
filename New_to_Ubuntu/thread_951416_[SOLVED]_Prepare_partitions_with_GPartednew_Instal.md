---
title: "[SOLVED] Prepare partitions with GParted/new Install?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by germanix on 2008-10-18
I am doing a new install and wish to have a seperate "Home" partition. I have chosen the manual option in GParted. I currently have the following partitions:

sda1 ext3 20GiB (here I want to boot from)
sda3 ext3 292 GiB (this will now be my home)
sda5 swap

I have never done this before, so I do not know how to set up the partitions so that Ubuntu installs the "Home" where I want it.
How do I continue from here, set the mount points etc.?

---

### Post by Nepherte on 2008-10-18
This might help: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by eternalnewbee on 2008-10-18
> **germanix said:**
> I am doing a new install and wish to have a seperate "Home" partition. I have chosen the manual option in GParted. I currently have the following partitions:

sda1 ext3 20GiB (here I want to boot from)
sda3 ext3 292 GiB (this will now be my home)
sda5 swap

I have never done this before, so I do not know how to set up the partitions so that Ubuntu installs the "Home" where I want it.
How do I continue from here, set the mount points etc.?

I usually do this when I get to partitioning, during the installation.
But wait for advice from others who are better at home with Gparted.
Good luck.

---

### Post by Steve1961 on 2008-10-18
The key to doing this is to choose the correct option when you get to the partitioning stage of installation.  You need to choose the manual option.  You should then mount your main partition on / and your home partition on /home - you can select both from a drop down menu - and select ext3 for both  I think that the swap partition will be picked up automatically, but if there's an option to choose swap for sda5 do that.

---

### Post by Elfy on 2008-10-18
If the partitions are already made then it's simple enough. Use manual when the partition part of the install is reached.

Pick sda1 - edit partition, pick ext3 from the Use As box and / from the mountpoint, close

Pick sda3 - edit partition, pick ext3 from the Use As box and /home from the mountpoint, close

Carry on with the installation - check when it shows you that sda1 is to be ext3 and / and sda3 is ext3 and /home

Swap will be sorted automatically

---

### Post by germanix on 2008-10-18
This might help: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
__________________
This was what caused the whole problem. I tried to use this tutorial 3 times the last 3 weeks and it does not work for me. So I am forced to do a new install as I cannot boot anymore. I used the live CD to do the patitioning the way I wanted. I now just need to tell Ubuntu to install "Home" on the sda3 partition and to boot from the sda1 partition during the install. I now face a screen "prepare partitions" in GParted and need somehow to set mounting points (I assume) and do not know how to do it.

---

### Post by germanix on 2008-10-18
Forrestpixie, Steve1961, I understand. Sounds simple enough. I will now try it and report.

---

### Post by eternalnewbee on 2008-10-18
> **germanix said:**
> Forrestpixie, Steve1961, I understand. Sounds simple enough. I will now try it and report.

Click on the partition you want to mount from, choose edit, and then mount as /.
same step for home, but choose home.

---

### Post by eternalnewbee on 2008-10-18
I think that the swap partition will be picked up automatically

I don't think that will happen if you choose to manually partition, but I am not 100 % sure of that..

---

### Post by germanix on 2008-10-18
I now had a seperate home partition, so all was fine, untill I then decided to restore the back-up of my home file that I had made with SBackup. Something went terribly wrong and I cannot boot into the system once again. So I am now doing a new install once again. At least I now know how to get the "Home" configured.
Thank you all-
.

---

### Post by gusanto on 2008-10-24
Hi all,
Sorry if I'm hijacking this thread.
I have a related quesstion to ask.
My system(Ubuntu 8.04) is messed up after installing the kernel 2.6.24-21 and playing around with suspend/hibernate problem in my laptop (Sony Vaio VGN-NR120E). Now I'm waiting for the new 8.10 version to come and will fresh install it but with the separate partition (I don't have separate /home partition yet so far). I'm thinking to create new partition as /home (if still possible).
So far I have these partitions (I dual Ubuntu with Vista):
> Partition       Filesystem     Mountpoint   Size         Flags
unallocated            unallocated                 1.00 MiB
/dev/sda1              ntfs                        7.37 GiB
/dev/sda2              ntfs                       92.57 GiB      boot
unallocated            unallocated                 5.94 MiB
/dev/sda4              ext3             /         29.57 GiB
/dev/sda3              extended                   19.53 GiB

My plan is to shrink the /dev/sda4 partition to 20 GiB and make the rest as /home partition. Is that possible to do it on my hard disk where I have already 3 primaries and 1 extended partition.
Please give me some guides.
Thanks.

---

### Post by Elfy on 2008-10-24
It's hard to be completely sure from that - run ```
sudo fdisk -l
``` but assuming that sda4 is in fact within the extended then it would be a matter of shrinking sda4 and creating a new partition inside the extended.

If though sda4 is not inside then you need to shrink sda4, grow sda3 and then make a new partition within the extended.

It depends what you want to do, sometimes you need more room in tmp - working with video files can use a lot of temporary space, but I would suggest that 20Gb for / is quite big - mine is 9.9G and I've used  5.4G 

I though don't actuially feel the need for a larger /home as I don't use it now for data - keep that on seperate partitions.

---

### Post by gusanto on 2008-10-25
> **forestpixie said:**
> It's hard to be completely sure from that - run ```
sudo fdisk -l
``` but assuming that sda4 is in fact within the extended then it would be a matter of shrinking sda4 and creating a new partition inside the extended.

If though sda4 is not inside then you need to shrink sda4, grow sda3 and then make a new partition within the extended.

It depends what you want to do, sometimes you need more room in tmp - working with video files can use a lot of temporary space, but I would suggest that 20Gb for / is quite big - mine is 9.9G and I've used  5.4G 

I though don't actually feel the need for a larger /home as I don't use it now for data - keep that on seperate partitions.

That's right, sda4 is not inside sda3, sda4 is a primary partition itself.  So I basically already have 4 primary partitions (3 primary + 1 extended). 
In this case, if I shrink sda4 then I grow sda3, I'll be able to create a new logical partition within sda3 then I can assign it as /home partition. Am I right?

---

### Post by Elfy on 2008-10-25
yes, you are right - > In this case, if I shrink sda4 then I grow sda3, I'll be able to create a new logical partition within sda3 then I can assign it as /home partition. Am I right?

---

### Post by gusanto on 2008-10-25
Hi there,
Here is the screenshot of my hard drive partition.
[ATTACH]89615[/ATTACH]
I have maximum primary partitions allowed (3 primary + 1 extended).
The final objective is to create /home partition.
I tried to grow the sda5 to the left but it's not possible. 
I'm thinking I have to move the unallocated to the right side of sd5 (OR move sda5 to the left side of the unallocated partition) THEN I can grow the sda5 to the right to take up the unallocated space. If this idea is correct, how to do it.  I used gparted from the Hardy 8.04 liveCD to do all these jobs.
Any suggestion?

---

### Post by Elfy on 2008-10-25
Before you can do anything you must right click the swap partition and unmount it.

To move - use move/resize and instead of resizing, use mouse to move the partition to where you want it.

Be aware that if you used UUID in your fstab at all then it has to be amended before you can boot or you'll get a fsck error 8.

On more thing, unless you are hibernating/suspend it is unlikely that you need to have a 3GB swap partition.

It can take a _long_ time to move/resize partitions - don't assume that it has stopped/crashed.

One more thing - make sure of backups in case of failure.

---

