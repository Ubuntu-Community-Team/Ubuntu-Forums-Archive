---
title: "Help with VidCutter"
date: 2019-10-05
forum: New to Ubuntu
---

### Post by wombat71 on 2019-10-05
Hello All,
Am fairly new to Ubuntu and am trying to use VidCutter as a very simple way of cutting and saving parts of existing video clips in 18.04..
Other alternatives have far more features that I really dont want.
Vid Cutter works very very well in Windows but seems to 'freeze' halfway through in Ubuntu.
There appears to be a lot of people with exactly the same problem but so far noone I can find seems to have found the fix.
Can anyyone help please ?
Thanks,
wombat71

---

### Post by TheFu on 2019-10-05
VidCutter is a flatpak and hasn't worked for me since the dev switched to that packaging.  However, if you open a bug report on the project site, the team is pretty responsive. The startup command is:
```
$ /usr/bin/flatpak  run com.ozmartians.VidCutter $@
qt.qpa.xcb: could not connect to display 
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

Available platform plugins are: eglfs, minimal, minimalegl, offscreen, vnc, wayland-egl, wayland, wayland-xcomposite-egl, wayland-xcomposite-glx, xcb.
```

I'm pretty unhappy with the flatpak updates asking for passwords continuously.  Boo.  Just updated everything for vidcutter and the same error is happening.

---

