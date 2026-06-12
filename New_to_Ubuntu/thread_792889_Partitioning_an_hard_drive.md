---
title: "Partitioning an hard drive"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by silverjohnlong on 2008-05-13
Being a very new convert to the wonderful world of Linux and Ubuntu 8.4 in paticular. I would like to view other Linux distro's but sadly don't have much of an idea how to partition an hard drive. Can anyone recommend a very easy (child like) tutorial that i could follow please?

---

### Post by TeoBigusGeekus on 2008-05-13
If the hard drive is different than the one you have Ubuntu on, then install gparted
```
sudo apt-get install gparted
```
and then go to system->administration->partition editor.

If the hard drive you want to partition is the one you have Ubuntu on, then you'd better download gparted live cd,
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
boot with it and perform your preferred partitioning. You could do this with Ubuntu live cd, but I've read somewhere than gparted from live cd is a bit buggy.

EDIT: Before you do anything, do a backup of your crucial data!

---

### Post by aeiah on 2008-05-13
you'll want gparted if you havent got it installed already
```
sudo apt-get update
sudo apt-get install gparted
```

it'll be in your administration section of your menu.

you'll want to create a new partition or two. you can format them as well, although you'll have the chance to do that when you're installing your 2nd linux distribution anyway. if you choose one partition, then everything will go in there. if you choose two, you can select one as home. its possible to point a new install of linux to your existing home partition on your normal linux OS, although i find it a bit messy. you dont need to create a new swap or anything.

most linux distros will recognise your existing installation and will ammend add an entry onto your grub. backing up grub may be a good idea though

---

### Post by tech9 on 2008-05-13
> **TeoBigusGeekus said:**
> If the hard drive is different than the one you have Ubuntu on, then install gparted
```
sudo apt-get install gparted
```and then go to system->administration->partition editor.

If the hard drive you want to partition is the one you have Ubuntu on, then you'd better download gparted live cd,
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
boot with it and perform your preferred partitioning. You could do this with Ubuntu live cd, but I've read somewhere than gparted from live cd is a bit buggy.

EDIT: Before you do anything, do a backup of your crucial data!

+ 1

---

### Post by silverjohnlong on 2008-05-13
I already have Ubuntu 8.04 installed courtesy of a friend. But is it possible to run another Linux OS and let Ubuntu set the partition for new OS during installation?

---

### Post by tech9 on 2008-05-13
> **silverjohnlong said:**
> I already have Ubuntu 8.04 installed courtesy of a friend. But is it possible to run another Linux OS and let Ubuntu set the partition for new OS during installation?

you can always run another OS via live CD...

---

### Post by NR1224 on 2008-05-13
if ubuntu is installed first, the new os will "take over" grub(the boot loader). This shouldnt present much of a problem, just make sure the new OS uses grub, as it is much more supported than others, such as LILO. Also, if there are any problems, you can manually edit grub yourself

---

### Post by silverjohnlong on 2008-05-13
Have got the "live" GParted CD and when i booted up from it took a screen shot but it's in the root or something similar folder and i can't find it so as to show you. Ubuntu is currently using the whole hard drive.

---

