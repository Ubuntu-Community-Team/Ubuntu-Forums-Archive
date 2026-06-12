---
title: "Dual Boot 3 windows partitions"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by RoboGuitarist on 2012-11-05
Hello everyone,

I am completely new to linux, and thus far my experience with linux has been booting ubuntu 12.04 from a flash drive to play around with. I would eventually like to dual boot Ubuntu 12.04 alongside windows 7.

I have a Sony Vaio E series  SVE15115FXS model laptop. The computer comes with 3 partitions loaded:
1. Recovery Partition
2. System Reserved Partition
3. C: drive

  I have successfully shrunk my C: drive, and now have 182 GB of unallocated space. So this gives me 4 partitions if I am correct.My partition style is MBR, so this is my max. My question is: does it make sense to make both the swap and root partitions logical? and will this allow me to use the free space partition to successfully install Ubuntu with both a swap and root partition? In addition, when going through the steps of dividing the partition into swap and root in the installer (I did not execute the installation, just a practice run), it allows me to make the swap logical, but when I attempt to allocate the remaining space to root, it does not even give me an option to choose between logical and primary. Is this a problem?

I am in no hurry to actually commit to a dual boot right away, I will probably continue to play around with the bootable flash drive for a while longer. I would just like to hear any concerns or input you guys have on my situation. If there are any known problems with my particular computer specs, please feel free to let me know that as well. Thanks for your time guys, I hope this was a coherent post.

---

### Post by oldfred on 2012-11-05
Welcome to the forums.

Be sure to have good backups and make a Windows repairCD or USB.

If it is unallocated it is not yet a partition. But with 3 used you have to make the 4th the extended partition and put all additional partitions in the extended.

If you use the auto install it will just make a / & swap in the unallocated. If new to Ubuntu that is an ok configuration.

Many of use like more partitions. /home, data, NTFS shared data are all added choices. 
Often the /home is good to have so if you want to reinstall all your user settings are in /home and that simplifies the reinstall. But you still should have backups. 

The NTFS shared helps avoid issues with Windows. The Linux NTFS driver exposes all the Windows files including the normally hidden ones. Often that can lead to accidents. Better to set the Windows system partition as read-only and have data separate.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by RoboGuitarist on 2012-11-05
Thank you for reminding me to back up my data and create a Repair CD, I will certainly do so before I dual boot.
I think I will gun for at least getting a home partition in addition to / and swap. But its good to know that I can opt for the auto-install if I have to.

According to the top answer on this site: [http://social.technet.microsoft.com/Forums/en-US/w7itproinstall/thread/65bb4458-edb9-43f0-8313-bcadb1a8432f/](http://social.technet.microsoft.com/Forums/en-US/w7itproinstall/thread/65bb4458-edb9-43f0-8313-bcadb1a8432f/)

 the windows 7 disk manager makes the 4th partition an extended partition by default. Is that a viable option, or should I search for another way to create the extended partition? Thanks again.

---

### Post by oldfred on 2012-11-05
Do not use Windows to create partition. I have not seen anyone that has it work. And it normally converts your basic partitions to dynamic (or logical) which does not work with Ubuntu and does not even work with some of the Windows repair tools.

Use the Windows MMC to shrink Windows and reboot to make sure Windows has updated itself to its new size.
But then use gparted from the Ubuntu LiveCD or a gparted liveCD to create the extended and logical partitions you may want.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by RoboGuitarist on 2012-11-06
Thank you very much for your prompt responses, this should give me plenty to digest and figure out before I make the jump to dual boot.  One last question: After creating the extended partition,  and three logical partitions in GParted, do I then assign them their /,swamp, and home, functions in the "something else" ubuntu installer?

---

### Post by oldfred on 2012-11-06
Yes, you can use manual install or Something Else. All the auto installs just create root & swap.
If you have created partitions in advance you do have to keep track of which you want to use for / & /home. If assigned as swap it finds that automatically. I have lots of partitions and lost track of which was which and have installed to the wrong partition. One of the main reasons for good backup is user error. :)

---

### Post by RoboGuitarist on 2012-11-06
HaHa! I can definitely see where that would be the case. Thanks again for all of your help!

---

