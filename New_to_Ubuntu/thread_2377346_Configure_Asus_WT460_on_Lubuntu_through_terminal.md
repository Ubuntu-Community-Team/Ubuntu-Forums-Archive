---
title: "Configure Asus WT460 on Lubuntu through terminal"
date: 2017-11-12
forum: New to Ubuntu
---

### Post by sed_faster on 2017-11-12
Hello folks,

I am trying setup the mouse [https://www.asus.com/Keyboards-Mice/WT460/](https://www.asus.com/Keyboards-Mice/WT460/). I googled to found tips about how should I configure this device on my:
```

$ uname -a
Linux xxx 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

```
And a found this: [https://askubuntu.com/questions/205676/how-to-change-mouse-speed-sensitivity](https://askubuntu.com/questions/205676/how-to-change-mouse-speed-sensitivity)

After testing this commands:
```

$ xinput --list-props 16
Device 'HOLTEK Wireless USB Device':
    Device Enabled (140):    1
    Coordinate Transformation Matrix (142):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (271):    0
    Device Accel Constant Deceleration (272):    2.000000
    Device Accel Adaptive Deceleration (273):    1.000000
    Device Accel Velocity Scaling (274):    10.000000
    Device Product ID (260):    1241, 40989
    Device Node (261):    "/dev/input/event16"
    Evdev Axis Inversion (275):    0, 0
    Evdev Axes Swap (277):    0
    Axis Labels (278):    "Rel X" (150), "Rel Y" (151), "Rel Vert Wheel" (270)
    Button Labels (279):    "Button Left" (143), "Button Middle" (144), "Button Right" (145), "Button Wheel Up" (146), "Button Wheel Down" (147), "Button Horiz Wheel Left" (148), "Button Horiz Wheel Right" (149), "Button Side" (264), "Button Extra" (265), "Button Unknown" (263), "Button Unknown" (263), "Button Unknown" (263), "Button Unknown" (263)
    Evdev Scrolling Distance (280):    1, 1, 1
    Evdev Middle Button Emulation (281):    0
    Evdev Middle Button Timeout (282):    50
    Evdev Middle Button Button (283):    2
    Evdev Third Button Emulation (284):    0
    Evdev Third Button Emulation Timeout (285):    1000
    Evdev Third Button Emulation Button (286):    3
    Evdev Third Button Emulation Threshold (287):    20
    Evdev Wheel Emulation (288):    0
    Evdev Wheel Emulation Axes (289):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (290):    10
    Evdev Wheel Emulation Timeout (291):    200
    Evdev Wheel Emulation Button (292):    4
    Evdev Drag Lock Buttons (293):    0

```

Which parameter allows me change the velocity of the click on left button? When I pulse left button on my mouse, simply to selected a folder or component on my system, this action works as if I pulse two times the button (as a double-click). I need change this parameter because this is annoying me :/
I think it is something related to xinput --list-props 143 - Button Left. But which paramater I should choose to change this behaviour?

Thanks

---

