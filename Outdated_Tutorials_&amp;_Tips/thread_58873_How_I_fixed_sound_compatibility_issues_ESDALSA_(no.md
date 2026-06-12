---
title: "How I fixed sound compatibility issues ESD/ALSA (noobfriendly!)"
date: 2005-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by sneax on 2005-08-21
Well, I always had to do

killall esd

when I wanted to run cedega or whatever program with sound, and I tryed following a howto here which was complicated for the noob that I am. The directions were easy, but it's so complicated that a lot can go wrong and of course, it went wrong. I reinstalled Ubuntu (and promised myself to stay with the 'official' repositries as much as possible). This is what I did for my sound and it seems it ... WORKS!

ALSA howto:
- Make sure you only have 'official' repositries.
- Do a search for 'ALSA' and there is one item not installed. Install it. A package related to ESD (the mixer) will automaticaly uninstall.
- That's basicaly it. Go into volume control and select ALSA as mixer, just select ALSA wherever they ask for something about sound. I also had to set it as my 'device' in volume control preferences.

Now everything works. Cedega no more needs esd killall and I never had 'conflicted audio' messages again. Wow! My first howto. I hope i help someone with it, im just a noob myself.

---

