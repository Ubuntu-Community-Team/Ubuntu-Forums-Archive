---
title: "enable serial mouse (COM1)"
date: 2006-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by yossman on 2006-07-30
this afternoon i got help from a friend of mine who knows more about Xorg than i do to assist me in getting a serial mouse working on COM1, while leaving my laptop's trackpoint enabled at the same time.  i had succeeded in getting the serial mouse to replace the trackpoint, but i didn't want it to be an either-or solution.  i'm using a no-name serial mouse with 2 buttons.

i used 'mdetect -v' to ensure that it was seeing the mouse connected to COM1, which is /dev/ttyS0; moving the serial mouse around while mdetect is running is recommended.  our solution requires editing /etc/X11/xorg.conf, and as usual you should make a backup of it first.  using terminal:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.working
sudo gedit /etc/X11/xorg.conf &

```

this opens gedit to edit the xorg.conf file.  my suggestion is to scroll down this file until you see a section for your "Configured Mouse", and remember, not everyone's "Configured Mouse" section is going to look the same.  mine looks like this:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

```

underneath this 'section', you're going to put a new section:

```

Section "InputDevice"
	Identifier	"Generic Serial Mouse"
	Driver		"mouse"
	Option		"Device"		"/dev/ttyS0"
	Option		"Protocol"		"Microsoft"
	Option		"Emulate3Buttons"	"true"
	Option		"SendCoreEvents"	"true"
EndSection

```

now, further down this same xorg.conf file, there is a section called "ServerLayout".  you need to tell this section about the new mouse you just added.  my "ServerLayout" section looks like this, with the "Generic Serial Mouse" added already:

```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"Generic Serial Mouse"
EndSection

```

note, you may not have all those entries in your ServerLayout list; the important one in the list above that i added is the line that says 'InputDevice "Generic Serial Mouse"'.

at this point, you should save the xorg.conf file, and close gedit.  if you want to see if your changes worked right away, close all the windows you're working on, then hit 'ctrl-alt-backspace' keyboard combination.  this temporarily shuts down the X interface; you will momentarily see a black screen with a "login:" prompt.  wait a few seconds for X to come back up, which will then present you with your standard graphical login prompt.

at this point, you should be able to move your serial mouse, and it should be moving the cursor.  you should also be able to continue using whatever other mice or pointing devices you had connected to the system at the same time.

i know serial mice are a legacy device that most people do not use anymore.  to me, this isn't so much about 'geez go buy a $5 USB mouse', it's more about getting legacy hardware to work if there isn't anything wrong with it, or if it's the only option you have.  many older systems out there, including laptops, do NOT have USB ports on them; if they also don't have a PS/2 port, or the PS/2 port isn't working, a serial mouse could conceivably be the only pointing device that would work.  luckily, almost every single old laptop/system has at least one serial port on it. ;-)

hope this helps anyone with a serial mouse, thanks for reading.


yossman

---

### Post by shaharudin on 2008-06-12
thanks yossman... it works great...

---

### Post by judas3000gold on 2008-10-26
A friend gave me an old trackball mouse it's a "Genius - HiTrak Serial" really a big piece, so I also had to play with my xorg.config

```

Section "InputDevice"
	Identifier	"Generic Serial Mouse"
	Driver		"mouse"
	Option		"Device"		"/dev/ttyS0"
	Option		"Protocol"		"Mousesystems"
	Option		"Emulate3Buttons"	"no"
	Option		"SendCoreEvents"	"true"
EndSection

```

---

### Post by gargoyle60 on 2009-09-16
I've spent over a week trying to get a serial mouse to work with grub, xubuntu, etc. on an old PC.
I tried all sorts of tips from various sources - wish I'd found this one first!
This solution worked first time. Many thanks.

---

