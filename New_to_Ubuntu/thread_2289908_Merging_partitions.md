---
title: "Merging partitions"
date: 2015-08-08
forum: New to Ubuntu
---

### Post by Doug_Jones on 2015-08-08
I was given an older laptop that still works fine. It looks like there are already two versions of Ubuntu installed. I want to merge the partitions and then install a new version of Ubuntu. I also want to keep Windows and dual boot. Should I just delete sda 3-7 and then merge the partitions together? Anything else I might need to do?

Thanks!

---

### Post by roger_1960 on 2015-08-08
Hi

I would delete sda3 and sda4. This will leave empty space.  Do this when using gparted from a live session cd or usb (you can't delete a partition that you are running from - one that is mounted)

Then install your new distro alongside windows.  If its a ubuntu, the installer will give you the option to install into the empty space and it will create partitions for you.  For other distributions, follow their instructions.  (You may well have to create new partitions before installing.)

Don't forget to back up any data that you would not wish to lose (windows and ubuntu).  These things go wrong if you don't backup!

---

### Post by Topsiho on 2015-08-08
I think that deleting all partitions except sda1 and sda2 (the partitions with Windows) is a good idea. After that you have ***unallocated space of about 40 GiB***, that you can use for the Ubuntu install (advise: Ubuntu 14.04.3).
You can prepare the partitions before actually installing Ubuntu, or during the install, using GParted. Before you do this make a plan how you want to do this, just let Ubuntu use the unallocated space during the install (you don't get a separate /home partition for your personal files), or having a separate partition for /root (make it let's say 15 GiB), one partition for the /home (as large as possible), and one partition for swap (twice your RAM).
Easiest is to let Ubuntu do it's thing and see whether you like this or not.

Also be prepared for entering a strong password during the install, and other information, such as your name, and the computer name.
The password is the password you need when you make changes to the system (updating, installing, configuration and so on, using sudo). This prevents you using the system as root all the time.

Success!

Topsiho

---

### Post by mörgæs on 2015-08-08
If you let Buntu do the partitioning in the empty space it's recommended to choose 'something else' from the menu. There used to be a bug (I don't know if it's fixed) in the automatic installer which could make trouble for a dual boot. 

Seeing that your hard disk is 110 GiB I assume that the computer is semi-old. You could consider X/Lubuntu in stead of Ubuntu.

---

### Post by yancek on 2015-08-08
> Seeing that your hard disk is 110 GiB I assume that the computer is semi-old. You could consider X/Lubuntu in stead of Ubuntu. 		

Definitely something you should research before beginning.  Got to the site for Ubuntu/Lubuntu or any other Linux and you should be able to find minimum hardware requirements.  Compare that to the hardware you have before you begin.

There are a number of options you can use including leaving the partitions the way they are and installing to the current / partition and using other Linux partitions for /home and/or data storage.  I would suggest you use the manual installation method suggested above and you might read a few tutorials if this is new to you because if something goes wrong, I doubt you'll be able to boot whichever windows version you have as it undoubtedly is using the Ubuntu Grub bootloader.

---

