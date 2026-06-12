---
title: "no sound when playing youtube video"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by lance bermudez on 2008-08-07
How do i get sound when playing a video from youtube or some other flash video. I can see them but not hear them it dose not just happen with youtube video as in it happen to all flash videos. speaker are turned up have mplayer and vlc players in stalled with all the plugins. even have the plugin from mozilla firefox to play embedded flash videos.

---

### Post by tuxxy on 2008-08-07
Are you using ALSA in system > prefs > sound

---

### Post by lance bermudez on 2008-08-07
this is what is says

sound events
intel 82801BA-ICH2

music and movies
intel 82801BA-ICH2

audio conferencing
intel 82801BA-ICH2

default mixer tracks
intel 82801BA-ICH2 (alsa mixer)

I will also add the output from the lshw command.

---

### Post by iaculallad on 2008-08-08
Try installing the sound wrapper for non-free plugin:

```
sudo apt-get install libflashsupport
```

---

### Post by loligager on 2008-08-08
Does the sound work in every where else???
try veoh.com see if sound works there
if so... it would be rlly wierd.. probably a codec problem
search for ubuntu restricted extras in synaptics and get it... than youtube should work

---

