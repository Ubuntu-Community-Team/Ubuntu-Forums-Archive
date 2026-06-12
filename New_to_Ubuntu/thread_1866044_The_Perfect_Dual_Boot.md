---
title: "The Perfect Dual Boot"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by djk21108 on 2011-10-20
Hello everyone. I want to install 11.10 onto my Windows 7 machine from a live cd.

What's the best tutorial that shows you how to partition everything and set up GRUB perfectly so that I have no problems?

I would prefer if /home were on a different partition.

---

### Post by wolfen69 on 2011-10-20
[http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu)

---

### Post by BlinkinCat on 2011-10-20
Hi,

You could have a look at this too -

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2011-10-20
These are good:


Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Windows 7 almost always has used all 4 primary partitons.
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Supergoo on 2011-10-21
If you pick install from the LiveCD it will walk you through the install and it will even do the resizing of the partition. Its very simple and easy to understand.



supergoo

---

### Post by djk21108 on 2011-10-22
Is it best to make a new partition for home as I'm installing Ubuntu?

I don't understand how you designate that a partition is just for /home?

Also, I have 6GB ram, how much swap should I have?

Thank you so much!

---

### Post by d4m1r on 2011-10-22
> **djk21108 said:**
> Is it best to make a new partition for home as I'm installing Ubuntu?

I don't understand how you designate that a partition is just for /home?

Also, I have 6GB ram, how much swap should I have?

Thank you so much!


1)home directory is automatically created during install so not sure what you are asking here? I'd specify just / as the default directory during install so home would just be /home

2)6GB is more than plenty, my advice is to not have a swap file at all. Depending on your RAM specs and HDD specs, chances are the RAM is much faster so there is no need to be caching anything on the HDD....I have 8GB and I do some serious multitasking but Ubuntu has never even gotten past 1GB of usage, pretty amazing imho but I'll save that for another day :P

---

### Post by LinuxFan999 on 2011-10-22
> **djk21108 said:**
> Is it best to make a new partition for home as I'm installing Ubuntu?
 
I don't understand how you designate that a partition is just for /home?
 
Also, I have 6GB ram, how much swap should I have?
 
Thank you so much!
It is a good idea to make a separate partition for /home.
when creating the partitions (with the manual partitioner option), you set the home partition by setting the mount point as /home.
 
You should have 6 or 12 Gigabytes as the size of the swap partition.
 
Remember to create 4 partitions in this order, /boot, /, /home, swap.
Make sure the home partition is the largest partition.

---

### Post by Mark Phelps on 2011-10-23
Do NOT, repeat NOT, use the Ubuntu installer to shrink the Win7 OS partition.  Doing so is asking for problems as it sometimes corrupts the Win7 OS filesystem, rendering it unbootable.

Oldfred gave you some excellent advice regarding HOW to do what you want to do.  You need to follow that advice, not listen to others with shortcuts that could corrupt your filesystems.

Also, follow the advice to make a Win7 Repair CD.  You will need it if your Win7 loader or partition get corrupted.

---

### Post by drillerccg on 2011-10-23
I thought installing Ubuntu on a system with Windows 7n a lready installed was the way to go. I followed this last year and everything works perfect

[http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/](http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/)

---

