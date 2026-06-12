---
title: "Intel Nuc 2830 cpu."
date: 2014-11-04
forum: New to Ubuntu
---

### Post by bigjohn2 on 2014-11-04
Waiting for my Intel nuc to be delivered which is coming with a 40gb ssd and 4gb ram.

Going to install Ubuntu on this machine which will be the first time that I have used Linux since 2005 so hoping it all comes back to me.

Anyway anything that needs to be done or changed to ensure this installs and boots without any problems.

---

### Post by oldfred on 2014-11-04
Some links, may not be a bit older:

 Intel NUC
[http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html](http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html)
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)
[http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1)
UEFI - in efi partition Manual copy grubx64.efi to bootx64.efi to make it work.
[http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)
BIOS update fixes some issues
[http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/](http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/)

---

### Post by mastablasta on 2014-11-05
make sure no swap is on ssd (remove swapiness or something)

---

### Post by bigjohn2 on 2014-11-10
Many thanks for the replies.

Everything went smooth for the installation.

The plan is to use this as a media pc behind the tv so I'm looking to control the unit using the iPad so can anyone recommend the best software / iOS app for the job.I have tried a couple without success so far.

---

### Post by mastablasta on 2014-11-10
what kind of software did you load?

I have only OpenElec (on RaspberryPi) and control it using the TV remote controller. 
another option would be to get a dedicated remote (they are very cheap) or something like a Measly keyboard/airmouse. they are also quite cheap. and if you plan to type a bit more I guess they make sense.

if I need to do some changes or some other thing there is Filezilla for file transfers and SSH for terminal access. 
ofcourse there are also various remote apps for pad, tablets, phones. I wouldn't know much about them since what I have suffices.


I am curious why would you need such a strong computer only to play media? do you plan on playing 4K media or something? a Corei CPU, 4 GB RAM and an SSD?!?! oh well I guess you have more money to spend than I do. :)

---

### Post by bigjohn2 on 2014-11-10
I had intended to use unified remote to control the pc from the iPad but the Ubuntu software centre says the download server software is incompatible even though it's listed for Ubuntu.

The pc is the Celeron version which someone purchased new then decided he could use his laptop so I bought the bundle.I will use the pc for basic computing and iTunes if it runs under Wine as well as media.

---

### Post by mastablasta on 2014-11-11
how did you download/install the software?
I am not sure how unified remote works.

I suggest you look into OpenElec and XBMC (now rebranded as Kodi) they might have a few things already included. not sure at the moment since it's been a year when I gave them a closer look.

[http://kodi.wiki/view/XBMCbuntu](http://kodi.wiki/view/XBMCbuntu)

heh Google even offered a how to vide for NUC: *[www.youtube.com/watch?v=Xwb0fShqj1o]("http://www.youtube.com/watch?v=Xwb0fShqj1o")*

I guess since you plan to use the PC for some basic computing OpenElec is not for you. it is ment only as media PC and is a bit lighter than XBMC.

edit: XBMC iOS remote: [http://kodi.wiki/view/Official_XBMC_Remote/iOS](http://kodi.wiki/view/Official_XBMC_Remote/iOS)
edit2: I think XBMCbuntu might have a desktop. if not you could probably install it - you know, for basic computer use....

---

### Post by bigjohn2 on 2014-11-13
Decided to stick with Ubuntu and have it auto start into the xbmc session to make it foolproof for the better half.Along with the xbmc remote app for the iPad which wakes and shuts down the system it's a neat setup.

thanks for your help.

---

