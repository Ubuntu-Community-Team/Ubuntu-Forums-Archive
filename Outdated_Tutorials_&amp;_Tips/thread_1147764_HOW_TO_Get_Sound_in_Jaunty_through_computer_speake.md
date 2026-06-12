---
title: "HOW TO: Get Sound in Jaunty through computer speakers"
date: 2009-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by daboroe on 2009-05-03
Many of you with new laptops might be wondering why you get sound out of the headphone jacks but not the computer speakers itself. 

The answer is simple. You have to do some manual editing a configuration file.

First you need to find the chipset. You can find out by this command

```
aplay -l

```The output should be something like:

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Then you need to look at this file: /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

This file will tell you what model that you want. 

If you have a HP DV5-xxxxxx, your model is 

Next you need to run the following command

```

gksu gedit /etc/modprobe.d/alsa-base

```At the end of the file you need to enter

```

options snd-hda-intel model=<model>

```

<model> will need to be the model for your chipset. Like I said for the HP DV5 series the model is "hp-dv5".

What should be at the end of the file should be

```

options snd-hda-intel model=hp-dv5

```You want to save the file and exit out. Then reboot your machine and you should have sound. You may have to try several things. 

If you do not want to restart especially if you are going to try multiple things, you can run the following command

```

pulseaudio -k; sudo service alsa-utils stop; sudo rmmod snd_hda_intel; sudo modprobe snd_hda_intel; sudo service alsa-utils start; pulseaudio -D

```you can take out the pulse audio commands if you are not utilizing pulseaudio.



**Some information came from Zorael [post]("http://ubuntuforums.org/showpost.php?p=5017453&postcount=2") about this issue that many people are facing.

---

