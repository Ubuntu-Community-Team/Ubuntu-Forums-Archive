---
title: "ThinkPad X1 Carbon touchpad"
date: 2015-03-02
forum: New to Ubuntu
---

### Post by davidlubomirov on 2015-03-02
There is some problem with my ThinkPad X1 Carbon synaptic touchpad, sometimes the pad do not want to respond. I already install the latest updates but the problem is still there. I also try installing latest Debian and there's no problem with the touchpad while working. Can anyone help ?

---

### Post by sandyd on 2015-03-02
Can you post the output of
```
cat /var/log/Xorg.0.log | grep -i Synaptics
synclient -l
```

---

### Post by davidlubomirov on 2015-03-02
[     6.963] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[     6.963] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     6.963] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     6.963] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     6.963] (II) LoadModule: "synaptics"
[     6.963] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     6.964] (II) Module synaptics: vendor="X.Org Foundation"
[     6.964] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     6.964] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     6.976] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[     6.976] (II) synaptics: SynPS/2 Synaptics TouchPad: found top buttonpad property
[     6.976] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1024 - 5112 (res 45)
[     6.976] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 2024 - 4832 (res 52)
[     6.976] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     6.976] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     6.976] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[     6.976] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     6.976] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     6.976] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     6.988] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[     6.988] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     6.988] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     6.988] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[     6.988] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     6.988] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     6.988] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     6.988] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     6.988] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     6.988] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     6.988] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"


Parameter settings:
    LeftEdge                = 1310
    RightEdge               = 4826
    TopEdge                 = 2220
    BottomEdge              = 4636
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 218
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 99
    HorizScrollDelta        = 99
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0403307
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
    GrabEventDevice         = 0
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 24
    VertHysteresis          = 24
    ClickPad                = 1
    RightButtonAreaLeft     = 3068
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 4326
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

---

### Post by sandyd on 2015-03-02
Forgot a few commands - sorry about that
```
xinput list
uname -a
lsb_release -a

```

---

### Post by davidlubomirov on 2015-03-02
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Lenovo USB Receiver                     	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Lenovo USB Receiver                     	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Lenovo USB Receiver                     	id=9	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=16	[slave  keyboard (3)]


Linux ThinkPad-X1-Carbon-2nd 3.16.0-31-generic #41~14.04.1-Ubuntu SMP Wed Feb 11 19:30:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

---

### Post by sandyd on 2015-03-02
Which generation of X1 Carbon is this, for some reason, there are a multitude of bugs surrounding the X1 Carbon touchpad at the moment.

Is the actual touchpad not working, or only the buttons?
The touchpad is also reported to be extremely sensitive, and for some, requires a fix to stop it from jumping around.

---

### Post by davidlubomirov on 2015-03-03
It 2nd generation and here is what I found out for the moment. I also use Windows ( because of 3D modeling programs that I need ) and after I install latest driver, touchpad works PERFECT. On Debian also work PERFEKT, but here on Ubuntu there is some problem with setting the touchpad to work suitably. Can anyone tell where to find instructions of how to change the way touchpad respond? 
For example: basically 75% of the touchpad work as left button but here in Ubuntu is set on 50/50

---

### Post by sandyd on 2015-03-03
> **davidlubomirov said:**
> It 2nd generation and here is what I found out for the moment. I also use Windows ( because of 3D modeling programs that I need ) and after I install latest driver, touchpad works PERFECT. On Debian also work PERFEKT, but here on Ubuntu there is some problem with setting the touchpad to work suitably. Can anyone tell where to find instructions of how to change the way touchpad respond? 
For example: basically 75% of the touchpad work as left button but here in Ubuntu is set on 50/50

Ah, so you want it back to 75% as the left and 25% 

Thats adjustable.

Small Explanation in order:
From your output of synclient -l```
LeftEdge = 1310
RightEdge = 4826
TopEdge = 2220
BottomEdge = 4636
```

These are the coordinates of the touchpad.

```

RightButtonAreaLeft = 3068
RightButtonAreaRight = 0
RightButtonAreaTop = 4326
RightButtonAreaBottom = 0
MiddleButtonAreaLeft = 0
MiddleButtonAreaRight = 0
MiddleButtonAreaTop = 0
MiddleButtonAreaBottom = 0
```
These specify the position of the softbuttons.

For example, if want it to be 1/2 and 1/2 (like what Ubuntu does at the moment), you would do some calculations to find....
(1310 + 4826)/2 = 3068
Which is currently consistent with what your describe.
Touchpad right (RightButtonAreaRight) occupies everything to the left of 3068 because it is zero.

So 75% would be...
((1310 + 4826)/4)*3 = 4602

Lets apply that and have a test.
Run
```

synclient RightButtonAreaLeft=4602

```

---

### Post by davidlubomirov on 2015-03-05
Well nothing happen !

---

### Post by sandyd on 2015-03-05
> **davidlubomirov said:**
> Well nothing happen !

Main problem is that I don't have a carbon X1 to test with, so I cannot give you the right values.

Run this to reset your touchpad values
```

synclient RightButtonAreaLeft=3068 RightButtonAreaRight=0 RightButtonAreaTop=4326 RightButtonAreaBottom=0
```

Set the right corner button (side note, some touchpads have the value '3' as right click, some have '2' as right click):
```

synclient RBCornerButton=3
```

Now, tap on the very very bottom right corner of your touchpad, it should either paste (default middle mouse action) or right click.
If it pastes change the 3 in the command above to 2.

Now for the fun part.

```

synclient RightButtonAreaLeft=3068 RightButtonAreaRight=0 RightButtonAreaTop=4326 RightButtonAreaBottom=0
```

This sets the position of RBCornerButton. You will have to adjust the values yourself (Left side, right side, top, bottom) of the button.

---

### Post by davidlubomirov on 2015-03-06
Thanks it work, but how to set right button in bottom left corner , because with this settings right button is top right corner ? 

Thanks in advance :)

---

### Post by sandyd on 2015-03-06
> **davidlubomirov said:**
> Thanks it work, but how to set right button in bottom left corner , because with this settings right button is top right corner ? 

Thanks in advance :)

As noted in previous post - you will have to test which (1/2/3) is the correct button.

Generally 1 is the Left button
2/3 get swapped sometimes.

As for the corners... (just set whichever one you need these are default values)
```

#Set Right Top corner
synclient RTCornerButton=2
#Set Right Bottom corner
synclient RBCornerButton=3
# Set Left Top corner
synclient LTCornerButton=0
# Set Left Bottom corner
synclient LBCornerButton=0
```

---

### Post by davidlubomirov on 2015-03-06
Ok man you don't understand me but still thanks for the help I'll get used with this settings. Again THANKS :)

---

