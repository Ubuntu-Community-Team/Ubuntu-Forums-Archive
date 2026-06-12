---
title: "Really short xorg.conf = no gsynaptics = no circle scrolling"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Gepetto on 2008-11-17
My xorg.conf is really really short for some reason, which is fine since everything seems to work right now. But back in the day (before 8.10), I used gsynaptics so I could use circle scrolling. But now that I have nowhere to enable the SHMconfig thing, I can't get gsynaptics to work, and thus, no circle scrolling. Can I get circle scrolling back? 
Below is what my xorg.conf looks like

```

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
```

Any insight would be greatly appreciated!

---

### Post by phidia on 2008-11-17
From a google search > X.Org 7.4
The latest stable version of X.Org is available in Intrepid, promising better support for hot-pluggable input devices such as tablets, keyboards and mice. At the same time this will allow the great majority of users to run without an /etc/X11/xorg.conf file. A new failsafe X is introduced, to give better tools for troubleshooting X startup failures.

Everything you knew about xorg has changed and where configuration files are now is, to me, a mystery.

---

### Post by grim4593 on 2008-11-17
Note, this can break your X Graphic settings and dump you into the recovery mode on Intrepid. Make sure to back up to working xorg.conf file. You should be able to edit the /etc/X11/xorg.conf file from the command line or low graphics mode to get your computer back to the GUI.

What I did was add the Section "InputDevice" with the synaptics section as shown below. Then in the Server Layout I added "InputDevice	"Synaptics Touchpad".

Note, that while the default xorg.conf settings are sparse, you can still add sections just as before.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option 		"Protocol"		"auto"
	Option		"Device"		"/dev/psaux"
#	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"7"
	Option		"ButtonMapping"		"1 2 3 4 5 6 7"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "SHMConfig" "true"
	Option	    "RTCornerButton" "3"
	Option	    "RBCornerButton" "0"
	Option	    "LTCornerButton" "2"
	Option      "LBCornerButton" "2"
	Option      "PalmDetect" "1"
	Option      "PalmMinWidth" "5"
	Option      "PalmMinZ" "200"
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

---

### Post by kerry_s on 2008-11-17
you can alt+f# , kill X, then run
sudo su 
Xorg -configure

you should get a very basic xorg.conf.new file that you can copy to xorg.conf (cat xorg.conf.new > /etc/X11/xorg.conf)

---

### Post by Gepetto on 2008-11-17
Ohh, thanks guys, I totally forgot that 8.10 did a whole new thing tith Xorg. I got shmconfig enabled via [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig")

---

