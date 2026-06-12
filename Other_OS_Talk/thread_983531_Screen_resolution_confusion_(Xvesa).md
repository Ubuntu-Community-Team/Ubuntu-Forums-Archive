---
title: "Screen resolution confusion (Xvesa)"
date: 2008-11-15
forum: Other OS Talk
---

### Post by cardinals_fan on 2008-11-15
I have a quick question about my screen resolution with Xvesa and a NVIDIA GeForce 6100.  This is on SliTaz, but could easily apply to other distros (and will, if I can get it right).  The 1280x1024 resolution works okay, but it doesn't 'fit' my screen perfectly, causing a six-millimeter-thick vertical black bar on the right side of my screen.  As I understand it, changing the refresh rate might help.  Does anyone have any suggestions?

---

### Post by handy on 2008-11-15
If you are on LCD I think the refresh rate is always 60hz.

The only thing I could see, is that there are different Xvesa installations for different hardware, have you looked into that?

---

### Post by cardinals_fan on 2008-11-15
> **handy said:**
> If you are on LCD I think the refresh rate is always 60hz.

The only thing I could see, is that there are different Xvesa installations for different hardware, have you looked into that?
I think 60 is right too.  I'll check out different hardware variants.

---

### Post by init1 on 2008-11-16
> **cardinals_fan said:**
> I have a quick question about my screen resolution with Xvesa and a NVIDIA GeForce 6100.  This is on SliTaz, but could easily apply to other distros (and will, if I can get it right).  The 1280x1024 resolution works okay, but it doesn't 'fit' my screen perfectly, causing a six-millimeter-thick vertical black bar on the right side of my screen.  As I understand it, changing the refresh rate might help.  Does anyone have any suggestions?
Although Slitaz uses Xvesa by default, I think there might be a way to install Xorg.

---

### Post by cardinals_fan on 2008-11-16
> **init1 said:**
> Although Slitaz uses Xvesa by default, I think there might be a way to install Xorg.
There certainly is, but I'd prefer not to.

---

### Post by zmjjmz on 2008-11-16
Can you adjust the horizontal position of the image on the screen itself?

---

### Post by cardinals_fan on 2008-11-16
> **zmjjmz said:**
> Can you adjust the horizontal position of the image on the screen itself?
Not that I know of - how would I do that (it's an LCD screen, not a CRT)?

---

### Post by zmjjmz on 2008-11-17
> **cardinals_fan said:**
> Not that I know of - how would I do that (it's an LCD screen, not a CRT)?

Uh, chances are your screen has a little menu thingie going on. 
On my I-INC AG191D there's a menu button which summons an OSD that has options and stuff.
Changing horizontal position is one of the options.


I've noticed that different distros (I use this monitor on all of my old computers) tend to horizontally shift the screen one way or another, so that each time I connect it to a different comp I have to change the position. It's probably a driver thing.

---

### Post by cardinals_fan on 2008-11-17
> **zmjjmz said:**
> Uh, chances are your screen has a little menu thingie going on. 
On my I-INC AG191D there's a menu button which summons an OSD that has options and stuff.
Changing horizontal position is one of the options.


I've noticed that different distros (I use this monitor on all of my old computers) tend to horizontally shift the screen one way or another, so that each time I connect it to a different comp I have to change the position. It's probably a driver thing.
I'm an idiot.  The buttons have been on the bottom of my monitor all along!  I'll try them out tomorrow.

---

### Post by zmjjmz on 2008-11-17
> **cardinals_fan said:**
> I'm an idiot.  The buttons have been on the bottom of my monitor all along!  I'll try them out tomorrow.

Tomorrow? You really don't have like 30 seconds?

---

### Post by cardinals_fan on 2008-11-17
> **zmjjmz said:**
> Tomorrow? You really don't have like 30 seconds?
I really didn't.  Anyway, it worked great.  I have to seriously consider replacing my Arch partition with SliTaz now...

---

### Post by init1 on 2008-11-18
Yeah, nice to see that the fix was so simple and quick :D

---

### Post by cardinals_fan on 2008-11-18
> **init1 said:**
> Yeah, nice to see that the fix was so simple and quick :D
It isn't a total solution, as I have to do it at every boot, but it's certainly a nice option.

---

### Post by -grubby on 2008-11-18
I've got the same video card and my LCD is running at 75 HZ right now

---

### Post by cardinals_fan on 2008-11-18
> **nathangrubb said:**
> I've got the same video card and my LCD is running at 75 HZ right now
Have you also noticed the way NVIDIA has simply stopped caring about its customers using older cards? ;)

---

### Post by K.Mandla on 2008-11-19
> **cardinals_fan said:**
> Have you also noticed the way NVIDIA has simply stopped caring about its customers using older cards? ;)
Heh, I lol'd. 

You should really be more considerate of multi-billion-dollar international corporations. How will they feed their executives if you don't buy a newer version of the same product you already own, long before you actually need it? :mrgreen:

---

### Post by zmjjmz on 2008-11-19
> **K.Mandla said:**
> Heh, I lol'd. 

You should really be more considerate of multi-billion-dollar international corporations. How will they feed their executives if you don't buy a newer version of the same product you already own, long before you actually need it? :mrgreen:

We should start a charity!

---

### Post by -grubby on 2008-11-20
> **cardinals_fan said:**
> Have you also noticed the way NVIDIA has simply stopped caring about its customers using older cards? ;)

Yes, I have terrible problems with it, which is why I'm hesitant to try new distros sometimes. Arch is the only distro I've ever gotten to run it at 60 HZ

---

