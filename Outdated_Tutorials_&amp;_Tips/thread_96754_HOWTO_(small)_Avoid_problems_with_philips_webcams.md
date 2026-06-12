---
title: "HOWTO (small): Avoid problems with philips webcams"
date: 2005-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by ember on 2005-11-29
Well, this is not exactly a howto, however:

If you own a philips 820/830/840K webcam (pwc driver) and it does not work and tells you something like:

[4294758.333000] pwc Failed to set LED on/off time.
[4294758.336000] pwc set_video_mode(176x144 @ 10, palette 15).
[4294758.336000] pwc decode_size = 1.
[4294758.336000] pwc Using alternate setting 1.
[4294758.336000] pwc Failed to set video mode QSIF@10 fps; return code = -32
[4294758.336000] pwc set_video_mode(160x120 @ 10, palette 15).
[4294758.336000] pwc decode_size = 1.
[4294758.336000] pwc Using alternate setting 1.
[4294758.337000] pwc Failed to set video mode QSIF@10 fps; return code = -32


Then you are possibly connecting it via an USB-2 hub. This causes the webcam not to work properly. If you want it to work, directly connect it to your computer - it seems this is a known problem with USB-2 support in the linux kernel.

Best,
ember

---

### Post by Jingo on 2006-01-10
Thanks. Same goes for Logitech Quickcam 3000 Pro, which also uses pwc.

Is there filed a bug?

Sure this is not a pwc bug?

---

### Post by chele on 2006-01-14
EasyCam [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") is a cool utility to update, download and build drivers for many webcams.

---

