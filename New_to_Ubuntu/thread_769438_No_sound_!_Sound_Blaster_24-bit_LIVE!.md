---
title: "No sound ! Sound Blaster 24-bit LIVE!"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Victoroth on 2008-04-26
Hi to everyone,
I installed ubuntu 8.04 just a hours ago and everything was ok , but there is no SOUND coming from my Sound Blaster 24-bit LIVE! soundcard ... I read that [http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106) but I can get it (I can't make it to work) , can someone help ?

---

### Post by Victoroth on 2008-04-26
Here are result of lspci -v

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
	Subsystem: Giga-byte Technology GA-7VAX Mainboard
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: e0000000-e1ffffff
	Prefetchable memory behind bridge: d8000000-dfffffff
	Capabilities: <access denied>

00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs SB0410 SBLive! 24-bit
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d000 [size=32]
	Capabilities: <access denied>

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RT8139
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at d400 [size=256]
	Memory at e2000000 (32-bit, non-prefetchable) [size=256]

00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RT8139
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at d800 [size=256]
	Memory at e2001000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology GA-7VAX Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 19
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at dc00 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-7VAX Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at e000 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-7VAX Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at e400 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-7VAX Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at e800 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-7VAX Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at e2002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: Giga-byte Technology GA-7VT600 Motherboard
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: Giga-byte Technology GA-7VAX Onboard Audio (Realtek ALC650)
	Flags: medium devsel, IRQ 20
	I/O ports at ec00 [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 17
	Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at e1000000 [disabled] [size=128K]
	Capabilities: <access denied>

---

### Post by RichardG891 on 2008-04-26
It's probably a dumb question but have you unchecked Analog/Digital Output Jack on the Switches tab in Volume Control?

---

### Post by DarkSim on 2008-04-26
Type ```
cat /proc/asound/modules
``` into a terminal. It should spit out something like this with ca0106 at the snd_0 part.

 0 snd_ca0106
 1 snd_via82xx

If its not in that order use this help guide at [https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29#head-72023a784829d5d128546a6092d67062ab50dfea](https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29#head-72023a784829d5d128546a6092d67062ab50dfea)

Configuring default soundcards / stopping soundcards from switching

Note: This section assumes that you have installed each soundcard properly.

*

In a shell, type ```
cat /proc/asound/modules
```
*

This will give the the name and index of each soundcard you have currently. Make a note of the names, and decide which one you want to be the default card.
*

Now type ```
sudo nano /etc/modprobe.d/alsa-base
```
*

At the very end of the file, add the following (assuming you have 3 cards with module names A, B and C and you want to have them in the order CAB)

options snd-C index=0
options snd-A index=1
options snd-B index=2

---

### Post by Victoroth on 2008-04-27
Thanks but i revice from "sudo nano /etc/modprobe.d/alsa-base" command this
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

From "cat /proc/asound/modules"
 0 snd_via82xx
 1 snd_ca0106

You tell that I should replace this 2 lines of some conf file (instead of ca0106 , it must be CA0106),I can't understood where is that file.What I should do ?

---

### Post by DarkSim on 2008-04-27
Add these two lines to the file that sudo nano /etc/modprobe.d/alsa-base brings up at the bottom.

options snd-ca0106 index=0
options snd-via82xx index=1
 hit ctrl+x and save.

Then type ```
asoundconf set-default-card CA0106
``` into a terminal. Reboot and you should have sound.

---

