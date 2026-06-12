---
title: "Brasero"
date: 2014-08-20
forum: New to Ubuntu
---

### Post by ross5 on 2014-08-20
I am trying to burn a bootable .iso file with Brasero.

I selected Image to disk, but everytime I burn the file it just puts the file on the disk. It doesn't actually burn/expand the .iso file to it.   

( If any of that makes sense )

---

### Post by grahammechanical on 2014-08-20
I always use the Ubuntu File Manager (nautilus). I select the ISO image and right click it and then from the menu I select Write to Disc. A dialog will appear and if you have a DVD disc in the drive it will be recognised. If there is already data on the disc you will be asked to confirm to blank the disc. File Manager does the job for me.

Regards.

---

### Post by Sanctimonious_Ape on 2014-08-20
From personal experience, I'd use almost anything *other* than Brasero.  It's buggy.  There are plenty of other disc burning programs available in the software center.  Xubuntu came with xfburn and I've not had a problem with it (in my admittedly limited usage) thus far.  I have no idea why some distros include that program other than the distro builders don't actually use it to build disks and therefore don't realize its flaws.

---

### Post by craig10x on 2014-08-20
I use to find Brasero buggy, but it has a new maintainer now and it's been working fine for me since 13.10 as well as my current 14.04 install....

Although one thing that is important to do is to go to the brasero menu and under "edit" select plug ins and be sure to uncheck the two "checksum" plug ins...by doing so, it will burn isos in the normal amount of time....if you leave them checked, it takes like forever!

Try doing that...not sure if it will help your problem though i often burn isos with Brasero exactly as you have been trying to do and it works fine for me...I select Burn Image on the Brasero menu, then add the image and set the speed to slowest burning (for best results with an iso)....

if you can't get it to work then you might try installing XF Burn and use that instead...

---

### Post by kansasnoob on 2014-08-20
Look here:

[http://ubuntuforums.org/showthread.php?t=2236433&p=13083753#post13083753](http://ubuntuforums.org/showthread.php?t=2236433&p=13083753#post13083753)

---

### Post by Sanctimonious_Ape on 2014-08-20
I'm new to Linux in the past couple months (but not new to PCs by a loonnngggg shot, even have some years of UNIX experience from a decade ago), so I'm not referring to old versions.  I tried building a disk in Brasero that contained 4.2xGiB of data (a DVD-R should hold 4.37GiB), but it wouldn't let me burn it because it insisted my 4.7GB of files were too big for the disk.  It was pretty obvious to me that it was confusing GiB (base2, the way computers **really** count and thus how it **should** be done) and base10 (the way humans count, and something hard drive manufacturers forced upon us in the '90s when we started having Gigabyte-sized drives because it made their drives sound larger than they actually were - this is why my "1TB" hard drive is really 932GiB).

Brasero would have me waste several hundred MiB of space per disk due to its poor programming in confusing these counting methods.

---

### Post by kansasnoob on 2014-08-20
> **Sanctimonious_Ape said:**
> I'm new to Linux in the past couple months (but not new to PCs by a loonnngggg shot, even have some years of UNIX experience from a decade ago), so I'm not referring to old versions.  I tried building a disk in Brasero that contained 4.2xGiB of data (a DVD-R should hold 4.37GiB), but it wouldn't let me burn it because it insisted my 4.7GB of files were too big for the disk.  It was pretty obvious to me that it was confusing GiB (base2, the way computers **really** count and thus how it **should** be done) and base10 (the way humans count, and something hard drive manufacturers forced upon us in the '90s when we started having Gigabyte-sized drives because it made their drives sound larger than they actually were - this is why my "1TB" hard drive is really 932GiB).

Brasero would have me waste several hundred MiB of space per disk due to its poor programming in confusing these counting methods.

It's not just Brasero, it also effects Nautilus. I needed to make a 12.04.1 CD last night and couldn't:

[ATTACH=CONFIG]255677[/ATTACH]

But actual size is small enough:

```
lance@lance-desktop:~$ cd Downloads/Ubuntu
lance@lance-desktop:~/Downloads/Ubuntu$ ls -lah
total 11G
drwxrwxr-x  2 lance lance 4.0K Aug 20 13:19 .
drwxr-xr-x 12 lance lance 4.0K Aug 19 18:21 ..
-rw-r--r--  1 lance lance 744M Jul 18 02:27 precise-desktop-amd64.iso
-rw-------  1 lance lance 756M Aug  7 21:12 precise-desktop-i386.iso
-rw-------  1 lance lance 980M Jul 22 07:16 trusty-desktop-i386.iso
-rw-r--r--  1 lance lance 696M May 21 12:07 ubuntu-11.10-desktop-i386.iso
-rw-rw-r--  1 lance lance 693M Aug 19 18:47 ubuntu-12.04.1-alternate-i386.iso
**-rw-------  1 lance lance [COLOR="#FF0000"]696M[/COLOR] Aug 17  2012 ubuntu-12.04.1-desktop-i386.iso**
-rw-------  1 lance lance 695M Feb 13  2013 ubuntu-12.04.2-desktop-amd64.iso
-rw-------  1 lance lance 987M Jul 22 22:38 ubuntu-14.04.1-desktop-i386.iso
-rw-------  1 lance lance 964M Apr 17 01:35 ubuntu-14.04-desktop-amd64.iso
-rw-------  1 lance lance 970M Apr 17 01:37 ubuntu-14.04-desktop-i386.iso
-rw-------  1 lance lance 1.1G Aug  8 08:21 utopic-desktop-i386.iso
-rw-------  1 lance lance 1.1G Jul 27 08:20 utopic-desktop-i386.iso.zs-old

```

It also effected Xfburn :cry:

I had to settle for using a netboot image.

There is a very old bug report regarding that but I can't find it.

---

### Post by Sanctimonious_Ape on 2014-08-20
Sorry, you're right - it wasn't xfburn I used last, it was k3b.  KDE always was more Windows-like, but it's become a little too heavy-feeling for my old laptop - k3b works fine under Xubuntu and Lubuntu, just needs to install a bunch of dependencies (including the needless nepomuk).

---

### Post by ellisf2 on 2014-08-21
I'm not an experienced Linux user, but when I tried to use Bracero, which is bundled with a lot of Linux distros, I was surprised by how bad it is. I did a little research and quickly downloaded and installed K3b, burned the ISO I needed and moved on. I'm not sure why anyone uses Bracero. Perhaps it has some hidden usefulness that I missed, but I found K3b to be easy to use and reliable.

---

### Post by Jonathan Precise on 2014-08-21
> **ellisf2 said:**
> I'm not an experienced Linux user, but when I tried to use Bracero, which is bundled with a lot of Linux distros, I was surprised by how bad it is. I did a little research and quickly downloaded and installed K3b, burned the ISO I needed and moved on. I'm not sure why anyone uses Bracero. Perhaps it has some hidden usefulness that I missed, but I found K3b to be easy to use and reliable.

Brasero is bundled in sessions like GNOME/Unity/etc. that use the GTK renderers (except XFCE/LXDE, as they come with lighter burning tools) because it uses the GTK toolkit, unlike k3b, which is specifically made for KDE (even though it works fine under GTK renderers)

As for the bug, I can't reproduce it on my system. It expands the image on my case.

---

### Post by craig10x on 2014-08-21
> **ellisf2 said:**
> I'm not an experienced Linux user, but when I tried to use Bracero, which is bundled with a lot of Linux distros, I was surprised by how bad it is. I did a little research and quickly downloaded and installed K3b, burned the ISO I needed and moved on. I'm not sure why anyone uses Bracero. Perhaps it has some hidden usefulness that I missed, but I found K3b to be easy to use and reliable.

Assuming you're using a current version of Brasero, it should work well (mine does) because it has a new maintainer who fixed the bugs in it (agrred it use to be terrible but the original maintainer had stopped maintaining it like over 2 years ago!)...but if you don't turn off the two checksum plug ins (found under edit in the brasero menu) you would get the impression it is still bad news...with thise plug ins on (which they are by default) it could take 45 minutes to bun on 4.7 gb dvd!  But with those two plug ins off:  TEN MINUTES for the same dvd...quite a difference ;)
And i never get coasters using Brasero now, either...

Why it has those stupid checksum plug ins is beyond me...it slows down the burning to a crawl :rolleyes:

---

### Post by Jonathan Precise on 2014-08-21
> **craig10x said:**
> Assuming you're using a current version of Brasero, it should work well (mine does) because it has a new maintainer who fixed the bugs in it (agrred it use to be terrible but the original maintainer had stopped maintaining it like over 2 years ago!)...but if you don't turn off the two checksum plug ins (found under edit in the brasero menu) you would get the impression it is still bad news...with thise plug ins on (which they are by default) it could take 45 minutes to bun on 4.7 gb dvd!  But with those two plug ins off:  TEN MINUTES for the same dvd...quite a difference ;)
And i never get coasters using Brasero now, either...

Why it has those stupid checksum plug ins is beyond me...it slows down the burning to a crawl :rolleyes:

I currently have those plugins enabled, and it never takes much time for those to run. It takes me less than ten minutes burning a 3 GB image to a 4.7 GB DVD with those plugins enabled.

Regards.

---

### Post by Mike_Walsh on 2014-08-21
Every OS I'm running (I'm running 6 at the moment) that has had Brasero installed, I've immediately dumped it and installed XFburn instead. Works perfectly, every time.

Craig10x may well be correct about the app having new maintainers.....I won't dispute that. But I read a LOT of blog and forum postings about Brasero's bugginess when I first moved to Linux back in May, and almost everybody was recommending to use XFburn instead; and that's what I've done. I have had zero problems with it, despite the fact that it was supposed to be still in the beta stage when I first tried it. 

I would recommend it to anyone.

Regards,

Mike.

---

### Post by craig10x on 2014-08-21
I'll have to check it again with the plugins enabled the next time i do a dvd burn...maybe they fixed it...it was quite some time ago when i last tried it with them on...
I had gone to XFBurn also which does work well...but i did return to Brasero once i saw it was working properly again...but i would agree that XFBurn is a nice alternative...
K3b was my favorite but it brings in all those kde libraries so prefer to use a gnome or xfce based burner...

---

### Post by craig10x on 2014-08-23
Just out of curiousity, i burned the same 4 gb dvd with 4 gb of data twice....the first time with the two checksum plug ins enabled...the second time with them disabled...
With Checksum plug ins enabled:  55 minutes  With Checksum plug ins disabled:   10 Minutes....

Aside from the Checksums slowing down the process, it also reduced the burn speed to 1x EVEN THOUGH i had it set to burn at MAXIMUM SPEED...

So again i say, those plug ins are defective and anyone who would like to be able to use Brasero as their dvd burner in a FAST and EFFICIENT manner, be sure to un check those two plug ins before you start to use Brasero and leave them off permanently...@Jonathan: I am AMAZED you can have them on and burn a disc so fast...but it surely hasn't been my experience...

---

### Post by uRock on 2014-08-23
I've had the same problem with the checksums taking forever, but I usually spot when the Disk is done burning and the last checksum is running and eject the disk. 

To be honest, I usually do most of my burning in Windows. IMGBurn is probably the best burner software I've ever used. I've never had it fail.

---

### Post by craig10x on 2014-08-23
@uRock...a shame that imgburn is not available for linux...yes, i would have to say that one would get a VERY BAD impression of Brasero with those default checksum plug ins enabled...but once unchecked, Brasero has been burning for me like a dream!  Fast, Efficient, never get a coaster either...so i would say the new maintainer is doing a good job with it but he really should remove (or fix) those darn plug ins...

K3b use to be my favorite and i think it's probably the best linux burner i have found but i just like to avoid bringing in all the kde stuff just to get the one program...
XFBurn works very well, but Brasero has a few extra nice features...

---

