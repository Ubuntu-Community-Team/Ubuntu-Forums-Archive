---
title: "dual monitors"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Sham885 on 2008-06-11
I'm trying to setup bigdesktop.  I followed this thread: [http://ubuntuforums.org/showthread.php?p=1773544]("http://ubuntuforums.org/showthread.php?p=1773544") typing the commands into the terminal and then restarted.  It only asked for my login on one screen but then went back to both screens showing the same thing.  I opened the xorg file and under the devices sections it shows this:

```
Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1280x1024+1280x1024,0x0+0x0"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

```

I'm not sure what I need to change?  Also it says there is crt1 and crt2 connected and enabled when one monitor is a vga and I still only have one display listed under screen resolution settings.

---

