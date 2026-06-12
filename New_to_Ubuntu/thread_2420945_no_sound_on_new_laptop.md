---
title: "no sound on new laptop"
date: 2019-06-13
forum: New to Ubuntu
---

### Post by partyzen on 2019-06-13
Hi there, I'm new to linux and need some help.

I just installed ubuntu 18.04 on my new laptop, and there is no sound through the speakers or through headset. I tried two headsets, one with a usb plug and one with the usual headphone plug.

the soundcard seems to be recognized, I have "Speakers - Built-in Audio" and "Digital Output (S/PDIF) - Built-in Audio" on the sound control screen.
Alsamixer looks ok too, lists the drivers, and nothing muted
pavucontrol shows Built-in Audio Analog Stereo, Port: Speakers, and the orange bar indicating volume moves with the music. I just cant hear anything. It also recognizes if i plug in a speaker, e.g. Plantronics. I played around with all the settings on the configuration tab

I purged and reinstalled alsa, restarrted, 
also made sure the speach-dispatcher was set to run = no (it was)
also added "options snd-hda-intel model=generic" to alsa-base.conf  Didin't do much only added one more (HDMI) device to the sound control panel.

My config:
inxi -GAz
Graphics:  Card-1: Intel Device 3e9b
           Card-2: NVIDIA Device 1f51
           Display Server: x11 (X.Org 1.20.1 ) driver: i915 Resolution: 1920x1080@144.03hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 630 (Coffeelake 3x8 GT2) version: 4.5 Mesa 18.2.8
Audio:     Card-1 Intel Cannon Lake PCH cAVS driver: snd_hda_intel Sound: ALSA v: k4.18.0-21-generic
           Card-2 NVIDIA Device 10f9 driver: snd_hda_intel


running out of ideas, can you guys think of anything else I could check

```
00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 122
    Bus: primary=00, secondary=01, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 60000000-740fffff
    Prefetchable memory behind bridge: 000000604b000000-000000604b0fffff
    Capabilities: [88] Subsystem: CLEVO/KAPOK Computer Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Capabilities: [d94] #19
    Kernel driver in use: pcieport

00:02.0 VGA compatible controller: Intel Corporation Device 3e9b (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, fast devsel, latency 0, IRQ 180
    Memory at 604a000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 4000000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [40] Vendor Specific Information: Len=0c <?>
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [100] Process Address Space ID (PASID)
    Capabilities: [200] Address Translation Service (ATS)
    Capabilities: [300] Page Request Interface (PRI)
    Kernel driver in use: i915
    Kernel modules: i915

00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 604b20b000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal

00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10) (prog-if 30 [XHCI])
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, medium devsel, latency 0, IRQ 130
    Memory at 74500000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: xhci_hcd

00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, fast devsel, latency 0
    Memory at 604b204000 (64-bit, non-prefetchable) [size=8K]
    Memory at 604b20a000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3

00:15.0 Serial bus controller [0c80]: Intel Corporation Device a368 (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 4010000000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:15.1 Serial bus controller [0c80]: Intel Corporation Device a369 (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 4010001000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, fast devsel, latency 0, IRQ 165
    Memory at 604b207000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [a4] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:17.0 SATA controller: Intel Corporation Device a353 (rev 10) (prog-if 01 [AHCI 1.0])
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 133
    Memory at 74510000 (32-bit, non-prefetchable) [size=8K]
    Memory at 74514000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 5080 [size=8]
    I/O ports at 5088 [size=4]
    I/O ports at 5060 [size=32]
    Memory at 74513000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1b.0 PCI bridge: Intel Corporation Device a340 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Bus: primary=00, secondary=06, subordinate=6f, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: 78000000-a60fffff
    Prefetchable memory behind bridge: 0000006000000000-0000006049ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 65d1
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [220] #19
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport

00:1b.4 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port 21 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 124
    Bus: primary=00, secondary=70, subordinate=70, sec-latency=0
    Memory behind bridge: 74400000-744fffff
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 65d4
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [220] #19
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport

00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port 9 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 125
    Bus: primary=00, secondary=71, subordinate=71, sec-latency=0
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 65d1
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [220] #19
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport

00:1d.5 PCI bridge: Intel Corporation Device a335 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 126
    Bus: primary=00, secondary=72, subordinate=72, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 74300000-743fffff
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 65d1
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [220] #19
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport

00:1d.6 PCI bridge: Intel Corporation Device a336 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 127
    Bus: primary=00, secondary=73, subordinate=73, sec-latency=0
    Memory behind bridge: 74200000-742fffff
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 65d1
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [220] #19
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport

00:1d.7 PCI bridge: Intel Corporation Device a337 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 128
    Bus: primary=00, secondary=74, subordinate=74, sec-latency=0
    Memory behind bridge: 74100000-741fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 65d1
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [220] #19
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport

00:1f.0 ISA bridge: Intel Corporation Device a30d (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, medium devsel, latency 0

00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at 604b200000 (64-bit, non-prefetchable) [size=16K]
    Memory at 604b100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Vendor Specific Information: Len=14 <?>
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: medium devsel, IRQ 255
    Memory at 604b206000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5040 [size=32]
    Kernel modules: i2c_i801

00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 65d1
    Flags: bus master, fast devsel, latency 0
    Memory at fe010000 (32-bit, non-prefetchable) [size=4K]

01:00.0 VGA compatible controller: NVIDIA Corporation Device 1f51 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer Device 65d4
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 73000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 60000000 (64-bit, prefetchable) [size=256M]
    Memory at 70000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    Expansion ROM at 72000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [250] Latency Tolerance Reporting
    Capabilities: [258] L1 PM Substates
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [420] Advanced Error Reporting
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Capabilities: [bb0] #15
    Kernel modules: nvidiafb, nouveau

01:00.1 Audio device: NVIDIA Corporation Device 10f9 (rev a1)
    Subsystem: CLEVO/KAPOK Computer Device 65d4
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 74000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

01:00.2 USB controller: NVIDIA Corporation Device 1ada (rev a1) (prog-if 30 [XHCI])
    Subsystem: NVIDIA Corporation Device 0000
    Flags: bus master, fast devsel, latency 0, IRQ 131
    Memory at 604b000000 (64-bit, prefetchable) [size=256K]
    Memory at 604b040000 (64-bit, prefetchable) [size=64K]
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: xhci_hcd

01:00.3 Serial bus controller [0c80]: NVIDIA Corporation Device 1adb (rev a1)
    Subsystem: NVIDIA Corporation Device 0000
    Flags: fast devsel, IRQ 255
    Memory at 74004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Power Management version 3
    Capabilities: [100] Advanced Error Reporting

06:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06) (prog-if 00 [Normal decode])
    Physical Slot: 16
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=06, secondary=07, subordinate=6f, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: 78000000-a60fffff
    Prefetchable memory behind bridge: 0000006000000000-0000006049ffffff
    Capabilities: [80] Power Management version 3
    Capabilities: [88] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [ac] Subsystem: CLEVO/KAPOK Computer JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
    Capabilities: [c0] Express Upstream Port, MSI 00
    Capabilities: [50] #15 [0000]
    Capabilities: [100] Device Serial Number cb-43-a5-11-2c-b7-d0-00
    Capabilities: [200] Advanced Error Reporting
    Capabilities: [300] Virtual Channel
    Capabilities: [400] Power Budgeting <?>
    Capabilities: [500] Vendor Specific Information: ID=1234 Rev=1 Len=100 <?>
    Capabilities: [600] Vendor Specific Information: ID=8086 Rev=2 Len=04c <?>
    Capabilities: [700] #19
    Capabilities: [800] Latency Tolerance Reporting
    Capabilities: [a00] L1 PM Substates
    Capabilities: [b00] Precision Time Measurement
    Kernel driver in use: pcieport

07:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=07, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: a6000000-a60fffff
    Capabilities: [80] Power Management version 3
    Capabilities: [88] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [ac] Subsystem: CLEVO/KAPOK Computer JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
    Capabilities: [c0] Express Downstream Port (Slot+), MSI 00
    Capabilities: [50] #15 [0000]
    Capabilities: [100] Device Serial Number cb-43-a5-11-2c-b7-d0-00
    Capabilities: [200] Advanced Error Reporting
    Capabilities: [300] Virtual Channel
    Capabilities: [400] Power Budgeting <?>
    Capabilities: [500] Vendor Specific Information: ID=1234 Rev=1 Len=100 <?>
    Capabilities: [600] Vendor Specific Information: ID=8086 Rev=2 Len=04c <?>
    Capabilities: [700] #19
    Capabilities: [900] Access Control Services
    Kernel driver in use: pcieport

07:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 129
    Bus: primary=07, secondary=09, subordinate=6e, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: 78000000-a5efffff
    Prefetchable memory behind bridge: 0000006000000000-0000006049ffffff
    Capabilities: [80] Power Management version 3
    Capabilities: [88] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [ac] Subsystem: CLEVO/KAPOK Computer JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
    Capabilities: [c0] Express Downstream Port (Slot+), MSI 00
    Capabilities: [50] #15 [0000]
    Capabilities: [100] Device Serial Number cb-43-a5-11-2c-b7-d0-00
    Capabilities: [200] Advanced Error Reporting
    Capabilities: [300] Virtual Channel
    Capabilities: [400] Power Budgeting <?>
    Capabilities: [500] Vendor Specific Information: ID=1234 Rev=1 Len=100 <?>
    Capabilities: [600] Vendor Specific Information: ID=8086 Rev=2 Len=04c <?>
    Capabilities: [700] #19
    Capabilities: [900] Access Control Services
    Kernel driver in use: pcieport

07:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Bus: primary=07, secondary=6f, subordinate=6f, sec-latency=0
    Memory behind bridge: a5f00000-a5ffffff
    Capabilities: [80] Power Management version 3
    Capabilities: [88] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [ac] Subsystem: CLEVO/KAPOK Computer JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
    Capabilities: [c0] Express Downstream Port (Slot+), MSI 00
    Capabilities: [50] #15 [0000]
    Capabilities: [100] Device Serial Number cb-43-a5-11-2c-b7-d0-00
    Capabilities: [200] Advanced Error Reporting
    Capabilities: [300] Virtual Channel
    Capabilities: [400] Power Budgeting <?>
    Capabilities: [500] Vendor Specific Information: ID=1234 Rev=1 Len=100 <?>
    Capabilities: [600] Vendor Specific Information: ID=8086 Rev=2 Len=04c <?>
    Capabilities: [700] #19
    Capabilities: [900] Access Control Services
    Kernel driver in use: pcieport

08:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018] (rev 06)
    Subsystem: CLEVO/KAPOK Computer JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at a6000000 (32-bit, non-prefetchable) [size=256K]
    Memory at a6040000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [88] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [c0] Express Endpoint, MSI 00
    Capabilities: [a0] MSI-X: Enable+ Count=16 Masked-
    Capabilities: [100] Device Serial Number cb-43-a5-11-2c-b7-d0-00
    Capabilities: [200] Advanced Error Reporting
    Capabilities: [300] Virtual Channel
    Capabilities: [400] Power Budgeting <?>
    Capabilities: [500] Vendor Specific Information: ID=1234 Rev=1 Len=100 <?>
    Capabilities: [600] Latency Tolerance Reporting
    Kernel driver in use: thunderbolt
    Kernel modules: thunderbolt

6f:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018] (rev 06) (prog-if 30 [XHCI])
    Subsystem: CLEVO/KAPOK Computer JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018]
    Flags: bus master, fast devsel, latency 0, IRQ 132
    Memory at a5f00000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [80] Power Management version 3
    Capabilities: [88] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [c0] Express Endpoint, MSI 00
    Capabilities: [100] Device Serial Number cb-43-a5-11-2c-b7-d0-00
    Capabilities: [200] Advanced Error Reporting
    Capabilities: [300] Virtual Channel
    Capabilities: [400] Power Budgeting <?>
    Capabilities: [500] Vendor Specific Information: ID=1234 Rev=1 Len=100 <?>
    Capabilities: [600] Vendor Specific Information: ID=8086 Rev=2 Len=04c <?>
    Capabilities: [700] #19
    Capabilities: [800] Latency Tolerance Reporting
    Kernel driver in use: xhci_hcd

70:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981 (prog-if 02 [NVM Express])
    Subsystem: Samsung Electronics Co Ltd Device a801
    Flags: bus master, fast devsel, latency 0, IRQ 16, NUMA node 0
    Memory at 74400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [b0] MSI-X: Enable+ Count=33 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [148] Device Serial Number 00-00-00-00-00-00-00-00
    Capabilities: [158] Power Budgeting <?>
    Capabilities: [168] #19
    Capabilities: [188] Latency Tolerance Reporting
    Capabilities: [190] L1 PM Substates
    Kernel driver in use: nvme
    Kernel modules: nvme

72:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: CLEVO/KAPOK Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 3000 [size=256]
    Memory at 74304000 (64-bit, non-prefetchable) [size=4K]
    Memory at 74300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable+ Count=4 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] L1 PM Substates
    Kernel driver in use: r8169
    Kernel modules: r8169

73:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
    Subsystem: CLEVO/KAPOK Computer RTS525A PCI Express Card Reader
    Flags: bus master, fast devsel, latency 0, IRQ 151
    Memory at 74200000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [148] Device Serial Number 00-00-00-01-00-4c-e0-00
    Capabilities: [158] Latency Tolerance Reporting
    Capabilities: [160] L1 PM Substates
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci

74:00.0 Network controller: Intel Corporation Wireless-AC 9260 (rev 29)
    Subsystem: Intel Corporation Device 0014
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 74100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [80] MSI-X: Enable+ Count=16 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [14c] Latency Tolerance Reporting
    Capabilities: [154] L1 PM Substates
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
```

---

### Post by jproberge2 on 2019-06-16
I have this exact same problem, I also happen to have exactly the same setup as you! Same CPU and audio card! I'm also affected by this, has anyone found a solution to this yet? It's been hours I'm trying to make this work and I've tried a lot of different things already.

---

### Post by partyzen on 2019-06-16
I have sound now. I reinstalled ubuntu from scratch, and I went with 19.04. 

Here is what I did:
1. played around with alsamixer
2. played around with pavucontrol
3. reinstalled alsa
4. edited various options settings in the conf file
5. reinstalled graphics driver for the nvidia card (this was successful, yay!!!)
6. explored bios and realized it didnt have advanced settings
7. researched how to flash bios
8. considered flashing bios and then decided not to
9. following a tutorial, i installed hda-intel as a module rather than part of the kernel
10. realized that I messed up now all my drivers badly, I only had the dummy driver, no intel or nvidia
11.reinstalled ubuntu from scratch, and went with 1904. the only reason I went with 1804 before was my expectation it's going to be less problematic, being LTS and all.Ha!
12. 1904 worked as a charm. geforce video immediately, sound, everything.

20 hours of my life I'll never get back

@jproberge2: good luck mate!

---

### Post by jproberge2 on 2019-06-17
Thanks Partyzen for your reply! I'm in the same situation as you for the number of hours spent now :) However I don't want to go with 19.04 since 1) I'd like to stick with the LTS version, but mostly: 2) I tried Ubuntu 19.04 live from a USB stick and sound was still not working. I did exactly the same procedure as you did, except that I stuck with the steps from 1 to 8. Anyway, thanks a lot for taking the time to share your outcome, I'll open my own thread now.

All the best ;)

---

### Post by jproberge2 on 2019-06-19
Last update: I finally was able to solve the problem and make everything work with Ubuntu 18.04! Please see this post [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1833161") and [here]("https://ubuntuforums.org/showthread.php?t=2421187").

Summary of what I've done to make things work:
> 
[COLOR=#000000]1) First of all, by looking at the output of "cat /proc/asound/card0/codec*" it was obvious something was wrong... So first to fix that I had to edit the file "/etc/modprobe.d/alsa-base.conf" to add the line: "options snd-hda-intel probe_mask=0x1" . After reboot, then I could see everything the output of "cat /proc/asound/card0/codec*" that was looking perfect but still no sound. At least, things had improved a little bit now;[/COLOR]

[COLOR=#000000]2) As shown by the output of "cat /proc/asound/card0/codec* | grep Codec", my HD Audio Codec is ALC1220 so I went [/COLOR][here]("https://www.infradead.org/~mchehab/rst_conversion/sound/hd-audio/models.html")[COLOR=#000000] to look at what specific model that corresponded. My laptop is a clevo laptop ("clevo-p950", in the list), so I added the line "options snd-hda-intel model=clevo-p950" to the the "/etc/modprobe.d/alsa-base.conf" file and rebooted. I thought I had solved it at this point but.... nope, still no sound from the speakers or the headphones... but then;[/COLOR]

[COLOR=#000000]3) After I posted a bug report [/COLOR][here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1833161")[COLOR=#000000], someone suggested that I upgrade my kernel version to at least 5.0. So if you are in this situation where you think you should proceed with a kernel upgrade and it's your first time, don't worry, it's not hard to do at all. I used to build my kernel from source (which can be a long process depending on your machine) but now there's a nice GUI and debian packages to help you out, this tool is Ukuu, see [/COLOR][this article]("https://www.addictivetips.com/ubuntu-linux-tips/get-the-latest-linux-kernel-version-in-ubuntu/")[COLOR=#000000] for example... In my case and at this moment of writing, after a fresh Ubuntu 18.04 install and update, the kernel version was [/COLOR][COLOR=#333333][FONT=monospace]4.18.0-22 [/FONT][/COLOR][COLOR=#000000]which was not able to make the "clevo-p950" option work. So I upgraded my kernel to 5.0.2, rebooted and everything started to work! Now my microphone, my headphone and my speakers are all working. This is nice! I hope this can help somebody! Good luck![/COLOR]

Leaving this here in case this could help someone :) Good luck!

---

