---
title: "Get The Cyborg M.M.O.7 Mouse To Work"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by Narcas on 2013-02-25
Hello!
I'm a newb to Ubuntu and I have a Saitek Cyborg M.M.O.7 Gaming mouse. But I wonder how I can get it to work properly with Ubuntu. When I use it, it like stays in one window and I can't click somewhere else. But I can move the cursor around. I've searched through other threads but I haven't got the right answer. And I'm not this mouse's first owner.

Here's my mouse config file, that I tried to edit.

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg M.M.O.7 Gaming Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "Buttons"        "24"
        Option "ButtonMapping" "1 2 3 4 5 0 0 8 9 10 11 12 13 14 15 16 17 7 6 0$
        Option "ZAxisMapping" "4 5 6 7"
        Option "AutoReleaseButtons" "20 21 22 23 24"
EndSection
```

---

### Post by Narcas on 2013-02-26
It works if I log out with Ctrl+Alt+Delete, but I need a permanent fix, anybody? Thanks!

---

### Post by Narcas on 2013-03-08
If there's no solution for this I'll have to move to windows.. =/

---

