---
title: "No Right Click/Cursor Jumping"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by Neutralinos on 2013-03-23
Hello,

For whatever reason I have no right click ability on my laptop when running Ubuntu (12.04). When I plug in a USB mouse it has right click and full functionality, but with just my pad thing I have yet to find a way to right click. 

The cursor also jumps around randomly when I'm moving it around using the pad making it peskingly inaccurate. In Windows or with a USB mouse I have no issues with the cursor. 

I know yall need more info to help me, but I'm not sure what's relevant or where to find it. 

Thanks!

---

### Post by Impavidus on 2013-03-23
Perhaps the make and model of your laptop, and of your touchpad. I'm not really a specialist in debugging this kind of hardware related stuff, but that info will probably be helpful.

On my synaptics touchpad in a HP laptop I can right click with the right button (well, that's obvious) and by tapping the touchpad with two fingers simultaneously.

---

### Post by mikewhatever on 2013-03-24
Can you post the outputs of **xinput list** and **synclient**. If the touchpad is detected, hopefully, we can get it configered properly.

---

### Post by Neutralinos on 2013-05-04
adam@AdamEtc:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=12	[slave  keyboard (3)]
adam@AdamEtc:~$ synclient
Parameter settings:
    LeftEdge                = 1755
    RightEdge               = 5233
    TopEdge                 = 1627
    BottomEdge              = 4325
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 225
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 102
    HorizScrollDelta        = 102
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0390854
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 409
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 2
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

---

