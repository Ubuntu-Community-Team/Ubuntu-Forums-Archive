---
title: "Could not write bytes: broken pipe"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by rqr on 2013-05-26
Hello,
I cannot boot my computer and the "Could not write bytes: broken pipe" message appears.
Some information:
Computer: dell with nvidia. Ubuntu 12.04LTS 64 bits

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1f0c667f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400   de  Dell Utility
/dev/sda2   *      206848    30926847    15360000    7  HPFS/NTFS/exFAT
/dev/sda3        30926848   133326847    51200000    7  HPFS/NTFS/exFAT
/dev/sda4       133328894  1250263039   558467073    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1242357760  1250263039     3952640   82  Linux swap / Solaris
/dev/sda6       296554496  1242353663   472899584   83  Linux
/dev/sda7       133328896   296552447    81611776   83  Linux

Partition table entries are not in disk order

I've tried without any success.....

Through the recovery mode: Repair broken packages.

By Purging nvidia and re-installing it again

rm .Xauthoroty didn't work

I tried to use the nano editor (sudo nano -w) to delete a supossed failed var/lib/dpg/status and didn't know how....

At the moment,  I'm using this live-cd to try to solve this.

Thankyou.

---

### Post by prodigy_ on 2013-05-26
I saw "Could not write bytes: broken pipe" message on an 12.04 server that booted and worked perfectly. There's [a bug in Plymouth](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/521298) but it's supposed to be a cosmetic issue.

So there's a good chance this message has nothing to do with why your PC doesn't boot. You should mount the root partition from your installation while you're in Live environment and check if there's anything interesting in **/var/log/dmesg** or **/var/log/system** there.

---

### Post by rqr on 2013-05-26
Thanyou. Could you tell me step by step how to do it?

---

### Post by rqr on 2013-05-26
> **prodigy_ said:**
> I saw "Could not write bytes: broken pipe" message on an 12.04 server that booted and worked perfectly. There's [a bug in Plymouth]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/521298") but it's supposed to be a cosmetic issue.

So there's a good chance this message has nothing to do with why your PC doesn't boot. You should mount the root partition from your installation while you're in Live environment and check if there's anything interesting in **/var/log/dmesg** or **/var/log/system** there.

Finally I've done this:
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ ls /mnt
lost+found  rqsal
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ ls /mnt
bin                         initrd.img      mnt      srv
boot                        initrd.img.old  opt      sys
cdrom                       lib             proc     tmp
C:\nppdf32Log\debuglog.txt  lib32           root     usr
dev                         lib64           run      var
etc                         lost+found      sbin     vmlinuz
home                        media           selinux  vmlinuz.old

Does it help???

---

### Post by prodigy_ on 2013-05-26
Your installation appears to be on /dev/sda7. You need to go into var/log subfolder:
```
cd /mnt/var/log
```
and then check log files, say:
```
tail -200 dmesg # outputs last 200 lines, increase the number if needed
tail -200 syslog
```

See if you can find any obvious error messages. If unsure, post the output here but wrap in [code] tags because otherwise it's very annoying to read.

---

### Post by rqr on 2013-05-26
> **prodigy_ said:**
> I saw "Could not write bytes: broken pipe" message on an 12.04 server that booted and worked perfectly. There's [a bug in Plymouth]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/521298") but it's supposed to be a cosmetic issue.

So there's a good chance this message has nothing to do with why your PC doesn't boot. You should mount the root partition from your installation while you're in Live environment and check if there's anything interesting in **/var/log/dmesg** or **/var/log/system** there.

I've found this....
[    3.814414] VFS: Disk quotas dquot_6.5.2
[    3.814459] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.814848] fuse init (API version 7.17)
[    3.814915] msgmni has been set to 7715
[    3.815231] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.815258] io scheduler noop registered
[    3.815259] io scheduler deadline registered
[    3.815283] io scheduler cfq registered (default)
[    3.815365] pcieport 0000:00:01.0: setting latency timer to 64
[    3.815391] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    3.815445] pcieport 0000:00:1c.0: setting latency timer to 64
[    3.815486] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    3.815550] pcieport 0000:00:1c.1: setting latency timer to 64
[    3.815590] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    3.815667] pcieport 0000:00:1c.3: setting latency timer to 64
[    3.815707] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    3.815777] pcieport 0000:00:1c.4: setting latency timer to 64
[    3.815839] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    3.815938] pcieport 0000:00:1c.7: setting latency timer to 64
[    3.816002] pcieport 0000:00:1c.7: irq 45 for MSI/MSI-X
[    3.816114] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    3.816116] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    3.816118] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    3.816120] pcie_pme 0000:00:01.0cie01: service driver pcie_pme loaded
[    3.816137] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    3.816141] pcie_pme 0000:00:1c.0cie01: service driver pcie_pme loaded
[    3.816158] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    3.816160] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    3.816165] pcie_pme 0000:00:1c.1cie01: service driver pcie_pme loaded
[    3.816182] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    3.816184] pci 0000:09:00.0: Signaling PME through PCIe PME interrupt
[    3.816188] pcie_pme 0000:00:1c.3cie01: service driver pcie_pme loaded
[    3.816209] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    3.816211] pci 0000:0b:00.0: Signaling PME through PCIe PME interrupt
[    3.816216] pcie_pme 0000:00:1c.4cie01: service driver pcie_pme loaded
[    3.816236] pcieport 0000:00:1c.7: Signaling PME through PCIe PME interrupt
[    3.816241] pcie_pme 0000:00:1c.7cie01: service driver pcie_pme loaded
[    3.816253] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.816294] pciehp 0000:00:1c.7cie04: HPC vendor_id 8086 device_id 1c1e ss_vid 1028 ss_did 4b0
[    3.816314] pciehp 0000:00:1c.7cie04: service driver pciehp loaded
[    3.816322] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.816361] intel_idle: MWAIT substates: 0x21120
[    3.816363] intel_idle: v0.4 model 0x2A
[    3.816364] intel_idle: lapic_timer_reliable_states 0xffffffff
[    3.816437] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    3.816474] ACPI: AC Adapter [AC] (on-line)
[    3.816579] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    3.817912] ACPI: Lid Switch [LID0]
[    3.817945] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    3.817948] ACPI: Power Button [PWRB]
[    3.817977] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    3.817979] ACPI: Sleep Button [SBTN]
[    3.818007] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    3.818010] ACPI: Power Button [PWRF]
[    3.826347] thermal LNXTHERM:00: registered as thermal_zone0
[    3.826350] ACPI: Thermal Zone [THM] (74 C)
[    3.826369] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    3.826375] ACPI: Battery Slot [BAT0] (battery present)
[    3.826404] ERST: Table is not found!
[    3.826406] GHES: HEST is not enabled!
[    3.826485] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.895912] ACPI: Battery Slot [BAT0] (battery present)
[    4.027725] Linux agpgart interface v0.103
[    4.027797] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    4.027939] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    4.029132] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    4.029232] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    4.030299] brd: module loaded
[    4.030834] loop: module loaded
[    4.030932] ahci 0000:00:1f.2: version 3.0
[    4.030944] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.030986] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    4.031011] ahci: SSS flag set, parallel bus scan disabled
[    4.043354] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x31 impl SATA mode
[    4.043363] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    4.043375] ahci 0000:00:1f.2: setting latency timer to 64
[    4.059746] scsi0 : ahci
[    4.059827] scsi1 : ahci
[    4.059885] scsi2 : ahci
[    4.059943] scsi3 : ahci
[    4.060001] scsi4 : ahci
[    4.060056] scsi5 : ahci
[    4.060293] ata1: SATA max UDMA/133 abar m2048@0xf7b06000 port 0xf7b06100 irq 46
[    4.060295] ata2: DUMMY
[    4.060296] ata3: DUMMY
[    4.060297] ata4: DUMMY
[    4.060300] ata5: SATA max UDMA/133 abar m2048@0xf7b06000 port 0xf7b06300 irq 46
[    4.060303] ata6: SATA max UDMA/133 abar m2048@0xf7b06000 port 0xf7b06380 irq 46
[    4.060580] Fixed MDIO Bus: probed
[    4.060594] tun: Universal TUN/TAP device driver, 1.6
[    4.060595] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.060644] PPP generic driver version 2.4.2
[    4.060735] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.060750] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.060766] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.060770] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    4.060809] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.060833] ehci_hcd 0000:00:1a.0: debug port 2
[    4.064725] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    4.064739] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7b08000
[    4.079268] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    4.079450] hub 1-0:1.0: USB hub found
[    4.079454] hub 1-0:1.0: 2 ports detected
[    4.079504] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.079518] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.079521] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    4.079558] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.079578] ehci_hcd 0000:00:1d.0: debug port 2
[    4.083466] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    4.083479] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7b07000
[    4.099235] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    4.099409] hub 2-0:1.0: USB hub found
[    4.099412] hub 2-0:1.0: 2 ports detected
[    4.099463] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.099471] uhci_hcd: USB Universal Host Controller Interface driver
[    4.099502] xhci_hcd 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.099535] xhci_hcd 0000:0b:00.0: setting latency timer to 64
[    4.099539] xhci_hcd 0000:0b:00.0: xHCI Host Controller
[    4.099576] xhci_hcd 0000:0b:00.0: new USB bus registered, assigned bus number 3
[    4.099738] xhci_hcd 0000:0b:00.0: irq 16, io mem 0xf7900000
[    4.099806] xhci_hcd 0000:0b:00.0: irq 47 for MSI/MSI-X
[    4.099809] xhci_hcd 0000:0b:00.0: irq 48 for MSI/MSI-X
[    4.099812] xhci_hcd 0000:0b:00.0: irq 49 for MSI/MSI-X
[    4.099815] xhci_hcd 0000:0b:00.0: irq 50 for MSI/MSI-X
[    4.099819] xhci_hcd 0000:0b:00.0: irq 51 for MSI/MSI-X
[    4.099958] xHCI xhci_add_endpoint called for root hub
[    4.099960] xHCI xhci_check_bandwidth called for root hub
[    4.099979] hub 3-0:1.0: USB hub found
[    4.099989] hub 3-0:1.0: 2 ports detected
[    4.100031] xhci_hcd 0000:0b:00.0: xHCI Host Controller
[    4.100070] xhci_hcd 0000:0b:00.0: new USB bus registered, assigned bus number 4
[    4.100142] xHCI xhci_add_endpoint called for root hub
[    4.100144] xHCI xhci_check_bandwidth called for root hub
[    4.100163] hub 4-0:1.0: USB hub found
[    4.100172] hub 4-0:1.0: 2 ports detected
[    4.155227] usbcore: registered new interface driver libusual
[    4.155293] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13S2] at 0x60,0x64 irq 1,12
[    4.157398] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.157403] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.157507] mousedev: PS/2 mouse device common for all mice
[    4.157678] rtc_cmos 00:05: RTC can wake from S4
[    4.157782] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    4.157810] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    4.157868] device-mapper: uevent: version 1.0.3
[    4.157933] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    4.158032] cpuidle: using governor ladder
[    4.158176] cpuidle: using governor menu
[    4.158178] EFI Variables Facility v0.08 2004-May-17
[    4.158330] TCP cubic registered
[    4.158407] NET: Registered protocol family 10
[    4.158716] NET: Registered protocol family 17
[    4.158726] Registering the dns_resolver key type
[    4.158853] PM: Hibernation image not present or could not be loaded.
[    4.158862] registered taskstats version 1
[    4.171172]   Magic number: 13:790:930
[    4.171286] rtc_cmos 00:05: setting system clock to 2013-05-26 09:55:46 UTC (1369562146)
[    4.172013] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.172015] EDD information not available.
[    4.176819] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.378912] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.379726] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    4.390895] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    4.523472] hub 1-1:1.0: USB hub found
[    4.523668] hub 1-1:1.0: 6 ports detected
[    4.634535] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    4.760300] ata1.00: ATA-8: TOSHIBA MK6475GSX, GT002D, max UDMA/100
[    4.760310] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    4.761546] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    4.761842] ata1.00: configured for UDMA/100
[    4.762106] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6475GS GT00 PQ: 0 ANSI: 5
[    4.762281] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    4.762284] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    4.762306] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.762416] sd 0:0:0:0: [sda] Write Protect is off
[    4.762420] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.762452] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.766954] hub 2-1:1.0: USB hub found
[    4.767010] hub 2-1:1.0: 8 ports detected
[    4.770251] Refined TSC clocksource calibration: 2394.564 MHz.
[    4.770263] Switching to clocksource tsc
[    4.838297] usb 1-1.4: new full-speed USB device number 3 using ehci_hcd
[    4.844043]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    4.845160] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.006059] usb 1-1.5: new high-speed USB device number 4 using ehci_hcd
[    5.081855] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.084497] ata5.00: ATAPI: HL-DT-ST DVD+-RW GT50N, A101, max UDMA/133
[    5.087390] ata5.00: configured for UDMA/133
[    5.089241] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GT50N    A101 PQ: 0 ANSI: 5
[    5.091697] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.091706] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.091950] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    5.092084] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    5.409369] ata6: SATA link down (SStatus 0 SControl 300)
[    5.410598] Freeing unused kernel memory: 920k freed
[    5.410683] Write protecting the kernel read-only data: 12288k
[    5.414313] Freeing unused kernel memory: 1608k freed
[    5.417102] Freeing unused kernel memory: 1196k freed
[    5.431117] udevd[113]: starting version 175
[    5.452866] [drm] Initialized drm 1.1.0 20060810
[    5.456379] wmi: Mapper loaded
[    5.465053] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.465059] i915 0000:00:02.0: setting latency timer to 64
[    5.467397] MXM: GUID detected in BIOS
[    5.467735] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG0.PEGP handle
[    5.467761] nouveau 0000:01:00.0: power state changed by ACPI to D0
[    5.467765] nouveau 0000:01:00.0: power state changed by ACPI to D0
[    5.467769] nouveau 0000:01:00.0: enabling device (0006 -> 0007)
[    5.467776] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.467780] nouveau 0000:01:00.0: setting latency timer to 64
[    5.470118] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.470152] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.470470] r8169 0000:05:00.0: setting latency timer to 64
[    5.470542] r8169 0000:05:00.0: irq 52 for MSI/MSI-X
[    5.470920] r8169 0000:05:00.0: eth0: RTL8105e at 0xffffc90001074000, 18:03:73:a7:b5:b4, XID 00a00000 IRQ 52
[    5.532867] i915 0000:00:02.0: irq 53 for MSI/MSI-X
[    5.532872] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.532873] [drm] Driver supports precise vblank timestamp query.
[    5.533697] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[    5.533711] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    5.533713] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[    6.100163] fbcon: inteldrmfb (fb0) is primary device
[    6.469776] Console: switching to colour frame buffer device 170x48
[    6.471696] fb0: inteldrmfb frame buffer device
[    6.471697] drm: registered panic notifier
[    6.471861] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    6.472685] acpi device:1d: registered as cooling_device4
[    6.472872] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input5
[    6.472932] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    6.473601] acpi device:3c: registered as cooling_device5
[    6.473774] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
[    6.473816] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    6.473844] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    6.476400] [drm] nouveau 0000:01:00.0: Detected an NVc0 generation card (0x0c1a80a1)
[    6.483446] vga_switcheroo: enabled
[    6.483459] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[    6.493172] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[    6.493174] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PROM
[    6.493182] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[    6.493184] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PCIROM
[    6.503016] nouveau 0000:01:00.0: Invalid ROM contents
[    6.503084] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[    6.503085] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from ACPI
[    6.696203] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    6.696207] [drm] nouveau 0000:01:00.0: BIT BIOS found
[    6.696209] [drm] nouveau 0000:01:00.0: Bios version 70.08.56.00
[    6.696213] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[    6.696215] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[    6.696217] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02011300 00000000
[    6.696219] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02022362 00020010
[    6.696221] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 0000000e 00000000
[    6.696223] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[    6.696225] [drm] nouveau 0000:01:00.0:   0: 0x00000040: type 0x40 idx 0 tag 0xff
[    6.696227] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[    6.696229] [drm] nouveau 0000:01:00.0:   2: 0x00001261: type 0x61 idx 2 tag 0x07
[    6.696243] [drm] nouveau 0000:01:00.0: Adaptor not initialised, running VBIOS init tables.
[    6.696245] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD5E7
[    6.720240] [drm] nouveau 0000:01:00.0: 0xD591: i2c wr fail: -6
[    6.760213] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xDC43
[    6.787027] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xEE49
[    6.787032] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xEE4D
[    6.787083] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEF35
[    6.787084] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xEF9A
[    6.825575] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
[    6.825577] [drm] nouveau 0000:01:00.0: 0: core 50MHz shader 101MHz memory 135MHz timing 0 voltage 850mV
[    6.825580] [drm] nouveau 0000:01:00.0: 1: core 202MHz shader 405MHz memory 324MHz timing 1 voltage 850mV
[    6.825582] [drm] nouveau 0000:01:00.0: 3: core 600MHz shader 1200MHz memory 900MHz timing 2 voltage 950mV
[    6.825651] [drm] nouveau 0000:01:00.0: c: core 202MHz shader 405MHz memory 324MHz voltage 950mV
[    6.827922] [TTM] Zone  kernel: Available graphics memory: 1976942 kiB.
[    6.827924] [TTM] Initializing pool allocator.
[    6.827932] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
[    6.829822] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[    6.834867] [drm] nouveau 0000:01:00.0: ACPI backlight interface available, not registering our own
[    6.864428] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    6.864430] [drm] No driver support for vblank timestamp query.
[    6.917678] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x1a0000, bo ffff880127c3f800
[    6.917809] fb1: nouveaufb frame buffer device
[    6.917814] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 1
[   12.012676] Btrfs loaded
[   12.016379] xor: automatically using best checksumming function: generic_sse
[   12.035403]    generic_sse: 13328.000 MB/sec
[   12.035405] xor: using function: generic_sse (13328.000 MB/sec)
[   12.035791] device-mapper: dm-raid45: initialized v0.2594b
[   13.386153] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   13.562510] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   14.255911] ISO 9660 Extensions: Microsoft Joliet Level 3
[   14.276631] ISO 9660 Extensions: RRIP_1991A
[   14.954817] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   77.702621] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.573191] udevd[1362]: starting version 175
[   78.714540] Adding 3952636k swap on /dev/sda5.  Priority:-1 extents:1 across:3952636k 
[   87.950969] device-mapper: multipath: version 1.3.0 loaded
[   88.676636] Bluetooth: Core ver 2.16
[   88.676664] NET: Registered protocol family 31
[   88.676666] Bluetooth: HCI device and connection manager initialized
[   88.676669] Bluetooth: HCI socket layer initialized
[   88.676671] Bluetooth: L2CAP socket layer initialized
[   88.676677] Bluetooth: SCO socket layer initialized
[   89.211299] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   89.692390] Bluetooth: RFCOMM TTY layer initialized
[   89.692396] Bluetooth: RFCOMM socket layer initialized
[   89.692398] Bluetooth: RFCOMM ver 1.11
[   90.044703] init: failsafe main process (1565) killed by TERM signal
[   90.283900] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   90.284256] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   90.284264] mei 0000:00:16.0: setting latency timer to 64
[   90.284328] mei 0000:00:16.0: irq 54 for MSI/MSI-X
[   91.408452] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input7
[   91.463145] cfg80211: Calling CRDA to update world regulatory domain
[   91.668761] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   91.668954] usbcore: registered new interface driver btusb
[   91.670899] lp: driver loaded but no devices found
[   91.808003] Linux video capture interface: v2.00
[   92.382367] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   92.626227] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   92.626230] Bluetooth: BNEP filters: protocol multicast
[   92.628533] ppdev: user-space parallel port driver
[   92.727340] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (0c45:6483)
[   92.993308] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input9
[   92.993403] usbcore: registered new interface driver uvcvideo
[   92.993413] USB Video Class driver (1.1.1)
[   93.680548] cfg80211: World regulatory domain updated:
[   93.680552] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   93.680555] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.680558] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   93.680561] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   93.680563] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.680566] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   95.837508] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   95.837512] Copyright(c) 2003-2011 Intel Corporation
[   95.837608] iwlwifi 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   95.837617] iwlwifi 0000:09:00.0: setting latency timer to 64
[   95.837647] iwlwifi 0000:09:00.0: pci_resource_len = 0x00002000
[   95.837649] iwlwifi 0000:09:00.0: pci_resource_base = ffffc9000117c000
[   95.837651] iwlwifi 0000:09:00.0: HW Revision ID = 0x34
[   95.837734] iwlwifi 0000:09:00.0: irq 55 for MSI/MSI-X
[   95.837773] iwlwifi 0000:09:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   95.837837] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   95.853369] iwlwifi 0000:09:00.0: device EEPROM VER=0x71a, CALIB=0x6
[   95.853371] iwlwifi 0000:09:00.0: Device SKU: 0X150
[   95.853373] iwlwifi 0000:09:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   95.853385] iwlwifi 0000:09:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   99.358660] iwlwifi 0000:09:00.0: loaded firmware version 18.168.6.1
[   99.358896] Registered led device: phy0-led
[   99.358926] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  100.786598] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  100.786655] snd_hda_intel 0000:00:1b.0: irq 56 for MSI/MSI-X
[  100.786679] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[  100.787552] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  102.078886] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[  102.078957] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[  102.079126] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  102.079129] hda_intel: Disabling MSI
[  102.079186] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[  103.924205] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[  103.946874] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[  103.970650] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[  103.994742] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[  103.994863] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[  103.995028] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[  103.995117] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[  103.995196] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[  106.094381] r8169 0000:05:00.0: eth0: link down
[  106.094387] r8169 0000:05:00.0: eth0: link down
[  106.094654] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  106.094969] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  106.096569] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[  106.103277] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[  106.188666] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[  106.195366] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[  106.270482] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  106.270907] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  107.783714] r8169 0000:05:00.0: eth0: link up
[  107.784032] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  112.760874] init: alsa-restore main process (1834) terminated with status 99
[17595.480693] EXT4-fs (sda6): warning: maximal mount count reached, running e2fsck is recommended
[17595.495158] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[17669.929997] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)

---

### Post by prodigy_ on 2013-05-26
Well, your dmesg log looks fine. Could you post syslog as well? And what exactly happened during boot after that "broken pipe" warning? Did you get logon prompt? Blinking cursor? Blank screen?

---

### Post by rqr on 2013-05-26
> **prodigy_ said:**
> Your installation appears to be on /dev/sda7. You need to go into var/log subfolder:
```
cd /mnt/var/log
```
and then check log files, say:
```
tail -200 dmesg # outputs last 200 lines, increase the number if needed
tail -200 syslog
```

See if you can find any obvious error messages. If unsure, post the output here but wrap in [code] tags because otherwise it's very annoying to read.

Hi, I've found this cuts....

  	 	 	 	   

   1.327903] PM: Hibernation image not present or could not be loaded. 
 [    1.327913] registered taskstats version 1 
 [    1.334327]   Magic number: 13:687:829 
 [    1.334431] rtc_cmos 00:05: setting system clock to 2013-05-26 09:50:48 UTC (1369561848) 
 [    1.335139] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
 [    1.335140] EDD information not available. 
 [    1.341309] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
 [    1.567461] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
 [    1.568282] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04) 
 [    1.579444] usb 1-1: new high-speed USB device number 2 using ehci_hcd 
 

 (….................................................)
 

  15.545707] usbcore: registered new interface driver uvcvideo 
 [   15.545710] USB Video Class driver (1.1.1) 
 [   15.564181] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro 
 [   15.842212] fbcon: inteldrmfb (fb0) is primary device 
 [   15.842268] Console: switching to colour frame buffer device 170x48 
 [   15.842285] fb0: inteldrmfb frame buffer device 
 [   15.842286] drm: registered panic notifier 
 [   15.842505] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS 
 [   15.881699] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input7 
 

 (…...................................................)
 

 

 I don't know if this information would be enough and I don't know how to wrap the information in codes, as you said before. I'm Sorry, I am a real absolute beginner

---

### Post by rqr on 2013-05-26
> **prodigy_ said:**
> Well, your dmesg log looks fine. Could you post syslog as well? And what exactly happened during boot after that "broken pipe" warning? Did you get logon prompt? Blinking cursor? Blank screen?

How shall I extract the syslog?

After that broken pipe stuff nothing happens, and I cannot do anything apart from entering by pressing ctrl Alt F1 buttons.

---

### Post by prodigy_ on 2013-05-26
Well, if you see command line logon prompt then most probably it's a video driver issue and most probably the issue was caused by a kernel update.

D/l the [latest nVidia driver](http://www.nvidia.com/object/linux-display-amd64-319.23-driver.html), put it somewhere on sda7, reboot to your installation, navigate to the folder where you put the script and run the script: ```
sudo sh ./NVIDIA-Linux-x86_64-319.23.run
```
Follow the instructions and reboot again when the installation is complete.

---

### Post by rqr on 2013-05-26
> **prodigy_ said:**
> Well, if you see command line logon prompt then most probably it's a video driver issue and most probably the issue was caused by a kernel update.

D/l the [latest nVidia driver]("http://www.nvidia.com/object/linux-display-amd64-319.23-driver.html"), put it somewhere on sda7, reboot to your installation, navigate to the folder where you put the script and run the script: ```
sudo sh ./NVIDIA-Linux-x86_64-319.23.run
```
Follow the instructions and reboot again when the installation is complete.

I cannot paste the file in sda7. I've tried to do it directly, copying the file from folder in live cd where nvidia was downloaded and by pasting it in the mention partition, but I wasn't allowed to do it
 Could you tell me how I could do?
Thanks

---

### Post by prodigy_ on 2013-05-26
Not even with [sudo](https://help.ubuntu.com/community/RootSudo)? Please post your command and the error message you get.

---

### Post by rqr on 2013-05-26
> **prodigy_ said:**
> Not even with [sudo]("https://help.ubuntu.com/community/RootSudo")? Please post your command and the error message you get.

Sorry, this is too much for me. As I wrote before, I'm an absolute beginner. I need you to tell me step by step  absolutely everything.

I haven't got an error message when trying to put the nvidia driver within the sda7. I didn't use the command way, I don't know how....

---

### Post by rqr on 2013-05-26
> **prodigy_ said:**
> Not even with [sudo]("https://help.ubuntu.com/community/RootSudo")? Please post your command and the error message you get.

root@ubuntu:~# sudo mount /dev/sda7 /media/disk 
root@ubuntu:~# sudo sh ./NVIDIA-Linux-x86_64-319.23.run
sh: 0: Can't open ./NVIDIA-Linux-x86_64-319.23.run
root@ubuntu:~#

---

### Post by prodigy_ on 2013-05-26
> **rqr said:**
> root@ubuntu:~# sudo sh ./NVIDIA-Linux-x86_64-319.23.run
That's the command to run the script.

> **rqr said:**
> I need you to tell me step by step absolutely everything.
Let's try.

From Live environment:
```

sudo -i
mount /dev/sda7 /media/disk
updatedb
cp "$(locate NVIDIA-Linux-x86_64-319.23.run)" /media/disk/root/
reboot
```

Reboot to your Ubuntu installation and log on (to a command line console) with your user name and password.

From your Ubuntu installation:
```
sudo -i # enter your password when prompted
sh ./NVIDIA-Linux-x86_64-319.23.run
reboot
```

---

### Post by rqr on 2013-05-27
> **prodigy_ said:**
> That's the command to run the script.


Let's try.

From Live environment:
```

sudo -i
mount /dev/sda7 /media/disk
updatedb
cp "$(locate NVIDIA-Linux-x86_64-319.23.run)" /media/disk/root/
reboot
```

Reboot to your Ubuntu installation and log on (to a command line console) with your user name and password.

From your Ubuntu installation:
```
sudo -i # enter your password when prompted
sh ./NVIDIA-Linux-x86_64-319.23.run
reboot
```

Thank you. But something does not work

I have done this....

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda7 /media/disk 
mount: mount point /media/disk does not exist

---

