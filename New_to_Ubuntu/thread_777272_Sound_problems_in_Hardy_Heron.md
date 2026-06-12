---
title: "Sound problems in Hardy Heron"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by sooperspook on 2008-05-01
Since I installed HH I've been having some sound problems.

Every once in a while, about every 20mins or so, the sound cuts out. A few minutes after this, everything freezes and I can't even shut down properly. I have to use the reboot button.

Has this been happening to anyone else? Any idea what to do? It didn't happen under 7.10

thanks all

---

### Post by twright on 2008-05-01
try sudo apt-get remove pulseaudio

---

### Post by mivo on 2008-05-01
Or less severe, and possibly still able to fix the problem: In *System -> Preferences -> Sound*, change everything to ALSA. If you are using VLC to play movies and audio files, you might also want to do this: In VLC, go to *Settings -> Preferences -> Audio* and check "Advanced Options" (right lower corner). Then choose "ALSA audio output".

If you have a problem with sound only working for one application at a time, download the **alsa-oss** package and add aoss before the command in the appropriate application launcher.

---

### Post by brownknight on 2008-05-01
> **sooperspook said:**
> Since I installed HH I've been having some sound problems.

Every once in a while, about every 20mins or so, the sound cuts out. A few minutes after this, everything freezes and I can't even shut down properly. I have to use the reboot button.

Has this been happening to anyone else? Any idea what to do? It didn't happen under 7.10

thanks all

Try changing from >System >Preferences >Sound and choose ALSA. Its more stable in my experience

---

### Post by sooperspook on 2008-05-02
Cool thanks guys. I'll give it a try and let you know how it works out.

---

### Post by sooperspook on 2008-05-03
Changing everything to ALSA seems to have worked.

Thanks again for the help guys. :)

---

