---
title: "Touchpad not working"
date: 2015-02-14
forum: New to Ubuntu
---

### Post by ragheed2 on 2015-02-14
New guy here, touchpad stopped working 3 days ago, it works perfectly of windows 8.1 installed as double boot with linux ubuntu 14.04. xinput list:
 Virtual core pointer                       id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                  id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=12   [slave  pointer  (2
cat /proc/bus/input/devices:
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input10
U: Uniq=
H: Handlers=mouse1 event5 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003
my log file :
[    21.954] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    21.954] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.954] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    21.954] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    21.954] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.954] (II) Using input driver 'evdev' for 'SynPS/2 Synaptics TouchPad'
[    21.954] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.954] (**) evdev: SynPS/2 Synaptics TouchPad: Device: "/dev/input/event4"
[    21.954] (II) evdev: SynPS/2 Synaptics TouchPad: Using mtdev for this device
[    21.954] (--) evdev: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    21.954] (--) evdev: SynPS/2 Synaptics TouchPad: Found 1 mouse buttons
[    21.954] (--) evdev: SynPS/2 Synaptics TouchPad: Found absolute axes
[    21.954] (--) evdev: SynPS/2 Synaptics TouchPad: Found absolute multitouch axes
[    21.954] (--) evdev: SynPS/2 Synaptics TouchPad: Found x and y absolute axes
[    21.954] (--) evdev: SynPS/2 Synaptics TouchPad: Found absolute touchpad.
[    21.954] (II) evdev: SynPS/2 Synaptics TouchPad: Configuring as touchpad
[    21.954] (**) evdev: SynPS/2 Synaptics TouchPad: YAxisMapping: buttons 4 and 5
[    21.954] (**) evdev: SynPS/2 Synaptics TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.955] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[    21.955] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    21.955] (II) evdev: SynPS/2 Synaptics TouchPad: initialized for absolute axes.
[    21.955] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    21.955] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    21.955] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    21.955] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    21.955] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
tried the thing with "sudo modprobe -r psmouse" and it didn't work either, also I re-installed the driver for synpatics and it did nothing. I don't know if it can help, but I tried to replace ubuntu with mint 17.1 to solve the problem and even in mint it remained so I reinstalled ubuntu. I hope you help me, I removed my windows yesterday accidentally and now i'm stuck with ubuntu.
Guys I really need help here.

---

### Post by mörgæs on 2015-02-15
Hi, welcome to the fora.
How does it work in a live boot of 14.10 and 15.04 (development)?

---

