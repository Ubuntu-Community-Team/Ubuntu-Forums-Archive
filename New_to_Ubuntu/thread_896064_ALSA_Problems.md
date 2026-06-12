---
title: "ALSA Problems"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Unanimated on 2008-08-20
Whenever I open System-->Preferences-->Sound and choose ALSA as the driver for any of my sound devices and hit test, it comes up with an error message, which just happens to be the attached image. ALSA is the only driver that will make all my sound go perfectly, and it also supports my sound cards. Also, sometimes when Amarok crashes and I'm using ALSA, it will stop working until I restart my computer. I'm sure there's an update somewhere for it, but it never appears in the update manager and the website doesn't tell me how to download it. I really don't want a link to the website, if possible--I would rather use the much more user-friendly terminal, if possible. When I type in sudo alsamixer, here's what comes up:
```
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

```

It never even asks for my password. Also, when I actually installed PulseAudio again, I open up Manager and hit connect, and it says connection refused, in any window that I go to. I have the default server set to the default option. I really don't know what's going on, and it's getting kind of frustrating. I also installed a bunch of ALSA packages from Synaptic.

---

### Post by Unanimated on 2008-08-20
bump

---

