---
title: "Delete old ubuntu partition"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by peterson43 on 2012-01-21
I have a computer with a dual boot setup of windows Vista and Ubuntu. I was running Ubuntu 10.04, but there were some major issues (sudo was corrupted and the wireless no longer worked) so I decided to just install fresh a Ubuntu 11.10. 

When I installed the new Ubuntu I thought that I was replacing the old Ubuntu partition, but apparently I just re-partitioned the non-Windows partition into two different Ubuntu partitions and I didn't make my new Ubuntu partition big enough. Now I'm running out of room with my new Ubuntu installation. 

I think what I want to do is just completely delete the old partitions. What is the easiest and safest way to do this? I've attached a picture of my partition map from gparted. 

I figured out that the old partitions that I no longer need are the sda6 and sda7 partitions. In gparted it appears that I could delete them by right-clicking on the partition map and choosing delete. Is this a smart/safe way to do this? Should I be doing this from a livecd session instead of a regular login session?

Also, it appears that I have two swap partitions. I think the old one is the 6GB one and the new one is 3GB. Is there a way to tell for sure. Since I have 3GB of RAM on my computer and I've heard that the swap should be twice as big as the RAM I was thinking of expanding the swap partition when I resize the other partitions. I seem to remember hearing that resizing swap can be dangerous as well. Is this true and how do I avoid possible errors? 

Thanks for any help.

---

### Post by Double.J on 2012-01-21
Hi there!

Yes it's best to do this from a live cd - as this will allow you to edit your root partition, for your current install - move it, expandit etc - basically make better use of the space available - you can't edit your root partition if your running off it ;)

But you are quite right in that right click, unmount, then delete will free up the space.

A couple of tips - always click apply after each action - don't build up a large list of things to do - this can cause gparted to crash and mess up your partition table in rare instances... that'll really ruin your day!

Back up first - always the golden rule to any partitioning of any disk - make sure you're backed up first!

As for swap - you may have to right click and "swapoff" to edit the partition. The traditional piece of advice is that swap should be twice the size of your ram... now we can have 16GB of RAM at a relatively affordable price, this is silly - a 32GB swap for most people if silly. Basically aim for 1GB over the amount of RAM your system usually uses - this will leave plenty of space and enable you to hibernate just fine.

Hope it helps.. if you'd like any more info, please just ask :)

---

### Post by Savio2010 on 2012-01-21
First thing BACKUP all important data from all partitions to an external drive.

If your HDD is in good health, boot Ubuntu Live CD and delete, re-size the partitions.

About swap for 3 GB or RAM I guess 5 GB of Swap swap is good specially if you are using hibernation. 

If gparted does your work successfully reboot into windows and see if everything is fine there.

Later go ahead and boot Ubuntu. Swap partitions may need to be edited. in the /etc/fstab

---

### Post by peterson43 on 2012-01-21
Thanks for the answers so far. 
However, no answer yet to my question about how to tell which swap partition I should delete (or if it even matters)? In particular is either swap partition "linked" in some way to my current ubuntu installation or does it just use whatever swap partition is available? Since one of the swap partitions available (the old one) is the size I want could I just delete the smaller swap partition (the new one) or would that cause problems?

---

### Post by Double.J on 2012-01-21
Hi there the swap isn't really a problem - if you're still in gparted on your install - right click your swap partitions - if they're being used the option will be "swapoff" if not it'll be "swapon" Hope it helps!

If both are in use, or you already swapoff'd and can't remember type this into the terminal
```

gedit /etc/fstab

```

in the descrition (the bit after the #) it will say on which partition swap was on during install

All the best

Gnu

---

### Post by peterson43 on 2012-01-21
> **gnu/mirow said:**
> Hi there the swap isn't really a problem - if you're still in gparted on your install - right click your swap partitions - if they're being used the option will be "swapoff" if not it'll be "swapon" Hope it helps!

If both are in use, or you already swapoff'd and can't remember type this into the terminal
```

gedit /etc/fstab

```

in the descrition (the bit after the #) it will say on which partition swap was on during install

All the best

Gnu

Thanks for the help. From gparted it appears that the 6GB swap is not being used and the 3GB one is. Thus, I'll assume that its okay to delete the 6GB swap partition. 

Also, I looked at the /etc/fstab file. It reads as follows. 

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=699467bf-821b-4768-a15a-718fdf93670c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=3e38130f-cab6-4c67-a1c6-05e56e0287d0 none            swap    sw              0       0

```

From this I gather that my new ubuntu partition is the sda8 and my new swap partition that is being used is the sda9 (this is what I thought from looking at gparted as well). The one thing that concerns me is the part of the fstab file that reads "errors=remount-ro" under the <options> part of the table. Does this mean anything or is this normal?

---

### Post by Double.J on 2012-01-21
From what I can see, you are quite right in your assumptions from what I can see :)

those options are completely normal for your root partition, what it means is - should there be an error with the filesystem, attempt to remount as read only at start up. This is a good thing :) usually it will just follow the defualts and mount as writable automatically :)

While you are partitioning, it may be of interest to you to create a seperate EXT4 formated partition that you could then use as a seperate /home partition - if you are keeping all your personal's on the windows install this isn't that important, but it can be useful should you have to reinstall and you have things in your /home?

---

### Post by peterson43 on 2012-01-21
> **gnu/mirow said:**
> 
While you are partitioning, it may be of interest to you to create a seperate EXT4 formated partition that you could then use as a seperate /home partition - if you are keeping all your personal's on the windows install this isn't that important, but it can be useful should you have to reinstall and you have things in your /home?

If I create a seperate EXT4 partition for my /home partition how do I move my current /home directory to that partition?

---

### Post by oldfred on 2012-01-21
Just a few more choices. Are you using Windows a fair amount. If so it may be better to create a shared NTFS partition for any data that you may want from both systems (cannot be /home). I still have my Firefox and Thunderbird profiles in a NTFS partition so I have the same bookmarks & email. I do not boot XP much anymore but have not moved my data. 

I always suggest making the c: drive partition in Linux as read only to avoid accidentally moving or deleting essential Windows files. Linux shows all the hidden files that Windows protects (hides) from you. Good for when you have to repair Windows from Linux, bad if you mess something up.

I read all three, but they really are the same. You create a new partition with Linux format. Copy all files including hidden files, folders with permissions & ownership from current home to new home. Change fstab to use new home as home.
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by peterson43 on 2012-01-21
Okay, I ran a livecd session and used gparted to delete the old partitions and resize the new ones. Everything seemed to work fine, but when I tried to reboot the computer nothing would load - it wouldn't even get to the grub menu. I've heard that this is possible when you mess with the partitions, but I don't remember how to fix it (I think it has to do with editing the /etc/fstab file but I don't know what to do). 

The new ubuntu partition and swap partition were sda8 and sda9, but they are now sda5 and sda6. Does this renaming of partitions have something to do with my problem?

---

### Post by peterson43 on 2012-01-21
I went back in with a livecd session and looked at the /etc/fstab file. It looks like

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=699467bf-821b-4768-a15a-718fdf93670c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=3e38130f-cab6-4c67-a1c6-05e56e0287d0 none            swap    sw              0       0
```

which seems to be the same as it was before. I see that the files are listed as /sda8 and /sda9, but this appears to be commented out so that changing it shouldn't really do anything.

I also used gparted to examine the partition again (see the attached picture). From this, it looks like the UUID for the ext4 partition hasn't changed. I don't know how to find the UUID for the swap partition to match what is in the fstab file. 

Any help is much appreciated.

---

### Post by oldfred on 2012-01-21
You can see UUIDs with this:

```
sudo blkid
```

I have not seen it automatically renumber partitions? But both grub2 & fstab normally use UUIDs, so partition numbers do not matter as much.

If still not getting grub menu:

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

---

### Post by peterson43 on 2012-01-21
Just to give some more information. When, I try to turn on my computer I get the following message on my screen. 

```

error: no such partition
grub rescue>

```

From the Grub2 documentation I found [here]("https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting") it appears that maybe I could fix things from this grub rescue prompt. However, I'm a bit hesitant to do things this way since I fear I could really screw things up. For instance, the first line of the instructions says to enter 
```

set prefix=(hdX,Y)/boot/grub
```
but I'm not entirely sure what to put for "hdX" and "Y". From the comments I think it should be "hd0" and "5" but I don't know how to tell for sure. 

Also, if I try to do things from the grub rescue command will my dual boot still work correctly. That is, will grub still recognize that I can also start a Windows session? 

I'm currently downloading the boot-repair tool, so maybe that will be an easier fix. But it's taking like an hour to download (I have a slow internet connection) so I thought maybe there would be a faster way.

---

### Post by peterson43 on 2012-01-21
Okay, I'm impatient so I tried using the grub repair commands. Following the instructions I linked to previously I was able to start grub successfully and log in to my ubuntu session. However, this didn't fix anything since when I restarted the computer the grub repair> prompt came up again. 

One thing I noticed in going through the instructions. On step 6 I was supposed to type 
```

ls /boot
```
at the grub> prompt and I was supposed to check for a "vmlinuz" and a "initrd.img" entry. I found two of each so I'm not sure if that's a problem or if that's normal. 

Anyway, I'm downloading the boot-repair tool now and I'll probably try that next.

---

### Post by peterson43 on 2012-01-21
It appears that the boot-repair app did indeed repair the boot. Rather quick and painless too. I should note that for others with a slow internet like me, it's way faster to install the boot-repair app directly in Ubuntu rather than make an .iso image on a CD. Of course if you can't get to Ubuntu in the first place this is a problem, but thankfully using the grub repair commands I noted above I was able to log into Ubuntu. 

Thanks everyone for your help!

---

### Post by Double.J on 2012-01-21
Glad it's all working for you again :)

---

