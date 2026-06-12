---
title: "why my installation is so slow"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by aoken1 on 2013-05-22
Hello,

I wonder why my Ubuntu installation is so slow,I installed Ubuntu 64 bit latest version using Virtual Box
since I'm using Windows 8 which doesn't run alongside with Ubuntu (as far as I know):

my configuration installation configuration:

3.5 GB of memory
128 MB for graphics card
enabled 3D acceleration
installed guest tools

my laptop:
[http://www.dell.com/us/p/inspiron-15r-se-7520/pd](http://www.dell.com/us/p/inspiron-15r-se-7520/pd)

i7 version

p.s if I downgraded to Windows 7,do you think my problem would be solved?

---

### Post by HermanAB on 2013-05-22
The problem is that you are running Ubuntu instead of Xubuntu.

[http://www.aeronetworks.ca/2013/05/virtualbox-ubuntu.html](http://www.aeronetworks.ca/2013/05/virtualbox-ubuntu.html)

---

### Post by KoRnKloWn on 2013-05-22
Ubuntu should be able to run alongside Windows 8 as far as I know, and you shouldn't need to disable secureboot to do it. However keep in mind that resizing the Windows 8 partition can actually break it's recovery partition, and quite honestly, many other things can also break it's recovery partition, so if you haven't already then create a recovery disk, I reccommend getting a 32GB flash drive, then either use the Windows 8 recovery media creator or Dell should also have their own. Also keep in mind that when you create recovery media on Windows 8 it only allows 1 creation, and failing will block you from another try (you can reset it in the registry, but it's not easy). I know this because I work in Geek Squad at Best Buy and deal with Windows 8 on a daily basis, and every day I'm so happy to come home to Ubuntu :D

Once you have a recovery disk label it and put it in a SAFE location, then you can partition the disk safely, and you shouldn't have any problem installing Ubuntu alongside Windows 8, assuming you're installing the latest version it should be secureboot ready, so no need to disable that in the UEFI.

And to answer your question about the virtual box running slow, with those specs it's most likely that Virtual Box isn't yet Windows 8 ready, however if you are running Ubuntu pre-13.04 with Unity, it was pretty clunky before 13.04, so that could have to do with it also. But if you are running 13.04, or you aren't even running Unity, then my money is on Virtual Box not playing well with Windows 8, not necessarily a Windows problem (never thought I'd say that :P), keep in mind that as soon as Oracle bought Sun, all their software including Virtual Box got hit hard performance-wise. You can check out VMWare Player, it's free-ware, but works much better, and to be quite honest open source means basically nothing when it's Oracle.

---

### Post by squakie on 2013-05-22
This is a box running on windows 8 and Ubuntu in the VM unique problem.  I ran into the same thing and did a search on the net that turned up some suggestions.  One had something to do with the video mode - changing it did help.  Without that my Ubuntu in a VM running in windows 8 ran unbelievably slow - I'm talking there are 100 year old turtles that are faster.  Do the net search and you should find it.

---

### Post by sandyd on 2013-05-22
Have you tried using Hyper-V?

Hasnt been slow in Hyper-V for me

---

