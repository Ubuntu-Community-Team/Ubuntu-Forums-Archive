---
title: "Where can I download old xserver xorg drivers?"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by klemperal on 2008-10-11
My intel 945 chip has been giving me all sorts of trouble with the current and bleeding edge xserver xorg intel video packs.  Does anyone know where I can download older versions?  Thanks.

---

### Post by handydan918 on 2008-10-11
> **klemperal said:**
> My intel 945 chip has been giving me all sorts with the current and bleeding edge xserver xorg intel video packs.  Does anyone know where I can download older versions?  Thanks.

Teh 945 is new enough that you won't likely find "older" packs.
Good luck with it, tho.

---

### Post by prshah on 2008-10-12
> **klemperal said:**
> My intel 945 chip has been giving me all sorts of trouble with the current and bleeding edge xserver xorg intel video packs.  Does anyone know where I can download older versions?  Thanks.

The older ones are availible on your system; instead of using "intel" or "intel experimental modesetting drivers" switch to i810. Those are older drivers, and are included in the xserver-xorg-video-intel package.

To switch, press Alt+F2, give the command```
gksudo displayconfig-gtk
``` Select the "Graphics Card" tab, and change from whatever displayed to "i810". If it's vesa or i810 already, then change to "intel" or "intel experimental modesetting driver"

However, switching to i810 will not really help; you should stick with "intel".

What is the problem you are facing? Maybe we can help clearing that up.

---

### Post by klemperal on 2008-10-12
Very cool, I didn't know about that command.  I have my driver set to "intel" within the xorg.conf.  From reading [this post]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/220019") that describes the the same problems I'm having (computer crashing durring 3D games requiring hard restarts) with the same card and xorg ver that the poster has I assumed the solution for me was to get an older package (I'm sure I butchered that sentence, but bear with me). Maybe you could have a look at the article and let me know if I came to the right conclusion, or if I missed something.  I'll try experimenting around with that command you showed me in the mean time.  Thanks for the response and let me know if you need me to post any more information.

---

