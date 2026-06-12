---
title: "GLXGEARS speed very slow"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-11-08
In 8.10 I get the following error in glxgears and my speed is:
> terminator@terminator-desktop:~$ glxgears
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
NVIDIA: Direct rendering failed; attempting indirect rendering.
3017 frames in 5.0 seconds = 602.033 FPS
3320 frames in 5.0 seconds = 663.258 FPS
3700 frames in 5.0 seconds = 739.746 FPS
3640 frames in 5.0 seconds = 726.667 FPS
3710 frames in 5.0 seconds = 741.988 FPS
3710 frames in 5.0 seconds = 741.795 FPS
3720 frames in 5.0 seconds = 741.804 FPS
3720 frames in 5.0 seconds = 743.248 FPS
3700 frames in 5.0 seconds = 739.499 FPS


In 8.04.1 my speed has been in the 1300 range.
How would I go about upping my glxgear speed in 8.10?
How would I fix the direct rendering error?

---

### Post by alienexplorers on 2008-11-08
Is there another benchmarking program that can be used with Ubuntu 8.xx?

---

### Post by alienexplorers on 2008-11-08
Modified /dev/nvidiactl and /dev/nvidia0 so that I was the owner instead of root.  I am now getting speeds of 1350 fps.  Not great, but better than I had before.  Also noticed that after changing owner of those 2 files that direct rendering is now working.

---

