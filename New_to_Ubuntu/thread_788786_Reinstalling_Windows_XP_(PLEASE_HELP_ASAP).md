---
title: "Reinstalling Windows XP (PLEASE HELP ASAP)"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by rfsquared on 2008-05-10
Hi all,

I have installed a copy of Hardy Heron on my PC...and I love it.  But the only problem is...I wasn't paying attention during the install and I deleted my whole Windows partition and dedicated my whole hard drive to Ubuntu.  And I really still need Windows as well.
That being said (and I'm sure this is a really dumb question), when I pop in my handy XP Professional CD, it says that there are no hard disk volumes detected on my computer.

I don't mind formatting my hard disk and reinstalling everything later.  The question is...what kind of reformatting do I need to do to get my computer to install XP?

---

### Post by Xiong Chiamiov on 2008-05-10
You'll need to resize your main linux partition, then format the new empty space as ntfs.  You can do this with gparted on the live cd.  If you try to do it while running Ubuntu, you'll get an error because you can't resize partitions while they are mounted.

After installing XP, you'll have to reinstall GRUB.  The easiest way I've found to do that is to use [SuperGRUBdisk]("http://supergrubdisk.org").

---

### Post by rfsquared on 2008-05-10
Ok well what if I want to just reformat the whole thing and start over?  Because honestly that's kind of what I want to do at this point...

---

### Post by ecrivain5 on 2008-05-10
as a newbie myself I have done the same thing yet when I booted from my XP disk again it worked fine on new install. I lost ubuntu true. But it was easy enough to reinstall afterwards. Incidentally. I have had to do this twice because of elementary errors by me and not found a problem.
I would suggest you try again with bios set to boot from cd. I have to say though that my boot cd is only sp1 so that could make a difference

---

### Post by rfsquared on 2008-05-10
Well, my copy of XP is an ISO that I downloaded through my university, so I don't really even know if it has an SP pre-loaded on it at all, although the ISO is brand new so I'm assuming it has at least SP2 on it, maybe 3.

But yeah...anyway, I just wanna reformat the whole thing.  When you put the CD in and restart the computer, it doesn't make you go into the BIOS.  It just pops up and says "to boot from CD press any key to continue."

Then, in the installation program itself, it says there's no hard disk.

---

### Post by HotShotDJ on 2008-05-10
Depending on what you do with Windows and the amount of RAM you have in your system, you might take this opportunity to try something a little different.  Rather than dual-booting, why don't you use [VirtualBox]("http://www.virtualbox.org") and create a Windows virtual machine.  That way, when you need Windows, you just point and click... no need to reboot.  I recommend using the version that you can download from Sun via the above link and NOT the version in the Ubuntu repositories.

---

### Post by theRightNee on 2008-05-10
> **HotShotDJ said:**
> Depending on what you do with Windows and the amount of RAM you have in your system, you might take this opportunity to try something a little different.  Rather than dual-booting, why don't you use [VirtualBox]("http://www.virtualbox.org") and create a Windows virtual machine.  That way, when you need Windows, you just point and click... no need to reboot.  I recommend using the version that you can download from Sun via the above link and NOT the version in the Ubuntu repositories.

or vmware! personally i enjoy vmware more because of 
1. vmware tools
2. 3D acceleration (not the greatest, but hey its a start)

also...
if you want to reinstall (just for clarificatioN)
1. download gparted live cd
2. boot using cd
3. after starting, edit partition (50/50, 60/20, your choice)
         note: do not worry of messing up, the program lines up your actions, and once you are satisfied, the real formatting begins
4. then install windows (you will see some unpartitioned space, or NTFS space, whatever you formatted the partion to)
5 you are good to dual boot

---

### Post by rfsquared on 2008-05-10
OK so:
-Got GParted
-Ran the Live CD
-Cut Down the size of my Linux partition
-Used the leftovers to create about a 90GB NTFS partition

When I tried to install XP this time, it STILL says I have no hard disks installed on this computer.


:confused:

HALP!

---

### Post by TeoBigusGeekus on 2008-05-10
Do you have SATA disks?

---

### Post by rfsquared on 2008-05-10
Yeah, I do.

Ok...here's the NEW Problem:

I have the drivers for my SATA hard disk that I downloaded from Compaq.  My NEW problem is that they come in EXE format, and I have to open the executable file to put them onto my external removable disk (in this case, my iPod which I'm using as a jump drive).

How do I open the EXE file to copy the drivers when I don't have access to Windows already?  And will my iPod work in place of a floppy diskette drive or will I have to go get one of those too?

---

### Post by TeoBigusGeekus on 2008-05-10
Install Wine (sudo apt-get install wine) and run the .exe with it. It should probably work - it will extract the drivers in a location of your choice.

As for the ipod, I think it depends on your BIOS. Give it a try anyway. If that doesn't work, I could tell you to download a bloated version of windows which has sata drivers preinstalled through torrents
[http://www.torrentz.com/search?q=windows+xp]("http://www.torrentz.com/search?q=windows+xp")
but I won't - it's illegal!

---

### Post by rfsquared on 2008-05-10
OK so...

NOW, I basically just want to have Windows XP back on my system.  I don't care about Ubuntu or anything else at this point, I'll worry about that later.

Anyway, the drivers at the beginning of the XP install seemed to work.  Setup installed the necessary files and, right as it was about to reboot, it said those same device driver files could NOT be copied to disk.  After retrying a couple times, I hit ESC to continue the install.

Now, the computer restarted and the XP screen started to load.  At this point, a blue screen of death popped up saying I had a critical error and that I probably had a virus on the machine and that I needed to uninstall all hard disk controllers, etc. and run CHKDSK and all that mess.

And I can't even get to Ubuntu anymore.  It automatically loads XP and ***** up everytime.  So my comp. is out of commission.

Anyway, wtf do I do now?  Like I said, PLEASE just help me get to XP even if that means I have to delete Ubuntu for the time being.

:confused:

---

### Post by HotShotDJ on 2008-05-10
> **rfsquared said:**
> Like I said, PLEASE just help me get to XP even if that means I have to delete Ubuntu for the time beingOk.  Not that I actually RECOMMEND this... :)

Use your Ubuntu installation CD to boot up. Run GParted on the unmounted harddrive.  Delete ALL partitions you find.  Remember, this deletes ALL the data... but I guess this is what you want.

DO NOT CREATE ANY PARTITIONS.  Just delete the ones that you find.  Shut down the computer.

Now, use your XP install disk and let it do the partitioning and formating.  If this doesn't work, then there is a problem with your XP installation disk (although I doubt that will be the case).

---

### Post by kansasnoob on 2008-05-10
You could have a memory resident virus which can truly reside in mem sticks, cpu's, and even the tiny mem bits of every chip on the mobo, hd, etc.

WARNING: If you don't know what you're doing DON"T do this!

At this point I'd try clearing the CMOS and restoring BIOS. Let's start by clearing the CMOS: try restarting and holding down the "delete" key (this works with about 80% of newer computers, and if it doesn't you need a technician).

That should clear the CMOS and bring you to BIOS. At that point you MUST have a BIOS setup disc for that mobo or a true OEM system recovery disc.

But, the odds of truly recovering from a mrv are about 50%!

---

### Post by cgarre on 2008-05-10
I presume you wont have floppy drive, in which case here is one procedure .. you might need some other laptop which has a cd writer and windows .. use this [http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml) it has some instructions. 

If you have a floppy drive then its much easier its instructions are here [http://www.raymond.cc/blog/archives/2008/01/21/install-xp-setup-did-not-find-any-hard-disk-drives-installed-in-your-computer/](http://www.raymond.cc/blog/archives/2008/01/21/install-xp-setup-did-not-find-any-hard-disk-drives-installed-in-your-computer/)

---

