---
title: "Wipe Computer"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by knifyspoony on 2008-09-16
When I installed Ubuntu I screwed up partitioning my disks and ended up with 60 GB of free space and lost 20 GB on another drive. I thought I could fix it later in Gparted but when I launch the program it will say 'scanning all drives' for hours, the longest I've waited was four hours. When I attempt to do a reinstall from the live CD, it won't boot. 

Also after installing Ubuntu I noticed it didn't wipe my hard drives and I still had files from Windows - which is where I have trojan I've been trying to get rid of.

I've gotten so desperate that I tried reinstalling Windows but it gives me an error and shuts itself down. It said to check for viruses, remove any newly installed hard drive controllers, check the hard drive configuration and run CHKDSK /F.

Are there any other methods of wiping a computer?

---

### Post by zephyrcat on 2008-09-16
Try DBAN:

[http://www.dban.org/](http://www.dban.org/)

It is most commonly used in cases where there is sensitive data on the drive, but it should world for regular stuff, too.

---

### Post by oilchangeguy on 2008-09-16
> **knifyspoony said:**
> When I installed Ubuntu I screwed up partitioning my disks and ended up with 60 GB of free space and lost 20 GB on another drive. I thought I could fix it later in Gparted but when I launch the program it will say 'scanning all drives' for hours, the longest I've waited was four hours. When I attempt to do a reinstall from the live CD, it won't boot. 

Also after installing Ubuntu I noticed it didn't wipe my hard drives and I still had files from Windows - which is where I have trojan I've been trying to get rid of.

I've gotten so desperate that I tried reinstalling Windows but it gives me an error and shuts itself down. It said to check for viruses, remove any newly installed hard drive controllers, check the hard drive configuration and run CHKDSK /F.

Are there any other methods of wiping a computer?

sounds like your hard drive has problems. do what the error message tells you to do. boot from the windows cd, after it loads press r to enter the recovery console. at the admin password prompt enter it, if none press enter to bypass the prompt. then type chkdsk /f and press enter.

---

### Post by VeeDubb on 2008-09-16
Wiping your hard drive, is generally one of the simplest things you can do with a hard drive.  Backing up, repairing, all that stuff is a mess.  If all you want to do is wipe it clean, it's VERY simple.  Pretty much any version of widows or linux will do this for you if you have an installation disk.

WARNING:  Following these instructions will destroy ALL of the data on your drive.  In fact, that's the point.

Ubuntu: Just put the disk in, boot up the disk and do a clean install.  When you get to the part about disk partitioning, just select "guided, use entire disk"

That will remove all partitions, create a new single partition, and wipe the drive.  


Windows (Should be the same with any variant of Windows 2000, XP or Vista)  :  Put the disk in, and reboot as you normally would to install.  Select "Install."  Do NOT select, repair or reinstall.  These will not format your drive.  

You'll eventually be asked where you want to install, and get a screen showing all of your partitions.  Follow the directions on that screen to delete all of your partitions.  Then, create a new single partition.  (In XP and 2000, you'll be asked if you want to use fat32 or NTFS, choose whichever you want.  If in doubt, use NTFS because it is now the "standard")

You'll also be asked if you want to do a "quick" format or a "full" format.  Choose full.

Other versions of linux: Most versions of linux with a graphical installer should have an option similar to ubuntu's "gudied: use entire disk".  If the one you decide to use does not, just do the same as windows, and follow the on-screen directions for deleting all the partitions and creating new ones.

---

### Post by oilchangeguy on 2008-09-16
> **VeeDubb said:**
> Wiping your hard drive, is generally one of the simplest things you can do with a hard drive.  Backing up, repairing, all that stuff is a mess.  If all you want to do is wipe it clean, it's VERY simple.  Pretty much any version of widows or linux will do this for you if you have an installation disk.

WARNING:  Following these instructions will destroy ALL of the data on your drive.  In fact, that's the point.

Ubuntu: Just put the disk in, boot up the disk and do a clean install.  When you get to the part about disk partitioning, just select "guided, use entire disk"

That will remove all partitions, create a new single partition, and wipe the drive.  


Windows (Should be the same with any variant of Windows 2000, XP or Vista)  :  Put the disk in, and reboot as you normally would to install.  Select "Install."  Do NOT select, repair or reinstall.  These will not format your drive.  

You'll eventually be asked where you want to install, and get a screen showing all of your partitions.  Follow the directions on that screen to delete all of your partitions.  Then, create a new single partition.  (In XP and 2000, you'll be asked if you want to use fat32 or NTFS, choose whichever you want.  If in doubt, use NTFS because it is now the "standard")

You'll also be asked if you want to do a "quick" format or a "full" format.  Choose full.

Other versions of linux: Most versions of linux with a graphical installer should have an option similar to ubuntu's "gudied: use entire disk".  If the one you decide to use does not, just do the same as windows, and follow the on-screen directions for deleting all the partitions and creating new ones.

i do agree, however the op's hard drive probably has bad clusters. the chkdsk /f needs to be run.

---

### Post by VeeDubb on 2008-09-16
> **oilchangeguy said:**
> i do agree, however the op's hard drive probably has bad clusters. the chkdsk /f needs to be run.

Good call.  I shouldn't have missed that.

---

### Post by knifyspoony on 2008-09-17
I'm not sure how to run chkdsk because that's a microsoft command. I don't think I can defrag in ubuntu because I don't have a linux file system, just free space. Unless that's the same thing - I have no idea. After Googling around someone said to run 'e2fsk /dev/media' but I don't know what my media cards location is, so I'll run '/etc/fstab' in a minute. 

Right now I'm trying to backup Xp on one of my other computers. lol. 


'Ubuntu: Just put the disk in, boot up the disk and do a clean install. When you get to the part about disk partitioning, just select "guided, use entire disk"'

I tried booting for the cd last night and it didn't boot. I logged in to Ubuntu normally and it didn't even display the live cd in the drive.

---

### Post by NewJack on 2008-09-17
If you think it may be bad clusters, try Spin Rite from:

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

It's worth the $89 dollars.  Saved me a couple of times.

Or

Just use DBAN (as suggested previously) to nuke your drive and start from scratch.

---

### Post by Malac on 2008-09-17
If you can't boot from the LiveCD now it may be that you motherboard/disk controller is going down (i.e. breaking) these sort of erratic failures are a common symptom of hardware starting to fail.
 
If not that then get gparted LiveCD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and try that. You should be able to wipe the drive with that.

---

### Post by oilchangeguy on 2008-09-17
> **knifyspoony said:**
> I'm not sure how to run chkdsk because that's a microsoft command. I don't think I can defrag in ubuntu because I don't have a linux file system, just free space. Unless that's the same thing - I have no idea. After Googling around someone said to run 'e2fsk /dev/media' but I don't know what my media cards location is, so I'll run '/etc/fstab' in a minute. 

Right now I'm trying to backup Xp on one of my other computers. lol. 


'Ubuntu: Just put the disk in, boot up the disk and do a clean install. When you get to the part about disk partitioning, just select "guided, use entire disk"'

I tried booting for the cd last night and it didn't boot. I logged in to Ubuntu normally and it didn't even display the live cd in the drive.

read post #3. it tells you how to run the chkdsk /f command.

---

### Post by knifyspoony on 2008-09-17
> **oilchangeguy said:**
> read post #3. it tells you how to run the chkdsk /f command.

I have a bootleg copy of windows, during the install pressing 'r' for the recovery console didn't do anything.

---

### Post by Malac on 2008-09-17
> **knifyspoony said:**
> I have a bootleg copy of windows, during the install pressing 'r' for the recovery console didn't do anything.
That's probably what screwed your disk then. A lot of bootleg versions of XP especially early ones have rootkits/virus stuff built into them by the bootleggers which mess up several things especially as they are usually badly written so create hardware trouble.
If you want XP get a legitimate copy it's only a few quid / dollars on ebay (or other auction sites are available:) )

---

### Post by knifyspoony on 2008-09-17
> **NewJack said:**
> If you think it may be bad clusters, try Spin Rite from:

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

It's worth the $89 dollars.  Saved me a couple of times.

Or

Just use DBAN (as suggested previously) to nuke your drive and start from scratch.

Yeah, I'm going to try DBAN now. SpinRite looks really impressive - I'll think about it.

---

### Post by knifyspoony on 2008-09-17
> **Malac said:**
> If you can't boot from the LiveCD now it may be that you motherboard/disk controller is going down (i.e. breaking) these sort of erratic failures are a common symptom of hardware starting to fail.
 
If not that then get gparted LiveCD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and try that. You should be able to wipe the drive with that.

I have the gparted live cd. I also went to the forum on gparted but they couldn't help me. When DBAN finishes, I'll install whatever os works and try gparted again.

---

### Post by NewJack on 2008-09-17
Good luck!

---

