---
title: "I inherited a broken HP"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by teleromeo on 2008-09-13
I got it for free and want to play with it without making any cost before being sure I can make it work...

It's a HP pavilion desktop with a crashed hard disk that came without any instalation disks.
I burned a DVD with ubuntu and the PC recognizes it but it takes ages to load. I guess there isn't enough memory  to load completely. (it has 256 Mb)

Also I tried to install an old but working drive that needs to be formatted. It's a 60 gig drive that I pulled out of an Apple iMac. When that drive is connected, the PC does not start up any further than the HP welcome screen.

Any help or suggestion to make this machine work in any way would be very appreciated.

---

### Post by ronnielsen1 on 2008-09-13
Try Puppy, Dsl or AntiX on it

---

### Post by cozmicharlie on 2008-09-13
Try ronneilsen1's suggestion (unless you can afford to buy more memory).  
As per the hard disk issue.  Can you access the bios when you start the computer?  It should say on the screen (my Pavilion laptop I press F2) when you start.  Go into the bios and set it up to boot to the cd and not the hard drive.  Then when you start it should boot to the puppy linux cd (or whatever distro you are trying to install).  Then you should be able to install from the cd and reformat the HD during the installation process.

---

### Post by stalkingwolf on 2008-09-13
try using 7.10 feisty fawn. Ive had good luck running it on systems
with 256 ram.  You might also try changing the jumper setting on the
HDD.  Try "cable select" and "master" settings.  You can also try
leaving the drive out and just booting from the disk.

---

### Post by 3rdalbum on 2008-09-13
Xubuntu works on 256mb of RAM, but I reckon you should beg, borrow, or scrounge some more memory for it.

---

### Post by Pro-reason on 2008-09-13
As others have said, it's not ideal to try to squeeze some version of Ubuntu on to a machine like that.  Use *Puppy Linux*, or *Damn Small Linux*.  That's what they are for.

---

### Post by teleromeo on 2008-09-13
Thanks for all the suggestions !

I'm downloading puppy right now and will try it when I get home from work, I also downloaded Xubuntu. (puppy seems to look very small in comparision to ubuntu and Xubuntu)

I have a free memory bank so it can be upgraded. I will do so  when I can get this machine at work with the spare hard disk and when I find a usefull destination for it.

I can acces the bios when the faulty drive is connected and when there is no drive connected. When I hook up the apple formatted drive I can not get any further than the HP screen at startup. pressing F2 gives no result. I guess the jumpers are set wrong so can anyone point me to a picture how the jumpers should be set ?

---

### Post by arpanaut on 2008-09-13
> I guess the jumpers are set wrong so can anyone point me to a picture how the jumpers should be set ?
I would go to the disk mfg. website and get the manual for the drive. They usually have diagrams of the jumper settings.

---

### Post by ibgeorgeb on 2008-09-13
Puppy linux is alright but I used Xubuntu on an old Gateway with 256mg and it works great. Matter-of-fact, the person I gave this computer to loves it for web surfing and thinks the world of me (he-he). gB

---

### Post by Sef on 2008-09-13
> Puppy linux is alright but I used Xubuntu on an old Gateway with 256mg and it works great. Matter-of-fact, the person I gave this computer to loves it for web surfing and thinks the world of me (he-he). gB

Xubuntu on 256 mb ram will run really fast.  It is made for computers with less memory than what Ubuntu or Kubuntu require.

---

### Post by Kellemora on 2008-09-13
Hi TR

Ironically, that's how I got both an HP and an e-machines.

The e-machine only has 256 megs of memory and I'm using an ANCIENT 4 gig hard drive from an old 386 machine in it.  CPU is 1.6 MHz P4.

Installed is Ubuntu 8.04 and it works just fine, a little bit slower than on the HP.

This is the machine I TRY THINGS ON FIRST before trying it on my slightly faster FREE HP pavilion, 512 megs memory.
That one has the 60 gig drive from the e-machines showing 149 bad blocks.
Yet I have CentOS, Debian and Ubuntu running on it with no problems.

I know this isn't kosher, but I'm always moving hard drives around from machine to machine, because some of my old machines don't even have CD drives in them.  Boot up looks for new or changed hardware and reconfigures itself, usually automatically.

Ubuntu is the ONLY Linux Distro I've found that works right out of the box so to speak.  It only messes up when I go changing things around on my own.

Good Luck

TTUL
Gary

---

### Post by skippuff54 on 2008-09-13
i hooked up xubuntu on an old gateway with similar specs for my folks. my dad doesn't know how to touch type, yet they are gettin a lot of use out of it

---

### Post by egalvan on 2008-09-13
> **teleromeo said:**
> ...downloading puppy  now and will try it..., I also downloaded Xubuntu. (puppy seems to look very small in comparision to ubuntu and Xubuntu)

Yes, Puppy is MUCH smaller than Ubuntu/Xubuntu,
It's optimized for that.
I run it on my 2GB machine, totally in RAM,
and on a 512MB, also totally in RAM.
Very fast.

> 
I have a free memory bank so it can be upgraded. I will do so
yes, more ram is always good, most always a better up-grade than cpu speed.
My #2 option would be a faster drive. You can sometimes find 7200-rpm drives as small as 40Gb, which may lower the price (who wants such a small hard drive these days, no?)
Also, try to get the latest BIOS for your HP. As old as it is, it may have the 80gb or 137gb drive limitations, tho these can be rather easily worked around in Linux.

> I can acces the bios when the faulty drive is connected or no drive connected. When I hook up the apple formatted drive I can not get any further than the HP screen at startup. pressing F2 gives no result. I guess the jumpers are set wrong so can anyone point me to a picture how the jumpers should be set ?

As others have indicated, the manufacturer's website may have that info.
But depending on the hardware, the Apple firmware in that drive may not be compatible with the HP BIOS.

---

