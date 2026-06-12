---
title: "[SOLVED] Macbook Linux?"
date: 2008-09-03
forum: Other OS Talk
---

### Post by liquidfunk on 2008-09-03
Are there any Linux Distros that will work out of the box with my Macbook 2,1? 

 Or any BSD for that matter?

 I fancy a switch.

---

### Post by atoc on 2008-09-03
Ubuntu.
Elive.

---

### Post by liquidfunk on 2008-09-03
Elive is a bit outdated, and Ubuntu doesn't work out of the box, thanks anyway.

---

### Post by zmjjmz on 2008-09-03
Yeah, that MacBook Elive thing is for the first gen MacBooks...

---

### Post by liquidfunk on 2008-09-03
I have tried that, and it does work out of the box with my Macbook, but its quite outdated. I want something thats quite up to date.

---

### Post by MaxIBoy on 2008-09-03
PPC architecture? 

Well, there's Yellow Dog Linux which costs money.

---

### Post by Twitch6000 on 2008-09-04
Well I am almost positive that any BSD will work with MAC.

Mainly FREEBSD.

I think a good Linux that will work with MAc with a little tweaking would probably be OpenSuse or Ubuntu.

---

### Post by spencercarran on 2008-09-04
Out of the box? I doubt it. But it shouldn't be too horrible to get it running. But OSX is based on BSD, so I would imagine FreeBSD would work pretty well.

---

### Post by Dojan5 on 2008-09-04
> **liquidfunk said:**
> Are there any Linux Distros that will work out of the box with my Macbook 2,1? 

 Or any BSD for that matter?

 I fancy a switch.

What does "out of the box" mean?

---

### Post by spencercarran on 2008-09-04
> **Dojan5 said:**
> What does "out of the box" mean?

Without having to do anything special or tweak anything at all, ie you install the distro and the wireless works without messing with searching out a new driver or using ndiswrapper.

Since most of the stuff that doesn't work "out of the box" can be made to work with a handful of copy-and-pasted commands in the terminal, I don't really see why having every single thing work out of the box is a make or break thing, but to each his own.

---

### Post by oswaldkelso on 2008-09-05
> **MaxIBoy said:**
> PPC architecture? 

Well, there's Yellow Dog Linux which costs money.

Wrong. They have a staggered release on new releases. After a short period of time its a free download. You can of course buy a box set if you choose. 

Yellowdog is ppc only.

---

### Post by liquidfunk on 2008-09-05
Just to clarify. 

 My Macbook has the following:

 Intel Core2Duo 2Ghz
 2Gb RAM
 Intel GMA
 Atheros Based Wifi card

 So not PPC. I got this at the end of last year. 

 Ideas?

---

### Post by Pinoy915 on 2008-09-05
> **liquidfunk said:**
> Just to clarify. 

 My Macbook has the following:

 Intel Core2Duo 2Ghz
 2Gb RAM
 Intel GMA
 Atheros Based Wifi card

 So not PPC. I got this at the end of last year. 

 Ideas?

So, what does not work out of the box? The Atheros wifi card? My laptop has an Atheros based card and it did not work out of the box either but it was easily fixed by a Windows driver and ndisgtk. Easier option would be to do the madwifi patch.

---

### Post by liquidfunk on 2008-09-05
The Wireless doesn't work, the camera doesn't work, right clicking is an issue. The booting up is an issue as it takes about 30seconds + to load it up.

---

### Post by zmjjmz on 2008-09-05
Elive _can_ be upgraded.
Run "sudo apt-get install distro-upgrade".

---

### Post by marsmissionaries on 2008-09-06
You are going to have to wait to get out of the box support, as most distros will not support your WIFI chip yet. Your chipset is very new, i have the same chipset in my desktop PC and to get support i have to compile madwifi from svn. 

you can try open suse 11 or fedora 9 but once again they might not even have the module yet. (there was just recently an opensource module for that chipset made)

Edit: [http://www.phoronix.com/scan.php?page=news_item&px=NjYyMw](http://www.phoronix.com/scan.php?page=news_item&px=NjYyMw) <--some info on the driver

---

### Post by billgoldberg on 2008-09-06
> **MaxIBoy said:**
> PPC architecture? 

Well, there's Yellow Dog Linux which costs money.

Eumm, Yellow Dog Linux is free, as far as I know. Or at least they have a free distro.

---

### Post by billgoldberg on 2008-09-06
> **liquidfunk said:**
> The Wireless doesn't work, the camera doesn't work, right clicking is an issue. The booting up is an issue as it takes about 30seconds + to load it up.

You are complaining for a 30 second boot up time?

---

### Post by liquidfunk on 2008-09-09
> **billgoldberg said:**
> You are complaining for a 30 second boot up time?

 No, because Apple Mac's use EFI instead of BIOS, they search for the OS and then boot it differently. So if for example I were to use Ubuntu on my Mac Book, it would sit there searching for the OS, then find it, then load it up. So it would be 30secs to find it, then Ubuntu load up. 

 I'd much rather it turn on and then load up immediately. 

 I may well check out Elive again.

---

### Post by tdrusk on 2008-09-09
Debian has a powerpc download.
[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

---

### Post by liquidfunk on 2008-09-09
Thanks for that, but it's an Intel Processor, not a PPC.

---

### Post by liquidfunk on 2008-09-13
Solved! I'm just using Hardy!

---

