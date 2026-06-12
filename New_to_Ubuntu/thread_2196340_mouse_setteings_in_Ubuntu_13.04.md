---
title: "mouse setteings in Ubuntu 13.04"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by aqkshin on 2013-12-29
Hello,

I am really having trouble in configuring my logitech mouse (M-BZ96C). The problem is that I can't find a way to setup/configure the speed/acceleration/deceleration/dpi of this mouse to my liking. I have done some search and found about _xinput_ and _xset_, but none of them helps me (well, partially they do). And it is still uncomfartable when compared to its functionality in Windows. 

I was wondering what are the other ways of configuring mouse in ubuntu. By the way, I found _lomoco_ driver, but it doesn't support my mouse. Hope to hear from you soon.

Thank you

---

### Post by conversationjames on 2014-01-02
Hope these help:
[Mouse sensitivity on Linux]("http://www.reddit.com/r/linux_gaming/comments/1ew39a/")
[Sensitivity Ubuntu]("http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/") (older but maybe still applicable?)

---

### Post by varunendra on 2014-01-02
Have you tried "gpointing-device-settings" yet? It is a GUI program to tweak the settings of pointing devices, and offers a lot more settings and flexibility than the default settings program in Ubuntu.

To install it -
```
sudo apt-get install gpointing-device-settings
```

Be aware that it can override default settings and there is no option like "Reset to Defaults" in it, so you may wish to note down the current settings (outputs of "synclient", "xinput list-props <your mouse's id>") before playing with it.

By default it does not create a clickable icon in Unity or any desktop environment other than Gnome. So to run it in Unity, you'll have to run it with Alt-F2 > type "gpointing-device-settings".

To get its clickable icon in Unity, remove a line from its .desktop file -
```
sudo sed -i '/OnlyShowIn/ d' /usr/share/applications/gpointing-device-settings.desktop
```

I'd also recommend to post your outputs of "synclient" and "xinput list-props <id of your mouse>" here so we can see if something can be optimized to your liking. Of course that also means posting a description of what kind of optimization you want (speed, acceleration, sensitivity etc.).

This doesn't mean I'm able to help with every setting you want, but I'd like to try if no one else comes up with a precise answer and you don't mind some experimenting.

*[Disclaimer : I don't even understand the meaning of most of the things in the output of "xinput list-props.." command :P]*

---

### Post by aqkshin on 2014-01-10
Thanks for the replies. Also, I am sorry for my such a late post. I thought no one would reply to this thread after waiting two days. 

I looked at the links above, and the one from *reddit* has an interesting post which mentions *mousepoll* parameter for dpi. I will look at it and read about this parameter thoroughly when I have time. 

Also, I had installed *[COLOR=#000000]gpointing-device-settings [/COLOR]*[COLOR=#000000]but it didn't help: there wasn't much to change for the mouse settings.

**this is the result of the command _synclient_:**
[/COLOR][COLOR=#000000]
[/COLOR]Parameter settings:
    LeftEdge                = 299
    RightEdge               = 1701
    TopEdge                 = 209
    BottomEdge              = 1191
    FingerLow               = 12
    FingerHigh              = 15
    FingerPress             = 128
    MaxTapTime              = 180
    MaxTapMove              = 107
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 141
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 48
    HorizScrollDelta        = 48
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0819336
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 15
    EdgeMotionMaxZ          = 80
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 195
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
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 100
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 15
    PressureMotionMaxZ      = 80
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 12
    VertHysteresis          = 12
    ClickPad                = 0


**this is the result of _xinput list-props:_**

Device 'Logitech USB-PS/2 Optical Mouse':
	Device Enabled (133):	1
	Coordinate Transformation Matrix (135):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (261):	0
	Device Accel Constant Deceleration (262):	1.000000
	Device Accel Adaptive Deceleration (263):	1.000000
	Device Accel Velocity Scaling (264):	10.000000
	Device Product ID (250):	1133, 49221
	Device Node (251):	"/dev/input/event15"
	Evdev Axis Inversion (265):	0, 0
	Evdev Axes Swap (267):	0
	Axis Labels (268):	"Rel X" (143), "Rel Y" (144), "Rel Horiz Wheel" (259), "Rel Vert Wheel" (260)
	Button Labels (269):	"Button Left" (136), "Button Middle" (137), "Button Right" (138), "Button Wheel Up" (139), "Button Wheel Down" (140), "Button Horiz Wheel Left" (141), "Button Horiz Wheel Right" (142), "Button Side" (254), "Button Extra" (255), "Button Forward" (256), "Button Back" (257), "Button Task" (258), "Button Unknown" (253), "Button Unknown" (253), "Button Unknown" (253), "Button Unknown" (253)
	Evdev Middle Button Emulation (270):	0
	Evdev Middle Button Timeout (271):	50
	Evdev Third Button Emulation (272):	0
	Evdev Third Button Emulation Timeout (273):	1000
	Evdev Third Button Emulation Button (274):	3
	Evdev Third Button Emulation Threshold (275):	20
	Evdev Wheel Emulation (276):	0
	Evdev Wheel Emulation Axes (277):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (278):	10
	Evdev Wheel Emulation Timeout (279):	200
	Evdev Wheel Emulation Button (280):	4
	Evdev Drag Lock Buttons (281):	0
[B]
=============================================

Actually now I have only set my mouse by one command:  xset m 3 2[/B]
That does fine job for me. The main thing though that is a little annoying is low dpi. It's not problem during normal use. But when I use gimp, this low dpi problem becomes very obvious: the pointer jumps a little when i try to make finer movements.

So, if you guys show how can I **change mouse dpi value**, that would be much appreciated. I think this value is 400 at the moment, though I am not sure and don't know how to check.

---

