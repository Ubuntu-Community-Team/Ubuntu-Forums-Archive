---
title: "Monitor flickering relentlessly... refresh rate?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by theShaggy on 2008-10-07
I'm not sure where else to put this...

For seemingly no reason, the other day I went to an old PIII with Xubuntu 7.10 using the NV driver on my Geforce MMX 440 and discovered that moving the mouse or anything on the screen caused the monitor to flicker.  Not just the screen, but I get a clicking noise and the whole thing flickers back and forth.

The next day I restarted the computer, and this completely destroyed using it.  I have used a dpkg-reconfigure on the xserver, have installed the proprietary Nvidia legacy drivers and tried to change ht refresh rate as much as a can.  No luck.

The thing is, loading up the computer works fine, it's when the X server starts that I have a problem.

Anyone have any suggestions?  I am at a complete loss at this point.

---

### Post by talsemgeest on 2008-10-08
Can you post your xorg.conf?

---

### Post by theShaggy on 2008-10-08
Not as far as I can tell.  I can't even load up the login screen with any consistency, let alone open xorg.conf.  Now it starts flickering and most of the time will completely stall on me.

It appears to be the same problem as this: [http://ubuntuforums.org/showthread.php?t=761447&highlight=battery.ko%3Bxserver](http://ubuntuforums.org/showthread.php?t=761447&highlight=battery.ko%3Bxserver)

However, using acpi=force on the Grub command line does nothing, nor noapic, nor uninstalling acpi (which takes Xubuntu-desktop with it).  Apparently it has decided that my desktop computer is, in fact, a laptop, and for some reason this won't let me reconfigure xorg.

I will try tomorrow or Thursday, though.

---

### Post by talsemgeest on 2008-10-08
Well you can go into recovery mode to the root command line. You can see your xorg.conf by ```
nano /etc/X11/xorg.conf
```And if you need to post it onto a website, you can use the text only web browser lynx ```
apt-get install lynx
```

---

### Post by theShaggy on 2008-10-10
Unfortunately, I won't be able to at this point.  I've been slowly trying to eek out the problem, and have replaced my Xorg.conf repeatedly by installing drivers and removing drivers.  I've even completely replaced GDM and Xubuntu-desktop and xserver-xorg and it still gives me the problem, so I'm betting my xorg.conf isn't the issue.

However, I have stopped the monitor clicking, but the refresh rate refuses to budge, and it appears to be causing the screen (not the mouse, though) to freeze at random instances during boot.

I've tried to upgrade to Hardy from Gutsy with no luck, physically edited my xorg.conf file (after all the other issues) to run with NV, Vesa and Nvidia drivers, and have recently attempted to reinstall Xubuntu.  Which froze in the middle and so now grub won't load at all.

I just tried running the LiveCD, and it's giving me the same refresh problem, so I have no idea.  The Ubuntu loading screen (whth the progress bar) looks perfectly fine, but as soon as the login screen hits the refresh problem starts.

Another interesting thing is that when I ran the recovery boot, the command line looked fine, but if I loaded to the login screen and Ctrl-Alt-F1'ed to the command line, it would still be giving me refresh problems.

Is this my video card melting?  It is slightly old.  I was going to check on my windows partition that I forgot I still had on there, but Grub doesn't work any more so I can't.

---

### Post by theShaggy on 2008-10-10
Just to follow up:

I've managed to resintall Xubuntu, and everything worked lovely.

And then I tried to switch the video driver in xorg from "vesa" to "nv," and the problem came back.

It seems to me that this is effectively the issue.  When I do a dpkg-reconfigure xserver-xorg, it goes through the rigamarole but then I only have the simple "configured monitor" entry.  I will post it here when I get back to that computer (in the other room).

For whatever reason, the only driver that works is vesa.  That's it.  I'm confused.

---

### Post by theShaggy on 2008-10-10
Okay, here is my xorg.conf as requested.

Mods (or whomever), I am obviously not an absolute beginner, just didn't know where I'd get a response.  Could you move this somewhere more appropriate?

Anyway, currently it sits in "Vesa" mode because if it is anything but vesa, the refresh rate goes bananas, the monitor flickers and often clicks on and off.  I'd think that my card is crapping out at high resolutions and refreshes, but Vesa is running 1078x780 an 85hz without a problem.  If I try NV, or if I try Nvidia, it immediate drops the refresh to 60 and will often crash the computer entirely.

So... yeah.  When I run a dpkg-reconfigure I get pretty much nothing, as if it can't detect my monitor.  However, if I install the nvidia drivers, it will detect it without problem and everything goes nuts again.

What's going on, anyone know?

> # Xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	31-70
	VertRefresh	55-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by talsemgeest on 2008-10-10
Try giving envy a go. It is in the repositories, and should configure everything properly.

---

### Post by theShaggy on 2008-10-10
Already done so, way back.

It really seems to be that the computer doesn't like anything above vesa.  I am about to try the legacy driver from the repos, just to see if I can get any reaction.

*And react it did*, by freezing my computer and killing the monitor.

---

### Post by talsemgeest on 2008-10-11
Ok, I just had a thought. Maybe try installing the new xubuntu 8.10 intrepid ibex. It uses the new xserver, so it might help you out. You can either wait until the 31st of October or install the beta now.

---

### Post by theShaggy on 2008-10-11
Hmm... I might actually try that.  I've just used Envy to give it one more go, and if it still screws up will post my xorg.conf from that to compare to the one that does work.

If all else fails, 8.10 may just be worth trying.  I do use that machine on a daily basis for video playing, so I am missing it a bit.

---

