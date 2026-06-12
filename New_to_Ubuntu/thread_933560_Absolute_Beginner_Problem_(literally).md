---
title: "Absolute Beginner Problem (literally)"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Fingbut on 2008-09-29
Ok I apologize in advance if this is a little too absolute beginner talk but I've been having some issues with getting Ubuntu running in the gui. I am trying to install as a dual operating system with windows XP, I have tried installing within windows and from the read only Ubuntu CD boot thing. However, in both cases it hasn't worked. 

When booting from the cd and installing from that I have issues with the partitioning menu(step 4/7), it always comes up blank. I have tried loading with unpartitioned space and a couple of other things but it doesn't seem to work.

When installing from Windows everything seems to run fine until I reset and when trying to open Ubuntu (I assume) it loads up a dos like linux tool that I am unable to use.

I have checked the quality of my burnt cd and have copied it at low speed with as few errors as possible. I have tried a few other things but didn't want to write a huge post (too late!)


I have found lots of similar issues in forums so if anyone has a link with good instructions that'd be awesome but I've looked for a while with no luck. 

Any help is much appreciated. 



_Update:_

I have defragged my primary HD and tried reinstalling. I also updated my Bios and am certain that the linux Kernel works with my system. I have tried Gparted (thx lowsky and shoot2kill) and it cannot detect any devices, I have found similar issues on the forum but they seem to relate to certain PC's (mostly Dell) and I built this one. 

Details:

Ubuntu Version 8.04 Desktop 64bit

PC Spec

AMD 3500 64bit
1GB Kingston RAM
(ASUS mobo and graphics)

---

### Post by malachi1990 on 2008-09-29
I haad a similar problem, which I solved by redownloading the ubuntu iso file and burning a new cd after checking the md5sum, to make sure I had a match.  You can probably download an md5sum checker by doing a google search.

Make sure to use an iso burner, as well, as simple extraction doesn't always work.  

You can also try a 32 bit version, though I don't know how to get one of those working on a 64 bit system.

Hope this helps.

---

### Post by LowSky on 2008-09-29
Ok a few things

1. Are you using one hard drive for both Operating systems?
A. If Yes see 2.
B. If No see 3.
2. Have you done a disk defragment from Windows? Is there enough space on the hard drive ( 2-4GB is a normal install)? 
3. Set the drive you wish to install Ubuntu on as the Boot Drive.
4. Have you tried a 32 bit version of Ubuntu?
5. Try using Gnome Partitioner (GParted) from the Ubutnu LiveCD

---

### Post by shoot2kill on 2008-09-29
what i usually do when setting up a dual boot.

boot to the live cd
[ALT + F2] type in 'sudo gparted'
partition the HDD through this program, giving me my required space for ubuntu, and 2GB for my swap (double my RAM)
then run the installer, and select the newly formatted (ext3) partition for ubuntu to install..

please let us know if your problems are not resolved by this method..

ALSO, im sure you know to back up all ur data from ur MS partition before trying install a new OS...

---

### Post by DrMega on 2008-09-29
> **malachi1990 said:**
> You can also try a 32 bit version, though I don't know how to get one of those working on a 64 bit system.

The 32 bit one should work fine on a 64 bit system, it just means it isn't optimised for 64bit.

---

### Post by gnuvistawouldbecool on 2008-09-29
Some idea of what it says when you install from windows on reboot could be useful.  Also, is this after it actually installs, or when it restarts to do the main install, ie has it until then only copied the disc to hard disc in windows?

And I must admit my computer has taken a while to load the partitioning menu, particularly in 8.04 and earlier, though it works better in the test releases of 8.10 I think, but I don't recommend trying that to a beginner until the final release for it, as it can be unstable.

You could maybe try the 32bit version, it may work slightly slower though.  This is not a recommendation though, more a try this possibly idea.

And that is about all I can say, as I don't really know much more than that on your issues.

---

### Post by semitone36 on 2008-09-29
> **LowSky said:**
> Ok a few things

1. Are you using one hard drive for both Operating systems?
A. If Yes see 2.
B. If No see 3.
2. Have you done a disk defragment from Windows? Is there enough space on the hard drive ( 2-4GB is a normal install)? 
3. Set the drive you wish to install Ubuntu on as the Boot Drive.
4. Have you tried a 32 bit version of Ubuntu?
5. Try using Gnome Partitioner (GParted) from the Ubutnu LiveCD

Another idea is to be sure to run ScanDisk from windows (when you right click your C:/ drive and select properties youll see an button labeled "check disk for errors").  Also there should not be any issues with running a 32 bit OS on your rig.

---

### Post by pofigster on 2008-09-29
Maybe the motherboard isn't compatible with the Linux Kernel - I had a white box that had that problem.

---

### Post by Fingbut on 2008-09-29
Wow that was fast, thanks. I'll try the defrag, I'd like to avoid downloading again because I have a tiny download limit here :( but I could do it elsewhere.

But I forgot HD details so I'll tack them on here

HD 1 Seagate 160GB (windows is on here and so is Ubuntu in a different 30gb partition I made) 
HD 2 Samsung 750GB

And here's the motherboard I'm googling it now to try and find out

Motherboard ASUS AV8 XE Socket 939 (the linux kernel runs on it)

When it restarts after windows it goes into Busybox V1.1.3, I've tried to find commands to help but I don't really understand this tool.

---

