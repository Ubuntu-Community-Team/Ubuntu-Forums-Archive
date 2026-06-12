---
title: "not able to create vnc which have multiple desktops having copy paste etc"
date: 2020-01-23
forum: New to Ubuntu
---

### Post by rashidhbti02 on 2020-01-23
Hi Guys,

I am trying to create vnc by below script:
[COLOR=#1E889B]#!/bin/sh
[/COLOR][COLOR=#1E889B][/COLOR]
[COLOR=#228B22]# Uncomment the following two lines for normal desktop:[/COLOR]
[COLOR=#228B22]# unset SESSION_MANAGER[/COLOR]
[COLOR=#228B22]# exec /etc/X11/xinit/xinitrc[/COLOR]

[ -x /etc/vnc/xstartup ] && [COLOR=#658B00]exec[/COLOR] /etc/vnc/xstartup
[ -r [COLOR=#00688B]$HOME[/COLOR]/.Xresources ] && xrdb [COLOR=#00688B]$HOME[/COLOR]/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title [COLOR=#CD5555]"[/COLOR][COLOR=#00688B]$VNCDESKTOP[/COLOR][COLOR=#CD5555] Desktop"[/COLOR] &
x-window-manager &

gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &

===
But after creating, I am seeing copy paste is not working. 
I am not able to see preferances etc to set keyboard shortcuts.
I am not able to open multiple shells in same window and many problems.
No right click option working.

How to solve all those?

Below is my machine:
uname -a>>
Linux <confidentialmachine> 4.4.0-130-generic #156-Ubuntu SMP Thu Jun 14 08:53:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

lsb_release -a>>
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


Do we have kde supported on this?

---

### Post by rashidhbti02 on 2020-01-24
Can somebody please help me on this?

---

