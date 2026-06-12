---
title: "LCD Brightness"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-05-13
I installed Lubuntu 12.04 on an old comp and its brightness keyboard control was working a lil erratic (some times worked some times didnt work) some times it would start with brightness 100 % some times very low.
But after i updated the system today the keyboard controls have stopped working.

I used the following cmd but got the result as :
xbacklight -set 100
No outputs have backlight property

for 
sudo modprobe video
i got no responce

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=fdf9f8e9-e349-4eb5-8f56-339a1e49e7b6 ro quiet splash vt.handoff=7

lspci -vnn | grep -A10 VGA
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780M/RS780MN [Mobility Radeon HD 3200 Graphics] [1002:9612] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device [103c:30e4]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 40000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=256]
	Memory at 54300000 (32-bit, non-prefetchable) [size=64K]
	Memory at 54200000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: fglrx_pci

i am a lil confused plz help !

---

### Post by llamabr on 2012-05-13
Maybe ddcontrol or gddcontrol?  From your question, it's not quite clear what you want to do. Just control the brightness?

```
brock@vader:~$ apt-cache search lcd brightness
armada-backlight - adjust backlight of Compaq Armada laptops (E300, M500, M700)
fnfxd - ACPI and hotkey daemon for Toshiba laptops
spicctrl - Sony Vaio controller program to set LCD backlight brightness
tpb - program to use the IBM ThinkPad(tm) special keys
xfce4-power-manager - power manager for Xfce desktop
brock@vader:~$ apt-cache search laptop brightness
acpi-support - scripts for handling many ACPI events
armada-backlight - adjust backlight of Compaq Armada laptops (E300, M500, M700)
eeepc-acpi-scripts - Scripts to support suspend and hotkeys on the Asus Eee PC laptop
fnfxd - ACPI and hotkey daemon for Toshiba laptops
guidance-power-manager - A frontend to HAL's power features for KDE
kde-guidance-powermanager - A frontend to HAL's power features for KDE (dummy package)
spicctrl - Sony Vaio controller program to set LCD backlight brightness
xfce4-power-manager-plugins - power manager plugins for Xfce panel
xfce4-power-manager - power manager for Xfce desktop
brock@vader:~$ apt-cache search screen brightness
acpi-support - scripts for handling many ACPI events
ddccontrol - a program to control monitor parameters
gddccontrol - a program to control monitor parameters
guidance-power-manager - A frontend to HAL's power features for KDE
kde-guidance-powermanager - A frontend to HAL's power features for KDE (dummy package)
olpc-kbdshim-common - OLPC XO keyboard support daemon (common files)
olpc-kbdshim-hal - OLPC XO keyboard support daemon (hal version)
olpc-kbdshim - OLPC XO keyboard support daemon
qiv - A quick image viewer for X
totem - A simple media player for the GNOME desktop based on GStreamer
tpb - program to use the IBM ThinkPad(tm) special keys
brock@vader:~$ 

```

---

### Post by 3dmatrix on 2012-05-13
> **llamabr said:**
> Maybe ddcontrol or gddcontrol?  From your question, it's not quite clear what you want to do. Just control the brightness?


Yes i would like to increase or decrease brightness as needed and wish the brighness does not changes on its own !

---

### Post by anaconda on 2012-05-13
You should be able to control the brightness directly:

first get the VGA device id, by (typing in terminal)
lspci
```
Part of the output I get on my machine:
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller

```

from the above I see that my VGA device id is: 00:02.0  (Yours may be different)
And Now I can control my displays brightness with command:
sudo setpci -s 00:02.0 f4.b=FF

THe last 2 letters are the brightness in hex. eg. 00 is the dimmest (no backlight) and FF is the brightest. You have 255 different brightness settings.

PS. dont try the 00 setting. With it your display will become completely black.... Good values are for example 5F, CF, FF etc.. changing the first number should be enough....


[http://www.permadi.com/tutorial/numDecToHex/](http://www.permadi.com/tutorial/numDecToHex/)

---

### Post by 3dmatrix on 2012-05-13
Well, i find it very strange ! but some times the brightness control works from the keyboard function keys and on other occations it does not :)
You can check the attached pic.
What might be happening ?

---

### Post by 3dmatrix on 2012-05-13
The following code generated no responce :

sudo setpci -s 01:05.0 f4.b=FF

where my VGA device is :

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780M/RS780MN [Mobility Radeon HD 3200 Graphics]

Some how it works a few times (as shown in the pic in my previous post) but again most other times it does not works.

Brightness can be controlled at the grub menu stage but when lubuntu boots the brightness gets reset. The screen is too dull and dark to read. Plz advise.

---

