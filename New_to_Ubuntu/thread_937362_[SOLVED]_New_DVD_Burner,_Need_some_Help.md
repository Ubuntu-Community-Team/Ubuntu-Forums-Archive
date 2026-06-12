---
title: "[SOLVED] New DVD Burner, Need some Help"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-10-03
Hey everyone.


I just bought an LG GE20 External DVD burner. I just took it out of the box and need some advice concerning the setup of said burner.

I have not plugged it in yet, decided it was best not to mess about with something that I have minimal experience with as it. 

So without further adue, I will ask, what should I do about this? Is there something critical to the operation of said burner I need to get? or should I just plug it in and expect it to work?


Thanks

V

---

### Post by indytim on 2008-10-03
I'd suggest plugging it in an re-booting.  Never heard of an external burner consuming anything organic ... :D.

Report back with any problems from that point forward.

Good Luck,

IndyTim

---

### Post by Vendettaseve on 2008-10-03
Ok plugged it in and restarted... It ate my cat... Lol jk


But really it did nothing. Ubuntu doesnt see it -_-


So should I install the CD it came with through Wine? or what.

---

### Post by fooman on 2008-10-03
load a cd or dvd (not a blank one) into it and see if it springs to life?

---

### Post by Vendettaseve on 2008-10-03
LOading a CD into it doesnt do anything either..... Is it safe/able to work with wine? the drivers and DVD burning programs that work wiht Lightscribe?

---

### Post by Vendettaseve on 2008-10-03
Ok so attempting to install anything from that CD with wine was a failure lol -_-

I really need some help here.

---

### Post by anjilslaire on 2008-10-03
We assume it has power, and is plugged into a working usb or firewire port?

---

### Post by Dr Small on 2008-10-03
Just connect power and a ribbon cable to it, reboot and the system should automatically work with it. There isn't anything special you need to do with it, besides open the bay and insert a CD, that I have delt with.

---

### Post by Vendettaseve on 2008-10-03
Yes it is plugged in.  Its an external Burner. plugged into both the power and the USB.

It still does not work however -_-

Any way I can check my USB ports to make sure there working? I know a few of them dont work and Im not sure if Ubuntu sees me second set of USB ports I installed back while I was on windows.

---

### Post by fooman on 2008-10-03
what do you get when you run:

```
lsusb
```

---

### Post by Vendettaseve on 2008-10-04
this.


vendettaseve@vendettaseve-Lair:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Vendettaseve on 2008-10-04
is that bad? Anyone?

it looks like it isnt reading my USB ports but IM not sure what it means really,.. thats just what it looks like to me.

---

### Post by Vendettaseve on 2008-10-04
Anyone?

---

### Post by kansasnoob on 2008-10-04
There are two packages in Synaptic Package Manager that may get you going:

1) pmount
Installing pmount should drag in hal unless it's already installed.

2) usbmount

Quote from synaptic:

> USBmount is intended as a lightweight solution which is independent of a desktop environment. Users which would like an icon to appear when an USB device is plugged in should use the pmount and hal packages
instead.

Oh, don't install both at the same time!

---

### Post by Vendettaseve on 2008-10-04
installed Pmount... Nothing happend.

---

### Post by bobpur on 2008-10-04
I dunno. Maybe, after eating the cat, it's decided to take a nap. :) :)

---

### Post by cariboo on 2008-10-04
What is the output of dmesg when you plug your external into your computer. I should look somethig like this:

```
 5439.184034] usb 1-6: new high speed USB device using ehci_hcd and address 6
[ 5439.319297] usb 1-6: configuration #1 chosen from 1 choice
[ 5439.404796] usbcore: registered new interface driver libusual
[ 5439.416607] Initializing USB Mass Storage driver...
[ 5439.417043] scsi6 : SCSI emulation for USB Mass Storage devices
[ 5439.417407] usb-storage: device found at 6
[ 5439.417414] usb-storage: waiting for device to settle before scanning
[ 5439.417422] usbcore: registered new interface driver usb-storage
[ 5439.417425] USB Mass Storage support registered.
[ 5444.416337] usb-storage: device scan complete
[ 5444.418766] scsi 6:0:0:0: Direct-Access     LEXAR    JD FIREFLY       1100 PQ: 0 ANSI: 0 CCS
```

This is from a thumb drive, but your ouput should be similar. Open a Applications-->Accessories-->Terminal and type:

```
dmesg
```

Jim

---

### Post by Vendettaseve on 2008-10-04
This is the part you asked for I think lol.


[   90.286066] usb 5-1: device descriptor read/64, error -71
[   90.501836] usb 5-1: device descriptor read/64, error -71
[   90.717605] usb 5-1: new high speed USB device using ehci_hcd and address 7
[   90.829484] usb 5-1: device descriptor read/64, error -71
[   91.045268] usb 5-1: device descriptor read/64, error -71
[   91.261028] usb 5-1: new high speed USB device using ehci_hcd and address 8
[   91.668595] usb 5-1: device not accepting address 8, error -71
[   91.784482] usb 5-1: new high speed USB device using ehci_hcd and address 9
[   92.192051] usb 5-1: device not accepting address 9, error -71
[   92.487616] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   92.487638] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   92.487672] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   46.697381] NET: Registered protocol family 17
[   99.584559] NET: Registered protocol family 10
[   99.585175] lo: Disabled Privacy Extensions
[  109.701640] eth0: no IPv6 routers present
vendettaseve@vendettaseve-Lair:~$ dmesg


Hope you can make some sence of this.

Thanks :D

---

### Post by geezerone on 2008-10-04
Try ```
sudo modprobe -r ehci_hcd
``` and see if it works. This removes the module ehci_hcd.

---

### Post by Vendettaseve on 2008-10-05
> **geezerone said:**
> Try ```
sudo modprobe -r ehci_hcd
``` and see if it works. This removes the module ehci_hcd.



Ding ding we have a winner. DVD burner jumped to life within seconds of me tossing that line of code into the terminal. 

Much thanks, :D


V

---

