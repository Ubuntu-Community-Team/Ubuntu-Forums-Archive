---
title: "Envy 14 (First Generation) Touchpad Issues"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by Bad Cook on 2012-09-22
Hello all,

I've just installed Ubuntu 12.04 on my HP Envy 14 (first generation) laptop (first time installing Linux which is why I'm in this forum). The touchpad is giving me problems. Although basic functionality such as clicking and right clicking work, higher functions such as multitouch and (most importantly) disabling the touchpad while typing do not work. 

Apart from that, the touchpad does not show up under the "Mouse and Touchpad" option in settings. I only have the mouse settings, i.e. the Touchpad tab does not appear. 

Another odd symptom (I don't know whether it is related or not) is that at startup I hear a sound which seems to normally be reserved for errors and notifications (e.g. when closing a Firefox browser window with multiple tabs open) as soon as the login screen appears. 

I've been mucking around on the internet for a while now, but still have yet to come up with a solution. It looks like I'm not alone either ([http://ubuntuforums.org/showthread.php?p=12154676#post12154676](http://ubuntuforums.org/showthread.php?p=12154676#post12154676)). 

Some things I've tried so far (to no avail):

[LIST]
[*]Reinstalling xserver-xorg-input-synaptics
[*]Running synclient gives me ```
Couldn't find synaptics properties. No synaptics driver loaded?
```
[*]Naturally syndaemon also doesn't end up doing anything (although it doesn't throw any errors either)
[*]Tried mucking around in the xorg.conf file located at /etc/X11/xorg.conf. Originally there were only two items ```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection
```. The touchpad was not working with only those two items present. I added ```
Section "InputDevice"
    Identifier    "Touchpad"
    Driver    "synaptics"
    Option    "Protocol"    "auto-dev"
    Option    "Device"    "/dev/evdev/"
EndSection
``` after seeing [http://ubuntuforums.org/archive/index.php/t-1655339.html](http://ubuntuforums.org/archive/index.php/t-1655339.html). The touchpad was still not giving me other functionality. I have tried changing the protocol to "alps" and "auto" and those have not worked either.
[*]Messing with modprobe has not given me anything either. Running ```
sudo modprobe -r psmouse
sudo modprobe psmouse
``` turns the touchpad on and off, but the functionality is still not there.
[*]Using dconf Editor after going into org.gnome.settings-daemon.periphals.touchpad and setting disable-while-typing  to true (which didn't work). Indeed it didn't look like any of the  touchpad settings did anything. I disabled the touchpad in dconf Editor  and my touchpad just kept chugging along.
[*]Tried using a custom .deb package from [http://linuxenvy.blogspot.com/2011/01/touchpad-fixed.html](http://linuxenvy.blogspot.com/2011/01/touchpad-fixed.html). It refused to run. Running dpkg from the command line gave me an error that it was not a debian type file. Running it from the Ubuntu Software Center gave me a generic error that it couldn't open the file.
[/LIST]
As for what Ubuntu detects my hardware to be, I have that

[LIST]
[*]```
xinput
``` gives me ```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Synaptics TouchPad                     id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=13    [slave  keyboard (3)]

```
[*]```
xinput --list-props 12
``` gives me ```
Device 'PS/2 Synaptics TouchPad':
    Device Enabled (126):    1
    Coordinate Transformation Matrix (128):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (247):    0
    Device Accel Constant Deceleration (248):    1.000000
    Device Accel Adaptive Deceleration (249):    1.000000
    Device Accel Velocity Scaling (250):    10.000000
    Device Product ID (243):    2, 1
    Device Node (244):    "/dev/input/event11"
    Evdev Axis Inversion (251):    0, 0
    Evdev Axes Swap (253):    0
    Axis Labels (254):    "Rel X" (136), "Rel Y" (137)
    Button Labels (255):    "Button Left" (129), "Button Middle" (130), "Button Right" (131), "Button Wheel Up" (132), "Button Wheel Down" (133)
    Evdev Middle Button Emulation (256):    0
    Evdev Middle Button Timeout (257):    50
    Evdev Third Button Emulation (258):    0
    Evdev Third Button Emulation Timeout (259):    1000
    Evdev Third Button Emulation Button (260):    3
    Evdev Third Button Emulation Threshold (261):    20
    Evdev Wheel Emulation (262):    0
    Evdev Wheel Emulation Axes (263):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (264):    10
    Evdev Wheel Emulation Timeout (265):    200
    Evdev Wheel Emulation Button (266):    4
    Evdev Drag Lock Buttons (267):    0

```
[*]If I look at Xorg's log (in other words if I run ```
cat /var/log/log/Xorg.0.log | grep -iE "touchpad|mouse|synaptics"
```), I get the following:```
[    20.538] (==) intel(0): Silken mouse enabled
[    20.677] (II) config/udev: Adding input device PS/2 Synaptics TouchPad (/dev/input/event11)
[    20.677] (**) PS/2 Synaptics TouchPad: Applying InputClass "evdev pointer catchall"
[    20.677] (II) Using input driver 'evdev' for 'PS/2 Synaptics TouchPad'
[    20.677] (**) PS/2 Synaptics TouchPad: always reports core events
[    20.677] (**) evdev: PS/2 Synaptics TouchPad: Device: "/dev/input/event11"
[    20.677] (--) evdev: PS/2 Synaptics TouchPad: Vendor 0x2 Product 0x1
[    20.677] (--) evdev: PS/2 Synaptics TouchPad: Found 3 mouse buttons
[    20.677] (--) evdev: PS/2 Synaptics TouchPad: Found relative axes
[    20.677] (--) evdev: PS/2 Synaptics TouchPad: Found x and y relative axes
[    20.677] (II) evdev: PS/2 Synaptics TouchPad: Configuring as mouse
[    20.677] (**) evdev: PS/2 Synaptics TouchPad: YAxisMapping: buttons 4 and 5
[    20.677] (**) evdev: PS/2 Synaptics TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.677] (II) XINPUT: Adding extended input device "PS/2 Synaptics TouchPad" (type: MOUSE, id 12)
[    20.677] (II) evdev: PS/2 Synaptics TouchPad: initialized for relative axes.
[    20.677] (**) PS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    20.677] (**) PS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    20.677] (**) PS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    20.677] (**) PS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    20.677] (II) config/udev: Adding input device PS/2 Synaptics TouchPad (/dev/input/mouse0)
[  3507.336] (II) config/udev: removing device PS/2 Synaptics TouchPad
[  3507.339] (II) evdev: PS/2 Synaptics TouchPad: Close
[  3514.827] (II) config/udev: Adding input device PS/2 Synaptics TouchPad (/dev/input/event11)
[  3514.827] (**) PS/2 Synaptics TouchPad: Applying InputClass "evdev pointer catchall"
[  3514.827] (II) Using input driver 'evdev' for 'PS/2 Synaptics TouchPad'
[  3514.827] (**) PS/2 Synaptics TouchPad: always reports core events
[  3514.827] (**) evdev: PS/2 Synaptics TouchPad: Device: "/dev/input/event11"
[  3514.827] (--) evdev: PS/2 Synaptics TouchPad: Vendor 0x2 Product 0x1
[  3514.827] (--) evdev: PS/2 Synaptics TouchPad: Found 3 mouse buttons
[  3514.827] (--) evdev: PS/2 Synaptics TouchPad: Found relative axes
[  3514.827] (--) evdev: PS/2 Synaptics TouchPad: Found x and y relative axes
[  3514.827] (II) evdev: PS/2 Synaptics TouchPad: Configuring as mouse
[  3514.827] (**) evdev: PS/2 Synaptics TouchPad: YAxisMapping: buttons 4 and 5
[  3514.827] (**) evdev: PS/2 Synaptics TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  3514.827] (II) XINPUT: Adding extended input device "PS/2 Synaptics TouchPad" (type: MOUSE, id 12)
[  3514.827] (II) evdev: PS/2 Synaptics TouchPad: initialized for relative axes.
[  3514.828] (**) PS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  3514.828] (**) PS/2 Synaptics TouchPad: (accel) acceleration profile 0
[  3514.828] (**) PS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  3514.828] (**) PS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  3514.829] (II) config/udev: Adding input device PS/2 Synaptics TouchPad (/dev/input/mouse0)

```
[/LIST]
In essence it looks like for some reason my touchpad is getting treated as a mouse and I can't figure out why. 



There's been some other stuff that I've tried/read about, but I can't quite remember all of it (lots and lots of Googling has made my mind and eyes glaze over). Regardless, if anybody knows what's going on here or can point me in the right direction, it would very much be appreciated!

---

