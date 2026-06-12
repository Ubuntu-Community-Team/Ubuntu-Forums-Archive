---
title: "wireless keyboard not recognised"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by wildmanne39 on 2011-10-08
Hi, does anyone know how to get 11.10 to use my wireless logitech keyboard?

It is a new keyboard and it works great in 11.04, but when I run:
```
lsusb
```
it is not seen but my wireless mouse of the same brand is.
Thank you

---

### Post by crdlb on 2011-10-08
What model is it? The mouse and keyboard have separate USB dongles, right?

---

### Post by wildmanne39 on 2011-10-08
Hi, it is a logitech k350.
Thank you

---

### Post by crdlb on 2011-10-08
So, are you using a separate USB receiver for each device, or have you paired both of them to one receiver? You said it works in 11.04, but have you tested it on another OS since it stopped working? I would have guessed that they had somehow become unpaired, but the receiver should still show up in lsusb.

---

### Post by effenberg0x0 on 2011-10-08
I have a Logitech marble trackball that also uses a unified receptor. It works perfectly, out of the box, with Oneiric. So, looking at lsusb I should see the unified receptor there. 
If your wireless mouse is working, lsusb is also showing you the unified receiver.
```

[02:50 ][al:AL-DESK:~]
$ uname -a
Linux AL-DESK 3.0.0-12-generic #19-Ubuntu SMP Fri Sep 23 21:23:39 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

[02:51 ][al:AL-DESK:~]
$ sudo lsusb
[sudo] password for al: 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
**Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver**
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
```However, here's the trick: I know this unified receptors create two event handlers, one for keyboard and other for mouse. Look at my dmesg:
```
[02:56 ][al:AL-DESK:~]
$ dmesg | grep -i logitech
[    2.725396] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.0/input/input4
[    2.725448] generic-usb 0003:046D:C52B.0003: input,hidraw2: USB HID v1.11 **Keyboard** [Logitech USB Receiver] on usb-0000:00:13.0-5/input0
[    2.730471] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.1/input/input5
[    2.730554] generic-usb 0003:046D:C52B.0004: input,hiddev0,hidraw3: USB HID v1.11 **Mouse** [Logitech USB Receiver] on usb-0000:00:13.0-5/input1
[    2.739315] generic-usb 0003:046D:C52B.0005: hiddev0,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-5/input2

```I can also see more detail about the two event handlers: event 4 and event5.
```

[02:56 ][al:AL-DESK:~]
$ cat /proc/bus/input/devices
I: Bus=0003 Vendor=046d Product=c52b Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:13.0-5/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.0/input/input4
U: Uniq=
**H: Handlers=sysrq kbd event4 **
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c52b Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:13.0-5/input1
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.1/input/input5
U: Uniq=
**H: Handlers=kbd mouse0 event5 **
B: PROP=0
B: EV=1f
B: KEY=837fff072ff32d bf54444600000000 ffff0001 20f948b17c000 6773fad941dfed 9ed68000004400 10000002
B: REL=1c3
B: ABS=100000000
B: MSC=10
 
```So if I cat this handlers, I will see some output when I move the mouse (on the right handler, of course). Lets see.
```
[02:57 ][al:AL-DESK:~]
$ sudo cat /dev/input/event4
^C
[02:57 ][al:AL-DESK:~]
$ sudo cat /dev/input/event5
&#65533;&#65533;b*    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;g*    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p*    &#65533;&#65533;GI    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;II    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;KI    &#65533;&#65533;&#65533;h    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h    &#65533;&#65533;&#65533;&#65533;    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;    &#65533;&#65533;#&#65533;    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;'&#65533;    &#65533;&#65533;I&#65533;    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;K&#65533;    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;P&#65533;    &#65533;&#65533;    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;    &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;    &#65533;&#65533;
```Good, so my mouse responds on event handler 5. Event handler 4 is for the keyboard (which I don't own - can't test). You probably can cat your handler for the keyboard and see something in console too.

From this point you can rely on any tutorial (xorg.conf (MatchDevicePath, etc), evdev, even devinput, etc) to make it work.

Good luck.

Regards,
Effenberg

**EDIT:** Don't know if I was clear enough (going to bed in a second, very tired, tough week). You labeled this thread "Keyboard not recognized". When you use a wireless set, the only thing that is (has to be) in fact recognized is the receiver. If the receiver is recognized and the system creates handlers, than you can use any input method you choose to work with this handlers. You'll treat it like any USB wired keyboard for example.

---

### Post by wildmanne39 on 2011-10-08
Hi crdlb, yes I have 2 receivers, the mouse I already had and the unified receiver only operated the keyboard so I have to use the mouse receiver for the mouse.

Yes the keyboard works when I boot 11.04.

I used the ID numbers and googled each one and none showed up as the unified receiver or the keyboard, there is only one for the mouse, but I will look into it more tomorrow, I am also tired tonight and it is late here.
Thank you both for your replies and suggestions.

---

