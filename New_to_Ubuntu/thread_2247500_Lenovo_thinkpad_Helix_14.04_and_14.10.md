---
title: "Lenovo thinkpad Helix 14.04 and 14.10"
date: 2014-10-08
forum: New to Ubuntu
---

### Post by blackholdmailer on 2014-10-08
Hi,
I have just bought a Lenovo Thinkpad Helix and it is still on windows 8.1 but want to install there some linux version, the one is ubuntu for it's support about hardware. So that I tried it with a livecd version (14.04 and 14.10 in 64bit). The finally tests were done with 14.10 (unity).

I could see that everything is working out the box (obvously could not try deattach of screen - usb ports on tablet are in the bottom).

- UEFI boot worked ok
- wifi worked ok
- audio works, up, down, mute audio, mute mic buttons works
- screen up and down volume buttons works
- screen lock button do nothing
- brightness buttons works
- enable/disable wifi button works
- suspend could not test
- deattach could not test
- virtual buttons of touchpad are working (all the regions of touchpad are left click unless right-top and right-bottom that are the right click)*
- trackpoint: scroll is not working (push middle button and get 360º scrolling with the red button)
- touchscreen is working (using finger and pen) but not tapping+scrolling
- touchpen: works ok, but on using touchpad, trackpoint, finger and more, it uncalibrates.


* to do scroll out of the box you should tap to touchpad with one finger and with the other do the scrolling

Now I paste more info.

I offer to do tests on this machine, always on livecd. User will don't allow not be able to do tapping scrolling... so... users...


Here more info:
root@ubuntu:/home/ubuntu# lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QS77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 96)
root@ubuntu:/home/ubuntu# lsusb
Bus 002 Device 004: ID 03eb:8406 Atmel Corp. 
Bus 002 Device 003: ID 04ca:7027 Lite-On Technology Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04ca:7028 Lite-On Technology Corp. 
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 003: ID 8087:0a04 Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 05e3:0612 Genesys Logic, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bdb:1936 Ericsson Business Mobile Networks BV 
Bus 003 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ubuntu:/home/ubuntu# dmesg |grep wacom
[  984.184510] usbcore: registered new interface driver wacom
root@ubuntu:/home/ubuntu# lsmod |grep wacom
wacom                  71280  0 
root@ubuntu:/home/ubuntu# ls /proc/bus/input/devices
/proc/bus/input/devices
root@ubuntu:/home/ubuntu# cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input4
U: Uniq=
H: Handlers=mouse0 event3 
B: PROP=15
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=synaptics-pt/serio0/input0
S: Sysfs=/devices/platform/i8042/serio1/serio2/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=03eb Product=8406 Version=0111
N: Name="Atmel Atmel maXTouch Digitizer"
P: Phys=usb-0000:00:1d.0-1.6/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/0003:03EB:8406.0002/input/input7
U: Uniq=
H: Handlers=mouse2 event6 
B: PROP=2
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=260800000000003

I: Bus=0019 Vendor=17aa Product=5054 Version=4101
N: Name="ThinkPad Extra Buttons"
P: Phys=thinkpad_acpi/input0
S: Sysfs=/devices/platform/thinkpad_acpi/input/input9
U: Uniq=
H: Handlers=rfkill kbd event7 
B: PROP=0
B: EV=33
B: KEY=18040000 0 10000000000000 0 1501b02102004 c000080021104000 10e000000000000 0
B: MSC=10
B: SW=a

I: Bus=0003 Vendor=04ca Product=7028 Version=0010
N: Name="Integrated Camera"
P: Phys=usb-0000:00:1a.0-1.6/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input10
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0003 Vendor=04ca Product=7027 Version=0037
N: Name="Integrated Rear Camera"
P: Phys=usb-0000:00:1d.0-1.3/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input11
U: Uniq=
H: Handlers=kbd event9 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input14
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input15
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=140
root@ubuntu:/home/ubuntu# xsetwacom --list devices
root@ubuntu:/home/ubuntu# dpkg -l |grep wacom
ii  libwacom-common                                      0.8-1                                      all          Wacom model feature query library (common files)
ii  libwacom2:amd64                                      0.8-1                                      amd64        Wacom model feature query library
ii  xserver-xorg-input-wacom                             1:0.25.0-0ubuntu1                          amd64        X.Org X server -- Wacom input driver

So if something more is needed, please, tell it to me.

Thanks you much

---

### Post by Sef on 2014-10-08
Moved to New to Ubuntu.

---

### Post by blackholdmailer on 2014-10-09
I autoreply a half solution:

[https://addons.mozilla.org/en-US/firefox/addon/grab-and-drag/](https://addons.mozilla.org/en-US/firefox/addon/grab-and-drag/)

Installing this addon with default config is possible to have the desired behaviour only on browser.

So, nice to could enable this function to operating system. Wishlist.

---

