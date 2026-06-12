---
title: "Audacious playing music too softly... Why?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by norfair on 2008-08-03
I use Audacious as my mini audio player (can't find any other close to Winamp), but for some reason it plays things really softly. I have to crank up my speakers to listen to the music at a decent volume. Then if I should watch something on YouTube or what have you, I'm defeaned by the sound - given that the volume was turned up to hear music via Audacious. It's especially jarring when listening to stuff via Audacious and visiting a site with embedded audio. It scares the you know what out of me. I've checked every setting I know to check. Does anyone know how I can fix Audacious to match my system's volume settings? Thanks.

---

### Post by Vivaldi Gloria on 2008-08-03
Try choosing pulseaudio in the sound settings of audacious.

---

### Post by norfair on 2008-08-03
> **Vivaldi Gloria said:**
> Try choosing pulseaudio in the sound settings of audacious.

Thanks for the suggestion, but it didn't change anything sadly. I had it originally set to the ALSA plugin, and noticed no change after switching to the Pulse Audio plugin (I closed and restarted Audacious). It's so weird, as every other program plays audio at the volume level it should.

---

### Post by kihjin on 2008-08-03
Run the command amixer in a Terminal and post back the results.

It should look like this

kjgibson@anarix:~$ amixer 
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
...

---

### Post by norfair on 2008-08-03
> **kihjin said:**
> Run the command amixer in a Terminal and post back the results.

It should look like this

kjgibson@anarix:~$ amixer 
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
...

Is this what you wanted me to post? If so, it's a lot lengthier than your example! I hope my setup isn't too messed up. 

-------

norfair@ubuntu:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 9 [29%] [0.00dB] [off]
  Front Right: Capture 9 [29%] [0.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'

-----

Thanks.

---

### Post by kostkon on 2008-08-03
> **norfair said:**
> Thanks for the suggestion, but it didn't change anything sadly. I had it originally set to the ALSA plugin, and noticed no change after switching to the Pulse Audio plugin (I closed and restarted Audacious). It's so weird, as every other program plays audio at the volume level it should.
Since it's using *PulseAudio* then I don't think you have to check the ALSA mixer volume levels but the *PulseAudio* ones. But, I'll find it strange if the volume level for *Audacious* in *PulseAudio* (since it can control the levels of every application separately) has been set by default to anything lower than 100%.

Unfortunately, to control *PulseAudio* and check the volume levels you'll have to install something, the *padevchooser* (*PulseAudio Device Chooser*) application.

Unless someone has an idea on how to check the *PulseAudio* volume levels from the command line.

---

### Post by norfair on 2008-08-04
Do you think if I uninstalled it and then reinstalled it my issue might be resolved? (I'm running out of ideas!)

---

### Post by norfair on 2008-08-05
Is it okay to "bump" a thread on this forum? Well, if it isn't just lock the thread, I guess. But if it is, if there's anyone out there that might have an idea of how I can get Audacious' master volume to match that of my system, I would greatly appreciate it. I don't mean to be a pest, I just don't know where else to turn. Thanks.

---

### Post by Living2007 on 2008-08-05
> **norfair said:**
> I use Audacious as my mini audio player (can't find any other close to Winamp), but for some reason it plays things really softly. I have to crank up my speakers to listen to the music at a decent volume. Then if I should watch something on YouTube or what have you, I'm defeaned by the sound - given that the volume was turned up to hear music via Audacious. It's especially jarring when listening to stuff via Audacious and visiting a site with embedded audio. It scares the you know what out of me. I've checked every setting I know to check. Does anyone know how I can fix Audacious to match my system's volume settings? Thanks.
I might not be much of a helper but try WINE with Winamp.

---

### Post by norfair on 2008-08-05
> **Living2007 said:**
> I might not be much of a helper but try WINE with Winamp.

Any form of input at this point is helpful, so thank you. I've read about WINE, but have yet to try it. Perhaps I ought to look into more closely. I just hate to give up on Audacious, as I like it overall.

---

