---
title: "No Edge Scroll (was Change touchpad driver)"
date: 2024-09-14
forum: New to Ubuntu
---

### Post by rudeelf on 2024-09-14
I've edited this post to reflect some minor successes I had after originally posting, but the overall problem still persists - I can't get edge scrolling to work on my old Sony Vaio's Alps touchpad.

I think the touchpad should be capable of edge scrolling because it's worked in the past on Windows 7 (but not on Windows 10), and because of the following terminal output:

```

me@Vaio:~$ sudo libinput list-devices
Device:           AlpsPS/2 ALPS GlidePoint
Kernel:           /dev/input/event5
Group:            8
Seat:             seat0, default
Size:             69x50mm
Capabilities:     pointer 
Tap-to-click:     disabled
Tap-and-drag:     enabled
Tap drag lock:    disabled
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: enabled
Calibration:      n/a
Scroll methods:   *two-finger edge 
Click methods:    none
Disable-w-typing: enabled
Disable-w-trackpointing: enabled
Accel profiles:   flat *adaptive custom
Rotation:         n/a


```

I *think*, I can't be sure, the original completely vanilla Lubuntu 24.04.1 LTS I installed to a single SSD set the touchpad up with the libinput driver (I believe this because I heard it's the normal default). I tried changing to the synaptics touchpad driver:

```

sudo apt install xserver-xorg-input-synaptics

```

then I ran:

```

me@Vaio:~$ sudo synclient VertEdgeScroll=1
me@Vaio:~$ sudo synclient HorizEdgeScroll=1

```

I then tried to check the parameters of the driver in use for the touchpad:

```

me@Vaio:~$ xinput list-props "AlpsPS/2 ALPS GlidePoint"
Device 'AlpsPS/2 ALPS GlidePoint':
        Device Enabled (150):   1
        Coordinate Transformation Matrix (152): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (277):     1
        Device Accel Constant Deceleration (278):       2.500000
        Device Accel Adaptive Deceleration (279):       1.000000
        Device Accel Velocity Scaling (280):    12.500000
        Synaptics Edges (288):  300, 1700, 210, 1190
        Synaptics Finger (289): 12, 15, 0
        Synaptics Tap Time (290):       180
        Synaptics Tap Move (291):       107
        Synaptics Tap Durations (292):  180, 180, 100
        Synaptics ClickPad (293):       0
        Synaptics Middle Button Timeout (294):  75
        Synaptics Two-Finger Pressure (295):    141
        Synaptics Two-Finger Width (296):       7
        Synaptics Scrolling Distance (297):     48, 48
        Synaptics Edge Scrolling (298): 1, 1, 0
        Synaptics Two-Finger Scrolling (299):   1, 0
        Synaptics Move Speed (300):     1.000000, 1.750000, 0.081934, 0.000000
        Synaptics Off (301):    0
        Synaptics Locked Drags (302):   0
        Synaptics Locked Drags Timeout (303):   5000
        Synaptics Tap Action (304):     2, 3, 0, 0, 1, 3, 0
        Synaptics Click Action (305):   1, 1, 0
        Synaptics Circular Scrolling (306):     0
        Synaptics Circular Scrolling Distance (307):    0.100000
        Synaptics Circular Scrolling Trigger (308):     0
        Synaptics Circular Pad (309):   0
        Synaptics Palm Detection (310): 0
        Synaptics Palm Dimensions (311):        10, 100
        Synaptics Coasting Speed (312): 20.000000, 50.000000
        Synaptics Pressure Motion (313):        15, 80
        Synaptics Pressure Motion Factor (314): 1.000000, 1.000000
        Synaptics Resolution Detect (315):      1
        Synaptics Grab Event Device (316):      0
        Synaptics Gestures (317):       1
        Synaptics Capabilities (318):   1, 1, 1, 1, 1, 1, 0
        Synaptics Pad Resolution (319): 1, 1
        Synaptics Area (320):   0, 0, 0, 0
        Synaptics Noise Cancellation (321):     12, 12
        Device Product ID (270):        2, 8
        Device Node (269):      "/dev/input/event5"

```

I did wonder what the three parameters are, here:

```

Synaptics Edge Scrolling (298): 1, 1, 0

```

Just as an aside.. Is there a reference somewhere to understand these parameters? I wondered if that last 0 needed to be a 1 maybe.. but not sure what it represents

Anyway.. everything about the touchpad continued to work fine with the synaptics driver installed, again except for the lack of edge scrolling (at least I think that's the right term.. I'm talking about when I grab a window by the handle and start dragging across it across the screen, and my finger runs out of touchpad and hits the edge.. it should continue to drag the window across even though my finger is stationary at the extreme edge of the pad..)

I thought maybe I should now just go into Preferences > LXQt Settings > Keyboard and Mouse > Mouse and Touchpad, perhaps something has popped up in there I can configure..

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294241&stc=1[/IMG]

Oh dear :-( 

I uninstalled the synaptics driver and this seemed to succeed in reinstating the libinput driver. Looked into xinput list-props for the libinput driver and absolutely no mention anywhere of edge scrolling. Nevertheless, rebooted & went back into LXQt Keyboard and Mouse settings where this time, there *was* a selectable option for edge scrolling. Enabled it, rebooted... nope, still no edge scrolling.

Someone suggested I try

```

sudo xinput set-prop "AlpsPS/2 ALPS GlidePoint" "libinput Scroll Method Enabled" 0 1 0

```

It completed, but didn't result in edge scrolling becoming available.

Somebody else suggested adding the following to /etc/X11/xorg.conf.d/40-libinput.conf:

```

Section "InputClass"
    Identifier "libinput touchpad catchall"
    MatchIsTouchpad "on"
    Driver "libinput"
    Option "ScrollMethod" "edge"
    Option "Tapping" "on"  # Optional: Enable tapping if desired
    Option "NaturalScrolling" "false"  # Change to "true" if you prefer natural scrolling
EndSection

```

Turned out  /etc/X11/xorg.conf.d/40-libinput.conf didn't exist, so I created it with the above content. No luck. There was a different file in the /xorg.conf.d/ folder, 00-keyboard.conf - I tried also inserting the above content in there and rebooting. Still no luck & I began to think, I'm really just shooting in the dark here now.

Somebody else mentioned a "DKMS Alps driver", is that a lead worth following up?

Am I following the wrong approach to troubleshoot this?

Likelihood of the hardware being faulty? It was working in Win7 a while ago but maybe it's gone south since. It's not the newest of machines..

Machine information:
```

Machine              : Laptop - Sony Vaio VPCEJ3T1E (2011 vintage) PCG-91211M
Processor            : Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz
Memory               : 8112MB (878MB used)
Installation iso     : Lubuntu 24.04.1 LTS amd64 (Downloaded 14th Sep 2024)
Touchpad (detected)  : AlpsPS/2 ALPS GlidePoint
???                  : Sony Vaio Jogdial (not physically present, but detected)
Kernel               : Linux 6.8.0-44-generic (x86_64)
Version              : #44-Ubuntu SMP PREEMPT_DYNAMIC Tue Aug 13 13:35:26 UTC 2024
Palmrest & Touchpad  : Sony part no. 4FHK2PHN010 / (with CIRQUE/ALPS 1CA033 rushmore? touch controller)

```

---

