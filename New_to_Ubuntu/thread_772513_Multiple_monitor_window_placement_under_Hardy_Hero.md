---
title: "Multiple monitor window placement under Hardy Heron"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by pzs on 2008-04-28
I have a dual monitor setup, where each virtual desktop is spread over two monitors. Under Gutsy, if I clicked on the Firefox icon (left hand monitor) and then (quickly) moved the mouse to the right hand monitor, the new Firefox windows would appear over there. 

Now, it briefly flicks up on the right hand monitor, but ultimately appears in the left hand monitor. Any idea how I fix this?

Peter

---

### Post by Hospadar on 2008-04-28
How are you dual screens set up? (dual x screen with xinerama, nvidia twinview, etc) and what video hardware and drivers are you using?

---

### Post by pzs on 2008-04-29
It's an Nvidia card but I have this in my xorg.conf:

Section "ServerLayout"
        Identifier     "Multihead layout"
        Screen      0  "Screen0" LeftOf "Screen1"
        Screen      1  "Screen1" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        Option      "Xinerama" "on"
        Option      "Clone" "off"
EndSection

which seems to suggest it's using Xinerama.

Peter

---

