---
title: "[SOLVED] /dev/input/eventX"
date: 2008-01-13
forum: Programming Talk
---

### Post by quandary on 2008-01-13
Hi!

I'm reading & writing device input directly from/to   /dev/input/eventX.

I got it working with the keyboard, and the USB mouse.

However, it seems I'm not able to read/write events from/to the Touchpad, because I don't find the event file of Touchpad...
(BTW: the touchpad works fine so far)

Can anybody tell me where the touchpad event is, or how to change it?
I've tried all of these (especially mouse1 and event8 ):
```

root@googlebot:/dev/input# dir
by-path  event1  event3  event5  event7  mice    mouse1
event0   event2  event4  event6  event8  mouse0

```
as well as /dev/psaux


Below the output of /proc/bus/input/devices and of /proc/bus/input/handlers

Output for /proc/bus/input/handlers:
```

root@googlebot:/proc/bus/input# cat handlers
N: Number=0 Name=kbd
N: Number=1 Name=mousedev Minor=32
N: Number=2 Name=evdev Minor=64
N: Number=3 Name=joydev Minor=0
root@googlebot:/proc/bus/input# clear

```

Output for /proc/bus/input/devices:
```

root@googlebot:/proc/bus/input# cat devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=100f 2002000 380307a f800d001 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0007 Version=a5b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

root@googlebot:/proc/bus/input# dir
devices  handlers
root@googlebot:/proc/bus/input# cat devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=100f 2002000 380307a f800d001 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0007 Version=a5b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

```

---

### Post by slavik on 2008-01-13
seems like event8 is the touchpad

```
I: Bus=0011 Vendor=0002 Product=0007 Version=a5b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003
```

---

### Post by quandary on 2008-01-13
That's what i thought, too.
But i already said there is no reaction on event8...

And i've tested all events just to be sure. But nothing happens...

Hmm, maybe it is a synaptics problem with the driver?

---

### Post by quandary on 2008-01-13
bump.

---

### Post by quandary on 2008-01-13
Wow, it took hours, but finally i am the quickest:

[http://linux.die.net/man/5/synaptics](http://linux.die.net/man/5/synaptics)
says that:
```

Protocol (String)
    auto-dev 	automatic, default
    psaux 	raw
    event 	linux 2.6 kernel events
    psm 	FreeBSD psm driver

```

which i had to change in the Xorg configuration file, and now it works....

---

### Post by diter on 2009-05-12
Sorry, what do you mean ?  Section "InputDevice"     ..     Option      "Protocol"      "auto-dev"      You change this option to what ?

---

