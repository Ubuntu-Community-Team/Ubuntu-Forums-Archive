---
title: "[SOLVED] My PC Hates Linux (Distro Hell)"
date: 2008-09-10
forum: Other OS Talk
---

### Post by BrokenKingpin on 2008-09-10
I seriously think my new desktop PC hates Linux. I have tried 8-10 distros on this thing and none of them want to work properly. I have been using Linux for many years and I have never had so much trouble getting a distro to play nice with a computer. My computer is a HP Pavilion m9250f (Intel quad core, 4GB RAM, Nvidia 8600GT). Let me give you the run down of what I have tried:

Ubuntu 8.04.1 64-bit:
-	Weird kernel error on boot, which I think is causing major stability problems (I think an update to the latest kernel might fix this, but have yet to try it):
 	[http://ubuntuforums.org/showthread.php?t=888580](http://ubuntuforums.org/showthread.php?t=888580) 
-	Wireless is terrible for some reason. At max I get a 2MB connection:
[http://ubuntuforums.org/showthread.php?t=888583](http://ubuntuforums.org/showthread.php?t=888583) 

OpenSUSE 11.0 64-bit:
-	No wireless out of the box and was too lazy to figure out how to get the driver I needed
-	Once in a while the start-up would take up to 15 minutes. I am assuming it was hanging on one thing, but I never really looked into this
-	Yast still sort of sucks, but is getting better
-	I never have liked SUSE, so I didn’t give it much of a chance. I was running out of options so I decided to try it

MEPIS 7.0 64-bit
-	Live CD would boot, but could not start X and leave me at a command line login. I when I tried start x, it would give an error saying no screens found – IO Error 104. I tried starting the live CD with the VESA driver, but the monitor would go black and lose the signal when X started

Sabayon 3.5 64-bit
-	This was the only distro to work with all my hardware out of the box, but unfortunately this distro is riddled with bugs
-	Spritz package manger is terrible &#61664; hangs after installing packages. When you close it the process hangs around and if you open it back up you can’t use it because there is already an instance of it running.
-	When closing an OpenOffice application in KDE a crash reports pops up
-	Gnome terminal gives security error when running apps as su
-	Gnome and KDE menus are badly managed. For example the Gnome menus have entries for KDE configuration apps
-	… there are a couple more I don’t feel liking typing out

Mint 5 32-bit
-	Similar problems to Ubuntu (because it based on Ubuntu)

PCLinuxOS 2008 Gnome Edition (32-bit I think)
-	Live CD hangs on boot after starting HAL service

Fedora
-	Installation hangs

Mandriva One 2008.1 64-bit
-	Installation goes fine, but in the post installation configuration it hangs after entering in user information right before the GRUB install. I was really looking forward to trying this Disrto as well

If anyone has any suggestions on how to make any of these distros work or even another distro to try (64-bit of possible) please let me know. Thanks!

---

### Post by ffi on 2008-09-10
> **BrokenKingpin said:**
> 
Mandriva One 2008.1 64-bit
-	Installation goes fine, but in the post installation configuration it hangs after entering in user information right before the GRUB install. I was really looking forward to trying this Disrto as well

Maybe when it hangs, shutdown, restart the livecd again and use the control center to install grub at the were your install hangs the install should be done basicly...

---

### Post by zmjjmz on 2008-09-10
Seeing as Sabayon works, if you're willing to spend time setting up Gentoo you should try so.

---

### Post by SunnyRabbiera on 2008-09-10
Try a non 64bit verion of one of them. Like mandriva.
Sometimes the 64bit version isnt as good as the 32bit one

---

### Post by Sef on 2008-09-10
> If anyone has any suggestions on how to make any of these distros work or even another distro to try (64-bit of possible) please let me know. Thanks!

Some hardware just does not work with GNU/Linux.  Sometimes, GNU/Linux just needs a future update to work well.

---

### Post by BrokenKingpin on 2008-09-14
ffi, I tried this and it still fails to install grub, I don't think it likes the Vista partitions for some reason.

zmjjmz, I was thinking of trying Gentoo, I just don't think I have the time right now.

SunnyRabbiera, I was hoping I could find a good 64-bit distro. I have been using a 64-bit OS since Fedora Core 4, I would hate to go back to 32-bit now. I am quite surprised 64-bit isn't the standard by now. I know it isn't a huge gain in most situations, but I do make use of it.

---

### Post by BrokenKingpin on 2008-09-14
[Solved] I installed Ubuntu 8.10 Alpha-5 64-bit (which uses the latest kernel) and everything works fine. I no longer get the kernel errors on startup and all freezing problems are gone. Also, my wireless card works perfectly now. This release does have a few bugs, but nothing too severe and it's only an alpha. I will keep using this and just upgrade as the new betas come out.

Edit: It must be noted that this Alpha release of Ubuntu is far less buggy than Sabayon lol.

---

### Post by SunnyRabbiera on 2008-09-16
> **BrokenKingpin said:**
> ffi, I tried this and it still fails to install grub, I don't think it likes the Vista partitions for some reason.

zmjjmz, I was thinking of trying Gentoo, I just don't think I have the time right now.

SunnyRabbiera, I was hoping I could find a good 64-bit distro. I have been using a 64-bit OS since Fedora Core 4, I would hate to go back to 32-bit now. I am quite surprised 64-bit isn't the standard by now. I know it isn't a huge gain in most situations, but I do make use of it.

Well most people still use 32bit chips (like me) and the world of 64bit is still not where many would like it when concerning hardware/ software compatibility.

---

