---
title: "USB thumb drive not showing up"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by happyisland on 2012-02-03
So I bought one of these:

[http://www.woodenboatstore.com/WoodenBoat-Magazine-The-Complete-Back-Issue-Collection/productinfo/202-002/](http://www.woodenboatstore.com/WoodenBoat-Magazine-The-Complete-Back-Issue-Collection/productinfo/202-002/)

which is a USB stick that has all the back issues of Wooden Boat magazine. 

Here's the rub: when I plug it into my laptop's USB port NOTHING HAPPENS.

here's what lsusb has to say:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 04f2:b221 Chicony Electronics Co., Ltd 
Bus 001 Device 031: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 002 Device 006: ID 0011:7788 

```

Any ideas?

---

### Post by lechien73 on 2012-02-03
What does dmesg report?

I was reading about this issue recently, that it can be to do with the flash drive reporting a greater capacity than the chipset says it's capable of.

I've taken a quick search on some of the keywords that I used before, and came up with this blog post. It's in Italian, but Google Translate gives a readable version:

[http://diegovicentini.blogspot.com/2011/09/usb-flash-disk-mount-problem-solved.html](http://diegovicentini.blogspot.com/2011/09/usb-flash-disk-mount-problem-solved.html)

I thought this was useful because it's the exact same bus ID of your flash drive.

I hope it helps you :)

---

### Post by happyisland on 2012-02-03
> **lechien73 said:**
> What does dmesg report?

I was reading about this issue recently, that it can be to do with the flash drive reporting a greater capacity than the chipset says it's capable of.

I've taken a quick search on some of the keywords that I used before, and came up with this blog post. It's in Italian, but Google Translate gives a readable version:

[http://diegovicentini.blogspot.com/2011/09/usb-flash-disk-mount-problem-solved.html](http://diegovicentini.blogspot.com/2011/09/usb-flash-disk-mount-problem-solved.html)

I thought this was useful because it's the exact same bus ID of your flash drive.

I hope it helps you :)

Here's the dmesg output, hope it helps:

```
[271094.102625] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[271094.727669] usb 1-1.4: USB disconnect, device number 30
[271094.727777] btusb_bulk_complete: hci0 urb ffff8801ffcee3c0 failed to resubmit (19)
[271094.727870] btusb_intr_complete: hci0 urb ffff8801ffceed80 failed to resubmit (19)
[271094.727905] btusb_bulk_complete: hci0 urb ffff8801ffceea80 failed to resubmit (19)
[271094.728444] btusb_send_frame: hci0 urb ffff88022dacf9c0 submission failed
[271095.721097] PM: Syncing filesystems ... done.
[271095.753348] PM: Preparing system for mem sleep
[271096.051573] Freezing user space processes ... (elapsed 0.01 seconds) done.
[271096.067473] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[271096.083479] PM: Entering mem sleep
[271096.083579] Suspending console(s) (use no_console_suspend to debug)
[271096.260025] PM: suspend of drv:psmouse dev:serio2 complete after 160.533 msecs
[271096.260149] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[271096.260517] sd 0:0:0:0: [sda] Stopping disk
[271096.507312] PM: suspend of drv:tpm_tis dev:00:0a complete after 190.318 msecs
[271096.507624] sdhci-pci 0000:05:00.0: PCI INT A disabled
[271096.512080] PM: suspend of drv:sd dev:0:0:0:0 complete after 252.014 msecs
[271096.512107] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[271096.512113] PM: suspend of drv:scsi dev:target0:0:0 complete after 251.978 msecs
[271096.519081] PM: suspend of drv:scsi dev:host0 complete after 258.750 msecs
[271096.519092] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[271096.519543] ACPI handle has no context!
[271096.535246] i915 0000:00:02.0: power state changed by ACPI to D3
[271096.627589] HDA Intel 0000:00:1b.0: PCI INT A disabled
[271096.647185] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 128.142 msecs
[271096.733813] e1000e 0000:00:19.0: PME# enabled
[271096.733818] e1000e 0000:00:19.0: wake-up capability enabled by ACPI
[271096.747160] PM: suspend of drv:e1000e dev:0000:00:19.0 complete after 228.136 msecs
[271096.747169] PM: suspend of drv: dev:pci0000:00 complete after 227.587 msecs
[271096.747173] PM: suspend of devices complete after 647.888 msecs
[271096.747174] PM: suspend devices took 0.664 seconds
[271096.795192] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D3
[271096.831195] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D3
[271096.847228] PM: late suspend of devices complete after 100.077 msecs
[271096.847902] ACPI: Preparing to enter system sleep state S3
[271097.027186] PM: Saving platform NVS memory
[271097.029909] Disabling non-boot CPUs ...
[271097.031798] CPU 1 is now offline
[271097.135070] CPU 2 is now offline
[271097.239032] CPU 3 is now offline
[271097.239335] Extended CMOS year: 2000
[271097.239575] ACPI: Low-level resume complete
[271097.239613] PM: Restoring platform NVS memory
[271097.240412] Extended CMOS year: 2000
[271097.240446] Enabling non-boot CPUs ...
[271097.240512] Booting Node 0 Processor 1 APIC 0x1
[271097.240514] smpboot cpu 1: start_ip = 98000
[271097.328055] Disabled fast string operations
[271097.352064] Switched to NOHz mode on CPU #1
[271097.460182] CPU1 is up
[271097.460270] Booting Node 0 Processor 2 APIC 0x2
[271097.460271] smpboot cpu 2: start_ip = 98000
[271097.547985] Disabled fast string operations
[271097.571978] Switched to NOHz mode on CPU #2
[271097.680115] CPU2 is up
[271097.680189] Booting Node 0 Processor 3 APIC 0x3
[271097.680190] smpboot cpu 3: start_ip = 98000
[271097.767915] Disabled fast string operations
[271097.791957] Switched to NOHz mode on CPU #3
[271097.900151] CPU3 is up
[271097.902502] ACPI: Waking up from system sleep state S3
[271098.207981] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[271098.207988] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[271098.208005] mei 0000:00:16.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[271098.208018] mei 0000:00:16.0: restoring config space at offset 0x4 (was 0xfed0a004, writing 0xd1625004)
[271098.208023] mei 0000:00:16.0: restoring config space at offset 0x1 (was 0x100006, writing 0x180006)
[271098.208040] serial 0000:00:16.3: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[271098.208052] serial 0000:00:16.3: restoring config space at offset 0x5 (was 0x0, writing 0xd162c000)
[271098.208056] serial 0000:00:16.3: restoring config space at offset 0x4 (was 0x1, writing 0x40b1)
[271098.208061] serial 0000:00:16.3: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00007)
[271098.208080] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[271098.208090] e1000e 0000:00:19.0: restoring config space at offset 0x6 (was 0x1, writing 0x4081)
[271098.208097] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100007)
[271098.208119] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[271098.208134] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xd162a000)
[271098.208140] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[271098.227912] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[271098.227937] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[271098.227956] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[271098.227968] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xd1620004)
[271098.227972] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[271098.227977] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[271098.228011] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[271098.228025] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[271098.228030] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[271098.228036] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0xf0)
[271098.228046] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[271098.228052] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100004)
[271098.228102] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x207)
[271098.228115] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[271098.228121] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xd150d150)
[271098.228126] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
[271098.228136] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[271098.228142] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[271098.228191] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x40b)
[271098.228204] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xd0b1d041)
[271098.228209] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xd140d0d0)
[271098.228214] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x20003030)
[271098.228223] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[271098.228230] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[271098.228269] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[271098.228278] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[271098.228282] pcieport 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xd0c0d0c0)
[271098.228286] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
[271098.228292] pcieport 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[271098.228297] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[271098.228324] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[271098.228338] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xd1629000)
[271098.228344] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[271098.228359] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[271098.228362] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[271098.228417] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
[271098.228538] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[271098.228575] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd1500004)
[271098.228583] iwlagn 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[271098.228593] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100406)
[271098.228930] sdhci-pci 0000:05:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0d00000)
[271098.228938] sdhci-pci 0000:05:00.0: restoring config space at offset 0x2 (was 0x8800004, writing 0x8800007)
[271098.228944] sdhci-pci 0000:05:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[271098.228949] sdhci-pci 0000:05:00.0: restoring config space at offset 0x0 (was 0xe8231180, writing 0xe8221180)
[271098.228986] sdhci-pci 0000:05:00.0: MMC controller base frequency changed to 50Mhz.
[271098.229022] xhci_hcd 0000:0d:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[271098.229044] xhci_hcd 0000:0d:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd0c00004)
[271098.229049] xhci_hcd 0000:0d:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[271098.229056] xhci_hcd 0000:0d:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100402)
[271098.229164] PM: early resume of devices complete after 21.228 msecs
[271098.229283] e1000e 0000:00:19.0: wake-up capability disabled by ACPI
[271098.229290] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[271098.229292] e1000e 0000:00:19.0: PME# disabled
[271098.229343] xhci_hcd 0000:0d:00.0: setting latency timer to 64
[271098.229376] usb usb3: root hub lost power or was reset
[271098.229377] usb usb4: root hub lost power or was reset
[271098.229685] xhci_hcd 0000:0d:00.0: irq 40 for MSI/MSI-X
[271098.229688] xhci_hcd 0000:0d:00.0: irq 41 for MSI/MSI-X
[271098.229691] xhci_hcd 0000:0d:00.0: irq 42 for MSI/MSI-X
[271098.229693] xhci_hcd 0000:0d:00.0: irq 43 for MSI/MSI-X
[271098.229696] xhci_hcd 0000:0d:00.0: irq 44 for MSI/MSI-X
[271098.233021] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[271098.235769] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[271098.235777] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[271098.235784] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[271098.235820] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[271098.235825] HDA Intel 0000:00:1b.0: setting latency timer to 64
[271098.235855] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[271098.235918] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[271098.235928] ahci 0000:00:1f.2: setting latency timer to 64
[271098.235947] sdhci-pci 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[271098.235955] i915 0000:00:02.0: power state changed by ACPI to D0
[271098.235957] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[271098.235959] i915 0000:00:02.0: power state changed by ACPI to D0
[271098.235965] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[271098.235967] i915 0000:00:02.0: setting latency timer to 64
[271098.235973] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[271098.251831] sd 0:0:0:0: [sda] Starting disk
[271098.285098] Extended CMOS year: 2000
[271098.332938] PM: resume of drv:e1000e dev:0000:00:19.0 complete after 103.692 msecs
[271098.351826] PM: resume of drv:hub dev:3-0:1.0 complete after 122.338 msecs
[271098.351836] PM: resume of drv: dev:ep_00 complete after 122.316 msecs
[271098.351844] PM: resume of drv: dev:ep_81 complete after 122.349 msecs
[271098.351857] PM: resume of drv:hub dev:4-0:1.0 complete after 122.308 msecs
[271098.351873] PM: resume of drv: dev:ep_00 complete after 122.307 msecs
[271098.351890] PM: resume of drv: dev:ep_81 complete after 122.339 msecs
[271098.415832] PM: resume of drv:hub dev:1-1:1.0 complete after 186.085 msecs
[271098.415860] PM: resume of drv: dev:ep_00 complete after 186.081 msecs
[271098.415873] PM: resume of drv: dev:ep_81 complete after 186.121 msecs
[271098.487917] usb 1-1.6: reset high speed USB device number 4 using ehci_hcd
[271098.534425] PM: resume of drv:i915 dev:0000:00:02.0 complete after 305.260 msecs
[271098.587707] ata2: SATA link down (SStatus 0 SControl 300)
[271098.587741] ata5: SATA link down (SStatus 0 SControl 300)
[271098.739622] sdhci-pci 0000:05:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[271098.739642] sdhci-pci 0000:05:00.0: setting latency timer to 64
[271098.739682] PM: resume of drv:sdhci-pci dev:0000:05:00.0 complete after 510.514 msecs
[271098.765961] restoring control 00000000-0000-0000-0000-000000000001/2/3
[271098.767114] PM: resume of drv: dev:ep_00 complete after 537.264 msecs
[271098.767125] PM: resume of drv:uvcvideo dev:1-1.6:1.0 complete after 537.304 msecs
[271098.767132] PM: resume of drv:uvcvideo dev:1-1.6:1.1 complete after 537.299 msecs
[271098.767149] PM: resume of drv: dev:ep_81 complete after 537.332 msecs
[271099.467424] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[271099.470082] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[271099.470092] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[271099.470099] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[271099.475618] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[271099.475628] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[271099.475635] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[271099.478190] ata1.00: configured for UDMA/133
[271099.532574] PM: resume of drv:sd dev:0:0:0:0 complete after 1303.132 msecs
[271099.532625] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1303.171 msecs
[271099.532633] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 793.102 msecs
[271099.533623] PM: resume of devices complete after 1304.832 msecs
[271099.533683] PM: resume devices took 1.304 seconds
[271099.533704] PM: Finishing wakeup.
[271099.533705] Restarting tasks ... done.
[271099.547264] video LNXVIDEO:00: Restoring backlight state
[271099.590711] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[271100.227288] usb 1-1.4: new full speed USB device number 31 using ehci_hcd
[271102.302990] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[271102.491191] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[271102.546564] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[271102.548162] ADDRCONF(NETDEV_UP): eth0: link is not ready
[271102.672120] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[271110.188889] wlan0: authenticate with 00:1e:e5:6c:4f:37 (try 1)
[271110.194995] wlan0: authenticated
[271110.195587] wlan0: associate with 00:1e:e5:6c:4f:37 (try 1)
[271110.197884] wlan0: RX AssocResp from 00:1e:e5:6c:4f:37 (capab=0x411 status=0 aid=4)
[271110.197893] wlan0: associated
[271110.203263] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[271119.640426] Valid eCryptfs headers not found in file header region or xattr region
[271119.640430] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[271121.173116] wlan0: no IPv6 routers present
[271200.683746] usb 2-1.2: new high speed USB device number 5 using ehci_hcd
[271200.865616] scsi7 : usb-storage 2-1.2:1.0
[271201.866579] scsi 7:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
[271201.964379] sd 7:0:0:0: Attached scsi generic sg1 type 0
[271201.965799] sd 7:0:0:0: [sdb] 15769600 512-byte logical blocks: (8.07 GB/7.51 GiB)
[271201.967948] sd 7:0:0:0: [sdb] Write Protect is off
[271201.967961] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[271201.971318] sd 7:0:0:0: [sdb] No Caching mode page present
[271201.971330] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[271201.975029] sd 7:0:0:0: [sdb] No Caching mode page present
[271201.975037] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[271201.998325]  sdb: sdb1
[271202.000408] sd 7:0:0:0: [sdb] No Caching mode page present
[271202.000416] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[271202.000421] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[271232.689608] usb 2-1.2: reset high speed USB device number 5 using ehci_hcd
[271263.735275] usb 2-1.2: reset high speed USB device number 5 using ehci_hcd
[271294.716822] usb 2-1.2: reset high speed USB device number 5 using ehci_hcd
[271325.698547] usb 2-1.2: reset high speed USB device number 5 using ehci_hcd
[271356.680088] usb 2-1.2: reset high speed USB device number 5 using ehci_hcd
[271387.661809] usb 2-1.2: reset high speed USB device number 5 using ehci_hcd
[271387.838900] sd 7:0:0:0: [sdb] Unhandled error code
[271387.838909] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[271387.838917] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 9f f8 00 00 01 00
[271387.838936] end_request: I/O error, dev sdb, sector 15769592
[271387.838945] Buffer I/O error on device sdb, logical block 1971199
[271418.643382] usb 2-1.2: reset high speed USB device number 5 using ehci_hcd
[271449.753035] usb 2-1.2: reset high speed USB device number 5 using ehci_hcd
[271480.734724] usb 2-1.2: reset high speed USB device number 5 using ehci_hcd
[271497.206173] sd 7:0:0:0: [sdb] Unhandled error code
[271497.206197] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[271497.206210] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 9f f8 00 00 01 00
[271497.206234] end_request: I/O error, dev sdb, sector 15769592
[271497.206244] Buffer I/O error on device sdb1, logical block 1970951
[271497.206326] usb 2-1.2: USB disconnect, device number 5
[271528.775357] usb 2-1.2: new high speed USB device number 6 using ehci_hcd
[271528.957088] scsi8 : usb-storage 2-1.2:1.0
[271529.958216] scsi 8:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
[271530.010957] sd 8:0:0:0: Attached scsi generic sg1 type 0
[271530.016100] sd 8:0:0:0: [sdb] 15769600 512-byte logical blocks: (8.07 GB/7.51 GiB)
[271530.017706] sd 8:0:0:0: [sdb] Write Protect is off
[271530.017718] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[271530.018865] sd 8:0:0:0: [sdb] No Caching mode page present
[271530.018875] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[271530.022430] sd 8:0:0:0: [sdb] No Caching mode page present
[271530.022440] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[271530.045917]  sdb: sdb1
[271530.049423] sd 8:0:0:0: [sdb] No Caching mode page present
[271530.049426] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[271530.049429] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[271560.685283] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271591.730949] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271622.712520] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271653.744571] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271684.774713] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271715.740817] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271715.917853] sd 8:0:0:0: [sdb] Unhandled error code
[271715.917863] sd 8:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[271715.917871] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 9f f8 00 00 01 00
[271715.917891] end_request: I/O error, dev sdb, sector 15769592
[271715.917900] Buffer I/O error on device sdb, logical block 1971199
[271746.707019] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271777.673107] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271808.639291] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271839.733331] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271870.699531] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271901.665731] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271901.842279] sd 8:0:0:0: [sdb] Unhandled error code
[271901.842288] sd 8:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[271901.842296] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 9f f8 00 00 01 00
[271901.842315] end_request: I/O error, dev sdb, sector 15769592
[271901.842325] Buffer I/O error on device sdb1, logical block 1970951
[271932.631775] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271963.598017] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[271994.692030] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272025.658227] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272056.624271] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272077.289622] INFO: task udisks-daemon:1753 blocked for more than 120 seconds.
[272077.289631] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[272077.289646] udisks-daemon   D 0000000000000000     0  1753   1752 0x00000000
[272077.289650]  ffff88022ef85b18 0000000000000082 ffff88022ef85ac8 0000000000000000
[272077.289654]  ffff88022ef85fd8 ffff88022ef85fd8 ffff88022ef85fd8 0000000000012a40
[272077.289657]  ffff8802055e5c80 ffff8802314dae40 0000000000800010 ffff88022ea09058
[272077.289660] Call Trace:
[272077.289667]  [<ffffffff815eff1f>] schedule+0x3f/0x60
[272077.289670]  [<ffffffff815f0d27>] __mutex_lock_slowpath+0xd7/0x150
[272077.289673]  [<ffffffff815f093a>] mutex_lock+0x2a/0x50
[272077.289677]  [<ffffffff8119df3b>] __blkdev_get+0x7b/0x420
[272077.289679]  [<ffffffff8119e33e>] blkdev_get+0x5e/0x1e0
[272077.289682]  [<ffffffff8119e520>] blkdev_open+0x60/0x90
[272077.289686]  [<ffffffff81165d64>] __dentry_open+0x144/0x320
[272077.289689]  [<ffffffff8119e4c0>] ? blkdev_get+0x1e0/0x1e0
[272077.289692]  [<ffffffff811674ad>] nameidata_to_filp+0xad/0xb0
[272077.289696]  [<ffffffff811755f0>] do_last+0x3a0/0x730
[272077.289699]  [<ffffffff811774fa>] path_openat+0xca/0x3f0
[272077.289704]  [<ffffffff812eaa97>] ? kobject_put+0x27/0x60
[272077.289708]  [<ffffffff813cba97>] ? put_device+0x17/0x20
[272077.289711]  [<ffffffff81177922>] do_filp_open+0x42/0xa0
[272077.289714]  [<ffffffff812f5771>] ? strncpy_from_user+0x31/0x40
[272077.289717]  [<ffffffff81172caa>] ? do_getname+0x10a/0x180
[272077.289720]  [<ffffffff815f1dfe>] ? _raw_spin_lock+0xe/0x20
[272077.289723]  [<ffffffff81184cd7>] ? alloc_fd+0xf7/0x150
[272077.289726]  [<ffffffff8116759d>] do_sys_open+0xed/0x220
[272077.289729]  [<ffffffff811676f0>] sys_open+0x20/0x30
[272077.289732]  [<ffffffff815fa1c2>] system_call_fastpath+0x16/0x1b
[272077.289748] INFO: task hald-addon-stor:3930 blocked for more than 120 seconds.
[272077.289749] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[272077.289751] hald-addon-stor D 0000000000000000     0  3930  24735 0x00000000
[272077.289754]  ffff880203819928 0000000000000086 ffff880203819918 ffffffff8104f536
[272077.289757]  ffff880203819fd8 ffff880203819fd8 ffff880203819fd8 0000000000012a40
[272077.289760]  ffff8802314dae40 ffff8802056a9720 ffff8802055e5c80 7fffffffffffffff
[272077.289763] Call Trace:
[272077.289767]  [<ffffffff8104f536>] ? check_preempt_wakeup+0x196/0x260
[272077.289770]  [<ffffffff815eff1f>] schedule+0x3f/0x60
[272077.289772]  [<ffffffff815f0565>] schedule_timeout+0x2a5/0x320
[272077.289776]  [<ffffffff8104a3b6>] ? ttwu_do_activate.constprop.174+0x66/0x70
[272077.289779]  [<ffffffff810329b9>] ? default_spin_lock_flags+0x9/0x10
[272077.289782]  [<ffffffff815efd5f>] wait_for_common+0xdf/0x180
[272077.289785]  [<ffffffff81057340>] ? try_to_wake_up+0x200/0x200
[272077.289787]  [<ffffffff815efedd>] wait_for_completion+0x1d/0x20
[272077.289790]  [<ffffffff8107d14e>] flush_work+0x2e/0x40
[272077.289794]  [<ffffffff81079450>] ? do_work_for_cpu+0x30/0x30
[272077.289797]  [<ffffffff8107d1ab>] flush_delayed_work+0x4b/0x60
[272077.289800]  [<ffffffff812da224>] disk_clear_events+0x84/0x130
[272077.289803]  [<ffffffff8119ca47>] check_disk_change+0x37/0x80
[272077.289807]  [<ffffffff814071ad>] sd_open+0xad/0x1e0
[272077.289809]  [<ffffffff8119e1ab>] __blkdev_get+0x2eb/0x420
[272077.289811]  [<ffffffff8119e33e>] blkdev_get+0x5e/0x1e0
[272077.289814]  [<ffffffff8119e520>] blkdev_open+0x60/0x90
[272077.289817]  [<ffffffff81165d64>] __dentry_open+0x144/0x320
[272077.289819]  [<ffffffff8119e4c0>] ? blkdev_get+0x1e0/0x1e0
[272077.289822]  [<ffffffff811674ad>] nameidata_to_filp+0xad/0xb0
[272077.289825]  [<ffffffff811755f0>] do_last+0x3a0/0x730
[272077.289827]  [<ffffffff811774fa>] path_openat+0xca/0x3f0
[272077.289830]  [<ffffffff812eaa97>] ? kobject_put+0x27/0x60
[272077.289832]  [<ffffffff813cba97>] ? put_device+0x17/0x20
[272077.289835]  [<ffffffff81177922>] do_filp_open+0x42/0xa0
[272077.289838]  [<ffffffff812f5771>] ? strncpy_from_user+0x31/0x40
[272077.289841]  [<ffffffff81172caa>] ? do_getname+0x10a/0x180
[272077.289843]  [<ffffffff815f1dfe>] ? _raw_spin_lock+0xe/0x20
[272077.289845]  [<ffffffff81184cd7>] ? alloc_fd+0xf7/0x150
[272077.289848]  [<ffffffff8116759d>] do_sys_open+0xed/0x220
[272077.289851]  [<ffffffff811676f0>] sys_open+0x20/0x30
[272077.289854]  [<ffffffff815fa1c2>] system_call_fastpath+0x16/0x1b
[272087.590502] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272087.767475] sd 8:0:0:0: [sdb] Unhandled error code
[272087.767484] sd 8:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[272087.767492] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 9f f8 00 00 01 00
[272087.767511] end_request: I/O error, dev sdb, sector 15769592
[272087.767521] Buffer I/O error on device sdb1, logical block 1970951
[272118.556555] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272149.586728] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272180.616949] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272197.251439] INFO: task fdisk:4023 blocked for more than 120 seconds.
[272197.251448] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[272197.251454] fdisk           D 0000000000000001     0  4023   4022 0x00000004
[272197.251466]  ffff880214c1bb18 0000000000000086 ffff8801bfff6a00 0000000000000000
[272197.251475]  ffff880214c1bfd8 ffff880214c1bfd8 ffff880214c1bfd8 0000000000012a40
[272197.251484]  ffff8800a970dc80 ffff88022cb20000 0000000000800010 ffff88022ea09058
[272197.251493] Call Trace:
[272197.251507]  [<ffffffff815eff1f>] schedule+0x3f/0x60
[272197.251516]  [<ffffffff815f0d27>] __mutex_lock_slowpath+0xd7/0x150
[272197.251523]  [<ffffffff815f093a>] mutex_lock+0x2a/0x50
[272197.251532]  [<ffffffff8119df3b>] __blkdev_get+0x7b/0x420
[272197.251539]  [<ffffffff8119e33e>] blkdev_get+0x5e/0x1e0
[272197.251546]  [<ffffffff8119e520>] blkdev_open+0x60/0x90
[272197.251557]  [<ffffffff81165d64>] __dentry_open+0x144/0x320
[272197.251564]  [<ffffffff8119e4c0>] ? blkdev_get+0x1e0/0x1e0
[272197.251573]  [<ffffffff811674ad>] nameidata_to_filp+0xad/0xb0
[272197.251584]  [<ffffffff811755f0>] do_last+0x3a0/0x730
[272197.251590]  [<ffffffff811774fa>] path_openat+0xca/0x3f0
[272197.251599]  [<ffffffff810329b9>] ? default_spin_lock_flags+0x9/0x10
[272197.251607]  [<ffffffff81177922>] do_filp_open+0x42/0xa0
[272197.251617]  [<ffffffff812f5771>] ? strncpy_from_user+0x31/0x40
[272197.251626]  [<ffffffff81172caa>] ? do_getname+0x10a/0x180
[272197.251633]  [<ffffffff815f1dfe>] ? _raw_spin_lock+0xe/0x20
[272197.251640]  [<ffffffff81184cd7>] ? alloc_fd+0xf7/0x150
[272197.251649]  [<ffffffff8116759d>] do_sys_open+0xed/0x220
[272197.251655]  [<ffffffff811695e5>] ? fput+0x25/0x30
[272197.251663]  [<ffffffff811676f0>] sys_open+0x20/0x30
[272197.251671]  [<ffffffff815fa1c2>] system_call_fastpath+0x16/0x1b
[272211.583023] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272242.549214] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272273.515286] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272273.692090] sd 8:0:0:0: [sdb] Unhandled error code
[272273.692099] sd 8:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[272273.692107] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 9f f8 00 00 01 00
[272273.692126] end_request: I/O error, dev sdb, sector 15769592
[272273.692137] Buffer I/O error on device sdb1, logical block 1970951
:~$ 

```

---

### Post by lechien73 on 2012-02-03
It looks like the problem I'd described.

The size is reported as:

```
[271201.965799] sd 7:0:0:0: [sdb] 15769600 512-byte logical blocks: (8.07 GB/7.51 GiB)
```

On every other 8Gb device I have, the size is reported as:

```
[ 4572.859157] sd 3:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
```

So, I would say that the size is being mis-reported, and suggest that you follow the steps in the Italian blog post I gave you. It does seem that you need access to a Windows PC in order to fix the problem, though.

---

### Post by happyisland on 2012-02-03
> **lechien73 said:**
> It looks like the problem I'd described.

The size is reported as:

```
[271201.965799] sd 7:0:0:0: [sdb] 15769600 512-byte logical blocks: (8.07 GB/7.51 GiB)
```

On every other 8Gb device I have, the size is reported as:

```
[ 4572.859157] sd 3:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
```

So, I would say that the size is being mis-reported, and suggest that you follow the steps in the Italian blog post I gave you. It does seem that **you need access to a Windows PC in order to fix the problem**, though.

Oh noeesssss! I've eliminated all Windows PCs from my life ever since I switched over to Ubuntu a few years ago. 

Thanks for the help anyway - and if anybody knows of a linux-friendly approach to fixing this problem please let me know.

---

### Post by kevdog on 2012-02-03
Your getting a bunch of these errors:
[272211.583023] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272242.549214] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd
[272273.515286] usb 2-1.2: reset high speed USB device number 6 using ehci_hcd

not sure what I can do about those.

---

