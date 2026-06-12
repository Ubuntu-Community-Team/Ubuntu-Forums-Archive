---
title: "howto: via8237 sound working - snd_via82xx module - 2.6.10 kernel"
date: 2005-01-10
forum: Outdated Tutorials &amp; Tips
---

### Post by taygan on 2005-01-10
I'm running hoary with the 2.6.10 kernel and an ASUS a7v600-x motherboard with via8237 onboard sound.

Replacing the kernel did not fix my poor GStreamer and system sounds (way too much bass stutter), but adding this line to /etc/modprobe.d/alsa-base worked wonders (you can add the line to any file in the /etc/modprobe.d folder)

```

sudo nano /etc/modprobe.d/alsa-base

# add the following line to the end of the file
options snd_via82xx dxs_support=4

sudo update-modules


```

when you restart be sure to run alsamixer

```

alsamixer

```

press the right arrow until you see the DXS settings, unmute them by pressing m (so there's no MM at the top) and turn them up to the beginning of the red. also make sure you PCM and Master channels are unmuted and turned up.



if that doesn't work you can also try:
```

sudo nano /etc/modprobe.d/alsa-base
options snd_via82xx dxs_support=1

sudo update-modules

```

There are 4 DXS channels on the VIA8233/5/7 (and others?) that allow the hardware to control sounds, disabling the DXS support means that your software (ESD) will have to do all the mixing. 

this website helped a lot: [http://alsa.opensrc.org/index.php?page=via8233](http://alsa.opensrc.org/index.php?page=via8233)

an excerpt explaining dxs_support settings:

# 0 - the default value; set 48000 Hz only mode in most cases, except on some known motherboards (which are in the whitelist).
# 1 - enable full DXS support (at any supported sample rate).
# 2 - disable DXS support completely. In this case the hardware mixing ability of the chip is not used.
# 3 - use DXS at 48000 Hz only.
# 4 - enable DXS at any supported sample rate, but always set the codec to 48000 Hz (apparently on some motherboards this works better than dxs_support=1).

---

### Post by taygan on 2005-01-10
Just tested it with hoary and kernel 2.6.9.  Sounds good both under GStreamer and XMMS (GStreamer uses DXS-1 XMMS uses DXS-2)

---

### Post by jul on 2005-10-11
Hello,

i have also a motherboard with via 8237 chipset but i haven't  succeeds to configure my sound card :???: .

could you help me ? :confused: 

Thanks ;) 

Sorry for my english but i speak french ;)

---

