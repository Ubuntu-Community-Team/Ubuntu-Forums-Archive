---
title: "totem and youtube"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by hazman on 2008-08-09
how do i get videos from youtube to play in totem ubuntu 7.10. tried adding all plugins as various sites have said but no joy

---

### Post by benerivo on 2008-08-09
So you're trying to play youtube clips that you have saved to your computer (as .flv or .mp4 files?), but are unable to play them back with totem even though you have installed

gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-ffmpeg

which are pretty much all the plugins you might need for totem.

---

### Post by mc4100 on 2008-08-09
> **benerivo said:**
> So you're trying to play youtube clips that you have saved to your computer (as .flv or .mp4 files?), but are unable to play them back with totem even though you have installed

gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-ffmpeg

which are pretty much all the plugins you might need for totem.

I believe they are trying to watch the videos from *within* totem, through the YouTube plugin.

---

### Post by hazman on 2008-08-09
no u can play them directly from youtube. i know cos i have before in 8.04 but when i tried upgrading to that other day it crashed and had to reinstall

---

### Post by benerivo on 2008-08-09
So your problem is trying to play downloaded files using the totem movie player? It really should work given that you have all the gstreamer plugins installed. Try opening totem fom the terminal, then trying to play one of your youtube vids, and see what it says in the terminal when it fails to play.

Have you also considered using another video player. I reccommend vlc.

---

### Post by Vadi on 2008-08-09
Sorry, but that feature is only available from 8.04 (browse and watch youtube videos).

To everyone else, this is different from downloading the .flv and watching it - you actually can search youtube videos right inside totem.

---

### Post by hazman on 2008-08-09
thats right i could in 8.04 but unable to get it now and am uneasy about trying 8.04 again as update as it crashed and left me having to reinstall

---

### Post by Vadi on 2008-08-09
Well, backup your important data, and try it again.

---

### Post by hazman on 2008-08-09
ok try it over night again. thanks any way

---

### Post by benerivo on 2008-08-09
It is safer to upgrade via a reinstall using the new installation cd (8.04) rather than using the inbuilt upgrade option from your existing version -- if that helps you with your problem.

---

### Post by hazman on 2008-08-09
can only do things over net main desktop motherboard blown and wrecked cdrw in process this is an old laptop but coped fine with ubuntu before upgrades and everything other than youtube being crap but ace thru totem

---

### Post by AndyCooll on 2008-08-09
> **hazman said:**
> can only do things over net main desktop motherboard blown and wrecked cdrw in process this is an old laptop but coped fine with ubuntu before upgrades and everything other than youtube being crap but ace thru totem
Might be missing the point here, but I watch Youtube videos using Firefox and the Flash-plugin. Are you watching through Totem because your Flash plugin isn't working properly?

:cool:

---

### Post by hazman on 2008-08-09
yes it really poor like flashing 1 frame to next really jumpy

---

### Post by t0p on 2008-08-09
> **AndyCooll said:**
> Might be missing the point here, but I watch Youtube videos using Firefox and the Flash-plugin. Are you watching through Totem because your Flash plugin isn't working properly?

:cool:

I prefer the look of the playback thru totem.

---

