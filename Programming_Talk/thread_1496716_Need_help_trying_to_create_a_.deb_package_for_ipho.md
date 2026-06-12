---
title: "Need help trying to create a .deb package for iphone!"
date: 2010-05-29
forum: Programming Talk
---

### Post by flashkid4243 on 2010-05-29
So I've tried many times to create a debian package for the iphone. I'm having a problem as soon as I enter the command

dpkg-deb -b cydia

(after -b, i add the name of the folder which is "cydia")

I get the error
 "flashkid4243@flashkid4243-laptop:~$ dpkg-deb -b cydia
dpkg-deb: failed to open package info file `cydia/DEBIAN/control' for reading: No such file or directory"


The contents of my "control" file are as follows:
&#65279;Package: com.iphonedude4243.pokemontheme
Name: Pokemon Theme
Version: 1.0.4-1
Architecture: iphoneos-arm
Description: This is a Pokemon Theme for the iPhone and iPod Touch 
Homepage: [http://www.youtube.com/users/iphonedude4243](http://www.youtube.com/users/iphonedude4243)
Maintainer: ***** ******* <myemail@email.com>
Author: iPhonedude4243 <myemail@email.com> 
Sponsor: iPhonedude4243 <http://www.youtube.com/users/iphonedude4243>
Section: Themes (Springboard) 

(The maintainer area has been censored for security purposes) 


Everything seems to be okay. I downloaded the dpkg-deb-lnx file already and I've removed the .txt extension from the control file. I've tried everything and every time has failed with this error. I don't know what else to do.

---

### Post by SledgeHammer_999 on 2010-05-29
Are you sure that your "control" file is located in the DEBIAN subdirectory of cydia?

---

### Post by flashkid4243 on 2010-05-30
yeah I noticed that the directory was off and I fixed it and made a deb file. but there seems to be a new problem. I don't know if anyone on here knows how to fix it but when I add my repo to Cydia, and I try to download a theme from that repo, I get a "size mismatch" error. I've tried looking all around the internet for solutions but I've found nothing. Can you help me out?

My repo is: [http://iphonedude4243.110mb.com/cydia](http://iphonedude4243.110mb.com/cydia)


The theme is a cheesy pokemon theme that I made a long time ago.

Thanks for any help!

---

### Post by bsquidwrd on 2011-02-20
Try setting the permissions of the DEBIAN folder and the control file to 775. I know this is a year afterwards but just a thought.
:popcorn:

---

