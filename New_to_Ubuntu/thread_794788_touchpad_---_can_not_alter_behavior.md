---
title: "touchpad --- can not alter behavior"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by raequin on 2008-05-14
Hi, all. I have been trying since installation of Hardy to get my touchpad working well when I type. I have edited xorg.conf, as shown below. Syndaemon has no effect when I run it. Also, System->Preferences->Mouse changes nothing, even when I uncheck the box "enable touchpad."

There are only two things that I can do to affect the touchpad, use Fn+F7 that is the touchpad on / off button that came with the laptop (an Acer), or use Mousetweaks pointer capture on the panel.

I would like to be able to either turn off the touchpad with either keyboard shortctus or by terminal command (which maybe I could bind to a keyboard shortcut), or get the syndaemon working so that I can type without worrying about the touchpad.

Here is a part of xorg.conf:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "SHMConfig" "on"
# Option "MaxTapTime" "0"
EndSection

"MaxTapTime" did nothing either.  Nothing I do in gsynaptics has any effect.

---

### Post by ZabiGG on 2008-05-14
Hi ;)

Try the Hardware and Laptops section of this site. I'm sure someone knowledgeable can help you there :)

---

### Post by starcannon on 2008-05-15
change Option "SHMConfig" "on"

to Option "SHMConfig" "true"

then sudo apt-get install gsynapic

---

### Post by raequin on 2008-05-15
I had already tried using "true" instead of "on," and I received the following message regarding installing gsynaptic:

Note, selecting synaptic instead of gsynaptic
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

