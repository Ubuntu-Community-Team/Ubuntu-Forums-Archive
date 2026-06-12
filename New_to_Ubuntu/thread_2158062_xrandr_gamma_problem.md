---
title: "xrandr gamma problem"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by adilip on 2013-06-27
Hi,

My resolution abruptly changed, and when I enter "xrandr" in terminal I get:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0*

Previously, I'd be able to get different resolutions that I could change to but now I don't have that. I only moved onto ubuntu 2 days ago so really simple answers please!

Also I'm on ubuntu 13.04

---

### Post by cwsnyder on 2013-06-29
Check your connections to your display from your computer. ** xrandr** is reporting a problem with properly detecting your display.  If your resolution choices were available after installation, but are not now, that is your most likely problem.

---

