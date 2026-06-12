---
title: "touchpad not working Toshiba U940-10F"
date: 2013-11-11
forum: New to Ubuntu
---

### Post by ivan.matas84 on 2013-11-11
Hi lads,




   I have been installed ubuntu 13.10 on my laptop Toshiba U940-10F but unfortunately touchpad completely unresponsive. I installed the latest stable kernel 3.12, synaptics drivers but still does not respond. Please help me. Using an external mouse on a laptop is not confortable. Thanks and sorry for my poor english

---

### Post by tonio1128 on 2014-01-04
Hi,

Same computer, same problem :(

The xinput command :
```
antoine@tonio-u940:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PIXART USB OPTICAL MOUSE                    id=9    [slave  pointer  (2)]
&#9116;   **&#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]**
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                     id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=13    [slave  keyboard (3)]

```

So the Synaptics touchpad is well recognized.

the synclient command :
```
antoine@tonio-u940:~$ synclient
Parameter settings:
    LeftEdge                = 1766
    RightEdge               = 5386
    TopEdge                 = 1640
    BottomEdge              = 4496
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 235
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -100
    HorizScrollDelta        = -100
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0373134
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 8
    VertHysteresis          = 8
    ClickPad                = 1
    RightButtonAreaLeft     = 0
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 0
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

```

Synaptics driver is loaded and seems to work well.

Loaded dkms entries :
```
antoine@tonio-u940:~$ dkms status
psmouse, custom-1.2, 3.11.0-15-generic, x86_64: installed
virtualbox, 4.2.16, 3.11.0-12-generic, x86_64: installed
virtualbox, 4.2.16, 3.11.0-13-generic, x86_64: installed
virtualbox, 4.2.16, 3.11.0-14-generic, x86_64: installed
virtualbox, 4.2.16, 3.11.0-15-generic, x86_64: installed

```

psmouse is loaded.

I am looking to fix this bug for hours, I think another brain should be helpful :D 
Any idea ?

Thanks,
Antoine

---

### Post by tonio1128 on 2014-01-05
I tried what is explained in this post : [http://ubuntuforums.org/showthread.php?t=2182947](http://ubuntuforums.org/showthread.php?t=2182947) but even Fn+F7 or Fn+F9 doesn't change anything.

Maybe it could be reactivated by an hardware way, but how ?

---

### Post by tonio1128 on 2014-01-06
Up.

Any idea ?

---

### Post by tonio1128 on 2014-01-11
I solved it. I just booted on a Windows 8 Installation DVD, and then I hit Fn+F5, and I immediatly restarted my laptop before any action of the Windows setup. 
It seems that Ubuntu doesn't recognize my Toshiba keyboard configuration, then Fn+F5 is not recognized as a signal for touchpad hardware enabling/disabling. Although, Windows does.

---

