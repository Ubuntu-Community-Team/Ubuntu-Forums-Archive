---
title: "Why does Ubuntu proxy Firefox versions?"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by allanonmage on 2013-06-22
Hi there! First post ont he forums, relatively new to Ubuntu, though not brand new to it. I've installed it a few times, but this time I'm going to learn it and use it.

I used pendrivelinux to make a bootable USB stick and installed 13.04 x64 onto a hard drive of a Compaq CQ61.  I remembered having a hard time updating Firefox last time I fooled around with Linux, so I checked the version of Firefox.  It said 20, but didnt' mention if it was the current reelase or not.  Eventually I found out that 20 is what shipped with this version of Ubuntu, and Ubuntu eturns off Firefox's ability to auto update itself.

Why does Ubuntu turn off Firefox's ability to update itself?  Is there some benefit to this?  To me, it seems like they made the same stupid call that Android handsets make by baking in junkware and not allowing you to remove it, which is the polar opposite to the Linus & open source movement, right?  I'm going to try to learn Linux because I don't like where Microsoft is going.

I tried googling and searching the forum and found instructions on how to manually update, but nothing talking about how or why this was done or a good thing.

---

### Post by mike555 on 2013-06-22
Firefox should update when Ubuntu updates, if you want a newer version use the PPA ( [http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_next](http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_next) )

---

### Post by allanonmage on 2013-06-22
I can find elsewhere how to do the update.  I want to know what benefit or what reasoning is behind the decision to ship an old version of Firefox AND, AND, why the auto-update already built in to Firefox was disabled.

---

### Post by Frogs Hair on 2013-06-22
Hello and Welcome

Firefox updates via the software  updater through the Ubuntu repositories .  The reason you don't have FF 21 may be due to the USB installation . My current 13.04 installation has 21 .  I have no experience with a USB installation, but you can try the software updater.

It used to be that the version of Firefox that came with the ISO is what you were stuck with for the life of the release, but that changed some time ago and now FF updates regularly.

---

### Post by allanonmage on 2013-06-22
Hmmm.... it seems we're all talking about different things here and I'm not sure how to resolve them.

I understnad that OS's that are packaged can come with outdated software and need updates, and I'm not concerned about that.

It seems that the version of Firefox that came with 13.04 came with the auto-update functionality disabled.  Firefox on Windows will tell you if it's up to date or not, as well as give you the option to check and install updates.  You can do this in the Help, About section.  The version of Firefox that came with Ubuntu does not have that ability, which makes no sense to me.  Why would that be turned off?

---

### Post by Frogs Hair on 2013-06-22
The version of FF on Ubuntu has modifications  for the operating system and the software repository system is a way of screening for malicious code. Windows uses a different package and installation system. Chrome has no modifications yet updates come via the repository as well even through the .deb package is downloaded and installed directly from the website.

---

### Post by arpanaut on 2013-06-22
The packages that come from the ubuntu repositories have been tested and packaged expressly for ubuntu.
What you get from mozilla may or may not work flawlessly with ubuntu, there are some tweaks made by the ubuntu devs. that make it integrate better with the default desktop environment.

And as said before one is better off using the ubuntu repositories to ensure better security.
This is true not only for firefox, but for most all packages used on ubuntu.

Hence for better stability and security it is better to use what is delivered by the repository system. 
And is why the auto-update is turned off by default.

---

