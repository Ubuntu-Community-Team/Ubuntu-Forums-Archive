---
title: "Triple boot XP/Vista/Ubuntu?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by brons2 on 2008-08-24
Hello all,

I upgraded my system from an Opteron 165 to an Intel E2200 (overclocked), also picked up an ATI Radeon HD4850 and a new 500GB SATA hard drive as my new motherboard only has 1 PATA port so I had to choose between new optical drives or a new hard drive.

With my new spacious hard drive I have already dual booted XP and Vista, everything's going great.  But I have some more space left for yet another partition and I was wondering if Ubuntu would work with an already dual-booted machine.  

I do have my laptop dual booted between Vista and Ubuntu and it works fine with Grub, but I was wondering how this would work with grub added to the Windows process on my new desktop build.  If I chose Windows in grub, would it then give me a 2nd boot screen to choose my version of Windows?

---

### Post by brons2 on 2008-08-24
nobody?  bueller??

---

### Post by nickgaydos on 2008-08-24
I would think so! I've seen many people do it on like YouTube and stuff...try it out :-)

---

### Post by nickgaydos on 2008-08-24
> **brons2 said:**
> nobody?  bueller??
lol Funny movie :-)

---

### Post by bodhi.zazen on 2008-08-24
> **brons2 said:**
> Hello all,

I upgraded my system from an Opteron 165 to an Intel E2200 (overclocked), also picked up an ATI Radeon HD4850 and a new 500GB SATA hard drive as my new motherboard only has 1 PATA port so I had to choose between new optical drives or a new hard drive.

With my new spacious hard drive I have already dual booted XP and Vista, everything's going great.  But I have some more space left for yet another partition and I was wondering if Ubuntu would work with an already dual-booted machine.  

I do have my laptop dual booted between Vista and Ubuntu and it works fine with Grub, but I was wondering how this would work with grub added to the Windows process on my new desktop build.  If I chose Windows in grub, would it then give me a 2nd boot screen to choose my version of Windows?

You directly boot windows from grub.

If you have multiple versions of windows, you need to "hide" them form each other :lolflag:

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_)

---

### Post by zamadatix on 2008-08-24
if you get the iwndows to not interfere you can pretty much put anything else as long as you dont mess with the partitions to much. i have ubuntu puppy linux fedora 10 windows xp and windows vista on this comp. (i dunno what thats called lol)

---

### Post by Joeb454 on 2008-08-24
I triple boot that same system :)

Basically - Install XP, then install Vista - This way, Vista will recognise that XP is there, and add it as an option to the Vista bootloader.

Then, Install Ubuntu on the next partition, GRUB should then detect that Windows *Vista* is there, and will add an option to the bottom of the menu.lst.

This bottom option will then allow you to boot Vista's bootloader, which then allows you to choose which version of Windows to boot :)

Got that? ;)

---

### Post by brons2 on 2008-08-24
> **Joeb454 said:**
> I triple boot that same system :)

Basically - Install XP, then install Vista - This way, Vista will recognise that XP is there, and add it as an option to the Vista bootloader.

Then, Install Ubuntu on the next partition, GRUB should then detect that Windows *Vista* is there, and will add an option to the bottom of the menu.lst.

This bottom option will then allow you to boot Vista's bootloader, which then allows you to choose which version of Windows to boot :)

Got that? ;)

Thank you, that mirrors my expectations, but I wanted someone to confirm it before I went forward.  I've already got some time invested in getting this setup going, so I didn't want to needlessly trash it.

---

### Post by Joeb454 on 2008-08-24
As long as you have free (i.e. unpartitioned/formatted) space available, it should be easy :)

I set it up, updated Windows etc. and now I hardly ever boot into them :p

---

### Post by brons2 on 2008-08-24
I'm about 50/50 on my laptop between Ubuntu 8.04 and Vista Home Premium.  I could probably skew it a bit more toward Ubuntu if I had the Cisco VPN client for Linux, but I don't have a SmartNet login so I can't just download it.  Client works fine in Vista anyways and this laptop only takes a matter of seconds to reboot, so NBD.

---

### Post by exowraith on 2008-08-26
dont really need unpartitioned space. ask long as you got more than some gigs free you can just resize your partition to install ubuntu.

i managed to triple boot my desktop XP Vista and Ubuntu. was running XP and Vista for a while and just recently installed Ubuntu.

My laptop also managed to resize partitions to install Ubuntu. double boot Vista and Ubuntu

---

### Post by bdk09 on 2008-09-16
Sorry to "jack" this thread or bump it though I do need some help. 

I'm trying to triple boot as well, though with 2 HDDs. 1 HDD has xp and vista, so I want to install ubuntu on a whole separate drive.

How would I triple boot a setup like this?

---

### Post by FOBioPatel on 2008-09-20
> **bdk09 said:**
> Sorry to "jack" this thread or bump it though I do need some help. 

I'm trying to triple boot as well, though with 2 HDDs. 1 HDD has xp and vista, so I want to install ubuntu on a whole separate drive.

How would I triple boot a setup like this?


I suspect when you install Ubuntu you will see the existing Vista/XP installation you already have, and you have the choice of installing (and resizing the disk) named HDDA which has this Microsoft OSes data, or to HDDB which is your clean empty drive.

Grub is the Ubuntu bootloader, and you should only see the Vista or Ubuntu option when you fire up your PC. When you select Vista, you will be again prompted, Vista or XP.

I hope I am correct; I'm about to do something similar. All on 1 drive.

And just for Google's sake here are keywords I wish this thread was optimized for: ubuntu 8.04 xp vista triple boot 64 bit

---

