---
title: "Setting Video resolution Xserver for Ubuntu 17.10 and 16.04.3"
date: 2018-01-02
forum: New to Ubuntu
---

### Post by oldbikerpete on 2018-01-02
I have two screens, one 1280x1024 via D-sub connector and a 1920x1080 via a HDMI connector - but only one connected at a time.
Without the 'bumblebee' driver for the NVIDIA N710 card, Ubuntu cannot identify the 1280x1024 screen so applies a 'safe' resolution of 1024x768.
Once I load the 'bumblebee' drivers, the Xserver complains the screen is set to a low resolution and won't allow itself to run until the issue is 'resolved' and insists on dialog windows which are far from helpful.

The 1920x1024 screen (when attached) plugs into a HDMI socket on the motherboard and uses the video hardware in the AX 370 chipset on the motherboard combined with the 6 GPU's in the CPU.
I don't know whether a driver for this hardware is loaded automatically during boot when Ubuntu sets the resolution of this screen to 800x600. Given the behaviour outlined above, I doubt it.

The full description of my hardware is given in this post.
[https://ubuntuforums.org/showthread.php?t=2381607](https://ubuntuforums.org/showthread.php?t=2381607)

I want to use the 1280x1024 screen only.

How can I force the Xserver to use this definition?

---

