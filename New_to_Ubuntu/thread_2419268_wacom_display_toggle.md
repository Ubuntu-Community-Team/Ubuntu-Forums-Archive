---
title: "wacom display toggle"
date: 2019-05-19
forum: New to Ubuntu
---

### Post by tamtamx1332 on 2019-05-19
Hi guys, 
I'm trying to use display toggle for my wacom but since I have the "unable to find an output" issue I have to do this math calculation to solve the coordinate transform matrix but I'm not smart enough for that :P
I would be forever greatful if someone could do it for two monitors that have 1080p resolutions.
It's explained on this link.

[https://github.com/linuxwacom/xf86-input-wacom/wiki/Dual-and-Multi-Monitor-Set-Up](https://github.com/linuxwacom/xf86-input-wacom/wiki/Dual-and-Multi-Monitor-Set-Up)

when I do xinput xinput list-props "Wacom Cintiq 27QHD touch Pen stylus" I get this output.

Device 'Wacom Cintiq 27QHD touch Pen stylus':
    
    Coordinate Transformation Matrix (157):    0.775758, 0.000000, 0.224242, 0.000000, 0.500000, 0.000000, 0.000000, 0.000000, 1.000000
 

So then on the website it says to sett new coordinates you need to execute the command in this format:

xinput set-prop "Wacom Cintiq 27QHD touch Pen stylus" --type=float "Coordinate Transformation Matrix" 0.5 0 0 0 1 0 0 0 1

But those numbers have to be different for monitor 1 and monitor 2.

If someone has done this before please help.

Thanks in advance.

T

---

### Post by LwIh%*7 on 2019-06-03
Will this help? 

[https://ubuntuforums.org/showthread.php?t=1393775](https://ubuntuforums.org/showthread.php?t=1393775)

---

