---
title: "Drivers?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Rad1 on 2008-07-29
Up-n-running with Hardy Desktop.

Have installed 'firmware' for wireless adapter (Broadcom BCM 43xx).

Wondering if I need to find drivers for other specific hardware.

For example, my touchpad (Synaptics) doesn't seem very smooth. And what about my onboard gfx (Intel 915 chipset)? Would my gfx look prettier (and run faster) with Intel 915 chipset/gfx drivers? 

Is it common practice to find Linux-specific drivers for all hardware in a system? Or only if non come with the distro?

What is wisdom on finding/using Linux drivers for specfic hardware?

---

### Post by Sef on 2008-07-29
> And what about my onboard gfx (Intel 915 chipset)?

System > Administration > Hardware Drivers

---

### Post by sam_delta on 2008-07-29
for the mouse, try going into system>preferences>mouse and adjust the sensivility/acceleration

if still too slow,
open a terminal and type
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```

the first command will make a backup
the second command will open a text file in "gedit"

in the text file, search for the Device "synaptic touchpad" and add the following lines 

> Option		"Minspeed"		"1.00"
	Option		"Maxspeed"		"1.00"
so it will look like this:
> 
Section "InputDevice"
	    Identifier	"Synaptics Touchpad"
	    Driver		"synaptics"
	    Option		"SendCoreEvents"	"true"
	    Option		"Device"		"/dev/psaux"
	   Option		"Protocol"		"auto-dev"
	    Option		"HorizEdgeScroll"	"0"
	   [b]Option		"Minspeed"		"1.00"
	  Option		"Maxspeed"		"1.00"[/b]
EndSection


save the file and restart X server by pressing "Control+Alt+backspace"

if something goes wrong, restore the backup file by typing ```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

tell us how it goes
sam

---

### Post by ModdTaco on 2008-07-29
If you can go max on the visual effects (Tier 3) then your pretty much set. You dont need to install new drivers. Also If you can go that high, the Compiz Config Manager can take your gnome desktop to the next level in effects.

---

### Post by Rad1 on 2008-07-29
Thanks, I will try your suggestions.

---

