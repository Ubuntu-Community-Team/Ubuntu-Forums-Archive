---
title: "Boot Errors"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by skymera on 2008-11-08
Hi

Just booted Ubuntu for first time in a few days and i'm getting some weird errors.

Here's a section of my dmesg:

```

[    9.677655] sd 6:0:0:0: [sde] Mode Sense: 27 00 00 00
[    9.677657] sd 6:0:0:0: [sde] Assuming drive cache: write through
[    9.678283] sd 6:0:0:0: [sde] 160836480 512-byte hardware sectors (82348 MB)
[    9.679165] sd 6:0:0:0: [sde] Write Protect is off
[    9.679167] sd 6:0:0:0: [sde] Mode Sense: 27 00 00 00
[    9.679169] sd 6:0:0:0: [sde] Assuming drive cache: write through
[    9.679172]  sde: sde1
[    9.690629] sd 6:0:0:0: [sde] Attached SCSI disk
[    9.690696] sd 6:0:0:0: Attached scsi generic sg5 type 0
[   10.799934] end_request: I/O error, dev sr0, sector 1429728
[   10.799940] Buffer I/O error on device sr0, logical block 178716
[   11.368457] end_request: I/O error, dev sr0, sector 1429728
[   11.368461] Buffer I/O error on device sr0, logical block 178716
[   11.935999] end_request: I/O error, dev sr0, sector 1429728
[   11.936014] Buffer I/O error on device sr0, logical block 178716
[   12.570426] end_request: I/O error, dev sr0, sector 1429728
[   12.570429] Buffer I/O error on device sr0, logical block 178716
[   13.168960] end_request: I/O error, dev sr0, sector 1429728
[   13.168963] Buffer I/O error on device sr0, logical block 178716
[   13.696602] end_request: I/O error, dev sr0, sector 1429728
[   13.696605] Buffer I/O error on device sr0, logical block 178716
[   14.361210] end_request: I/O error, dev sr0, sector 1429728
[   14.361213] Buffer I/O error on device sr0, logical block 178716
[   15.131865] end_request: I/O error, dev sr0, sector 1429728
[   15.131868] Buffer I/O error on device sr0, logical block 178716
[   15.797814] end_request: I/O error, dev sr0, sector 1429728
[   15.797817] Buffer I/O error on device sr0, logical block 178716
[   21.840053] end_request: I/O error, dev sr0, sector 1429728
[   21.840057] Buffer I/O error on device sr0, logical block 178716
[   22.444136] end_request: I/O error, dev sr0, sector 1429728
[   22.444139] Buffer I/O error on device sr0, logical block 178716
[   23.008286] end_request: I/O error, dev sr0, sector 1429728
[   23.008288] Buffer I/O error on device sr0, logical block 178716
[   23.570223] end_request: I/O error, dev sr0, sector 1429728
[   23.570282] Buffer I/O error on device sr0, logical block 178716
[   24.133537] end_request: I/O error, dev sr0, sector 1429728
[   24.133595] Buffer I/O error on device sr0, logical block 178716
[   24.729806] end_request: I/O error, dev sr0, sector 1429728
[   24.729864] Buffer I/O error on device sr0, logical block 178716
[   25.359514] end_request: I/O error, dev sr0, sector 1429728
[   25.359572] Buffer I/O error on device sr0, logical block 178716
[   26.162350] end_request: I/O error, dev sr0, sector 1429728
[   26.162409] Buffer I/O error on device sr0, logical block 178716
[   26.793932] end_request: I/O error, dev sr0, sector 1429728
[   26.793990] Buffer I/O error on device sr0, logical block 178716
[   27.764698] PM: Starting manual resume from disk
[   27.764700] PM: Resume from partition 8:18
[   27.764701] PM: Checking hibernation image.
[   27.764822] PM: Resume from disk failed.
[   27.794627] kjournald starting.  Commit interval 5 seconds
[   27.794638] EXT3-fs: mounted filesystem with writeback data mode.
[   32.559124] udevd version 124 started
[   32.670786] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   32.688518] ACPI: Power Button (FF) [PWRF]
[   32.688575] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   32.720519] ACPI: Power Button (CM) [PWRB]
[   32.975352] parport_pc 00:09: reported by Plug and Play ACPI
[   32.975378] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   32.993894] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.000756] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.015914] ACPI: I/O resource nForce2_smbus [0x1c00-0x1c3f] conflicts with ACPI region SM00 [0x1c00-0x1c05]
[   33.015916] ACPI: Device needs an ACPI driver
[   33.015940] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   33.015955] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   33.065132] nvidia: module license 'NVIDIA' taints kernel.
[   33.321475] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   33.321479] nvidia 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   33.321484] nvidia 0000:01:00.0: setting latency timer to 64
[   33.321600] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   33.463791] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   33.463798] rt61pci 0000:03:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   33.471055] phy0: Selected rate control algorithm 'pid'
[   33.491518] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   33.528092] Registered led device: rt61pci-phy0:radio
[   33.528105] Registered led device: rt61pci-phy0:assoc
[   33.614189] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   33.614195] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   33.614227] HDA Intel 0000:00:10.1: setting latency timer to 64
[   38.114622] end_request: I/O error, dev sr0, sector 1429728
[   38.114708] Buffer I/O error on device sr0, logical block 178716
[   38.682766] end_request: I/O error, dev sr0, sector 1429728
[   38.682836] Buffer I/O error on device sr0, logical block 178716
[   42.341954] end_request: I/O error, dev sr0, sector 1429728
[   42.342024] Buffer I/O error on device sr0, logical block 178716
[   42.912071] end_request: I/O error, dev sr0, sector 1429728
[   42.912141] Buffer I/O error on device sr0, logical block 178716
[   43.478286] end_request: I/O error, dev sr0, sector 1429728
[   43.478355] Buffer I/O error on device sr0, logical block 178716
[   44.008512] end_request: I/O error, dev sr0, sector 1429728
[   44.008582] Buffer I/O error on device sr0, logical block 178716
[   44.676899] end_request: I/O error, dev sr0, sector 1429728
[   44.676969] Buffer I/O error on device sr0, logical block 178716
[   45.414059] end_request: I/O error, dev sr0, sector 1429728
[   45.414129] Buffer I/O error on device sr0, logical block 178716
[   46.044544] end_request: I/O error, dev sr0, sector 1429728
[   46.044614] Buffer I/O error on device sr0, logical block 178716
[   47.535573] lp0: using parport0 (interrupt-driven).
[   48.247846] Adding 1951888k swap on /dev/sdb2.  Priority:-1 extents:1 across:1951888k
[   48.558838] EXT3 FS on sdb1, internal journal
[   49.068736] ip_tables: (C) 2000-2006 Netfilter Core Team
[   49.101511] firmware: requesting rt2561s.bin
[   49.892041] wlan0: authenticate with AP 08:10:73:0a:a1:3e
[   49.893393] wlan0: authenticated
[   49.893396] wlan0: associate with AP 08:10:73:0a:a1:3e
[   49.895610] wlan0: RX AssocResp from 08:10:73:0a:a1:3e (capab=0x411 status=0 aid=2)
[   49.895612] wlan0: associated
[   50.232540] NET: Registered protocol family 17
[   51.817373] ACPI: WMI: Mapper loaded
[   56.177115] warning: `pulseaudio' uses 32-bit capabilities (legacy support in use)
[   70.616998] UDF-fs: No VRS found
[   70.670442] ISO 9660 Extensions: Microsoft Joliet Level 3
[   70.824068] ISO 9660 Extensions: RRIP_1991A
[  106.966253] NET: Registered protocol family 10
[  106.966688] lo: Disabled Privacy Extensions
[  117.920007] wlan0: no IPv6 routers present
scott@scott-desktop:~$ 

```

it maybe i had a LiveCD in my CD-RW drive, but i've never know this before.

---

