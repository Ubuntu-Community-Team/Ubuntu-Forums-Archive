---
title: "Mouse/usb issue in 12.04"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by jraftb on 2012-06-20
hey all, im new here, just got ubuntu set up on my laptop, and i cant get my mouse to work properly, it is a microsoft wireless 4000 mouse, the system shows it as an input but when trying to use it there is a delay and its very choppy,i tried adjusting sensitivity and acceleration to either extremes and its the same on either setting,
sorry its a dell inspiron m5030 amd with 4gig ram
also the touch pad works fine, i read people say its a usb issue the usb open in usb 1.0 instead of 2.0 causing it to run slow, i ran a check and it shows them in 1.1 mode and no amount of rebooting is helping the problem as was recomeneded by someone else

---

### Post by jkurtisr32 on 2012-06-20
> **jraftb said:**
> hey all, im new here, just got ubuntu set up on my laptop, and i cant get my mouse to work properly, it is a microsoft wireless 4000 mouse, the system shows it as an input but when trying to use it there is a delay and its very choppy,i tried adjusting sensitivity and acceleration to either extremes and its the same on either setting,
sorry its a dell inspiron m5030 amd with 4gig ram
also the touch pad works fine, i read people say its a usb issue the usb open in usb 1.0 instead of 2.0 causing it to run slow, i ran a check and it shows them in 1.1 mode and no amount of rebooting is helping the problem as was recomeneded by someone else

Have you checked to see if you have the same problem in older versions of Ubuntu? I would make a live CD/USB of an older distribution and see if the problem is with 12.04. One of my machines is still on 10.04 for a similar reason.

---

### Post by jraftb on 2012-06-20
where would i find an older version of it? sorry, im new to all this

---

### Post by cortman on 2012-06-20
> **jraftb said:**
> hey all, im new here, just got ubuntu set up on my laptop, and i cant get my mouse to work properly, it is a microsoft wireless 4000 mouse, the system shows it as an input but when trying to use it there is a delay and its very choppy,i tried adjusting sensitivity and acceleration to either extremes and its the same on either setting,
sorry its a dell inspiron m5030 amd with 4gig ram
also the touch pad works fine, i read people say its a usb issue the usb open in usb 1.0 instead of 2.0 causing it to run slow, i ran a check and it shows them in 1.1 mode and no amount of rebooting is helping the problem as was recomeneded by someone else

Try running

```
sudo modprobe ehci_hcd
```

in a terminal, and see if that helps.

---

### Post by jraftb on 2012-06-20
i will try that as soon as possible, im at work and ill have to run home and grab my laptop when i take lunch, but i found this linked on the ubuntu site [http://www.mirrorservice.org/sites/releases.ubuntu.com/11.10/](http://www.mirrorservice.org/sites/releases.ubuntu.com/11.10/) would i use the 11.10 desktop installer file to make a boot disk?

---

### Post by cortman on 2012-06-20
> **jraftb said:**
> i will try that as soon as possible, im at work and ill have to run home and grab my laptop when i take lunch, but i found this linked on the ubuntu site [http://www.mirrorservice.org/sites/releases.ubuntu.com/11.10/](http://www.mirrorservice.org/sites/releases.ubuntu.com/11.10/) would i use the 11.10 desktop installer file to make a boot disk?

If the modprobe command doesn't work and you want to try reinstalling, use images from [this site]("http://releases.ubuntu.com/").

---

### Post by jraftb on 2012-06-20
well i tried the 
sudo modprobe ehci_hcd

but there was no diffrence, and also no diffrence booting an older version of ubuntu, i used 11.04 natty to go back to, should i try going further back?

---

### Post by cortman on 2012-06-20
> **jraftb said:**
> well i tried the 
sudo modprobe ehci_hcd

but there was no diffrence, and also no diffrence booting an older version of ubuntu, i used 11.04 natty to go back to, should i try going further back?

OK, run the modprobe command again, and after that run

```
lspci -v
```

and post the output here.

Also, I'll make sure to ask the obvious as well- you're sure the batteries are full in the mouse and that you're not on glass or some other difficult surface? Have you tried the mouse on a different computer?

---

### Post by jraftb on 2012-06-20
Yea, the mouse i have works on windows 7 thats also installed, fresh batterys and on a mouse pad,

---

### Post by jraftb on 2012-06-20
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32
    Capabilities: <access denied>

00:01.0 PCI bridge: Dell Device 9602 (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 32
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: ff300000-ff4fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: ff600000-ff6fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: ff500000-ff5fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 42
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=16]
    Memory at ff709000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at ff708000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at ff707000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at ff706000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
    Subsystem: Dell Device 0487
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Dell Device 0487
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at ff700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=0c, subordinate=13, sec-latency=64

00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at ff705000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at ff704000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0487
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at e000 [size=256]
    Memory at ff400000 (32-bit, non-prefetchable) [size=64K]
    Memory at ff300000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Wistron NeWeb Corp. DNXA-95 802.11bgn Wireless Half-size Mini PCIe Card
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ff600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

05:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
    Subsystem: Dell Device 0487
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at ff500000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at d000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

this is what it says

---

### Post by cortman on 2012-06-20
> **jraftb said:**
> 
this is what it says

Thanks; just FYI when you post output like that, post it between ```
 tags (the little hash # symbol in the post editing toolbar) for easier reading.

Ok, another (seemingly) basic suggestion- try the mouse in all the available USB ports- it looks as though there are 2 USB controllers? - one is using the 1.1 driver, and the other the 2.0

Also, run

[CODE]sudo lspci -v
```

and post the output. Thanks!

---

### Post by jraftb on 2012-06-20
yes no matter which usb port its plugged into, its a laptop with only ports on it,
and here is the output, also thanks for the help so far, 

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Dell Device 9602 (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 32
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: ff300000-ff4fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: Dell Device 0487
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: ff600000-ff6fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Dell Device 0487
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: ff500000-ff5fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Dell Device 0487
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 42
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=16]
    Memory at ff709000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] MSI: Enable+ Count=1/4 Maskable- 64bit+
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at ff708000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at ff707000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at ff706000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
    Subsystem: Dell Device 0487
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Dell Device 0487
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at ff700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=0c, subordinate=13, sec-latency=64

00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at ff705000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Dell Device 0487
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at ff704000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0487
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at e000 [size=256]
    Memory at ff400000 (32-bit, non-prefetchable) [size=64K]
    Memory at ff300000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Wistron NeWeb Corp. DNXA-95 802.11bgn Wireless Half-size Mini PCIe Card
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ff600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
    Capabilities: [170] Power Budgeting <?>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

05:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
    Subsystem: Dell Device 0487
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at ff500000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at d000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-c8-4c-c1-f0-4d-a2-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c

```

---

### Post by jraftb on 2012-06-20
its possible that the mouse im using is not compatable, but i have a microsoft 3000 mouse and a 4000 and neither work, the 3000 works slightly better but still laggy/jumpy like the usb isnt transfering quick enough, and what ive read both of them should work fine

---

### Post by jraftb on 2012-06-20
well just dug out my old wired optical mouse, and still the same problem, so im guessing its a usb issue, just booted up windows to make sure it was still working good, and no issues there

---

### Post by cortman on 2012-06-21
Hm. Run

```
sudo modprobe ehci_hcd
sudo modprobe -r ochi_hcd
sudo modprobe -r uchi_hcd
```

And see if that makes a difference. It definitely appears to be the USB port.
You're quite welcome for the help; I'm just sorry it's taking this long!

---

### Post by jraftb on 2012-06-21
well when i try to run that i get a fatal module not found, i tried copy and pasting the entire thing in at once, but that didnt do anything either

```
joe@joe-Inspiron-M5030:~$ sudo modprobe ehci_hcd
joe@joe-Inspiron-M5030:~$ sudo modprobe -r ochi_hcd
FATAL: Module ochi_hcd not found.
joe@joe-Inspiron-M5030:~$ sudo modprobe -r uchi_hcd
FATAL: Module uchi_hcd not found.

```

---

### Post by cortman on 2012-06-21
Ok, run this instead

```
sudo echo -n "00:16.0" > /sys/bus/pci/drivers/ohci_hcd/unbind
sudo echo -n "00:16.0" > /sys/bus/pci/drivers/ohci_hcd/bind
```

---

### Post by jraftb on 2012-06-21
Do i run them together or one after the other? im assuming its one then the other, just never to sure on these things lol

---

### Post by jraftb on 2012-06-21
either way i run it i get a permission denied message

```
joe@joe-Inspiron-M5030:~$ sudo echo -n "00:16.0" > /sys/bus/pci/drivers/ohci_hcd/unbind
bash: /sys/bus/pci/drivers/ohci_hcd/unbind: Permission denied
joe@joe-Inspiron-M5030:~$ sudo echo -n "00:16.0" > /sys/bus/pci/drivers/ohci_hcd/bind
bash: /sys/bus/pci/drivers/ohci_hcd/bind: Permission denied

```

---

### Post by cortman on 2012-06-21
Whoops, my bad- you need to be root to do this. Root account isn't enabled in Ubuntu by default, so you'll have to enable it first. In a terminal

```
sudo passwd root
```

Enter a new root password, and login as root by typing

```
su
```

Now run

```
update-pciids
update-usbids
```

Then run

```
/sys/bus/pci/drivers/ohci_hcd echo -n 00:16.0 > unbind
/sys/bus/pci/drivers/ehci_hcd echo -n 00:16.0 > bind
```

---

### Post by jraftb on 2012-06-21
this is what i get once i enter that 
```
root@joe-Inspiron-M5030:/home/joe# update-pciids
Downloaded daily snapshot dated 2012-05-07 03:15:01
root@joe-Inspiron-M5030:/home/joe# update-usbids
--2012-06-21 16:54:41--  http://www.linux-usb.org/usb.ids
Resolving www.linux-usb.org (www.linux-usb.org)... 216.34.181.97
Connecting to www.linux-usb.org (www.linux-usb.org)|216.34.181.97|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 478065 (467K) [text/plain]
Saving to: `/var/lib/usbutils/usb.ids.new'

100%[======================================>] 478,065      198K/s   in 2.4s    

2012-06-21 16:54:43 (198 KB/s) - `/var/lib/usbutils/usb.ids.new' saved [478065/478065]

Done.
root@joe-Inspiron-M5030:/home/joe# /sys/bus/pci/drivers/ohci_hcd echo -n 00:16.0 > unbind
bash: /sys/bus/pci/drivers/ohci_hcd: Is a directory
root@joe-Inspiron-M5030:/home/joe# /sys/bus/pci/drivers/ehci_hcd echo -n 00:16.0 > bind
bash: /sys/bus/pci/drivers/ehci_hcd: Is a directory

```

---

### Post by cortman on 2012-06-21
OK, some progress made anyway. :-?
Run these slightly modified original commands-

```
echo -n 00:16.0 > /sys/bus/pci/drivers/ohci_hcd/unbind
echo -n 00:16.0 > /sys/bus/pci/drivers/ohci_hcd/bind
```

---

### Post by jraftb on 2012-06-21
it says no such device, sorry for bothering you so much, i didn't want to go in and try to do it on my own with the fear of messing it all up, and i sincerely appreciate the help so far

```
root@joe-Inspiron-M5030:/home/joe# echo -n 00:16.0 > /sys/bus/pci/drivers/ohci_hcd/unbind
bash: echo: write error: No such device
root@joe-Inspiron-M5030:/home/joe# echo -n 00:16.0 > /sys/bus/pci/drivers/ohci_hcd/bind
bash: echo: write error: No such device
```

---

### Post by cortman on 2012-06-21
No bother at all- I'm rather sorry it's taking this long with no real effect.
At this point your best bet may be to try a quick reinstallation of Ubuntu- unless you've spent a lot of time getting it customized to your liking this might be the best idea.
If that doesn't work, I'll get some more talented people in to take a look. :-?

---

### Post by jraftb on 2012-06-21
This is actually my 4th install of ubuntu on this computer, first i used the 32 bit version, with the wubi install,and then changed it and instaled off the live cd and had this problem with both, but since i have an amd processor and was running 64 bit windoes i tried a install of ubuntu 64 bit, and i also put an older version on a seprate partion as well with the same results when you advised an older version, so at this point im completely lost, i still have windows if i need to just stick with that, but i have come to love the ubuntu so far, if only the mouse would work it would be perfect

---

### Post by jraftb on 2012-06-21
do you know if a wi fi mouse will work on ubuntu? theres a good deal on one on amazon and if it will work im gonna buy it and forget about using the usb one

---

### Post by cortman on 2012-06-22
> **jraftb said:**
> do you know if a wi fi mouse will work on ubuntu? theres a good deal on one on amazon and if it will work im gonna buy it and forget about using the usb one

Not sure about that. I haven't abandoned this project yet; I'm talking with some other people about it. Will be back soon!

---

### Post by jmfal on 2012-06-22
I had a similar problem, using a Microsoft 2000 wireless keyboard/mouse
Had to unplug replug dongle then get  45 min -1hr  before it would freeze again.

Gave up and bought  Logitech wireless from walmart---$35
Problem solved

At first I thought the problem was plugging the dongle into my card reader, moves it  but it just froze anyway just took a little bit longer.

---

### Post by cortman on 2012-06-22
> **jmfal said:**
> Gave up and bought  Logitech wireless from walmart---$35
Problem solved

From talking it over with more knowledgeable people, it sounds like this is probably your best bet- apparently the module isn't a problem.
Sorry I wasn't more helpful!

---

### Post by jraftb on 2012-06-22
thanks for the help, is there a way to uninstall and re install my usb hub drivers? that would be my last thing i would try if you didnt already have me do that lol, im gonna try to use my girlfriends logitec mouse tomorrow and see what happens

---

### Post by cortman on 2012-06-22
> **jraftb said:**
> thanks for the help, is there a way to uninstall and re install my usb hub drivers? that would be my last thing i would try if you didnt already have me do that lol, im gonna try to use my girlfriends logitec mouse tomorrow and see what happens

That's pretty much what I was trying to do with you earlier; it either doesn't appear to be working or else it isn't the problem... :?

---

### Post by jraftb on 2012-06-22
ahhh, im gonna try my girlfriends mouse and hopefully it works, if not i found one that says its compatible with 1.1 or 2.0 so if the usb is the issue then that should still work, i thank you for your time, even tho we werent able to sort it out i have to say its great to see members of the community so willing to help out a total newbie

---

### Post by cortman on 2012-06-23
> **jraftb said:**
> ahhh, im gonna try my girlfriends mouse and hopefully it works, if not i found one that says its compatible with 1.1 or 2.0 so if the usb is the issue then that should still work, i thank you for your time, even tho we werent able to sort it out i have to say its great to see members of the community so willing to help out a total newbie

We're always happy to help- and thank you for being so easy to help. Cheers!

---

### Post by jraftb on 2012-06-25
Well figured id give you guys an update, i tried my girlfriend mouse and all is good with that, so i ordered on from amazon and i thank you for your time, who would have thought that the 3 diffrent mice i tried were all having issues

---

### Post by cortman on 2012-06-25
> **jraftb said:**
> Well figured id give you guys an update, i tried my girlfriend mouse and all is good with that, so i ordered on from amazon and i thank you for your time, who would have thought that the 3 diffrent mice i tried were all having issues

Thanks for concluding the issue; glad it's working for you. :)
Good luck!

---

### Post by jraftb on 2012-06-28
man mice hate me, lol is there anyway to set the sensitivity way down below what it allows with sliders, this new logitec mouse is crazy sensitive

---

