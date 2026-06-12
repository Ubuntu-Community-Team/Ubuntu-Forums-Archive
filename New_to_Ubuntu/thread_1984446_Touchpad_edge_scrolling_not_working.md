---
title: "Touchpad edge scrolling not working?"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by rom3lol on 2012-05-21
As the title says, I have been trying to fix scrolling with no avail. Touchpad is being recognized but does not work.

I'm running:

Distributor ID:    Ubuntu 
Description:    Ubuntu 11.10 x64
Release:    11.10 
Codename:    oneiric

My laptop is Toshiba Satellite. 

[COLOR=Red]$xinput list[/COLOR]
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; CNF9055                                     id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=13    [slave  keyboard (3)]
```[IMG]http://bayimg.com/OaoLCAAdL[/IMG]
[IMG]http://bayimg.com/oAoLdAADL[/IMG] 
[IMG]http://bayimg.com/oAoLdAADL[/IMG]

---

### Post by afriseun on 2012-09-16
bump

---

### Post by lkraemer on 2012-09-18
rom3lol,
Your posting title states Edge Scrolling does not work, but your text states the Synaptic Touchpad does not work?  Which is it?

If you execute the following command in a Terminal Window you can see all the Synaptics Touchpad command parameters that are available:
```

synclient -l

```
such as:
> 
Parameter settings:
LeftEdge = 53
RightEdge = 1099
TopEdge = 48
BottomEdge = 720
FingerLow = 25
FingerHigh = 30
FingerPress = 256
MaxTapTime = 180
MaxTapMove = 59
MaxDoubleTapTime = 180
SingleTapTimeout = 180
ClickTime = 100
FastTaps = 0
EmulateMidButtonTime = 75
EmulateTwoFingerMinZ = 257
EmulateTwoFingerMinW = 7
VertScrollDelta = 27
HorizScrollDelta = 27
VertEdgeScroll = 1
HorizEdgeScroll = 0
CornerCoasting = 0
VertTwoFingerScroll = 0
HorizTwoFingerScroll = 0
MinSpeed = 0.4
MaxSpeed = 0.7
AccelFactor = 0.0367107
TrackstickSpeed = 40
EdgeMotionMinZ = 30
EdgeMotionMaxZ = 160
EdgeMotionMinSpeed = 1
EdgeMotionMaxSpeed = 108
EdgeMotionUseAlways = 0
UpDownScrolling = 1
LeftRightScrolling = 1
UpDownScrollRepeat = 1
LeftRightScrollRepeat = 1
ScrollButtonRepeat = 100
TouchpadOff = 0
GuestMouseOff = 0
LockedDrags = 0
LockedDragTimeout = 5000
RTCornerButton = 0
RBCornerButton = 0
LTCornerButton = 0
LBCornerButton = 0
TapButton1 = 0
TapButton2 = 0
TapButton3 = 0
ClickFinger1 = 1
ClickFinger2 = 1
ClickFinger3 = 1
CircularScrolling = 0
CircScrollDelta = 0.1
CircScrollTrigger = 0
CircularPad = 0
PalmDetect = 0
PalmMinWidth = 10
PalmMinZ = 200
CoastingSpeed = 0
PressureMotionMinZ = 30
PressureMotionMaxZ = 160
PressureMotionMinFactor = 1
PressureMotionMaxFactor = 1
GrabEventDevice = 1
TapAndDragGesture = 1
AreaLeftEdge = 0
AreaRightEdge = 0
AreaTopEdge = 0
AreaBottomEdge = 0


So, just add the correct parameter to your synaptics.conf file at:
/usr/share/X11/xorg.conf.d/50-synaptics.conf

Or, where ever it's located.

ie.:
```

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        Option "TapButton1" "1"    # tap to click
        Option "VertEdgeScroll" "1"
        Option "HorizEdgeScroll" "1"

```

On next system boot it should be changed & persistent.

LK

---

