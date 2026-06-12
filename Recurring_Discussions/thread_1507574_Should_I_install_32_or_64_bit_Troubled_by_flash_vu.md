---
title: "Should I install 32 or 64 bit? Troubled by flash vulnerability..."
date: 2010-06-11
forum: Recurring Discussions
---

### Post by zlapidus on 2010-06-11
Hi everyone.

I've decided to dump windows once and for all. I'm going to install ubuntu tonight, but I've been unsure as to whether I should install the 32-bit or 64-bit version. The ominous warning against 64-bit on the site (not for daily desktop use) has somewhat scared me, as has some chatter on reddit about the vulnerability of flash that's unpatched in the 64-bit version, and how much of a nightmare running the 32 bit version with ndiswrapper is.

here's an idea of the hardware of the computer - 4gb ram, phenom x4 2.8 ghz, ati radeon hd 4850.

I'd be really curious as to your advice. Is 64-bit ubuntu somewhat uncompatible? I view a lot of web video, I suppose, so if flash is inoperable, I would dislike that. If it's livable though, and running 64-bit would be worth it, I'd interested in that as well.

Although off-topic, I would also be interested in any advice you might offer as to the ati drivers. I've heard they are generally good, but ati can be somewhat tricky.

I'd appreciate any assistance! Thanks a lot! Seems like the ubuntu community on these forums is really great.

---

### Post by SIGTERMer on 2010-06-11
I've been running the 64-bit version for a while now (since 8.04). I've noticed no problem with the system except for flash which is somewhat buggy (i'm running the native 64-bit version). but even with its temperamental behavior, it's still very usable; you can still watch videos, play games, and do everything you could do with other versions. Don't know anything about the security problem though (or more precisely, I don't really care :))
As for dumping windows, go for it. The last time i had a dual boot system was a couple of years back.

---

### Post by t.rei on 2010-06-11
There are basically two reasons for me to not run 64 bit:
a) the rare occasion that I find time for and feel like gaming: less hassle with wine (at least, last time I checked)
b) flash - hate it, but it's everywhere. And I do like to watch a quick video for giggles and such.

That's basically it. I don't die of lack of performance and gain some workiness. *shrugs*

---

### Post by Metrop021 on 2010-06-11
there's a 64 bit version of flash out there that works fine for me, and i'm not sure how much of a difference 64 bit has on wine... not much i feel since i'm able to run most things that are written as viable in the wine appdb. I'd recomment the 64 bit version but if you feel like going extra safe take the 32.

---

### Post by Zemblan on 2010-06-11
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

A bit old but it might help. I'm not sure that unless you are going to be running computationally intensive applications or have more than 4GB of RAM that there is any particular advantage to running 64bit rather than 32. For normal desktop use 32bit has always been entirely sufficient for me.

---

### Post by dookiebowser on 2010-06-11
> **zlapidus said:**
> Hi everyone.

I've decided to dump windows once and for all. I'm going to install ubuntu tonight, but I've been unsure as to whether I should install the 32-bit or 64-bit version. The ominous warning against 64-bit on the site (not for daily desktop use) has somewhat scared me, as has some chatter on reddit about the vulnerability of flash that's unpatched in the 64-bit version, and how much of a nightmare running the 32 bit version with ndiswrapper is.

here's an idea of the hardware of the computer - 4gb ram, phenom x4 2.8 ghz, ati radeon hd 4850.

I'd be really curious as to your advice. Is 64-bit ubuntu somewhat uncompatible? I view a lot of web video, I suppose, so if flash is inoperable, I would dislike that. If it's livable though, and running 64-bit would be worth it, I'd interested in that as well.

Although off-topic, I would also be interested in any advice you might offer as to the ati drivers. I've heard they are generally good, but ati can be somewhat tricky.

I'd appreciate any assistance! Thanks a lot! Seems like the ubuntu community on these forums is really great.

When I ran 64bit Ubuntu 8.04 HH on a midrange Dell desktop it had no problems with drivers. Things were noticeably and visibly faster.  There was a x64 beta version of flash but they have since closed the beta and I wouldn't trust it as far as I can spit considering their x64 endeavors. You may have to run a 32-bit version of Firefox or whatever browser to accommodate the 32-bit version of Flash that has been left in the dust. If this is your only 32-bit application I don't think you will notice a slowdown. My poor 32-bit laptop system runs Flash and watches 480p youtube videos better than my wife's 64-bit quad-core system running on windows. Less video jitter, smoother FPS, but some background and less noticeable audio crackling on my USB headset.

You could always run 64-bit browsers and forget about Flash. HTML5 is where it's at. Flash will be playing catchup for the foreseeable future IMO, and it will be easy for the major sites that serve flash video to switch to HTML5.

---

### Post by dookiebowser on 2010-06-11
> **Zemblan said:**
> [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

A bit old but it might help. I'm not sure that unless you are going to be running computationally intensive applications or have more than 4GB of RAM that there is any particular advantage to running 64bit rather than 32. For normal desktop use 32bit has always been entirely sufficient for me.


You can support more than 4gb RAM if he had it with generic-pae kernel anyway, no?

---

### Post by PinchedNerve on 2010-06-11
> **zlapidus said:**
> Hi everyone.

I've decided to dump windows once and for all. I'm going to install ubuntu tonight, but I've been unsure as to whether I should install the 32-bit or 64-bit version. The ominous warning against 64-bit on the site (not for daily desktop use) has somewhat scared me, as has some chatter on reddit about the vulnerability of flash that's unpatched in the 64-bit version, and how much of a nightmare running the 32 bit version with ndiswrapper is.

here's an idea of the hardware of the computer - 4gb ram, phenom x4 2.8 ghz, ati radeon hd 4850.

I'd be really curious as to your advice. Is 64-bit ubuntu somewhat uncompatible? I view a lot of web video, I suppose, so if flash is inoperable, I would dislike that. If it's livable though, and running 64-bit would be worth it, I'd interested in that as well.

Although off-topic, I would also be interested in any advice you might offer as to the ati drivers. I've heard they are generally good, but ati can be somewhat tricky.

I'd appreciate any assistance! Thanks a lot! Seems like the ubuntu community on these forums is really great.
I've been running x64 on 4 computers here in my house. I can say without a doubt that the flash issue is pretty annoying to me.  I am not a Ubuntu Guru, in fact I just started using Ubuntu out of necessity about 2 months ago (wifes kids kept killing one windows computers) & I liked it enough that I put it on most of the computers in the house.

My biggest issues so far are the Flash madness, lack of ability to play new games & that I can't control the fan speed on any of the video cards.  I have a ATI 4870 on my desktop & it gets pretty hot on default fan speed. 

Due to the flash issue alone I've been seriously considering (today) going to i386 (32bit) version.

My personal D-top is
Core 2 Duo E8400
4 gigs of mem
ATI 4870

I think I would lose about 500mb of mem going to 32bit though.  Bottom line though, if you don't want flash hassles you might want to go 32bit install

Edit: Btw: I believe Adobe decided to kill 64bit Flash support.  So its only going to be 32bit Flash for the foreseeable future.

---

### Post by NightwishFan on 2010-06-11
I advise 64-bit unless:

[LIST]
[*]You plan on installing a lot of stuff not in the repositories.
[*]You really enjoy flash videos and want to ensure a future of it. Personally I just install the 64-bit plug-in and disable it in Firefox until I need it.
[*]You have under 1gb of ram.
[/LIST]

The performance benefits are there, and will likely be important soon, so getting used to 64-bit (which is likely going to be the standard for years to come) is not a bad thing. I have used 64-bit on various *nix systems since 2007. Thats not too long but long enough to know my way around. I have encountered no problems. On Ubuntu you can even install the ia32-libs package to run 32-bit software on 64-bit. Lately even ndiswrapper has been working better if you are worried about flash.

---

### Post by lswartz on 2010-06-11
If it was me, I would probably install the 32 bit desktop, but why don't you try both? Install 1 for a week & then try the other & see. One thing I like about Ubuntu is it sure is fast to do a clean install. I always planned on a day for Windows. To be fair to Windows, I probably got bored & wondered off a few times.

---

### Post by bodhi.zazen on 2010-06-11
> **zlapidus said:**
> Hi everyone.

I've decided to dump windows once and for all. I'm going to install ubuntu tonight, but I've been unsure as to whether I should install the 32-bit or 64-bit version. The ominous warning against 64-bit on the site (not for daily desktop use) has somewhat scared me, as has some chatter on reddit about the vulnerability of flash that's unpatched in the 64-bit version, and how much of a nightmare running the 32 bit version with ndiswrapper is.

here's an idea of the hardware of the computer - 4gb ram, phenom x4 2.8 ghz, ati radeon hd 4850.

I'd be really curious as to your advice. Is 64-bit ubuntu somewhat uncompatible? I view a lot of web video, I suppose, so if flash is inoperable, I would dislike that. If it's livable though, and running 64-bit would be worth it, I'd interested in that as well.

Although off-topic, I would also be interested in any advice you might offer as to the ati drivers. I've heard they are generally good, but ati can be somewhat tricky.

I'd appreciate any assistance! Thanks a lot! Seems like the ubuntu community on these forums is really great.

Moved to recurring discussions. Search the forums, you will find tons of these discussions.

IMO you should use 64 bit unless there is a reason not to. Flash is sometimes spotty and site dependent on both 32 and 64 bit and I do not have any more or less problems with 64 bit flash. I use the 64 bit version from adobe.

In terms of security, "Troubled by flash vulnerability..." 32 vs 64 bit makes no difference, use noscript.

---

