---
title: "Problem with USB Mouse"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Aceor on 2008-10-20
I'm having trouble getting a USB mouse to work on Ubuntu.  Is this the best forum for help, or should I try another?  Thanks.

---

### Post by LowSky on 2008-10-20
what kind of problems? USB mice should "just work"

What model, what issue?

---

### Post by Aceor on 2008-10-20
First off, I'm new to Ubuntu, and Linux in general.  But not new to computers.  So feel free to proceed quickly with direction.

I installed the latest version of Ubuntu on an older machine.  Specs:
AMD XP2000 on an ECS K7S5A Pro MB
1 GB Ram
Geforce4 Vid card
etc etc.

When I first installed the OS, the mouse pointer was on screen, but I had no mouse control.  I read through the forums and found out how to connect/configure a serial mouse, and successfully did that.  So I am running on an old serial mouse right now.  But I would like to use my wireless Logitech USB mouse.  (btw, the mouse works fine in windows xp).

Here is the output of lsusb:
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Here is the output from sudo lspci:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)

Here is the relevant line from lsmod:
usbcore               146028  2 ohci_hcd

Here is the section from my xorg.conf file.
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/ttyS0"
	Option		"Protocol"	"Microsoft"
EndSection

Clearly, the USB mouse won't work with the serial device setting.  But I tried with a generic '/dev/input/mice' setting, and both mice won't work.

Thanks in advance for the help!

---

### Post by Dr Small on 2008-10-20
I have occasionally had problems with different distros regarding mice. Some liked USB, others would only work with PS/2. This simplest solution is to carry a PS/2 converter (one should come with your USB mouse) to support legacy systems. I just keep mine on all the time and I never have any problems.

Dr Small

---

### Post by LowSky on 2008-10-20
does the Wireless USB mouse work on the LiveCD?

if you havn't tried reboot into recovery mode and try to resetup Xorg

---

### Post by Aceor on 2008-10-20
Tried the live cd.  No luck

Tried recovery/reset xorg.  No luck.  (in fact, both of these left me mouseless, just like the original install)

Tried the USB to Mouse port adapter.  Couldn't get this to work, but, I may not have the right setup in xorg (i even tried it with the reset/live cd mentioned above, and no luck).

Keep it coming please.  I appreciate the help so far.

---

### Post by Dr Small on 2008-10-20
> **Aceor said:**
> Tried the USB to Mouse port adapter.  Couldn't get this to work, but, I may not have the right setup in xorg (i even tried it with the reset/live cd mentioned above, and no luck).

Keep it coming please.  I appreciate the help so far.

Did you try reconfiguring Xorg with the PS/2 converter on the USB mouse?

---

### Post by Aceor on 2008-10-21
The only change I made was to go back to the generic mouse device setting.  (I think it is /dev/input/mice or similar).   Is this corrrect?

I also tested a USB drive, and it did not work in Ubuntu.  So it is definitely Ubuntu's ability to read the USB ports.

---

### Post by Aceor on 2008-10-25
Hey Dr Small ... how do I configure xorg to recognize the usb mouse with a ps2 converter?  Thank you.

---

### Post by Dr Small on 2008-10-25
Here is my section on my PS/2 mouse. I am know Xorg master:
```
Section "InputDevice"
	Identifier  "PS/2 Mouse"
	Driver      "mouse"
	Option      "Protocol" "auto"
	Option          "ZAxisMapping"          "4 5"
	Option      "Device" "/dev/psaux"
	Option      "Emulate3Buttons" "true"
	Option      "Emulate3Timeout" "70"
	Option	    "SendCoreEvents"  "true"
EndSection
```

You can always try backing up your Xorg and then reconfiguring xserver-xorg and see if that will help:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```

If it doesn't work, you can always restore the backup to your original settings.

---

### Post by Feanor22 on 2008-10-26
I bought a microsoft wireless mouse but it doesnt install the cd that comes with it. I tried the synaptics but gives a error.
help me please!

---

