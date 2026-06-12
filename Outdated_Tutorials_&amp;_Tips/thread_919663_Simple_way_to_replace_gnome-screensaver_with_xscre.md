---
title: "Simple way to replace gnome-screensaver with xscreensaver"
date: 2008-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Apocrathia on 2008-09-14
I have always been partial to the xscreensaver setup over anything. I am an avid mac user and have the entire xscreensaver library on all of my macs. When I discovered that the xscreensavers had been taken out of ubuntu I was very sad. If you were too heres 3 very simple terminal commands that will rid you of the setting-less gnome screensaver:

First: just remove the gnome-screensaver package all together
```
sudo aptitude remove gnome-screensaver
```
Second: we have to kill the process of the original gnome-screensaver, without the package, it will not ever restart.
```
sudo killall gnome-screensaver
```
Third: install teh x! (with all the bells and whistles)
```
sudo apt-get install xscreensaver xscreensaver-data-extra xscreensaver-gl-extra
```

there you go, set it up the same way you did your original screensaver, the options are just expanded.

---

