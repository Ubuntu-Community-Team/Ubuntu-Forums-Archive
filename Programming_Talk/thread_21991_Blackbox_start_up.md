---
title: "Blackbox start up"
date: 2005-03-25
forum: Programming Talk
---

### Post by saax on 2005-03-25
Hey

i installed blackbox on ubuntu everything ok but i dont know how to start it up 
if any1 know please help me step by step ,thx

---

### Post by cow_racer on 2005-03-25
[QUOTE=saax]Hey

i installed blackbox on ubuntu everything ok but i dont know how to start it up 
if any1 know please help me step by step ,thx[/QUOt]

Create a file /usr/share/xsession/blackbox.desktop
With the followng content.

[Desktop Entry]
Encoding=UTF-8
Name=BlackBox
Comment=Highly configurable and low resource X11 Window manager
Exec=blackbox
Terminal=False
TryExec=blackbox
Type=Application

[Window Manager]
SessionManaged=true


---------------
now log out.. 
You should see blackbox under session..  Select it and login in.

---

