---
title: "Xubuntu error logs"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by aimpau on 2008-08-28
Where does xubuntu store it's error logs? My PC just crashed, while using Gimp, which needed a hard reset. I want to know what's the cause of the problem.

---

### Post by Ryadt on 2008-08-28
try /var/log/debug

---

### Post by aimpau on 2008-08-28
Ok. Just a side question, I have, in that log, this:

Aug 28 16:44:27 paulo-desktop kernel: [   28.729943] PM: Resume from disk failed.

not just one but a lot of it. Anyone know's why? Here's the whole log from today:

Aug 28 16:04:49 paulo-desktop kernel: [   28.758473] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug 28 16:04:49 paulo-desktop kernel: [   28.792077] sr 1:0:1:0: Attached scsi CD-ROM sr0
Aug 28 16:04:49 paulo-desktop kernel: [   29.668598] swsusp: Resume From Partition 8:5
Aug 28 16:04:49 paulo-desktop kernel: [   29.668600] PM: Checking swsusp image.
Aug 28 16:04:49 paulo-desktop kernel: [   29.678651] PM: Resume from disk failed.
Aug 28 16:04:56 paulo-desktop NetworkManager: <debug> [1219910696.531168] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD/DVDW_SH_S182M'). 
Aug 28 16:05:09 paulo-desktop kernel: [   70.929204] eth0: no IPv6 routers present
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 114400) 0 entries of 256 used
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000] On node 0 totalpages: 114400
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000]   Normal zone: 861 pages used for memmap
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000]   Normal zone: 109443 pages, LIFO batch:31
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 28 16:28:24 paulo-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 28 16:28:24 paulo-desktop kernel: [   24.232490] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
Aug 28 16:28:24 paulo-desktop kernel: [   24.232504] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
Aug 28 16:28:24 paulo-desktop kernel: [   24.747580] CPU0 attaching sched-domain:
Aug 28 16:28:24 paulo-desktop kernel: [   24.747583]  domain 0: span 01
Aug 28 16:28:24 paulo-desktop kernel: [   24.747585]   groups: 01
Aug 28 16:28:24 paulo-desktop kernel: [   24.771215] ACPI: EC: Look up EC in DSDT
Aug 28 16:28:24 paulo-desktop kernel: [   24.779177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 28 16:28:24 paulo-desktop kernel: [   25.362549] Switched to high resolution mode on CPU 0
Aug 28 16:28:24 paulo-desktop kernel: [   25.650008] Boot video device is 0000:01:00.0
Aug 28 16:28:24 paulo-desktop kernel: [   27.933097] libata version 3.00 loaded.
Aug 28 16:28:24 paulo-desktop kernel: [   28.008235] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 28 16:28:24 paulo-desktop kernel: [   28.488691] PCI: cache line size of 64 is not supported by device 0000:00:03.3
Aug 28 16:28:24 paulo-desktop kernel: [   28.760911] pata_sis 0000:00:02.5: version 0.5.2
Aug 28 16:28:24 paulo-desktop kernel: [   29.548272] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 28 16:28:24 paulo-desktop kernel: [   29.548340] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 28 16:28:24 paulo-desktop kernel: [   29.591135] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug 28 16:28:24 paulo-desktop kernel: [   29.591200] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug 28 16:28:24 paulo-desktop kernel: [   29.628853] sr 1:0:1:0: Attached scsi CD-ROM sr0
Aug 28 16:28:24 paulo-desktop kernel: [   30.542386] swsusp: Resume From Partition 8:5
Aug 28 16:28:24 paulo-desktop kernel: [   30.542388] PM: Checking swsusp image.
Aug 28 16:28:24 paulo-desktop kernel: [   30.552443] PM: Resume from disk failed.
Aug 28 16:28:31 paulo-desktop NetworkManager: <debug> [1219912111.344179] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD/DVDW_SH_S182M'). 
Aug 28 16:28:54 paulo-desktop kernel: [   80.652920] eth0: no IPv6 routers present
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 114400) 0 entries of 256 used
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000] On node 0 totalpages: 114400
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000]   Normal zone: 861 pages used for memmap
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000]   Normal zone: 109443 pages, LIFO batch:31
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 28 16:44:27 paulo-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 28 16:44:27 paulo-desktop kernel: [   22.530914] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
Aug 28 16:44:27 paulo-desktop kernel: [   22.530928] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
Aug 28 16:44:27 paulo-desktop kernel: [   23.046004] CPU0 attaching sched-domain:
Aug 28 16:44:27 paulo-desktop kernel: [   23.046007]  domain 0: span 01
Aug 28 16:44:27 paulo-desktop kernel: [   23.046009]   groups: 01
Aug 28 16:44:27 paulo-desktop kernel: [   23.069651] ACPI: EC: Look up EC in DSDT
Aug 28 16:44:27 paulo-desktop kernel: [   23.077617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 28 16:44:27 paulo-desktop kernel: [   23.660974] Switched to high resolution mode on CPU 0
Aug 28 16:44:27 paulo-desktop kernel: [   23.948426] Boot video device is 0000:01:00.0
Aug 28 16:44:27 paulo-desktop kernel: [   26.228948] libata version 3.00 loaded.
Aug 28 16:44:27 paulo-desktop kernel: [   26.308462] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 28 16:44:27 paulo-desktop kernel: [   26.791137] PCI: cache line size of 64 is not supported by device 0000:00:03.3
Aug 28 16:44:27 paulo-desktop kernel: [   27.063301] pata_sis 0000:00:02.5: version 0.5.2
Aug 28 16:44:27 paulo-desktop kernel: [   27.850731] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 28 16:44:27 paulo-desktop kernel: [   27.850798] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 28 16:44:27 paulo-desktop kernel: [   27.892056] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug 28 16:44:27 paulo-desktop kernel: [   27.892121] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug 28 16:44:27 paulo-desktop kernel: [   27.930068] sr 1:0:1:0: Attached scsi CD-ROM sr0
Aug 28 16:44:27 paulo-desktop kernel: [   28.719923] swsusp: Resume From Partition 8:5
Aug 28 16:44:27 paulo-desktop kernel: [   28.719925] PM: Checking swsusp image.
Aug 28 16:44:27 paulo-desktop kernel: [   28.729943] PM: Resume from disk failed.
Aug 28 16:44:27 paulo-desktop kernel: [   29.580043] ext3_orphan_cleanup: deleting unreferenced inode 426892
Aug 28 16:44:34 paulo-desktop NetworkManager: <debug> [1219913074.400381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD/DVDW_SH_S182M'). 
Aug 28 16:44:37 paulo-desktop kernel: [   60.793809] eth0: no IPv6 routers present


I have another HD for winXP, which is the default though I have my Xubuntu as the master.

---

### Post by Ryadt on 2008-08-28
Have a look here : [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

