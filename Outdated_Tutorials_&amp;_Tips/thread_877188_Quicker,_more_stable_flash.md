---
title: "Quicker, more stable flash"
date: 2008-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by kjander on 2008-08-01
This is just a quick tip I found useful. Im using a slower laptop, so Flash has been a bit of trouble for me. Running slowly (videos in flash had very low fps) and occasionaly crashing, causing Firefox to close. A simple change I found:
edit the firefoxrc file
```
sudo gedit /etc/firefox/firefixrc
```
this is the whole contents of my file:
```
# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See https://launchpad.net/bugs/29760.
```
I changed where it says "none" to "padsp" (to allow firefox to use the pulseaudio server) and now flash (and I imagine, any sound served over the browser) is now much smoother and more reliable. Maybe I'm the last to know about this, but thought I'd mention it, in case someone else could use the tip. Also, if flash is a problem for you like me, the flashblock extension to firefox is great! prevents flash-based ads and such from slowing down the browser unexpectedly. I highly recommend it!

---

