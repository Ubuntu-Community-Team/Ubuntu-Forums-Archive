---
title: "Error while running Qt application with wayland"
date: 2020-12-23
forum: New to Ubuntu
---

### Post by amolk2 on 2020-12-23
[COLOR=#333333][FONT=&quot]Hi,[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I am trying to run simple Qt application Hello World on Ubuntu 18.04 desktop with wayland. Following commands I tried.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]$ export QT_QPA_PLATFORM=wayland
$ ./qello
also tried with following command
$ ./qello -platform wayland[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]but I am getting the same error.
$ ./qello -platform wayland
Failed to create wl_display (No such file or directory)
qt.qpa.plugin: Could not load the Qt platform plugin "wayland" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, wayland-egl, wayland, wayland-xcomposite-egl, wayland-xcomposite-glx, webgl, xcb.
Aborted (core dumped)[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I have installed weston-launch. I am able to run that in virtual terminal ctrl+alt+F2.
Do I need install any package or need to do some configuration?[/FONT][/COLOR]

---

### Post by TheFu on 2020-12-23
Before you login, did you select the Wayland GUI, not the X11 GUI?  It is probably a dumb question from me, but needs to be asked.  
Maybe this info here: [https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/) will explain it better?

---

### Post by wildmanne39 on 2020-12-24
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

