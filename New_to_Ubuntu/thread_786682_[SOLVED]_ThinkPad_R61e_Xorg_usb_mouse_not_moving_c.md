---
title: "[SOLVED] ThinkPad R61e Xorg usb mouse not moving cursor on screen"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by tubbygweilo on 2008-05-08
I have Ubuntu 8.04 LVM full disk encryption running on an [Lenovo R61e]("http://www5.pc.ibm.com/uk/products.nsf/$wwwPartNumLookup/_NG1DNUK?open&OpenDocument&epi=web_express") my problem is that the touchpad works yet a mouse connected to one of the two usb ports does not. The mouse light glows but when moved or the buttons clicked nothing happens to the pointer on the screen.

Code from xorg.conf
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
```

Could someone please publish a section of their xorg.conf that allows a mouse and touchpad to work together with an Rseries Thinkpad or point me to further sites / links for me to examine.

Many thanks.

---

### Post by tubbygweilo on 2008-05-10
Solved now. The problem was caused by a dead rodent so I went out and brought a new one - it all now works.

---

