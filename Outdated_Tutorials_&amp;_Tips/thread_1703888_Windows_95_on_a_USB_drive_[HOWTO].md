---
title: "Windows 95 on a USB drive [HOWTO]"
date: 2011-03-09
forum: Outdated Tutorials &amp; Tips
---

### Post by ?#Yhf%*&amp; on 2011-03-09
I had originally posted this on [MacRumors]("http://forums.macrumors.com/showthread.php?t=1091019"), but I thought I would post an Ubuntu version of it here:

[CENTER]**[SIZE=5]Windows 95 on a USB drive[/SIZE]**
Create a fully bootable Windows 95 installation, bootable on most modern computers
Requires Ubuntu ([Windows How-To available here]("http://forums.macrumors.com/showthread.php?t=1091019"))
[/CENTER]

**Part 1: Getting Everything**
You must have:
1. A CD of MS-DOS 6.22 ([Brought to you by AllBootDisks.com!]("http://www.allbootdisks.com/download/iso.html")) ([link]("http://www.allbootdisks.com/downloads/ISO/AllBootDisks_ISO_Image_Downloads25/DOS6.22_bootdisk.iso"))
_You can use a different version, but 6.22 is recommended._
2. A CD of Windows 95 (legally obtained, of course)
3. A blank CD
4. A USB drive from 256 MB to 2 GB (You can use larger drives if you partition it, FAT only supports up to 2GB partitions).
5. A computer capable of booting from a USB drive. Most computers made in the past 10 years can boot from a USB drive, it's just a matter of knowing how.

[B]Part 2: Creating a MS-DOS 6.22 CD
[/B]_To make the USB drive bootable, we need to use tools FORMAT and SYS in MS-DOS 6.22._
1. Launch Brasero Disk Burner. It should have come with your Ubuntu install.
2. Select "Burn Image".
3. Under "Select a disk image to write", click the button and locate the MS-DOS 6.22 image you should have downloaded in Part 1.
4. Select the CD to burn it to and start burning.
5. After it's done, simply close Brasero.

**Part 3: Formatting your USB drive**
_Now you have to format your USB drive as FAT16. Once you format it, MS-DOS can recognize the volume and format it._
1. Open the Disk Utility, found in the System application category.
2. Under "Devices" select your USB drive.
3. Select Format Volume.
4. Select FAT and enter a label.
5. Click Start. If it gives you an alert, just continue.

You can now try to boot your computer from your blank CD. There are  about a thousand ways to do this, so just try Google. If you see  C:\>, then it has successfully booted.

**Part 4: Making your USB drive bootable**
1. Boot from your MS-DOS CD.
2. Determine what drive letter is your USB drive (e.g. - C:  ). If you don't know, type **C:** and push ENTER.
3. At **C:>\**, type **FORMAT C:** and press ENTER.
4. It will ask you if you want to continue. Just push Y.
5. When it is done, type** SYS C:** and press ENTER.
6. When that's done, you can shut your computer down.

You can now try to boot your computer from your USB drive. There are  about a thousand ways to do this, so just try Google. If you see  C:\>, then it has successfully booted.

**Part 5: Copying Windows 95 files**
_Here you can boot back into good Ubuntu. ;)_
1. Insert your Windows 95 CD into your computer.
2. Make a new folder on your USB drive called, "WIN95".
3. Copy all of the files from your Windows 95 CD to the WIN95 folder on your USB drive. Make sure one of the files is SETUP.EXE.

**Part 6: Installing Windows**
1. Boot your computer from your USB drive again.
2. When you see C:>\, type: **CD WIN95** and press ENTER.
3. Type: **SETUP** and press ENTER.
4. Just go through the setup as normal, when it's done, just restart. Make sure your computer boots from USB when it restarts.

Sometimes when your start Windows 95, it may give you an alert that you  have not enough memory when you actually have too much. Read on for the  fix.

**Part 6: Fixing Windows 95.............argh.......**
I will post this later.... 

This might have a couple of errors, I am still working on it. Feel free to comment! :P
[RIGHT]Last Edited: July 24, 2011
[/RIGHT]

---

### Post by Quadunit404 on 2011-03-09
Woah, start me up, man!

I wonder how fast Windows 95 will run on a 2.53GHz Core i5 :lolflag: I'll have to try this the next time I get a USB drive :lol: (getting a 4GB one to replace a 2GB one I use for portable apps and stuff like that for my 18th b-day next month so when that happens I'll have a free USB drive to try this experiment on :D)

---

### Post by ?#Yhf%*&amp; on 2011-03-09
> **Quadunit404 said:**
> Woah, start me up, man!

I wonder how fast Windows 95 will run on a 2.53GHz Core i5 :lolflag: I'll have to try this the next time I get a USB drive :lol: (getting a 4GB one to replace a 2GB one I use for portable apps and stuff like that for my 18th b-day next month so when that happens I'll have a free USB drive to try this experiment on :D)

Thanks - Oh, by the way, I just looked up the "Start Me up" ad on YouTube. I still like the screaming Windows 1.0 and Win XP commercials more, though,

It will only work with drives over 2 GB if yo have a 2 GB or lower partition on it. For example:

Partition #1: FAT16 - Windows 95 Stuff
Partition #2: FAT32 - Other Stuff

Windows 95 can regconize FAT32 partitions, it just can't boot from them. From my knowledge. :confused:

---

### Post by Quadunit404 on 2011-03-09
I used to have Windows 95 and tbh would love to use it on real hardware again, or better yet, real hardware that's easily 15 billion times more powerful than what I ran Win95 on back in the '90s :lolflag:

And the Windows 1.0 commercial... best, commercial, ever. [s]CAN YOU BELIEVE IT?! WINDOWS 1.0 HAS REVERSI!!! Except in Nebraska! :o[/s]

---

### Post by ?#Yhf%*&amp; on 2011-03-09
> **Quadunit404 said:**
> I used to have Windows 95 and tbh would love to use it on real hardware again, or better yet, real hardware that's easily 15 billion times more powerful than what I ran Win95 on back in the '90s :lolflag:

And the Windows 1.0 commercial... best, commercial, ever. [s]CAN YOU BELIEVE IT?! WINDOWS 1.0 HAS REVERSI!!! Except in Nebraska! :o[/s]

I tried it on my Dad's Toshiba NB205 netbook, and it rocks so hard. It starts up in like 8 seconds and is much more responsive than the XP crap on that machine. I only use Notepad and DOS game emulators, but it runs all of them extremely well.

The only catch was that at first it gave me an error that there was not enough memory, when there was actually to much (1 GB). I looked up and all it took was editing adding a line in the system.ini file and it started normal. Apparently it limits Windows' memory to about 700 MB, but that's the equivalent of about 4 GB of memory in Ubuntu.

I'll try to add that to the tutorial tomorrow.

---

### Post by reverenddave on 2011-03-12
> **Quadunit404 said:**
> 
_**my 18th b-day next month**_ 

> **Quadunit404 said:**
> [U][B]real hardware that's easily 15 billion times more powerful than what I ran Win95 on back in the '90s 
[/B][/U] [/s]


you've been using computers since you were 3-4 years old ????????

HHHHHHHHMMMMMMMMMM

---

### Post by reverenddave on 2011-03-12
is it possible to create a bootable USB disk with the likes of Vista or even XP ????????

i need to run either one of these for some college software

---

### Post by Quadunit404 on 2011-03-12
> **reverenddave said:**
> you've been using computers since you were 3-4 years old ????????

HHHHHHHHMMMMMMMMMM

Yes, actually, my first PC ran MS-DOS (couldn't actually do anything with it though :lol:)

---

### Post by cblnchat on 2011-03-23
omg thanks for posting this!  I really look forward to doing this when i get a usb optical drive for my netbook!
Ive only been using computers seriously for the last 4 or 5 years so i never got a chance to see older stuff like this!

---

### Post by Sef on 2011-03-23
Moved to T n T.

---

### Post by blueturtl on 2011-03-23
If I'm not mistaken you could use FAT32 if you have Windows 95 B or C (OSR 2 and later) and thus use a memory as large as 32 GiB. Windows 95 will crap out if you have more than 512 MiB of RAM. Also the default memory management is poor. Use Cacheman 4.1 to fix that. Opera 10.1 is the latest modern web browser that will run on Win95.

If you want to supplement your guide with any of this I'll gladle supply you with all my files and knowledge (still running 95 on one rig here). :)

---

### Post by ?#Yhf%*&amp; on 2011-07-23
> **reverenddave said:**
> is it possible to create a bootable USB disk with the likes of Vista or even XP ????????

i need to run either one of these for some college software

Sorry, I forgot about this thread.

No you cannot. This tutorial reuqires that you use a version of Windows based on MS-DOS. These include Windows 1.0, 2.0, 3.0, 95. 98, and ME. XP or later does not work. :( But there are tools that let you make bootable installs of XP, Vista, or 7. Try this: [http://en.wikipedia.org/wiki/WinBuilder](http://en.wikipedia.org/wiki/WinBuilder)

---

### Post by ?#Yhf%*&amp; on 2011-07-23
> **blueturtl said:**
> If I'm not mistaken you could use FAT32 if you  have Windows 95 B or C (OSR 2 and later) and thus use a memory as large  as 32 GiB. Windows 95 will crap out if you have more than 512 MiB of  RAM. Also the default memory management is poor. Use Cacheman 4.1 to fix  that. Opera 10.1 is the latest modern web browser that will run on  Win95.

If you want to supplement your guide with any of this I'll gladly supply  you with all my files and knowledge (still running 95 on one rig here).  :smile:

Thanks for the info. Yes, Windows 95 supports FAT32, but the HP  Format Tool won't let you format it as FAT32 (it says DOS won't support  it, even though it does). And to fix the RAM problem, you can trick  Windows into thinking it has ~700 MB of RAM. Read about it here:  [http://support.microsoft.com/kb/q253912/](http://support.microsoft.com/kb/q253912/)

And instead of Windows  95, you could use this same guide to install Windows 98, 98SE, or ME  instead. With ME you could run Firefox 2.0.0.20, or with unofficial  builds, 3.x. :razz:

---

