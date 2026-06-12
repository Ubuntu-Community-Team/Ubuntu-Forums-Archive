---
title: "how to save arandr configuration"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by Dor_Zohar on 2014-06-14
Hi

I want to save the configuration I set with arandr so everytime that Ill reboot the system it will remain.
how do I do it? thanks in advance :)

---

### Post by TheFu on 2014-06-14
I don't know about arandr (not loaded here) - but xrandr (a close relative) accepts command line parameters. lxrandr does not. These can be placed into a script to be run whenever you like, under whatever userid is needed. Something like:
[B]$ sudo xrandr --output DFP2 --mode 1280x720
[/B]

Or you could fiddle with the /etc/X11/xorg.conf file. That's the really old-school way and tends to work the best - though I've had luck with xrandr too.

All options supported by any (almost) program is spelled out inside the man page for that program.  **man arandr**

---

### Post by steeldriver on 2014-06-14
AFAIK arandr is just a GUI interface to xrandr - it's been a while since I played with it, but there should be a 'Save' (disk) icon on the main menu

It saves a little shell script (#!/bin/sh) that contains the corresponding xrandr command - by default in a ~/.screenlayout directory

In order to have it autorun you would need to add the script as a startup application to your session - I don't think the session actually reads the ~/.screenlayout dir by default

---

