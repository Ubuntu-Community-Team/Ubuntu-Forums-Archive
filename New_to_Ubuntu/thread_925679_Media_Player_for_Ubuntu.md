---
title: "Media Player for Ubuntu"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by henrypradeep on 2008-09-20
Which one is good media player for Ubuntu???? From where i should install??


Thanks

---

### Post by mc4100 on 2008-09-20
"Banshee", it's the first google result. Plays audio, and video.
The have instructions for downloading on their website. 
You could also just go the default route, of using Rhythmbox Music Player for audio only, and Totem Movie Player for everything else.

The first step to getting immediate playback of proprietary formats (like mp3) in a media player in to install Ubuntu Restricted Extras. Search for it in Add/Remove, or open a terminal (Applications -> Accessories) and type:
```
sudo apt-get install ubuntu-restricted-extras
```

Optionally, you might want vlc:
```
sudo apt-get install vlc
``` Which pretty much plays anything you can ever throw at it.

---

### Post by k33bz on 2008-09-20
for audio try Audacious, it is in the synaptic manager.

for video:
xine
vlc
ogle

all these are in the synaptic manager as well

---

### Post by cariboo on 2008-09-20
If you are new to Ubuntu always use either Add/Remove Programs or Synaptic Package Manager. I use vlc for video and listen for audio, although vlc willl do audio also. To install either of these programs go to Applications-->Add/Remove Programs. Make sure All Open Source Applications is selected in Show, then search for vlc or listen. Another meta package you should install is **ubuntu-restricted-extras** this will install many audio and video codecs as well as flash, java and mscorefonts.

Jim

---

