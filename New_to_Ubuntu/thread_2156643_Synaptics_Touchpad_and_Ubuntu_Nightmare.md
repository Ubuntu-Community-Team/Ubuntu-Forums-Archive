---
title: "Synaptics Touchpad and Ubuntu Nightmare"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by cylent on 2013-06-22
I am not sure if this will ever be resolved or not. frankly i skipped version 12.x for ubuntu in hopes 13.x would have it fixed.
well... now i have 13.04 installed and the same problem persists! why cant they get this correct?

The fact remains the Synaptics touchpad on this X220 IBM Lenovo laptop is drama ... not just my laptop ... 

if i wanted to tap the cursor would start dancing. with every tap i have to bring the cursor back to what i wanted to click on and try to tap again. the moment i try to tap it would do a small "dance" ... its just NOT stable.

I should not be required to find an alternate laptop that doesnt have a Synaptics touchpad in it. 
In the meantime I have spent two days searching for a solution and simply got no where!

I am not sure which of these values needs to be changed:

```
cylent@ThinkPad-X220:~$ xinput list-props "SynPS/2 Synaptics TouchPad" 
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (133):    1
    Coordinate Transformation Matrix (135):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (256):    1
    Device Accel Constant Deceleration (257):    2.500000
    Device Accel Adaptive Deceleration (258):    1.000000
    Device Accel Velocity Scaling (259):    12.500000
    Synaptics Edges (260):    1752, 5192, 1620, 4236
    Synaptics Finger (261):    12, 35, 255
    Synaptics Tap Time (262):    150
    Synaptics Tap Move (263):    221
    Synaptics Tap Durations (264):    180, 180, 100
    Synaptics ClickPad (265):    1
    Synaptics Tap FastTap (266):    1
    Synaptics Middle Button Timeout (267):    0
    Synaptics Two-Finger Pressure (268):    282
    Synaptics Two-Finger Width (269):    7
    Synaptics Scrolling Distance (270):    100, 100
    Synaptics Edge Scrolling (271):    0, 0, 0
    Synaptics Two-Finger Scrolling (272):    1, 0
    Synaptics Move Speed (273):    0.000000, 0.000000, 0.000000, 40.000000
    Synaptics Edge Motion Pressure (274):    30, 160
    Synaptics Edge Motion Speed (275):    1, 401
    Synaptics Edge Motion Always (276):    0
    Synaptics Off (277):    0
    Synaptics Locked Drags (278):    0
    Synaptics Locked Drags Timeout (279):    5000
    Synaptics Tap Action (280):    0, 0, 0, 0, 1, 3, 0
    Synaptics Click Action (281):    1, 3, 0
    Synaptics Circular Scrolling (282):    0
    Synaptics Circular Scrolling Distance (283):    0.100007
    Synaptics Circular Scrolling Trigger (284):    0
    Synaptics Circular Pad (285):    0
    Synaptics Palm Detection (286):    0
    Synaptics Palm Dimensions (287):    10, 200
    Synaptics Coasting Speed (288):    0.000000, 50.000000
    Synaptics Pressure Motion (289):    30, 160
    Synaptics Pressure Motion Factor (290):    1.000000, 1.000000
    Synaptics Resolution Detect (291):    1
    Synaptics Grab Event Device (292):    1
    Synaptics Gestures (293):    0
    Synaptics Capabilities (294):    1, 0, 0, 1, 1, 1, 1
    Synaptics Pad Resolution (295):    129, 75
    Synaptics Area (296):    0, 0, 0, 0
    Synaptics Soft Button Areas (297):    3472, 0, 3900, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (298):    8, 8
    Device Product ID (250):    2, 7
    Device Node (251):    "/dev/input/event6"
cylent@ThinkPad-X220:~$ 

```

If anybody can help out with this please please please say something.

---

