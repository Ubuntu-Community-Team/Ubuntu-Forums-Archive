---
title: "Upgrade finished -- no sound !!!!"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Bodsda on 2008-04-26
Hi, ive just finished upgrading from hardy 8.04 beta to the full release and now my sound is not working - nothing is muted in alsamixer and sound worked just befor the upgrade -- plz help!!!

---

### Post by Airfoot on 2008-11-13
With 8.10 and 8.04 (sometimes) pulse audio conflicts with alsa.

first go into "system > preferences > sessions" and unselect pulse audio.
next go into terminal and type the following:

$ pulseaudio -k
$ sudo alsa force-reload

then go into the volume control and turn the volume up(reloading alsa might set the volume at minimum) 
make sure your audio devices are set to alsa.

---

