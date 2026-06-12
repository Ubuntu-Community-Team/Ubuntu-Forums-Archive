---
title: "Need help on dual boot"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by zoner on 2008-11-21
Okay, I am about to install Ubuntu but need a dual install with Vista.  I have copied the desk but need help on setting up the dual boot.  How do you set up the dual boot?  thanks.

---

### Post by jimmy the saint on 2008-11-21
what do you mean you copied the desk?

---

### Post by zoner on 2008-11-21
oops. copied the iso on the dvd.

---

### Post by nhasian on 2008-11-21
this guide will help you setup dual boot:

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by Twitch6000 on 2008-11-21
You could just use the wubi install >.>.

pop in your dvd and say install on windows and follow the instructions from there :).

---

### Post by lkraemer on 2008-11-21
Have a look at this site.  It is the best I have found.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Basically, if you have Windows XP, or Vista, and maybe a Recovery Partition, you can install Ubuntu and the linux-swap parition.  There
is a maximum of four Primary partitions on any Physical Hard drive. Your Windows and possibly a recovery partition will make up the first two.

So, if your install has allocated the complete Partition just for Windows, just boot the Ubuntu 8.10 LiveCD, and use Gparted to resize the partition.  I like to keep Wonders as small as possible, and give more to Ubuntu, as I know that after you use Ubuntu for 6-8 months you won't be booting Wonders.  After resizing Wonders, just make a linux-swap partition that is twice as large as your RAM, and make the remainder a ext3 partition for Ubuntu.  During the install, do a manual partition, and assign the mount point as / for the ext3 partition.

Zit Zot, Boot Ubuntu, and wonder why you kept Wonders as the first partition.  Another possibility is to install Ubuntu ONLY, then Install VirtualBox, and then install Windows XP in the Virtual Disk as am Image.  WOrks wonderful and you can copy the VDI to any computer and run XP in VirtualBox.

Just be sure to make a SUPERGRUB Disk in case you want to get Windows to boot again after installing Grub.

Either method works wonderful.  And once again, after you use Ubuntu, you won't go back.  Faster bootup and shutdown, easy upgrades, good support, good forums, and easy to use.

I am sticking with 8.04 LTS For a year or two, then upgrade to the next LTS version.....maybe....

lk

---

### Post by Miljet on 2008-11-21
A couple more pointers. Before you begin, run defrag on your Windows partition. Actually it is best to run it several times to move as much as possible to the front of the disk. Backup any important files before you change any partitions.Then, especially if you have Vista, use the partition tool in Windows to shrink the Windows partition. 
Put in the Livecd and go for it.

---

