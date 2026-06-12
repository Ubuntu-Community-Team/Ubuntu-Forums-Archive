---
title: "Raspberry Pi 3 - Remote desktop with tightvnc - blank gray screen?"
date: 2017-01-21
forum: New to Ubuntu
---

### Post by timg11 on 2017-01-21
I've installed TightVNCserver on the Pi, and ran the server to set up password, then ran again
I'm using TightVNCviewer from the client. I connect to screen 1 with 192.168.1.123:5901. 
The viewer prompts for the password and then connects. But the display is only an X cursor on an entirely empty, nonresponsive window. 
How can I remotely access the Mate desktop that is shown on the Pi's HDMI output?

Here is the vnc server log from the Pi:

```
cat Pi3:1.log
21/01/17 15:49:24 Xvnc version TightVNC-1.3.10
21/01/17 15:49:24 Copyright (C) 2000-2009 TightVNC Group
21/01/17 15:49:24 Copyright (C) 1999 AT&T Laboratories Cambridge
21/01/17 15:49:24 All Rights Reserved.
21/01/17 15:49:24 See http://www.tightvnc.com/ for information on TightVNC
21/01/17 15:49:24 Desktop name 'X' (Pi3:1)
21/01/17 15:49:24 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
21/01/17 15:49:24 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/pi/.Xresources'

```

---

### Post by TheFu on 2017-01-21
Have you tried right-clicking on the desktop to see a menu?  Normal behavior when no DE is specified in the vnc-startup.  If there isn't a window manager running, then the right-click won't work either. I would usually open a terminal <ctl><alt>-t and run a window manager then whatever panel/DE I like.  Mate should work, if you add that to the vnc-server startup.

A reasonable how-to for 16.04:
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)
You don't just get to install the vnc-server. Manual configuration is mandatory.
Inside your LAN, you can leave out the ssh part, but I prefer to always use it, so the VNC connection is never allowed except from 'localhost' - much more secure that way.

The setup is a little different for 14.04 (no systemd).

---

### Post by kevdog on 2017-01-22
Kind of unrelated, however did you just install the X-window system?  For your purposes, a console log in isn't sufficiient?

---

