---
title: "weird sound problem.."
date: 2008-07-12
forum: Philippine Team
---

### Post by Pedro0727 on 2008-07-12
help plz how to fix this,
weird sound on my Laptop after i installed UBUNTU 8.04
Sink sound playback problem.?:confused:
the sound is like tiktak.the played loop.

---

### Post by jeffimperial on 2008-07-12
Do you happen to have both an integrated sound device *and* a sound card (PCI/PCIE) ? If so, you can change the driver (ALSA/PulseAudio) for those devices at System > Preferences > Sound

---

### Post by Pedro0727 on 2008-07-12
> **jeffimperial said:**
> Do you happen to have both an integrated sound device *and* a sound card (PCI/PCIE) ? If so, you can change the driver (ALSA/PulseAudio) for those devices at System > Preferences > Sound

Built-in sound device. i used Pulse Audio sometimes it works but sometimes not.

how to edit the audio sink properties on Pulse Audio?

---

### Post by jeffimperial on 2008-07-12
I myself have not had that much audio problems with any of the few Ubuntu boxes I've set up. I hope this helps --> [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

Do tell if this isn't what you're looking for, or in case you need any more help :D

---

### Post by Nhatz on 2008-07-13
[QUOTE=Pedro0727]help plz how to fix this,
weird sound on my Laptop after i installed UBUNTU 8.04
Sink sound playback problem.?
the sound is like tiktak.the played loop. [/QUOTE]

try this...

```
sudo apt-get install linux-386
```

ASTIG! :guitar:

---

