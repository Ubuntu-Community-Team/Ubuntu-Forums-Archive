---
title: "USB Mouse - how to restart after dis/reconnecting"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by FokkerCharlie on 2008-10-25
Hi All

I have a laptop with a USB mouse (actually, Logiteck Trackman optical wireless, if it makes a difference!), that works OK with Hardy.  However, if I disconnect the device (eg when moving my lappy around), and then re-connect it, the only way that I can get my mouse to work again is to re-start X.

Am I missing something?  Is it possible to re-start the mouse?

Cheers
Charlie

---

### Post by Hexagoon on 2008-10-25
What ubuntu version are you running, and do you have all upgrades? It _should_ work :)

---

### Post by FokkerCharlie on 2008-10-25
Hi

I have 8.04.1, all updates are installed (though no -proposed or -backports) at the moment.

Here's a bit of xorg.conf, don't know if it makes a difference!
```

Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"evdev"
	Option		"Device"	"/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
	Option 		"Device" 	"/dev/input/event2"
	Option		"ZAxisMapping"		"4 5 9 10"
	Option 		"ButtonMapping" 	"1 2 3 6 7 4 5"
EndSection
```

VMT in advance.
Charlie

---

### Post by FokkerCharlie on 2008-10-29
Bump.

Nobody else able to help?

---

