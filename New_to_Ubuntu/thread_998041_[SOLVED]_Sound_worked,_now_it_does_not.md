---
title: "[SOLVED] Sound worked, now it does not"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by ant2ne on 2008-11-30
I did have sound, now i got no sound. I can't think of anything I may have changed. Other than updates, and installing Alien Arena.

System-> Preferences-> Sound-> Devices -> All are set to Autodetect. Clicking the Test button for anything results in> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

```
ant2ne@2ne-buntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ant2ne@2ne-buntu:~$ 

```

Playing anything via Brasero or Rythmbox gives me "unknown errors".

---

### Post by alwayshere on 2008-11-30
Autodetect does not work for me so maybe ya should try each one till ya find the one that works .

i got big sound troubles ,"alien arena" has no sound but "sauerbraten" does 

sound seems in the to hard basket so hope someone with the smarts will sort it soon

---

### Post by ant2ne on 2008-11-30
i fixed it, i'm an idiot. It seems that I've managed put it on mute, and then remove the icon from the panel, so I couldn't see it was muted.

:rolleyes:

---

