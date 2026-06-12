---
title: "Screensaver gconf and Ati"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by dwarx on 2008-09-17
Hello, I am a complete newbie to Ubuntu. I was having problems with 3D screensavers due to the typical Ati problems (Radeon X200) which apparently is not very user friendly with Ubuntu, I've had drivers crash, not boot, etc... I've just recently added drivers which just let me use the advanced visual in the gui alone. 

So due to video problem  I couldn't switch screensavers in the System > Preferences > Screensaver options because it would constantly crash the whole system. So I edited with gconf-editor to disable the screensaver. 

Now, I want to set it up to blank-screen, but I can't because I don't know what I exactly edited in the gconf-editor. When I try to lock the screen I get the following error:

** Message: Screensaver is not running!

Can anyone post the default values so I can now what I changed or how to restore it atleast?
I'm running Ubuntu 8.04 Hardy Heron. 

Also, if anyone has an absolute winning driver for Ati Radeon X200 I would much appreciate it, I think my video card is very unstable.

---

### Post by dwarx on 2008-09-17
Umm... Okay I got the screensaver running, so just the driver pending, if not, forget it :)!

---

### Post by raviproff on 2009-02-27
I got same error massage while click on Lock Button, same time screen saver also not working for me!!!

```
root@ServerOSS:/home/ravi# gnome-screensaver

** (gnome-screensaver:6690): WARNING **: failed to register with the message bus
root@ServerOSS:/home/ravi# gnome-settings-daemon

** (gnome-settings-daemon:6693): WARNING **: Couldn't connect to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (gnome-settings-daemon:6693): WARNING **: Could not get a connection to the bus
root@ServerOSS:/home/ravi# dbus-launch
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-pAGCa0Z7tV,guid=0b02092101110e077f9ad20549a7ede9
DBUS_SESSION_BUS_PID=6698
DBUS_SESSION_BUS_WINDOWID=35651585
root@ServerOSS:/home/ravi# ls /tmp/
gconfd-ravi  gconfd-root  keyring-FxoAZI  orbit-ravi  orbit-root  pulse-ravi  seahorse-HRyKSY  tmp.VFbKHV5480  Tracker-ravi.6440  virtual-ravi.q5OP2K
root@ServerOSS:/home/ravi# gnome-screensaver-command
** Message: Failed to connect to the D-BUS daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
root@ServerOSS:/home/ravi# gnome-screensaver

** (gnome-screensaver:6701): WARNING **: failed to register with the message bus
root@ServerOSS:/home/ravi# 

```

Any idea!!!

---

