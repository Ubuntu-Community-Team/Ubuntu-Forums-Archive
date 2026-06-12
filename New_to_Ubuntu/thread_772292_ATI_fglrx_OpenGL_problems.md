---
title: "ATI fglrx OpenGL problems"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by figuringout on 2008-04-28
I have been struggling with this for a few days now. Here goes

my xorg.conf has this

Section "Device"
	Identifier	"ATI Technologies Inc RC410 [Radeon Xpress 200]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	Busid		"PCI:1:5:0"
EndSection

my fglrxinfo gives me this

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

I'm on Ubuntu 7.10 and need to get the standard ATI Radeon OpenGL drivers. i.e I need to see these magical words

$fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.1.7415 Release

I have tried trick #1 from here [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying) to no avail.

Any help is appreciated.

PS: I'm getting a FPS of around 600-700 on glxgears, is that good/bad? Anyone has experience with this particular chipset could also chip in.

---

### Post by forrestcupp on 2008-04-28
Edit: Nevermind, I didn't read your post well.

If you have Xgl installed, that may be your problem.  Uninstall it.
```
sudo apt-get remove xserver-xgl
```

---

