---
title: "no sound-audio device busy"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by vitu on 2008-08-21
I am a freshy to ubuntu and have no programming experience and need everything explained in the "for dummies" way. I run ubuntu on a IBM T 41/ 512Ram/ 40 GB. I have the xine, the caffeine, and the totem mediaplayer installed. But I can't play DVDs nor Audio CDs on any player. Error mesages: "The audio device is busy, is another application using it","Audio output unavailable, Device busy". 
:confused: Firefox closed and working offline

---

### Post by fahadsadah on 2008-08-21
Please open a terminal and type: ```
sudo dd if=/dev/urandom of=/dev/dsp
```

Does this make a crackling noise?

---

### Post by vitu on 2008-08-22
> **fahadsadah said:**
> Please open a terminal and type: ```
sudo dd if=/dev/urandom of=/dev/dsp
```

Does this make a crackling noise?


No crackling sound! The system speakers are working - laptop beeps, when taken off docking station. Otherwise no sound - tried to play Youtube videos- videos play, but no sound:confused: ,music cd's- album and titles list displayed, but not playing:( ,dvd's: introduction warning,piracy advertisments playing - then "no audio device" showing](*,)????

---

