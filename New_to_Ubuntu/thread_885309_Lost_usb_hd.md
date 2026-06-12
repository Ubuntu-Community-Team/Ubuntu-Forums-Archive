---
title: "Lost usb hd"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by dabazzman on 2008-08-10
After a month of annoyances and flustration attempting to install 8.4 on my pc Windoze can't even see my usb hd...](*,)](*,)](*,)](*,) 5 hours wasted just tonight.
W-98 was far easier to install than this pita, and far faster. I boot into Unbuntu and I get this error now... 

BusyBox v1.1.1[Debian 1:1.1.3-5unbuntu12] built in shell [ash]
enter 'help' for a list of built in commands

then I get the prompt

[initramfs] and then a blinking cursor

Now what? I've got 500gb of useless new junk or what?

This install has been anything but user friendly from the start.

---

### Post by dabazzman on 2008-08-10
*bump*

---

### Post by bpowell2005 on 2008-08-10
Hmmm...Let's start at the beginning:

What exactly are you trying to do? 

You have a windows machine now (XP?) 
You want to install Ubuntu on that machine?
Dual Boot?
You have a 500G USB Hard drive.
Windows can't see that drive?
Is it formatted correctly?

Please lay out exactly where you were (system wise) what you've done, and where you want to go, and we'll be able to help vector you in.

---

### Post by dabazzman on 2008-08-10
After a month of attempting to install 8.4 only to discover it it was in 'live' mode and wouldn't keep my settings and repeated attempts to get error 10 [partman] the partitioner, I belive, and dealing with error 141 and incredibly long scans on the wrong hd, to the point where I had to forcibly shut the system down [read surge protecter] as my system had slowed to a crawl [ installing W-98 on an old p-133 w/64mbs of ram seemed fast, and was compared to this] I've wound up with a brand new 500gb usb hd that windows can't even see.
If it wasn't for XP I would have a dead box. I had better results with Mandrak 4 back in 2000 except for the lack of a working video driver. And it took far less time to install.

---

### Post by bpowell2005 on 2008-08-10
> **dabazzman said:**
> After a month of attempting to install 8.4 only to discover it it was in 'live' mode and wouldn't keep my settings and repeated attempts to get error 10 [partman] the partitioner, I belive, and dealing with error 141 and incredibly long scans on the wrong hd, to the point where I had to forcibly shut the system down [read surge protecter] as my system had slowed to a crawl [ installing W-98 on an old p-133 w/64mbs of ram seemed fast, and was compared to this] I've wound up with a brand new 500gb usb hd that windows can't even see.
If it wasn't for XP I would have a dead box. I had better results with Mandrak 4 back in 2000 except for the lack of a working video driver. And it took far less time to install.

Well, if you have a computer that will run Windows XP, then it is most likely powerful enough to run Ubuntu. Provided you have the hard drive space (On your internal drive, not on the USB) then you should be able to insert the Ubuntu CD, boot into the "Live" distro...and click the "install" icon on the desktop. You'll be asked 7 questions, and the installation will take off...it usually takes me about 30 - 40 minutes to install Ubuntu from CD.

During the installation interview, you'll be asked how you want to install ubuntu, tell it to resize the windows partition (you can choose how much HD windows and Ubuntu will get) and then it'll do the rest.

After installation, remove the live cd, and reboot...you should get a boot menu (that will default to Ubuntu) but you could choose XP if you wanted...let Ubuntu boot...and you'll be in your brand new OS...now, any changes you make here will be persistent, not like the live cd.

As for your 500 gig USB drive. I recommend you fire up Windows, plug the USB drive in, and then look for it in the device manager and format it to NTFS. Windows should then recognize it.

---

### Post by dabazzman on 2008-08-10
deleted a repeat

---

### Post by dabazzman on 2008-08-10
> **bpowell2005 said:**
> Well, if you have a computer that will run Windows XP, then it is most likely powerful enough to run Ubuntu. Provided you have the hard drive space (On your internal drive, not on the USB) then you should be able to insert the Ubuntu CD, boot into the "Live" distro...and click the "install" icon on the desktop. You'll be asked 7 questions, and the installation will take off...it usually takes me about 30 - 40 minutes to install Ubuntu from CD.

During the installation interview, you'll be asked how you want to install ubuntu, tell it to resize the windows partition (you can choose how much HD windows and Ubuntu will get) and then it'll do the rest.

After installation, remove the live cd, and reboot...you should get a boot menu (that will default to Ubuntu) but you could choose XP if you wanted...let Ubuntu boot...and you'll be in your brand new OS...now, any changes you make here will be persistent, not like the live cd.

As for your 500 gig USB drive. I recommend you fire up Windows, plug the USB drive in, and then look for it in the device manager and format it to NTFS. Windows should then recognize it.

Been there, done that
Now my pc doesn't even see the usb drive, which was origionaly formated for ntfs.
 Something seems to have gone wrong in my partioning and now I'm left with the prompt...

BusyBox v1.1.1[Debian 1:1.1.3-5unbuntu12] built in shell [ash]
enter 'help' for a list of built in commands

then I get the prompt

[initramfs] and then a blinking cursor

whatever that means.

---

### Post by dabazzman on 2008-08-10
Well, if you have a computer that will run Windows XP, then it is most likely powerful enough to run Ubuntu. Provided you have the hard drive space (On your internal drive, not on the USB)

Mine was sent to the usb, maybe we're on to something here. While I can do a 5 gb install on my internal hd and boot it, hmmmm... something to ponder as I go to bed.

---

### Post by dabazzman on 2008-08-11
Ok, my install has gone horribly wrong and I need to compleatly delete it and reformat it, my pc knows that my 500gb hd is there, xp doesn't see it and when I try to fire up ubuntu it goes to a grub command using the cd. I need to somehow pry linux off of the pc and my usb hd to try a clean install.
So how do I go about doing it?

---

### Post by starcannon on 2008-08-11
Easiest utility going for this sort of thing:
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

Download it directly using this link:

[http://downloads.sourceforge.net/gparted/gparted-live-0.3.7-7.iso?modtime=1215010676&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-live-0.3.7-7.iso?modtime=1215010676&big_mirror=0)

Will let you do anything you want with your hdd partitions, delete, create, resize etc...

Its a relatively small download and should do what your asking.

---

### Post by dabazzman on 2008-08-11
Thanks, I'll give it a try and see how it goes.

---

