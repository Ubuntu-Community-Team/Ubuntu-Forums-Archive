---
title: "Create fn shortcuts for ALSA"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by ViliX64 on 2014-06-15
I have started using ALSA as audio controller for my ASUS notebook and one thing that really bugs me is that the only way I can controll the volume is via ALSA's mixer in terminal, is there any way that I could bind my fn keys (fn + F12 to volume up, fn + F11 to volume down, F10 to mute) to perform these actions?

---

### Post by ViliX64 on 2014-06-15
Ok, so apparently it can be done using amixer, which is implemented utility in ALSA. I have done it binding commands like:
```

amixer set Master 5+
amixer set Master 5-
amixer set Master toggle

```

to my fn keys in Keyboard settings.

---

