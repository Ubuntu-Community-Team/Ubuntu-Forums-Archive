---
title: "How to setup a dual boot?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by linux_newf on 2008-05-03
Hey guys, my father actually wants to checkout linux after i shown him Ubuntu on my laptop lastnight. (Thanks to the wireless connection!)

Anyhow, i have an older computer here that has XP. I was looking over some docs on partitions and it seems its pretty self explanatory once you get to the install screen. 

How much memory do i need? I was reading some info on Xbuntu and it required at least 1.5Gb, is this correct?

What amount should i use to have a good working OS?

Any other info or tips would be great.

---

### Post by mtonsbeek on 2008-05-03
I would think that if it could run XP, it should be able to run Ubuntu.

---

### Post by phoenix_abhi on 2008-05-03
> **linux_newf said:**
> Hey guys, my father actually wants to checkout linux after i shown him Ubuntu on my laptop lastnight. (Thanks to the wireless connection!)

Anyhow, i have an older computer here that has XP. I was looking over some docs on partitions and it seems its pretty self explanatory once you get to the install screen. 

How much memory do i need? I was reading some info on Xbuntu and it required at least 1.5Gb, is this correct?

What amount should i use to have a good working OS?

Any other info or tips would be great.

If ur XP working fine then forget about all other issues, Ubuntu will run faster. Basic ram req is 256 and 512 n above is recco

---

### Post by drsox1899 on 2008-05-03
Ubuntu needs about 512mb to run well (relative to what is not clear!), but I have 7.10 running on an old Toshiba laptop with 384mb.

If you have less then look at Xubuntu (uses a less resource intensive Window Manager than Ubu). Kubuntu is in the middle.

If it runs Xp, then it will run better on Ubuntu.

All can be tried out with live CDs.  

What spec do you have ?

You need minimum 4GB for the / partition, 2xMemory for swap and as much as you want for the /home partition.

Luck

---

### Post by linux_newf on 2008-05-03
> **drsox1899 said:**
> Ubuntu needs about 512mb to run well (relative to what is not clear!), but I have 7.10 running on an old Toshiba laptop with 384mb.

If you have less then look at Xubuntu (uses a less resource intensive Window Manager than Ubu). Kubuntu is in the middle.

If it runs Xp, then it will run better on Ubuntu.

All can be tried out with live CDs.  

What spec do you have ?

You need minimum 4GB for the / partition, 2xMemory for swap and as much as you want for the /home partition.

Luck

XP runs on it but its pretty sluggish.

It has 386mb - i think it is, i added some ram from another PC - and 1.7mhz celeron processor.

Its actually my first computer its about 6 or 7 years old. :)

Are the repositories much the same for Xbuntu? IE the flash plugins and stuff easy to install?

---

### Post by unbuntued on 2008-05-03
> **linux_newf said:**
> XP runs on it but its pretty sluggish.

It has 386mb - i think it is, i added some ram from another PC - and 1.7mhz celeron processor.

Its actually my first computer its about 6 or 7 years old. :)

Are the repositories much the same for Xbuntu? IE the flash plugins and stuff easy to install?

The difference between Xubuntu and Ubuntu is just the desktop environment used (Ubuntu uses GNOME, Xubuntu uses Xfce), the software is the same. So you'll find what you need in the repository similarly to Ubuntu.

---

### Post by linux_newf on 2008-05-03
Well i just tried to install Xbuntu but when i used the "guided" options it came back telling me disk size was to small.

I have about 21Gb of free spcae but i only want to use 8 so i assume i have to use the manual conf option.

What file system and mount point do i use? Is it "primary or logical"?

---

### Post by linux_newf on 2008-05-03
> **linux_newf said:**
> Well i just tried to install Xbuntu but when i used the "guided" options it came back telling me disk size was to small.

I have about 21Gb of free spcae but i only want to use 8 so i assume i have to use the manual conf option.

What file system and mount point do i use? Is it "primary or logical"?

Any suggestions?

---

### Post by Serpentinsek on 2008-05-03
> **linux_newf said:**
> Well i just tried to install Xbuntu but when i used the "guided" options it came back telling me disk size was to small.

I have about 21Gb of free spcae but i only want to use 8 so i assume i have to use the manual conf option.

What file system and mount point do i use? Is it "primary or logical"?

First things first...

If your winXP is using the entire disk and if you want to use manual partitioning , you will have to use gParted (you can run it via live CD) to shrink your existing NTFS (I presume you use NTFS file system for XP) partition to free some space and create a ext3 partition for your Xubuntu install and swap partition 

Than you go for the manual config and click edit partition and under mount information type in "/" this will signal your installer that this is your root partition for your installer.

Have fun installing :)

---

### Post by linux_newf on 2008-05-03
> **Serpentinsek said:**
> First things first...

If your winXP is using the entire disk and if you want to use manual partitioning , you will have to use gParted (you can run it via live CD) to shrink your existing NTFS (I presume you use NTFS file system for XP) partition to free some space and create a ext3 partition for your Xubuntu install and swap partition 

Than you go for the manual config and click edit partition and under mount information type in "/" this will signal your installer that this is your root partition for your installer.

Have fun installing :)

Well suddenly this doesn't seem simple.. :(

I'm refering to the manual option on the install window. It asks for a number of things like mount, filesystem and if it is primary or logical.

XP is the only OS on the drive it has 21Gb of free space.

---

### Post by Serpentinsek on 2008-05-03
> Well suddenly this doesn't seem simple..
Ok let's try one more time.

> XP is the only OS on the drive it has 21Gb of free space.
Fine. You see this is free space on a single partition that is used by your XP. Do not mix up this with free space on the device itself ;)

> I'm refering to the manual option on the install window. It asks for a number of things like mount, filesystem and if it is primary or logical.
If you chose to do the manual config for your partitioning, you will have to run gParted first.

Run it via command line 
```
$ gparted
```

In gParted you will have to create 2 new partitions besides your existing one that is used to run XP
- create one partition with file system ext3 (make it 3-4 GB or more)
- create the second partition formated to swap (usually twice the size of your RAM)

Remember this will shrink your NTFS partition! Don't try to delete it! gParted can be dangerous so when you will install your xubuntu you will have to run it with a sudo prefix via command line

Than go to your installer, chose manual config for partitioning. Click on your previously created ext3 partition and click "edit partition" 
and under "mount", type in "/" 

Your installer will now know what partition to use for your Xubuntu install.

For extra help with gParted read this: [http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

---

### Post by linux_newf on 2008-05-03
I need 2 more partitions!? Its busy now setting up a 10GB partition. 

Gparted was under partition manager.

I'll get back to this thread when Gparted is finished.

---

### Post by Serpentinsek on 2008-05-03
> **linux_newf said:**
> I need 2 more partitions!? Its busy now setting up a 10GB partition. 


Yes but swap is only twice the size of your RAM ;)
If you want to know more about partitioning for linux you have a complete HOWTO right over here [http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)

---

### Post by linux_newf on 2008-05-03
> **Serpentinsek said:**
> Yes but swap is only twice the size of your RAM ;)
If you want to know more about partitioning for linux you have a complete HOWTO right over here [http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)

Ok thanks dude, you have to understand i really don't know what swap is. :)

I'll get it figured out, thanks for the link.

---

### Post by Serpentinsek on 2008-05-03
> **linux_newf said:**
> Ok thanks dude, you have to understand i really don't know what swap is. :)

Swap definition:
[http://people.debian.org/~psg/ddg/node81.html](http://people.debian.org/~psg/ddg/node81.html)

---

### Post by franzrebs on 2008-05-06
Hi, I'm currently running XP and it's doing fine, fast enough for me. I have 224mb RAM, and a 1.7GHz processor. I want to install Ubuntu/Xubuntu alongside XP (dual boot).Do you think Ubuntu 8.04 would run as fast?

Another question: Is the Xubuntu installation as easy as Ubuntu? I read your previous posts and I'm confused about the partitioning stuff.

Hope you guys can help me because I'm very eager to try out Ubuntu/Xubuntu on my PC.

---

### Post by phoenix_abhi on 2008-05-06
> **franzrebs said:**
> Hi, I'm currently running XP and it's doing fine, fast enough for me. I have 224mb RAM, and a 1.7GHz processor. I want to install Ubuntu/Xubuntu alongside XP (dual boot).Do you think Ubuntu 8.04 would run as fast?

Another question: Is the Xubuntu installation as easy as Ubuntu? I read your previous posts and I'm confused about the partitioning stuff.

Hope you guys can help me because I'm very eager to try out Ubuntu/Xubuntu on my PC.

The installation partitioning and all other methods are same, even applications are works like twins. The repositories also same. The main difference is Ubuntu uses GNOME DE tech while Xubuntu a mixture of KDE and GNOME DE (XFCE)but promoted as Fast compare to others. If u  know how 2 in stall UBUNTU do the same for Xubuntu also

Believe me Ubuntu runs 40 % more faster than any of the MS OS

---

### Post by franzrebs on 2008-05-07
> **phoenix_abhi said:**
> The installation partitioning and all other methods are same, even applications are works like twins. The repositories also same. The main difference is Ubuntu uses GNOME DE tech while Xubuntu a mixture of KDE and GNOME DE (XFCE)but promoted as Fast compare to others. If u  know how 2 in stall UBUNTU do the same for Xubuntu also

Believe me Ubuntu runs 40 % more faster than any of the MS OS
Thanks, I'll have to make do with Xubuntu until I can upgrade my RAM. By the way, can I install Xubuntu while I only have one partition (30% currently used by XP)? Will the partitioning task occur during installation or do I have to partition before installing Xubuntu? Which do you recommend?

---

### Post by phoenix_abhi on 2008-05-07
> **franzrebs said:**
> Thanks, I'll have to make do with Xubuntu until I can upgrade my RAM. By the way, can I install Xubuntu while I only have one partition (30% currently used by XP)? Will the partitioning task occur during installation or do I have to partition before installing Xubuntu? Which do you recommend?

u can find several partition articles in this forum. use manual method. 2 x ram as logial for swap, 10 or 15 gb for root and 10 gb for home is an ideal partition

---

