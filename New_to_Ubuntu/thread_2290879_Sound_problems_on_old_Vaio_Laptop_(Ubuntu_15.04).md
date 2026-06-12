---
title: "Sound problems on old Vaio Laptop (Ubuntu 15.04)"
date: 2015-08-16
forum: New to Ubuntu
---

### Post by toyo2 on 2015-08-16
Hello, this is my first time using Ubuntu on one of my own PCs. I have some experience with it from school. I'm using a Vaio VGN-FS515B. 
From the first start there were crackling/clicking sounds coming from the left speaker whenever a system sound was supposed to play. 
Music/Video playback has non-existent/intermittent/distorted sound.

I followed [this troubleshooting guide]("https://help.ubuntu.com/community/SoundTroubleshooting"), but nothing changed. 
I tried out the method in [this thread]("http://ubuntuforums.org/showthread.php?t=1043568") with the model codes "sony", "vaio" and "laptop", but nothing changed.

My sound settings don't show any devices for sound output, so look like this.

[[IMG]http://imagizer.imageshack.us/v2/320x240q90/913/MjkKAd.png[/IMG]]("https://imageshack.com/i/pdMjkKAdp")


Alsamixer looks like this:

[[IMG]http://imagizer.imageshack.us/v2/320x240q90/673/bl38uA.png[/IMG]]("https://imageshack.com/i/ipbl38uAp")


This: 
```
aplay -l
```
shows me this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


This:
```
lspci -v | grep -A7 -i "audio"
```
shows me this:
```

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
    Subsystem: Sony Corporation Device 81bb
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
```

Any suggestions or help would be very much appreciated.

---

