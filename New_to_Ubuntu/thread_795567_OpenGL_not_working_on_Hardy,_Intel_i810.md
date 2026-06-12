---
title: "OpenGL not working on Hardy, Intel i810"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by spling on 2008-05-15
Hi,

I'm a complete Linux newbie and I would appreciate some clues to help me sort out what I think is either a video driver or OpenGL problem on my PC with a new installation of Hardy Heron.

Dell Optiplex GX150, 1GHz PIII, 512MB RAM
Built-in graphics, Intel i810 (I think)

X itself is running fine but I noticed that most of the screensavers didn't work properly, all they did was to display random moving horizontal lines.  A bit of googling suggested I try glxgears and that opens a black window and then we get the random horizontal lines again. 

I'm guessing that it's either a video driver or OpenGL problem as most video-related apps are working well.  I don't know if this is related but I've noticed also that the 'Visual Effects' part of Appearance Prefs comes up with a 'Desktop Effects could not be enabled' error if I select anything other than None,

Can anyone give me some pointers as to what I need to look at to help me diagnose this further?  From the googling I've done I've seen reference to the Device section in /etc/X11/xorg.conf as being where the video driver is specified but this is all I've got there:

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```
As a result I've got no idea where I can find out what video driver is actually in use.  For what it's worth, the screen resolution applet is showing appropriate options for screen size and refresh rate, but I don't know if that is a reliable  indicator that the appropriate driver is enabled or not.

Any clues would be well appreciated!

Thanks,
  Matthew.

---

### Post by Cato2 on 2008-05-16
Hardy can run without an xorg.conf file - a new feature that should help auto-configure X. (Google for Bulletproof X).

Something that may help to see what's going on is ```
less /var/log/Xorg.*.log
``` (you may have more than one, pick the one with most recent date/time.)  Scroll through here to see what driver is being loaded and what chipset it detects.

Other commands that may help are glxinfo and xdpyinfo.

Googling the Ubuntu forums may help, e.g. [http://ubuntuforums.org/showthread.php?t=672314](http://ubuntuforums.org/showthread.php?t=672314) .... Generally it seems that using Compiz on the i810 is not a great option.

---

