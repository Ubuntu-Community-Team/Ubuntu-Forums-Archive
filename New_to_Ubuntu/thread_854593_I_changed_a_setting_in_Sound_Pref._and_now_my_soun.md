---
title: "I changed a setting in Sound Pref. and now my sound doesn't work"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by erans on 2008-07-09
I changed SOMETHING in my sound prefs and now my sound doesn't work (but it worked fine when I installed Ubuntu and up until I accidentally changed something).

My sound prefs are right now: 

Sound events: autodetect

Sound playback: autodetect

Audio conferencing
Sound playback: ALSA
Sound capture: ALSA

Default mixer track: 
Device: Audigy 2 ZS

Thanks! This is really frustrating. :(

edit: I'm using hardy Ubuntu with GNOME

---

### Post by tjwoosta on 2008-07-09
try setting everything to alsa then close the sound prefs and re-open before testing it

---

### Post by billgoldberg on 2008-07-09
> **erans said:**
> I changed SOMETHING in my sound prefs and now my sound doesn't work (but it worked fine when I installed Ubuntu and up until I accidentally changed something).

My sound prefs are right now: 

Sound events: autodetect

Sound playback: autodetect

Audio conferencing
Sound playback: ALSA
Sound capture: ALSA

Default mixer track: 
Device: Audigy 2 ZS

Thanks! This is really frustrating. :(

Change everyting to alsa, exept the last one.

Also to be sure, go to synaptic and install "asoundconf-gtk".

Open it (alt+f2 -> asoundconf-gtk) and make sure the correct card is used.

Also, install "gnome-alsamixer". Unmute everything and turn everything up to max.

---

### Post by erans on 2008-07-09
Changing everything to ALSA did not fix the problem (is "testing" in sound pref. supposed to start some sort of sound loop? I just see the bar moving back and forth). Still no sound.

I installed asoundconf-gtk but cannot get it to run. I tried running the command from Terminal and this is what I got: 
```
Traceback (most recent call last):
  File "/usr/bin/asoundconf-gtk", line 24, in <module>
    import sys, re, os, pygtk, gtk, string
ImportError: No module named pygtk

```

---

### Post by erans on 2008-07-09
is there any way to restore these settings to default?

---

### Post by erans on 2008-07-09
selecting p16v and testing that emits a very loud beep. Selecting ADC emits the same beep but at a much lower volume, but neither gives me sound in playing movies.

---

