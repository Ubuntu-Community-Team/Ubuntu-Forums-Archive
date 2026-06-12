---
title: "High-pitched sound through ogg123."
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Sslaxx on 2011-09-25
So, I'm braving the waters of 11.10 (via Kubuntu) a month early... and I've encountered a bug. A minor one, I think (at least from my limited testing thus far).

ogg123 is playing OGG files about 5-10% higher pitched than they should be. Audacity seems to be OK. So does Rhythmbox.

Anyone else encountered this?

---

### Post by Sslaxx on 2011-10-12
Bump. Has nobody else been suffering from this issue? From what I can tell it is only ogg123 that has this issue.

It is reporting this error message in verbose mode:[quote="ogg123"]ao_alsa WARNING: sample rate 44100 not supported by the hardware, using 48000[/quote]

---

### Post by crdlb on 2011-10-12
If you are using pulseaudio, try ```
ogg123 -d pulse /path/to/file.ogg
``` If that works, you can change the default output in /etc/libao.conf. There seems to be something broken or misconfigured in alsa, but I have no idea how to fix it.

---

### Post by Sslaxx on 2011-10-12
> **crdlb said:**
> If you are using pulseaudio, try ```
ogg123 -d pulse /path/to/file.ogg
``` If that works, you can change the default output in /etc/libao.conf. There seems to be something broken or misconfigured in alsa, but I have no idea how to fix it.
Seems to have done the trick, thanks.

---

