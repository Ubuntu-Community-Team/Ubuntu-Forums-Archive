---
title: "Touchpad not working after update - Samsung N150 'plus' netbook"
date: 2015-03-02
forum: New to Ubuntu
---

### Post by cg4288 on 2015-03-02
Just found a netbook in a closet (long story) - figured i'd restore it.  Just put on lubuntu, did an update, restarted and my touchpad went out.  :(  No movement, no two finger scrolling, nothing, although i can right click - and somehow my left click came back.   I'm using my brother's wireless mouse right now - that works fine.  Here's some stuff that might be helpful:

```
user@plop:~$ xinput list&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=11	[slave  pointer  (2)]
&#9116;   &#8627; reserved Dynex Watermelon Wireless Mice 	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; WebCam SCB-0340N                        	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
user@plop:~$ xinput list-props "ETPS/2 Elantech Touchpad"
Device 'ETPS/2 Elantech Touchpad':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (262):	0
	Device Accel Constant Deceleration (263):	1.000000
	Device Accel Adaptive Deceleration (264):	1.000000
	Device Accel Velocity Scaling (265):	10.000000
	Device Product ID (252):	2, 14
	Device Node (253):	"/dev/input/event5"
	Evdev Axis Inversion (266):	0, 0
	Evdev Axis Calibration (267):	<no items>
	Evdev Axes Swap (268):	0
	Axis Labels (269):	"Abs MT Position X" (260), "Abs MT Position Y" (261), "Abs Pressure" (258), "Abs Tool Width" (259), "None" (0), "None" (0)
	Button Labels (270):	"Button Left" (138), "Button Unknown" (255), "Button Right" (140), "Button Wheel Up" (141), "Button Wheel Down" (142)
	Evdev Middle Button Emulation (271):	0
	Evdev Middle Button Timeout (272):	50
	Evdev Third Button Emulation (273):	0
	Evdev Third Button Emulation Timeout (274):	1000
	Evdev Third Button Emulation Button (275):	3
	Evdev Third Button Emulation Threshold (276):	20
	Evdev Wheel Emulation (277):	0
	Evdev Wheel Emulation Axes (278):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (279):	10
	Evdev Wheel Emulation Timeout (280):	200
	Evdev Wheel Emulation Button (281):	4
	Evdev Drag Lock Buttons (282):	0
	Synaptics Off (670):	0



```

---

### Post by cg4288 on 2015-03-02
Well, after a bunch of digging, I found a solution-ish:

[http://ubuntuforums.org/showthread.php?t=1668438](http://ubuntuforums.org/showthread.php?t=1668438)

But every time I reboot, I have to open up terminal and change the driver.  Halp.

EDIT:  I figured it out.  I feel like Mark Watney on Mars.

Okay, so I did this
```
gk[COLOR=#000000][FONT=Ubuntu Mono]sudo gedit /etc/rc.local[/FONT][/COLOR]
```

and put in these two lines
```
[COLOR=#000000][FONT=Ubuntu Mono]modprobe -r psmouse
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]modprobe psmouse proto=imps[/FONT][/COLOR]
```
After the #blablabla but before Exit 0

I'll keep this here in case someone else has touchpad troubles - it's an older generic driver, but it'll do.

---

