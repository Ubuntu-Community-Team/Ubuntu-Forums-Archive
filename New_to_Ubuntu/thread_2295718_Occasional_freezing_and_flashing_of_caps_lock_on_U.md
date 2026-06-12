---
title: "Occasional freezing and flashing of caps lock on Ubuntu boot"
date: 2015-09-20
forum: New to Ubuntu
---

### Post by Michael_Incardona on 2015-09-20
I have separate Windows 10 and Ubuntu partitions on my laptop. I use the normal Ubuntu boot launcher to select what I want to run when my computer starts. Sometimes, when selecting Ubuntu, the screen will go black, the computer will freeze, and the light on the caps lock key will flash continuously. There's no way to interact with the machine at all, so I'm forced to manual reset (by holding down the power button). I know this is bad for the machine, so I want to find out why this keeps happening. The problem only occurs when booting Ubuntu, not with Windows, and it happens about 1/3 times. The machine does not seem to be overheating.

---

### Post by ArgentWarrior on 2015-09-21
I believe that's a kernel panic OP. At least my laptop's done the same thing when that happens (I build my own kernels from source).

Try setting "nomodeset" in GRUB. Hold shift during startup until the GRUB menu comes up. Hit "e" with the Ubuntu entry selected and go to the line starting with "linux". This is the line that tells GRUB where the kernel image is. At the end of that line put "nomodeset" and hit F10.

Tell me if this works.

---

### Post by Michael_Incardona on 2015-09-21
The first time I tried this, I immediately went into kernel panic upon hitting F10. I rebooted and tried it again. This time, I got to the login screen, but entering my password only caused the password screen to disappear for a few seconds before reappearing so I couldn't log in. I rebooted again (from the menu this time) and loaded Ubuntu without changing the GRUB parameters, and I got in fine, password and everything.

We'll need to try something else, I'm afraid.

---

### Post by ArgentWarrior on 2015-09-21
Hmmm. I thought it might be that. My girlfriend had a similar issue on Debian. Can I get some info about your system so I can look into it?
```
sudo lspci -knnv
```

---

### Post by Michael_Incardona on 2015-09-21
Here's the output:

```
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
    Subsystem: Dell Device [1028:058f]
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: ivb_uncore


00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: [88] Subsystem: Dell Device [1028:058f]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport


00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:0590]
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915


00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: Dell Device [1028:058f]
    Flags: bus master, medium devsel, latency 0, IRQ 27
    Memory at f7a00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd


00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Dell Device [1028:058f]
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f7a1b000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me


00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:058f]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7a18000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci


00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Dell Device [1028:058f]
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f7a10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device [1028:058f]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport


00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: f7900000-f79fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device [1028:058f]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport


00:1c.5 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 [8086:1e1a] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7800000-f78fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device [1028:058f]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport


00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:058f]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7a17000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci


00:1f.0 ISA bridge [0601]: Intel Corporation HM77 Express Chipset LPC Controller [8086:1e57] (rev 04)
    Subsystem: Dell Device [1028:058f]
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich


00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 Mobile SATA Controller [RAID mode] [8086:282a] (rev 04)
    Subsystem: Dell Device [1028:058f]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f060 [size=32]
    Memory at f7a16000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci


00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Dell Device [1028:058f]
    Flags: medium devsel, IRQ 5
    Memory at f7a15000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]


02:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] [10de:1140] (rev a1)
    Subsystem: Dell GeForce GT 630M [1028:0590]
    Flags: bus master, fast devsel, latency 0, IRQ 34
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia


07:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4462]
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f7900000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 60-6c-66-ff-ff-da-81-30
    Kernel driver in use: iwlwifi


09:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Dell Device [1028:057e]
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at f7800000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at d000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [c0] MSI: Enable+ Count=1/16 Maskable+ 64bit+
    Capabilities: [d8] MSI-X: Enable- Count=16 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-b0-f8-ad-e0-db-55-ff
    Kernel driver in use: alx
```

---

### Post by ArgentWarrior on 2015-09-21
I see you have both an Intel iGPU and Nvidia. Do you have the proprietary drivers installed, or just Noveau?

By default Ubuntu uses the free Noveau driver for Nvidia cards, which is very lacking. If you can get back into Ubuntu (if you're not already there) try installing the proprietary Nvidia drivers for your GPU.
```

wget http://us.download.nvidia.com/XFree86/Linux-x86_64/295.33/NVIDIA-Linux-x86_64-295.33.run
sudo bash NVIDIA-Linux-x86_64-295.33.run

```

---

### Post by Michael_Incardona on 2015-09-21
The wget download completes fine but the actual driver install fails, telling me that I have an X server running which is blocking it. I tried running the commands after doing CTRL-ALT-F2, but it still says an X server is running.

Normally I just want to use the Intel integrated graphics as the primary adapter for everyhting, since it consumes less power/generates less heat, but I suppose there's nothing wrong with making sure the nvidia drivers are proper.

---

### Post by ArgentWarrior on 2015-09-21
Have you tried this? I don't know if the Nvidia drivers would show up here, as I've never used it on Ubuntu. But it's worth a shot.

[IMG]http://i.imgur.com/MWBoGNp.png[/IMG]

---

### Post by Michael_Incardona on 2015-09-21
OK, that worked. I'm now using the tested, proprietary nvidia 340.76 driver. I still get the kernel panic sometimes, just as before.

Here's something that might be related: Windows is configured to use a 30GB SSD as a RAID cache drive to improve boot times (it does make a big difference; the software is called "Intel rapid storage technology"). Could this be causing the issue?

---

### Post by Vladlenin5000 on 2015-09-21
> **Michael_Incardona said:**
> Here's something that might be related: Windows is configured to use a 30GB SSD as a RAID cache drive to improve boot times (it does make a big difference; the software is called "Intel rapid storage technology"). Could this be causing the issue?

Yes.
Intel Rapid Storage Technology has known issues with Linux/Ubuntu. The often quoted advice is to simply turn it off.


PS - The proprietary driver should provide better performance but it's unrelated.

---

### Post by Michael_Incardona on 2015-09-21
All right, I'll turn it off and test it a few times. Maybe I can reduce the windows boot time by disabling startup programs in lieu of the SSD.

---

### Post by Michael_Incardona on 2015-09-21
> **Michael_Incardona said:**
> All right, I'll turn it off and test it a few times. Maybe I can reduce the windows boot time by disabling startup programs in lieu of the SSD.

In case anyone else has this issue: disabling acceleration in Intel RST seems to have solved the problem. Booting Windows is slower now, but not intolerable. Thanks a ton everyone! I'll mark the thread as solved.

---

