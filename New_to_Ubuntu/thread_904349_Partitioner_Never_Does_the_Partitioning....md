---
title: "Partitioner Never Does the Partitioning..."
date: 2008-08-29
forum: New to Ubuntu
---

### Post by henryrhenryr on 2008-08-29
I'm trying to install Dapper on a reasonable old Laptop.  I'm using the Xubuntu Alternate CD as RAM only 96MB.  The CD drive is broken so I'm using an external CDROM drive by USB and a nifty little thing to boot using that.  All happy and good until...

The partitioner - I set up the partitions, select OK Partition, then confirm yes to get it started.

I get a blank screen for about a minute then it loads the partitioner again.

I tried this a few times, changing the partitions around to see if that was the problem.

Eventually I aborted and tried again.  Mysteriously, the partitioner seems to have done something (the table has changed from the original) but when I try to continue it still returns back to the partitioner.

I have used the CD twice without a problem on other machines.

Anyone have any clues?  I am going to try CentOS now which has a different partitioner but I would prefer Ubuntu on this one!

Thanks in advance.

Henry

---

### Post by eggdeng on 2008-08-29
The version of gparted bundled with Dapper is buggy. Download the gparted live cd from [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") and do your partitioning before you start the install.

---

### Post by kellemes on 2008-08-29
> **henryrhenryr said:**
> I am going to try CentOS now which has a different partitioner but I would prefer Ubuntu on this one!

If you partitioned using Centos you can simply install Ubuntu based on the partition scheme you setup.

---

### Post by forger on 2008-08-29
Um, why not try Ubuntu/Xubuntu 8.04.1?
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
[http://cdimage.ubuntu.com/xubuntu/releases/hardy/release/](http://cdimage.ubuntu.com/xubuntu/releases/hardy/release/)

---

### Post by maybeway36 on 2008-08-29
I would do the command-line install of Ubuntu 8.04 then add xorg (and fluxbox or similar.)

---

### Post by henryrhenryr on 2008-08-29
> **eggdeng said:**
> The version of gparted bundled with Dapper is buggy. Download the gparted live cd from [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") and do your partitioning before you start the install.

That would explain it! For once it's not me...

I managed to partition using the CentOS cd but then something else went wrong.  Uggh.  Messy.

I used Dapper just because I have a working CD and the computer is v. old so it seemed like a safer bet given specs...

Thanks for help!

---

### Post by kellemes on 2008-08-29
> **henryrhenryr said:**
> That would explain it! For once it's not me... 
Yes it is.. you should have known! :popcorn:
Just joking..

Anyway, glad you got this issue fixed.

---

### Post by forger on 2008-08-30
> **henryrhenryr said:**
> I used Dapper just because I have a working CD and the computer is v. old so it seemed like a safer bet given specs...
You shouldn't look at it that way, but: the newer the release, the better chance you have for it to support your hardware

---

### Post by hyper_ch on 2008-08-30
hardy won't run on 96 mb ram

---

### Post by forger on 2008-08-30
[ I bet the mini iso can :) [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) ]

---

### Post by hyper_ch on 2008-08-31
not really... the mini iso will get all the stuff through the net... you can run the mini iso but then hardy won't run

> 
System Requirements

Ubuntu is available for PC, 64-Bit PC and Intel based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space.


---

### Post by henryjm206 on 2008-08-31
HI HenryrHenryr

henry:)

---

