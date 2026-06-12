---
title: "How to properly set up an X11 startup script"
date: 2017-02-24
forum: New to Ubuntu
---

### Post by vanillasnake21 on 2017-02-24
I'm trying to get my desktop to startup with the background and resolution that I have preset, however I can't seem to figure out how to do this. So far I've tried making a ~./.xprofile with xrandr and feh commands in it, but I think my window manager doesn't read the xprofile, I then tried to use xorg.conf and put it in /etc/X11 with settings I found online, the xserver says it's using it but my resolution stays the same. Right now what I have is just a sessionInit script that I call when I log into the window manager that sets resolution and background, however I'd like to get rid of it and do it the right way. 

This is my system info: Running in VMWare on Windows 10, installed Ubuntu minimal, using Awesome window manager. I start my x session with startx manually. Thanks.

---

### Post by altlock on 2017-02-26
You should try moving all startup commands for X to "~/.xinitrc". The Ubuntu wiki has a nice page about how to use "~/.xinitrc": [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession).

---

