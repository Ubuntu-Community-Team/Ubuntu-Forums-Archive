---
title: "How do I format a WD Passport HD (more)"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by BlackWolfe on 2012-07-05
Firstly, I'm a complete noob. I don't even really know what "grub" is, etc. I'm an old-school DOS/Windows user so go easy on me please. ;)

I want to format a Western Digital My Passport drive that currently has Ubuntu 11.10 on it. This is the drive that I have had Ubuntu on from the beginning, and I have had numerous problems after updating it to Ubuntu 12.04 LST. I first updated 11.10 on the drive online and when I rebooted everything went south. I tried updating it from a LiveCD but no go. I'm wondering whether or not some if not all of my problems are with old partitions/installs, SO, what I want to do is wipe this HD as thoroughly as possible to get it all "shiny and new" so to speak, and then try a straight-up clean install from a LiveCD and see if that works. Working from a LiveCD isn't what I need at this point, hence wanting to get it working from the HD. How do I do this running from a LiveCD?

BTW: I have another thread that pertains to this, but it isn't about formatting. I'm assuming that I should mark it solved but I need to know that from someone before I do.

Your help is greatly appreciated.

---

### Post by ajgreeny on 2012-07-05
Assuming you have already backed up all files you need from the now broken 11.10 installation, you can just choose to "use whole disk" at the new installation disk partitioning/preparation stage.  That will wipe everything that is currently on the disk and put the new OS in its place.

---

### Post by BlackWolfe on 2012-07-05
> **ajgreeny said:**
> Assuming you have already backed up all files you need from the now broken 11.10 installation, you can just choose to "use whole disk" at the new installation disk partitioning/preparation stage.  That will wipe everything that is currently on the disk and put the new OS in its place.


Thanks. I tried that though, twice. All I kept getting were two errors:

12.04 install error was:

[COLOR=Red]kernel not loaded
grub:[/COLOR]

11.10 install error was:

[COLOR=Red]error: file not found
grub rescue: [/COLOR]


Again, I really don't understand very much about the whole 'grub' outlay. Both of these errors occurred after the BIOS had gone through it's processes, and I've seen no indication that the BIOS has anything to do with the boot problems. Any ideas?

Again, thanks ahead of time.

---

### Post by NikTh on 2012-07-05
Try these 

1) Boot from LiveCD and have your HDD WD plugged in. 

2) Hit Install Ubuntu 

3) Hit something else 

4)[COLOR=Red] Careful here[/COLOR] : find your HDD WD and delete . Do not do anything if you are not sure that this is the correct disk . Break here if you are unsure. 

5) Create a new filesystem ext4 in your HDD WD and mount it with / (root) . Leave some space 4000MB

6) mount the 4000MB space with swap 

7)Check down and expand "grub install to: " and select your HDD WD . If assume that your WD is /dev/sdb then grub must installed to /dev/sdb NOT /dev/sdb1 .

**Tip: **you can recognize WD HDD from size . Sizes in Ubuntu installer are in MB's . If your disk is 500GB you will see something like.. 499990MB of space. 
Also ext.drives usually are with letters like /dev/sdb or /deb/sdc . Usually dev/sda is your first internal drive.

---

### Post by BlackWolfe on 2012-07-05
> **NikTh said:**
> Try these 

1) Boot from LiveCD and have your HDD WD plugged in. 

2) Hit Install Ubuntu 

3) Hit something else 

4)[COLOR=Red] Careful here[/COLOR] : find your HDD WD and delete . Do not do anything if you are not sure that this is the correct disk . Break here if you are unsure. 

5) Create a new filesystem ext4 in your HDD WD and mount it with / (root) . Leave some space 4000MB

6) mount the 4000MB space with swap 

7)Check down and expand "grub install to: " and select your HDD WD . If assume that your WD is /dev/sdb then grub must installed to /dev/sdb NOT /dev/sdb1 .

**Tip: **you can recognize WD HDD from size . Sizes in Ubuntu installer are in MB's . If your disk is 500GB you will see something like.. 499990MB of space. 
Also ext.drives usually are with letters like /dev/sdb or /deb/sdc . Usually dev/sda is your first internal drive.


Okay, I started the steps, but whether you mean to "dismount or safe remove" the drive or if you mean for me to "open up the drive and erase everything on it by selecting all and moving to the trash", it will not let me delete even one file from the drive. I'm assuming this is because they are system files from the LiveCD that I am running right now. Is there any Ubuntu program that you know of that will allow me to format the HD and get rid of everything? I can do so on another system I have running Windows XP, but it will only format in NTFS, not FAT. I can remove the partitions only on that computer as well if that would help. Man I'm lost. *ugh*

---

### Post by NikTh on 2012-07-05
Ok. Forget those steps.. are little advanced.. 

Do this..
 from liveCD click Dash(dash=the ubuntu icon up-left) and write **Disk **open **Disk Utility** and you will see there your WD . Click on it and then Unmount > Delete > Create and choose ext4 . 
**Again **, [COLOR=Red]Be Careful [/COLOR]what disk you will erase.. this will erase EVERYTHING . 

After creation of file-system complete you can choose this HDD (WD) to do your Ubuntu install.

---

### Post by BlackWolfe on 2012-07-05
> **NikTh said:**
> Ok. Forget those steps.. are little advanced.. 

Do this..
 from liveCD click Dash(dash=the ubuntu icon up-left) and write **Disk **open **Disk Utility** and you will see there your WD . Click on it and then Unmount > Delete > Create and choose ext4 . 
**Again **, [COLOR=Red]Be Careful [/COLOR]what disk you will erase.. this will erase EVERYTHING . 

After creation of file-system complete you can choose this HDD (WD) to do your Ubuntu install.

Followed your instructions. Just did the install. On reboot I get this:

error: invalid extent
grub rescue:


I have no idea what that means, or what I may have done wrong. Any advice is greatly appreciated, as is your help from the beginning.

---

### Post by NikTh on 2012-07-06
Why you marked thread as solved ? Untick it.. solved threads have not much traffic. ;)

Boot from a LiveCD and follow these instructions [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) i hope this will solve your boot problem.

---

### Post by BlackWolfe on 2012-07-06
> **NikTh said:**
> Why you marked thread as solved ? Untick it.. solved threads have not much traffic. ;)

Boot from a LiveCD and follow these instructions [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) i hope this will solve your boot problem.

Yeah kinda figured that. ;)  I managed to format the drive just fine. Then it came up and gave me a whole different set of problems and I didn't know if using the same thread would work or if starting a new one would be the way to go. Thanks a ton for the new advice, I'm going to give it a shot and see what happens. Kinda frustrating that Ubuntu 11.whatever was running fine for me every time Windows XP gave me the digital finger, and then suddenly Ubuntu joined in. Think your advice here might just do the trick though, so thank you again. Have a great weekend!  :cool:

---

### Post by BlackWolfe on 2012-07-06
> **NikTh said:**
> Why you marked thread as solved ? Untick it.. solved threads have not much traffic. ;)

Boot from a LiveCD and follow these instructions [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) i hope this will solve your boot problem.

You, Sir, are  a steely-eyed missile man! :D
So far everything is working just fine. 
A thousand thanks for putting a weeks worth of frustration to rest! 
Have a killer weekend! You RAWK! :guitar:

---

### Post by NikTh on 2012-07-06
Glad it worked ! 
Now its the time to** mark thread as solved** ;)

---

### Post by BlackWolfe on 2012-07-08
> **NikTh said:**
> Why you marked thread as solved ? Untick it.. solved threads have not much traffic. ;)

Boot from a LiveCD and follow these instructions [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) i hope this will solve your boot problem.

Okay, it seems to boot "okay" most of the time, though some times I have to resort to banging on the space bar to get it started. I have a WD 2.5 TB External that I use to back up everything (I record music so I need the space). If I dock that for use while I'm using Ubuntu, should I un-dock it and unplug it when I shutdown? Or is it okay to unplug it while my system is off, and then reboot without the external plugged in? Someone mentioned something in another thread about MBR problems, and I was wondering if that could have something to do with my booting issues.

---

### Post by NikTh on 2012-07-08
This is a special case of Ubuntu installation. Its on External HDD and its not the same as Internal. When your system boots the external drive do not load as quick as internal , so you must wait few second for the drive to be ready and then you can boot in it. 

I am not sure but , i don't think that you will have problems if you leave the disk docked . If you unplugged and boot your system i don't know if you will be able to start any OS.. check it out and if you are , then you can do anything please you . I don't know and i never heard about MBR problems in this case.

---

### Post by BlackWolfe on 2012-07-09
> **NikTh said:**
> This is a special case of Ubuntu installation. Its on External HDD and its not the same as Internal. When your system boots the external drive do not load as quick as internal , so you must wait few second for the drive to be ready and then you can boot in it. 

I am not sure but , i don't think that you will have problems if you leave the disk docked . If you unplugged and boot your system i don't know if you will be able to start any OS.. check it out and if you are , then you can do anything please you . I don't know and i never heard about MBR problems in this case.

Okay, gotcha on the External drive installation stuff, makes sense. I let it update to 12.04, and it rebooted just fine 3 times (haven't done a shutdown yet, have some things to make sure I get done online before I take THAT leap). Here's the rub though, when I plugged in the 2.5 TB external drive, everything stopped. The keyboard stopped working, all of the "interface" disappeared on me, only the mouse still worked. I let it sit there for 20 minutes, just to make sure that it wasn't just a large drive read interrupting or something like that. Nope, just stopped. I rebooted and got yet another booting error, but I couldn't catch it in time after I pressed the space bar (a trick that seems to work most of the time btw with all the issues I've had) because it booted right up, the large external hard drive is docked and available. I'm at a loss as to what the deal was, and every indication says 'will be'. Again, I'm wondering if Ubuntu lays some kind of information on other drives, external USB or otherwise, that would cause it to lock up or get all weird. I know it's not Windows, yet I know that Windows does that crap and it messes with you if you unplug any drives, etc.

---

### Post by Kain000 on 2012-07-10
If you are still having issues I would try a drastic wipe, re partition and re-install.


Deriks boot and nuke for the win.

search google for DBAN, (i'd give you a link but i'm in Afghan right now so most download and software sites are blocked)

-burn the ISO file to a blank cd

-reboot your computer and boot from the cd (with the usb drive attached)

-once DBAN begins READ THE INFORMATION CAREFULLY!!!   configure it to errase your WD passport drive and ONLY that drive, with the level data errasure you would like.  (the default DOD wipe is usually sufficent) 

-go our or dinner and a movie (this takes a WHILE) lol

-once complete, remove the cd, insert the live usb or disk you use to install ubuntu and boot from it

-once in the ubuntu live os, open the dash (pop up menu on the left, or just hit the windows key on the keyboard) and search for a program called gparted  (type usb or dive and it will come up)

-Use gparted to format your WD disk to ext3 (to be safe) 

-After that you can finally install the os to the now readable WD drive, it should take care of the rest (swap partitions data partations and master boot record/flag) if not let me know and I can walk you thru it. 

happy linuxing! :)
-sean

---

### Post by BlackWolfe on 2012-07-15
> **Kain000 said:**
> If you are still having issues I would try a drastic wipe, re partition and re-install.


Deriks boot and nuke for the win.

search google for DBAN, (i'd give you a link but i'm in Afghan right now so most download and software sites are blocked)

-burn the ISO file to a blank cd

-reboot your computer and boot from the cd (with the usb drive attached)

-once DBAN begins READ THE INFORMATION CAREFULLY!!!   configure it to errase your WD passport drive and ONLY that drive, with the level data errasure you would like.  (the default DOD wipe is usually sufficent) 

-go our or dinner and a movie (this takes a WHILE) lol

-once complete, remove the cd, insert the live usb or disk you use to install ubuntu and boot from it

-once in the ubuntu live os, open the dash (pop up menu on the left, or just hit the windows key on the keyboard) and search for a program called gparted  (type usb or dive and it will come up)

-Use gparted to format your WD disk to ext3 (to be safe) 

-After that you can finally install the os to the now readable WD drive, it should take care of the rest (swap partitions data partations and master boot record/flag) if not let me know and I can walk you thru it. 

happy linuxing! :)
-sean

Ruling. \m/ I'll give that a shot once I back-up everything. I have a strange theory by the way about this. I'm almost certain that there is something wrong with my MB, that it is failing and/or fails and then reconnects (weird I know) so I'm saving the $$$ for a new one. HERE'S the kicker: It appears that the only time I have problems with booting up from the Passport drive (doesn't matter if I have any other External drives plugged in) is after the Clock has changed to the next DAY. It's like once it goes past midnight on my PCs internal clock, everything goes FUBAR. Anyway, thanks a ton for all your help and advice. I'm going to wipe the thing DOD style and format as you said and then see where we get. Take care! BW O:)

---

### Post by BlackWolfe on 2012-07-19
> **Kain000 said:**
> If you are still having issues I would try a drastic wipe, re partition and re-install.


Deriks boot and nuke for the win.

search google for DBAN, (i'd give you a link but i'm in Afghan right now so most download and software sites are blocked)

-burn the ISO file to a blank cd

-reboot your computer and boot from the cd (with the usb drive attached)

-once DBAN begins READ THE INFORMATION CAREFULLY!!!   configure it to errase your WD passport drive and ONLY that drive, with the level data errasure you would like.  (the default DOD wipe is usually sufficent) 

-go our or dinner and a movie (this takes a WHILE) lol

-once complete, remove the cd, insert the live usb or disk you use to install ubuntu and boot from it

-once in the ubuntu live os, open the dash (pop up menu on the left, or just hit the windows key on the keyboard) and search for a program called gparted  (type usb or dive and it will come up)

-Use gparted to format your WD disk to ext3 (to be safe) 

-After that you can finally install the os to the now readable WD drive, it should take care of the rest (swap partitions data partations and master boot record/flag) if not let me know and I can walk you thru it. 

happy linuxing! :)
-sean

UPDATE AND NEW PROBLEM: 
Followed your instructions to the letter. Now everything boots up just fine, but almost every time I boot up, the mouse freezes. I'm looking into mouse freezing around here but wanted to post this update and see if there were any 'new' issues with mouse freezing with Ubuntu 12.04

I'm using a Logitech track-ball mouse, and even Windows always managed to make it work, so...........????? 

Thanks!

---

### Post by BlackWolfe on 2012-07-26
Going to mark this one as SOLVED, since apparently the problems I'm having now with my Logitech mouse don't fall under this thread. No big deal. THANK YOU to ALL who helped me get this far.
 You ALL :guitar: !!!!! \m/

---

