---
title: "Partition and install questions"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by Three11s12 on 2012-05-03
Hello all! Long time person, first time poster.
 
Please let me know if I should create a completely new post for this, but it seems so closely related to this thread that I thought I'd try here first. I don't want to breach any etiquette.
 
Basically what I'm wondering is if someone would mind breaking it down for me even more. You won't offend me at all, as I'm a dual-boot/partitioning/formatting virgin, but I am actually about to do the exact same as Toporango: I have a laptop with Windows XP Home, and I made the decision to set up a dual boot with Ubuntu (latest release, I believe 12.04). I _do_ understand the basic concept of partitioning, and I have read just about every link on the first three pages of my Google results about it. The problem is that every resource about partitioning seems to assume a bit more knowledge of it than I have. What does it mean when someone says, "you'll want a /root partition," and similarly, "you'll want *x* GB in your /swap"? Are these terms that each user determines at the time of partitioning? Does it ask you what you want to name a partition, and you type in "/root" or does it say "Do you want to create a /root partition?"
 
Part of me is tempted to just go for it, and see where I get, but I'd like to have a gameplan before I begin. Also, I downloaded the latest Ubuntu version, and have saved it onto a jumpdrive. Do I need to do something special to this? Or can I just boot up my computer with the drive in the USB port, and it will ask me if I want to boot off of this drive? Do I need to "install" Ubuntu onto this memory stick?
 
Thanks in advance for your help, and again, please let me know if there is a more appropriate place for this post.
 
EDIT: I should maybe add that of the responses I've read so far, this is the set up I think I would like best:
Windows on one partition, with just as much space as is needed.
Ubuntu on one partition, with just as much space as is needed.
A "common space" on one partition (accesible to both OS's), with the bulk of my HD.
A space for trying future Linux flavors before more permanent install on one partition.
The "swap" thingy on one partition, with 2x RAM (would 3x be better? I think I only have 512 MB ram, it's an older machine, but I'm willing to spare the space, if it would help)
Anything that is NEEDED, but not already covered.

---

### Post by Bartender on 2012-05-03
Yeah, generally speaking you should start your own.  For instance, if the OP marks this post as "Solved" and you tag a question on the end, most people aren't gonna look.

It is good to have a gameplan :)

And insurance.  Do you have XP recovery discs?  And an external HDD for your personal data?  Did you write down or print out all your passwords, email addresses, etc.?

You say you "saved" the Ubuntu download to a thumb drive?  That won't work.  The Ubuntu download is an image, that has to be burned to a CD.  I've made a USB thumbdrive installer, but I had to boot from a CD first, then go into the menu and find the "Startup Disc Creator", then go thru the steps.  There are a couple of programs that will install the USB installer to a thumbdrive and download the Linux installer all in one shot, but I don't have any experience with those.  I found out that some flash drives don't work, so that's another potential problem.

Whether you use a CD or have created a USB flash drive installer, you still have to go into BIOS (or UEFI on a new PC) and tell the machine to boot from either the optical drive or USB.  Otherwise your PC will ignore the Ubuntu installer and go to Windows like usual.  Most PC's nowadays have a "Quick Boot" option during startup.  You tap on a key, you get a menu that asks what device you want to start from.  This is easier and faster than actually changing the Boot Order from within BIOS.

Setting up swap with 2X your physical RAM should be plenty AFAIK.

---

### Post by oldfred on 2012-05-03
Moved to your own thread. 
You have a few issues that are a lot different and as posted by Bartender it is better to have your own thread. Few look at solved threads.
For reference it was here which was just partitioning issues:
[http://ubuntuforums.org/showthread.php?t=1970636](http://ubuntuforums.org/showthread.php?t=1970636)

Did you install using the instructions here?
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Be sure to have good backups of all your data.

Boot from liveUSB or liveCD to test that it works on your system.
Some older systems have USB ports, but do not boot from them. Does your BIOS have an option to boot from USB?

USB is faster that CD, and hard drive will be faster still, but 512MB is pretty much the minimum for Ubuntu as it is a full fledged system with lots of features and larger applications. Xubuntu or Lubuntu may give a better experience.

---

### Post by chubble10 on 2012-05-03
> **Three11s12 said:**
> 
A "common space" on one partition (accesible to both OS's), with the bulk of my HD.

You can use the current XP partition as the "common space" as Ubuntu will happily read/write to Windows partitions. Note that Windows doesn't return the favour, and you are unable to read/write anything on the Ubuntu partition from inside Windows.

> **Three11s12 said:**
> 
A space for trying future Linux flavors before more permanent install on one partition.

If you are still unsure about what version of linux you want, you can do a temporary "wubi" install from within Windows without doing any partitioning whatsoever (it makes a virtual hard drive in your current Windows partition). This works with all flavours of Ubuntu, and you can uninstall it from the Windows add/remove programs screen just like any other app. (You can only have one wubi install at once though). See the [Wubi Documentation]("https://wiki.ubuntu.com/WubiGuide") for more info.

> **Three11s12 said:**
> 
Part of me is tempted to just go for it, and see where I get, but I'd like to have a gameplan before I begin.

If you're a bit nervous about choosing the partitions yourself, if you create an empty partition (unformatted or "unallocated space") that you want all the Ubuntu stuff in, then the Ubuntu installer normally detects the free space and automatically installs and makes all the neccesary extra partitions itself from this free space. You can make the "unallocated space" by using the [GParted liveCD]("http://gparted.sourceforge.net/livecd.php") - just burn it to a CD and boot up with the disc in your drive. Then resize your Windows partition to the size you want and the rest of the drive is automatically left as "unallocated space".

Hope this helps! ;)

---

### Post by oldfred on 2012-05-03
I have always partitioned in advance as I want to know what it is doing.

So just as an experiment I used the liveCD and just let it auto install. If found 40GB unallocated on my sdd drive, created sdd18 new partition in the extended partition and installed. I was a little surprised that it did install grub2's boot loader to that drive and not sda as it always used to.
So auto install to unallocated does work.

---

### Post by Three11s12 on 2012-05-04
_Couple of updates_

First and foremost:
I actually have 2GB ram (I JUST got laptop, so I don't have all specs memorized yet), so I'll proceed with Ubuntu, thank you for letting me know that might have been a problem, so I knew to check into it fully.

Second:
I'm thinking that I'll partition my HD from within Windows, before attempting the install, but some questions arise.  Namely, do I want the partition on which Ubuntu will reside to be a primary partition?  And does Ubuntu come with a boot manager?  Boot manager is a concept I don't QUITE understand, and when I started to get into the partitioning phase, the program mentioned that I can only boot an operating system if I have a boot manager installed.  I DON'T have one, unless Windows or Linux comes with one.  I'm assuming Linux does (because, as I understand, it's amazing).  What do I need to do regarding this area of my project?

Third - Other partitions:
Will Linux handle the additional partitions (i.e. swap [and what is the purpose of the swap partition], /home, /root, etc), and of what type should these be?  Primary, extended, or logical?

Fourth and (for now) final:
Based on my questions so far, do any of the more experienced users out there believe I should not be attempting this install on my own?  I tend to be overly cautious when doing something for the first time, and it can be hard to separate "over reacting" from "hesitance through wisdom" ;)

Thank you all for your help!

---

### Post by oldfred on 2012-05-04
Use Windows partitioning tools to shrink the Windows partition, but do not use it to create partitions. It will often create a Microsoft proprietary partition scheme it calls dynamic which is not compatible with Linux nor even some Windows tools.

Use gparted to create Linux partitions if you partition in advance.

Windows has a simple boot loader it installs to the MBR. All it does is transfer to the Windows partitions boot sector or PBR to find more boot code. Ubuntu's boot loader is grub2, but others can be used.

Computer boot by first loading BIOS which is on Motherboard. The BIOS transfers to the MBR or first sector of the boot drive and reads that code to continue to boot. Since MBR is only first sector it cannot have much code so grub2's boot loader find more boot code in the Ubuntu boot folder (or partition) and continues the booting process.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

A suggestion for partitioning, many have different as each user may have different needs. Even my own optimal partitioning is not so good a couple of years later.
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Three11s12 on 2012-05-04
Thank you so much OldFred!  I'm busy reading that partitioning tutorial and I can already tell it's going to help immensely.  I'm going to mark this thread as Solved, but I reserve the right to ask more questions! Lol. 

Wish me luck!

---

### Post by oldfred on 2012-05-05
The space I suggest for Linux does not include other partitions such as the shared NTFS data or other partitions you may want. I am up to 18 partitions on my 640GB drive but most are 25G / installs of older or testing version of Ubuntu. Since I still have unallocated I just create another. Soon I will have to houseclean and start reusing some of them.

If you have a separate NTFS shared data partition, you may need less space in /home or you can combine it in / (root) and not have it separate. /home does two things. It has your hidden user configuration files and your data files some hidden and most just data folders like Music, Documents etc. 

If you have all your data, but not settings in other partitions /home is tiny, mine is about 1GB and I keep it in / (root) but have data in two 100GB data partitions, one NTFS from back when I dual booted with Windows and most data now in a ext3 partition. I consider splitting /home more advanced as you have to mount the data partitions, link folders back and modify fstab to permanently mount.

---

### Post by Three11s12 on 2012-05-05
I think I understand.

So, further update:

I ran into a snag last night. Around about hour 6 (or 7) I installed 12.04.  Let me recap.

System:
1. HD - 160GB
2. RAM - 2GB
3. Proc - 1.73 Ghz "Genuine Intel"
4. Let me know if any other specs would help

Actions:
1. Using Acronis I resized my Windows primary partition to around 30GB.
2. I restarted and booted into Ubuntu from the liveCD using "Try Ubuntu"
3. I found and ran GPartEd (which I like more than Acronis...and it's free!  I'm going to love Linux!!!)
4. At this point I had 29.98GB Primary partition, and 117.7 Unallocated.
5. I created an extended partition. (I'll let you know when I hit Apply and ACTUALLY made the following changes)  This was 109 or so GB (I left about 8GB because I read somewhere that windows uses unallocated space, and I should leave some for it.)
6. I created a logical ext4 partition of around 20GB (Thinking this is where I would install Linux)
7. I created a logical NTFS partition of around 10GB (shared "folder" for windows/linux use)
8. I created a logical ext4 partition of about 75GB that I intended for /home.
9. I created a linux-swap logical partition (4.29 GB) and actually used the linux-swap flag.
10.  After about 10-15 mins of reviewing to make sure I was sure about it, I applied the changes.
11. I then clicked on Install Ubuntu 12.04 LTS from the "temporary" Linux workspace.
12. It began doing its thing and about 30 mins later (give or take, I wasn't looking at a clock at this point as it was almost 3 and I was tired) it rebooted into Linux.
13.  During the install it asked how I wanted to install: "Alongside Windows", "Replace Windows", "Other".  I chose alongside windows.
14.  The trouble is, I don't know linux well enough to figure out from within it where anything is installed, which partitions etc, and from within windows, obviously I can't see anything except the two NTFS partitions.
_Sidenote:_
I do notice that the unallocated space I left at the beginning of the process has shrunk to about 800 MB, but it didn't create any additional partitions, so I don't know where it allocated that space.

Very frustrated!!!  Any help you can give would possibly save me ANOTHER 6-7 hours of sorting this out.  I'm thinking I should have selected "Other" instead of "Alongside Windows", because I'm betting it would have let me choose on which partitions to install the various components.

---

### Post by oldfred on 2012-05-05
If you manually partition you have to manually install or Something else. All the auto install options either find unallocated and use that or auto shrink Windows and install. 

If you auto installed it may have just created new partitions, not using any of the partitions you created.

Post this from liveCD:

sudo fdisk -lu

or screenshot from gparted.

---

### Post by Three11s12 on 2012-05-05
Screen Shot of GParted




I now want to uninstall and reinstall Ubuntu, but I can't even figure out how to do that  :(

---

### Post by Three11s12 on 2012-05-05
Ugh, image didn't show.  I keep getting an "Invalid File" error when I try to Upload my screen shot.  I simply hit Prnt Scrn and saved the image.  But I get the invalid file message upon Upload.

---

### Post by Three11s12 on 2012-05-05
So here is my screen shot.

Ok, I got it to work.  Now, is uninstall/reinstall my best option from here?

---

### Post by Toporagno on 2012-05-05
I don't know what the best option would be, but you could always delete the extended partition (that would delete your Ubuntu installation as well) and do the process of partitioning again. Then when you go to install Ubuntu you should choose Other, it will let you choose in which partition you would put root, swap and home. In the GUI you will find a drop-down menu with the /, swap and /home alongside many others.

---

### Post by Three11s12 on 2012-05-05
Ok, that is what I was basically thinking, but I didn't know it was that "simple".  I'll do that now!

---

### Post by oldfred on 2012-05-05
You only have to delete the install partition and expand the nearest partition in to the unallocated space. You may have to move swap first.

From liveCD so partitions are not mount, plus you have to click on swap and right click swap off to unmount swap. LiveCDs like to use swap if found to speed up activities.

Then use manual install.

---

### Post by Three11s12 on 2012-05-05
Success!!! Thanks for your help!  I'm so geeked right now, I'm off to play with it!

Thanks again!

---

