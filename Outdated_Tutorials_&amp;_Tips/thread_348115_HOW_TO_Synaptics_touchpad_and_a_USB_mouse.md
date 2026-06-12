---
title: "HOW TO: Synaptics touchpad *and* a USB mouse"
date: 2007-01-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Choad on 2007-01-28
This how to will get your laptop's touchpad working with a USB mouse at the same time. People who use their laptop as a replacement desktop often want to use a proper mouse when sitting at a desk, and ubuntu doesnt set this up for you if you want to use the full-featured synaptic driver as well.

**_[SIZE="4"]here goes:[/SIZE]_**

```
stuff written in these boxes should be entered in to a terminal. applications > accessories > terminal
```

**Step 1**

Make sure your touchpad IS using the synaptics driver, or at least CAN use the synaptics driver. Im not entirely sure how you go about finding this out, but 95% of laptops use this type of touchpad.

Also make sure you have a USB mouse otherwise you wont be able to test if it works.

**Step 2**

Back up the old xorg.conf file. 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```

**Step 3**

Open up your xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
(note: other *buntu distributions will use a different text editor)

this is the important bit.

below are the RELEVANT sections from my xorg.conf file. everyones xorg.conf file looks different, so dont worry if you arent seeing what i have. All you need to do is make sure the bits that i have made colourful are in your file too. it is not necessary to change the name of your devices to "Synaptics Mouse" and "USB Mouse" but it just makes more sense that way 

it is likely that you only have one "input device" for one mouse at the moment. this is probably set up to use either the "synaptic" driver, or the generic "mouse" driver. If this is the case, then you will want to add a new device. you can safely use my ones here and just copy and paste them,

(this is not to be entered in to a terminal, i used a code box to keep the formatting)
```
[B][COLOR="Red"]Section "InputDevice"
	Identifier	[COLOR="DeepSkyBlue"]"Synaptics Mouse"[/COLOR]
	Driver		"synaptics"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"[/COLOR][/B]
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"HorizScrollDelta"	"0"
        #Option		"SHMConfig"    		"true"
[COLOR="Red"]**EndSection**[/COLOR]

[B][COLOR="Red"]Section "InputDevice"
        Identifier  [COLOR="SeaGreen"]"USB Mouse"[/COLOR]
        Driver      "mouse"
        Option      "Protocol"         "Auto"
        Option      "Device"           "/dev/input/mice"[/COLOR][/B]
        Option      "ZAxisMapping"     "4 5"
        Option      "Emulate3Buttons"  "false"
**[COLOR="Red"]EndSection[/COLOR]**

[COLOR="Red"]**Section "ServerLayout"**[/COLOR]
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	[COLOR="Red"][B]InputDevice	[COLOR="DeepSkyBlue"]"Synaptics Mouse" [/COLOR]		"CorePointer"
	InputDevice	[COLOR="SeaGreen"]"USB Mouse"	[/COLOR]		"AlwaysCore"[/B][/COLOR]
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
[COLOR="Red"]**EndSection**[/COLOR]

```

make sure that the device "identifier" is the same as what is written in the "ServerLayout" section at the end (i colour coded to make it more obvious)

all done? good!

**_save_** and quit

**Step 4**

copy the instructions from the bit below, about how to recover if it blows up in your face

**Step 5**

restart your X Server by pressing ctrl+alt+backspace (this will kill all your programs - be warned)

all done!




**_[SIZE="4"]What if everything now doesnt work?[/SIZE]_**

if the mouse now doesnt work at all, or your computer gives you errors about the xserver, do the following

**Step 1**

move to a console by pressing ctrl+alt+f1

**Step 2**

log in

**Step 3**

```
sudo cp /etc/X11/xorg.conf ~/xorg.conf
sudo cp /etc/X11/xorg.conf.mybackup /etc/X11/xorg.conf
startx

```

-----------------------------------------------------------------------------------------------

i cant guarantee anything about this how to. i have to the best of my ability reduced the risk of trying this, but ya know... if you bork your system messing with system files you can only blame yourself :)

having said that, i see no reason why this should do any damage that cant be easily recovered from

---

### Post by earlycj5 on 2007-02-05
Thanks Choad.

I had this set-up before when I was using Slackware on another computer and it was driving me nuts trying to figure it out again.

I did have to make one change, I'm using Ksynaptics, it complained that I needed to add 
```

[COLOR="Blue"]**Option		"SHMConfig"    		"on" **[/COLOR]

```to my xorg.conf file.

I uncommented 
```

**[COLOR="Red"]#Option		"SHMConfig"    		"true"[/COLOR]**

```

and replaced true with on, works great now!

One other thing, don't forget to load the synaptics module.

Put this in the modules section at the beginning of your xorg.conf file.
```

Section "Module"
           Several other modules loaded here.
           [COLOR="Blue"]**Load    "synaptics"**[/COLOR]
End Section

```

---

