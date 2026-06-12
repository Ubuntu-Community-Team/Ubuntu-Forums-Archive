---
title: "Creative X-fi sound cards"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by bgast1 on 2008-08-17
Has anyone made any progress in supporting X-Fi Extreme Gamer sound cards yet? Last time I checked they didn't work in Hardy Heron. I'm getting by with my on board sound, but figured since I have one installed I might as well get some use out of it.

---

### Post by Chainek on 2008-08-18
There appears to be a 64 bit version driver on the creative website for linux.No 32 bit. I just removed my fatality yesterday and put my old audigy back in after giving up.I don't think my pentium D will hold out too well in 64 bit.

---

### Post by Nepherte on 2008-08-18
Ubuntu won't recognize and configure the card when you install Hardy. You can get the card to work with OSSv4: [http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961) It's very straight forward.

---

### Post by jukingeo on 2008-09-23
> **Nepherte said:**
> Ubuntu won't recognize and configure the card when you install Hardy. You can get the card to work with OSSv4: [http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961) It's very straight forward.

Don't bother with OSS, it is nothing but trouble.  It keeps knocking other stuff out.

Follow the guide in my sig below.  THAT works fine with the X-Fi (in Hardy).  At least you will get just about everything to work.

With OSS, I only got half of my stuff to get sound and when I got sound on the second half, it knocked the first half out.  Then you needed something called Pulse Audio.

OSS is old and outdated.  Hardy seems to "like" ALSA, so I would stick with that.

Geo

---

### Post by Nepherte on 2008-09-23
Well, although I do prefer to use ALSA (also with x-fi), I can only say that OSS is easier to setup for x-fi for beginners. I got it to work with both ways and found OSS to be easier (subjected to my personal opinion of course). The functionality is the same, you only have to tell programs to use OSS instead of ALSA. Saying that OSS is old and outdated is absolutely not true. On the contrary, OSS is being actively developped by 4front technologies.

---

### Post by jukingeo on 2008-09-24
> **Nepherte said:**
> Well, although I do prefer to use ALSA (also with x-fi), I can only say that OSS is easier to setup for x-fi for beginners. I got it to work with both ways and found OSS to be easier (subjected to my personal opinion of course). The functionality is the same, you only have to tell programs to use OSS instead of ALSA. Saying that OSS is old and outdated is absolutely not true. On the contrary, OSS is being actively developped by 4front technologies.


It is true that OSS IS easier to set up and for most beginners, if they don't mind not getting sound out of half their applications, maybe then that is all that is needed.  Setting up OSS for games proved hard for me.  Pulse helped there, but that knocked out the streaming internet.  I NEVER had those problems with ALSA.  Also Jack (which is an application needed for DAW work) wouldn't work with OSS at all.

Ubuntu used to be OSS based, but made the switch with the latest version to support ALSA.  Ubuntu Hardy (8.04) comes set up off the CD with ALSA, not OSS.  While OSS is continued to be supported, it IS an older format and it probably will take a back seat to ALSA.  So I stand by what I said there.

---

