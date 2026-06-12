---
title: "no sound issue after upgarded to 12.04"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by mms ce on 2013-01-17
hey guys 
i trying to solve this since 3 days :( ,,, what i have to do >?
check below:
mms@mms-laptop:~$ cat /proc/asound/car*/co* |  grep Codec
Codec: Realtek ALC883
Codec: Motorola Si3054
mms@mms-laptop:~$ lspci -nn|egrep 'ultimedia|udio|sound|AC97|ac97|EMU'
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
mms@mms-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

thanks in advance

---

### Post by mms ce on 2013-01-18
i tried many things ...as sound troubleshooting in the forums and still the same !!
and still no response :( 
any advice >???

---

