---
title: "[SOLVED] Login twice!"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by jspolen on 2008-06-24
For some reason I need to log in twice on my computer now, (Ubuntu 8.04 Hardy Heron) The login page appears, I write my username and password (correct I might add) 

Then it looks like I'm on my way in, but instead it shows me some cryptic startup messages which are always shown when booting up. And now I have to login again????

Has anyone had this problem, or heard of it?

Also my computer shut downs now and then, for no reason it just stops. This may be hardware related though.

---

### Post by ukripper on 2008-06-24
> **jspolen said:**
> For some reason I need to log in twice on my computer now, (Ubuntu 8.04 Hardy Heron) The login page appears, I write my username and password (correct I might add) 

Then it looks like I'm on my way in, but instead it shows me some cryptic startup messages which are always shown when booting up. And now I have to login again????

Has anyone had this problem, or heard of it?

Also my computer shut downs now and then, for no reason it just stops. This may be hardware related though.

can you post output of the follwoign:
```
cat /var/log/messages
```

and ```
dmesg | tail
```

---

### Post by jspolen on 2008-06-24
```
Jun 24 13:10:07 laptop-joelbi kernel: [   17.041188] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
Jun 24 13:10:07 laptop-joelbi kernel: [   17.042037] scsi2 : pata_atiixp
Jun 24 13:10:07 laptop-joelbi kernel: [   17.042634] scsi3 : pata_atiixp
Jun 24 13:10:07 laptop-joelbi kernel: [   17.043476] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
Jun 24 13:10:07 laptop-joelbi kernel: [   17.043481] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
Jun 24 13:10:07 laptop-joelbi kernel: [   17.064857] usb 2-2: USB disconnect, address 2
Jun 24 13:10:07 laptop-joelbi kernel: [   17.205551] ata3.00: ATA-6: ST980811A, 3.ALA, max UDMA/100
Jun 24 13:10:07 laptop-joelbi kernel: [   17.205556] ata3.00: 156301488 sectors, multi 16: LBA48 
Jun 24 13:10:07 laptop-joelbi kernel: [   17.221476] ata3.00: configured for UDMA/100
Jun 24 13:10:07 laptop-joelbi kernel: [   17.541278] ata4.00: ATAPI: Optiarc DVD RW AD-5540A, 2.61, max UDMA/33
Jun 24 13:10:07 laptop-joelbi kernel: [   17.541296] ata4.00: simplex DMA is claimed by other device, disabling DMA
Jun 24 13:10:07 laptop-joelbi kernel: [   17.616671] usb 3-6: new high speed USB device using ehci_hcd and address 3
Jun 24 13:10:07 laptop-joelbi kernel: [   17.713266] ata4.00: configured for PIO4
Jun 24 13:10:07 laptop-joelbi kernel: [   17.713410] scsi 2:0:0:0: Direct-Access     ATA      ST980811A        3.AL PQ: 0 ANSI: 5
Jun 24 13:10:07 laptop-joelbi kernel: [   17.714981] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-5540A  2.61 PQ: 0 ANSI: 5
Jun 24 13:10:07 laptop-joelbi kernel: [   17.722027] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 19 (level, low) -> IRQ 18
Jun 24 13:10:07 laptop-joelbi kernel: [   17.723322] eth0: RealTek RTL8139 at 0xcf00, 00:40:d0:a0:a8:fa, IRQ 18
Jun 24 13:10:07 laptop-joelbi kernel: [   17.725518] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 24 13:10:07 laptop-joelbi kernel: [   17.725523] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 24 13:10:07 laptop-joelbi kernel: [   17.730795] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jun 24 13:10:07 laptop-joelbi kernel: [   17.743204] Driver 'sd' needs updating - please use bus_type methods
Jun 24 13:10:07 laptop-joelbi kernel: [   17.743315] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jun 24 13:10:07 laptop-joelbi kernel: [   17.743332] sd 2:0:0:0: [sda] Write Protect is off
Jun 24 13:10:07 laptop-joelbi kernel: [   17.743354] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 13:10:07 laptop-joelbi kernel: [   17.743413] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jun 24 13:10:07 laptop-joelbi kernel: [   17.743425] sd 2:0:0:0: [sda] Write Protect is off
Jun 24 13:10:07 laptop-joelbi kernel: [   17.743446] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 13:10:07 laptop-joelbi kernel: [   17.743450]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jun 24 13:10:07 laptop-joelbi kernel: [   17.760931]  sda1 sda2 < sda5 >
Jun 24 13:10:07 laptop-joelbi kernel: [   17.791780] sd 2:0:0:0: [sda] Attached SCSI disk
Jun 24 13:10:07 laptop-joelbi kernel: [   17.801729] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jun 24 13:10:07 laptop-joelbi kernel: [   17.801753] sr 3:0:0:0: Attached scsi generic sg1 type 5
Jun 24 13:10:07 laptop-joelbi kernel: [   17.803202] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jun 24 13:10:07 laptop-joelbi kernel: [   17.803208] Uniform CD-ROM driver Revision: 3.20
Jun 24 13:10:07 laptop-joelbi kernel: [   17.929110] usb 3-6: configuration #1 chosen from 1 choice
Jun 24 13:10:07 laptop-joelbi kernel: [   17.960207] usbcore: registered new interface driver hiddev
Jun 24 13:10:07 laptop-joelbi kernel: [   18.128831] Attempting manual resume
Jun 24 13:10:07 laptop-joelbi kernel: [   18.178456] kjournald starting.  Commit interval 5 seconds
Jun 24 13:10:07 laptop-joelbi kernel: [   18.178470] EXT3-fs: mounted filesystem with ordered data mode.
Jun 24 13:10:07 laptop-joelbi kernel: [   18.260512] usb 2-2: new low speed USB device using ohci_hcd and address 3
Jun 24 13:10:07 laptop-joelbi kernel: [   18.465498] usb 2-2: configuration #1 chosen from 1 choice
Jun 24 13:10:07 laptop-joelbi kernel: [   18.472704] input: USB Mouse as /devices/pci0000:00/0000:00:13.1/usb2/2-2/2-2:1.0/input/input2
Jun 24 13:10:07 laptop-joelbi kernel: [   18.484488] input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:13.1-2
Jun 24 13:10:07 laptop-joelbi kernel: [   18.484504] usbcore: registered new interface driver usbhid
Jun 24 13:10:07 laptop-joelbi kernel: [   18.484508] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jun 24 13:10:07 laptop-joelbi kernel: [   29.901683] Linux agpgart interface v0.102
Jun 24 13:10:07 laptop-joelbi kernel: [   30.065679] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 24 13:10:07 laptop-joelbi kernel: [   30.133537] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 24 13:10:07 laptop-joelbi kernel: [   30.389658] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jun 24 13:10:07 laptop-joelbi kernel: [   30.838987] input: Power Button (FF) as /devices/virtual/input/input3
Jun 24 13:10:07 laptop-joelbi kernel: [   30.849416] ACPI: Power Button (FF) [PWRF]
Jun 24 13:10:07 laptop-joelbi kernel: [   30.849551] input: Power Button (CM) as /devices/virtual/input/input4
Jun 24 13:10:07 laptop-joelbi kernel: [   30.865400] ACPI: Power Button (CM) [PWRB]
Jun 24 13:10:07 laptop-joelbi kernel: [   30.865499] input: Lid Switch as /devices/virtual/input/input5
Jun 24 13:10:07 laptop-joelbi kernel: [   30.867808] ACPI: Lid Switch [LID]
Jun 24 13:10:07 laptop-joelbi kernel: [   30.867883] input: Sleep Button (CM) as /devices/virtual/input/input6
Jun 24 13:10:07 laptop-joelbi kernel: [   30.877397] ACPI: Sleep Button (CM) [SBTN]
Jun 24 13:10:07 laptop-joelbi kernel: [   31.041530] ACPI: AC Adapter [AC] (on-line)
Jun 24 13:10:07 laptop-joelbi kernel: [   31.374703] ACPI: Battery Slot [BAT0] (battery present)
Jun 24 13:10:07 laptop-joelbi kernel: [   31.545515] input: PC Speaker as /devices/platform/pcspkr/input/input7
Jun 24 13:10:07 laptop-joelbi kernel: [   31.623112] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jun 24 13:10:07 laptop-joelbi kernel: [   31.889194] [fglrx] Maximum main memory to use for locked dma buffers: 866 MBytes.
Jun 24 13:10:07 laptop-joelbi kernel: [   31.889244] [fglrx] ASYNCIO init succeed!
Jun 24 13:10:07 laptop-joelbi kernel: [   31.889610] [fglrx] PAT is enabled successfully!
Jun 24 13:10:07 laptop-joelbi kernel: [   31.891461] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Jun 24 13:10:07 laptop-joelbi kernel: [   32.992241] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
Jun 24 13:10:07 laptop-joelbi kernel: [   34.509159] usbcore: registered new interface driver rt2500usb
Jun 24 13:10:07 laptop-joelbi kernel: [   34.610872] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x3aa0b4, caps: 0xa04713/0x200000
Jun 24 13:10:07 laptop-joelbi kernel: [   34.654845] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Jun 24 13:10:07 laptop-joelbi kernel: [   34.946562] usbcore: registered new interface driver rt73usb
Jun 24 13:10:07 laptop-joelbi kernel: [   37.051794] lp: driver loaded but no devices found
Jun 24 13:10:07 laptop-joelbi kernel: [   37.342880] Adding 2843464k swap on /dev/sda5.  Priority:-1 extents:1 across:2843464k
Jun 24 13:10:07 laptop-joelbi kernel: [   37.899600] EXT3 FS on sda1, internal journal
Jun 24 13:10:07 laptop-joelbi kernel: [   39.601864] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 24 13:10:07 laptop-joelbi kernel: [   40.154184] No dock devices found.
Jun 24 13:10:07 laptop-joelbi kernel: [   41.500805] apm: BIOS not found.
Jun 24 13:10:07 laptop-joelbi kernel: [   41.766790] ppdev: user-space parallel port driver
Jun 24 13:10:08 laptop-joelbi kernel: [   41.897883] audit(1214305808.075:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4830 profile="/usr/sbin/cupsd" namespace="default"
Jun 24 13:10:08 laptop-joelbi dhcdbd: Started up.
Jun 24 13:10:09 laptop-joelbi kernel: [   42.880616] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 24 13:10:09 laptop-joelbi kernel: [   43.178673] Bluetooth: Core ver 2.11
Jun 24 13:10:09 laptop-joelbi kernel: [   43.179478] NET: Registered protocol family 31
Jun 24 13:10:09 laptop-joelbi kernel: [   43.179482] Bluetooth: HCI device and connection manager initialized
Jun 24 13:10:09 laptop-joelbi kernel: [   43.179487] Bluetooth: HCI socket layer initialized
Jun 24 13:10:09 laptop-joelbi kernel: [   43.246394] Bluetooth: L2CAP ver 2.9
Jun 24 13:10:09 laptop-joelbi kernel: [   43.246400] Bluetooth: L2CAP socket layer initialized
Jun 24 13:10:09 laptop-joelbi kernel: [   43.286361] Bluetooth: RFCOMM socket layer initialized
Jun 24 13:10:09 laptop-joelbi kernel: [   43.286381] Bluetooth: RFCOMM TTY layer initialized
Jun 24 13:10:09 laptop-joelbi kernel: [   43.286384] Bluetooth: RFCOMM ver 1.8
Jun 24 13:10:10 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 24 13:10:11 laptop-joelbi kernel: [   45.462681] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 19
Jun 24 13:10:13 laptop-joelbi kernel: [   46.829513] NET: Registered protocol family 17
Jun 24 13:10:13 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun 24 13:10:13 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun 24 13:10:13 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 24 13:10:13 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 24 13:10:13 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun 24 13:10:13 laptop-joelbi kernel: [   47.390328] [fglrx] GART Table is not in FRAME_BUFFER range 
Jun 24 13:10:13 laptop-joelbi kernel: [   47.390344] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Jun 24 13:10:13 laptop-joelbi kernel: [   47.390347] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
Jun 24 13:10:13 laptop-joelbi kernel: [   47.564207] [fglrx] interrupt source 10000000 successfully enabled
Jun 24 13:10:13 laptop-joelbi kernel: [   47.564216] [fglrx] enable ID = 0x00000004
Jun 24 13:10:13 laptop-joelbi kernel: [   47.564561] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Jun 24 13:10:15 laptop-joelbi kernel: [   48.942391] NET: Registered protocol family 10
Jun 24 13:10:15 laptop-joelbi kernel: [   48.942923] lo: Disabled Privacy Extensions
Jun 24 13:10:15 laptop-joelbi kernel: [   48.944044] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 24 13:13:47 laptop-joelbi kernel: [  261.146558] [fglrx] interrupt source 10000000 successfully disabled!
Jun 24 13:13:47 laptop-joelbi kernel: [  261.146566] [fglrx] enable ID = 0x00000000
Jun 24 13:13:47 laptop-joelbi kernel: [  261.146570] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000004
Jun 24 13:13:50 laptop-joelbi kernel: [  264.537602] [fglrx] PCIe has already been initialized. Reinitializing ...
Jun 24 13:13:50 laptop-joelbi kernel: [  264.557738] [fglrx] GART Table is not in FRAME_BUFFER range 
Jun 24 13:13:50 laptop-joelbi kernel: [  264.557754] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Jun 24 13:13:50 laptop-joelbi kernel: [  264.557757] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
Jun 24 13:13:50 laptop-joelbi kernel: [  264.713835] [fglrx] interrupt source 10000000 successfully enabled
Jun 24 13:13:50 laptop-joelbi kernel: [  264.713846] [fglrx] enable ID = 0x00000004
Jun 24 13:13:50 laptop-joelbi kernel: [  264.714216] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Jun 24 13:14:24 laptop-joelbi kernel: [  298.760952] hda-intel: Invalid position buffer, using LPIB read method instead.
Jun 24 13:19:53 laptop-joelbi syslogd 1.5.0#1ubuntu1: restart.
Jun 24 13:30:06 laptop-joelbi -- MARK --
Jun 24 13:50:06 laptop-joelbi -- MARK --
Jun 24 14:10:06 laptop-joelbi -- MARK --
Jun 24 14:19:56 laptop-joelbi syslogd 1.5.0#1ubuntu1: restart.
Jun 24 14:19:56 laptop-joelbi kernel: Inspecting /boot/System.map-2.6.24-18-generic
Jun 24 14:19:56 laptop-joelbi kernel: Loaded 27880 symbols from /boot/System.map-2.6.24-18-generic.
Jun 24 14:19:56 laptop-joelbi kernel: Symbols match kernel version 2.6.24.
Jun 24 14:19:56 laptop-joelbi kernel: Loaded 23051 symbols from 93 modules.
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003bff0000 (usable)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]  BIOS-e820: 000000003bff0000 - 000000003bffffc0 (ACPI data)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]  BIOS-e820: 000000003bffffc0 - 000000003c000000 (ACPI NVS)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] 63MB HIGHMEM available.
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] 896MB LOWMEM available.
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Zone PFN ranges:
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]   DMA             0 ->     4096
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]   Normal       4096 ->   229376
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]   HighMem    229376 ->   245744
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Movable zone start PFN for each node
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] early_node_map[1] active PFN ranges
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000]     0:        0 ->   245744
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] DMI 2.3 present.
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: RSDP signature @ 0xC00E6010 checksum 0
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: RSDP 000E6010, 0014 (r0 OID_00)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: RSDT 3BFFC910, 0030 (r1 INSYDE RSDT_000        1 0000    10200)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: FACP 3BFFFAC0, 0074 (r1 INSYDE FACP_000      100 0000    10200)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: DSDT 3BFFC950, 316D (r1 INSYDE   Avani2     1004 INTL  2002036)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: FACS 3BFFFFC0, 0040
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: APIC 3BFFFB50, 0068 (r1 INSYDE APIC_000 30303030 0000    10200)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: MCFG 3BFFFBC0, 003C (r1 INSYDE MCFG_000 30303030 0000 30303030)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Processor #0 6:14 APIC version 20
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 3c000000:c3f80000)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243825
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Kernel command line: root=UUID=c650b068-797b-4799-85d5-c3391c7a7a20 ro quiet splash
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Initializing CPU#0
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun 24 14:19:56 laptop-joelbi kernel: [    0.000000] Detected 1466.703 MHz processor.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.007048] Console: colour VGA+ 80x25
Jun 24 14:19:56 laptop-joelbi kernel: [   12.007054] console [tty0] enabled
Jun 24 14:19:56 laptop-joelbi kernel: [   12.008078] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.008855] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040345] Memory: 962440k/982976k available (2176k kernel code, 19940k reserved, 1006k data, 368k init, 65472k highmem)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040354] virtual kernel memory layout:
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040356]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040357]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040359]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040360]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040362]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040363]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040365]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040369] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.040413] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120425] Calibrating delay using timer specific routine.. 2936.93 BogoMIPS (lpj=5873876)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120455] Security Framework initialized
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120465] SELinux:  Disabled at boot.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120482] AppArmor: AppArmor initialized
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120487] Failure registering capabilities with primary security module.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120496] Mount-cache hash table entries: 512
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120644] Initializing cgroup subsys ns
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120652] Initializing cgroup subsys cpuacct
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120675] monitor/mwait feature present.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120677] using mwait in idle threads.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120682] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120685] CPU: L2 cache: 1024K
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120701] Compat vDSO mapped to ffffe000.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.120718] Checking 'hlt' instruction... OK.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.136911] SMP alternatives: switching to UP code
Jun 24 14:19:56 laptop-joelbi kernel: [   12.139023] Freeing SMP alternatives: 11k freed
Jun 24 14:19:56 laptop-joelbi kernel: [   12.139160] Early unpacking initramfs... done
Jun 24 14:19:56 laptop-joelbi kernel: [   12.553696] ACPI: Core revision 20070126
Jun 24 14:19:56 laptop-joelbi kernel: [   12.553757] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.610503] CPU0: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
Jun 24 14:19:56 laptop-joelbi kernel: [   12.610532] Total of 1 processors activated (2936.93 BogoMIPS).
Jun 24 14:19:56 laptop-joelbi kernel: [   12.610710] ENABLING IO-APIC IRQs
Jun 24 14:19:56 laptop-joelbi kernel: [   12.610925] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 24 14:19:56 laptop-joelbi kernel: [   12.650708] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.650712] ...trying to set up timer as Virtual Wire IRQ... works.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.796343] Brought up 1 CPUs
Jun 24 14:19:56 laptop-joelbi kernel: [   12.796565] net_namespace: 64 bytes
Jun 24 14:19:56 laptop-joelbi kernel: [   12.796576] Booting paravirtualized kernel on bare hardware
Jun 24 14:19:56 laptop-joelbi kernel: [   12.797114] Time: 12:19:25  Date: 06/24/08
Jun 24 14:19:56 laptop-joelbi kernel: [   12.797142] NET: Registered protocol family 16
Jun 24 14:19:56 laptop-joelbi kernel: [   12.797373] EISA bus registered
Jun 24 14:19:56 laptop-joelbi kernel: [   12.797404] ACPI: bus type pci registered
Jun 24 14:19:56 laptop-joelbi kernel: [   12.797558] PCI: PCI BIOS revision 2.10 entry at 0xe9dc4, last bus=2
Jun 24 14:19:56 laptop-joelbi kernel: [   12.797561] PCI: Using configuration type 1
Jun 24 14:19:56 laptop-joelbi kernel: [   12.797563] Setting up standard PCI resources
Jun 24 14:19:56 laptop-joelbi kernel: [   12.801633] ACPI: Interpreter enabled
Jun 24 14:19:56 laptop-joelbi kernel: [   12.801636] ACPI: (supports S0 S3 S4 S5)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.801651] ACPI: Using IOAPIC for interrupt routing
Jun 24 14:19:56 laptop-joelbi kernel: [   12.806415] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 24 14:19:56 laptop-joelbi kernel: [   12.813545] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
Jun 24 14:19:56 laptop-joelbi kernel: [   12.813548] ACPI: EC: driver started in interrupt mode
Jun 24 14:19:56 laptop-joelbi kernel: [   12.813591] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 24 14:19:56 laptop-joelbi kernel: [   12.814899] PCI: Transparent bridge - 0000:00:14.4
Jun 24 14:19:56 laptop-joelbi kernel: [   12.819172] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 9 10 11) *0, disabled.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.819282] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 9 10 11) *0, disabled.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.819389] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 9 10 11) *0, disabled.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.819495] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.819601] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 7 9 10 11) *0, disabled.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.819707] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 7 9 10 11) *0, disabled.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.819813] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.819918] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.820041] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 24 14:19:56 laptop-joelbi kernel: [   12.820079] pnp: PnP ACPI init
Jun 24 14:19:56 laptop-joelbi kernel: [   12.820087] ACPI: bus type pnp registered
Jun 24 14:19:56 laptop-joelbi kernel: [   12.823860] pnp: PnP ACPI: found 9 devices
Jun 24 14:19:56 laptop-joelbi kernel: [   12.823863] ACPI: ACPI bus type pnp unregistered
Jun 24 14:19:56 laptop-joelbi kernel: [   12.823869] PnPBIOS: Disabled by ACPI PNP
Jun 24 14:19:56 laptop-joelbi kernel: [   12.824130] PCI: Using ACPI for IRQ routing
Jun 24 14:19:56 laptop-joelbi kernel: [   12.824133] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 24 14:19:56 laptop-joelbi kernel: [   12.824143] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Jun 24 14:19:56 laptop-joelbi kernel: [   12.832330] NET: Registered protocol family 8
Jun 24 14:19:56 laptop-joelbi kernel: [   12.832332] NET: Registered protocol family 20
Jun 24 14:19:56 laptop-joelbi kernel: [   12.832408] AppArmor: AppArmor Filesystem Enabled
Jun 24 14:19:56 laptop-joelbi kernel: [   12.836287] Time: tsc clocksource has been installed.
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844331] system 00:07: ioport range 0xc6c-0xc6c has been reserved
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844334] system 00:07: ioport range 0xcd4-0xcd5 has been reserved
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844338] system 00:07: ioport range 0xcd8-0xcdf has been reserved
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844341] system 00:07: ioport range 0x40b-0x40b has been reserved
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844344] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844347] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844351] system 00:07: ioport range 0xc00-0xc01 has been reserved
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844354] system 00:07: ioport range 0xc14-0xc14 has been reserved
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844357] system 00:07: ioport range 0xc50-0xc52 has been reserved
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844360] system 00:07: ioport range 0xc6f-0xc6f has been reserved
Jun 24 14:19:56 laptop-joelbi kernel: [   12.844364] system 00:07: ioport range 0xcd6-0xcd7 has been reserved
Jun 24 14:19:57 laptop-joelbi kernel: [   12.844367] system 00:07: ioport range 0x4000-0x403f has been reserved
Jun 24 14:19:57 laptop-joelbi kernel: [   12.844375] system 00:08: iomem range 0x0-0x9ffff could not be reserved
Jun 24 14:19:57 laptop-joelbi kernel: [   12.844379] system 00:08: iomem range 0xec000-0xfffff could not be reserved
Jun 24 14:19:57 laptop-joelbi kernel: [   12.844382] system 00:08: iomem range 0x100000-0x3bffffff could not be reserved
Jun 24 14:19:57 laptop-joelbi kernel: [   12.844386] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
Jun 24 14:19:57 laptop-joelbi kernel: [   12.844389] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
Jun 24 14:19:57 laptop-joelbi kernel: [   12.844393] system 00:08: iomem range 0xe0000000-0xefffffff has been reserved
Jun 24 14:19:57 laptop-joelbi kernel: [   12.874879] PCI: Bridge: 0000:00:01.0
Jun 24 14:19:57 laptop-joelbi kernel: [   12.874882]   IO window: d000-dfff
Jun 24 14:19:57 laptop-joelbi kernel: [   12.874886]   MEM window: dfc00000-dfdfffff
Jun 24 14:19:57 laptop-joelbi kernel: [   12.874890]   PREFETCH window: d0000000-df8fffff
Jun 24 14:19:57 laptop-joelbi kernel: [   12.874895] PCI: Bridge: 0000:00:14.4
Jun 24 14:19:57 laptop-joelbi kernel: [   12.874898]   IO window: c000-cfff
Jun 24 14:19:57 laptop-joelbi kernel: [   12.874906]   MEM window: dfa00000-dfbfffff
Jun 24 14:19:57 laptop-joelbi kernel: [   12.874912]   PREFETCH window: cff00000-cfffffff
Jun 24 14:19:57 laptop-joelbi kernel: [   12.874947] NET: Registered protocol family 2
Jun 24 14:19:57 laptop-joelbi kernel: [   12.912354] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 24 14:19:57 laptop-joelbi kernel: [   12.912688] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 24 14:19:57 laptop-joelbi kernel: [   12.914073] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 24 14:19:57 laptop-joelbi kernel: [   12.915056] TCP: Hash tables configured (established 131072 bind 65536)
Jun 24 14:19:57 laptop-joelbi kernel: [   12.915060] TCP reno registered
Jun 24 14:19:57 laptop-joelbi kernel: [   12.924505] checking if image is initramfs... it is
Jun 24 14:19:57 laptop-joelbi kernel: [   13.751541] Freeing initrd memory: 7317k freed
Jun 24 14:19:57 laptop-joelbi kernel: [   13.752445] audit: initializing netlink socket (disabled)
Jun 24 14:19:57 laptop-joelbi kernel: [   13.752465] audit(1214309965.520:1): initialized
Jun 24 14:19:57 laptop-joelbi kernel: [   13.752667] highmem bounce pool size: 64 pages
Jun 24 14:19:57 laptop-joelbi kernel: [   13.754911] VFS: Disk quotas dquot_6.5.1
Jun 24 14:19:57 laptop-joelbi kernel: [   13.755003] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 24 14:19:57 laptop-joelbi kernel: [   13.755170] io scheduler noop registered
Jun 24 14:19:57 laptop-joelbi kernel: [   13.755173] io scheduler anticipatory registered
Jun 24 14:19:57 laptop-joelbi kernel: [   13.755175] io scheduler deadline registered
Jun 24 14:19:57 laptop-joelbi kernel: [   13.755189] io scheduler cfq registered (default)
Jun 24 14:19:57 laptop-joelbi kernel: [   13.755548] isapnp: Scanning for PnP cards...
Jun 24 14:19:57 laptop-joelbi kernel: [   14.110469] isapnp: No Plug & Play device found
Jun 24 14:19:57 laptop-joelbi kernel: [   14.144415] Real Time Clock Driver v1.12ac
Jun 24 14:19:57 laptop-joelbi kernel: [   14.144542] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 24 14:19:57 laptop-joelbi kernel: [   14.145957] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 24 14:19:57 laptop-joelbi kernel: [   14.146046] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 24 14:19:57 laptop-joelbi kernel: [   14.146158] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 24 14:19:57 laptop-joelbi kernel: [   14.151013] i8042.c: Detected active multiplexing controller, rev 1.1.
Jun 24 14:19:57 laptop-joelbi kernel: [   14.153541] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 24 14:19:57 laptop-joelbi kernel: [   14.153546] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jun 24 14:19:57 laptop-joelbi kernel: [   14.153549] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jun 24 14:19:57 laptop-joelbi kernel: [   14.153552] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jun 24 14:19:57 laptop-joelbi kernel: [   14.153555] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156079] mice: PS/2 mouse device common for all mice
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156219] EISA: Probing bus 0 at eisa.0
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156229] Cannot allocate resource for EISA slot 1
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156242] Cannot allocate resource for EISA slot 4
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156263] EISA: Detected 0 cards.
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156267] cpuidle: using governor ladder
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156269] cpuidle: using governor menu
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156383] NET: Registered protocol family 1
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156422] Using IPI No-Shortcut mode
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156461] registered taskstats version 1
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156575]   Magic number: 12:346:330
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156702]   hash matches device tty51
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156735] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 24 14:19:57 laptop-joelbi kernel: [   14.156737] EDD information not available.
Jun 24 14:19:57 laptop-joelbi kernel: [   14.157101] Freeing unused kernel memory: 368k freed
Jun 24 14:19:57 laptop-joelbi kernel: [   14.161265] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun 24 14:19:57 laptop-joelbi kernel: [   15.412427] fuse init (API version 7.9)
Jun 24 14:19:57 laptop-joelbi kernel: [   15.434579] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Jun 24 14:19:57 laptop-joelbi kernel: [   15.434598] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 24 14:19:57 laptop-joelbi kernel: [   16.115923] SCSI subsystem initialized
Jun 24 14:19:57 laptop-joelbi kernel: [   16.208066] usbcore: registered new interface driver usbfs
Jun 24 14:19:57 laptop-joelbi kernel: [   16.208096] usbcore: registered new interface driver hub
Jun 24 14:19:57 laptop-joelbi kernel: [   16.231923] usbcore: registered new device driver usb
Jun 24 14:19:57 laptop-joelbi kernel: [   16.265810] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 16
Jun 24 14:19:57 laptop-joelbi kernel: [   16.265881] ACPI: PCI interrupt for device 0000:00:12.0 disabled
Jun 24 14:19:57 laptop-joelbi kernel: [   16.265908] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
Jun 24 14:19:57 laptop-joelbi kernel: [   16.265948] ACPI: PCI interrupt for device 0000:00:14.1 disabled
Jun 24 14:19:57 laptop-joelbi kernel: [   16.283421] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
Jun 24 14:19:57 laptop-joelbi kernel: [   16.283439] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 24 14:19:57 laptop-joelbi kernel: [   16.283775] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jun 24 14:19:57 laptop-joelbi kernel: [   16.283800] ohci_hcd 0000:00:13.0: irq 18, io mem 0x40080000
Jun 24 14:19:57 laptop-joelbi kernel: [   16.343418] usb usb1: configuration #1 chosen from 1 choice
Jun 24 14:19:57 laptop-joelbi kernel: [   16.343451] hub 1-0:1.0: USB hub found
Jun 24 14:19:57 laptop-joelbi kernel: [   16.343463] hub 1-0:1.0: 4 ports detected
Jun 24 14:19:57 laptop-joelbi kernel: [   16.344272] 8139too Fast Ethernet driver 0.9.28
Jun 24 14:19:57 laptop-joelbi kernel: [   16.447397] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
Jun 24 14:19:57 laptop-joelbi kernel: [   16.447419] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jun 24 14:19:57 laptop-joelbi kernel: [   16.447447] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jun 24 14:19:57 laptop-joelbi kernel: [   16.447467] ohci_hcd 0000:00:13.1: irq 18, io mem 0x40081000
Jun 24 14:19:57 laptop-joelbi kernel: [   16.507363] usb usb2: configuration #1 chosen from 1 choice
Jun 24 14:19:57 laptop-joelbi kernel: [   16.507395] hub 2-0:1.0: USB hub found
Jun 24 14:19:57 laptop-joelbi kernel: [   16.507408] hub 2-0:1.0: 4 ports detected
Jun 24 14:19:57 laptop-joelbi kernel: [   16.611528] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 16
Jun 24 14:19:57 laptop-joelbi kernel: [   16.613090] scsi0 : sata_sil
Jun 24 14:19:57 laptop-joelbi kernel: [   16.613814] scsi1 : sata_sil
Jun 24 14:19:57 laptop-joelbi kernel: [   16.614095] ata1: SATA max UDMA/100 mmio m512@0xdfff8e00 tf 0xdfff8e80 irq 16
Jun 24 14:19:57 laptop-joelbi kernel: [   16.614101] ata2: SATA max UDMA/100 mmio m512@0xdfff8e00 tf 0xdfff8ec0 irq 16
Jun 24 14:19:57 laptop-joelbi kernel: [   16.915136] usb 2-2: new low speed USB device using ohci_hcd and address 2
Jun 24 14:19:57 laptop-joelbi kernel: [   16.923133] ata1: SATA link down (SStatus 0 SControl 310)
Jun 24 14:19:57 laptop-joelbi kernel: [   17.120202] usb 2-2: configuration #1 chosen from 1 choice
Jun 24 14:19:57 laptop-joelbi kernel: [   17.235031] ata2: SATA link down (SStatus 0 SControl 310)
Jun 24 14:19:57 laptop-joelbi kernel: [   17.236083] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
Jun 24 14:19:57 laptop-joelbi kernel: [   17.236102] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jun 24 14:19:57 laptop-joelbi kernel: [   17.236143] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jun 24 14:19:57 laptop-joelbi kernel: [   17.236207] ehci_hcd 0000:00:13.2: irq 18, io mem 0xdfff9000
Jun 24 14:19:57 laptop-joelbi kernel: [   17.247034] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 24 14:19:57 laptop-joelbi kernel: [   17.247193] usb usb3: configuration #1 chosen from 1 choice
Jun 24 14:19:57 laptop-joelbi kernel: [   17.247222] hub 3-0:1.0: USB hub found
Jun 24 14:19:57 laptop-joelbi kernel: [   17.247230] hub 3-0:1.0: 8 ports detected
Jun 24 14:19:57 laptop-joelbi kernel: [   17.351353] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
Jun 24 14:19:57 laptop-joelbi kernel: [   17.352193] scsi2 : pata_atiixp
Jun 24 14:19:57 laptop-joelbi kernel: [   17.352788] scsi3 : pata_atiixp
Jun 24 14:19:57 laptop-joelbi kernel: [   17.353627] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
Jun 24 14:19:57 laptop-joelbi kernel: [   17.353632] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
Jun 24 14:19:57 laptop-joelbi kernel: [   17.375048] usb 2-2: USB disconnect, address 2
Jun 24 14:19:57 laptop-joelbi kernel: [   17.515728] ata3.00: ATA-6: ST980811A, 3.ALA, max UDMA/100
Jun 24 14:19:57 laptop-joelbi kernel: [   17.515732] ata3.00: 156301488 sectors, multi 16: LBA48 
Jun 24 14:19:57 laptop-joelbi kernel: [   17.531682] ata3.00: configured for UDMA/100
Jun 24 14:19:57 laptop-joelbi kernel: [   17.851433] ata4.00: ATAPI: Optiarc DVD RW AD-5540A, 2.61, max UDMA/33
Jun 24 14:19:57 laptop-joelbi kernel: [   17.851451] ata4.00: simplex DMA is claimed by other device, disabling DMA
Jun 24 14:19:57 laptop-joelbi kernel: [   17.926816] usb 3-6: new high speed USB device using ehci_hcd and address 3
Jun 24 14:19:57 laptop-joelbi kernel: [   18.023409] ata4.00: configured for PIO4
Jun 24 14:19:57 laptop-joelbi kernel: [   18.023556] scsi 2:0:0:0: Direct-Access     ATA      ST980811A        3.AL PQ: 0 ANSI: 5
Jun 24 14:19:57 laptop-joelbi kernel: [   18.025103] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-5540A  2.61 PQ: 0 ANSI: 5
Jun 24 14:19:57 laptop-joelbi kernel: [   18.032134] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 19 (level, low) -> IRQ 18
Jun 24 14:19:57 laptop-joelbi kernel: [   18.033427] eth0: RealTek RTL8139 at 0xcf00, 00:40:d0:a0:a8:fa, IRQ 18
Jun 24 14:19:57 laptop-joelbi kernel: [   18.035619] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 24 14:19:57 laptop-joelbi kernel: [   18.035625] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 24 14:19:57 laptop-joelbi kernel: [   18.040870] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jun 24 14:19:57 laptop-joelbi kernel: [   18.053221] Driver 'sd' needs updating - please use bus_type methods
Jun 24 14:19:57 laptop-joelbi kernel: [   18.053333] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jun 24 14:19:57 laptop-joelbi kernel: [   18.053349] sd 2:0:0:0: [sda] Write Protect is off
Jun 24 14:19:57 laptop-joelbi kernel: [   18.053372] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 14:19:57 laptop-joelbi kernel: [   18.053429] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jun 24 14:19:57 laptop-joelbi kernel: [   18.053441] sd 2:0:0:0: [sda] Write Protect is off
Jun 24 14:19:57 laptop-joelbi kernel: [   18.053462] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 14:19:57 laptop-joelbi kernel: [   18.053466]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jun 24 14:19:57 laptop-joelbi kernel: [   18.075300]  sda1 sda2 < sda5 >
Jun 24 14:19:57 laptop-joelbi kernel: [   18.106142] sd 2:0:0:0: [sda] Attached SCSI disk
Jun 24 14:19:57 laptop-joelbi kernel: [   18.116707] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jun 24 14:19:57 laptop-joelbi kernel: [   18.116731] sr 3:0:0:0: Attached scsi generic sg1 type 5
Jun 24 14:19:57 laptop-joelbi kernel: [   18.117765] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jun 24 14:19:57 laptop-joelbi kernel: [   18.117771] Uniform CD-ROM driver Revision: 3.20
Jun 24 14:19:57 laptop-joelbi kernel: [   18.235279] usb 3-6: configuration #1 chosen from 1 choice
Jun 24 14:19:57 laptop-joelbi kernel: [   18.272746] usbcore: registered new interface driver hiddev
Jun 24 14:19:57 laptop-joelbi kernel: [   18.435293] Attempting manual resume
Jun 24 14:19:57 laptop-joelbi kernel: [   18.452314] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun 24 14:19:57 laptop-joelbi kernel: [   18.452320] EXT3-fs: write access will be enabled during recovery.
Jun 24 14:19:57 laptop-joelbi kernel: [   18.558631] usb 2-2: new low speed USB device using ohci_hcd and address 3
Jun 24 14:19:57 laptop-joelbi kernel: [   18.763664] usb 2-2: configuration #1 chosen from 1 choice
Jun 24 14:19:57 laptop-joelbi kernel: [   18.770915] input: USB Mouse as /devices/pci0000:00/0000:00:13.1/usb2/2-2/2-2:1.0/input/input2
Jun 24 14:19:57 laptop-joelbi kernel: [   18.782602] input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:13.1-2
Jun 24 14:19:57 laptop-joelbi kernel: [   18.782621] usbcore: registered new interface driver usbhid
Jun 24 14:19:57 laptop-joelbi kernel: [   18.782626] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jun 24 14:19:57 laptop-joelbi kernel: [   22.270396] kjournald starting.  Commit interval 5 seconds
Jun 24 14:19:57 laptop-joelbi kernel: [   22.270419] EXT3-fs: sda1: orphan cleanup on readonly fs
Jun 24 14:19:57 laptop-joelbi kernel: [   22.270761] EXT3-fs: sda1: 4 orphan inodes deleted
Jun 24 14:19:57 laptop-joelbi kernel: [   22.270763] EXT3-fs: recovery complete.
Jun 24 14:19:57 laptop-joelbi kernel: [   22.318178] EXT3-fs: mounted filesystem with ordered data mode.
Jun 24 14:19:57 laptop-joelbi kernel: [   33.515315] input: PC Speaker as /devices/platform/pcspkr/input/input3
Jun 24 14:19:57 laptop-joelbi kernel: [   34.230163] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jun 24 14:19:57 laptop-joelbi kernel: [   34.270052] Linux agpgart interface v0.102
Jun 24 14:19:57 laptop-joelbi kernel: [   34.374051] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 24 14:19:57 laptop-joelbi kernel: [   34.418131] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 24 14:19:57 laptop-joelbi kernel: [   35.241955] input: Power Button (FF) as /devices/virtual/input/input4
Jun 24 14:19:57 laptop-joelbi kernel: [   35.269826] ACPI: Power Button (FF) [PWRF]
Jun 24 14:19:57 laptop-joelbi kernel: [   35.269923] input: Power Button (CM) as /devices/virtual/input/input5
Jun 24 14:19:57 laptop-joelbi kernel: [   35.301787] ACPI: Power Button (CM) [PWRB]
Jun 24 14:19:57 laptop-joelbi kernel: [   35.301881] input: Lid Switch as /devices/virtual/input/input6
Jun 24 14:19:57 laptop-joelbi kernel: [   35.316271] ACPI: Lid Switch [LID]
Jun 24 14:19:57 laptop-joelbi kernel: [   35.316367] input: Sleep Button (CM) as /devices/virtual/input/input7
Jun 24 14:19:57 laptop-joelbi kernel: [   35.345784] ACPI: Sleep Button (CM) [SBTN]
Jun 24 14:19:57 laptop-joelbi kernel: [   35.357882] ACPI: AC Adapter [AC] (on-line)
Jun 24 14:19:57 laptop-joelbi kernel: [   35.510216] ACPI: Battery Slot [BAT0] (battery present)
Jun 24 14:19:57 laptop-joelbi kernel: [   36.238507] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x3aa0b4, caps: 0xa04713/0x200000
Jun 24 14:19:57 laptop-joelbi kernel: [   36.281184] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Jun 24 14:19:57 laptop-joelbi kernel: [   36.939283] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
Jun 24 14:19:57 laptop-joelbi kernel: [   37.078700] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jun 24 14:19:57 laptop-joelbi kernel: [   37.156989] [fglrx] Maximum main memory to use for locked dma buffers: 866 MBytes.
Jun 24 14:19:57 laptop-joelbi kernel: [   37.157038] [fglrx] ASYNCIO init succeed!
Jun 24 14:19:57 laptop-joelbi kernel: [   37.157394] [fglrx] PAT is enabled successfully!
Jun 24 14:19:57 laptop-joelbi kernel: [   37.184838] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Jun 24 14:19:57 laptop-joelbi kernel: [   38.072546] usbcore: registered new interface driver rt2500usb
Jun 24 14:19:57 laptop-joelbi kernel: [   38.567266] usbcore: registered new interface driver rt73usb
Jun 24 14:19:57 laptop-joelbi kernel: [   40.380147] lp: driver loaded but no devices found
Jun 24 14:19:57 laptop-joelbi kernel: [   40.673647] Adding 2843464k swap on /dev/sda5.  Priority:-1 extents:1 across:2843464k
Jun 24 14:19:57 laptop-joelbi kernel: [   41.230476] EXT3 FS on sda1, internal journal
Jun 24 14:19:57 laptop-joelbi kernel: [   42.644067] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 24 14:19:57 laptop-joelbi kernel: [   43.152707] No dock devices found.
Jun 24 14:19:57 laptop-joelbi kernel: [   44.412569] apm: BIOS not found.
Jun 24 14:19:57 laptop-joelbi kernel: [   44.647014] ppdev: user-space parallel port driver
Jun 24 14:19:57 laptop-joelbi kernel: [   44.777941] audit(1214309997.643:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4847 profile="/usr/sbin/cupsd" namespace="default"
Jun 24 14:19:57 laptop-joelbi dhcdbd: Started up.
Jun 24 14:19:58 laptop-joelbi kernel: [   45.718610] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 24 14:19:58 laptop-joelbi kernel: [   45.885848] Bluetooth: Core ver 2.11
Jun 24 14:19:58 laptop-joelbi kernel: [   45.888341] NET: Registered protocol family 31
Jun 24 14:19:58 laptop-joelbi kernel: [   45.888347] Bluetooth: HCI device and connection manager initialized
Jun 24 14:19:58 laptop-joelbi kernel: [   45.888353] Bluetooth: HCI socket layer initialized
Jun 24 14:19:58 laptop-joelbi kernel: [   45.978631] Bluetooth: L2CAP ver 2.9
Jun 24 14:19:58 laptop-joelbi kernel: [   45.978637] Bluetooth: L2CAP socket layer initialized
Jun 24 14:19:58 laptop-joelbi kernel: [   46.062858] Bluetooth: RFCOMM socket layer initialized
Jun 24 14:19:58 laptop-joelbi kernel: [   46.063109] Bluetooth: RFCOMM TTY layer initialized
Jun 24 14:19:58 laptop-joelbi kernel: [   46.063113] Bluetooth: RFCOMM ver 1.8
Jun 24 14:19:59 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 24 14:20:01 laptop-joelbi kernel: [   48.290211] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 19
Jun 24 14:20:02 laptop-joelbi kernel: [   49.221670] NET: Registered protocol family 17
Jun 24 14:20:03 laptop-joelbi kernel: [   50.136355] [fglrx] GART Table is not in FRAME_BUFFER range 
Jun 24 14:20:03 laptop-joelbi kernel: [   50.136371] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Jun 24 14:20:03 laptop-joelbi kernel: [   50.136374] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
Jun 24 14:20:03 laptop-joelbi kernel: [   50.381635] [fglrx] interrupt source 10000000 successfully enabled
Jun 24 14:20:03 laptop-joelbi kernel: [   50.381644] [fglrx] enable ID = 0x00000004
Jun 24 14:20:03 laptop-joelbi kernel: [   50.382000] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Jun 24 14:20:06 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun 24 14:20:06 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun 24 14:20:06 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 24 14:20:06 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 24 14:20:06 laptop-joelbi dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun 24 14:20:07 laptop-joelbi kernel: [   54.559722] NET: Registered protocol family 10
Jun 24 14:20:07 laptop-joelbi kernel: [   54.560292] lo: Disabled Privacy Extensions
Jun 24 14:20:07 laptop-joelbi kernel: [   54.561418] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 24 14:20:19 laptop-joelbi kernel: [   66.742342] [fglrx] interrupt source 10000000 successfully disabled!
Jun 24 14:20:19 laptop-joelbi kernel: [   66.742350] [fglrx] enable ID = 0x00000000
Jun 24 14:20:19 laptop-joelbi kernel: [   66.742354] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000004
Jun 24 14:20:23 laptop-joelbi kernel: [   70.139649] [fglrx] PCIe has already been initialized. Reinitializing ...
Jun 24 14:20:23 laptop-joelbi kernel: [   70.160049] [fglrx] GART Table is not in FRAME_BUFFER range 
Jun 24 14:20:23 laptop-joelbi kernel: [   70.160064] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Jun 24 14:20:23 laptop-joelbi kernel: [   70.160067] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
Jun 24 14:20:23 laptop-joelbi kernel: [   70.315744] [fglrx] interrupt source 10000000 successfully enabled
Jun 24 14:20:23 laptop-joelbi kernel: [   70.315754] [fglrx] enable ID = 0x00000004
Jun 24 14:20:23 laptop-joelbi kernel: [   70.316121] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Jun 24 14:20:41 laptop-joelbi kernel: [   88.463622] hda-intel: Invalid position buffer, using LPIB read method instead.

```



```
[   66.742350] [fglrx] enable ID = 0x00000000
[   66.742354] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000004
[   70.139649] [fglrx] PCIe has already been initialized. Reinitializing ...
[   70.160049] [fglrx] GART Table is not in FRAME_BUFFER range 
[   70.160064] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   70.160067] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   70.315744] [fglrx] interrupt source 10000000 successfully enabled
[   70.315754] [fglrx] enable ID = 0x00000004
[   70.316121] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   88.463622] hda-intel: Invalid position buffer, using LPIB read method instead.

```

---

### Post by ukripper on 2008-06-24
looks like problem is with login screen/gdm no errors in your logs.

Can you do the following:
In the System->Administration->Login Window, under "Security" check the "Enable automatic login" option- then reboot,

 and then once it is logged in then again disable automatic login and then reboot. let's see if it fixes this for gdm.

---

### Post by jspolen on 2008-06-24
Yeah that worked, no problem logging in now, username and password worked.

Strange though, it feels like that simple change shouldn't do it. But the ubuntu works in mysterious ways!

Thanks!

---

### Post by Joeb454 on 2008-06-24
That is a strange "fix" ;)

You can mark your thread as solved from "Thread Tools" at the top of this page :)

---

### Post by sujoy on 2008-06-24
any explanation how that actually works? its weird

---

### Post by Cadmus on 2008-06-24
Conjecture:
Something messes up a gdm file, putting the machine on auto-login then back again changes/recreates the file.

---

### Post by ukripper on 2008-06-24
I think it was using both login modes single and multi that may have caused the problem. Using the above workaround sorted the gdm to use multi user mode.

---

### Post by naturalfreak on 2008-08-14
I tried enabling the ATI driver and that fixed things.  In Failsafe mode, System > Administration > Hardware Drivers then select the ATI driver.

---

