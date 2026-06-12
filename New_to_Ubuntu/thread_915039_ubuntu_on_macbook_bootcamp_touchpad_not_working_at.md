---
title: "ubuntu on macbook bootcamp touchpad not working at all"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by tettayes on 2008-09-09
I installed Ubuntu using wubi, Windows XP, on my bootcamp partition.
However, whenever I boot into Ubuntu, my touchpad is not responding at all.  So I have to use power button to restart each time I boot into Ubuntu.

I have VMware fusion on my mac osx.  When I start Ubuntu in VMware, there is no problem at all with the touchpad.

Can anyone help me solve my problem??

Thank you very much!

---

### Post by tettayes on 2008-09-09
hmmm

---

### Post by knix on 2008-09-09
Can you post the contents of your /etc/X11/xorg.conf?
Specifically, the Input Device or Mouse Section (or the whole thing if you can't find it)

---

### Post by schauerlich on 2008-09-09
Check the MacBook Wiki in my sig.

Also, there is an [Apple Users forum](http://ubuntuforums.org/forumdisplay.php?f=328) on here where you will get responses from people more familiar with Mac hardware and Mac-specific bugs.

---

### Post by tettayes on 2008-09-09
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

that's how my configurations...booting from vmware.  I do not know where is the problem...

EDavidBurg, i was actually trying to find solutions earlier on that wiki page, but i was not being able to find any problems similar to mine.

thank you guys for quick responses

---

