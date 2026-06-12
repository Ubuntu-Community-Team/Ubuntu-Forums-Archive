---
title: "Ubuntu + Flash + Web Browser = Garbage"
date: 2011-10-28
forum: Recurring Discussions
---

### Post by Ric_NYC on 2011-10-28
Rant= **[SIZE="4"]AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA....[/SIZE]**


Ok... I'm feeling better now.

---

### Post by LowSky on 2011-10-28
flash works fine for me. maybe it because you never got mono, lol

---

### Post by wolfen69 on 2011-10-29
"Ubuntu + Flash + Web Browser = Garbage"

Really? Do you think most people feel this way? For the record, flash + ubuntu + browser has always worked fine for me. Go figure.

Recurring?

---

### Post by nothingspecial on 2011-10-29
Moved to Recurring.

---

### Post by F.G. on 2011-10-29
yeah, i used to have real issues with this (choppy pictures, no fullscreen). however they've cleared up now, i think the canonical team have made an effort to fix it.

my suggestion is firefox + flashaid + javascript. (i still have issues using chromium and other browsers except iceweasel, particularly with javascript turned off).

---

### Post by tartalo on 2011-10-29
If your Ubuntu is 64 bits there is a problem with flash, at least before 11.10 (buttons not clickable, gray squares appear on top of videos...)

This was the fix:
[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

Did that help?

---

### Post by collisionystm on 2011-10-29
> **Ric_NYC said:**
> Rant= **[SIZE="4"]AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA....[/SIZE]**


Ok... I'm feeling better now.


High CPU much?

---

### Post by linuxyogi on 2011-10-29
I am using Xubuntu 10.04 
                   Firefox 7.0.1
                   Flash Aid

I get frequent flash player crashes. Downgrade FF ?

---

### Post by pqwoerituytrueiwoq on 2011-10-29
> **collisionystm said:**
> High CPU much?
cause the devs over at adobe decided hardware acceleration is a security risk
they completely disabled the override feature to top it off :mad::mad::mad:

---

### Post by Ric_NYC on 2011-10-29
I have Windows installed in the same computer and it plays Flash very well (so it's NOT a limitation from the hardware)...

---

### Post by kaldor on 2011-10-29
I've not had any Flash problems myself since Ubuntu 7.10. Flash performs just as well on my Ubuntu partition as it does in Win 7 for me.

I had a friend who wasn't so lucky, though, and reverted back to Windows XP because they couldn't watch YouTube without browser crashes and slowdowns.

---

### Post by LinuxFan999 on 2011-10-29
Flash on Linux is widely known to be inferior to Flash on Windows.
Here are 2 solutions for Youtube.
 
1. Use the HTML5 version of Youtube.
    Link: [http://www.youtube.com/html5](http://www.youtube.com/html5)
 
2. Download the videos and convert them to a different format.
    There are various utilities avaliable for this.

---

### Post by madjr on 2011-10-29
**AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA!!!!!!!!!!!1**

we may need a rants forum :p

oh and flash works pretty nice on my 4 year old computer (ati card, open drivers; 32bit ubuntu), should work even better for those that have Nvidia cards

---

### Post by beew on 2011-10-29
> **kaldor said:**
> I've not had any Flash problems myself since Ubuntu 7.10. Flash performs just as well on my Ubuntu partition as it does in Win 7 for me.

I had a friend who wasn't so lucky, though, and reverted back to Windows XP because they couldn't watch YouTube without browser crashes and slowdowns.

There are many ways to watch Youtube without flash: the flashvideo replacer addon, minitube, umplayer and HTML5 (there are probably other ways too) Apart from HTML5 which is still cpu taxing and doesn't always have options for the highest resolution all the other ways are better than flash in terms of cpu usage and smoothness.

I have no problem with flash until a Nvidia update a few days ago, after that flash crashes everywhere with Firefox (fine with Opera though) Turns out to be a bug in the Nvidia driver and it was reported in the Nvidia forum. Installing a .deb for flash 10.x and everything is working now. I updated to the latest Nvidia beta driver through xorg-edgers so it wouldn't affect most people who use the stable driver.

---

### Post by beew on 2011-10-29
> **madjr said:**
> **AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA!!!!!!!!!!!1**

we may need a rants forum :p

oh and flash works pretty nice on my 4 year old computer (ati card, open drivers; 32bit ubuntu), should work even better for those that have Nvidia cards

Flash 11 doesn't accelerate decoding with Nvidia even though flash 10 does.  As said above the latest Nvidia beta driver breaks flash 11 on Firefox, but I am sure that is temporary and meanwhile installing flash10 solves the problem (and get accelerated decoding as well)

---

