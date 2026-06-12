---
title: "Manual partition"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by GregoryPitts on 2008-05-28
I am not a new Linux user, but I have never manually partitioned my hard drive when installing and I do not want to mess anything up. I haven't been able to find step by step instructions on how to partition correctly so that I have the shared fat32 space for both Vista and Ubuntu. I basically want to share music and homework between the two. Can someone point me to a tutorial, or write one? Sorry if this topic is in the forums already, I am sure it is but I haven't found it. A link to another thread would be fine too. Thanks.

- Greg

---

### Post by Mark_in_Hollywood on 2008-05-28
I hope this helps:

SuperGrub LiveCD

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and

GParted LiveCD

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

however if you mean you want to manually set the CHS or somesuch, I cannot give you help in that area.

---

### Post by GregoryPitts on 2008-05-28
I was thinking about manually partitioning it during install. Are you are recommending I use the guided partition in my install, and then use this software to manipulate the partitions after the install is complete?

---

### Post by indytim on 2008-05-28
I would recommend that you get a copy of GParted Live.  Burn and boot to it.  Pre-configure your partitions there and note the designated partitions for "/", swap and others (like "/home").  Start the install and when it comes to the partition section, use the manual partition option.  This way, you minimize surprises down the road with the install.

IndyTim

---

### Post by bsharp on 2008-05-28
Doing the guided during install and then going back to change the partitions is a waste of time.  I have installed using the alternate cd for the past few releases (I personally believe it's faster) but if I remember correctly if you choose the manual partition than it starts gparted so you can choose your setup before it goes on with the install.

---

### Post by bodhi.zazen on 2008-05-28
IMO the best way to partition your hard drive is with the Ubuntu Live CD.

gparted is on the live CD and, although it is a very nice tool, there is no need to download the gparted live CD.

Before you partition your Hard drive, defragement your windows partitions and back up your data.

I advise you set up your partitions before you run the installer, then during the install, select manual partitioning and you will then give each partition a mount point.

See : [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

During the install you then select a partition, say /dev/sda2 and mount it somewhere like /media/data (call it what you will).

See also :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

