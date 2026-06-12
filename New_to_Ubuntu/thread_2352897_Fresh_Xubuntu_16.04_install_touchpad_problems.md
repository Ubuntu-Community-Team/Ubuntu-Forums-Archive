---
title: "Fresh Xubuntu 16.04 install touchpad problems"
date: 2017-02-16
forum: New to Ubuntu
---

### Post by guccimucci on 2017-02-16
So I just installed Xubuntu 16.04.1 on my laptop and after adding software updates my touchpad started to act strange. It is very sensitive at times and then stops working for a couple of seconds. Editing the settings from 'mouse and touchpad' doesn't help. Moreover, I'm used to natural scrolling, but this has reversed also. Somehow even one-finger scrolling is enabled although I've never wanted to use it. This means that when I move my cursor to battery icon for example then I can very rapidly increase or decrease my screen brightness by only touching my touchpad with one finger, which is also annoying. How could I fix this and is it possible that a recent update caused this? I really couldn't do anything else than install software updates, restart my computer and the problem just appeared. 

My laptop is Dell Latitude E7470, I've used Ubuntu, Ubuntu MATE, Gnome, Manjaro and I have had no issues with my touchpad.

---

### Post by vanadium on 2017-02-17
Check [here](https://ubuntuforums.org/showthread.php?t=2316240): perhaps also in your case two drivers are in use, in which case settings you apply through "Mouse & Touchpad" may not have effect. The thread indicates how you can disable one of the two using an xorg config file.

---

### Post by guccimucci on 2017-02-17
I don't think that's the issue here. 
> xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M705                               id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad            id=13    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint Stick               id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                        id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; DELL Wireless hotkeys                       id=15    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=16    [slave  keyboard (3)]


This is the output for xinput list command. I do not know what this "AlpsPS/2 ALPS DualPoint Stick" stands for.

Having further investigated the issue I've found that the left part of the touchpad works fine, but the right part has 'one-finger-scroll' enabled, which seems to confuse the system since when I move around the right part gets both 'scrolling' and 'moving' signals at the same time. Maybe I can fix it by disabling or editing something from here:
> xinput --watch-props 13
Device 'AlpsPS/2 ALPS DualPoint TouchPad':
    Device Enabled (139):    1
    Coordinate Transformation Matrix (141):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (270):    1
    Device Accel Constant Deceleration (271):    2.500000
    Device Accel Adaptive Deceleration (272):    1.000000
    Device Accel Velocity Scaling (273):    12.500000
    Synaptics Edges (294):    268, 1524, 230, 1306
    Synaptics Finger (295):    12, 15, 0
    Synaptics Tap Time (296):    180
    Synaptics Tap Move (297):    103
    Synaptics Tap Durations (298):    180, 100, 100
    Synaptics ClickPad (299):    0
    Synaptics Middle Button Timeout (300):    75
    Synaptics Two-Finger Pressure (301):    141
    Synaptics Two-Finger Width (302):    7
    Synaptics Scrolling Distance (303):    47, 47
    Synaptics Edge Scrolling (304):    1, 0, 0
    Synaptics Two-Finger Scrolling (305):    1, 0
    Synaptics Move Speed (306):    1.000000, 1.750000, 0.084746, 0.000000
    Synaptics Off (307):    1
    Synaptics Locked Drags (308):    0
    Synaptics Locked Drags Timeout (309):    5000
    Synaptics Tap Action (310):    2, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (311):    1, 1, 0
    Synaptics Circular Scrolling (312):    0
    Synaptics Circular Scrolling Distance (313):    0.100000
    Synaptics Circular Scrolling Trigger (314):    0
    Synaptics Circular Pad (315):    0
    Synaptics Palm Detection (316):    0
    Synaptics Palm Dimensions (317):    10, 100
    Synaptics Coasting Speed (318):    20.000000, 50.000000
    Synaptics Pressure Motion (319):    15, 80
    Synaptics Pressure Motion Factor (320):    1.000000, 1.000000
    Synaptics Resolution Detect (321):    1
    Synaptics Grab Event Device (322):    0
    Synaptics Gestures (323):    1
    Synaptics Capabilities (324):    1, 1, 1, 1, 1, 1, 0
    Synaptics Pad Resolution (325):    48, 45
    Synaptics Area (326):    0, 0, 0, 0
    Synaptics Noise Cancellation (327):    11, 11
    Device Product ID (259):    2, 8
    Device Node (260):    "/dev/input/event7"
Property 'Synaptics Off' changed.
    Synaptics Off (307):    0



---

### Post by Keith_Helms on 2017-02-17
I didn't care for all the tap and scroll functions that were enabled by default on my touchpad in Xubuntu, so I have a startup script that turns off the annoying stuff
```

#!/bin/bash

/usr/bin/synclient PalmDetect=1
/usr/bin/synclient PalmMinWidth=5
/usr/bin/synclient RTCornerButton=0
/usr/bin/synclient RBCornerButton=0
/usr/bin/synclient ClickFinger1=0
/usr/bin/synclient ClickFinger2=0
/usr/bin/synclient VertEdgeScroll=0
/usr/bin/synclient HorizEdgeScroll=0
/usr/bin/synclient VertTwoFingerScroll=0

```

I added the script to the Application Autostart tab under the Session and Startup option and it runs whenever I log in.

---

