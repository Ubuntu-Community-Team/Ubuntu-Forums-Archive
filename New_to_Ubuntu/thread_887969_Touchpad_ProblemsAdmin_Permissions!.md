---
title: "Touchpad Problems/Admin Permissions!"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Method of Rhythm on 2008-08-12
Ubuntu has been great thus so far but there is one thing that is KILLING me and that is the insensitivity of the touchpad.  I downloaded "Touchpad" from the Add/Remove Programs GUI and go to edit my xorg.conf to enable this program but when I add the:

```
Option        "SHMConfig"        true
```

and go to save the file, it says that I do not have the necessary permissions and should check to see that I entered it in the right field.  I tried making my user an admin by booting into recovery mode and tried the command:

```
gpasswd -a **USERNAME** admin
```

And that didn't seem to help at all either as I got the same prompt after trying to save my changes to the xorg.conf file!

Please help!  Thank you very much.

---

### Post by LowSky on 2008-08-12
to edit the file all you need is sudo

example ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Method of Rhythm on 2008-08-12
Alright, my xorg.conf looks like this:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	[COLOR="DarkOrange"]Option		"SHMConfig"		"true"[/COLOR]
EndSection

```
*The orange is what I myself added*

And when I go to run Touchpad, I still get an error saying:

> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics


Sorry if this is all obvious information but this is day 2 with Linux so I am still learning.

---

### Post by Xavier Oddmon on 2008-08-15
I have this exact same problem, and I'd like a solution. My touch pad has way too little sensitivity.

---

### Post by SZ07 on 2008-08-16
After saving changes to xorg.conf did you restart X (via logout or ctrl+alt+backspace)?

If it still doesn't work, try to change the settings manually by adding this to the touchpad section in your xorg.conf file:

```
Option         "AccelFactor" "0.2"
Option         "MinSpeed" "0.4"
Option         "MaxSpeed" "1.5"
Option         "FingerLow" "5"
Option         "FingerHigh" "25"
```

Then change the numbers to see which setting works best. Don't forget to restart X after saving the changes to xorg.conf.

---

