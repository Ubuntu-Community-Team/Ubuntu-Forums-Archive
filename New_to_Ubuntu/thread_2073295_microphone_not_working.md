---
title: "microphone not working"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by yogix on 2012-10-19
The microphone in my ubuntu is not working, so i'm unable to use any microphone apps like sound recorder, skype, etc.,. I've installed pavucontrol and tried various options in it but it didn't work. I'm having 12.04 installed in my Samsung N100SP netbook. Here's my system info on sound devices:-

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Kindly assist me to solve this problem.

Thanks in advance.

---

### Post by mikewhatever on 2012-10-19
1. Open Sound Preferences. Is there a device in the input tab?

2. If there was a device in 1., make sure it's not muted.

3. In not, try adding the following to alsa optios:
```
options snd-hda-intel  model=laptop-amic
```

To do that, open the config file for editin with

```
gksu gedit /etc/modprobe.d/asla-base.conf
```

...add the optiion line to the bottom, save and exit. 

Reboot to see if it has any effect. Repeat steps 1 and 2 if necessary.

---

### Post by oldcity11 on 2012-10-20
My microphone is also not working, so I'm unable to use my headset microphone with the program Audio-Recorder. However the microphone part of my Logitech Pro 9000 webcam works correctly. I'm working with a Dell Inspiron B130. Doing procedure in post #2 were fruitless. For the output it showed  "Microphone Built-in Audio". The headset works correctly on my desktop.
Below is audio information.

     lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

     aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

     arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any assistance appreciated
Otto-C

---

