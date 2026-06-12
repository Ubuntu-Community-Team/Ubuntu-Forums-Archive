---
title: "Sound card not working correctly"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by toasty_ghosty on 2008-10-12
Hello, 

I just built myself a new computer which uses a NVidia chipset. It has a high definition sound card built it. It works to a degree, meaning the normal output works, but the high definition output as well as the mic imput do not work. Any reason why?

Thanks.

---

### Post by Pro-reason on 2008-10-13
Have you tried [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)?

---

### Post by toasty_ghosty on 2008-10-13
I think the issue here is that within the single card, it actually contains two cards:

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


And device 1, the digital side, doesn't want to work and whenever I reinstall sound drivers, it only installs to the analog device.

---

