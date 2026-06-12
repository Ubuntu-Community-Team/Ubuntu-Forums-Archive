---
title: "[SOLVED] How do I set mouse and mousepad to have same speed?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by aridus on 2008-05-25
I am using a Dell 830 laptop with an external logitech bluetooth mouse but sometimes I only use the mousepad. Both mouse and mousepad work fine except the speed of the mousepad is much slower than the external mouse. If I change from one to the other I have to reset the speed in System - Preferences - Mouse. Is there anyway I can set the speed of the two to be the same so that I don't have to keep on changing the setting? It's really annoying!

With grateful thanks.

---

### Post by unutbu on 2008-05-25
Please post the "InputDevice" stanzas from your /etc/X11/xorg.conf.

Also take a look at [http://bbs.archlinux.org/viewtopic.php?id=44530](http://bbs.archlinux.org/viewtopic.php?id=44530).

Notice in jbromley's post there is an option that can be set on the ALPS GlidePoint (synaptics driver)  that looks like this:

```
 Option      "AccelFactor" "0.03"
```

I don't know what driver is controlling your mousepad (touchpad?), but if we can find that out, we may be able to find what options can be set in xorg.conf... hopefully something like AccelFactor...

---

### Post by Kinst on 2008-05-25
If you're using a synaptics touchpad you can use this command to see what your touchpad settings are. Then tweak them using xorg.conf.

```
synclient -l
```

---

### Post by unutbu on 2008-05-25
According to [http://www.suseforums.net/index.php?showtopic=36053&st=0&p=184850&#entry184850](http://www.suseforums.net/index.php?showtopic=36053&st=0&p=184850&#entry184850)
the Dell 830 does use the synaptics driver. Here is an example InputDevice stanza:

```
Section "InputDevice"
Driver "synaptics"
Identifier "Mouse[3]"         # <-- Change this to whatever Identifier you've been using
**Option "AccelFactor" "0.01"**
Option "BottomEdge" "650"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "2"
Option "CircularScrolling" "1"
Option "Device" "/dev/input/mice"
Option "EdgeMotionMaxSpeed" "15"
Option "EdgeMotionMinSpeed" "15"
Option "Emulate3Buttons" "on"
Option "EmulateMidButtonTime" "75"
Option "FingerHigh" "15"
Option "FingerLow" "14"
Option "HorizScrollDelta" "20"
Option "LeftEdge" "120"
**Option "MaxSpeed" "0.5"**
Option "MaxTapMove" "110"
Option "MaxTapTime" "180"
**Option "MinSpeed" "0.2"**
Option "Name" "Touchpad"
Option "Protocol" "auto-dev"
Option "RightEdge" "830"
Option "SHMConfig" "on"
Option "TopEdge" "120"
Option "UpDownScrolling" "1"
Option "Vendor" "ALPS"
Option "VertScrollDelta" "20"
Option "ZAxisMapping" "4 5"
EndSection
```

---

### Post by aridus on 2008-05-26
This is what happens when I try:

martin@martin-laptop:~$ synclient -l
Can't access shared memory area. SHMConfig disabled?

I do not no what this means. Any further help would be appreciated.

---

### Post by unutbu on 2008-05-26
There is a bug report which seems relevant:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/203815](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/203815)

You might want to try adding 

```
Option "SMHConfig" "on"
```
To the 'Section "InputDevice"' stanza (the quit all apps and restart X with Ctrl-Alt-Backspace), but it may not work given the bug report.

What does your xorg.conf look like now?
Have you tried 'Option "AccelFactor" "0.03"'?

---

### Post by aridus on 2008-05-27
My current xorg.conf is below. I tried adding Option "SMHConfig" "on" but it resolved nothing. I then added Option "AccelFactor" "0.03"' and it put my graphics into slow resolution and I had to do sudo dpkg-reconfigure -phigh xserver-xorg to return to the original configuration.

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

---

### Post by unutbu on 2008-05-27
Have you tried
```
Option "MaxSpeed" "0.5"
Option "MinSpeed" "0.2"
```
?

---

### Post by aridus on 2008-05-27
Many thanks! With a little experimentation I have found that this combination

	Option 		"MaxSpeed" 		"0.7"
	Option 		"MinSpeed" 		"0.2"
	Option      	"AccelFactor" 		"0.08"

gives me mousepad behaviour that more closely matches my mouse.

---

