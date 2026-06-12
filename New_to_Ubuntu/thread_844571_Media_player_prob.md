---
title: "Media player prob"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by nnjond on 2008-06-29
Hi, Can anyone help me?

I cannot run Mplayer after watching utube without re-booting? I also loose sound on my mp3s.

---

### Post by spydon on 2008-06-29
Try ```
sudo pkill pulseaudio
```
That might help for the mp3 part...

---

### Post by nnjond on 2008-06-29
That seems to of got my sound back except for Mplayer

---

### Post by vambo on 2008-06-29
It might be worth in Mplayer preferences selecting a driver other than pulse, alsa should be there - which works just fine with my pretty standard setup.

---

