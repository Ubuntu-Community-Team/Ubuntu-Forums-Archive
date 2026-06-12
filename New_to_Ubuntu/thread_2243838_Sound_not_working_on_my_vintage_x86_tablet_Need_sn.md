---
title: "Sound not working on my vintage x86 tablet? Need snd_t4dwave."
date: 2014-09-11
forum: New to Ubuntu
---

### Post by cody16 on 2014-09-11
I bought a vintage Pentium III x86 tablet on Ebay last week and I've  been having trouble finding a linux distro that actually works with all  of the drivers. Puppylinux works with everything but xorg crashes  constantly. Ubuntu only runs in software rendered mode which is horribly  slow. Opensuse, archlinux, and fedora won't run at all. Lubuntu 14.04  seems to run the best everything works perfectly except for the sound.  The tablet has a Sis 630 chipset and therefore requires the sis 7018  audio driver and from what i've discovered snd_t4dwave is the correct  module. But it won't load or maybe it is loading and not functioning.  The volume slider is present but it does nothing. I've tried adding  snd_t4dwave in /etc/modules but that didn't work. I'm not an advanced  linux user. Please help

---

### Post by cody16 on 2014-09-11
Okay apparently snd_t4dwave is a freebsd driver not linux .The driver I want has been included in the linux kernel since 2.3.40. So why isn't my audio working. I tried playing an mp3 and a youtube video My volume slider is at the max and not muted.

---

