---
title: "sound problems in Hardy"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Frantic-Atheist on 2008-05-11
hi everybody,
I just today upgraded to Hardy and I am experiencing some problems with the sound. firstly it's either 100% or 0% and it is way quieter then it was on Gutsy secondly my VLC player doesn't make a sound when I play .mp3 or .avi. If anyone can help me please do. My sound card is IXP SB4x0 High Definition Audio Controller (ATI)
thanks in advance Frantic-Atheist

---

### Post by alienexplorers on 2008-05-24
DOes the mp3 files play in rhythmbox?

---

### Post by Frantic-Atheist on 2008-05-24
sorry please erase this reply

---

### Post by Frantic-Atheist on 2008-05-24
yes also it totem but it's still low volume

---

### Post by sayakb on 2008-05-24
```
sudo apt-get install linux-backports-modules
```
Also, select the appropriate device (preferably ALSA) or set the volume by running alsamixer from a terminal.

---

### Post by Frantic-Atheist on 2008-05-24
I did what you said but it made no difference

---

### Post by dganders on 2008-06-13
yeah, im having a lot of sound problems also.  nothing is playing sound.

when it use:

aplay -l

i get:

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

is this right?  i think im just confused...

---

### Post by kansasnoob on 2008-06-13
While this is not a solved thread it contains links to everything I've tried to get sound working ............. other than maybe adding the Medibuntu repo and then adding alsa-firmware (medibuntu package).

[http://ubuntuforums.org/showthread.php?t=828199](http://ubuntuforums.org/showthread.php?t=828199)

---

