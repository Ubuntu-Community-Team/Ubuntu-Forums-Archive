---
title: "headphones not working - ubuntu 12.04"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-09-28
hi
headphones are not working on my system, i have installed fresh ubuntu 12.04...do i need to install some special driver/plugins....although i can listen from system speakers,, but when i plugin headphones,,, i listen from both,, sys speakers and headphones.....otherwise speakers of system are working fine....but when i plugin headphones,,, i can hear from both headphones and system speakers,,, whereas system speaksers should be silent and only i should listen from headphones....
initially it was not playing some videos, i connected from net and it automatically searched some mising plugins and installed it...and now videos are working....wt else i need...

---

### Post by lechien73 on 2012-09-28
Please could you post the output of:

```
aplay --list-devices
```

This will help us to see what sound card you're using. I suspect you're using an Intel card, in which case there are a few workarounds we can try.

---

### Post by syednasirraza on 2012-09-29
$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

