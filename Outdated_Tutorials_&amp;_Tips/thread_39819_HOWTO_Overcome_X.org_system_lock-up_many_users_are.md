---
title: "HOWTO: Overcome X.org system lock-up many users are experiencing"
date: 2005-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by simianMiscreant on 2005-06-06
You may or may not be one of hundreds of Linux users spanning multiple distros, video cards, and video drivers experiencing the nefarious system lock-up apparently caused by a driver-level problem (perhaps even kernel-level) with X.org. On my particular system, the system hard-locks and stops responding to ping, and I have to power off/on. Usually some sort of icon dragging, column resizing, or Firefox scrolling (all things that use acceleration) precipitates the crash. Some users report mouse movement, and some are even able to SSH back in to their machines. Those latter few have brought back the knowledge that the problem is caused by X.org - a "top" shows X.org eating 99.5% of CPU. I have found a way around this, but it isn't pretty - expect to disable all acceleration on your card (including 2-D) meaning no video playback, a laggy GUI, and zero 3-D of any sort. I've tried this using "radeon" and "fglrx," and since I don't have an nVidia card, I'd appreciate if an nVidia user could fiddle around and bring back results. For ATI users, here are the commands I used to negotiate the crash (I'm going to also include what options I'm using positively [not disabling], as these might or might not have anything to do with the fix):
```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
**[COLOR=Red]#	Load	"dri"[/COLOR]**
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
  	Load 	"GLcore"
        # Load "extmod" but omit DGA extension
  SubSection "extmod"
    Option "omit xfree86-dga"
  EndSubSection
``` 
In the Module section, comment out DRI support.
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9800 (M18 JN)"
	Driver "radeon"

**[COLOR=Red]	Option "NoAccel" "true"[/COLOR]**
	Option "DDCMode" "true"
	Option "DisplayPriority" "BIOS"
	Option "MonitorLayout" "LVDS, TMDS"
**[COLOR=Red]	Option "RenderAccel" "false"[/COLOR]**
**[COLOR=Red]	Option "MergedFB" "off"
``` [/COLOR]**
Your Device section should include these options - disabling acceleration, accelerated rendering, and a merged framebuffer.

I hope that fixes people up - it's a huge deal right now across many distros. I know for a fact users of Fedora Core 3 and Gentoo are experiencing this crash. Now we sit tight for an X.org update to fix this and give us back our hardware acceleration.

---

### Post by nocturn on 2005-06-07
For me, just disabling renderaccel did it (dri has to be disabled, it is in te driver README).

AFAIK, this bug is in the Nvidia drivers themselves, it happens with Xfree too, but it is less common there.

---

### Post by simianMiscreant on 2005-06-07
Something happened as a result of an update or something...a month ago (before I formatted) I was using the exact same xorg.conf, and had no problems (plus sexy acceleration). Then I format, reinstall, and all of a sudden i get this crash.

---

### Post by oddabe19 on 2005-06-07
Through research, in other forums mainly, there is a common theme, and that is ACPI and APM.

many people seem to agree that disabling powermanagement in bios and on startup fixes most problems.

It didn't for me, and i only get the crash when i tried to use Xcompmgr. Reverting to Nvidia 6111 drivers fixed it. But since i like living on the edge i use 7664 drivers, but i haven't used xcompmgr yet with them.

---

### Post by Tobi Vollebregt on 2005-06-07
[QUOTE=nocturn]For me, just disabling renderaccel did it[/QUOTE]
same for me

---

### Post by Spudgun on 2005-06-07
Me too, so far. *Crosses fingers*

---

### Post by nocturn on 2005-06-08
[QUOTE=oddabe19]Through research, in other forums mainly, there is a common theme, and that is ACPI and APM.

many people seem to agree that disabling powermanagement in bios and on startup fixes most problems.

It didn't for me, and i only get the crash when i tried to use Xcompmgr. Reverting to Nvidia 6111 drivers fixed it. But since i like living on the edge i use 7664 drivers, but i haven't used xcompmgr yet with them.[/QUOTE]

I have never used xcompmgr, for me, FireFox caused the crashes... (Pretty hard to avoid using it).

Anyway, xcompmgr is still highly experimental.

---

### Post by foxy123 on 2005-06-08
Actually it is not the best idea to disable 3D acceleration, since it is required for things like games and maybe some others. I would think that it should be the last option or a temporary solution.

I would proceed in the following order:

1. Disable FastWrite (in BIOS or in the xorg.conf)
2. Set UseInternalAGPGART to no
3. Downgrade AGP from x8 to x4 (or from x4 to x2)
4. Increase AGP voltage
5. Check your video chip cooling
6. Disable 3D acceleration, if the above did not help.

I can extend those sections if I have time this weekend, though you can take a look at 3DRage forum for more information.

---

### Post by simianMiscreant on 2005-06-23
Any progress here? Some people say 2.6.11 fixes this...true?

---

### Post by barnone on 2005-06-23
I disabled APM and ACPI and that fixed my problems.  I have full 3d and 2d acceleration enabled and it is running great!  Prior to that I would get the lockups people talk about here.

Radeon 9800 Pro - fglrx
2.6.10-5-686-smp

---

### Post by neighborlee on 2005-06-24
[QUOTE=barnone]I disabled APM and ACPI and that fixed my problems.  I have full 3d and 2d acceleration enabled and it is running great!  Prior to that I would get the lockups people talk about here.

Radeon 9800 Pro - fglrx
2.6.10-5-686-smp[/QUOTE]

My bios wont let me ( dell computer) disable power management so can both apm and acpi be disabled on kernel line ? ( noacpi noapm ?)

thx
nl

---

### Post by barnone on 2005-06-27
You can simply run /etc/init.d/apm stop and /etc/init.d/acpid stop to stop them.

I think it is apm, may be apmd... not sure as I am at work.

---

### Post by hesselim on 2005-06-28
I disabled all hardware accel support and the bios apm and acpi support. I even shut down linux apm and acpi (/etc/init.d/apmd stop etc. etc.) support after booting.

I am still experiencing system lock-ups. The lock-ups appear not directly, but 30 - 60 minutes after system startup.

I am using an IBM A50 with 2.4ghz celleron D, 512mb and onboard intel extreme graphics 2.

Has anyone also a similar configuration and still experiencing lock-ups

Note: I can disable APM in bios, but can't disavle acpi support. The IBM bios won't let me.

---

### Post by DarkT on 2005-06-28
I don't know if it's the same problem but I had something similar ages ago with my nvidia cards and the solution was to edit my xorg.conf adding the line in red:
```

Section "Device"
	Identifier	"NVIDIA Corporation NV36 [GeForce FX 5700]"
	Driver		"nvidia"
#	Driver		"nv"
	BusID		"PCI:2:0:0"
[COLOR=Red]	Option		"IgnoreDisplayDevices"	"TV, DFP"[/COLOR]
	Option		"NoLogo"
EndSection

```
 
This stops the driver from scanning for other visual adapters.
Like I said, may be the wrong problem but it's always fixed nvidia lockups for me.

---

### Post by carlosalvatore on 2008-03-27
I use nVidia  GForce MX 4000, when i had this problem i just uninstall the restricted driver from nvidia, i restart the pc, then i reinstall the restricted driver, restart again and everything was solved.

This also fix x problems when installing java fonts, i uninstall-reinstall nVidia restricted driver and everything works fine again.

I hope this works for you.

Greetings

---

