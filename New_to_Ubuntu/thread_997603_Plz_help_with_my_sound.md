---
title: "Plz help with my sound"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by jvilla777 on 2008-11-30
ive recently installed ubuntu because i was amazazed of what it can do and most of all its for FREE!!
im just having some problems with my sound..
ive been to system>preferences>sound and checked sounds but i dont hear no sounds.
ive also tried playing movies avi. mpeg. wmv. i get to see the video but no sound.
and when i go to sites like youtube.com i see the video and dont get no sound.
im using totem and also tried mplayer.
your help would be much appreciated. thank you

---

### Post by Xiong Chiamiov on 2008-11-30
[Start here.]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by nakama85 on 2008-11-30
Some Questions before anyone can help

What version of Ubuntu
What kind of sound card do you have?

Any other relative specs.

---

### Post by jvilla777 on 2008-11-30
ive jus installed ubuntu 8.10 intrepid on my external hard drive which i did a partition on. Im using my laptop "LG P1 Express Dual. im not really sure how to check the sound card but im pretty sure its somethin like REALTEK ALC880 or/and LSI si3054, that is what i got when i typed in "cat /proc/asound/card0/codec#* | grep Codec"..
any suggestions?

---

### Post by Xiong Chiamiov on 2008-11-30
Did you go through that guide I linked you?  If so, where did you have problems?

---

### Post by jvilla777 on 2008-11-30
hey yeah, i checked out the link i got up to step 2 and step 3 i jus dont understand, like i have to click on this link which says search for your sound card manufacturers in the drop down box... but i dont know if im lookin at the right site?

---

### Post by Xiong Chiamiov on 2008-11-30
EDIT: Actually, that page doesn't redirect where it used to; go [here]("http://www.alsa-project.org/main/index.php/Matrix:Main").

---

### Post by jvilla777 on 2008-11-30
it doesnt have a drop down box though.. it only has a "parent directory and underneath that has a folder which takes you to another site"..??

---

### Post by Xiong Chiamiov on 2008-11-30
My mistake, please see my edited post.

---

### Post by jvilla777 on 2008-11-30
hey its okay.. thanx but i dont think my sound card is in that website.. but i will show you what i got in the terminal when i went through steps 1 and 2 here is what i got..

jvilla777@jvilla777-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jvilla777@jvilla777-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d8000000-d80fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d8500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d4000000-d5ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d6000000-d7ffffff
	Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: d8100000-d81fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d8504000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d8200000-d82fffff
	Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1880 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 219
	I/O ports at 18c8 [size=8]
	I/O ports at 18ac [size=4]
	I/O ports at 18c0 [size=8]
	I/O ports at 18a8 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at d8504400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: medium devsel, IRQ 11
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at d8000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d8020000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Agere Systems ET-131x PCI-E Ethernet Controller (rev 02)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d4000000 (64-bit, non-prefetchable) [size=2M]
	[virtual] Expansion ROM at d0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: et131x
	Kernel modules: et131x

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1000
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at d8100000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

06:00.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at d8206000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 00005000-000050ff
	I/O window 1: 00005400-000054ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

06:00.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at d8205000 (32-bit, non-prefetchable) [size=2K]
	Memory at d8200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

06:00.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 57, IRQ 16
	Memory at d8204000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

06:00.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, medium devsel, latency 57, IRQ 16
	Memory at d8205800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

jvilla777@jvilla777-laptop:~$ sudo modprobe snd-
Display all 154 possibilities? (y or n)
snd-ac97-codec      snd-es1968          snd-pcsp
snd-ad1816a         snd-es968           snd-pcxhr
snd-ad1848          snd-fm801           snd-pdaudiocf
snd-ad1848-lib      snd-gina20          snd-portman2x4
snd-ad1889          snd-gina24          snd-pt2258
snd-adlib           snd-gusclassic      snd-rawmidi
snd-ak4114          snd-gusextreme      snd-riptide
snd-ak4117          snd-gus-lib         snd-rme32
snd-ak4xxx-adda     snd-gusmax          snd-rme96
snd-ali5451         snd-hda-intel       snd-rme9652
snd-als100          snd-hdsp            snd-sb16
snd-als300          snd-hdspm           snd-sb16-csp
snd-als4000         snd-hifier          snd-sb16-dsp
snd-atiixp          snd-hwdep           snd-sb8
snd-atiixp-modem    snd-i2c             snd-sb8-dsp
snd-au8810          snd-ice1712         snd-sbawe
snd-au8820          snd-ice1724         snd-sb-common
snd-au8830          snd-ice17xx-ak4xxx  snd-sc6000
snd-aw2             snd-indigo          snd-seq
snd-azt2320         snd-indigodj        snd-seq-device
snd-azt3328         snd-indigoio        snd-seq-dummy
snd-bt87x           snd-intel8x0        snd-seq-midi
snd-bt-sco          snd-intel8x0m       snd-seq-midi-emul
--More--

im not sure if im goin through the right stuff...?

---

### Post by nakama85 on 2008-11-30
ok try this.

in terminal ```
sudo gedit /etc/modprobe.d/alsa-base
``` 
Just like before add this next line to the bottom > options snd-hda-intel enable=1 index=0 model=dell-m82

Click save then close window.

Then in terminal enter the following```
sudo /etc/init.d/alsa-utils restart
```

then in terminal```
 sudo reboot
``` 
the above code will reboot your computer so save anything you need to first.

Then Let me know if this works.

---

