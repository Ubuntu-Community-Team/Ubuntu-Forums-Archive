---
title: "sound through firefox with flash."
date: 2013-11-23
forum: New to Ubuntu
---

### Post by thatredbird on 2013-11-23
(Just installed flash through the terminal, noticed that I am getting no sound.  I was wondering if I need to look into another terminal command to fix it. Or if there is a setting I am being dumb about. ) AN update apparently I have no sound at all.  perhaps i am a moron afterall.  thanks...

---

### Post by Mr.Dunham on 2013-11-23
You're not a moron, at least not yet :D (just kidding)

Didi you have any sound before you installed Flash? Also check out your Sound settings, to see if anything is muted.
Try checking sound settings with your system alone (I mean, no other software open), then do the same with Firefox opened while watching a video on YouTube, also check out any sound file like mp3 or an audio cd.

---

### Post by thatredbird on 2013-11-23
I realized my error after the fact, there is no sound at all. not even error sounds.  My guess is that it is a system setting, and I have been looking to find how to correct this sort of thing, I have checked in alsamixer, nothing seems to be muted anymore(the master sound was at 0,0 its back up). I have tried the gui option through xfce4-mixer, There is supposed to be mute at startup button that is uncheckable, however I dont see any that are.  Is there another interface that I might be missing?

---

### Post by thatredbird on 2013-11-24
First of all thanks for the fast response, it seems that I was looking at the wrong problem.  i discovered after I tested the sound on headphones that I had sound.

I found a work around, for the time being went into the alsa-base.conf file
sudo leafpad /etc/modprobe.d/alsa-base.conf
added this line to the end
options snd-hda-intel model=generic
 pa
when things came back up after restart, I went into volume controls(left click on the sound icon in panel settings) and un muted the ones that were muted.

---

