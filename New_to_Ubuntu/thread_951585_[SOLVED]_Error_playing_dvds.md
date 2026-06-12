---
title: "[SOLVED] Error playing dvds"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2008-10-18
I put ubuntu on a Lenovo Z61M and when I watch Some dvd's I get a "error opening/initializing the selected video_out (vo-) device" in Mplayer Movie Player and a "could not read from resource" error in regular Mplayer. While Other dvd's play fine. What going on?

---

### Post by philinux on 2008-10-18
[http://ubuntuforums.org/archive/index.php/t-20039.html](http://ubuntuforums.org/archive/index.php/t-20039.html)

---

### Post by LunaticHiatus on 2008-10-18
I tried to turn xv into x11 and gl2 as suggested in that link and neither worked. Instead of playing in mplayer movie player. It went crazy and looked like it was trying to resize itself faster then butterfly wings

---

### Post by Zzl1xndd on 2008-10-18
Just a quick question about your problem, Did you install the libdvdread3 package it is required to watch Encrypted DVD's. If you didn't non-encrypted DVD's would play fine but encrypted ones would give you a problem.

If you didn't here's the instructions 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by philinux on 2008-10-18
> **LunaticHiatus said:**
> I tried to turn xv into x11 and gl2 as suggested in that link and neither worked. Instead of playing in mplayer movie player. It went crazy and looked like it was trying to resize itself faster then butterfly wings

Install VLC from synaptic.

---

### Post by LunaticHiatus on 2008-10-18
Philinux: didn't work

tweakedenigma: Worked, only in VCL... so, sorta fixed I guess?

---

### Post by Zzl1xndd on 2008-10-18
Although it is possible to get the other players to work with DVD's, I find VLC does the best job for it anyway. For Totem, if I remember correctly you need to switch to Xine, if you do a search from Totem in synaptic it should be in the list, For me thought i this caused issues with some other Video playback, so I would recommend sticking with VLC.

---

### Post by LunaticHiatus on 2008-10-18
how would I go about making VLC my default video player?

---

### Post by philinux on 2008-10-18
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD)
Damn pain in Hardy.

I chose a simpler route. In nautilus preferences media tab, I select "do nothing" when dvd inserted. Then when it's mounted on desktop I right click and open with VLC.

---

### Post by Zzl1xndd on 2008-10-18
> **philinux said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD)
Damn pain in Hardy.

I chose a simpler route. In nautilus preferences media tab, I select "do nothing" when dvd inserted. Then when it's mounted on desktop I right click and open with VLC.

I took the same route.

---

### Post by philinux on 2008-10-18
> **tweakedenigma said:**
> i took the same route.

lol :)

---

### Post by LunaticHiatus on 2008-10-18
I'll probably just choose do nothing as well

---

### Post by philinux on 2008-10-18
> **LunaticHiatus said:**
> I'll probably just choose do nothing as well

At least in Intrepid they fixed this. I've installed VLC and it appears under the media tab for dvd's. Yeeeha

---

### Post by LunaticHiatus on 2008-10-18
for whatever reason, I rebooted recently and now it plays on mplayer as well. Not quite sure since I rebooted multiple times while doing this. Well, either way. Thanks and solved

---

