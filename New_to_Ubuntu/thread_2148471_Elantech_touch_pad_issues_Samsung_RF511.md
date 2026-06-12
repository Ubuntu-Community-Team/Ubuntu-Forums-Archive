---
title: "Elantech touch pad issues Samsung RF511"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by vipmeister on 2013-05-25
I am running ubuntu 13.4 and my touch pad is non responsive and use usb mouse instaed. Is there anyway I could start using touch pad again?

Many thanks

**xinput shows**
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; USB OpticalWheel Mouse                      id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; WebCam SCB-1100N                            id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

**Syclient -l**
Parameter settings:
    LeftEdge                = 100
    RightEdge               = 2408
    TopEdge                 = 71
    BottomEdge              = 1249
    FingerLow               = 9
    FingerHigh              = 12
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 124
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 96
    HorizScrollDelta        = 96
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 4.74
    MaxSpeed                = 4.78
    AccelFactor             = 0.49
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 40
    EdgeMotionMinSpeed      = 100
    EdgeMotionMaxSpeed      = 400
    EdgeMotionUseAlways     = 0
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
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.100007
    CircScrollTrigger       = 0
    CircularPad             = 0
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
    HorizHysteresis         = 14
    VertHysteresis          = 14
    ClickPad                = 1
    RightButtonAreaLeft     = 1254
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 1082
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0

---

### Post by ibjsb4 on 2013-05-25
```
**xinput shows**
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; USB OpticalWheel Mouse                      id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; WebCam SCB-1100N                            id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

**Syclient -l**
Parameter settings:
    LeftEdge                = 100
    RightEdge               = 2408
    TopEdge                 = 71
    BottomEdge              = 1249
    FingerLow               = 9
    FingerHigh              = 12
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 124
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 96
    HorizScrollDelta        = 96
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 4.74
    MaxSpeed                = 4.78
    AccelFactor             = 0.49
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 40
    EdgeMotionMinSpeed      = 100
    EdgeMotionMaxSpeed      = 400
    EdgeMotionUseAlways     = 0
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
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.100007
    CircScrollTrigger       = 0
    CircularPad             = 0
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
    HorizHysteresis         = 14
    VertHysteresis          = 14
    ClickPad                = 1
    RightButtonAreaLeft     = 1254
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 1082
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0 						
```

I can point you to this

[http://ubuntuforums.org/showthread.php?t=2067590](http://ubuntuforums.org/showthread.php?t=2067590)

also

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Elantech+touch+pad&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Elantech+touch+pad&sa=Search&cof=FORID:9)

---

### Post by vipmeister on 2013-05-25
tried that and various other suggestions. Not working though. I will be very grateful if someone could talk me through the solution.

Cheers

---

