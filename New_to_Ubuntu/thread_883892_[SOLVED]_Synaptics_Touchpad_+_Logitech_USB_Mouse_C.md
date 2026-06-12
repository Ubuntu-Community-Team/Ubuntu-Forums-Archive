---
title: "[SOLVED] Synaptics Touchpad + Logitech USB Mouse: Coonfiguration Problems"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by degroof on 2008-08-08
I've got 8.04 (wubi) on an Acer 5920 with a Synaptics touchpad and a Logitech USB wireless mouse. Both the mouse and the touchpad work, up to a point.

The problem I'm having is that the "touchpad" tab in the mouse settings dialog seems to have no effect on the touchpad. The touchpad seems to be defaulting to a state where it's very sensitive and the button1 tapping is enabled.

All I really want to do is disable tapping and maybe ease up on the sensitivity a bit. I'd rather not disable it altogether. 

I've added SHMConfig to xorg.conf. I've tried using synclient to alter the settings. I've even tried putting Option "Tapbutton1" "0"  in xorg.config. None of it affects the behavior of the touchpad.

Another clue: synclient -m 20 prints out a single status message, then nothing. No amount of tapping or clicking will cause it to send out another message.

I'm guessing that the mouse and the touchpad are interfering with each other. 

Any suggestions?

---

### Post by nicedude on 2008-08-11
You could try installing tpconfig from the repositories and see if it can properly manage your touchpad. Although it is command line based just read the manual page by typing "man tpconfig" without quotes to read the manual, then just start trying to see what you can get it to do.

Hope that helps

nicedude

---

### Post by degroof on 2008-08-11
Thanks. I installed tpconfig and tried a few things but can't seem to get the tapping disabled. The info is interesting, though:

```
sudo tpconfig -i
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;		no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.
```

I think it's saying that tapping is turned off but it's not. Nothing I do affects it. 

```
sudo tpconfig -t0
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Corner taps disabled;		no tap gestures.
```

```
sudo tpconfig -t1
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Corner taps disabled;		no tap gestures.
```

It's acting like it's ignoring the options.

---

### Post by degroof on 2008-08-11
My xorg.conf...

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"true"
	Option		"TapButton1"		"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```


And some info from Xorg.0.log...


```
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(**) Option "SHMConfig" "true"
(**) Option "TapButton1" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
...
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(--) Synaptics Touchpad touchpad found
```

---

### Post by degroof on 2008-08-22
Quick update: Still not getting anywhere. Neither synclient nor tpconfig seem to have any effect on the behavior of the touchpad. The only thing that affects it is hitting Fn-F7 to toggle it off and on. 

The fact that **synclient -m 20** prints out only one line is interesting, though. Not sure what to make of that.

---

### Post by degroof on 2008-08-27
I ended up getting it to work by following the instructions in the first message in this thread: [http://ubuntuforums.org/showthread.php?t=517156](http://ubuntuforums.org/showthread.php?t=517156)

errenay has done a great job of consolidating all the steps into one place. I didn't bother with the mediakeys stuff but I followed everything else. I've now got both mouse and touchpad working with tapping turned off.

It's nice to be able to type without having my cursor jump every time my palm hits the pad.

---

### Post by crps on 2008-09-13
I have a logitech M-UAG120 7-button usb mouse and Ubuntu 8.04. 

The 3D wheel is like a traditional mouse scrolling wheel but that has also lateral switches, left and right.
[http://211.78.161.57/res/gdsale/st_pic/0378/st-378909-1.jpg](http://211.78.161.57/res/gdsale/st_pic/0378/st-378909-1.jpg) 

the problem is that both left ad right scrolling wheel buttons generate no outcome in xev so i don't know how to continue in xorg.conf.

---

### Post by GCurry on 2009-11-08
Haha, what a great thread.   All of a sudden I was having trouble with my mouse warping.   I'd move it, then after investigation found that it'd warp back to the same spot on the screen.   Couldn't figure it out.

Saw this thread, realized I had a Wacom Bamboo tablet attached.   I'd just cleaned the desk, and placed the pen / holder on the tablet.   

The tablet and mouse were interfering.   Moved pen.   Problem solved.   Thanks!  :D

---

