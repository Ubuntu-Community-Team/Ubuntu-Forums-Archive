---
title: "No audio n Headphones Jack with Gateway t6836"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by enriqg9 on 2008-11-29
I have a Gateway T68636 Laptop, i have sound through the speakers, but when i plug the headphones in the headphone jack, the sound stops on the speakers but it doesnt starts in the headphones,Thanks.

enrique@enrique-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
Flags: bus master, fast devsel, latency 0
Capabilities:
Kernel driver in use: agpgart-intel
Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at f3000000 (64-bit, non-prefetchable) [size=1M]
Memory at d0000000 (64-bit, prefetchable) [size=256M]
I/O ports at 1800 [size=8]
Capabilities:
Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, fast devsel, latency 0
Memory at f3100000 (64-bit, non-prefetchable) [size=1M]
Capabilities:

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at 1820 [size=32]
Kernel driver in use: uhci_hcd
Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, medium devsel, latency 0, IRQ 21
I/O ports at 1840 [size=32]
Kernel driver in use: uhci_hcd
Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04) (prog-if 20)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, medium devsel, latency 0, IRQ 18
Memory at f3404800 (32-bit, non-prefetchable) [size=1K]
Capabilities:
Kernel driver in use: ehci_hcd
Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, fast devsel, latency 0, IRQ 2298
Memory at f3400000 (64-bit, non-prefetchable) [size=16K]
Capabilities:
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
I/O behind bridge: 00002000-00002fff
Memory behind bridge: f0000000-f0ffffff
Prefetchable memory behind bridge: 00000000c2000000-00000000c20fffff
Capabilities:
Kernel driver in use: pcieport-driver
Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
I/O behind bridge: 00003000-00003fff
Memory behind bridge: f1000000-f1ffffff
Capabilities:
Kernel driver in use: pcieport-driver
Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
I/O behind bridge: 00004000-00004fff
Memory behind bridge: f2000000-f2ffffff
Capabilities:
Kernel driver in use: pcieport-driver
Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, medium devsel, latency 0, IRQ 23
I/O ports at 1860 [size=32]
Kernel driver in use: uhci_hcd
Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at 1880 [size=32]
Kernel driver in use: uhci_hcd
Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at 18a0 [size=32]
Kernel driver in use: uhci_hcd
Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04) (prog-if 20)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, medium devsel, latency 0, IRQ 23
Memory at f3404c00 (32-bit, non-prefetchable) [size=1K]
Capabilities:
Kernel driver in use: ehci_hcd
Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4) (prog-if 01)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
Capabilities:

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, medium devsel, latency 0
Capabilities:
Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])
Subsystem: Gateway 2000 Device 0560
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at 1810 [size=16]
Kernel driver in use: ata_piix
Kernel modules: ata_piix, pata_acpi, ata_generic

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04) (prog-if 01)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2299
I/O ports at 1c00 [size=8]
I/O ports at 18d4 [size=4]
I/O ports at 18d8 [size=8]
I/O ports at 18d0 [size=4]
I/O ports at 18e0 [size=32]
Memory at f3404000 (32-bit, non-prefetchable) [size=2K]
Capabilities:
Kernel driver in use: ahci
Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
Subsystem: Gateway 2000 Device 0560
Flags: medium devsel, IRQ 10
Memory at c2100000 (32-bit, non-prefetchable) [size=256]
I/O ports at 1c20 [size=32]
Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
Subsystem: Gateway 2000 Device 0560
Flags: bus master, fast devsel, latency 0, IRQ 2300
I/O ports at 2000 [size=256]
Memory at f0000000 (64-bit, non-prefetchable) [size=4K]
[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
Capabilities:
Kernel driver in use: r8169
Kernel modules: r8169

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
Subsystem: Intel Corporation Device 1000
Flags: bus master, fast devsel, latency 0, IRQ 2297
Memory at f1000000 (32-bit, non-prefetchable) [size=4K]
Capabilities:
Kernel driver in use: iwl3945
Kernel modules: iwl3945

---

### Post by endoubt on 2008-11-29
Are you sure the headphones work? You could try plugging in your desktop speakers or another set of headphones to make sure it's not faulty headphones.

This answer came from defcon at [http://en.kioskea.net/forum/affich-1098-headphones-no-sound]("http://en.kioskea.net/forum/affich-1098-headphones-no-sound")

> Hi there I think I solved this prob i had the same thing. go to your control panel/hardware and sound. then click manage audio devices on SOUNDS. make the first SPEAKERS your default and that should solve it. This worked for me hope it helps you too.

This answer came from FredFjr at [http://ph.ubuntuforums.com/showthread.php?t=705287]("http://ph.ubuntuforums.com/showthread.php?t=705287")

> Well, no guarantees that this will help you (I have a HP Pavilion zv5320), but here's the process that got things working right for me:

1. Double-click on the speaker icon. You should see the Volume Control window open now.
2. Click Edit-->Preferences in the Volume Control window. The Volume Control Preferences window should be open with various check boxes that will display tracks to be visible when they're clicked.
3. There should be a check box there named Headphone Jack Sense. If it's there, click it to put a check there. A tab named Switches should be open now in your first Volume Control window. Close the Volume Control Preferences window to get back to the first Volume Control window.
4. Click on the Switches tab to display it. Click the check box for Headphone Jack Sense.

This is the point at which things worked well. The speaker would work until I plugged in headphones, at which time the headphones took over and the laptop speakers went silent.

My laptop has a NVidia NForce3 motherboard inside it so I can't be sure things will be the same for you. I hope this helps.

Have a good day.

Keep searching the forums, there are about as many answers as there are types of laptops.

---

### Post by enriqg9 on 2008-11-29
Hi, i tried what you told me but it didnt work ¡, im despered i already search in google for 2 days and i cant find the answer yet, i also tried to edit the alsa-base file without any results, thankyou.

---

### Post by bkanuka on 2008-12-05
I too have searched for, and desperately need a solution to this. Music is my life!

As possibly one of the worst workarounds ever, I can plug in my headphones (more like speaker system) and restart the computer and headphones work until they are unplugged once.

Maybe if someone could help me find what specific program to restart instead of the whole computer, I could live with this...but alas, it will suck until then.  Oh and its not just sudo etc/init.d/alsa-utils restart.  Already tried it.

---

### Post by psychoelf on 2008-12-06
I have a 6850FX and this worked for me:
[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

Update: No longer working after update.  I tried to re-edit the file but did not help.  External jack worked on reboot, but stopped as soon as I unplugged and plugged back in.

I get sound for about one second when I plug in external speakers.  Weird.  Help?

---

### Post by Xombie207 on 2008-12-21
This won't help much but I also have a Gateway T6836 and i've experienced the same problem.  All I know is that some headphones work and some don't, being as i've had a pair work in ubuntu and I have some that don't work in ubuntu.

---

### Post by tecknos11 on 2009-01-30
I have a gateway as well and I think that Alsa is muting both the headphones and the speakers when you plug in the headphones. When I plug in the headphones I get sound for a fraction of a second and then it goes away at the same time as the speakers are muted.

---

### Post by tufcamman on 2009-03-20
Any progress made on this yet?  Same prob here

---

