---
title: "Ubuntu won't display at native resolution"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by Satki on 2012-05-25
Hi, this seems to be a fairly common problem with Ubuntu, but none of the solutions I've googled seem to work. My monitor has a native resolution of 1280x1024, but in both the display settings and with xrandr, it is not listed (the maximum output is at 1024x768). I've tried adding the native resolution using xrandr, but with no luck. 
The other solution that I've come across involves editing xorg.conf. But, for whatever reason, this doesn't exist (in /etc/X11/). Any help would be appreciated.

---

### Post by wojox on 2012-05-25
What video card/chipset are you running?
```
lspci | grep VGA
```

---

