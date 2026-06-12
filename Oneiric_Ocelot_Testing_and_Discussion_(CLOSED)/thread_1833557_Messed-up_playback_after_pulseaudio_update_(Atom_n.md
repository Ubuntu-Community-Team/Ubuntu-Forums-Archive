---
title: "Messed-up playback after pulseaudio update (Atom netbook)"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by simplygades on 2011-08-26
Hi. Does anyone face skippy sound after pulseaudio 1:0.99.1-0ubuntu2 in Oneiric? I have an Acer AO751h with intel HDA.

```
AO751h:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Seems to affect low end machines, I've filed a bug at
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/825709](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/825709)
please subscribe if you are affected. Thanks!
[]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/825709")

---

### Post by lucazade on 2011-08-26
same here... bug confirmed

---

### Post by konas on 2011-09-15
I have the same netbook and the same problem. But when I erase the .pulse directory in my home one, the sound works as it should. On a reboot the sound is crappy again...


Konas.

---

