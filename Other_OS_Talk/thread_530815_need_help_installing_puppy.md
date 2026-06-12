---
title: "need help installing puppy"
date: 2007-08-20
forum: Other OS Talk
---

### Post by Linux_noob1 on 2007-08-20
I have a computer I pulled out of my closet with 64mb ram,300mhz intel PII processor 20gb hard drive, and 4mb video.

I got the puppy Live CD but how do you install puppy with swap?
Also is this the best rout to go or should I be looking at another distro?

Is there a tutorial for a complete noob on installing puppy linux and getting swap set up?

Thanks in advance

---

### Post by yeastpuppet on 2007-08-20
Hi Noob

And we all were noobs at one time!

Check here for Puppy installation and walkthroughs

[http://puppylinux.org/docs/?Puppy_Linux_Documentation_Project](http://puppylinux.org/docs/?Puppy_Linux_Documentation_Project)

YP

---

### Post by init1 on 2007-08-20
mkswap /dev/yourpartitionhere
swapon /dev/yourpartitionhere
There may be a /etc/rc.d/ script you can edit this to activate it at start up.

---

### Post by init1 on 2007-08-20
Oh, and DSL is better IMHO.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by wolfen69 on 2007-08-21
definitely damn small linux.

---

### Post by dptxp on 2007-08-21
You may have problems installing Puppy to HDD, many have, I had. I had XP and Ubuntu installed, could not boot Ubuntu after installing Puppy.
But as standalone, you may find it simple. You can make partitions first with GParted, including thec SWAP partition. Say 512 MB or 1 GB.

---

### Post by Linux_noob1 on 2007-08-21
I couldn't get puppy installed. Apparently Gparted just kept locking up on it. :(

I decided to try DeLi linux since it seems to be designed more for putting on the hard drive ? :confused:

Anyways just for the sake of not having to come back later asking for help saying I messed up the hard drive :lolflag: I thought if someone here could tell me how I should partition this with this program thingy? I have never partitioned a hard drive before.
Also shouldn't this be NFTS not FAT?
II am thinking of having a 1gb swap. (i mean, i am never gonna use 19gb on that old machine, right?) :)

[IMG]http://i211.photobucket.com/albums/bb153/woodland_photographer/IMG_7310.jpg[/IMG]
here is the image of the screen. If this is not clear enough I will post a larger image.


Thanks for helping me out here, as you know I am a complete noob at this :)

---

### Post by init1 on 2007-08-21
CFDisk? You shouldn't be using that, it's not easy enough for beginners. Use Gparted.

---

### Post by johnny4north on 2007-08-22
here is a link to Feather linux - [http://featherlinux.berlios.de/](http://featherlinux.berlios.de/)
Feather linux is based on debian and uses flux.  it is the easiest mini distro to install. it has a experimental installer to the harddrive.  just answer a few simple questions then click away.  i tried it and also did the manual install both worked easily.  i would recommend the experimental installer for a easy install.  good luck oh here a bunch of other small distros. have fun:) - [http://wiki.laptop.org/go/Minimal_Linux_distros](http://wiki.laptop.org/go/Minimal_Linux_distros)

---

### Post by dptxp on 2007-08-22
Yes 1-2 GB SWAP shall be fine, no one fills his Hard Disk anyway.

Take care to make a separate partition for data, like /home or maybe just a partition for data in ext3 format. You can keep 4-6 GB for / (root) partition for your OS and other programs you add.

THe separate data partition comes handy when you reinstall your OS.


MAKE PARTITIONS WITH GPARTED LIVE CD. DOWNLOAD GPARTED AND MAKE LIVE CD. BOOT WITH IT.

---

### Post by Linux_noob1 on 2007-08-22
I found a complete installation guide on installing DeLi.
Looks like I got it to work. Even got it hooked up to my network. So I can use it for browsing the web.

I set up the swap to 200 (thats around what the guide suggested for my amount of RAM)

So far I am really impressed with its performance.
I got DeLi working at 1024x768 24bit color. Opened 40 windows and it still is working extremely fast. It just won't lock up!!!


All I need to do is get firefox 1.5 on it. But all the browsers I have are dillo and some ?old? version of konquerer. When I try to download the firefox 1.5 for DeLi of the DeLi page, it wont work. So I just downloaded the it off of my primary PC and saved it to a cd. Only problem now is I can't figure out how to load files off of my cd drive :lolflag:
tried opening the cdrom folder, and a small sound would come from the cd drive, but nothing would happen. :confused:
   How do I get the cd drive to work???

---

### Post by init1 on 2007-08-23
> **Linux_noob1 said:**
> I found a complete installation guide on installing DeLi.
Looks like I got it to work. Even got it hooked up to my network. So I can use it for browsing the web.

I set up the swap to 200 (thats around what the guide suggested for my amount of RAM)

So far I am really impressed with its performance.
I got DeLi working at 1024x768 24bit color. Opened 40 windows and it still is working extremely fast. It just won't lock up!!!


All I need to do is get firefox 1.5 on it. But all the browsers I have are dillo and some ?old? version of konquerer. When I try to download the firefox 1.5 for DeLi of the DeLi page, it wont work. So I just downloaded the it off of my primary PC and saved it to a cd. Only problem now is I can't figure out how to load files off of my cd drive :lolflag:
tried opening the cdrom folder, and a small sound would come from the cd drive, but nothing would happen. :confused:
   How do I get the cd drive to work???
Mount it. 
```

mount /dev/cdrom /mnt

```
Type that into a terminal. It may or may not work.

---

### Post by Linux_noob1 on 2007-08-23
Ok it ended up all I needed to do was right click on the link and hit download URL (Hey don't laugh at me im a noob! :) )

 
Firefox runs well. I got 4 tabs open and all is well.... I wonder if this pc can handle 40......... 

Both fluxbox and icewm are working VERY fast. I am extreamly surprised at the speed (concidering how old this PC is and the resolution its set at)
      This PC with linux is probebly as fast as a 5ghz processor& 8gb of ram running VISTA :lolflag:
 
So far my only complaint is that it seems like I can't get firefox into the menu and I have to start it from the console. (same with some other programs with icewm) So if i accidently close the console it closes firefox with it. But its not that bad of a problem.


So it looks like everything is all good on this old PC. Thanks all for helping a noob install linux :)

---

