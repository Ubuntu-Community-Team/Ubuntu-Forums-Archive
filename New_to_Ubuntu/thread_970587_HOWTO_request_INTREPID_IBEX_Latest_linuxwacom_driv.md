---
title: "HOWTO request INTREPID IBEX Latest linuxwacom driver"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Arthur Millar on 2008-11-04
please please please

---

### Post by punong_bisyonaryo on 2008-11-04
I'm sure there are a lot of people who have Wacom tablets running on Intrepid, but you probably need to provide more info. Like, what model do you have? Is it working at all or are there just some issues, etc.

I'm sure a lot more people could help you if they know what exactly you need help with.

---

### Post by Peter09 on 2008-11-04
Hi,
I have a wacom tablet as well, normally the wacom driver is installed by default. I notice that in Intrepid it has not been. I have not looked at this any further as yet.

---

### Post by LowSky on 2008-11-04
a simple googe search lead me here

[http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)

---

### Post by Arthur Millar on 2008-11-05
> **LowSky said:**
> a simple googe search lead me here

[http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)

this guide is not that easy to follow 
i got up to detecting the devices
I am apparently on th HID driver based on the line of code 

```
more /proc/bus/input/devices
```

I: Bus=0003 Vendor=172f Product=0500 Version=0110
N: Name="WALTOP International Corp. Media Tablet"
P: Phys=usb-0000:00:13.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb1/1-2/1-2:1.0/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2 
B: EV=10001f
B: KEY=c03 1f0001 0 0 e08effdf01cfffff fffffffffffffffe
B: REL=143
B: ABS=1fffff0001000003
B: MSC=10

and 

```
tail -f /var/log/messages
```

Nov  5 11:36:59 art-pc kernel: [ 1729.244031] usb 1-2: new full speed USB device using ohci_hcd and address 6
Nov  5 11:36:59 art-pc kernel: [ 1729.411065] usb 1-2: configuration #1 chosen from 1 choice
Nov  5 11:36:59 art-pc kernel: [ 1729.429052] input: WALTOP International Corp. Media Tablet as /devices/pci0000:00/0000:00:13.0/usb1/1-2/1-2:1.0/input/input7
Nov  5 11:36:59 art-pc kernel: [ 1729.485987] input,hidraw0: USB [COLOR="Red"]HID v1.10 Mouse[/COLOR] [WALTOP International Corp. Media Tablet] on usb-0000:00:13.0-2


so now i am trying to make the wacom driver detect my tablet by updating  
wacom.c
[http://linuxwacom.sourceforge.net/index.php/howto/newwacom](http://linuxwacom.sourceforge.net/index.php/howto/newwacom)
adding the following rules in "/etc/udev/rules.d/10-wacom.rules"
this file does not exist in intrepid(or on my machine  
instead there is /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules

i added this line as instructed 
KERNEL=="event[0-9]*", SYSFS{idVendor}=="172f", SYSFS{idProduct}=="0500", SYMLINK+="input/tablet-Waltop International Corp. Media Tablet"


this has had no effect in detecting my tablet with the wacom driver 


building wacom.o
[http://linuxwacom.sourceforge.net/index.php/howto/buildwacom](http://linuxwacom.sourceforge.net/index.php/howto/buildwacom)

missing
model versioning - DCONFIG_MODVERSIONS -DMODVERSIONS -include /lib/modules
xorg SDK - /usr/include/xorg
TCL - /user/incluse
tk - /user/incluse

---

### Post by Arthur Millar on 2008-11-05
linux wacom driver cant find 

Tcl
tk
xorg SDK 
ncurses
module versioning

---

