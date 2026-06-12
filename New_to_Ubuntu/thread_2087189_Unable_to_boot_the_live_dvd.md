---
title: "Unable to boot the live dvd"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by HarlanT on 2012-11-23
Hello Forum Community :)
I have done a search forums, and not finding the right answer... suggestions so forgive me if this is already covered somewhere, and guide me thus please.

I am having issues with installing:
Downloaded from Ubuntu site [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) the ISO to burn the CD
I burned the CD with Power ISO
Repeat this step again for both versions 12.04  and 12.10

Rather than install alongside, I am using a clean 500 gig drive.
Set my BIOS to boot from CD 1st, Drive 2nd
Insert CD then power cycle, and I get "Disk Boot Failure"
Both CD's verify fine against the file during burn.
I have searched the Ubuntu site for the check-sum (MD5, and other?) but did not locate this.
I decided to download the windows version installer, for 12.10 and then ran that, chose the drive I wanted Ubuntu on, it did a 2 hour download for the files, then gave a message of "Setup/ installation failure" setup will exit.

I figured it would take 3 or 4 hours to download, burn and install Ubuntu, and have become concerned now at 14 hours so far, and no progress.
I am certain I should have come here a lot earlier, and am only wishing to share the concern of how long it is taking to change from Windows to Ubuntu.

So I ask "What am I doing wrong?"

Any advice is appreciated.

Harlan

---

### Post by -kg- on 2012-11-23
OK, first things first:

> **HarlanT said:**
> I have searched the Ubuntu site for the check-sum (MD5, and other?) but did not locate this.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

That page contains all the hashs for the current (and some not so current) releases.

It sounds like you're doing it right.  Are you burning an .iso file to the disk, or copying the file to it?  You have to make sure you're burning the .iso...you should have numerous files and folders on the CD when you're done, not one big file.  (I have to ask; it's a common mistake)

Other than that, I can't conceive of a problem, short of a corrupted download.  Can your computer boot to a USB device?  If so, you could download Unetbootin and burn the .iso file to a flash drive.  It might be your Optical drive is going.  I've seen that happen, too.

---

### Post by coldraven on 2012-11-23
--kg- is correct. Most CD creation applications have an option to "Burn Image", that is what you must use.
Look here for md5sum and also torrent downloads, I find the torrent the fastest way to download.
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by HarlanT on 2012-11-23
Thank you KG and Coldraven
I have never used or compared MD5 hash before, and now I know how :)
that was the "Good" news
of all my downloads, the only 2 that matched were the WUBI.ee files, for 12.10 and 12.04
All of the rest of the ISO images were bad, so I have a download problem to solve here.
I had already felt the concern on the burner, and swapped to a new one. Then for grits I tried a burn on my oldest one... HP9100
Then I realized that many old burners can not burn to 700MB cd's so I have a few more coasters.
I am fairly sure I have a good burner, and no issues on burning an ISO to a cd, taking image and dumping files to the media. Still is a good question KG ty :)
It is 2 am ish now so in the morning Ill reset the modem and get a torrent program or try the new browser thing (Torch) that has torrent file capabilities already in it.
I even tested out the recommended software for burning the ISO files and that's pretty kewl to see a "Free" burner proggy.

Thank you for the support Gentlemen, some shut eye and a new attack tomorrow.
this is sorta important as I will be receiving a new Puter here shortly, and ... *choking* comes with that 8 thing on it. I have put off linux and Ubuntu far too long, but the new prepackaged OS stuff, just forces me to get off my duff finally and make the switch.
I'll report back success /failure as I go along.

Harlan

---

### Post by mastablasta on 2012-11-23
> **HarlanT said:**
> Thank you KG and Coldraven
I have never used or compared MD5 hash before, and now I know how :)
that was the "Good" news
of all my downloads, the only 2 that matched were the WUBI.ee files, for 12.10 and 12.04
All of the rest of the ISO images were bad, so I have a download problem to solve here.

That is a major problem. the easiest way to solve it is to use torrent to download the image. torrent will constantly check the md5sum during download. downloaded image has to be exactly the same as the one on server.
 
be carefull not to overwrite your current OS and run it live to test it out (see if all hardware is compatible) before installing it
 
> 
Thank you for the support Gentlemen, some shut eye and a new attack tomorrow.
this is sorta important as I will be receiving a new Puter here shortly, and ... *choking* comes with that 8 thing on it. I have put off linux and Ubuntu far too long, but the new prepackaged OS stuff, just forces me to get off my duff finally and make the switch.
I'll report back success /failure as I go along.
 
 
 another potential problem he rei sthat new win8 computers often come with secure boto enabled. apparently only 12.10 can be installed on those. you might also have to do separate bootpartition for UEFI boot: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by HarlanT on 2012-11-23
Thank you mastablasta for the wisdom, not to overwrite old OS....... but would that really be a loss??
I have backed all data up and disabled the storage drives to prevent data loss.
I have chosen a good drive to use for the install, once I get a DVD burnt I will disable the boot drive as well prior to doing the install.
I just checked my MD5 and am a happy chappy, rested up now, so will begin the burn again.
My hope is to respond here later "FROM" the new OS

*"another potential problem he rei sthat new win8 computers often come with secure boto enabled"*
May I ask you to elaborate on the secure boto enabled

In short I am hoping to install and test Ubuntu a little, prior to the arrival of the new PC.
I did some reading before deciding to go Ubuntu on the system I am getting and the install issues.
I will be receiving an ASUS CM6870 system in a few days, NVIDIA GeForce GT 630 version and wireless option. I can not use hardwire :( here so stuck with wireless for all my networking.
I am a power switch operator and even have a hard time with that (they keep moving it)
I was old time Cobal, Pascal, Basic, pre-floppy drive trained, worked in the hardware maintenance of the 70's-90's (Wang, Rexon, TI, systems) watched the birth of the 8080.... learned to maintain a knowledge of power switch technology and deny all else.

Please continue the thoughts you have, it is helpful for me to mentally prepare my steps to making this work. I admit to frustration of earlier linux releases and installs, each time running out of time to attain an effective and usable tool which needed yet further learning and tweaking to become a proper OS usable to work with. 
I am really hoping this Ubuntu release will "BE THE ONE" so I could put the other OS style to bed for good. That is my goal, so I am at the mercy of those who can hammer knowledge into me last living brain cell (miss-fires a lot)

Thank you Bunches and Muchly!! Everyone

Harlan

---

### Post by HarlanT on 2012-11-23
Progress!
ISO File has been burned to the DVD and it now boots the system.
I get the splash screen of it loading then
like a DOS screen, and the statement says:
Cannot find a media containing the LIVE FILE SYSTEM
I will go research the term and learn it.
.....next?

Harlan

---

### Post by Bashing-om on 2012-11-23
HarlanT; Great attitude !

Situation at hand: Are you attempting to dual boot with windows ? (grub installation ?)

Is your last in reference to  booting the install disk ? or ?

--
I also come from a similar background (but networking directed) ; I find this os the answer to all my dreams about a usable os -> but takes a bit of time to realize all the tools that are at my disposal.
[INDENT]wanting to help ==> BDQ

[/INDENT]

---

### Post by nothingspecial on 2012-11-23
Title change to reflect the problem.

---

### Post by HarlanT on 2012-11-23
> **Bashing-om said:**
> HarlanT; Great attitude !

Situation at hand: Are you attempting to dual boot with windows ? (grub installation ?)

Is your last in reference to  booting the install disk ? or ?

--
I also come from a similar background (but networking directed) ; I find this os the answer to all my dreams about a usable os -> but takes a bit of time to realize all the tools that are at my disposal.[INDENT]wanting to help ==> BDQ

[/INDENT]

Success on making the DVD finally, the ISO for 12.10  does not work on this system but the ISO for the 12.04 boots fine.
Just reporting back here, will proceed now with the install of 12.04 

ANSWER: To Bashing-OM, no to dual boot
I am keeping it Simple-Simon here and disabling all drives prior to installs, so that the only thing the BIOS see's is the DVD ROM and a blank  hard drive.
ANSWER: Also is yes to a dual boot, but not from a single drive, only a BIOS enacted dual boot. I will use the F8 Boot Menu key to choose the boot drive for now. I will determine how on the new system once it arrives..... probably use the same method if available.

One question in my mind is whether I need to have a partition on the subject drive, hoping that Ubuntu will see an available drive and do all partitioning and formatting, but... I am sure it will let me know what it wants now as I go along.


Now! A BIG thanks to all of you here, I chuckle at the need to be hand held a bit, and realize it is comforting :)

Thank you to the thread name change nothingspecial,  I will try to test further the 12.10 thingy for reasons I do not get a grub or desktop or menu or ......(things I have to learn about yet)
I will post that back as well to the solution
Now to go do the install here and report back from within the Ubuntu system.
*ponders* if only we could migrate an install to hardware upgrades. ie new system complete. yeah yeah was just a thought :)

Harlan

---

### Post by HarlanT on 2012-11-23
I am posting now from within the Ubuntu 12.04 desktop operating system.
Install went good, one report of reset volume control mixer (Failed)
I also have received two bubbles to report a system problem and so I have agreed to that but do not know what the issues are.
I guess it is time to mark this now as resolved, and later try to determine the issue with 12.10 not offering the menu during boot.

Thank you everyone for the help!!!
Happy Holidays also!!

Harlan

---

