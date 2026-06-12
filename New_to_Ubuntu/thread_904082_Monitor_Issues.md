---
title: "Monitor Issues"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by zetagirl on 2008-08-28
Could someone help me please....Im using the latest version of ubuntu..I have a hp pavillion dv4000 my monitor is broken so im using an external monitor from dell...It was working until I was trying to disable my synpatic touch pad and then it went back to this small resolution........my only options are 800*600 and 640*480 and I know my monitor will take a bigger resolution...Here is my /etc/X11/xorg.conf 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	...
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


Here is my lpsci information 

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by jmate24 on 2008-08-28
it looks like you have onboard video, and it looks like a laptop, am i correct?

---

### Post by nicedude on 2008-08-28
Do you know what you did that caused it to stop working? What resolution was it working with before it started acting up? From your xorg I see 1024x768 is in there but I am guessing that you can't use that resolution now but before you were using that , is that correct?

Nice to see you are from Indy I live in Louisville Ky so it is a small world :-)

---

### Post by Crafty Kisses on 2008-08-28
You can technically reconfigure X and start over, on the X.org log as stated above it does say 1024x768, so try changing the resolution with the option "Screen Resolution" see if anything higher than 800x600 comes up.

---

### Post by nicedude on 2008-08-28
I see in synaptic that there is a program to manage the xorg file for graphics and I am not sure if it is installed by default or not but if not then you can install it with the command below. If it is installed then the install command wont do anything bad so just run it then the second command to start the program.

sudo apt-get install displayconfig-gtk

then this will start it up

sudo displayconfig-gtk


Then see if you can change resolution to 1024x768 or better :-)

---

### Post by timmo710 on 2008-08-28
i have a similer issue with a HP nc8000 laptop. and i found the issue to be when the lid is shut and the laptop boots, ubuntu couldnt recignise the external monitor. as when the laptop is booted up with the lid closed windows sees the external display as the only display it could be a similar case with you 

i am setting up an ubuntu laptop to run in the car with an external display and power button. but have come to a stand still. originally i thought it was the display drivers (had fun getting ati 9600 mobility working) but im now starting to wonder if this is a bug in ubuntu 8.04

all i was going to do to fix the issue was unplug the back light and remove the lid switch. fun workaround i know

---

### Post by zetagirl on 2008-08-28
> **jmate24 said:**
> it looks like you have onboard video, and it looks like a laptop, am i correct?  Yep its a laptop

---

### Post by nicedude on 2008-08-28
Zeta try installing the display config thing I suggested and run it and see if you can select a better resolution, it just may work and if it does it will modify your xorg file for you.

---

### Post by jmate24 on 2008-08-29
it also depends on how old it is and the manufacturer buying the parts in bulk to make the series of laptops with the sale going to the lowest bidder,

---

### Post by jmate24 on 2008-08-29
but one more thing is that ubuntu has minimal support for intel based video devices.

---

### Post by zetagirl on 2008-08-30
> **nicedude said:**
> Zeta try installing the display config thing I suggested and run it and see if you can select a better resolution, it just may work and if it does it will modify your xorg file for you.

I did and when I restarted it said that my video was in an incorrect format and I could not see the screen....So I got scared and I just reinstalled Ubuntu....

---

