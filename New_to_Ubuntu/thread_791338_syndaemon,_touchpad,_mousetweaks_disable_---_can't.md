---
title: "syndaemon, touchpad, mousetweaks disable --- can't disable touchpad"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by raequin on 2008-05-12
Hi, all.  I have been trying since installation of Hardy to get my touchpad working well when I type.  I have edited xorg.conf, as shown below.  Syndaemon has no effect when I run it.  Also, System->Preferences->Mouse changes nothing, even when I uncheck the box "enable touchpad."

There are only two things that I can do to affect the touchpad, use Fn+F7 that is the touchpad on / off button that came with the laptop (an Acer), or use Mousetweaks pointer capture on the panel.

I would like to be able to either turn off the touchpad with either keyboard shortctus or by terminal command (which maybe I could bind to a keyboard shortcut), or get the syndaemon working so that I can type without worrying about the touchpad.

Here is a part of xorg.conf:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"on"
#	Option		"MaxTapTime"		"0"
EndSection

Thanks.

ps --- "MaxTapTime" did nothing either.

---

