---
title: "[SOLVED] No sound in media players in 8.10"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by FreewheelinFrank on 2008-11-03
I've just tried to play an MP3 file in Ubuntu 8.10 but there's no sound.

VLC seemed to be playing the file but there was no output.

Amarok says:

> xine was unable to initialize any audio drivers

PulseAudio Manager says:

> Connection Refused

The login sound is played OK, and there was sound when I tried Open Arena.

I get this in System>Preferences>Sound

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

What could be wrong?

---

### Post by j.c.sackett on 2008-11-03
Do you have the necessary codec for mp3s?

If you're using xine as your media output you need the xine mp3 codecs.
```

$aptitude search xine
``` will list all the available xine files. You want xine-extra-plugins, I believe.

---

### Post by drs305 on 2008-11-03
Have you checked which sound system (pulse/alsa/autodetect/etc) you are currently using? When you check the sound via System, Preferences, Sound, note the type of audio used.

In VLC, you have to make sure it matches what your system is using. In VLC, Tools > Preferences > Audio, then make sure the 'Audio output' matches.

---

### Post by FreewheelinFrank on 2008-11-03
Thanks guys but it was a false alarm: sound is OK after a reboot. Open Arena had jammed up on exit and must have taken out the sound drivers. I hit Ctrl Alt Backspace but that obviously must've left the sound system in a messed up state. I then decided to try playing an MP3 for the first time after updating and thought it must've been the update that caused the problem.

Phew!

---

### Post by agoodliffe on 2008-11-03
I too have just upgraded to Ubuntu 8.10 and there is no sound. The sound is under autodetect. The sound worked fine before. I have INTEL ICH6 (ASLA).

---

### Post by FreewheelinFrank on 2008-11-03
agoodliffe, you need to start your own thread because I've marked this one as 'solved'.

---

