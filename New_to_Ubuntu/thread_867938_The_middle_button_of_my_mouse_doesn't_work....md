---
title: "The middle button of my mouse doesn't work..."
date: 2008-07-23
forum: New to Ubuntu
---

### Post by protoz on 2008-07-23
Hi there,
I just installed ubuntu 8.04 using the VMWare. Everything seems to work but my mouse doesn't work well. The middle button of my mouse doesn't work at all. Does anyone know how to fix this problem? I'd really appreciate your help.


protoz

---

### Post by protoz on 2008-07-23
Thank god I finally solved this problem.
So boring to use virtual machines:)
Here is the solution:
Run this command in the terminal:
```
$sudo gedit /etc/X11/xorg.conf
```
Then change the section beginning with
```
Section "InputDevice"
Identifier "Configured Mouse" 
```
to the context as follows:
```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "vmmouse"
Option "Protocol" "ImPS/2"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "yes"
EndSection
```
Then press Ctrl+Alt+Backspace to restart the X, and everything's ok.

---

