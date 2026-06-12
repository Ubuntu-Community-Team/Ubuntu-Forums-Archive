---
title: "sound drivers?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by chris200x9 on 2008-04-26
hi, I built a PC and I foolishly didn't check if it'd work with linux, however it does for the most part, the only problem I am having is the sound and the motherboard manufacturer only supplies windows drivers. Can I in anyway "wrap" the driver to work with linux? By the way I am using hardy heron 64 bit. any help would be much appreciated.

---

### Post by chris200x9 on 2008-04-26
...or if the only option is buying a sound card can anyone recomend me a very cheap compatible one?

---

### Post by DukeNuke2 on 2008-04-26
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

what kind of onboard sound is it?

---

### Post by DukeNuke2 on 2008-04-26
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by chris200x9 on 2008-04-26
its

```
 **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


and thank you so much that links looks very helpful :)

---

### Post by DukeNuke2 on 2008-04-26
try to add this to "/etc/modprobe.d/alsa-base" (you need root rights to edit the file!)

```
options snd-hda-intel model=auto
```

this works for me...

---

### Post by chris200x9 on 2008-04-26
no luck....I did everything.....maybe its an x64 issue?

or, to my embarassment I may have them in the wrong holes :-\ will check....

---

### Post by DukeNuke2 on 2008-04-27
have you rebooted your system after doing changes to the files?

---

