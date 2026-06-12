---
title: "How to make all mouse buttons work with a Logitech G9 Laser Mouse"
date: 2007-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by dlpfmVfH on 2007-12-28
_This is my first how to for the Logitech G9 Laser Mouse:_

1. First create a new udev rule because the mouse creates two device events, one mouse and one keyboard.

```
sudo gedit /etc/udev/rules.d/010_local.rules
```with this line in it:
```
KERNEL=="event[0-9]*", SYSFS{../name}==**"Logitech G9 Laser Mouse"**, SYSFS{../phys}==**"usb-0000:00:0b.0-4/input0"** NAME="input/event9"
```where the **bold** is change it accordingly with your:
cat /proc/bus/input/devices output


Mine is:
```
I: Bus=0003 Vendor=046d Product=c048 Version=0111
N: Name=**"Logitech G9 Laser Mouse"**
P: Phys=**usb-0000:00:0b.0-4/input0**
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input7
U: Uniq=E25A53DB020029
H: Handlers=mouse2 event7 
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=046d Product=c048 Version=0111
N: Name="Logitech G9 Laser Mouse"
P: Phys=usb-0000:00:0b.0-4/input1
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.1/input/input8
U: Uniq=E25A53DB020029
H: Handlers=kbd event8 
B: EV=10001f
B: KEY=37fff00ac3027 bf00444400000000 1 10f848a37c007 ffe67bfad9415fff febeffdfffefffff fffffffffffffffe
B: REL=40
B: ABS=100000000
B: MSC=10
```This wil create a static rule /dev/input/event9 for your mouse, we will use this later in the xorg.conf

2. Second change your xorg.conf input device section to

```
Section "InputDevice"
    Identifier "Logitech Mouse"
    Driver "evdev" 
    Option "Protocol"     "auto"
    Option "Name"        "Logitech G9 Laser Mouse"
    Option "Phys"          "usb-0000:00:0b.0-4/input0"
    Option "Device"       "/dev/input/event9"
    Option "Emulate3Buttons" "no"
EndSection
```Change your server layout so it points to the right identifier: "Logitech Mouse"

This will make sure xorg finds your mouse and uses it.

3. Third create a .Xmodmap file so your tilt wheel can be used to navigate within Firefox.

```
gedit ~/.Xmodmap
```insert this line:

```
pointer = 1 2 3 4 5 **7 6** 8 9 10 11 12 13 14 15 16 17 18 19 20
```See the change in **bold**. You must swap button 6 and 7 otherwise the tilt wheel works the other way round.

If you restart your Gnome Environment, you will have a fully working G9 Laser Mouse. :)

[COLOR=Red]ps. I haven't figured out what the keyboard event does, if anybody knows, I can change the how to.[/COLOR]

---

### Post by Tekno_Cowboy on 2008-01-07
There is a utility called btnx that works great on logitech mice, It provides great detection and easy configuration of extra mouse buttons.

---

### Post by desperado666 on 2008-01-07
btnx ?

---

### Post by Tekno_Cowboy on 2008-01-07
**B**u**t**to**n** E**x**tension. Google it.

---

### Post by dlpfmVfH on 2008-01-08
I looked at btnx from [http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/)

installing it is ok, but couldn't get it to recognize the G9 mouse. 

So no joy there, I'm trying to contact the author of the program...

---

