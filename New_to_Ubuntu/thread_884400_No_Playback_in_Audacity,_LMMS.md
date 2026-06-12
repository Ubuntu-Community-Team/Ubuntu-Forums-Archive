---
title: "No Playback in Audacity, LMMS"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Matt Nichols on 2008-08-09
I finally got recording to work in Audacity, but the playback doesn't work. Same thing happens in LMMS. I ran LMMS in the terminal, and I got this:
> could not set realtime priority.
ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave
Playback open error: Device or resource busy
No audio-driver working - falling back to dummy-audio-driver
You can render your songs and listen to the output files...
ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave

How can I fix this? I'm a total ignoramus as far as audio goes with Linux; I've previously just listened to music (which still works fine, by the way), but now I want to record some. Any hints? Thanks.

---

### Post by carlinuxlearner on 2008-08-12
What version of Ubuntu are you using?
Have you tried switching sound drivers? (double click on the sound icon in the upper right hand corner, then [File>>>Change Device] select a different on)
What are your audacity settings? [Edit>>>Preferences] then check your "Audio I/O" tab

C@RL

---

