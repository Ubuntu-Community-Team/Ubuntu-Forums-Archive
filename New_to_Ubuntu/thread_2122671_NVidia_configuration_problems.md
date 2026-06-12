---
title: "NVidia configuration problems"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by Elronius on 2013-03-05
Ever since I updated my kernel, my resolution has gone caddywompus. It's much lower than before, and after trying a possible solution, it's now even lower.

I just tried restarting and received the following error:

None of the selected modes were compatible with the possible modes:
Trying modes for CRTC 81.

CRTC 81: trying mode 800x600 @   0 Hz with output at 1024x768@61Hz (pass 0)
CRTC 81: trying mode 640x480 @ 60 Hz with output at 1024x768@61Hz (pass 0)
CRTC 81: trying mode 640x400 @   0 Hz with output at 1024x768@61Hz (pass 0)
CRTC 81: trying mode 320x400 @   0 Hz with output at 1024x768@61Hz (pass 0)
CRTC 81: trying mode 800x600 @   0 Hz with output at 1024x768@61Hz (pass 1)
CRTC 81: trying mode 640x480 @ 60 Hz with output at 1024x768@61Hz (pass 1)
CRTC 81: trying mode 640x400 @   0 Hz with output at 1024x768@61Hz (pass 1)
CRTC 81: trying mode 320x400 @   0 Hz with output at 1024x768@61Hz (pass 1)

When I try to access my video card, it gives me this error:
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
(I tried this before the last restart unsuccessfully.)

Any ideas? I'm using 32-bit 12.04.2 LTS with Unity :p

---

### Post by Mark_in_Hollywood on 2013-03-06
Let us try to keep this as simple as possible. On your next reboot, select the Grub Recovery and then the Update Grub option. If that helps, mark this post a solved by changing the prefix from Ubuntu to Solved in Advanced edit.

---

### Post by vamp774 on 2013-03-07
What driver were you using before you had problems?  Are you able to boot into Ubuntu even with those errors?  If so, NVIDIA has proprietary drivers for Linux.  Under additional drivers you can install them.  What model is the gfx card?

---

