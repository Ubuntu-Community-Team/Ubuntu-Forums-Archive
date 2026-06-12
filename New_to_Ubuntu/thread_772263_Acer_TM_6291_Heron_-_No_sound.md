---
title: "Acer TM 6291 Heron - No sound"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mormor on 2008-04-28
Acer Travelmate 6291, Intel soundcard. remember I had a lot of problems with it in 7.10. Worked after heron install. Funny thing is, my soundcard worked prior to me getting third party codecs for my music and video.

Now suddenly, its gone. No sound.

Any ideas?

-----

Solved:

> **Joshua Netterfield said:**
> The best way I have found to fix this problem is just to run alsaconf. Ubuntu doesn't include it, because it has a way cooler system which always works except for when it doesn't. Nice. We will need to install it ourselves.

1. Open up a terminal. (Applications->Accessories->Terminal)
2. Type "gedit ./alsaconf.sh" (without the quotes)
3. Go to [http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf), select everything (ctrl+a) and copy it (ctrl+c)
4. Go to the gedit window. Paste what you copied (ctrl+v)
5. Save it.
6. Go back to the terminal and run:
```
chmod +x ./alsaconf.sh
sudo ./alsaconf.sh
```
7. Follow the instructions
8. It should work. But it still might not...


"Chmod +x" makes the program runnable, and "sudo ./alsaconf.sh" runs it.
The script detects the sound cards that you have and gets them ready for use.

Good luck!

Edit: Oh ya. Source is [http://www.ubuntux.org/sound-card-not-detected](http://www.ubuntux.org/sound-card-not-detected) . You should thank them if it works (;



...

That one did the trick

---

### Post by martrn on 2008-04-28
Open a terminal and type :-

aplay -l
lspci -v

What do you get ?

Here is the official sound trouble-shooting guide...
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

The official sound trouble-shhoting guide does work, as I have been without sound and followed it through myself.

---

### Post by mormor on 2008-04-28
THnx, Ill start looking at the guide. Oh, and this is what I got. Doesnt tell me to much:P
---

marius@tobor:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

marius@tobor:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0300000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0400000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, fast devsel, latency 0
	Memory at d0380000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at d0440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: 88000000-880fffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: 88100000-881fffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at d0644000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
	Memory behind bridge: d0200000-d02fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 220
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at d0644400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at 88000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at 88100000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

0a:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 168, IRQ 19
	Memory at d0204000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
	Memory window 0: 8c000000-8ffff000 (prefetchable)
	Memory window 1: 90000000-93fff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001

0a:02.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: medium devsel, IRQ 255
	Memory at d0205a00 (32-bit, non-prefetchable) [disabled] [size=128]
	Capabilities: <access denied>

0a:02.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at d0205800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0a:02.2 FLASH memory: ENE Technology Inc Unknown device 0720
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: medium devsel, IRQ 255
	Memory at d0205a80 (32-bit, non-prefetchable) [disabled] [size=128]
	Capabilities: <access denied>

0a:02.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at d0205900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0a:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 012a
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at d0205000 (32-bit, non-prefetchable) [size=2K]
	Memory at d0200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by martrn on 2008-04-28
choose you driver from :-

intel8x0
intel8x0m
hda-intel

Or from the driver located at [http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

then one of :-
type at a terminal (ONE OF) > 
sudo modprobe snd-intel8x0
sudo modprobe snd-intel8x0m
sudo modprobe snd-hda-intel

which one it is likely to be.
**possiably intel8x0 , not sure**,
or whatever it might be.
see [http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

If we get sound at this point this is good.

If not we continue.............................
-----------------------------------------------
**Getting the ALSA drivers from a *fresh* kernel**

Type in a terminal :-

> sudo apt-get install build-essential linux-headers-$(uname -r) 
sudo apt-get install module-assistant
sudo apt-get install alsa-source
sudo module-assistant a-i alsa-source

Then selelect your driver and what to do, eg get asla-sorce, 
choose driver **possiably intel8x0 , not sure**, compile etc.............

You sound module should work by this point.......

---

### Post by mormor on 2008-04-28
haha. I have tryed so many things now, I must have destroyed it:P

---

### Post by mormor on 2008-04-28
Solved : ) and thx : )

> **Joshua Netterfield said:**
> The best way I have found to fix this problem is just to run alsaconf. Ubuntu doesn't include it, because it has a way cooler system which always works except for when it doesn't. Nice. We will need to install it ourselves.

1. Open up a terminal. (Applications->Accessories->Terminal)
2. Type "gedit ./alsaconf.sh" (without the quotes)
3. Go to [http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf), select everything (ctrl+a) and copy it (ctrl+c)
4. Go to the gedit window. Paste what you copied (ctrl+v)
5. Save it.
6. Go back to the terminal and run:
```
chmod +x ./alsaconf.sh
sudo ./alsaconf.sh
```
7. Follow the instructions
8. It should work. But it still might not...


"Chmod +x" makes the program runnable, and "sudo ./alsaconf.sh" runs it.
The script detects the sound cards that you have and gets them ready for use.

Good luck!

Edit: Oh ya. Source is [http://www.ubuntux.org/sound-card-not-detected](http://www.ubuntux.org/sound-card-not-detected) . You should thank them if it works (;

---

