---
title: "Why does suspend cause blank screen??"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by gabriella on 2008-08-11
When I click on Suspend my Laptop goes to sleep just fine. But... when I try to resume the drive powers up, i.e you can hear it engage etc, but the screen then goes blank and I cant do a thing with it. Nothing..it's frozen.. and I have to crash it and reboot.  Help!

---

### Post by edm1 on 2008-08-11
this is a problem with the closed source drivers the manufacturers have written for your graphics card. Unfortuately there is no real fix although i have seen some work-arounds on the forum (which havent worked for me).

---

### Post by tuxxy on 2008-08-11
Do you really need susped? if not you could remove the power settings at system > prefs > screen saver > power management

---

### Post by gabriella on 2008-08-11
> **tuxxy said:**
> Do you really need susped? if not you could remove the power settings at system > prefs > screen saver > power management

Thanks guys. Yes for now I've removed it in power management and just go to blank screen. But there's really no solution to this??? Where do I find the work arounds?

---

### Post by groosam on 2009-04-29
I have a Ideapad Y430 and had the same problem.  I installed a new driver for my video card, now everything works fine.  Go to Administration>Hardware Drivers..and download the most recent.

Cheers

---

### Post by gabriella on 2009-05-07
> **groosam said:**
> I have a Ideapad Y430 and had the same problem.  I installed a new driver for my video card, now everything works fine.  Go to Administration>Hardware Drivers..and download the most recent.

Cheers

Thanks for you comment :)

What driver did you download? Do you mean the open source one?
The one I have listed in Administration>Hardware Drivers is the  ATI accelerated graphics driver

---

### Post by presence1960 on 2009-05-07
> **edm1 said:**
> this is a problem with the closed source drivers the manufacturers have written for your graphics card. Unfortuately there is no real fix although i have seen some work-arounds on the forum (which havent worked for me).


+1

I had no suspend or hibernate in Hardy or Intrepid. I tried all those fixes and work arounds also to no avail. But here is the good news: I did a clean install of Jaunty and both work out of the box- no fussing or workarounds needed!

---

### Post by gabriella on 2009-05-08
> **presence1960 said:**
> +1

I had no suspend or hibernate in Hardy or Intrepid. I tried all those fixes and work arounds also to no avail. But here is the good news: I did a clean install of Jaunty and both work out of the box- no fussing or workarounds needed!

Thats good news indeed. I'm trying to resolve as many of these problems as a I can now for experience purposes before I go and install a clean copy of 9.04

---

