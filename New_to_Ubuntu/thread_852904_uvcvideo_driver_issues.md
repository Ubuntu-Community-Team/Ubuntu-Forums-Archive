---
title: "uvcvideo driver issues"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by aestrivex on 2008-07-08
Brand new Creative Live! Cam Video IM Pro VF0410 webcam works in a very limited fashion.

Specifically, I've gotten it to work exclusively with luvcview and xawtv.  The device does not show up under /dev/video0/, which is why i don't understand why it appears to work with luvcview and xawtv.  I have not tested it very rigorously with these programs and so far I haven't managed to get any audio out of it at all.

As far as I can tell the uvcvideo driver is working properly.  The device is recognized by lsusb (USB code 041e:4063) and for all i can tell should be recognized and registered under /dev/video0/.

dmesg registered the following upon plugging in the camera:
```

[  978.624385] uvcvideo: Found UVC 1.00 device VF0410 Live! Cam Video IM Pro (041e:4063)
[  978.630912] input: VF0410 Live! Cam Video IM Pro as /devices/pci0000:00/0000:00:13.5/usb6/6-2/6-2:1.0/input/input7
[  978.687148] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 4:3:1: cannot get freq at ep 0x84
[  979.292450] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 4:3:1: cannot get freq at ep 0x84

```

I recognize that the driver may be unsupported for some applications, but the device is not working in ekiga at all for V4L1 or V4L2.  other people have definitely gotten UVC to work in ekiga.

I would love to get this camera running for web applications which access the camera using flash.



any sudden inspired flashes of genius?  i'd settle for average-to-mediocre ideas as well.


edit: i'm also running a 64 bit architecture.

---

