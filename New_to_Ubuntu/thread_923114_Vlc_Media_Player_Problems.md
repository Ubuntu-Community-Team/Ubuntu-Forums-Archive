---
title: "Vlc Media Player Problems"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Mitchlb on 2008-09-18
I can't get the audio to work anymore. It just stopped working. Its possible I downloaded something through synaptic that interfered - but I don't know what that could have been. I don't get it. I've checked the vlc settings and re-installed the program all to no effect. Help!

---

### Post by Perfect Storm on 2008-09-18
Try start VLC via the terminal and see what output is shown.

You can also check synaptic history log to see which apps & libs is updated/removed/installed.

---

### Post by Bakon Jarser on 2008-09-18
Also, if you have other programs running that use sound it may be a pulseaudio issue.  Try closing all other programs before opening vlc.

---

### Post by Mitchlb on 2008-09-18
No help. How do I check my sound drivers?

---

### Post by jbrown96 on 2008-09-18
> **Mitchlb said:**
> No help. How do I check my sound drivers?
System-->Preferences(?)-->Sound and check the playback device. If it is pulseaudio, make sure that no application is muted. You can also try switching to alsa, which seems to have fewer problems.
```
alsamixer
``` and check that no essential channels are muted. You should remute the channels that don't fix the sound issue because there may be feedback from those channels once you do get audio working.

---

### Post by simtaalo on 2008-09-18
downloading the new version might help?

---

### Post by markbuntu on 2008-09-18
In Settings/Preferences/Audio/Output Modules make sure the audio output module is set t either pulseaudio or alsa. If you want some basic sound troubleshooting help, try the first part of my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If you want all your sound applications to play nice with each other, read it further.

---

### Post by Mitchlb on 2008-09-22
I thought it was just VLC but I tried to go on youtube today and the videos didn't even play. My sound isn't working at all... And youtube videos won't play. Though avi and other videos still play - the sound isn't working.

---

### Post by ethoxyethaan on 2008-09-22
It's because your default mixer is not set to alsa mixer.

this reminds me of a problem i had while running teamspeak. "some" bad compiled / written programs often prevent other programs from accessing alsa

it is most likely that youtube (flash) uses oss mixer and it might not work on your hardware

---

### Post by Mitchlb on 2008-09-22
That did it. Thanks man.

---

