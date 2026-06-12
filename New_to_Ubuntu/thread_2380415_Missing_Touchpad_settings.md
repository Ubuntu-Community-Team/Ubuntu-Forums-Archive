---
title: "Missing Touchpad settings"
date: 2017-12-17
forum: New to Ubuntu
---

### Post by knightshuffler on 2017-12-17
Hi everyone
I just moved from Linux Mint to UbuntuGnome 16.04.3 and I'm facing some issues with using my touchpad.
The settings don't show any touchpad settings
[IMG]https://i.imgur.com/M0iWiyO.png[/IMG]

I can use my touchpad just fine but I can't use natural scrolling or configure what tapping on the touchpad with how many figers does.
Here's an output from doing xinput:
[IMG]https://i.imgur.com/FGXFz7Y.png[/IMG]

There are two touchpads listed there with IDs 12 and 14; I'm not sure why this is or which one is my laptop's touchpad.
(If it's any help my laptop is a Dell Inspiron 1500 series)

Here are the outputs on checking the xinput properties of devices 12 and 14:

```

swagat@swagat-ubuntu-Inspiron-5558:~$ xinput list-props 12
Device 'DLLC6AE:00 06CB:75BF Touchpad':
    Device Enabled (169):    1
    Coordinate Transformation Matrix (171):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (291):    1
    Device Accel Constant Deceleration (292):    2.500000
    Device Accel Adaptive Deceleration (293):    1.000000
    Device Accel Velocity Scaling (294):    12.500000
    Synaptics Edges (295):    49, 1180, 50, 879
    Synaptics Finger (296):    25, 30, 0
    Synaptics Tap Time (297):    180
    Synaptics Tap Move (298):    67
    Synaptics Tap Durations (299):    180, 180, 100
    Synaptics ClickPad (300):    1
    Synaptics Middle Button Timeout (301):    0
    Synaptics Two-Finger Pressure (302):    282
    Synaptics Two-Finger Width (303):    7
    Synaptics Scrolling Distance (304):    30, 30
    Synaptics Edge Scrolling (305):    0, 0, 0
    Synaptics Two-Finger Scrolling (306):    1, 1
    Synaptics Move Speed (307):    1.000000, 1.750000, 0.129870, 0.000000
    Synaptics Off (308):    0
    Synaptics Locked Drags (309):    0
    Synaptics Locked Drags Timeout (310):    5000
    Synaptics Tap Action (311):    0, 0, 0, 0, 0, 0, 0
    Synaptics Click Action (312):    1, 3, 0
    Synaptics Circular Scrolling (313):    0
    Synaptics Circular Scrolling Distance (314):    0.100000
    Synaptics Circular Scrolling Trigger (315):    0
    Synaptics Circular Pad (316):    0
    Synaptics Palm Detection (317):    0
    Synaptics Palm Dimensions (318):    10, 200
    Synaptics Coasting Speed (319):    20.000000, 50.000000
    Synaptics Pressure Motion (320):    30, 160
    Synaptics Pressure Motion Factor (321):    1.000000, 1.000000
    Synaptics Resolution Detect (322):    1
    Synaptics Grab Event Device (323):    0
    Synaptics Gestures (324):    1
    Synaptics Capabilities (325):    1, 0, 0, 1, 1, 0, 0
    Synaptics Pad Resolution (326):    12, 12
    Synaptics Area (327):    0, 0, 0, 0
    Synaptics Soft Button Areas (328):    614, 0, 761, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (329):    7, 7
    Device Product ID (286):    1739, 30143
    Device Node (287):    "/dev/input/event14"


```

```

swagat@swagat-ubuntu-Inspiron-5558:~$ xinput list-props 14
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (169):    1
    Coordinate Transformation Matrix (171):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (291):    1
    Device Accel Constant Deceleration (292):    2.500000
    Device Accel Adaptive Deceleration (293):    1.000000
    Device Accel Velocity Scaling (294):    12.500000
    Synaptics Edges (295):    1585, 5357, 1446, 4408
    Synaptics Finger (296):    25, 30, 0
    Synaptics Tap Time (297):    180
    Synaptics Tap Move (298):    245
    Synaptics Tap Durations (299):    180, 180, 100
    Synaptics ClickPad (300):    1
    Synaptics Middle Button Timeout (301):    0
    Synaptics Two-Finger Pressure (302):    282
    Synaptics Two-Finger Width (303):    7
    Synaptics Scrolling Distance (304):    -111, -111
    Synaptics Edge Scrolling (305):    1, 1, 0
    Synaptics Two-Finger Scrolling (306):    1, 1
    Synaptics Move Speed (307):    1.000000, 1.750000, 0.035874, 0.000000
    Synaptics Off (308):    0
    Synaptics Locked Drags (309):    0
    Synaptics Locked Drags Timeout (310):    5000
    Synaptics Tap Action (311):    0, 0, 0, 0, 1, 3, 0
    Synaptics Click Action (312):    1, 3, 0
    Synaptics Circular Scrolling (313):    1
    Synaptics Circular Scrolling Distance (314):    0.100000
    Synaptics Circular Scrolling Trigger (315):    0
    Synaptics Circular Pad (316):    0
    Synaptics Palm Detection (317):    0
    Synaptics Palm Dimensions (318):    10, 200
    Synaptics Coasting Speed (319):    20.000000, 50.000000
    Synaptics Pressure Motion (320):    30, 160
    Synaptics Pressure Motion Factor (321):    1.000000, 1.000000
    Synaptics Resolution Detect (322):    1
    Synaptics Grab Event Device (323):    0
    Synaptics Gestures (324):    1
    Synaptics Capabilities (325):    1, 0, 0, 1, 1, 1, 1
    Synaptics Pad Resolution (326):    1, 1
    Synaptics Area (327):    0, 0, 0, 0
    Synaptics Soft Button Areas (328):    3471, 0, 4028, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (329):    27, 27
    Device Product ID (286):    2, 7
    Device Node (287):    "/dev/input/event7"


```

In an effort to solve this problem I also installed Touchpad-Indicator and tried altering the settings there but it didn't help.
I also tried to reinstall the drivers from this command but it failed and here is the output; I'm not sure how to fix that
[IMG]https://imgur.com/JSg6ftT.png[/IMG]

If you need any more information, I am willing to provide it.
[IMG]https://imgur.com/JSg6ftT[/IMG]

---

