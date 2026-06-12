---
title: "Sound not working: Intel ICH5"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-08-16
My sound is not working on my Intel ICH5:

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Dell Unknown device 0174
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at ee00 [size=256]
        I/O ports at edc0 [size=64]
        Memory at febffa00 (32-bit, non-prefetchable) [size=512]
        Memory at febff900 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

```

That is what lspci -v returned. In the SoundTroubleshooting guide, it shows my driver as installed, my card recognized, everything working perfectly. Except I can't hear anything! I've tried plugging my speakers in on every speaker/mic port. No luck. But I'm pretty sure it's this... (me trying to play MP3 in xmms)

```
** WARNING **: oss_open(): Failed to open audio device (/dev/dsp): Device or resource busy
```

All ALSA drivers are installed etc. This also confirms it being busy:

```
brad@debian-seed:~$ /dev/urandom > /dev/dsp
bash: /dev/dsp: Device or resource busy
```

Sound cards from /dev:

```
brad@debian-seed:~$ ls /dev | grep dsp
adsp
dsp
```

Thanks, hope someone can help!!

---

### Post by spiderbatdad on 2008-08-16
Check that you have the alsa packages shown in the screen shot below. Configure sound options under System>>Preferences>>Sound. Make sure master AND PCM are both up: ```
alsamixer
```

---

### Post by linkmaster03 on 2008-08-16
Totem plays sound now, but xmms still says /dev/dsp is busy. I had all programs closed except the one I was testing.

---

