---
title: "[SOLVED] dual monitor problems"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by taith on 2008-11-04
hello everyone
i just bought myself a new desk(ooo... shiney)... and as i have more space now, i decided to set up my second monitor... i plugged it in... and i'm getting nothing on it... my mainscreen is a 1440x900 widescreen... my 2nd is a 1024x768...

from reading it seemed i'd need to edit my xorg.conf file...
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

anyone know what i would need to modify here specifically?

i tried to "sudo dpkg-reconfigure -phigh xserver-xorg" and terminals erroring this at me...

```
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20081104220704
```

edit:
FYI i am running ibex fresh install... so no screens and graphics *tear*

---

### Post by houbysoft.xf.cz on 2008-11-04
Hi, you need to run the dpkg-reconfigure command, this is right. The code you posted is not an error, it's just a warning and it says to you that it backed-up the old configuration file. You can just ignore it and continue. Does it say any error then? Or does it just hang?

---

### Post by taith on 2008-11-04
ok good :P and no... it just goes back to the prompt... but still wont display anything on the new monitor...

---

### Post by houbysoft.xf.cz on 2008-11-04
Maybe try without the -phigh option, so just
```

sudo dpkg-reconfigure xserver-xorg

```.
Also, **make sure** that the xorg.conf is not used by any other process (like a text editor in which you may be editing it, etc.).

Hope this helps.

---

### Post by ad_267 on 2008-11-04
It would be extremely helpful if you said what video card you have.

---

### Post by taith on 2008-11-04
its an nVidia 6800 if i remember properly...

and the re-config worked better... but still nothing... didnt even seem to have any settings to enable a 2nd monitor...

---

### Post by ad_267 on 2008-11-04
You should be able to enable it by pressing Alt+F2 and running "gksu nvidia-settings"

Enable the second monitor using TwinView and make sure you click "Save to X Configuration File."

---

