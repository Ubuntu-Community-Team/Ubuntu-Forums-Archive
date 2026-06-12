---
title: "Mouse Scroll Wheel No Longer Works"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Patriot1776 on 2008-09-14
The scroll wheel of my USB Logitech Optical Wheel Mouse has stopped working.  Wheel-clicking still works, but scrolling doesn't.  Here's the mouse section of my xorg.conf file:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons" "true"
EndSection
```

Running with Hardy, 8.04.1, kernel 2.6.24-19.(24?)

Any ideas?

---

### Post by dRock1286 on 2008-09-14
hardware issue?

EDIT:  As in...it is the mouse that doesn't work properly.  Does it still work in windows or anything?

---

