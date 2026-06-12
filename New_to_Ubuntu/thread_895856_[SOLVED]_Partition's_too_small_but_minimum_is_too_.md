---
title: "[SOLVED] Partition's too small but minimum is too big"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by t4l0 on 2008-08-20
Hey I just registered here because I couldnt find a thread with this problem.. I don't know if I should file a bug report either. But I installed ubuntu on Sun xVM Virtualbox, and it works great. But when I try to install it, it messes up at the partition area.

First I use Guided partitioning, which brings up this message.

[IMG]http://img228.imageshack.us/img228/1890/help1cp5.png[/IMG]

So I click "Go Back" which brings me to the partitions.

[IMG]http://img59.imageshack.us/img59/6268/help2ks8.png[/IMG]

So I try to edit the partition telling it to use 2028 mb, but it only allows 2000 at the most.. Ok, I guess I'll keep it with 2000, at least we're getting somewhere, right?

[IMG]http://img231.imageshack.us/img231/1508/help4xb7.png[/IMG]

Wrong, it says anything over the original 1990 mb is too large. So really, everything is as big as they get.

[IMG]http://img84.imageshack.us/img84/103/help3sc7.png[/IMG]

So, what do I do? I tried continuing the installation, but at 73% it says I'm out of hard disk space, on my original XP I still have about 25gb on my hard drive, too.

Any answers?

P.S. If it helps, my RAM is 760mb

---

### Post by LowSky on 2008-08-20
you need more space than 2 gigabytes
> Bare Minimum requirements
It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation. 

300 MHz x86 processor 
64 MB of system memory (RAM) 
At least 4 GB of disk space (for full installation and swap space) 
VGA graphics card capable of 640x480 resolution 
CD-ROM drive or network card 

EDIT: Your installing on a Virtual Box? You will need to increase the amount of space alloted to the VM

---

### Post by t4l0 on 2008-08-20
And how do I do that? Go back and edit my xVM profile thing that starts up ubuntu?

---

### Post by LowSky on 2008-08-20
I'm not really that smart on using Virtual Box, but your idea should work

I would use about 10GB for Ubuntu, and Swap should be double your alloted RAM

---

### Post by BGFG on 2008-08-20
What kind of disk did you create for it in Virtual Box and what size did you dedicate ? fixed size or dynamically expanding ? What is the host OS ?

---

### Post by Too Late on 2008-08-20
Go to File -> Virtual Disk Management and create a new virtual disk there. Then select your Ubuntu virtual machine, press Settings, and select Hard Disks from the left and change your disk (or add one).

Or just create a new virtual machine.

edit: Anyway, Ubuntu installation program doesn't seem to handle that situation very well...

---

### Post by t4l0 on 2008-08-20
> **BGFG said:**
> What kind of disk did you create for it in Virtual Box and what size did you dedicate ? fixed size or dynamically expanding ? What is the host OS ?

I believe I mounted the ISO with a CD/DVD rom file. I have about 320 base memory but I'm increasing it a little bit. So i think its fixed size. The host OS I believe is Windows XP

---

### Post by t4l0 on 2008-08-20
> **Too Late said:**
> Go to File -> Virtual Disk Management and create a new virtual disk there. Then select your Ubuntu virtual machine, press Settings, and select Hard Disks from the left and change your disk (or add one).

Or just create a new virtual machine.

Wow thanks I think that's exactly what I needed, I'm starting it up again now to see if everythings in working order. This time its at least a dynamically expanding one.

---

### Post by BGFG on 2008-08-20
Cool, 
Well my Host OS is ubuntu, and i have XP running in VB. Initially when i was creating the virtual disk for xp, i gave it 10 gigs and made it fixed size. Turns out i gave it too much space. If your Host OS is xp (the one that VB is installed in) and seeing as you have'nt successully installed ubuntu yet, you could delete the virtual disk, defrag XP (defraggler by Piriform) recreate the Ubuntu virtual Disk (.vdi) give it like 6-8 gigs if you have the space and try the installation again.

Good luck man.

Late post :) right on the money with dynamically expanding.

---

### Post by t4l0 on 2008-08-20
Thanks everyone for your help, I am installing it now, and it appears to be working with no problems. This is an awesome forum too, since I got answers in less than 5 minutes.

---

### Post by forger on 2008-08-20
I think you should report it as a bug, the installer should handle limitations better

---

