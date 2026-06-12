---
title: "touchpad issues...."
date: 2008-06-29
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-06-29
ok I get this error plz help me fix it
```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

```

---

### Post by TeoBigusGeekus on 2008-06-29
```
You have to set 'SHMConfig' 'true' in xorg.conf
```
Well, have you done it?

---

### Post by soccerboy on 2008-06-29
> **133794m3r said:**
> ok I get this error plz help me fix it
```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

```

you'll find xorg.conf in /etc/X11/.

Open it up with your favorite editor.

---

### Post by 133794m3r on 2008-06-29
> **TeoBigusGeekus said:**
> ```
You have to set 'SHMConfig' 'true' in xorg.conf
```
Well, have you done it?
no.... I've even reset the file...
> **soccerboy said:**
> you'll find xorg.conf in /etc/X11/.

Open it up with your favorite editor.
and that shm line  isn't in there anymore.....so what do i do?

---

### Post by drs305 on 2008-06-29
If you want to make the change:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1		
gksudo gedit /etc/X11/xorg.conf

```
I didn't have a listing for GSynaptics. If you have one, it would go there. For my setup:

To Section "InputDevice"
	   Identifier      "Synaptics Touchpad"
Add:
```

Option         	"SHMConfig"             "true"

```

---

### Post by bhadotia on 2008-06-29
Do this:
```
 sudo gedit /etc/X11/xorg.conf 
```
Then in the file that open find the section with the heading "Synaptics touchpad" under input devices , it looks like this:
> Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Edit it to look like this:
> Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
        Option          "SHMConfig"             "true"
EndSection
You can also set "HorizEdgeScroll" to "1" if you want that.

---

### Post by 133794m3r on 2008-06-29
> **drs305 said:**
> If you want to make the change:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1		
gksudo gedit /etc/X11/xorg.conf

```
I didn't have a listing for GSynaptics. If you have one, it would go there. For my setup:

To Section "InputDevice"
	   Identifier      "Synaptics Touchpad"
Add:
```

Option         	"SHMConfig"             "true"

```

ok have this in taht section
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
        Option         	"SHMConfig"             "true"
EndSection
```
but I still get 
```
 GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

``` it seems it hates me....

---

### Post by bhadotia on 2008-06-29
You have to log out and then log back in to make it work.

---

### Post by 133794m3r on 2008-06-29
oh ok... thanks...

---

### Post by mindhaq on 2008-07-04
I also always get the following error when trying to start gsynaptics:

```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

The part in my xorg.conf is like this, and I restarted the system many times after adding it.

```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "true"
EndSection
```

What else needs to be done to enable this?

---

