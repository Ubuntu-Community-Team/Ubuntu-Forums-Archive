---
title: "Touchpad not working anymore on Acer V3-572G"
date: 2014-10-06
forum: New to Ubuntu
---

### Post by Olex_S. on 2014-10-06
So I did install Ubuntu 14.04 once, and the touchpad worked perfectly well. I did a couple of stupid things and had some errors, and since I didn't have any backups, I just decided to clear the Ubuntu partitions and reinstall everything. Had no issues with that, except that my touchpad won't work anymore whereas I was pretty sure it worked before. I tried the function keys which disable the touchpad, but they have no effect (other function keys work just fine). It doesn't show up in the xinput list, and it's not in the device list I've added at the end of the post either. I have no idea what is going on here - can anyone help me out?

```
#I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=10000 c020000000000 0 0 700f02000003 3802078f870f401 febfffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input8
U: Uniq=
H: Handlers=rfkill kbd event6 
B: PROP=0
B: EV=13
B: KEY=1c0000 0 0 0 0 1600800000c00 300000 0 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer BMA150 accelerometer"
P: Phys=wmi/input1
S: Sysfs=/devices/virtual/input/input9
U: Uniq=
H: Handlers=event7 js0 
B: PROP=0
B: EV=9
B: ABS=7

I: Bus=0003 Vendor=04f2 Product=b452 Version=2969
N: Name="HD WebCam"
P: Phys=usb-0000:00:14.0-7/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/input/input10
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2e/LNXVIDEO:00/input/input11
U: Uniq=
H: Handlers=kbd event9 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input12
U: Uniq=
H: Handlers=kbd event10 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input15
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input14
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input13
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input16
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0003 Vendor=1a81 Product=1701 Version=0111
N: Name="G-Tech Wireless Dongle"
P: Phys=usb-0000:00:14.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.0/input/input19
U: Uniq=
H: Handlers=kbd mouse0 event5 
B: PROP=0
B: EV=10001f
B: KEY=4837fff072ff32d bf54444600000000 1f0001 20c100b17c000 267bfad941dfed 9e168000004400 10000002
B: REL=1c3
B: ABS=100000000
B: MSC=10

```

---

### Post by varunendra on 2014-10-07
Welcome to the forums Olex_S.!

Does it show up in syslog? -
```
grep -i touchpad /var/log/syslog
```

And have you double-checked the BIOS to make sure it is enabled from there? If it is not a UEFI based installation, you may try resetting the BIOS as well.

---

### Post by Olex_S. on 2014-10-15
Strangely enough, it just started working after a while without me doing anything - no idea why. Thanks for trying to help, though!

---

