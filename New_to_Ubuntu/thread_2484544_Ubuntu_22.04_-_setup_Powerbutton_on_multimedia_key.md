---
title: "Ubuntu 22.04 - setup Powerbutton on multimedia keyboard"
date: 2023-03-02
forum: New to Ubuntu
---

### Post by francwalter on 2023-03-02
Hallo

I have installed Ubuntu 22.04 on my Desktop Computer where I have an old PS2-Keyboard attached with some Multimedia keys on it. One of the keys is a Hibernate Button, under Windows at least. Under Ubuntu it does Standby, but not Hibernate.
I just activated Hibernate (see [my post in german Ubuntuforum]("http://://forum.ubuntuusers.de/topic/ubuntu-neben-windows-installiert-alert-uuid-do/") )
I want to have it too as hibernate button under Ubuntu, how can I set it up?

I found the app Keytouch but I cannot install it, seems too old.
In settings, I dont find the special keys (media and power).
Is there an actual keyboard mapping tool for 22.04?

Thank.frank

---

### Post by TheFu on 2023-03-02
If you use X/Windows, there are a number of tools to capture the keycode each key causes. **xev** is the main one.  Then you can use **xdotool** to have that keypress do anything you like that can be scripted, including hibernation. Most WMs support capturing keypresses and calling programs/scripts.  openbox, fluxbox, fvwm all do.  I use fvwm on 20.04.  22.04 is a bit too new for me.  In the "Users Guide" for your specific flavor, there's usually a page on custom keyboard shortcuts. [https://help.ubuntu.com/lts/ubuntu-help/keyboard-shortcuts-set.html.en](https://help.ubuntu.com/lts/ubuntu-help/keyboard-shortcuts-set.html.en) is for Gnome.

I have no clue how or if Wayland supports this. Maybe it is seamless?  Most X-Tools don't seem to work under Wayland. xdotool doesn't. Think Wayland has a 'ydotool' that supports a subset of xdotool's capabilities.

---

