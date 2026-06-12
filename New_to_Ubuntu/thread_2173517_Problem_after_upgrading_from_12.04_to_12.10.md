---
title: "Problem after upgrading from 12.04 to 12.10"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by Dennis Primm on 2013-09-10
Dear Ubuntu Forums,

I am an inexperienced Ubuntu user.  I dual boot with Windows Vista Home Premium (32-bit) and Ubuntu 12.04 (64-bit as my computer is an AMD 64 bit machine).  Everything always worked OK until I did the following...
 
I updated my Ubuntu 12.04 until there were not any other updates available and then decided to upgrade my system from 12.04 to 12.10.  I was asked to restart the system for the upgrade to take effect.  I restarted it and it looked like things were going well and then a screen popped up stating that (and this went so fast that the information I'm about to give you is the best I can describe) the /tmp was something and there was something about mounting and to press "S" to skip.  I didn't press anything and then the screen disappeared and the computer continued to do its thing but it never booted into Ubuntu.  

Luckily I use Macrium Reflect in Windows and I can always revert to Ubuntu 12.04, but I would like to upgrade to 12.10 if possible and then go on to 13.04.

Can anyone give me any help with this limited description?  I'd sure appreciate your help.

Thank you,

Dennis :p

---

### Post by MrAli on 2013-09-10
i think best way for upgrading ubuntu is downloading ubuntu 13.04 and then installing it. upgrading from 12.04 to 12.10 and then to 13.04 and (maybe) to 13.10 is not the best way.

---

### Post by Dennis Primm on 2013-09-12
I have downloaded Ubuntu 13.04 and tried to install it alongside Windows Vista, but have run into another problem.  I have one internal HDD in my computer, which I have two partitions on, the C:\ is for Windows Vista and the D:\ is for Ubuntu.  When I run the .iso file from DVD it shows two partitions (I guess that is what they are) and they have approximately the same space on each of them, it states to drag the divider to allocate disk space for the installation, but it doesn't show which partition space the Ubuntu installation is going to be made on.  It also asks me what mount point I want to use and I don't know how to answer that.  Can you help?  I'd appreciate it!!!

---

### Post by whitesmith on 2013-09-12
> **Dennis Primm said:**
> I have one internal HDD in my computer, which I have two partitions on, the C:\ is for Windows Vista and the D:\ is for Ubuntu.[snip] Linux does not partition drives by letter. This is a Windows thing.

Seriously, I would remain on 12.04 LTS if I were you. Long term support benefits users with limited experience because, among other things, it is more stable and less often updated. This is a benefit, not a drawback.

But my observation does not solve your problem. I would recommend that you reinstall Ubuntu (preferably 12.04 LTS) and pick a side-by-side installation. Give Ubuntu a partition (drive letter, in Windows-speak) of 60 GB, more if you can spare it. It should co-exist peacefully with that other OS. The mount point should be / which you can select from the drop down.

---

### Post by Mark Phelps on 2013-09-13
If Ubuntu is really on your "D:" drive, that means you installed it using Wubi -- and upgrading Wubi from one Ubuntu release to another is fraught with problems.  Also, Wubi has been dropped as of Ubuntu 13.04 -- so there is no future path for it.

If you intend to use Ubuntu year after year, a better solution is to install to its own partition -- one formatted for Linux.

---

