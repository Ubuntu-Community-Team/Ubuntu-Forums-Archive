---
title: "Help with Drivers"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by matt_Schlichtman on 2013-08-17
Ok so I am absolutely new to Linux as my personal Os and want to install the needed drivers for my newly built pc.- MoBo:Asus M5A97 R2.0 GPU:Saphire Radeon 7770 CPU: AMD FX Vishera 3.9Ghz etc. I downloaded all the neccesary updates for Ubuntu now where do I go to begin updating my drivers. Really haven't dabbled in much command but more than willing to learn.Any help would be mmuch appreciated

BTW Read through some older posts and community threads and it all seems a little complicated so if someone could help within lamens terms that would be awesome

Matt

---

### Post by QIII on 2013-08-17
Hello and welcome to the forums!

If everything is working (which it seems to be), then all the drivers, with the exception of the driver for your video card, are installed.  (Video cards and wireless adapters seem to be the most troublesome things when people run into problems.)

Your video card should be running right now on the open source Radeon driver.  For the vast majority of people, this will work just fine.  I would suggest using Ubuntu for a bit before you decide if you want to install the proprietary driver from AMD/ATI.  Open source is preferrable!  You might want to familiarize yourself with the ATI driver wiki in my signature.  Don't worry if you get confused.  I do every time I update something in it!  You can always ask questions.

Cheers!

---

### Post by Bucky Ball on 2013-08-17
Welcome to the forums. As QIII mentions, if it's working, then you have the drivers installed and they are up to date if you've done an update. If video is fine, you're using the open-source drivers that came with the kernel. The only reason to install the third-party drivers is if the open-source ones are not adequate, really.

Good luck and enjoy. ;)

PS: You don't mention what release you are using and it can sometimes be *unhelpful* to look through old pages! Things change from release to release, some things radically.

PPS: An introduction to the terminal might be to do an update/upgrade in there. Applications>Accessories>Terminal, then copy/paste, one at a time, hitting enter between:

```
sudo apt-get update
sudo apt-get upgrade
```

The first command updates any and all packages in your system that need it, the second upgrades any and all packages that need it. After that, all drivers are up to date and at the newest possible for your release! That's it.

Always use the update command prior to the upgrade one.

PPPS: I just re-read your first post. By updating the system you've inadvertantly actually already done what you are asking how to do. Cool!

---

### Post by 3rdalbum on 2013-08-17
13.04: There is a program in Ubuntu called "Software Sources". You can do a search in the Dash for it. Open it and click the last tab, which is for drivers. Click on the AMD Proprietary driver and click Install. That's it. Not hard at all.

12.10 or earlier: You may need to do a web search for an AMD/ATI driver PPA. Ubuntu 12.10 and 12.04 probably wont know about your card so wont be able to do the automatic install, but if you can find a PPA that holds the driver, this will also be easy to install.

Otherwise, go to the AMD website and download the driver manually. The installer AMD provides is not very easy to use, so try the Software Sources or a PPA first.

---

### Post by Bucky Ball on 2013-08-17
> **3rdalbum said:**
> ... try the Software Sources or a PPA first.

Indeed, as these will be updated whereas the driver manually installed will not.

---

### Post by Rob Sayer on 2013-08-17
This issue, like codecs, is often confusing to new linux users.  It isn't that confusing.

It's not like windows where you have a poorly set up database (ie. windows registry) with a gazillion drivers.  It's better.

In linux drivers are integral to the kernel.  There are a number of open source drivers in there, and when you install ubuntu it determines which one is the right one for the hardware items it detects.  It isn't always perfect ... video and wireless may need tweaking ... but it does a pretty damn good job.

As mentioned (by people much more knowledgeable than myself) you don't actually seem to be having any actual problems now.

Linux may look compicated compared to some other OS's but it isn't.  It seems that way because it's open source, and therefore there is no attempt to hide anything from you.  It's actually pretty strauightforward, it just seems like there's a *lot* of it.

---

