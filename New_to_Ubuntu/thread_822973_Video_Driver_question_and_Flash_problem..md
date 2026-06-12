---
title: "Video Driver question and Flash problem."
date: 2008-06-08
forum: New to Ubuntu
---

### Post by soviet911 on 2008-06-08
Hi, I got Ubunto 8.04 32-bit running on my desktop (AMD 6000+, 4 gigs of ram and 8800GT) and I dual boot into Vista 64-bit for gaming, in any case, i have installed nvidia drivers using the restricted driver manger, are they the latest drivers? or should i download drivers from nvidia website and install those ( i tried that before but it completely effed up my system could not get the xorg config to set up correctly i think i know what the problem was though) In anycase, the main reason i want Ubunto is to watch videos and safely webbrows and word procces, so far its kinda failing, if i watch Flash videos in full screen they get choppy and ripped up in both FF2 and FF3, not sure what the problem is, im using Adobe Flash player 9 (or what ever the latest one is ) any one know how to fix that?

---

### Post by powerpleb on 2008-06-08
> **soviet911 said:**
> Hi, I got Ubunto 8.04 32-bit running on my desktop (AMD 6000+, 4 gigs of ram and 8800GT) and I dual boot into Vista 64-bit for gaming, in any case, i have installed nvidia drivers using the restricted driver manger, are they the latest drivers? or should i download drivers from nvidia website and install those ( i tried that before but it completely effed up my system could not get the xorg config to set up correctly i think i know what the problem was though) In anycase, the main reason i want Ubunto is to watch videos and safely webbrows and word procces, so far its kinda failing, if i watch Flash videos in full screen they get choppy and ripped up in both FF2 and FF3, not sure what the problem is, im using Adobe Flash player 9 (or what ever the latest one is ) any one know how to fix that?

I have the same problem. I think that Flash support in Linux just isn't very good yet which is the reason for the poor fullscreen video playback.

Interestingly on my laptop (Intel video card no compiz) the fullscreen videos play fine but on my desktop (nvidia compiz) they are awful.

---

### Post by OldTimeTech on 2008-06-08
I have a Dell laptop with the same nVidia card that you have....Hardy asked me if I wanted to use the newest nVidia drivers when I loaded it...and it installed nvidia accelerated graphics driver (latest card)...also I just got an update from repos like yesterday with a newer graphics driver and it's still working in Hardware drivers.

I'm using Gnash which is the gnome flash and it works great with streaming video.

---

### Post by Hospadar on 2008-06-08
The drivers from the restricted drivers manager may be slightly out of date, but it's a much better idea to use those than the ones from nvidia's website.  If you must have *the* latest drivers, you should use envy to install them.  It pulls the drivers off nvidia's website and packages them so they play nice with ubuntu.  google "ubuntu envy" and you'll find the website you need for that.

---

### Post by enderwig on 2008-06-08
> **Hospadar said:**
> The drivers from the restricted drivers manager may be slightly out of date, but it's a much better idea to use those than the ones from nvidia's website.  If you must have *the* latest drivers, you should use envy to install them.  It pulls the drivers off nvidia's website and packages them so they play nice with ubuntu.  google "ubuntu envy" and you'll find the website you need for that.

Envy is in the repos
synaptic search for envyng

---

