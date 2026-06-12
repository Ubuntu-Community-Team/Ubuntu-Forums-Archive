---
title: "Install crashed; now HDD isn't even detected in BIOS?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by mark_pdx on 2008-08-19
I'm hoping to migrate some of my PCs to Linux after two decades of frustration with MS products.  Unfortunately I'm having a bad first experience, but maybe you can help rescue it.

Wanted to try out Xubuntu 6.06 on a vintage 1998 Dell CP-x H500 laptop (256MB RAM, 20GB HDD).  Got the ISO Live CD image, burned it, checked the disk, and was able to boot Xubuntu from the CD drive and look around at the applications.  All looked great!

So I went ahead and tried the Install.  All dialogs went well.  At the partition question I accepted the simple choice to erase the entire HDD for the Linux partitions, because I didn't want to keep the old Windows 2000 OS or any programs or data around.

At the end of the install I got a message saying the Install Crashed.  There was a screen full of text, but without a printer I had not way to save it, and I didn't yet know how to go find log files.  So sorry, I don't have that.

I figured the best bet was just to try again.  This time, before I got to the partition screen, the installer reported something like "File System not found" and then hung up (cursor spinning, mouse works, but  HDD light is off, and no progress after 30 mins.  Cancelled out.  Rebooted and went into BIOS setup mode --  now the primary hard disk drive is no longer detected.  Yipes!

So my question is -- can a crashed install process scramble a hard disk so badly it is not recognized by the BIOS?  Maybe damage the low level formatting??  I recognize the possibility that the HDD just up and failed during the install, it is an old unit.  

Is there a helpful solution from Linux experts?  Can this happen during partitioning?  Or should I just go searching for low-level diagnostics programs for the laptop and its disk?

I totally support the concept of open source software and want to join the movement, if I can just get over this little hump...

Mark

Mark

---

### Post by halitech on 2008-08-19
I think it was just a case of bad timing and the drive failure came first and resulted in the failed install. If the machine isn't seeing the hard drive in the BIOS then there will be no way of formatting the drive cause you need to see it in order to format it

---

### Post by mark_pdx on 2008-08-19
Thanks for the quick reply.  There's more news now -- I decided to remove the HDD from the laptop (power off natch) and look at it.  Duhh, that didn't help, but maybe it was just a bad contact?  So I reinstalled it and bingo the BIOS sees it again.  

So...booted Linux from CD, tried install again.  Again the error message "Failed to create a file system" occurred just before the partition question.  Again asked it to erase the whole disk and create its own partitions.  Again the Install Crashed message.  But this time I took a digital photo of the message.  I apologize for the quality, but it seems readable at least. Here goes:

[IMG]http://i313.photobucket.com/albums/ll365/mark_pdx/computers/Screenphoto.jpg[/IMG]


Does this help?

---

### Post by halitech on 2008-08-19
the messages don't really help me but then again, I'm not a developer :D

Xubuntu 6.06 should run on the specs you gave but I never had much luck with the live cd installer back during 6.06 so maybe if you want to install, give the alt install cd a shot and it should load better as it goesn't load the desktop first, just launches right into the install.

---

### Post by nicedude on 2008-08-20
Once a drive has given me allot of trouble such as this I have found that giving it a quick once over with DBAN can work wonders. DBAN stands for "Darik's Boot n Nuke" which erases hard drives so that the data on them is destroyed, since you just want a nice clean disk and are not worried about destroying secret data you can just select 1 simple pass ( where it will just write 0's to the whole disk ) and turn verification off. That way the whole overwrite will probably take less than 1 hour to do. I have had PC's that I worked on that would not install an OS period and then after a DBAN session to blank them they took the OS install like nothing was ever wrong.

Here is where you can get a CD .ISO of DBAN - just burn it to a CD and then boot the PC with it and select method 1 pass verification off and then press F10 to fire it up.

[http://www.dban.org/](http://www.dban.org/)

Hope that gets it going :-)

---

### Post by mark_pdx on 2008-08-20
Nicedude and halitech, thanks for the ideas.  I burned an alternate install CD for Xubuntu (8.04 this time) and it seemed to start the install OK, but then it would just hang up indefinitely at some points with no disk activity or lights.  And sometimes if I tap the area of the hard disk the process would move forward again for a while, but again stall out.  I think the hard disk could have a sticking bearing or something.

I will try DBAN - great tip, it's worth having around anyway - but I think I'll chalk this up to a dying hard disk and no fault of Linux.  Thanks!

---

### Post by Gregmond on 2008-08-20
If it is playing up in the BIOS it normally means either the HDD or the M/B has an issue (although it could be a cable but unlikely). Could also be an overheat issue (check all your fans are working etc) - in the time it took remove it, look at it etc then plug it back in it can cool down enough to boot back up, then you start using it (checking partitions etc) it decides to play dead again as it has warmed up.

Before trying the install, try using the partition manager on the live CD manually and see what it shows. Not sure what this is in Xubuntu, its in the System/Administration menu on Ubuntu from memory.

---

### Post by Alkemist69 on 2008-08-20
On one of my computers, Ubuntu 7.xx installs fine from CD, but the newer ones always crash (read errors). I ended up upgrading via the internet (used up alot of my alotted download limit doing that!). I have no explanation other than I have a dodgy CD that 8.xx don't like. Just my two cents in case you continue to have troubles.

---

