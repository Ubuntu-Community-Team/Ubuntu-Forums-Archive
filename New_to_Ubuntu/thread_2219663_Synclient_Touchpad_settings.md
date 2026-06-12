---
title: "Synclient Touchpad settings"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by rahul11 on 2014-04-25
Hello,

I've been trying to figure these two things out

1. I want to be able to use the touchpad normally with one hand while finger of my other hand is placed on the left corner of the touchpad and the left corner which is supposed to be treated as left mouse button.

2. two finger click to be treated as right button click.

Here is the synclient current configuration:
Parameter settings:
    LeftEdge                = 1766
    RightEdge               = 5388
    TopEdge                 = 1643
    BottomEdge              = 4535
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 237
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 107
    HorizScrollDelta        = 107
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0371264
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
    RightButtonAreaLeft     = 3577
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 4164
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

---

### Post by el_garicimo on 2014-04-30
looks like you have a macbook- style clickpad (many new laptops do now), where there is only one physical button. Linux has a hard time playing nice with these sometimes--this link does a decent job talking about how to adjust the settings for the synaptic driver [https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Buttonless_touchpads_.28aka_ClickPads.29](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Buttonless_touchpads_.28aka_ClickPads.29)

---

### Post by squakie on 2014-05-01
You can also try installing the synaptic package (sudo apt-get install synaptic) and see if it gives you any options that might help you.

---

### Post by Mr._G on 2015-01-06
Hi there,

Did you ever get your settings figured out so that your trackpad worked according to your first condition (able to mouse while placing another finger on the trackpad)?

Any advice you'd have would be great, thanks.

---

