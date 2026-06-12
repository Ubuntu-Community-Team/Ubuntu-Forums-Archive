---
title: "Burning Audio CD's from mp3 files"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-09-07
I am unable to burn and audio CD from mp3 files - Brasero doesn't like it:

"(filename).mp3" is not suitable for audio or video media."

I have installed ubuntu-restricted-extras. mp3 files play fine on rhythmbox, banshee, audacious. What do I have to do to get Brasero to deal with them?

TIA

---

### Post by haqking on 2011-09-07
> **sgage said:**
> I am unable to burn and audio CD from mp3 files - Brasero doesn't like it:

"(filename).mp3" is not suitable for audio or video media."

I have installed ubuntu-restricted-extras. mp3 files play fine on rhythmbox, banshee, audacious. What do I have to do to get Brasero to deal with them?

TIA


personally brasero sucks IMO.

try k3b though you need the mp3 plugin

---

### Post by sgage on 2011-09-07
> **haqking said:**
> personally brasero sucks IMO.

try k3b though you need the mp3 plugin

Thanks, but I'm trying to get Brasero working. It's always worked fine for me in the past. I don't want to install 209 MB of KDE stuff just to burn a CD.

---

### Post by haqking on 2011-09-07
> **sgage said:**
> Thanks, but I'm trying to get Brasero working. It's always worked fine for me in the past. I don't want to install 209 MB of KDE stuff just to burn a CD.


Fair one ;-)

Actually just noticed this is in oneiric sub-forum.

My bad didnt notice that iniitally

---

### Post by sgage on 2011-09-07
I figured it out - I needed to remove the fluendo plugin (incompatible with Brasero) and re-install gstreamer-plugins-ugly. Somehow it had be removed over the past weeks. Works fine now.

---

