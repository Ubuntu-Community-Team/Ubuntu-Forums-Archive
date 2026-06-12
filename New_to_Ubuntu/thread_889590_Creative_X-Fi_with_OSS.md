---
title: "Creative X-Fi with OSS"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by pzs on 2008-08-14
I'm trying to get this set up using these instructions:

[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

(is there a whole thread to go with this post? I can't seem to find it)

So far, no luck. I get this output:


```

$ sudo ossdetect -v
Detected Creative SB X-Fi (EARLY BETA)
Detected Generic USB audio device (BETA)
$ sudo ossinfo
Version info: OSS 4.0 (b1016/200807241457) (0x00040003) 
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 (pzs-desktop)

Number of audio devices:        2
Number of audio engines:        2
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: sbxfi0 Sound Blaster X-Fi (UAA)
    PCI device 1102:0005, subdevice 1102:6002
 2: ossusb0 USB audio core services


Mixer devices
 0: Sound Blaster X-Fi (UAA) (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (UAA) output   /dev/oss/sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (UAA) input    /dev/oss/sbxfi0/pcmin0  (device index 1)

```

but when I run Totem on an ogg file, I get "Failed to connect stream: Invalid argument"

I'm running 64 bit Ubuntu, if that makes any difference.

---

### Post by SeaJey on 2008-08-14
> is there a whole thread to go with this post? I can't seem to find it
[http://ubuntuforums.org/showthread.php?p=4874981#post4874981](http://ubuntuforums.org/showthread.php?p=4874981#post4874981)

---

