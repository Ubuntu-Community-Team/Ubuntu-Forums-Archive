---
title: "Howto get everything to work on Acer TravelMate C300"
date: 2006-08-08
forum: Outdated Tutorials &amp; Tips
---

### Post by OpsVentus on 2006-08-08
To anyone it may help and for me when I need to reinstall.
The steps to take to make an Acer TravelMate C300(a lot may work with other types) fully functional.

Note:
This howto doesn't cover how to do the actions, just what to do. (yes, it's not an howto, but how to call it then?)

To install dual boot:
The recover cd's want to put Windows on the first partition.
So first boot from live-cd divide the disk so that Windows is on the first partition, then install Windows, then Ubuntu.
The first "PQService" partition can be removed, it's a waste of space.

Step 1:
Installing neccesary programs. (please replay if missing or obsolete)
```

xinput
wacom-kernel-source
wacom-tools
xserver-xorg-input-wacom
obexserver
gnome-bluetooth
hotkeys
setserial

Not in Ubuntu repository's:
acerhk -> http://www2.informatik.hu-berlin.de/~tauber/acerhk/

```

Step 2:
Adjusting configuration file's.
**/etc/X11/xorg.conf:**
Add/change this part: (note:the sequence is important!)
```

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"
	Option		"BottomX"	"28800"
	Option		"BottomY"	"21760"
	Option		"Mode"		"absolute"
	Option		"TPCButton"	"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"
	Option		"BottomX"	"28800"
	Option		"BottomY"	"21760"
	Option		"Mode"		"absolute"
	Option		"TPCButton"	"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"
	Option		"BottomX"	"28800"
	Option		"BottomY"	"21760"
	Option		"Mode"		"absolute"
	Option		"TPCButton"	"on"
EndSection

```
Add/change this part:(again sequence is important!)
```

	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"

```

**/etc/serial.conf**
Create the file or append:
```

#Stylus pen
/dev/ttyS0 port 0x06f8 irq 6 uart 16550A

```

**/etc/X11/Xsession.d/95Acerboot**
Create file:
```

hotkeys
xinput set-button-map stylus 1 3 2

```

**/etc/hotkeys.conf**
Still working on this one.

[b]/usr/share/hotkeys/c300.def[/d]
Still working on this one.

**/etc/modules**
Append:
```

acerhk

```

Step 3:
Optional scripts.
**/usr/sbin/bluetoothon**
Enables bluetooth.
```

echo "on" > /proc/driver/acerhk/blueled

```

**/usr/sbin/bluetoothoff**
Disables bluetooth.
```

echo "off" > /proc/driver/acerhk/blueled

```

**/usr/sbin/wirelesson**
Enables wireless network.
```

echo "on" > /proc/driver/acerhk/wirelessled

```

**/usr/sbin/wirelessoff**
Disables wireless network.
```

echo "off" > /proc/driver/acerhk/wirelessled

```

**Desktop launcher for sending file's over bluetooth**
Create new launcher on desktop the command is "gnome-obex-send".

Step 3:
Using your system.
After configuring your system to this.
Everything should work.
-To enable bluetooth run "bluetoothon"
-To disable bluetooth run "bluetoothoff"
-To enable wireless run "wirelesson"
-To disable wireless run "wirelessoff"
-To send a file over bluetooth, drop file on Desktop launcher, select device.
-To receive a file over bluetooth, start "gnome-obex-server". (this can be run as a deamon)
-To turn on the light in the mailbutton #echo "on" >> /proc/driver/acerhk/led
(no I'm not going to tell you how to turn it **off**)

If there's anything missing please replay or im me.

Have fun,
Bart.


Resources:
[http://www.duskzone.it/works/linux/c300howto/debianLinux_on_acer_travelmateC300.php](http://www.duskzone.it/works/linux/c300howto/debianLinux_on_acer_travelmateC300.php)
[http://22eleven.com/archives/2004/12/12/linux-on-the-acer-travelmate-c300-tablet](http://22eleven.com/archives/2004/12/12/linux-on-the-acer-travelmate-c300-tablet)
[http://linuxwacom.sourceforge.net/index.php/howto/toc](http://linuxwacom.sourceforge.net/index.php/howto/toc)
[http://www2.informatik.hu-berlin.de/~tauber/acerhk/](http://www2.informatik.hu-berlin.de/~tauber/acerhk/)

Status:
-Not all hotkeys working, work in progress.
-Modem unknown, not needed by me.
-Rotating screen, not working, is possible but to my knowledge not will gnome is running.
-Firewire unkown, not needed by me.
-Card-reader semi-working, doesn't see partitions on second insert.
-Tv-out semi-working, small screen, no known successtory's + Intel doesn't support it on Linux
-Rest working

---

### Post by hypnoticstate on 2006-08-08
Slightly off topic.

I've got an acer aspire wmli 1670 running kubuntu, I've got most things working except stuff I don't use anyway, was just wondering if you know of a way to get the sensors working ? ie temperatures, i've tried everything, have you got any ideas ?

---

### Post by OpsVentus on 2006-08-09
Havent got that working. Figured it wasn't worth the efford and let the laptop do the tuning itself.
But maybe a reading on the temperatures would be neet.
Going after the hotkeys first though.
A notch in the right direction "lm-sensors" it should be possible.

Cheers,
Bart.

---

### Post by mikebenny71 on 2009-03-14
I wrote a miniguide to configure Ubuntu on my Acer Travelmate C300. It's in Italian language but I also put my xorg.conf file as reference! 
I hope it could help all the people that has the same tablet pc! :popcorn:


[http://grappalug.homelinux.net/index.php?mod=01_Linux%20Doc/Ubuntu_su_Travelmate_C300_Tablet_PC](http://grappalug.homelinux.net/index.php?mod=01_Linux%20Doc/Ubuntu_su_Travelmate_C300_Tablet_PC)


Best Regards,
Michele ;)

---

