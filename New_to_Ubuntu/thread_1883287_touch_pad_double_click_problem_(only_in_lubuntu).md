---
title: "touch pad double click problem (only in lubuntu)"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by muppet317 on 2011-11-18
double click doesn't work on my touchpad in lubuntu.

single click, scroll etc. using the touchpad work fine. double clicking using the buttons next to the touchpad work fine. double click using the touchpad in standard ubuntu works fine.

i have used the standard ubuntu for nearly 2 yrs with no problems, then after upgrading to 11.10 added lubuntu through synaptic to speed up my eeepc.

not a major problem as the button double click still works, but frustrating nevertheless.

---

### Post by Rodney9 on 2011-11-18
> **muppet317 said:**
> double click doesn't work on my touchpad in lubuntu.

single click, scroll etc. using the touchpad work fine. double clicking using the buttons next to the touchpad work fine. double click using the touchpad in standard ubuntu works fine.

i have used the standard ubuntu for nearly 2 yrs with no problems, then after upgrading to 11.10 added lubuntu through synaptic to speed up my eeepc.

not a major problem as the button double click still works, but frustrating nevertheless.

I don't have a eeepc, but on my Toshiba laptop, double-click works, so  don't know what to say or how to help, sorry.

One thing I suggest is to post this link on the [[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755") where other Lubuntu users will see it.

The [[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755") is also a great page for all things Lubuntu, How-To's , Screen-Casts etc.

Rodney

---

### Post by muppet317 on 2011-11-18
Thanks Rodney - will post it on the One Stop Thread (its been a great help for all my other lubuntu related queries til now)

---

### Post by LinuxFan999 on 2011-11-18
> **muppet317 said:**
> double click doesn't work on my touchpad in lubuntu.

single click, scroll etc. using the touchpad work fine. double clicking using the buttons next to the touchpad work fine. double click using the touchpad in standard ubuntu works fine.

i have used the standard ubuntu for nearly 2 yrs with no problems, then after upgrading to 11.10 added lubuntu through synaptic to speed up my eeepc.

not a major problem as the button double click still works, but frustrating nevertheless.
Adding Lubuntu-desktop to standard Ubuntu is not recommended. Try installing the "real" Lubuntu and see if the issue still ocurrs.

---

### Post by muppet317 on 2011-11-18
> Try installing the "real" Lubuntu and see if the issue still ocurrs.

Not quite sure what you mean. I didn't want to do full format and clean install of lubuntu as a) i'm a bit lazy and didnt want to have to backup etc. and b) i didn't want to have to try and remember / find all the things you need after a clean install to get the system up & running e.g. software i dont use often, restricted extras etc.

I didn't just add the lubuntu-desktop through synaptic, i also added lubuntu-core and its dependencies.

---

### Post by LinuxFan999 on 2011-11-18
> **muppet317 said:**
> Not quite sure what you mean. I didn't want to do full format and clean install of lubuntu as a) i'm a bit lazy and didnt want to have to backup etc. and b) i didn't want to have to try and remember / find all the things you need after a clean install to get the system up & running e.g. software i dont use often, restricted extras etc.

I didn't just add the lubuntu-desktop through synaptic, i also added lubuntu-core and its dependencies.
By "real" lubuntu, I meant the lubuntu ISO file which you download from the lubuntu website, which doesn't include gnome.

---

### Post by muppet317 on 2011-11-18
Thanks, though if possible I'd like to see if i can fix it within the current setup without a complete fresh install, unless there are other problems between having gnome and lubuntu on the same system?

---

### Post by croque on 2011-11-18
I'm not sure which eeepc you have, but on my eeepc 1005ha with a clean install of lubuntu 11.10 (i.e. installed from the lubuntu 11.10 iso, onto a reformatted hd) the double-click works fine.

---

### Post by SteveDee on 2011-11-19
> **muppet317 said:**
> ...I didn't want to do full format and clean install of lubuntu...

No, don't re-install from scratch, its far too much aggro.

I'd suggest first downloading Lubuntu and creating a LiveCD (or probably a LiveUSB stick if you don't have a drive). You can then boot the system from this and see if there is some hardware/Lubuntu issue (I kinda doubt that there is).

If all is well, then I suggest you remove all trace of Ubuntu like this: [http://psychocats.net/ubuntu/purelxde](http://psychocats.net/ubuntu/purelxde)

If you are really cautious about this, you could remove the packages listed in the removal script one at a time via Synaptic Package Manager. Synaptic keeps a time-stamped History of what is added/removed. So if something goes wrong you can always backtrack.

However, for a more interesting approach, you could take a closer look at your touchpad settings. On my laptop I can type in a terminal:-
```

synclient

```
...which returns a list of settings. The meaning of some of these is clear, others less so. But if you get a list back then post it here.

I hope some of this helps.

---

### Post by muppet317 on 2011-11-19
thanks for the tip on how to remove ubuntu - i originally just added lubuntu through synaptic to test it out and it is working great, so I think i will now remove ubuntu.

however, randomly, without me changing any settings the touch pad double click is now working completely normally. strange.

anyway here's the output from synclient-
```

Parameter settings:
    LeftEdge                = 52
    RightEdge               = 524
    TopEdge                 = 49
    BottomEdge              = 335
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 26
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 12
    HorizScrollDelta        = 12
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.331675
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 48
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 2
    TapButton3              = 3
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
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
```

thanks for everyone's help...

---

### Post by muppet317 on 2011-11-20
> If all is well, then I suggest you remove all trace of Ubuntu like this: [http://psychocats.net/ubuntu/purelxde](http://psychocats.net/ubuntu/purelxde)

I did this (having previously added lubuntu to ubuntu through synaptic), and after apparently successfully running the code, my computer failed to restart. it just reached the lubuntu loading page and never got any further.

I'm now trying xubuntu and all seems to be going well so far. Just thought I should post this up in case anyone else runs that script and hadn't first backed up their files!
[]("http://psychocats.net/ubuntu/purelxde")

---

