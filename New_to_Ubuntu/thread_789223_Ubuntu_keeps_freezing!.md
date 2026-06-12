---
title: "Ubuntu keeps freezing!"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by jamieh on 2008-05-10
I have two drives in my computer, one has Ubuntu 8.04 and one has XP, the XP drive doesn't have this problem, but after about two hours on the Ubuntu drive, it just freezes. The mouse won't move, the keyboard won't work, and if a song is playing, it keeps playing a 0.00001 second long note over and over again. Ctrl-Alt-Backspace has no effect, I have to push the Reset button.

This happened as soon as I converted my extra drive to an Ubuntu drive. And if it makes a difference, it's a 30GB Maxtor DiamondMax, and it sits vertically in the case, whereas the Windows drive is horizontal. Could that be the problem?

Thanks in advance!

---

### Post by Canis familiaris on 2008-05-10
Try to disable all partitions in that Maxtor Drive i.e. Do NOT mount them at bootup. You can edit /etc/fstab and remove the lines corresponding partitions of the Maxtor. (Backup your fstab first though)

```
sudo cp /etc/stab /etc/fstab.bak
sudo gedit /etc/fstab

```

---

### Post by aimpau on 2008-05-10
> **jamieh said:**
> I have two drives in my computer, one has Ubuntu 8.04 and one has XP, the XP drive doesn't have this problem, but after about two hours on the Ubuntu drive, it just freezes. The mouse won't move, the keyboard won't work, and if a song is playing, it keeps playing a 0.00001 second long note over and over again. Ctrl-Alt-Backspace has no effect, I have to push the Reset button.

This happened as soon as I converted my extra drive to an Ubuntu drive. And if it makes a difference, it's a 30GB Maxtor DiamondMax, and it sits vertically in the case, whereas the Windows drive is horizontal. Could that be the problem?

Thanks in advance!

I have mine positioned vertically also and I do have 2 HDD with the other being XP.

It's not really about the positioning or the HDD. Ubuntu users have encountered lockups too including me.

if you can, type:

```
sudo gedit /var/log/syslog
```

and post it here.

---

### Post by jamieh on 2008-05-10
> **aimpau said:**
> I have mine positioned vertically also and I do have 2 HDD with the other being XP.

It's not really about the positioning or the HDD. Ubuntu users have encountered lockups too including me.

if you can, type:

```
sudo gedit /var/log/syslog
```

and post it here.

I don't understand any of this long code, but if you can, please help me!

```
May 10 08:04:31 jamie-ubuntu syslogd 1.5.0#1ubuntu1: restart.
May 10 08:04:31 jamie-ubuntu anacron[5407]: Job `cron.daily' terminated (exit status: 1) (mailing output)
May 10 08:04:31 jamie-ubuntu anacron[5407]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
May 10 08:04:31 jamie-ubuntu anacron[5407]: Normal exit (1 job run)
May 10 08:17:02 jamie-ubuntu /USR/SBIN/CRON[8349]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 10 08:19:17 jamie-ubuntu NetworkManager: <info>  Supplicant state changed: 1 
May 10 08:23:17 jamie-ubuntu NetworkManager: <info>  Supplicant state changed: 1 
May 10 16:51:08 jamie-ubuntu syslogd 1.5.0#1ubuntu1: restart.
May 10 16:51:08 jamie-ubuntu kernel: Inspecting /boot/System.map-2.6.24-16-generic
May 10 16:51:08 jamie-ubuntu kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
May 10 16:51:08 jamie-ubuntu kernel: Symbols match kernel version 2.6.24.
May 10 16:51:08 jamie-ubuntu kernel: Loaded 32476 symbols from 81 modules.
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] 511MB LOWMEM available.
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 131052) 0 entries of 256 used
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Zone PFN ranges:
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]   DMA             0 ->     4096
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]   Normal       4096 ->   131052
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]   HighMem    131052 ->   131052
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Movable zone start PFN for each node
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]     0:        0 ->   131052
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] On node 0 totalpages: 131052
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]   Normal zone: 991 pages used for memmap
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]   Normal zone: 125965 pages, LIFO batch:31
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] DMI 2.3 present.
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 ASUS  )
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] ACPI: RSDT 1FFEC000, 002C (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] ACPI: FACP 1FFEC080, 0074 (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] ACPI: DSDT 1FFEC100, 291E (r1   ASUS A7A266       1000 MSFT  100000B)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] ACPI: FACS 1FFFF000, 0040
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] ACPI: BOOT 1FFEC040, 0028 (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130029
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Kernel command line: root=UUID=9f65524a-b784-4baa-b7f6-6e62db2cecf1 ro quiet splash
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] mapped APIC to ffffb000 (0140d000)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Initializing CPU#0
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
May 10 16:51:08 jamie-ubuntu kernel: [    0.000000] Detected 1410.260 MHz processor.
May 10 16:51:08 jamie-ubuntu kernel: [   37.023414] Console: colour VGA+ 80x25
May 10 16:51:08 jamie-ubuntu kernel: [   37.023419] console [tty0] enabled
May 10 16:51:08 jamie-ubuntu kernel: [   37.024014] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
May 10 16:51:08 jamie-ubuntu kernel: [   37.024447] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
May 10 16:51:08 jamie-ubuntu kernel: [   37.051238] Memory: 507300k/524208k available (2157k kernel code, 16308k reserved, 998k data, 364k init, 0k highmem)
May 10 16:51:08 jamie-ubuntu kernel: [   37.051252] virtual kernel memory layout:
May 10 16:51:08 jamie-ubuntu kernel: [   37.051253]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May 10 16:51:08 jamie-ubuntu kernel: [   37.051255]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May 10 16:51:08 jamie-ubuntu kernel: [   37.051257]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
May 10 16:51:08 jamie-ubuntu kernel: [   37.051259]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
May 10 16:51:08 jamie-ubuntu kernel: [   37.051260]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
May 10 16:51:08 jamie-ubuntu kernel: [   37.051262]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
May 10 16:51:08 jamie-ubuntu kernel: [   37.051264]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
May 10 16:51:08 jamie-ubuntu kernel: [   37.051270] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May 10 16:51:08 jamie-ubuntu kernel: [   37.051334] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
May 10 16:51:08 jamie-ubuntu kernel: [   37.131362] Calibrating delay using timer specific routine.. 2822.62 BogoMIPS (lpj=5645254)
May 10 16:51:08 jamie-ubuntu kernel: [   37.131408] Security Framework initialized
May 10 16:51:08 jamie-ubuntu kernel: [   37.131418] SELinux:  Disabled at boot.
May 10 16:51:08 jamie-ubuntu kernel: [   37.131450] AppArmor: AppArmor initialized
May 10 16:51:08 jamie-ubuntu kernel: [   37.131457] Failure registering capabilities with primary security module.
May 10 16:51:08 jamie-ubuntu kernel: [   37.131472] Mount-cache hash table entries: 512
May 10 16:51:08 jamie-ubuntu kernel: [   37.131669] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000 00000000
May 10 16:51:08 jamie-ubuntu kernel: [   37.131684] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May 10 16:51:08 jamie-ubuntu kernel: [   37.131688] CPU: L2 Cache: 256K (64 bytes/line)
May 10 16:51:08 jamie-ubuntu kernel: [   37.131693] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000 00000000
May 10 16:51:08 jamie-ubuntu kernel: [   37.131708] Compat vDSO mapped to ffffe000.
May 10 16:51:08 jamie-ubuntu kernel: [   37.131728] Checking 'hlt' instruction... OK.
May 10 16:51:08 jamie-ubuntu kernel: [   37.147422] SMP alternatives: switching to UP code
May 10 16:51:08 jamie-ubuntu kernel: [   37.149020] Freeing SMP alternatives: 11k freed
May 10 16:51:08 jamie-ubuntu kernel: [   37.149230] Early unpacking initramfs... done
May 10 16:51:08 jamie-ubuntu kernel: [   37.657446] ACPI: Core revision 20070126
May 10 16:51:08 jamie-ubuntu kernel: [   37.657593] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 10 16:51:08 jamie-ubuntu kernel: [   37.658711] ACPI: setting ELCR to 0200 (from 0e60)
May 10 16:51:08 jamie-ubuntu kernel: [   37.659047] CPU0: AMD Athlon(TM)Processor stepping 04
May 10 16:51:08 jamie-ubuntu kernel: [   37.659057] SMP motherboard not detected.
May 10 16:51:08 jamie-ubuntu kernel: [   37.659061] Local APIC not detected. Using dummy APIC emulation.
May 10 16:51:08 jamie-ubuntu kernel: [   37.659144] Brought up 1 CPUs
May 10 16:51:08 jamie-ubuntu kernel: [   37.659188] CPU0 attaching sched-domain:
May 10 16:51:08 jamie-ubuntu kernel: [   37.659193]  domain 0: span 01
May 10 16:51:08 jamie-ubuntu kernel: [   37.659195]   groups: 01
May 10 16:51:08 jamie-ubuntu kernel: [   37.659561] net_namespace: 64 bytes
May 10 16:51:08 jamie-ubuntu kernel: [   37.659574] Booting paravirtualized kernel on bare hardware
May 10 16:51:08 jamie-ubuntu kernel: [   37.660315] Time: 16:50:27  Date: 05/10/08
May 10 16:51:08 jamie-ubuntu kernel: [   37.660370] NET: Registered protocol family 16
May 10 16:51:08 jamie-ubuntu kernel: [   37.660710] EISA bus registered
May 10 16:51:08 jamie-ubuntu kernel: [   37.660731] ACPI: bus type pci registered
May 10 16:51:08 jamie-ubuntu kernel: [   37.662449] PCI: PCI BIOS revision 2.10 entry at 0xf1170, last bus=1
May 10 16:51:08 jamie-ubuntu kernel: [   37.662453] PCI: Using configuration type 1
May 10 16:51:08 jamie-ubuntu kernel: [   37.662455] Setting up standard PCI resources
May 10 16:51:08 jamie-ubuntu kernel: [   37.674043] ACPI: EC: Look up EC in DSDT
May 10 16:51:08 jamie-ubuntu kernel: [   37.677444] ACPI: Interpreter enabled
May 10 16:51:08 jamie-ubuntu kernel: [   37.677450] ACPI: (supports S0 S1 S4 S5)
May 10 16:51:08 jamie-ubuntu kernel: [   37.677469] ACPI: Using PIC for interrupt routing
May 10 16:51:08 jamie-ubuntu kernel: [   37.684126] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 10 16:51:08 jamie-ubuntu kernel: [   37.684686] PCI quirk: region e400-e43f claimed by ali7101 ACPI
May 10 16:51:08 jamie-ubuntu kernel: [   37.684691] PCI quirk: region e800-e81f claimed by ali7101 SMB
May 10 16:51:08 jamie-ubuntu kernel: [   37.684834] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 10 16:51:08 jamie-ubuntu kernel: [   37.685071] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
May 10 16:51:08 jamie-ubuntu kernel: [   37.686778] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May 10 16:51:08 jamie-ubuntu kernel: [   37.686938] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
May 10 16:51:08 jamie-ubuntu kernel: [   37.687094] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May 10 16:51:08 jamie-ubuntu kernel: [   37.687246] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
May 10 16:51:08 jamie-ubuntu kernel: [   37.687510] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 16:51:08 jamie-ubuntu kernel: [   37.687667] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 16:51:08 jamie-ubuntu kernel: [   37.687758] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May 10 16:51:08 jamie-ubuntu kernel: [   37.687847] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May 10 16:51:08 jamie-ubuntu kernel: [   37.688002] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 16:51:08 jamie-ubuntu kernel: [   37.688320] Linux Plug and Play Support v0.97 (c) Adam Belay
May 10 16:51:08 jamie-ubuntu kernel: [   37.688370] pnp: PnP ACPI init
May 10 16:51:08 jamie-ubuntu kernel: [   37.688386] ACPI: bus type pnp registered
May 10 16:51:08 jamie-ubuntu kernel: [   37.693369] pnp: PnP ACPI: found 14 devices
May 10 16:51:08 jamie-ubuntu kernel: [   37.693373] ACPI: ACPI bus type pnp unregistered
May 10 16:51:08 jamie-ubuntu kernel: [   37.693379] PnPBIOS: Disabled by ACPI PNP
May 10 16:51:08 jamie-ubuntu kernel: [   37.693766] PCI: Using ACPI for IRQ routing
May 10 16:51:08 jamie-ubuntu kernel: [   37.693772] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 10 16:51:08 jamie-ubuntu kernel: [   37.693808] PCI: Cannot allocate resource region 0 of device 0000:00:0c.2
May 10 16:51:08 jamie-ubuntu kernel: [   37.719360] NET: Registered protocol family 8
May 10 16:51:08 jamie-ubuntu kernel: [   37.719363] NET: Registered protocol family 20
May 10 16:51:08 jamie-ubuntu kernel: [   37.719489] AppArmor: AppArmor Filesystem Enabled
May 10 16:51:08 jamie-ubuntu kernel: [   37.723344] Time: tsc clocksource has been installed.
May 10 16:51:08 jamie-ubuntu kernel: [   37.731404] system 00:00: iomem range 0x0-0x9ffff could not be reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.731409] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.731414] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.731418] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.731430] system 00:02: ioport range 0xe400-0xe47f could not be reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.731434] system 00:02: ioport range 0xe800-0xe81f has been reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.731438] system 00:02: ioport range 0x40b-0x40b has been reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.731442] system 00:02: ioport range 0x480-0x48f has been reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.731446] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.731459] system 00:03: iomem range 0xfffe0000-0xffffffff could not be reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.731470] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
May 10 16:51:08 jamie-ubuntu kernel: [   37.762148] PCI: Bridge: 0000:00:01.0
May 10 16:51:08 jamie-ubuntu kernel: [   37.762152]   IO window: disabled.
May 10 16:51:08 jamie-ubuntu kernel: [   37.762158]   MEM window: de000000-dfdfffff
May 10 16:51:08 jamie-ubuntu kernel: [   37.762162]   PREFETCH window: dff00000-efffffff
May 10 16:51:08 jamie-ubuntu kernel: [   37.762178] PCI: Setting latency timer of device 0000:00:01.0 to 64
May 10 16:51:08 jamie-ubuntu kernel: [   37.762197] NET: Registered protocol family 2
May 10 16:51:08 jamie-ubuntu kernel: [   37.799486] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
May 10 16:51:08 jamie-ubuntu kernel: [   37.799844] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
May 10 16:51:08 jamie-ubuntu kernel: [   37.800246] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
May 10 16:51:08 jamie-ubuntu kernel: [   37.800652] TCP: Hash tables configured (established 16384 bind 16384)
May 10 16:51:08 jamie-ubuntu kernel: [   37.800657] TCP reno registered
May 10 16:51:08 jamie-ubuntu kernel: [   37.811588] checking if image is initramfs... it is
May 10 16:51:08 jamie-ubuntu kernel: [   38.263376] Switched to high resolution mode on CPU 0
May 10 16:51:08 jamie-ubuntu kernel: [   38.772779] Freeing initrd memory: 7697k freed
May 10 16:51:08 jamie-ubuntu kernel: [   38.773075] Simple Boot Flag at 0x3a set to 0x1
May 10 16:51:08 jamie-ubuntu kernel: [   38.773820] audit: initializing netlink socket (disabled)
May 10 16:51:08 jamie-ubuntu kernel: [   38.773845] audit(1210438227.724:1): initialized
May 10 16:51:08 jamie-ubuntu kernel: [   38.776965] VFS: Disk quotas dquot_6.5.1
May 10 16:51:08 jamie-ubuntu kernel: [   38.777096] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 10 16:51:08 jamie-ubuntu kernel: [   38.777328] io scheduler noop registered
May 10 16:51:08 jamie-ubuntu kernel: [   38.777332] io scheduler anticipatory registered
May 10 16:51:08 jamie-ubuntu kernel: [   38.777335] io scheduler deadline registered
May 10 16:51:08 jamie-ubuntu kernel: [   38.777350] io scheduler cfq registered (default)
May 10 16:51:08 jamie-ubuntu kernel: [   38.777368] Limiting direct PCI/PCI transfers.
May 10 16:51:08 jamie-ubuntu kernel: [   38.777397] Activating ISA DMA hang workarounds.
May 10 16:51:08 jamie-ubuntu kernel: [   38.777429] Boot video device is 0000:01:00.0
May 10 16:51:08 jamie-ubuntu kernel: [   38.777866] isapnp: Scanning for PnP cards...
May 10 16:51:08 jamie-ubuntu kernel: [   39.132060] isapnp: No Plug & Play device found
May 10 16:51:08 jamie-ubuntu kernel: [   39.178323] Real Time Clock Driver v1.12ac
May 10 16:51:08 jamie-ubuntu kernel: [   39.178497] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 10 16:51:08 jamie-ubuntu kernel: [   39.178729] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 10 16:51:08 jamie-ubuntu kernel: [   39.178970] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 10 16:51:08 jamie-ubuntu kernel: [   39.179979] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 10 16:51:08 jamie-ubuntu kernel: [   39.180569] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 10 16:51:08 jamie-ubuntu kernel: [   39.181855] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 10 16:51:08 jamie-ubuntu kernel: [   39.181969] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 10 16:51:08 jamie-ubuntu kernel: [   39.182137] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May 10 16:51:08 jamie-ubuntu kernel: [   39.184934] serio: i8042 KBD port at 0x60,0x64 irq 1
May 10 16:51:08 jamie-ubuntu kernel: [   39.184943] serio: i8042 AUX port at 0x60,0x64 irq 12
May 10 16:51:08 jamie-ubuntu kernel: [   39.187339] mice: PS/2 mouse device common for all mice
May 10 16:51:08 jamie-ubuntu kernel: [   39.187559] EISA: Probing bus 0 at eisa.0
May 10 16:51:08 jamie-ubuntu kernel: [   39.187618] EISA: Detected 0 cards.
May 10 16:51:08 jamie-ubuntu kernel: [   39.187624] cpuidle: using governor ladder
May 10 16:51:08 jamie-ubuntu kernel: [   39.187627] cpuidle: using governor menu
May 10 16:51:08 jamie-ubuntu kernel: [   39.187854] NET: Registered protocol family 1
May 10 16:51:08 jamie-ubuntu kernel: [   39.187901] Using IPI No-Shortcut mode
May 10 16:51:08 jamie-ubuntu kernel: [   39.187958] registered taskstats version 1
May 10 16:51:08 jamie-ubuntu kernel: [   39.188118]   Magic number: 8:229:843
May 10 16:51:08 jamie-ubuntu kernel: [   39.188291]   hash matches device ptyu9
May 10 16:51:08 jamie-ubuntu kernel: [   39.188310]   hash matches device ptyrc
May 10 16:51:08 jamie-ubuntu kernel: [   39.188392] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 10 16:51:08 jamie-ubuntu kernel: [   39.188395] EDD information not available.
May 10 16:51:08 jamie-ubuntu kernel: [   39.189072] Freeing unused kernel memory: 364k freed
May 10 16:51:08 jamie-ubuntu kernel: [   39.215110] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May 10 16:51:08 jamie-ubuntu kernel: [   40.551183] fuse init (API version 7.9)
May 10 16:51:08 jamie-ubuntu kernel: [   40.584267] ACPI: Invalid PBLK length [5]
May 10 16:51:08 jamie-ubuntu kernel: [   41.490767] usbcore: registered new interface driver usbfs
May 10 16:51:08 jamie-ubuntu kernel: [   41.490809] usbcore: registered new interface driver hub
May 10 16:51:08 jamie-ubuntu kernel: [   41.499733] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May 10 16:51:08 jamie-ubuntu kernel: [   41.499745] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May 10 16:51:08 jamie-ubuntu kernel: [   41.523345] usbcore: registered new device driver usb
May 10 16:51:08 jamie-ubuntu kernel: [   41.543778] ALI15X3: IDE controller (0x10b9:0x5229 rev 0xc4) at  PCI slot 0000:00:04.0
May 10 16:51:08 jamie-ubuntu kernel: [   41.543816] ACPI: Unable to derive IRQ for device 0000:00:04.0
May 10 16:51:08 jamie-ubuntu kernel: [   41.543829] ALI15X3: not 100% native mode: will probe irqs later
May 10 16:51:08 jamie-ubuntu kernel: [   41.543854]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:DMA
May 10 16:51:08 jamie-ubuntu kernel: [   41.543873]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:DMA
May 10 16:51:08 jamie-ubuntu kernel: [   41.543891] Probing IDE interface ide0...
May 10 16:51:08 jamie-ubuntu kernel: [   41.566850] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May 10 16:51:08 jamie-ubuntu kernel: [   41.602643] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
May 10 16:51:08 jamie-ubuntu kernel: [   41.830785] hdb: Maxtor 6E030L0, ATA DISK drive
May 10 16:51:08 jamie-ubuntu kernel: [   42.166677] hda: Maxtor 6Y060L0, ATA DISK drive
May 10 16:51:08 jamie-ubuntu kernel: [   42.166702] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 16:51:08 jamie-ubuntu kernel: [   42.166824] hda: UDMA/100 mode selected
May 10 16:51:08 jamie-ubuntu kernel: [   42.166917] hdb: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 16:51:08 jamie-ubuntu kernel: [   42.167018] hdb: UDMA/100 mode selected
May 10 16:51:08 jamie-ubuntu kernel: [   42.167172] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
May 10 16:51:08 jamie-ubuntu kernel: [   42.180025] Probing IDE interface ide1...
May 10 16:51:08 jamie-ubuntu kernel: [   42.970490] hdd: HL-DT-STDVD-ROM GDR8164B, ATAPI CD/DVD-ROM drive
May 10 16:51:08 jamie-ubuntu kernel: [   43.754331] hdc: Hewlett-Packard CD-Writer Plus 8100, ATAPI CD/DVD-ROM drive
May 10 16:51:08 jamie-ubuntu kernel: [   43.754355] hdc: applying conservative PIO "downgrade"
May 10 16:51:08 jamie-ubuntu kernel: [   43.754359] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO2
May 10 16:51:08 jamie-ubuntu kernel: [   43.754903] hdc: MWDMA1 mode selected
May 10 16:51:08 jamie-ubuntu kernel: [   43.755459] hdd: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 16:51:08 jamie-ubuntu kernel: [   43.755889] hdd: UDMA/33 mode selected
May 10 16:51:08 jamie-ubuntu kernel: [   43.756496] ide1 at 0x170-0x177,0x376 on irq 15
May 10 16:51:08 jamie-ubuntu kernel: [   43.777509] ACPI: PCI Interrupt Link [LNKI] enabled at IRQ 9
May 10 16:51:08 jamie-ubuntu kernel: [   43.777518] PCI: setting IRQ 9 as level-triggered
May 10 16:51:08 jamie-ubuntu kernel: [   43.777522] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKI] -> GSI 9 (level, low) -> IRQ 9
May 10 16:51:08 jamie-ubuntu kernel: [   43.777545] ohci_hcd 0000:00:02.0: OHCI Host Controller
May 10 16:51:08 jamie-ubuntu kernel: [   43.777959] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
May 10 16:51:08 jamie-ubuntu kernel: [   43.777987] ohci_hcd 0000:00:02.0: irq 9, io mem 0xdd800000
May 10 16:51:08 jamie-ubuntu kernel: [   43.779855] SCSI subsystem initialized
May 10 16:51:08 jamie-ubuntu kernel: [   43.794010] libata version 3.00 loaded.
May 10 16:51:08 jamie-ubuntu kernel: [   43.832352] usb usb1: configuration #1 chosen from 1 choice
May 10 16:51:08 jamie-ubuntu kernel: [   43.832396] hub 1-0:1.0: USB hub found
May 10 16:51:08 jamie-ubuntu kernel: [   43.832410] hub 1-0:1.0: 4 ports detected
May 10 16:51:08 jamie-ubuntu kernel: [   43.934791] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
May 10 16:51:08 jamie-ubuntu kernel: [   43.934799] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
May 10 16:51:08 jamie-ubuntu kernel: [   43.934825] ohci_hcd 0000:00:06.0: OHCI Host Controller
May 10 16:51:08 jamie-ubuntu kernel: [   43.934873] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 2
May 10 16:51:08 jamie-ubuntu kernel: [   43.934895] ohci_hcd 0000:00:06.0: irq 9, io mem 0xdc800000
May 10 16:51:08 jamie-ubuntu kernel: [   43.992242] usb usb2: configuration #1 chosen from 1 choice
May 10 16:51:08 jamie-ubuntu kernel: [   43.992282] hub 2-0:1.0: USB hub found
May 10 16:51:08 jamie-ubuntu kernel: [   43.992294] hub 2-0:1.0: 2 ports detected
May 10 16:51:08 jamie-ubuntu kernel: [   44.094764] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
May 10 16:51:08 jamie-ubuntu kernel: [   44.094772] PCI: setting IRQ 11 as level-triggered
May 10 16:51:08 jamie-ubuntu kernel: [   44.094777] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
May 10 16:51:08 jamie-ubuntu kernel: [   44.094802] ohci_hcd 0000:00:0c.0: OHCI Host Controller
May 10 16:51:08 jamie-ubuntu kernel: [   44.094850] ohci_hcd 0000:00:0c.0: new USB bus registered, assigned bus number 3
May 10 16:51:08 jamie-ubuntu kernel: [   44.094873] ohci_hcd 0000:00:0c.0: irq 11, io mem 0xda800000
May 10 16:51:08 jamie-ubuntu kernel: [   44.181574] usb usb3: configuration #1 chosen from 1 choice
May 10 16:51:08 jamie-ubuntu kernel: [   44.181827] hub 3-0:1.0: USB hub found
May 10 16:51:08 jamie-ubuntu kernel: [   44.181842] hub 3-0:1.0: 3 ports detected
May 10 16:51:08 jamie-ubuntu kernel: [   44.238046] usb 1-3: new full speed USB device using ohci_hcd and address 2
May 10 16:51:08 jamie-ubuntu kernel: [   44.282712] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
May 10 16:51:08 jamie-ubuntu kernel: [   44.282718] PCI: setting IRQ 10 as level-triggered
May 10 16:51:08 jamie-ubuntu kernel: [   44.282723] ACPI: PCI Interrupt 0000:00:0c.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
May 10 16:51:08 jamie-ubuntu kernel: [   44.282748] ohci_hcd 0000:00:0c.1: OHCI Host Controller
May 10 16:51:08 jamie-ubuntu kernel: [   44.282800] ohci_hcd 0000:00:0c.1: new USB bus registered, assigned bus number 4
May 10 16:51:08 jamie-ubuntu kernel: [   44.282822] ohci_hcd 0000:00:0c.1: irq 10, io mem 0xda000000
May 10 16:51:08 jamie-ubuntu kernel: [   44.369545] usb usb4: configuration #1 chosen from 1 choice
May 10 16:51:08 jamie-ubuntu kernel: [   44.369807] hub 4-0:1.0: USB hub found
May 10 16:51:08 jamie-ubuntu kernel: [   44.369822] hub 4-0:1.0: 2 ports detected
May 10 16:51:08 jamie-ubuntu kernel: [   44.471246] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
May 10 16:51:08 jamie-ubuntu kernel: [   44.471254] PCI: setting IRQ 5 as level-triggered
May 10 16:51:08 jamie-ubuntu kernel: [   44.471259] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
May 10 16:51:08 jamie-ubuntu kernel: [   44.486344] eth0: VIA Rhine at 0xd9800000, 00:50:ba:a1:9f:88, IRQ 5.
May 10 16:51:08 jamie-ubuntu kernel: [   44.494424] ACPI: PCI Interrupt 0000:00:0c.2[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
May 10 16:51:08 jamie-ubuntu kernel: [   44.494452] ehci_hcd 0000:00:0c.2: EHCI Host Controller
May 10 16:51:08 jamie-ubuntu kernel: [   44.494508] ehci_hcd 0000:00:0c.2: new USB bus registered, assigned bus number 5
May 10 16:51:08 jamie-ubuntu kernel: [   44.494573] ehci_hcd 0000:00:0c.2: irq 5, io mem 0x30000000
May 10 16:51:08 jamie-ubuntu kernel: [   44.506022] ehci_hcd 0000:00:0c.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May 10 16:51:08 jamie-ubuntu kernel: [   44.506227] usb usb5: configuration #1 chosen from 1 choice
May 10 16:51:08 jamie-ubuntu kernel: [   44.506278] hub 5-0:1.0: USB hub found
May 10 16:51:08 jamie-ubuntu kernel: [   44.506291] hub 5-0:1.0: 5 ports detected
May 10 16:51:08 jamie-ubuntu kernel: [   44.545186] usb 1-3: configuration #1 chosen from 1 choice
May 10 16:51:08 jamie-ubuntu kernel: [   44.646108] hda: max request size: 128KiB
May 10 16:51:08 jamie-ubuntu kernel: [   44.646349] hda: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63
May 10 16:51:08 jamie-ubuntu kernel: [   44.647216] hda: cache flushes supported
May 10 16:51:08 jamie-ubuntu kernel: [   44.647286]  hda: hda1
May 10 16:51:08 jamie-ubuntu kernel: [   44.662597] hdb: max request size: 128KiB
May 10 16:51:08 jamie-ubuntu kernel: [   44.662743] hdb: 60058656 sectors (30750 MB) w/2048KiB Cache, CHS=59582/16/63
May 10 16:51:08 jamie-ubuntu kernel: [   44.662858] hdb: cache flushes supported
May 10 16:51:08 jamie-ubuntu kernel: [   44.662905]  hdb: hdb1 hdb2 < hdb5 >
May 10 16:51:08 jamie-ubuntu kernel: [   44.697973] hdc: ATAPI 24X CD-ROM CD-R/RW drive, 1024kB Cache
May 10 16:51:08 jamie-ubuntu kernel: [   44.697990] Uniform CD-ROM driver Revision: 3.20
May 10 16:51:08 jamie-ubuntu kernel: [   44.710489] hdd: ATAPI 52X DVD-ROM drive, 256kB Cache
May 10 16:51:08 jamie-ubuntu kernel: [   45.050066] usb 5-1: new high speed USB device using ehci_hcd and address 2
May 10 16:51:08 jamie-ubuntu kernel: [   45.062858] Attempting manual resume
May 10 16:51:08 jamie-ubuntu kernel: [   45.062866] swsusp: Resume From Partition 3:69
May 10 16:51:08 jamie-ubuntu kernel: [   45.062869] PM: Checking swsusp image.
May 10 16:51:08 jamie-ubuntu kernel: [   45.063206] PM: Resume from disk failed.
May 10 16:51:08 jamie-ubuntu kernel: [   45.087795] EXT3-fs: INFO: recovery required on readonly filesystem.
May 10 16:51:08 jamie-ubuntu kernel: [   45.087803] EXT3-fs: write access will be enabled during recovery.
May 10 16:51:08 jamie-ubuntu kernel: [   45.183635] usb 5-1: configuration #1 chosen from 1 choice
May 10 16:51:08 jamie-ubuntu kernel: [   45.421789] usb 5-4: new high speed USB device using ehci_hcd and address 3
May 10 16:51:08 jamie-ubuntu kernel: [   45.563117] usb 5-4: configuration #1 chosen from 1 choice
May 10 16:51:08 jamie-ubuntu kernel: [   45.563902] usbcore: registered new interface driver libusual
May 10 16:51:08 jamie-ubuntu kernel: [   45.574827] Initializing USB Mass Storage driver...
May 10 16:51:08 jamie-ubuntu kernel: [   45.579856] scsi0 : SCSI emulation for USB Mass Storage devices
May 10 16:51:08 jamie-ubuntu kernel: [   45.581844] usb-storage: device found at 2
May 10 16:51:08 jamie-ubuntu kernel: [   45.581853] usb-storage: waiting for device to settle before scanning
May 10 16:51:08 jamie-ubuntu kernel: [   45.584454] scsi1 : SCSI emulation for USB Mass Storage devices
May 10 16:51:08 jamie-ubuntu kernel: [   45.587298] usbcore: registered new interface driver usb-storage
May 10 16:51:08 jamie-ubuntu kernel: [   45.587312] USB Mass Storage support registered.
May 10 16:51:08 jamie-ubuntu kernel: [   45.587522] usb-storage: device found at 2
May 10 16:51:08 jamie-ubuntu kernel: [   45.587526] usb-storage: waiting for device to settle before scanning
May 10 16:51:08 jamie-ubuntu kernel: [   49.890207] kjournald starting.  Commit interval 5 seconds
May 10 16:51:08 jamie-ubuntu kernel: [   49.890246] EXT3-fs: hdb1: orphan cleanup on readonly fs
May 10 16:51:08 jamie-ubuntu kernel: [   49.890261] ext3_orphan_cleanup: deleting unreferenced inode 213078
May 10 16:51:08 jamie-ubuntu kernel: [   49.890316] ext3_orphan_cleanup: deleting unreferenced inode 213079
May 10 16:51:08 jamie-ubuntu kernel: [   49.890328] ext3_orphan_cleanup: deleting unreferenced inode 213080
May 10 16:51:08 jamie-ubuntu kernel: [   49.890339] ext3_orphan_cleanup: deleting unreferenced inode 213077
May 10 16:51:08 jamie-ubuntu kernel: [   49.890352] ext3_orphan_cleanup: deleting unreferenced inode 410429
May 10 16:51:08 jamie-ubuntu kernel: [   49.890394] ext3_orphan_cleanup: deleting unreferenced inode 409882
May 10 16:51:08 jamie-ubuntu kernel: [   49.890459] ext3_orphan_cleanup: deleting unreferenced inode 213063
May 10 16:51:08 jamie-ubuntu kernel: [   49.890471] ext3_orphan_cleanup: deleting unreferenced inode 213054
May 10 16:51:08 jamie-ubuntu kernel: [   49.890485] ext3_orphan_cleanup: deleting unreferenced inode 1131173
May 10 16:51:08 jamie-ubuntu kernel: [   49.922268] ext3_orphan_cleanup: deleting unreferenced inode 1132314
May 10 16:51:08 jamie-ubuntu kernel: [   49.939613] ext3_orphan_cleanup: deleting unreferenced inode 1155479
May 10 16:51:08 jamie-ubuntu kernel: [   49.953243] ext3_orphan_cleanup: deleting unreferenced inode 1155478
May 10 16:51:08 jamie-ubuntu kernel: [   49.959599] ext3_orphan_cleanup: deleting unreferenced inode 1155477
May 10 16:51:08 jamie-ubuntu kernel: [   49.959617] ext3_orphan_cleanup: deleting unreferenced inode 688146
May 10 16:51:08 jamie-ubuntu kernel: [   49.975139] ext3_orphan_cleanup: deleting unreferenced inode 688133
May 10 16:51:08 jamie-ubuntu kernel: [   49.981188] ext3_orphan_cleanup: deleting unreferenced inode 1132310
May 10 16:51:08 jamie-ubuntu kernel: [   50.008687] ext3_orphan_cleanup: deleting unreferenced inode 647224
May 10 16:51:08 jamie-ubuntu kernel: [   50.016984] ext3_orphan_cleanup: deleting unreferenced inode 647205
May 10 16:51:08 jamie-ubuntu kernel: [   50.027181] ext3_orphan_cleanup: deleting unreferenced inode 532485
May 10 16:51:08 jamie-ubuntu kernel: [   50.035393] ext3_orphan_cleanup: deleting unreferenced inode 532484
May 10 16:51:08 jamie-ubuntu kernel: [   50.035411] ext3_orphan_cleanup: deleting unreferenced inode 532482
May 10 16:51:08 jamie-ubuntu kernel: [   50.042007] ext3_orphan_cleanup: deleting unreferenced inode 1130911
May 10 16:51:08 jamie-ubuntu kernel: [   50.058005] ext3_orphan_cleanup: deleting unreferenced inode 1132412
May 10 16:51:08 jamie-ubuntu kernel: [   50.058025] ext3_orphan_cleanup: deleting unreferenced inode 1132171
May 10 16:51:08 jamie-ubuntu kernel: [   50.067261] ext3_orphan_cleanup: deleting unreferenced inode 1163938
May 10 16:51:08 jamie-ubuntu kernel: [   50.081572] ext3_orphan_cleanup: deleting unreferenced inode 1163934
May 10 16:51:08 jamie-ubuntu kernel: [   50.081592] ext3_orphan_cleanup: deleting unreferenced inode 1132459
May 10 16:51:08 jamie-ubuntu kernel: [   50.087479] ext3_orphan_cleanup: deleting unreferenced inode 1132161
May 10 16:51:08 jamie-ubuntu kernel: [   50.092611] ext3_orphan_cleanup: deleting unreferenced inode 1132316
May 10 16:51:08 jamie-ubuntu kernel: [   50.098544] ext3_orphan_cleanup: deleting unreferenced inode 1132035
May 10 16:51:08 jamie-ubuntu kernel: [   50.108126] ext3_orphan_cleanup: deleting unreferenced inode 1132273
May 10 16:51:08 jamie-ubuntu kernel: [   50.117231] ext3_orphan_cleanup: deleting unreferenced inode 1132109
May 10 16:51:08 jamie-ubuntu kernel: [   50.125654] ext3_orphan_cleanup: deleting unreferenced inode 1132107
May 10 16:51:08 jamie-ubuntu kernel: [   50.140748] ext3_orphan_cleanup: deleting unreferenced inode 1155591
May 10 16:51:08 jamie-ubuntu kernel: [   50.149012] ext3_orphan_cleanup: deleting unreferenced inode 1155584
May 10 16:51:08 jamie-ubuntu kernel: [   50.149031] ext3_orphan_cleanup: deleting unreferenced inode 1155582
May 10 16:51:08 jamie-ubuntu kernel: [   50.156824] ext3_orphan_cleanup: deleting unreferenced inode 1147702
May 10 16:51:08 jamie-ubuntu kernel: [   50.172067] ext3_orphan_cleanup: deleting unreferenced inode 1147745
May 10 16:51:08 jamie-ubuntu kernel: [   50.172233] ext3_orphan_cleanup: deleting unreferenced inode 1147731
May 10 16:51:08 jamie-ubuntu kernel: [   50.180959] ext3_orphan_cleanup: deleting unreferenced inode 1147729
May 10 16:51:08 jamie-ubuntu kernel: [   50.184927] ext3_orphan_cleanup: deleting unreferenced inode 1147725
May 10 16:51:08 jamie-ubuntu kernel: [   50.191788] ext3_orphan_cleanup: deleting unreferenced inode 1147723
May 10 16:51:08 jamie-ubuntu kernel: [   50.199911] ext3_orphan_cleanup: deleting unreferenced inode 1147717
May 10 16:51:08 jamie-ubuntu kernel: [   50.207489] ext3_orphan_cleanup: deleting unreferenced inode 1132027
May 10 16:51:08 jamie-ubuntu kernel: [   50.213979] ext3_orphan_cleanup: deleting unreferenced inode 1132025
May 10 16:51:08 jamie-ubuntu kernel: [   50.219162] ext3_orphan_cleanup: deleting unreferenced inode 1131943
May 10 16:51:08 jamie-ubuntu kernel: [   50.225349] ext3_orphan_cleanup: deleting unreferenced inode 1131941
May 10 16:51:08 jamie-ubuntu kernel: [   50.234727] ext3_orphan_cleanup: deleting unreferenced inode 1132033
May 10 16:51:08 jamie-ubuntu kernel: [   50.239129] ext3_orphan_cleanup: deleting unreferenced inode 1132373
May 10 16:51:08 jamie-ubuntu kernel: [   50.247893] ext3_orphan_cleanup: deleting unreferenced inode 1132368
May 10 16:51:08 jamie-ubuntu kernel: [   50.257315] ext3_orphan_cleanup: deleting unreferenced inode 1114157
May 10 16:51:08 jamie-ubuntu kernel: [   50.265620] ext3_orphan_cleanup: deleting unreferenced inode 213004
May 10 16:51:08 jamie-ubuntu kernel: [   50.265630] EXT3-fs: hdb1: 52 orphan inodes deleted
May 10 16:51:08 jamie-ubuntu kernel: [   50.265634] EXT3-fs: recovery complete.
May 10 16:51:08 jamie-ubuntu kernel: [   50.552149] EXT3-fs: mounted filesystem with ordered data mode.
May 10 16:51:08 jamie-ubuntu kernel: [   50.582471] usb-storage: device scan complete
May 10 16:51:08 jamie-ubuntu kernel: [   50.585496] usb-storage: device scan complete
May 10 16:51:08 jamie-ubuntu kernel: [   50.616670] scsi 1:0:0:0: Direct-Access     ST380021 A                0811 PQ: 0 ANSI: 0
May 10 16:51:08 jamie-ubuntu kernel: [   50.618435] scsi 0:0:0:0: Direct-Access     Generic  2.0 Reader   -CF 1.00 PQ: 0 ANSI: 0 CCS
May 10 16:51:08 jamie-ubuntu kernel: [   50.652503] scsi 0:0:0:1: Direct-Access     Generic  2.0 Reader   -SM 1.00 PQ: 0 ANSI: 0 CCS
May 10 16:51:08 jamie-ubuntu kernel: [   50.686515] scsi 0:0:0:2: Direct-Access     Generic  2.0 Reader   -SD 1.00 PQ: 0 ANSI: 0 CCS
May 10 16:51:08 jamie-ubuntu kernel: [   50.720490] scsi 0:0:0:3: Direct-Access     Generic  2.0 Reader   -MS 1.00 PQ: 0 ANSI: 0 CCS
May 10 16:51:08 jamie-ubuntu kernel: [   50.754415] scsi 0:0:0:4: Direct-Access     Generic  2.0 Reader   -xD 1.00 PQ: 0 ANSI: 0 CCS
May 10 16:51:08 jamie-ubuntu kernel: [   58.547180] Linux agpgart interface v0.102
May 10 16:51:08 jamie-ubuntu kernel: [   58.603322] agpgart: Detected ALi M1647 chipset
May 10 16:51:08 jamie-ubuntu kernel: [   58.682563] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 10 16:51:08 jamie-ubuntu kernel: [   58.711241] agpgart: AGP aperture is 128M @ 0xf0000000
May 10 16:51:08 jamie-ubuntu kernel: [   58.744151] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 10 16:51:08 jamie-ubuntu kernel: [   59.582501] input: Power Button (FF) as /devices/virtual/input/input2
May 10 16:51:08 jamie-ubuntu kernel: [   59.590911] ACPI: Power Button (FF) [PWRF]
May 10 16:51:08 jamie-ubuntu kernel: [   59.591100] input: Power Button (CM) as /devices/virtual/input/input3
May 10 16:51:08 jamie-ubuntu kernel: [   59.606907] ACPI: Power Button (CM) [PWRB]
May 10 16:51:08 jamie-ubuntu kernel: [   62.078514] nvidia: module license 'NVIDIA' taints kernel.
May 10 16:51:08 jamie-ubuntu kernel: [   63.032574] input: PC Speaker as /devices/platform/pcspkr/input/input4
May 10 16:51:08 jamie-ubuntu kernel: [   63.358892] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
May 10 16:51:08 jamie-ubuntu kernel: [   63.358901] PCI: setting IRQ 6 as level-triggered
May 10 16:51:08 jamie-ubuntu kernel: [   63.358906] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
May 10 16:51:08 jamie-ubuntu kernel: [   63.358935] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
May 10 16:51:08 jamie-ubuntu kernel: [   63.898913] logips2pp: Detected unknown logitech mouse model 127
May 10 16:51:08 jamie-ubuntu kernel: [   64.006103] Driver 'sd' needs updating - please use bus_type methods
May 10 16:51:08 jamie-ubuntu kernel: [   64.017144] sd 0:0:0:0: [sda] Attached SCSI removable disk
May 10 16:51:08 jamie-ubuntu kernel: [   64.028177] sd 0:0:0:1: [sdb] Attached SCSI removable disk
May 10 16:51:08 jamie-ubuntu kernel: [   64.039175] sd 0:0:0:2: [sdc] Attached SCSI removable disk
May 10 16:51:08 jamie-ubuntu kernel: [   64.050182] sd 0:0:0:3: [sdd] Attached SCSI removable disk
May 10 16:51:08 jamie-ubuntu kernel: [   64.061127] sd 0:0:0:4: [sde] Attached SCSI removable disk
May 10 16:51:08 jamie-ubuntu kernel: [   64.062462] sd 1:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
May 10 16:51:08 jamie-ubuntu kernel: [   64.063828] sd 1:0:0:0: [sdf] Test WP failed, assume Write Enabled
May 10 16:51:08 jamie-ubuntu kernel: [   64.063834] sd 1:0:0:0: [sdf] Assuming drive cache: write through
May 10 16:51:08 jamie-ubuntu kernel: [   64.064953] sd 1:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
May 10 16:51:08 jamie-ubuntu kernel: [   64.066218] sd 1:0:0:0: [sdf] Test WP failed, assume Write Enabled
May 10 16:51:08 jamie-ubuntu kernel: [   64.066224] sd 1:0:0:0: [sdf] Assuming drive cache: write through
May 10 16:51:08 jamie-ubuntu kernel: [   64.066231]  sdf: unknown partition table
May 10 16:51:08 jamie-ubuntu kernel: [   64.081283] sd 1:0:0:0: [sdf] Attached SCSI disk
May 10 16:51:08 jamie-ubuntu kernel: [   64.133525] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 10 16:51:08 jamie-ubuntu kernel: [   64.133588] sd 0:0:0:1: Attached scsi generic sg1 type 0
May 10 16:51:08 jamie-ubuntu kernel: [   64.133646] sd 0:0:0:2: Attached scsi generic sg2 type 0
May 10 16:51:08 jamie-ubuntu kernel: [   64.133699] sd 0:0:0:3: Attached scsi generic sg3 type 0
May 10 16:51:08 jamie-ubuntu kernel: [   64.133784] sd 0:0:0:4: Attached scsi generic sg4 type 0
May 10 16:51:08 jamie-ubuntu kernel: [   64.133841] sd 1:0:0:0: Attached scsi generic sg5 type 0
May 10 16:51:08 jamie-ubuntu kernel: [   64.362226] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
May 10 16:51:08 jamie-ubuntu kernel: [   64.380595] parport_pc 00:09: reported by Plug and Play ACPI
May 10 16:51:08 jamie-ubuntu kernel: [   64.380699] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
May 10 16:51:08 jamie-ubuntu kernel: [   65.086340] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
May 10 16:51:08 jamie-ubuntu kernel: [   65.087300] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
May 10 16:51:08 jamie-ubuntu kernel: [   69.176131] lp0: using parport0 (interrupt-driven).
May 10 16:51:08 jamie-ubuntu kernel: [   69.225087] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
May 10 16:51:08 jamie-ubuntu kernel: [   69.289758] ndiswrapper: driver net8185 (Realtek,01/29/2007,5.1096.0129.2007) loaded
May 10 16:51:08 jamie-ubuntu kernel: [   69.290676] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 9
May 10 16:51:08 jamie-ubuntu kernel: [   69.290682] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKF] -> GSI 9 (level, low) -> IRQ 9
May 10 16:51:08 jamie-ubuntu kernel: [   69.565937] ndiswrapper: using IRQ 9
May 10 16:51:08 jamie-ubuntu kernel: [   74.505453] wlan0: ethernet device 00:14:d1:3e:dd:b8 using NDIS driver: net8185, version: 0x50448, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
May 10 16:51:08 jamie-ubuntu kernel: [   74.505611] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
May 10 16:51:08 jamie-ubuntu kernel: [   74.508823] usbcore: registered new interface driver ndiswrapper
May 10 16:51:08 jamie-ubuntu kernel: [   74.600842] Adding 1277128k swap on /dev/hdb5.  Priority:-1 extents:1 across:1277128k
May 10 16:51:08 jamie-ubuntu kernel: [   75.193222] EXT3 FS on hdb1, internal journal
May 10 16:51:08 jamie-ubuntu kernel: [   76.710383] ip_tables: (C) 2000-2006 Netfilter Core Team
May 10 16:51:08 jamie-ubuntu kernel: [   77.399534] No dock devices found.
May 10 16:51:08 jamie-ubuntu kernel: [   77.969014] powernow: No powernow capabilities detected
May 10 16:51:08 jamie-ubuntu NetworkManager: <info>  starting... 
May 10 16:51:08 jamie-ubuntu avahi-daemon[5051]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
May 10 16:51:08 jamie-ubuntu avahi-daemon[5051]: Successfully dropped root privileges.
May 10 16:51:08 jamie-ubuntu avahi-daemon[5051]: avahi-daemon 0.6.22 starting up.
May 10 16:51:08 jamie-ubuntu avahi-daemon[5051]: Successfully called chroot().
May 10 16:51:08 jamie-ubuntu avahi-daemon[5051]: Successfully dropped remaining capabilities.
May 10 16:51:09 jamie-ubuntu avahi-daemon[5051]: No service file found in /etc/avahi/services.
May 10 16:51:09 jamie-ubuntu avahi-daemon[5051]: Network interface enumeration completed.
May 10 16:51:09 jamie-ubuntu avahi-daemon[5051]: Registering HINFO record with values 'I686'/'LINUX'.
May 10 16:51:09 jamie-ubuntu avahi-daemon[5051]: Server startup complete. Host name is jamie-ubuntu.local. Local service cookie is 2482164842.
May 10 16:51:09 jamie-ubuntu kernel: [   79.125454] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 10 16:51:09 jamie-ubuntu kernel: [   79.125465] apm: overridden by ACPI.
May 10 16:51:09 jamie-ubuntu kernel: [   79.263763] ppdev: user-space parallel port driver
May 10 16:51:09 jamie-ubuntu kernel: [   79.411679] audit(1210463469.355:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5091 profile="/usr/sbin/cupsd" namespace="default"
May 10 16:51:09 jamie-ubuntu dhcdbd: Started up.
May 10 16:53:32 jamie-ubuntu syslogd 1.5.0#1ubuntu1: restart.
May 10 16:53:32 jamie-ubuntu kernel: Inspecting /boot/System.map-2.6.24-16-generic
May 10 16:53:32 jamie-ubuntu kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
May 10 16:53:32 jamie-ubuntu kernel: Symbols match kernel version 2.6.24.
May 10 16:53:32 jamie-ubuntu kernel: Loaded 32268 symbols from 79 modules.
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] 511MB LOWMEM available.
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 131052) 0 entries of 256 used
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Zone PFN ranges:
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]   DMA             0 ->     4096
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]   Normal       4096 ->   131052
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]   HighMem    131052 ->   131052
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Movable zone start PFN for each node
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]     0:        0 ->   131052
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] On node 0 totalpages: 131052
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]   Normal zone: 991 pages used for memmap
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]   Normal zone: 125965 pages, LIFO batch:31
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] DMI 2.3 present.
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 ASUS  )
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] ACPI: RSDT 1FFEC000, 002C (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] ACPI: FACP 1FFEC080, 0074 (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] ACPI: DSDT 1FFEC100, 291E (r1   ASUS A7A266       1000 MSFT  100000B)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] ACPI: FACS 1FFFF000, 0040
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] ACPI: BOOT 1FFEC040, 0028 (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130029
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Kernel command line: root=UUID=9f65524a-b784-4baa-b7f6-6e62db2cecf1 ro quiet splash
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] mapped APIC to ffffb000 (0140d000)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Initializing CPU#0
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
May 10 16:53:32 jamie-ubuntu kernel: [    0.000000] Detected 1410.254 MHz processor.
May 10 16:53:32 jamie-ubuntu kernel: [   21.613218] Console: colour VGA+ 80x25
May 10 16:53:32 jamie-ubuntu kernel: [   21.613223] console [tty0] enabled
May 10 16:53:32 jamie-ubuntu kernel: [   21.613820] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
May 10 16:53:32 jamie-ubuntu kernel: [   21.614253] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
May 10 16:53:32 jamie-ubuntu kernel: [   21.641040] Memory: 507300k/524208k available (2157k kernel code, 16308k reserved, 998k data, 364k init, 0k highmem)
May 10 16:53:32 jamie-ubuntu kernel: [   21.641053] virtual kernel memory layout:
May 10 16:53:32 jamie-ubuntu kernel: [   21.641055]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May 10 16:53:32 jamie-ubuntu kernel: [   21.641057]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May 10 16:53:32 jamie-ubuntu kernel: [   21.641059]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
May 10 16:53:32 jamie-ubuntu kernel: [   21.641060]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
May 10 16:53:32 jamie-ubuntu kernel: [   21.641062]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
May 10 16:53:32 jamie-ubuntu kernel: [   21.641064]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
May 10 16:53:32 jamie-ubuntu kernel: [   21.641066]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
May 10 16:53:32 jamie-ubuntu kernel: [   21.641071] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May 10 16:53:32 jamie-ubuntu kernel: [   21.641136] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
May 10 16:53:32 jamie-ubuntu kernel: [   21.721164] Calibrating delay using timer specific routine.. 2822.62 BogoMIPS (lpj=5645256)
May 10 16:53:32 jamie-ubuntu kernel: [   21.721209] Security Framework initialized
May 10 16:53:32 jamie-ubuntu kernel: [   21.721220] SELinux:  Disabled at boot.
May 10 16:53:32 jamie-ubuntu kernel: [   21.721251] AppArmor: AppArmor initialized
May 10 16:53:32 jamie-ubuntu kernel: [   21.721258] Failure registering capabilities with primary security module.
May 10 16:53:32 jamie-ubuntu kernel: [   21.721274] Mount-cache hash table entries: 512
May 10 16:53:32 jamie-ubuntu kernel: [   21.721471] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000 00000000
May 10 16:53:32 jamie-ubuntu kernel: [   21.721485] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May 10 16:53:32 jamie-ubuntu kernel: [   21.721489] CPU: L2 Cache: 256K (64 bytes/line)
May 10 16:53:32 jamie-ubuntu kernel: [   21.721494] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000 00000000
May 10 16:53:32 jamie-ubuntu kernel: [   21.721510] Compat vDSO mapped to ffffe000.
May 10 16:53:32 jamie-ubuntu kernel: [   21.721529] Checking 'hlt' instruction... OK.
May 10 16:53:32 jamie-ubuntu kernel: [   21.737224] SMP alternatives: switching to UP code
May 10 16:53:32 jamie-ubuntu kernel: [   21.738824] Freeing SMP alternatives: 11k freed
May 10 16:53:32 jamie-ubuntu kernel: [   21.739034] Early unpacking initramfs... done
May 10 16:53:32 jamie-ubuntu kernel: [   22.247275] ACPI: Core revision 20070126
May 10 16:53:32 jamie-ubuntu kernel: [   22.247421] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 10 16:53:32 jamie-ubuntu kernel: [   22.248535] ACPI: setting ELCR to 0200 (from 0e60)
May 10 16:53:32 jamie-ubuntu kernel: [   22.248872] CPU0: AMD Athlon(TM)Processor stepping 04
May 10 16:53:32 jamie-ubuntu kernel: [   22.248881] SMP motherboard not detected.
May 10 16:53:32 jamie-ubuntu kernel: [   22.248886] Local APIC not detected. Using dummy APIC emulation.
May 10 16:53:32 jamie-ubuntu kernel: [   22.248968] Brought up 1 CPUs
May 10 16:53:32 jamie-ubuntu kernel: [   22.249011] CPU0 attaching sched-domain:
May 10 16:53:32 jamie-ubuntu kernel: [   22.249016]  domain 0: span 01
May 10 16:53:32 jamie-ubuntu kernel: [   22.249018]   groups: 01
May 10 16:53:32 jamie-ubuntu kernel: [   22.249382] net_namespace: 64 bytes
May 10 16:53:32 jamie-ubuntu kernel: [   22.249395] Booting paravirtualized kernel on bare hardware
May 10 16:53:32 jamie-ubuntu kernel: [   22.250137] Time: 16:52:55  Date: 05/10/08
May 10 16:53:32 jamie-ubuntu kernel: [   22.250191] NET: Registered protocol family 16
May 10 16:53:32 jamie-ubuntu kernel: [   22.250531] EISA bus registered
May 10 16:53:32 jamie-ubuntu kernel: [   22.250552] ACPI: bus type pci registered
May 10 16:53:32 jamie-ubuntu kernel: [   22.252267] PCI: PCI BIOS revision 2.10 entry at 0xf1170, last bus=1
May 10 16:53:32 jamie-ubuntu kernel: [   22.252271] PCI: Using configuration type 1
May 10 16:53:32 jamie-ubuntu kernel: [   22.252274] Setting up standard PCI resources
May 10 16:53:32 jamie-ubuntu kernel: [   22.263863] ACPI: EC: Look up EC in DSDT
May 10 16:53:32 jamie-ubuntu kernel: [   22.267232] ACPI: Interpreter enabled
May 10 16:53:32 jamie-ubuntu kernel: [   22.267238] ACPI: (supports S0 S1 S4 S5)
May 10 16:53:32 jamie-ubuntu kernel: [   22.267257] ACPI: Using PIC for interrupt routing
May 10 16:53:32 jamie-ubuntu kernel: [   22.273914] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 10 16:53:32 jamie-ubuntu kernel: [   22.274443] PCI quirk: region e400-e43f claimed by ali7101 ACPI
May 10 16:53:32 jamie-ubuntu kernel: [   22.274449] PCI quirk: region e800-e81f claimed by ali7101 SMB
May 10 16:53:32 jamie-ubuntu kernel: [   22.274590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 10 16:53:33 jamie-ubuntu kernel: [   22.274826] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
May 10 16:53:33 jamie-ubuntu kernel: [   22.276445] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May 10 16:53:33 jamie-ubuntu kernel: [   22.276606] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
May 10 16:53:33 jamie-ubuntu kernel: [   22.276764] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May 10 16:53:33 jamie-ubuntu kernel: [   22.276918] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
May 10 16:53:33 jamie-ubuntu kernel: [   22.277072] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 16:53:33 jamie-ubuntu kernel: [   22.277334] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 16:53:33 jamie-ubuntu kernel: [   22.277425] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May 10 16:53:33 jamie-ubuntu kernel: [   22.277515] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May 10 16:53:33 jamie-ubuntu kernel: [   22.277670] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 16:53:33 jamie-ubuntu kernel: [   22.277982] Linux Plug and Play Support v0.97 (c) Adam Belay
May 10 16:53:33 jamie-ubuntu kernel: [   22.278035] pnp: PnP ACPI init
May 10 16:53:33 jamie-ubuntu kernel: [   22.278048] ACPI: bus type pnp registered
May 10 16:53:33 jamie-ubuntu kernel: [   22.283080] pnp: PnP ACPI: found 14 devices
May 10 16:53:33 jamie-ubuntu kernel: [   22.283084] ACPI: ACPI bus type pnp unregistered
May 10 16:53:33 jamie-ubuntu kernel: [   22.283090] PnPBIOS: Disabled by ACPI PNP
May 10 16:53:33 jamie-ubuntu kernel: [   22.283472] PCI: Using ACPI for IRQ routing
May 10 16:53:33 jamie-ubuntu kernel: [   22.283479] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 10 16:53:33 jamie-ubuntu kernel: [   22.309161] NET: Registered protocol family 8
May 10 16:53:33 jamie-ubuntu kernel: [   22.309165] NET: Registered protocol family 20
May 10 16:53:33 jamie-ubuntu kernel: [   22.309292] AppArmor: AppArmor Filesystem Enabled
May 10 16:53:33 jamie-ubuntu kernel: [   22.313146] Time: tsc clocksource has been installed.
May 10 16:53:33 jamie-ubuntu kernel: [   22.321206] system 00:00: iomem range 0x0-0x9ffff could not be reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.321212] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.321216] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.321220] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.321232] system 00:02: ioport range 0xe400-0xe47f could not be reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.321236] system 00:02: ioport range 0xe800-0xe81f has been reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.321240] system 00:02: ioport range 0x40b-0x40b has been reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.321244] system 00:02: ioport range 0x480-0x48f has been reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.321248] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.321260] system 00:03: iomem range 0xfffe0000-0xffffffff could not be reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.321270] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
May 10 16:53:33 jamie-ubuntu kernel: [   22.351935] PCI: Bridge: 0000:00:01.0
May 10 16:53:33 jamie-ubuntu kernel: [   22.351938]   IO window: disabled.
May 10 16:53:33 jamie-ubuntu kernel: [   22.351946]   MEM window: de000000-dfdfffff
May 10 16:53:33 jamie-ubuntu kernel: [   22.351951]   PREFETCH window: dff00000-efffffff
May 10 16:53:33 jamie-ubuntu kernel: [   22.351966] PCI: Setting latency timer of device 0000:00:01.0 to 64
May 10 16:53:33 jamie-ubuntu kernel: [   22.351985] NET: Registered protocol family 2
May 10 16:53:33 jamie-ubuntu kernel: [   22.389287] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
May 10 16:53:33 jamie-ubuntu kernel: [   22.389643] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
May 10 16:53:33 jamie-ubuntu kernel: [   22.390045] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
May 10 16:53:33 jamie-ubuntu kernel: [   22.390451] TCP: Hash tables configured (established 16384 bind 16384)
May 10 16:53:33 jamie-ubuntu kernel: [   22.390455] TCP reno registered
May 10 16:53:33 jamie-ubuntu kernel: [   22.401392] checking if image is initramfs... it is
May 10 16:53:33 jamie-ubuntu kernel: [   22.853173] Switched to high resolution mode on CPU 0
May 10 16:53:33 jamie-ubuntu kernel: [   23.364911] Freeing initrd memory: 7697k freed
May 10 16:53:33 jamie-ubuntu kernel: [   23.365231] Simple Boot Flag at 0x3a set to 0x1
May 10 16:53:33 jamie-ubuntu kernel: [   23.365982] audit: initializing netlink socket (disabled)
May 10 16:53:33 jamie-ubuntu kernel: [   23.366007] audit(1210438375.728:1): initialized
May 10 16:53:33 jamie-ubuntu kernel: [   23.369110] VFS: Disk quotas dquot_6.5.1
May 10 16:53:33 jamie-ubuntu kernel: [   23.369242] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 10 16:53:33 jamie-ubuntu kernel: [   23.369477] io scheduler noop registered
May 10 16:53:33 jamie-ubuntu kernel: [   23.369481] io scheduler anticipatory registered
May 10 16:53:33 jamie-ubuntu kernel: [   23.369484] io scheduler deadline registered
May 10 16:53:33 jamie-ubuntu kernel: [   23.369499] io scheduler cfq registered (default)
May 10 16:53:33 jamie-ubuntu kernel: [   23.369519] Limiting direct PCI/PCI transfers.
May 10 16:53:33 jamie-ubuntu kernel: [   23.369547] Activating ISA DMA hang workarounds.
May 10 16:53:33 jamie-ubuntu kernel: [   23.369577] Boot video device is 0000:01:00.0
May 10 16:53:33 jamie-ubuntu kernel: [   23.370007] isapnp: Scanning for PnP cards...
May 10 16:53:33 jamie-ubuntu kernel: [   23.724228] isapnp: No Plug & Play device found
May 10 16:53:33 jamie-ubuntu kernel: [   23.770697] Real Time Clock Driver v1.12ac
May 10 16:53:33 jamie-ubuntu kernel: [   23.770849] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 10 16:53:33 jamie-ubuntu kernel: [   23.771077] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 10 16:53:33 jamie-ubuntu kernel: [   23.771321] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 10 16:53:33 jamie-ubuntu kernel: [   23.772263] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 10 16:53:33 jamie-ubuntu kernel: [   23.772876] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 10 16:53:33 jamie-ubuntu kernel: [   23.774162] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 10 16:53:33 jamie-ubuntu kernel: [   23.774285] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 10 16:53:33 jamie-ubuntu kernel: [   23.774452] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May 10 16:53:33 jamie-ubuntu kernel: [   23.777202] serio: i8042 KBD port at 0x60,0x64 irq 1
May 10 16:53:33 jamie-ubuntu kernel: [   23.777210] serio: i8042 AUX port at 0x60,0x64 irq 12
May 10 16:53:33 jamie-ubuntu kernel: [   23.781092] mice: PS/2 mouse device common for all mice
May 10 16:53:33 jamie-ubuntu kernel: [   23.781306] EISA: Probing bus 0 at eisa.0
May 10 16:53:33 jamie-ubuntu kernel: [   23.781365] EISA: Detected 0 cards.
May 10 16:53:33 jamie-ubuntu kernel: [   23.781371] cpuidle: using governor ladder
May 10 16:53:33 jamie-ubuntu kernel: [   23.781373] cpuidle: using governor menu
May 10 16:53:33 jamie-ubuntu kernel: [   23.781608] NET: Registered protocol family 1
May 10 16:53:33 jamie-ubuntu kernel: [   23.781655] Using IPI No-Shortcut mode
May 10 16:53:33 jamie-ubuntu kernel: [   23.781714] registered taskstats version 1
May 10 16:53:33 jamie-ubuntu kernel: [   23.781863]   Magic number: 8:779:893
May 10 16:53:33 jamie-ubuntu kernel: [   23.782013]   hash matches device ptyy3
May 10 16:53:33 jamie-ubuntu kernel: [   23.782133] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 10 16:53:33 jamie-ubuntu kernel: [   23.782136] EDD information not available.
May 10 16:53:33 jamie-ubuntu kernel: [   23.782813] Freeing unused kernel memory: 364k freed
May 10 16:53:33 jamie-ubuntu kernel: [   23.808906] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May 10 16:53:33 jamie-ubuntu kernel: [   25.148274] fuse init (API version 7.9)
May 10 16:53:33 jamie-ubuntu kernel: [   25.181437] ACPI: Invalid PBLK length [5]
May 10 16:53:33 jamie-ubuntu kernel: [   25.595682] usbcore: registered new interface driver usbfs
May 10 16:53:33 jamie-ubuntu kernel: [   25.595725] usbcore: registered new interface driver hub
May 10 16:53:33 jamie-ubuntu kernel: [   25.616554] usbcore: registered new device driver usb
May 10 16:53:33 jamie-ubuntu kernel: [   25.628551] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May 10 16:53:33 jamie-ubuntu kernel: [   25.629150] ACPI: PCI Interrupt Link [LNKI] enabled at IRQ 9
May 10 16:53:33 jamie-ubuntu kernel: [   25.629155] PCI: setting IRQ 9 as level-triggered
May 10 16:53:33 jamie-ubuntu kernel: [   25.629159] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKI] -> GSI 9 (level, low) -> IRQ 9
May 10 16:53:33 jamie-ubuntu kernel: [   25.629182] ohci_hcd 0000:00:02.0: OHCI Host Controller
May 10 16:53:33 jamie-ubuntu kernel: [   25.629598] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
May 10 16:53:33 jamie-ubuntu kernel: [   25.629631] ohci_hcd 0000:00:02.0: irq 9, io mem 0xdd800000
May 10 16:53:33 jamie-ubuntu kernel: [   25.686742] usb usb1: configuration #1 chosen from 1 choice
May 10 16:53:33 jamie-ubuntu kernel: [   25.686792] hub 1-0:1.0: USB hub found
May 10 16:53:33 jamie-ubuntu kernel: [   25.686806] hub 1-0:1.0: 4 ports detected
May 10 16:53:33 jamie-ubuntu kernel: [   25.789186] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
May 10 16:53:33 jamie-ubuntu kernel: [   25.789194] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
May 10 16:53:33 jamie-ubuntu kernel: [   25.789216] ohci_hcd 0000:00:06.0: OHCI Host Controller
May 10 16:53:33 jamie-ubuntu kernel: [   25.789278] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 2
May 10 16:53:33 jamie-ubuntu kernel: [   25.789300] ohci_hcd 0000:00:06.0: irq 9, io mem 0xdc800000
May 10 16:53:33 jamie-ubuntu kernel: [   25.842451] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May 10 16:53:33 jamie-ubuntu kernel: [   25.842463] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May 10 16:53:33 jamie-ubuntu kernel: [   25.846638] usb usb2: configuration #1 chosen from 1 choice
May 10 16:53:33 jamie-ubuntu kernel: [   25.846680] hub 2-0:1.0: USB hub found
May 10 16:53:33 jamie-ubuntu kernel: [   25.846694] hub 2-0:1.0: 2 ports detected
May 10 16:53:33 jamie-ubuntu kernel: [   25.949198] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
May 10 16:53:33 jamie-ubuntu kernel: [   25.949207] PCI: setting IRQ 11 as level-triggered
May 10 16:53:33 jamie-ubuntu kernel: [   25.949212] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
May 10 16:53:33 jamie-ubuntu kernel: [   25.949236] ohci_hcd 0000:00:0c.0: OHCI Host Controller
May 10 16:53:33 jamie-ubuntu kernel: [   25.949279] ohci_hcd 0000:00:0c.0: new USB bus registered, assigned bus number 3
May 10 16:53:33 jamie-ubuntu kernel: [   25.949303] ohci_hcd 0000:00:0c.0: irq 11, io mem 0xda800000
May 10 16:53:33 jamie-ubuntu kernel: [   26.034466] usb usb3: configuration #1 chosen from 1 choice
May 10 16:53:33 jamie-ubuntu kernel: [   26.035496] hub 3-0:1.0: USB hub found
May 10 16:53:33 jamie-ubuntu kernel: [   26.035509] hub 3-0:1.0: 3 ports detected
May 10 16:53:33 jamie-ubuntu kernel: [   26.092403] usb 1-3: new full speed USB device using ohci_hcd and address 2
May 10 16:53:33 jamie-ubuntu kernel: [   26.137081] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
May 10 16:53:33 jamie-ubuntu kernel: [   26.137090] PCI: setting IRQ 10 as level-triggered
May 10 16:53:33 jamie-ubuntu kernel: [   26.137094] ACPI: PCI Interrupt 0000:00:0c.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
May 10 16:53:33 jamie-ubuntu kernel: [   26.137117] ohci_hcd 0000:00:0c.1: OHCI Host Controller
May 10 16:53:33 jamie-ubuntu kernel: [   26.137162] ohci_hcd 0000:00:0c.1: new USB bus registered, assigned bus number 4
May 10 16:53:33 jamie-ubuntu kernel: [   26.137187] ohci_hcd 0000:00:0c.1: irq 10, io mem 0xda000000
May 10 16:53:33 jamie-ubuntu kernel: [   26.223329] usb usb4: configuration #1 chosen from 1 choice
May 10 16:53:33 jamie-ubuntu kernel: [   26.223374] hub 4-0:1.0: USB hub found
May 10 16:53:33 jamie-ubuntu kernel: [   26.223388] hub 4-0:1.0: 2 ports detected
May 10 16:53:33 jamie-ubuntu kernel: [   26.324714] ALI15X3: IDE controller (0x10b9:0x5229 rev 0xc4) at  PCI slot 0000:00:04.0
May 10 16:53:33 jamie-ubuntu kernel: [   26.324755] ACPI: Unable to derive IRQ for device 0000:00:04.0
May 10 16:53:33 jamie-ubuntu kernel: [   26.324769] ALI15X3: not 100% native mode: will probe irqs later
May 10 16:53:33 jamie-ubuntu kernel: [   26.324794]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:DMA
May 10 16:53:33 jamie-ubuntu kernel: [   26.324816]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:DMA
May 10 16:53:33 jamie-ubuntu kernel: [   26.324833] Probing IDE interface ide0...
May 10 16:53:33 jamie-ubuntu kernel: [   26.399537] usb 1-3: configuration #1 chosen from 1 choice
May 10 16:53:33 jamie-ubuntu kernel: [   26.612477] hdb: Maxtor 6E030L0, ATA DISK drive
May 10 16:53:33 jamie-ubuntu kernel: [   26.712361] usb 3-1: new full speed USB device using ohci_hcd and address 2
May 10 16:53:33 jamie-ubuntu kernel: [   26.921477] usb 3-1: configuration #1 chosen from 1 choice
May 10 16:53:33 jamie-ubuntu kernel: [   26.948426] hda: Maxtor 6Y060L0, ATA DISK drive
May 10 16:53:33 jamie-ubuntu kernel: [   26.948452] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 16:53:33 jamie-ubuntu kernel: [   26.948569] hda: UDMA/100 mode selected
May 10 16:53:33 jamie-ubuntu kernel: [   26.948684] hdb: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 16:53:33 jamie-ubuntu kernel: [   26.948789] hdb: UDMA/100 mode selected
May 10 16:53:33 jamie-ubuntu kernel: [   26.948947] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
May 10 16:53:33 jamie-ubuntu kernel: [   26.961437] Probing IDE interface ide1...
May 10 16:53:33 jamie-ubuntu kernel: [   27.228186] usb 4-2: new full speed USB device using ohci_hcd and address 2
May 10 16:53:33 jamie-ubuntu kernel: [   27.447335] usb 4-2: configuration #1 chosen from 1 choice
May 10 16:53:33 jamie-ubuntu kernel: [   27.624150] usbcore: registered new interface driver libusual
May 10 16:53:33 jamie-ubuntu kernel: [   27.641869] SCSI subsystem initialized
May 10 16:53:33 jamie-ubuntu kernel: [   27.651998] Initializing USB Mass Storage driver...
May 10 16:53:33 jamie-ubuntu kernel: [   27.655204] scsi0 : SCSI emulation for USB Mass Storage devices
May 10 16:53:33 jamie-ubuntu kernel: [   27.656960] usb-storage: device found at 2
May 10 16:53:33 jamie-ubuntu kernel: [   27.656968] usb-storage: waiting for device to settle before scanning
May 10 16:53:33 jamie-ubuntu kernel: [   27.664074] scsi1 : SCSI emulation for USB Mass Storage devices
May 10 16:53:33 jamie-ubuntu kernel: [   27.665862] usbcore: registered new interface driver usb-storage
May 10 16:53:33 jamie-ubuntu kernel: [   27.665874] USB Mass Storage support registered.
May 10 16:53:33 jamie-ubuntu kernel: [   27.666051] usb-storage: device found at 2
May 10 16:53:33 jamie-ubuntu kernel: [   27.666054] usb-storage: waiting for device to settle before scanning
May 10 16:53:33 jamie-ubuntu kernel: [   27.752224] hdd: HL-DT-STDVD-ROM GDR8164B, ATAPI CD/DVD-ROM drive
May 10 16:53:33 jamie-ubuntu kernel: [   28.536074] hdc: Hewlett-Packard CD-Writer Plus 8100, ATAPI CD/DVD-ROM drive
May 10 16:53:33 jamie-ubuntu kernel: [   28.536099] hdc: applying conservative PIO "downgrade"
May 10 16:53:33 jamie-ubuntu kernel: [   28.536103] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO2
May 10 16:53:33 jamie-ubuntu kernel: [   28.536647] hdc: MWDMA1 mode selected
May 10 16:53:33 jamie-ubuntu kernel: [   28.537203] hdd: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 16:53:33 jamie-ubuntu kernel: [   28.537633] hdd: UDMA/33 mode selected
May 10 16:53:33 jamie-ubuntu kernel: [   28.538239] ide1 at 0x170-0x177,0x376 on irq 15
May 10 16:53:33 jamie-ubuntu kernel: [   28.559651] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
May 10 16:53:33 jamie-ubuntu kernel: [   28.559660] PCI: setting IRQ 5 as level-triggered
May 10 16:53:33 jamie-ubuntu kernel: [   28.559664] ACPI: PCI Interrupt 0000:00:0c.2[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
May 10 16:53:33 jamie-ubuntu kernel: [   28.559687] ehci_hcd 0000:00:0c.2: EHCI Host Controller
May 10 16:53:33 jamie-ubuntu kernel: [   28.559756] ehci_hcd 0000:00:0c.2: new USB bus registered, assigned bus number 5
May 10 16:53:33 jamie-ubuntu kernel: [   28.559817] ehci_hcd 0000:00:0c.2: irq 5, io mem 0xd9800000
May 10 16:53:33 jamie-ubuntu kernel: [   28.559909] usb 4-2: USB disconnect, address 2
May 10 16:53:33 jamie-ubuntu kernel: [   28.567920] libata version 3.00 loaded.
May 10 16:53:33 jamie-ubuntu kernel: [   28.571920] ehci_hcd 0000:00:0c.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May 10 16:53:33 jamie-ubuntu kernel: [   28.572133] usb usb5: configuration #1 chosen from 1 choice
May 10 16:53:33 jamie-ubuntu kernel: [   28.572174] hub 5-0:1.0: USB hub found
May 10 16:53:33 jamie-ubuntu kernel: [   28.572186] hub 5-0:1.0: 5 ports detected
May 10 16:53:33 jamie-ubuntu kernel: [   28.711581] hda: max request size: 128KiB
May 10 16:53:33 jamie-ubuntu kernel: [   28.713446] hda: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63
May 10 16:53:33 jamie-ubuntu kernel: [   28.713604] hda: cache flushes supported
May 10 16:53:33 jamie-ubuntu kernel: [   28.713664]  hda: hda1
May 10 16:53:33 jamie-ubuntu kernel: [   28.722898] hdb: max request size: 128KiB
May 10 16:53:33 jamie-ubuntu kernel: [   28.723130] hdb: 60058656 sectors (30750 MB) w/2048KiB Cache, CHS=59582/16/63
May 10 16:53:33 jamie-ubuntu kernel: [   28.723373] hdb: cache flushes supported
May 10 16:53:33 jamie-ubuntu kernel: [   28.723426]  hdb: hdb1 hdb2 < hdb5 >
May 10 16:53:33 jamie-ubuntu kernel: [   28.767830] hdc: ATAPI 24X CD-ROM CD-R/RW drive, 1024kB Cache
May 10 16:53:33 jamie-ubuntu kernel: [   28.767847] Uniform CD-ROM driver Revision: 3.20
May 10 16:53:33 jamie-ubuntu kernel: [   28.784214] hdd: ATAPI 52X DVD-ROM drive, 256kB Cache
May 10 16:53:33 jamie-ubuntu kernel: [   28.927821] usb 5-1: new high speed USB device using ehci_hcd and address 2
May 10 16:53:33 jamie-ubuntu kernel: [   29.061535] usb 5-1: configuration #1 chosen from 1 choice
May 10 16:53:33 jamie-ubuntu kernel: [   29.067173] scsi2 : SCSI emulation for USB Mass Storage devices
May 10 16:53:33 jamie-ubuntu kernel: [   29.075048] usb-storage: device found at 2
May 10 16:53:33 jamie-ubuntu kernel: [   29.075055] usb-storage: waiting for device to settle before scanning
May 10 16:53:33 jamie-ubuntu kernel: [   29.127305] Attempting manual resume
May 10 16:53:33 jamie-ubuntu kernel: [   29.127313] swsusp: Resume From Partition 3:69
May 10 16:53:33 jamie-ubuntu kernel: [   29.127316] PM: Checking swsusp image.
May 10 16:53:33 jamie-ubuntu kernel: [   29.127654] PM: Resume from disk failed.
May 10 16:53:33 jamie-ubuntu kernel: [   29.151319] EXT3-fs: INFO: recovery required on readonly filesystem.
May 10 16:53:33 jamie-ubuntu kernel: [   29.151327] EXT3-fs: write access will be enabled during recovery.
May 10 16:53:33 jamie-ubuntu kernel: [   29.206458] kjournald starting.  Commit interval 5 seconds
May 10 16:53:33 jamie-ubuntu kernel: [   29.206487] EXT3-fs: recovery complete.
May 10 16:53:33 jamie-ubuntu kernel: [   29.206944] EXT3-fs: mounted filesystem with ordered data mode.
May 10 16:53:33 jamie-ubuntu kernel: [   29.311720] usb 5-4: new high speed USB device using ehci_hcd and address 3
May 10 16:53:33 jamie-ubuntu kernel: [   29.453111] usb 5-4: configuration #1 chosen from 1 choice
May 10 16:53:33 jamie-ubuntu kernel: [   29.453831] usb 3-1: USB disconnect, address 2
May 10 16:53:33 jamie-ubuntu kernel: [   32.656843] usb-storage: device scan complete
May 10 16:53:33 jamie-ubuntu kernel: [   32.692842] scsi 0:0:0:0: Direct-Access     Generic  2.0 Reader   -CF 1.00 PQ: 0 ANSI: 0 CCS
May 10 16:53:33 jamie-ubuntu kernel: [   34.071908] usb-storage: device scan complete
May 10 16:53:33 jamie-ubuntu kernel: [   34.072656] scsi 2:0:0:0: Direct-Access     ST380021 A                0811 PQ: 0 ANSI: 0
May 10 16:53:33 jamie-ubuntu kernel: [   36.335884] scsi 0:0:0:1: Direct-Access     Generic  2.0 Reader   -SM 1.00 PQ: 0 ANSI: 0 CCS
May 10 16:53:33 jamie-ubuntu kernel: [   36.369793] scsi 0:0:0:2: Direct-Access     Generic  2.0 Reader   -SD 1.00 PQ: 0 ANSI: 0 CCS
May 10 16:53:33 jamie-ubuntu kernel: [   36.403783] scsi 0:0:0:3: Direct-Access     Generic  2.0 Reader   -MS 1.00 PQ: 0 ANSI: 0 CCS
May 10 16:53:33 jamie-ubuntu kernel: [   36.437774] scsi 0:0:0:4: Direct-Access     Generic  2.0 Reader   -xD 1.00 PQ: 0 ANSI: 0 CCS
May 10 16:53:33 jamie-ubuntu kernel: [   38.352036] Linux agpgart interface v0.102
May 10 16:53:33 jamie-ubuntu kernel: [   38.418039] agpgart: Detected ALi M1647 chipset
May 10 16:53:33 jamie-ubuntu kernel: [   38.498492] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 10 16:53:33 jamie-ubuntu kernel: [   38.525781] agpgart: AGP aperture is 128M @ 0xf0000000
May 10 16:53:33 jamie-ubuntu kernel: [   38.552192] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 10 16:53:33 jamie-ubuntu kernel: [   39.432097] input: Power Button (FF) as /devices/virtual/input/input2
May 10 16:53:33 jamie-ubuntu kernel: [   39.441615] ACPI: Power Button (FF) [PWRF]
May 10 16:53:33 jamie-ubuntu kernel: [   39.441803] input: Power Button (CM) as /devices/virtual/input/input3
May 10 16:53:33 jamie-ubuntu kernel: [   39.457588] ACPI: Power Button (CM) [PWRB]
May 10 16:53:33 jamie-ubuntu kernel: [   42.121425] nvidia: module license 'NVIDIA' taints kernel.
May 10 16:53:33 jamie-ubuntu kernel: [   42.782647] input: PC Speaker as /devices/platform/pcspkr/input/input4
May 10 16:53:33 jamie-ubuntu kernel: [   43.253417] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
May 10 16:53:33 jamie-ubuntu kernel: [   43.253426] PCI: setting IRQ 6 as level-triggered
May 10 16:53:33 jamie-ubuntu kernel: [   43.253431] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
May 10 16:53:33 jamie-ubuntu kernel: [   43.253458] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
May 10 16:53:33 jamie-ubuntu kernel: [   43.579120] logips2pp: Detected unknown logitech mouse model 127
May 10 16:53:33 jamie-ubuntu kernel: [   44.051501] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
May 10 16:53:33 jamie-ubuntu kernel: [   44.067338] parport_pc 00:09: reported by Plug and Play ACPI
May 10 16:53:33 jamie-ubuntu kernel: [   44.067445] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
May 10 16:53:33 jamie-ubuntu kernel: [   44.257080] Driver 'sd' needs updating - please use bus_type methods
May 10 16:53:33 jamie-ubuntu kernel: [   44.267921] sd 0:0:0:0: [sda] Attached SCSI removable disk
May 10 16:53:33 jamie-ubuntu kernel: [   44.278917] sd 0:0:0:1: [sdb] Attached SCSI removable disk
May 10 16:53:33 jamie-ubuntu kernel: [   44.289880] sd 0:0:0:2: [sdc] Attached SCSI removable disk
May 10 16:53:33 jamie-ubuntu kernel: [   44.300881] sd 0:0:0:3: [sdd] Attached SCSI removable disk
May 10 16:53:33 jamie-ubuntu kernel: [   44.311882] sd 0:0:0:4: [sde] Attached SCSI removable disk
May 10 16:53:33 jamie-ubuntu kernel: [   44.313513] sd 2:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
May 10 16:53:33 jamie-ubuntu kernel: [   44.314778] sd 2:0:0:0: [sdf] Test WP failed, assume Write Enabled
May 10 16:53:33 jamie-ubuntu kernel: [   44.314788] sd 2:0:0:0: [sdf] Assuming drive cache: write through
May 10 16:53:33 jamie-ubuntu kernel: [   44.315884] sd 2:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
May 10 16:53:33 jamie-ubuntu kernel: [   44.317152] sd 2:0:0:0: [sdf] Test WP failed, assume Write Enabled
May 10 16:53:33 jamie-ubuntu kernel: [   44.317160] sd 2:0:0:0: [sdf] Assuming drive cache: write through
May 10 16:53:33 jamie-ubuntu kernel: [   44.317170]  sdf: unknown partition table
May 10 16:53:33 jamie-ubuntu kernel: [   44.332124] sd 2:0:0:0: [sdf] Attached SCSI disk
May 10 16:53:33 jamie-ubuntu kernel: [   44.436799] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 10 16:53:33 jamie-ubuntu kernel: [   44.437095] sd 0:0:0:1: Attached scsi generic sg1 type 0
May 10 16:53:33 jamie-ubuntu kernel: [   44.437156] sd 0:0:0:2: Attached scsi generic sg2 type 0
May 10 16:53:33 jamie-ubuntu kernel: [   44.437210] sd 0:0:0:3: Attached scsi generic sg3 type 0
May 10 16:53:33 jamie-ubuntu kernel: [   44.437264] sd 0:0:0:4: Attached scsi generic sg4 type 0
May 10 16:53:33 jamie-ubuntu kernel: [   44.437336] sd 2:0:0:0: Attached scsi generic sg5 type 0
May 10 16:53:33 jamie-ubuntu kernel: [   44.630873] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
May 10 16:53:33 jamie-ubuntu kernel: [   44.631826] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
May 10 16:53:33 jamie-ubuntu kernel: [   49.017138] lp0: using parport0 (interrupt-driven).
May 10 16:53:33 jamie-ubuntu kernel: [   49.057708] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
May 10 16:53:33 jamie-ubuntu kernel: [   49.139153] ndiswrapper: driver net8185 (Realtek,01/29/2007,5.1096.0129.2007) loaded
May 10 16:53:33 jamie-ubuntu kernel: [   49.140129] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 9
May 10 16:53:33 jamie-ubuntu kernel: [   49.140135] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKF] -> GSI 9 (level, low) -> IRQ 9
May 10 16:53:33 jamie-ubuntu kernel: [   49.412586] ndiswrapper: using IRQ 9
May 10 16:53:33 jamie-ubuntu kernel: [   55.751844] wlan0: ethernet device 00:14:d1:3e:dd:b8 using NDIS driver: net8185, version: 0x50448, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
May 10 16:53:33 jamie-ubuntu kernel: [   55.752004] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
May 10 16:53:33 jamie-ubuntu kernel: [   55.755724] usbcore: registered new interface driver ndiswrapper
May 10 16:53:33 jamie-ubuntu kernel: [   55.851117] Adding 1277128k swap on /dev/hdb5.  Priority:-1 extents:1 across:1277128k
May 10 16:53:33 jamie-ubuntu kernel: [   56.443689] EXT3 FS on hdb1, internal journal
May 10 16:53:33 jamie-ubuntu kernel: [   57.860402] ip_tables: (C) 2000-2006 Netfilter Core Team
May 10 16:53:33 jamie-ubuntu kernel: [   58.520754] No dock devices found.
May 10 16:53:33 jamie-ubuntu kernel: [   59.085897] powernow: No powernow capabilities detected
May 10 16:53:33 jamie-ubuntu NetworkManager: <info>  starting... 
May 10 16:53:33 jamie-ubuntu avahi-daemon[5015]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
May 10 16:53:33 jamie-ubuntu avahi-daemon[5015]: Successfully dropped root privileges.
May 10 16:53:33 jamie-ubuntu avahi-daemon[5015]: avahi-daemon 0.6.22 starting up.
May 10 16:53:33 jamie-ubuntu avahi-daemon[5015]: Successfully called chroot().
May 10 16:53:33 jamie-ubuntu avahi-daemon[5015]: Successfully dropped remaining capabilities.
May 10 16:53:33 jamie-ubuntu avahi-daemon[5015]: No service file found in /etc/avahi/services.
May 10 16:53:33 jamie-ubuntu avahi-daemon[5015]: Network interface enumeration completed.
May 10 16:53:33 jamie-ubuntu avahi-daemon[5015]: Registering HINFO record with values 'I686'/'LINUX'.
May 10 16:53:33 jamie-ubuntu avahi-daemon[5015]: Server startup complete. Host name is jamie-ubuntu.local. Local service cookie is 4088072292.
May 10 16:53:33 jamie-ubuntu kernel: [   60.250693] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 10 16:53:33 jamie-ubuntu kernel: [   60.250704] apm: overridden by ACPI.
May 10 16:53:33 jamie-ubuntu kernel: [   60.397273] ppdev: user-space parallel port driver
May 10 16:53:33 jamie-ubuntu kernel: [   60.570259] audit(1210463613.673:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5055 profile="/usr/sbin/cupsd" namespace="default"
May 10 16:53:33 jamie-ubuntu dhcdbd: Started up.
May 10 16:53:35 jamie-ubuntu NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
May 10 16:53:35 jamie-ubuntu NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
May 10 16:53:35 jamie-ubuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 10 16:53:35 jamie-ubuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 10 16:53:35 jamie-ubuntu NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
May 10 16:53:35 jamie-ubuntu NetworkManager: <info>  Deactivating device wlan0. 
May 10 16:53:35 jamie-ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
May 10 16:53:35 jamie-ubuntu hcid[5300]: Bluetooth HCI daemon
May 10 16:53:35 jamie-ubuntu kernel: [   62.473910] Bluetooth: Core ver 2.11
May 10 16:53:35 jamie-ubuntu kernel: [   62.475449] NET: Registered protocol family 31
May 10 16:53:35 jamie-ubuntu kernel: [   62.475457] Bluetooth: HCI device and connection manager initialized
May 10 16:53:35 jamie-ubuntu kernel: [   62.475464] Bluetooth: HCI socket layer initialized
May 10 16:53:35 jamie-ubuntu hcid[5300]: Starting SDP server
May 10 16:53:35 jamie-ubuntu kernel: [   62.537178] Bluetooth: L2CAP ver 2.9
May 10 16:53:35 jamie-ubuntu kernel: [   62.537187] Bluetooth: L2CAP socket layer initialized
May 10 16:53:35 jamie-ubuntu hcid[5300]: Created local server at unix:abstract=/var/run/dbus-OkirC2afjV,guid=90a17dd0397b9f2987227f604826357f
May 10 16:53:35 jamie-ubuntu input[5331]: Bluetooth Input daemon
May 10 16:53:35 jamie-ubuntu input[5331]: Registered input manager path:/org/bluez/input
May 10 16:53:35 jamie-ubuntu audio[5333]: Bluetooth Audio daemon
May 10 16:53:35 jamie-ubuntu audio[5333]: Unix socket created: 5
May 10 16:53:35 jamie-ubuntu audio[5333]: audio.conf: Key file does not have key 'Enable'
May 10 16:53:35 jamie-ubuntu audio[5333]: audio.conf: Key file does not have key 'Disable'
May 10 16:53:35 jamie-ubuntu NetworkManager: <debug> [1210463615.739368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 10 16:53:35 jamie-ubuntu kernel: [   62.650259] Bluetooth: RFCOMM socket layer initialized
May 10 16:53:35 jamie-ubuntu kernel: [   62.651187] Bluetooth: RFCOMM TTY layer initialized
May 10 16:53:35 jamie-ubuntu kernel: [   62.651192] Bluetooth: RFCOMM ver 1.8
May 10 16:53:35 jamie-ubuntu audio[5333]: add_service_record: got record id 0x10000
May 10 16:53:35 jamie-ubuntu audio[5333]: audio.conf: Key file does not have key 'Disable'
May 10 16:53:35 jamie-ubuntu audio[5333]: audio.conf: Key file does not have group 'A2DP'
May 10 16:53:35 jamie-ubuntu last message repeated 3 times
May 10 16:53:35 jamie-ubuntu audio[5333]: SEP 0x806d658 registered: type:0 codec:0 seid:1
May 10 16:53:35 jamie-ubuntu audio[5333]: add_service_record: got record id 0x10001
May 10 16:53:35 jamie-ubuntu audio[5333]: add_service_record: got record id 0x10002
May 10 16:53:35 jamie-ubuntu audio[5333]: add_service_record: got record id 0x10003
May 10 16:53:35 jamie-ubuntu audio[5333]: Registered manager path:/org/bluez/audio
May 10 16:53:38 jamie-ubuntu anacron[5407]: Anacron 2.3 started on 2008-05-10
May 10 16:53:38 jamie-ubuntu kernel: [   65.103004] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
May 10 16:53:38 jamie-ubuntu kernel: [   65.103025] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
May 10 16:53:38 jamie-ubuntu kernel: [   65.103062] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
May 10 16:53:38 jamie-ubuntu anacron[5407]: Normal exit (0 jobs run)
May 10 16:53:38 jamie-ubuntu /usr/sbin/cron[5439]: (CRON) INFO (pidfile fd = 3)
May 10 16:53:38 jamie-ubuntu /usr/sbin/cron[5440]: (CRON) STARTUP (fork ok)
May 10 16:53:38 jamie-ubuntu /usr/sbin/cron[5440]: (CRON) INFO (Running @reboot jobs)
May 10 16:54:00 jamie-ubuntu kernel: [   87.537502] NET: Registered protocol family 10
May 10 16:54:00 jamie-ubuntu kernel: [   87.538846] lo: Disabled Privacy Extensions
May 10 16:54:00 jamie-ubuntu pulseaudio[5628]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
May 10 16:54:00 jamie-ubuntu pulseaudio[5628]: alsa-util.c: Cannot find fallback mixer control "PCM".
May 10 16:54:02 jamie-ubuntu avahi-daemon[5015]: Registering new address record for fe80::214:d1ff:fe3e:ddb8 on wlan0.*.
May 10 16:54:05 jamie-ubuntu hcid[5300]: Default passkey agent (:1.25, /org/bluez/passkey) registered
May 10 16:54:05 jamie-ubuntu hcid[5300]: Default authorization agent (:1.25, /org/bluez/auth) registered
May 10 16:54:11 jamie-ubuntu kernel: [   98.453280] wlan0: no IPv6 routers present
May 10 16:54:12 jamie-ubuntu ntfs-3g[5773]: Version 1.2216 external FUSE 27 
May 10 16:54:12 jamie-ubuntu ntfs-3g[5773]: Mounted /dev/sdf (Read-Write, label "External Storage", NTFS 3.1) 
May 10 16:54:12 jamie-ubuntu ntfs-3g[5773]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_CA.UTF-8 
May 10 16:54:12 jamie-ubuntu ntfs-3g[5773]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,noatime,fsname=/dev/sdf,blkdev,blksize=4096 
May 10 16:54:12 jamie-ubuntu hald: mounted /dev/sdf on behalf of uid 1000
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
May 10 16:54:12 jamie-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Will activate connection 'wlan0/hamiltons'. 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Device wlan0 activation scheduled... 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) started... 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'hamiltons' is encrypted, but NO valid key exists.  New key needed. 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'hamiltons'. 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'hamiltons' received. 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 10 16:54:12 jamie-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'hamiltons' is encrypted, and a key exists.  No new key needed. 
May 10 16:54:13 jamie-ubuntu NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May 10 16:54:13 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May 10 16:54:14 jamie-ubuntu kernel: [  101.044432] NET: Registered protocol family 17
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: response was '0' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 68616d696c746f6e73' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 16:54:14 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 10 16:54:17 jamie-ubuntu NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May 10 16:54:17 jamie-ubuntu NetworkManager: <info>  Supplicant state changed: 1 
May 10 16:54:17 jamie-ubuntu NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'hamiltons'. 
May 10 16:54:17 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 10 16:54:17 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
May 10 16:54:18 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
May 10 16:54:18 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
May 10 16:54:18 jamie-ubuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
May 10 16:54:19 jamie-ubuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
May 10 16:54:19 jamie-ubuntu dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
May 10 16:54:19 jamie-ubuntu dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May 10 16:54:19 jamie-ubuntu avahi-daemon[5015]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
May 10 16:54:19 jamie-ubuntu avahi-daemon[5015]: New relevant interface wlan0.IPv4 for mDNS.
May 10 16:54:19 jamie-ubuntu avahi-daemon[5015]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
May 10 16:54:19 jamie-ubuntu NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface wlan0 
May 10 16:54:19 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
May 10 16:54:19 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
May 10 16:54:19 jamie-ubuntu dhclient: bound to 192.168.1.101 -- renewal in 41523 seconds.
May 10 16:54:20 jamie-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
May 10 16:54:20 jamie-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>    address 192.168.1.101 
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>    netmask 255.255.255.0 
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>    broadcast 192.168.1.255 
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>    gateway 192.168.1.1 
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>    nameserver 75.154.133.68 
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>    nameserver 75.154.133.100 
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>    hostname 'jamie-ubuntu' 
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>    domain name 'bc.hsia.telus.net' 
May 10 16:54:20 jamie-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
May 10 16:54:20 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
May 10 16:54:20 jamie-ubuntu avahi-daemon[5015]: Withdrawing address record for 192.168.1.101 on wlan0.
May 10 16:54:20 jamie-ubuntu avahi-daemon[5015]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
May 10 16:54:20 jamie-ubuntu avahi-daemon[5015]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 10 16:54:20 jamie-ubuntu avahi-daemon[5015]: Withdrawing address record for fe80::214:d1ff:fe3e:ddb8 on wlan0.
May 10 16:54:20 jamie-ubuntu avahi-daemon[5015]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
May 10 16:54:20 jamie-ubuntu avahi-daemon[5015]: New relevant interface wlan0.IPv4 for mDNS.
May 10 16:54:20 jamie-ubuntu avahi-daemon[5015]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
May 10 16:54:21 jamie-ubuntu NetworkManager: <info>  Clearing nscd hosts cache. 
May 10 16:54:21 jamie-ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May 10 16:54:21 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) successful, device activated. 
May 10 16:54:21 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
May 10 16:54:21 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
May 10 16:54:22 jamie-ubuntu ntpdate[5875]: step time server 91.189.94.4 offset 2.098657 sec
May 10 16:54:25 jamie-ubuntu avahi-daemon[5015]: Registering new address record for fe80::214:d1ff:fe3e:ddb8 on wlan0.*.
May 10 16:54:34 jamie-ubuntu kernel: [  119.552864] wlan0: no IPv6 routers present
May 10 17:04:28 jamie-ubuntu kernel: [  713.638919] totem[6351]: segfault at 990df810 eip b703bf98 esp b07e5ee8 error 6
May 10 19:56:38 jamie-ubuntu syslogd 1.5.0#1ubuntu1: restart.
May 10 19:56:38 jamie-ubuntu kernel: Inspecting /boot/System.map-2.6.24-16-generic
May 10 19:56:38 jamie-ubuntu kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
May 10 19:56:38 jamie-ubuntu kernel: Symbols match kernel version 2.6.24.
May 10 19:56:38 jamie-ubuntu kernel: Loaded 32476 symbols from 81 modules.
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] 511MB LOWMEM available.
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 131052) 0 entries of 256 used
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Zone PFN ranges:
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]   DMA             0 ->     4096
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]   Normal       4096 ->   131052
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]   HighMem    131052 ->   131052
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Movable zone start PFN for each node
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]     0:        0 ->   131052
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] On node 0 totalpages: 131052
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]   Normal zone: 991 pages used for memmap
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]   Normal zone: 125965 pages, LIFO batch:31
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] DMI 2.3 present.
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 ASUS  )
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] ACPI: RSDT 1FFEC000, 002C (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] ACPI: FACP 1FFEC080, 0074 (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] ACPI: DSDT 1FFEC100, 291E (r1   ASUS A7A266       1000 MSFT  100000B)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] ACPI: FACS 1FFFF000, 0040
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] ACPI: BOOT 1FFEC040, 0028 (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130029
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Kernel command line: root=UUID=9f65524a-b784-4baa-b7f6-6e62db2cecf1 ro quiet splash
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] mapped APIC to ffffb000 (0140d000)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Initializing CPU#0
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
May 10 19:56:38 jamie-ubuntu kernel: [    0.000000] Detected 1410.282 MHz processor.
May 10 19:56:38 jamie-ubuntu kernel: [   12.994336] Console: colour VGA+ 80x25
May 10 19:56:38 jamie-ubuntu kernel: [   12.994341] console [tty0] enabled
May 10 19:56:38 jamie-ubuntu kernel: [   12.994936] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
May 10 19:56:38 jamie-ubuntu kernel: [   12.995366] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
May 10 19:56:38 jamie-ubuntu kernel: [   13.022153] Memory: 507300k/524208k available (2157k kernel code, 16308k reserved, 998k data, 364k init, 0k highmem)
May 10 19:56:38 jamie-ubuntu kernel: [   13.022167] virtual kernel memory layout:
May 10 19:56:38 jamie-ubuntu kernel: [   13.022168]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May 10 19:56:38 jamie-ubuntu kernel: [   13.022170]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May 10 19:56:38 jamie-ubuntu kernel: [   13.022172]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
May 10 19:56:38 jamie-ubuntu kernel: [   13.022174]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
May 10 19:56:38 jamie-ubuntu kernel: [   13.022176]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
May 10 19:56:38 jamie-ubuntu kernel: [   13.022178]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
May 10 19:56:38 jamie-ubuntu kernel: [   13.022180]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
May 10 19:56:38 jamie-ubuntu kernel: [   13.022185] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May 10 19:56:38 jamie-ubuntu kernel: [   13.022250] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
May 10 19:56:38 jamie-ubuntu kernel: [   13.102277] Calibrating delay using timer specific routine.. 2822.62 BogoMIPS (lpj=5645257)
May 10 19:56:38 jamie-ubuntu kernel: [   13.102323] Security Framework initialized
May 10 19:56:38 jamie-ubuntu kernel: [   13.102334] SELinux:  Disabled at boot.
May 10 19:56:38 jamie-ubuntu kernel: [   13.102365] AppArmor: AppArmor initialized
May 10 19:56:38 jamie-ubuntu kernel: [   13.102372] Failure registering capabilities with primary security module.
May 10 19:56:38 jamie-ubuntu kernel: [   13.102387] Mount-cache hash table entries: 512
May 10 19:56:38 jamie-ubuntu kernel: [   13.102585] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000 00000000
May 10 19:56:38 jamie-ubuntu kernel: [   13.102599] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May 10 19:56:38 jamie-ubuntu kernel: [   13.102604] CPU: L2 Cache: 256K (64 bytes/line)
May 10 19:56:38 jamie-ubuntu kernel: [   13.102608] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000 00000000
May 10 19:56:38 jamie-ubuntu kernel: [   13.102624] Compat vDSO mapped to ffffe000.
May 10 19:56:38 jamie-ubuntu kernel: [   13.102643] Checking 'hlt' instruction... OK.
May 10 19:56:38 jamie-ubuntu kernel: [   13.118338] SMP alternatives: switching to UP code
May 10 19:56:38 jamie-ubuntu kernel: [   13.119935] Freeing SMP alternatives: 11k freed
May 10 19:56:38 jamie-ubuntu kernel: [   13.120145] Early unpacking initramfs... done
May 10 19:56:38 jamie-ubuntu kernel: [   13.628302] ACPI: Core revision 20070126
May 10 19:56:38 jamie-ubuntu kernel: [   13.628449] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 10 19:56:38 jamie-ubuntu kernel: [   13.629564] ACPI: setting ELCR to 0200 (from 0e60)
May 10 19:56:38 jamie-ubuntu kernel: [   13.629899] CPU0: AMD Athlon(TM)Processor stepping 04
May 10 19:56:38 jamie-ubuntu kernel: [   13.629908] SMP motherboard not detected.
May 10 19:56:38 jamie-ubuntu kernel: [   13.629912] Local APIC not detected. Using dummy APIC emulation.
May 10 19:56:38 jamie-ubuntu kernel: [   13.629994] Brought up 1 CPUs
May 10 19:56:38 jamie-ubuntu kernel: [   13.630038] CPU0 attaching sched-domain:
May 10 19:56:38 jamie-ubuntu kernel: [   13.630042]  domain 0: span 01
May 10 19:56:38 jamie-ubuntu kernel: [   13.630045]   groups: 01
May 10 19:56:38 jamie-ubuntu kernel: [   13.630409] net_namespace: 64 bytes
May 10 19:56:38 jamie-ubuntu kernel: [   13.630422] Booting paravirtualized kernel on bare hardware
May 10 19:56:38 jamie-ubuntu kernel: [   13.631164] Time: 19:55:57  Date: 05/10/08
May 10 19:56:38 jamie-ubuntu kernel: [   13.631218] NET: Registered protocol family 16
May 10 19:56:38 jamie-ubuntu kernel: [   13.631559] EISA bus registered
May 10 19:56:38 jamie-ubuntu kernel: [   13.631580] ACPI: bus type pci registered
May 10 19:56:38 jamie-ubuntu kernel: [   13.633297] PCI: PCI BIOS revision 2.10 entry at 0xf1170, last bus=1
May 10 19:56:38 jamie-ubuntu kernel: [   13.633301] PCI: Using configuration type 1
May 10 19:56:38 jamie-ubuntu kernel: [   13.633303] Setting up standard PCI resources
May 10 19:56:38 jamie-ubuntu kernel: [   13.644903] ACPI: EC: Look up EC in DSDT
May 10 19:56:38 jamie-ubuntu kernel: [   13.648265] ACPI: Interpreter enabled
May 10 19:56:38 jamie-ubuntu kernel: [   13.648271] ACPI: (supports S0 S1 S4 S5)
May 10 19:56:38 jamie-ubuntu kernel: [   13.648290] ACPI: Using PIC for interrupt routing
May 10 19:56:38 jamie-ubuntu kernel: [   13.654957] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 10 19:56:38 jamie-ubuntu kernel: [   13.655516] PCI quirk: region e400-e43f claimed by ali7101 ACPI
May 10 19:56:38 jamie-ubuntu kernel: [   13.655521] PCI quirk: region e800-e81f claimed by ali7101 SMB
May 10 19:56:38 jamie-ubuntu kernel: [   13.655664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 10 19:56:38 jamie-ubuntu kernel: [   13.655900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
May 10 19:56:38 jamie-ubuntu kernel: [   13.657608] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May 10 19:56:38 jamie-ubuntu kernel: [   13.657770] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
May 10 19:56:38 jamie-ubuntu kernel: [   13.657925] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May 10 19:56:38 jamie-ubuntu kernel: [   13.658078] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
May 10 19:56:38 jamie-ubuntu kernel: [   13.658240] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 19:56:38 jamie-ubuntu kernel: [   13.658499] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 19:56:38 jamie-ubuntu kernel: [   13.658588] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May 10 19:56:38 jamie-ubuntu kernel: [   13.658678] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May 10 19:56:38 jamie-ubuntu kernel: [   13.658833] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 19:56:38 jamie-ubuntu kernel: [   13.659148] Linux Plug and Play Support v0.97 (c) Adam Belay
May 10 19:56:38 jamie-ubuntu kernel: [   13.659200] pnp: PnP ACPI init
May 10 19:56:38 jamie-ubuntu kernel: [   13.659217] ACPI: bus type pnp registered
May 10 19:56:38 jamie-ubuntu kernel: [   13.664239] pnp: PnP ACPI: found 14 devices
May 10 19:56:38 jamie-ubuntu kernel: [   13.664243] ACPI: ACPI bus type pnp unregistered
May 10 19:56:38 jamie-ubuntu kernel: [   13.664250] PnPBIOS: Disabled by ACPI PNP
May 10 19:56:38 jamie-ubuntu kernel: [   13.664640] PCI: Using ACPI for IRQ routing
May 10 19:56:38 jamie-ubuntu kernel: [   13.664647] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 10 19:56:38 jamie-ubuntu kernel: [   13.664683] PCI: Cannot allocate resource region 0 of device 0000:00:0c.2
May 10 19:56:38 jamie-ubuntu kernel: [   13.690275] NET: Registered protocol family 8
May 10 19:56:38 jamie-ubuntu kernel: [   13.690279] NET: Registered protocol family 20
May 10 19:56:38 jamie-ubuntu kernel: [   13.690405] AppArmor: AppArmor Filesystem Enabled
May 10 19:56:38 jamie-ubuntu kernel: [   13.694259] Time: tsc clocksource has been installed.
May 10 19:56:38 jamie-ubuntu kernel: [   13.702319] system 00:00: iomem range 0x0-0x9ffff could not be reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.702325] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.702329] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.702333] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.702345] system 00:02: ioport range 0xe400-0xe47f could not be reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.702349] system 00:02: ioport range 0xe800-0xe81f has been reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.702354] system 00:02: ioport range 0x40b-0x40b has been reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.702358] system 00:02: ioport range 0x480-0x48f has been reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.702362] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.702374] system 00:03: iomem range 0xfffe0000-0xffffffff could not be reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.702384] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
May 10 19:56:38 jamie-ubuntu kernel: [   13.733066] PCI: Bridge: 0000:00:01.0
May 10 19:56:38 jamie-ubuntu kernel: [   13.733069]   IO window: disabled.
May 10 19:56:38 jamie-ubuntu kernel: [   13.733075]   MEM window: de000000-dfdfffff
May 10 19:56:38 jamie-ubuntu kernel: [   13.733080]   PREFETCH window: dff00000-efffffff
May 10 19:56:38 jamie-ubuntu kernel: [   13.733095] PCI: Setting latency timer of device 0000:00:01.0 to 64
May 10 19:56:38 jamie-ubuntu kernel: [   13.733114] NET: Registered protocol family 2
May 10 19:56:38 jamie-ubuntu kernel: [   13.770402] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
May 10 19:56:38 jamie-ubuntu kernel: [   13.770761] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
May 10 19:56:38 jamie-ubuntu kernel: [   13.771163] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
May 10 19:56:38 jamie-ubuntu kernel: [   13.771570] TCP: Hash tables configured (established 16384 bind 16384)
May 10 19:56:38 jamie-ubuntu kernel: [   13.771575] TCP reno registered
May 10 19:56:38 jamie-ubuntu kernel: [   13.782504] checking if image is initramfs... it is
May 10 19:56:38 jamie-ubuntu kernel: [   14.234288] Switched to high resolution mode on CPU 0
May 10 19:56:38 jamie-ubuntu kernel: [   14.743918] Freeing initrd memory: 7697k freed
May 10 19:56:38 jamie-ubuntu kernel: [   14.744217] Simple Boot Flag at 0x3a set to 0x1
May 10 19:56:38 jamie-ubuntu kernel: [   14.744963] audit: initializing netlink socket (disabled)
May 10 19:56:38 jamie-ubuntu kernel: [   14.744988] audit(1210449357.724:1): initialized
May 10 19:56:38 jamie-ubuntu kernel: [   14.748096] VFS: Disk quotas dquot_6.5.1
May 10 19:56:38 jamie-ubuntu kernel: [   14.748227] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 10 19:56:38 jamie-ubuntu kernel: [   14.748462] io scheduler noop registered
May 10 19:56:38 jamie-ubuntu kernel: [   14.748466] io scheduler anticipatory registered
May 10 19:56:38 jamie-ubuntu kernel: [   14.748469] io scheduler deadline registered
May 10 19:56:38 jamie-ubuntu kernel: [   14.748484] io scheduler cfq registered (default)
May 10 19:56:38 jamie-ubuntu kernel: [   14.748503] Limiting direct PCI/PCI transfers.
May 10 19:56:38 jamie-ubuntu kernel: [   14.748531] Activating ISA DMA hang workarounds.
May 10 19:56:38 jamie-ubuntu kernel: [   14.748563] Boot video device is 0000:01:00.0
May 10 19:56:38 jamie-ubuntu kernel: [   14.748998] isapnp: Scanning for PnP cards...
May 10 19:56:38 jamie-ubuntu kernel: [   15.103229] isapnp: No Plug & Play device found
May 10 19:56:38 jamie-ubuntu kernel: [   15.149949] Real Time Clock Driver v1.12ac
May 10 19:56:38 jamie-ubuntu kernel: [   15.150160] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 10 19:56:38 jamie-ubuntu kernel: [   15.150392] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 10 19:56:38 jamie-ubuntu kernel: [   15.150635] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 10 19:56:38 jamie-ubuntu kernel: [   15.151617] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 10 19:56:38 jamie-ubuntu kernel: [   15.152200] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 10 19:56:38 jamie-ubuntu kernel: [   15.153486] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 10 19:56:38 jamie-ubuntu kernel: [   15.153595] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 10 19:56:38 jamie-ubuntu kernel: [   15.153752] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May 10 19:56:38 jamie-ubuntu kernel: [   15.156560] serio: i8042 KBD port at 0x60,0x64 irq 1
May 10 19:56:38 jamie-ubuntu kernel: [   15.156568] serio: i8042 AUX port at 0x60,0x64 irq 12
May 10 19:56:38 jamie-ubuntu kernel: [   15.158293] mice: PS/2 mouse device common for all mice
May 10 19:56:38 jamie-ubuntu kernel: [   15.158503] EISA: Probing bus 0 at eisa.0
May 10 19:56:38 jamie-ubuntu kernel: [   15.158562] EISA: Detected 0 cards.
May 10 19:56:38 jamie-ubuntu kernel: [   15.158567] cpuidle: using governor ladder
May 10 19:56:38 jamie-ubuntu kernel: [   15.158570] cpuidle: using governor menu
May 10 19:56:38 jamie-ubuntu kernel: [   15.158796] NET: Registered protocol family 1
May 10 19:56:38 jamie-ubuntu kernel: [   15.158844] Using IPI No-Shortcut mode
May 10 19:56:38 jamie-ubuntu kernel: [   15.158900] registered taskstats version 1
May 10 19:56:38 jamie-ubuntu kernel: [   15.159057]   Magic number: 8:650:950
May 10 19:56:38 jamie-ubuntu kernel: [   15.159095]   hash matches device ttya5
May 10 19:56:38 jamie-ubuntu kernel: [   15.159287]   hash matches device tty7
May 10 19:56:38 jamie-ubuntu kernel: [   15.159330] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 10 19:56:38 jamie-ubuntu kernel: [   15.159333] EDD information not available.
May 10 19:56:38 jamie-ubuntu kernel: [   15.160006] Freeing unused kernel memory: 364k freed
May 10 19:56:38 jamie-ubuntu kernel: [   15.186050] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May 10 19:56:38 jamie-ubuntu kernel: [   16.525989] fuse init (API version 7.9)
May 10 19:56:38 jamie-ubuntu kernel: [   16.558192] ACPI: Invalid PBLK length [5]
May 10 19:56:38 jamie-ubuntu kernel: [   17.463623] usbcore: registered new interface driver usbfs
May 10 19:56:38 jamie-ubuntu kernel: [   17.463664] usbcore: registered new interface driver hub
May 10 19:56:38 jamie-ubuntu kernel: [   17.478182] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May 10 19:56:38 jamie-ubuntu kernel: [   17.478194] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May 10 19:56:38 jamie-ubuntu kernel: [   17.497638] usbcore: registered new device driver usb
May 10 19:56:38 jamie-ubuntu kernel: [   17.510214] ALI15X3: IDE controller (0x10b9:0x5229 rev 0xc4) at  PCI slot 0000:00:04.0
May 10 19:56:38 jamie-ubuntu kernel: [   17.510252] ACPI: Unable to derive IRQ for device 0000:00:04.0
May 10 19:56:38 jamie-ubuntu kernel: [   17.510265] ALI15X3: not 100% native mode: will probe irqs later
May 10 19:56:38 jamie-ubuntu kernel: [   17.510290]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:DMA
May 10 19:56:38 jamie-ubuntu kernel: [   17.510309]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:DMA
May 10 19:56:38 jamie-ubuntu kernel: [   17.510322] Probing IDE interface ide0...
May 10 19:56:38 jamie-ubuntu kernel: [   17.545621] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May 10 19:56:38 jamie-ubuntu kernel: [   17.577004] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
May 10 19:56:38 jamie-ubuntu kernel: [   17.797703] hdb: Maxtor 6E030L0, ATA DISK drive
May 10 19:56:38 jamie-ubuntu kernel: [   18.133668] hda: Maxtor 6Y060L0, ATA DISK drive
May 10 19:56:38 jamie-ubuntu kernel: [   18.133695] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 19:56:38 jamie-ubuntu kernel: [   18.133801] hda: UDMA/100 mode selected
May 10 19:56:38 jamie-ubuntu kernel: [   18.133917] hdb: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 19:56:38 jamie-ubuntu kernel: [   18.134022] hdb: UDMA/100 mode selected
May 10 19:56:38 jamie-ubuntu kernel: [   18.134180] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
May 10 19:56:38 jamie-ubuntu kernel: [   18.147286] Probing IDE interface ide1...
May 10 19:56:38 jamie-ubuntu kernel: [   18.937488] hdd: HL-DT-STDVD-ROM GDR8164B, ATAPI CD/DVD-ROM drive
May 10 19:56:38 jamie-ubuntu kernel: [   19.721341] hdc: Hewlett-Packard CD-Writer Plus 8100, ATAPI CD/DVD-ROM drive
May 10 19:56:38 jamie-ubuntu kernel: [   19.721365] hdc: applying conservative PIO "downgrade"
May 10 19:56:38 jamie-ubuntu kernel: [   19.721369] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO2
May 10 19:56:38 jamie-ubuntu kernel: [   19.721914] hdc: MWDMA1 mode selected
May 10 19:56:38 jamie-ubuntu kernel: [   19.722470] hdd: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 19:56:38 jamie-ubuntu kernel: [   19.722899] hdd: UDMA/33 mode selected
May 10 19:56:38 jamie-ubuntu kernel: [   19.723507] ide1 at 0x170-0x177,0x376 on irq 15
May 10 19:56:38 jamie-ubuntu kernel: [   19.744443] ACPI: PCI Interrupt Link [LNKI] enabled at IRQ 9
May 10 19:56:38 jamie-ubuntu kernel: [   19.744452] PCI: setting IRQ 9 as level-triggered
May 10 19:56:38 jamie-ubuntu kernel: [   19.744456] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKI] -> GSI 9 (level, low) -> IRQ 9
May 10 19:56:38 jamie-ubuntu kernel: [   19.744479] ohci_hcd 0000:00:02.0: OHCI Host Controller
May 10 19:56:38 jamie-ubuntu kernel: [   19.744920] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
May 10 19:56:38 jamie-ubuntu kernel: [   19.744946] ohci_hcd 0000:00:02.0: irq 9, io mem 0xdd800000
May 10 19:56:38 jamie-ubuntu kernel: [   19.746823] SCSI subsystem initialized
May 10 19:56:38 jamie-ubuntu kernel: [   19.762031] libata version 3.00 loaded.
May 10 19:56:38 jamie-ubuntu kernel: [   19.799396] usb usb1: configuration #1 chosen from 1 choice
May 10 19:56:38 jamie-ubuntu kernel: [   19.799437] hub 1-0:1.0: USB hub found
May 10 19:56:38 jamie-ubuntu kernel: [   19.799452] hub 1-0:1.0: 4 ports detected
May 10 19:56:38 jamie-ubuntu kernel: [   19.901810] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
May 10 19:56:38 jamie-ubuntu kernel: [   19.901818] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
May 10 19:56:38 jamie-ubuntu kernel: [   19.901843] ohci_hcd 0000:00:06.0: OHCI Host Controller
May 10 19:56:38 jamie-ubuntu kernel: [   19.901891] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 2
May 10 19:56:38 jamie-ubuntu kernel: [   19.901913] ohci_hcd 0000:00:06.0: irq 9, io mem 0xdc800000
May 10 19:56:38 jamie-ubuntu kernel: [   19.959251] usb usb2: configuration #1 chosen from 1 choice
May 10 19:56:38 jamie-ubuntu kernel: [   19.959291] hub 2-0:1.0: USB hub found
May 10 19:56:38 jamie-ubuntu kernel: [   19.959303] hub 2-0:1.0: 2 ports detected
May 10 19:56:38 jamie-ubuntu kernel: [   20.061781] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
May 10 19:56:38 jamie-ubuntu kernel: [   20.061789] PCI: setting IRQ 11 as level-triggered
May 10 19:56:38 jamie-ubuntu kernel: [   20.061794] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
May 10 19:56:38 jamie-ubuntu kernel: [   20.061819] ohci_hcd 0000:00:0c.0: OHCI Host Controller
May 10 19:56:38 jamie-ubuntu kernel: [   20.061869] ohci_hcd 0000:00:0c.0: new USB bus registered, assigned bus number 3
May 10 19:56:38 jamie-ubuntu kernel: [   20.061891] ohci_hcd 0000:00:0c.0: irq 11, io mem 0xda800000
May 10 19:56:38 jamie-ubuntu kernel: [   20.148589] usb usb3: configuration #1 chosen from 1 choice
May 10 19:56:38 jamie-ubuntu kernel: [   20.148820] hub 3-0:1.0: USB hub found
May 10 19:56:38 jamie-ubuntu kernel: [   20.148835] hub 3-0:1.0: 3 ports detected
May 10 19:56:38 jamie-ubuntu kernel: [   20.205080] usb 1-3: new full speed USB device using ohci_hcd and address 2
May 10 19:56:38 jamie-ubuntu kernel: [   20.249719] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
May 10 19:56:38 jamie-ubuntu kernel: [   20.249724] PCI: setting IRQ 10 as level-triggered
May 10 19:56:38 jamie-ubuntu kernel: [   20.249729] ACPI: PCI Interrupt 0000:00:0c.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
May 10 19:56:38 jamie-ubuntu kernel: [   20.249755] ohci_hcd 0000:00:0c.1: OHCI Host Controller
May 10 19:56:38 jamie-ubuntu kernel: [   20.249804] ohci_hcd 0000:00:0c.1: new USB bus registered, assigned bus number 4
May 10 19:56:38 jamie-ubuntu kernel: [   20.249828] ohci_hcd 0000:00:0c.1: irq 10, io mem 0xda000000
May 10 19:56:38 jamie-ubuntu kernel: [   20.336595] usb usb4: configuration #1 chosen from 1 choice
May 10 19:56:38 jamie-ubuntu kernel: [   20.336857] hub 4-0:1.0: USB hub found
May 10 19:56:38 jamie-ubuntu kernel: [   20.336873] hub 4-0:1.0: 2 ports detected
May 10 19:56:38 jamie-ubuntu kernel: [   20.438252] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
May 10 19:56:38 jamie-ubuntu kernel: [   20.438260] PCI: setting IRQ 5 as level-triggered
May 10 19:56:38 jamie-ubuntu kernel: [   20.438265] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
May 10 19:56:38 jamie-ubuntu kernel: [   20.453347] eth0: VIA Rhine at 0xd9800000, 00:50:ba:a1:9f:88, IRQ 5.
May 10 19:56:38 jamie-ubuntu kernel: [   20.461479] ACPI: PCI Interrupt 0000:00:0c.2[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
May 10 19:56:38 jamie-ubuntu kernel: [   20.461506] ehci_hcd 0000:00:0c.2: EHCI Host Controller
May 10 19:56:38 jamie-ubuntu kernel: [   20.461560] ehci_hcd 0000:00:0c.2: new USB bus registered, assigned bus number 5
May 10 19:56:38 jamie-ubuntu kernel: [   20.461635] ehci_hcd 0000:00:0c.2: irq 5, io mem 0x30000000
May 10 19:56:38 jamie-ubuntu kernel: [   20.473041] ehci_hcd 0000:00:0c.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May 10 19:56:38 jamie-ubuntu kernel: [   20.473247] usb usb5: configuration #1 chosen from 1 choice
May 10 19:56:38 jamie-ubuntu kernel: [   20.473299] hub 5-0:1.0: USB hub found
May 10 19:56:38 jamie-ubuntu kernel: [   20.473311] hub 5-0:1.0: 5 ports detected
May 10 19:56:38 jamie-ubuntu kernel: [   20.512174] usb 1-3: configuration #1 chosen from 1 choice
May 10 19:56:38 jamie-ubuntu kernel: [   20.613122] hda: max request size: 128KiB
May 10 19:56:38 jamie-ubuntu kernel: [   20.613364] hda: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63
May 10 19:56:38 jamie-ubuntu kernel: [   20.615154] hda: cache flushes supported
May 10 19:56:38 jamie-ubuntu kernel: [   20.615218]  hda: hda1
May 10 19:56:38 jamie-ubuntu kernel: [   20.625630] hdb: max request size: 128KiB
May 10 19:56:38 jamie-ubuntu kernel: [   20.625765] hdb: 60058656 sectors (30750 MB) w/2048KiB Cache, CHS=59582/16/63
May 10 19:56:38 jamie-ubuntu kernel: [   20.625877] hdb: cache flushes supported
May 10 19:56:38 jamie-ubuntu kernel: [   20.625924]  hdb: hdb1 hdb2 < hdb5 >
May 10 19:56:38 jamie-ubuntu kernel: [   20.669028] hdc: ATAPI 24X CD-ROM CD-R/RW drive, 1024kB Cache
May 10 19:56:38 jamie-ubuntu kernel: [   20.669046] Uniform CD-ROM driver Revision: 3.20
May 10 19:56:38 jamie-ubuntu kernel: [   20.683176] hdd: ATAPI 52X DVD-ROM drive, 256kB Cache
May 10 19:56:38 jamie-ubuntu kernel: [   21.006112] Attempting manual resume
May 10 19:56:38 jamie-ubuntu kernel: [   21.006120] swsusp: Resume From Partition 3:69
May 10 19:56:38 jamie-ubuntu kernel: [   21.006122] PM: Checking swsusp image.
May 10 19:56:38 jamie-ubuntu kernel: [   21.006449] PM: Resume from disk failed.
May 10 19:56:38 jamie-ubuntu kernel: [   21.017116] usb 5-1: new high speed USB device using ehci_hcd and address 2
May 10 19:56:38 jamie-ubuntu kernel: [   21.030266] EXT3-fs: INFO: recovery required on readonly filesystem.
May 10 19:56:38 jamie-ubuntu kernel: [   21.030275] EXT3-fs: write access will be enabled during recovery.
May 10 19:56:38 jamie-ubuntu kernel: [   21.150624] usb 5-1: configuration #1 chosen from 1 choice
May 10 19:56:38 jamie-ubuntu kernel: [   21.388827] usb 5-4: new high speed USB device using ehci_hcd and address 3
May 10 19:56:38 jamie-ubuntu kernel: [   21.530035] usb 5-4: configuration #1 chosen from 1 choice
May 10 19:56:38 jamie-ubuntu kernel: [   21.530773] usbcore: registered new interface driver libusual
May 10 19:56:38 jamie-ubuntu kernel: [   21.541122] Initializing USB Mass Storage driver...
May 10 19:56:38 jamie-ubuntu kernel: [   21.545998] scsi0 : SCSI emulation for USB Mass Storage devices
May 10 19:56:38 jamie-ubuntu kernel: [   21.547191] usb-storage: device found at 2
May 10 19:56:38 jamie-ubuntu kernel: [   21.547198] usb-storage: waiting for device to settle before scanning
May 10 19:56:38 jamie-ubuntu kernel: [   21.549336] scsi1 : SCSI emulation for USB Mass Storage devices
May 10 19:56:38 jamie-ubuntu kernel: [   21.551832] usbcore: registered new interface driver usb-storage
May 10 19:56:38 jamie-ubuntu kernel: [   21.551846] USB Mass Storage support registered.
May 10 19:56:38 jamie-ubuntu kernel: [   21.552060] usb-storage: device found at 2
May 10 19:56:38 jamie-ubuntu kernel: [   21.552064] usb-storage: waiting for device to settle before scanning
May 10 19:56:38 jamie-ubuntu kernel: [   26.105027] kjournald starting.  Commit interval 5 seconds
May 10 19:56:38 jamie-ubuntu kernel: [   26.105068] EXT3-fs: hdb1: orphan cleanup on readonly fs
May 10 19:56:38 jamie-ubuntu kernel: [   26.105081] ext3_orphan_cleanup: deleting unreferenced inode 213004
May 10 19:56:38 jamie-ubuntu kernel: [   26.105141] EXT3-fs: hdb1: 1 orphan inode deleted
May 10 19:56:38 jamie-ubuntu kernel: [   26.105145] EXT3-fs: recovery complete.
May 10 19:56:38 jamie-ubuntu kernel: [   26.151272] EXT3-fs: mounted filesystem with ordered data mode.
May 10 19:56:38 jamie-ubuntu kernel: [   26.545504] usb-storage: device scan complete
May 10 19:56:38 jamie-ubuntu kernel: [   26.548574] usb-storage: device scan complete
May 10 19:56:38 jamie-ubuntu kernel: [   26.549236] scsi 1:0:0:0: Direct-Access     ST380021 A                0811 PQ: 0 ANSI: 0
May 10 19:56:38 jamie-ubuntu kernel: [   26.581496] scsi 0:0:0:0: Direct-Access     Generic  2.0 Reader   -CF 1.00 PQ: 0 ANSI: 0 CCS
May 10 19:56:38 jamie-ubuntu kernel: [   26.615479] scsi 0:0:0:1: Direct-Access     Generic  2.0 Reader   -SM 1.00 PQ: 0 ANSI: 0 CCS
May 10 19:56:38 jamie-ubuntu kernel: [   26.649519] scsi 0:0:0:2: Direct-Access     Generic  2.0 Reader   -SD 1.00 PQ: 0 ANSI: 0 CCS
May 10 19:56:38 jamie-ubuntu kernel: [   26.683507] scsi 0:0:0:3: Direct-Access     Generic  2.0 Reader   -MS 1.00 PQ: 0 ANSI: 0 CCS
May 10 19:56:38 jamie-ubuntu kernel: [   26.717415] scsi 0:0:0:4: Direct-Access     Generic  2.0 Reader   -xD 1.00 PQ: 0 ANSI: 0 CCS
May 10 19:56:38 jamie-ubuntu kernel: [   34.914327] Linux agpgart interface v0.102
May 10 19:56:38 jamie-ubuntu kernel: [   34.990412] agpgart: Detected ALi M1647 chipset
May 10 19:56:38 jamie-ubuntu kernel: [   35.060131] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 10 19:56:38 jamie-ubuntu kernel: [   35.083646] agpgart: AGP aperture is 128M @ 0xf0000000
May 10 19:56:38 jamie-ubuntu kernel: [   35.132668] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 10 19:56:38 jamie-ubuntu kernel: [   35.955404] input: Power Button (FF) as /devices/virtual/input/input2
May 10 19:56:38 jamie-ubuntu kernel: [   35.970100] ACPI: Power Button (FF) [PWRF]
May 10 19:56:38 jamie-ubuntu kernel: [   35.970332] input: Power Button (CM) as /devices/virtual/input/input3
May 10 19:56:38 jamie-ubuntu kernel: [   35.986071] ACPI: Power Button (CM) [PWRB]
May 10 19:56:38 jamie-ubuntu kernel: [   38.626466] nvidia: module license 'NVIDIA' taints kernel.
May 10 19:56:38 jamie-ubuntu kernel: [   39.541604] input: PC Speaker as /devices/platform/pcspkr/input/input4
May 10 19:56:38 jamie-ubuntu kernel: [   39.833991] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
May 10 19:56:38 jamie-ubuntu kernel: [   39.834001] PCI: setting IRQ 6 as level-triggered
May 10 19:56:38 jamie-ubuntu kernel: [   39.834006] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
May 10 19:56:38 jamie-ubuntu kernel: [   39.834034] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
May 10 19:56:38 jamie-ubuntu kernel: [   40.473357] logips2pp: Detected unknown logitech mouse model 127
May 10 19:56:38 jamie-ubuntu kernel: [   40.565135] Driver 'sd' needs updating - please use bus_type methods
May 10 19:56:38 jamie-ubuntu kernel: [   40.576016] sd 0:0:0:0: [sda] Attached SCSI removable disk
May 10 19:56:38 jamie-ubuntu kernel: [   40.587025] sd 0:0:0:1: [sdb] Attached SCSI removable disk
May 10 19:56:38 jamie-ubuntu kernel: [   40.598042] sd 0:0:0:2: [sdc] Attached SCSI removable disk
May 10 19:56:38 jamie-ubuntu kernel: [   40.609056] sd 0:0:0:3: [sdd] Attached SCSI removable disk
May 10 19:56:38 jamie-ubuntu kernel: [   40.620057] sd 0:0:0:4: [sde] Attached SCSI removable disk
May 10 19:56:38 jamie-ubuntu kernel: [   40.621451] sd 1:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
May 10 19:56:38 jamie-ubuntu kernel: [   40.622698] sd 1:0:0:0: [sdf] Test WP failed, assume Write Enabled
May 10 19:56:38 jamie-ubuntu kernel: [   40.622703] sd 1:0:0:0: [sdf] Assuming drive cache: write through
May 10 19:56:38 jamie-ubuntu kernel: [   40.623698] sd 1:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
May 10 19:56:38 jamie-ubuntu kernel: [   40.624946] sd 1:0:0:0: [sdf] Test WP failed, assume Write Enabled
May 10 19:56:38 jamie-ubuntu kernel: [   40.624950] sd 1:0:0:0: [sdf] Assuming drive cache: write through
May 10 19:56:38 jamie-ubuntu kernel: [   40.624958]  sdf: unknown partition table
May 10 19:56:38 jamie-ubuntu kernel: [   40.638277] sd 1:0:0:0: [sdf] Attached SCSI disk
May 10 19:56:38 jamie-ubuntu kernel: [   40.665917] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 10 19:56:38 jamie-ubuntu kernel: [   40.665979] sd 0:0:0:1: Attached scsi generic sg1 type 0
May 10 19:56:38 jamie-ubuntu kernel: [   40.666075] sd 0:0:0:2: Attached scsi generic sg2 type 0
May 10 19:56:38 jamie-ubuntu kernel: [   40.666130] sd 0:0:0:3: Attached scsi generic sg3 type 0
May 10 19:56:38 jamie-ubuntu kernel: [   40.666180] sd 0:0:0:4: Attached scsi generic sg4 type 0
May 10 19:56:38 jamie-ubuntu kernel: [   40.666238] sd 1:0:0:0: Attached scsi generic sg5 type 0
May 10 19:56:38 jamie-ubuntu kernel: [   40.949631] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
May 10 19:56:38 jamie-ubuntu kernel: [   40.999837] parport_pc 00:09: reported by Plug and Play ACPI
May 10 19:56:38 jamie-ubuntu kernel: [   40.999942] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
May 10 19:56:38 jamie-ubuntu kernel: [   41.512057] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
May 10 19:56:38 jamie-ubuntu kernel: [   41.513056] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
May 10 19:56:38 jamie-ubuntu kernel: [   45.562224] lp0: using parport0 (interrupt-driven).
May 10 19:56:38 jamie-ubuntu kernel: [   45.602770] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
May 10 19:56:38 jamie-ubuntu kernel: [   45.684038] ndiswrapper: driver net8185 (Realtek,01/29/2007,5.1096.0129.2007) loaded
May 10 19:56:38 jamie-ubuntu kernel: [   45.685009] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 9
May 10 19:56:38 jamie-ubuntu kernel: [   45.685015] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKF] -> GSI 9 (level, low) -> IRQ 9
May 10 19:56:38 jamie-ubuntu kernel: [   45.957263] ndiswrapper: using IRQ 9
May 10 19:56:38 jamie-ubuntu kernel: [   50.896967] wlan0: ethernet device 00:14:d1:3e:dd:b8 using NDIS driver: net8185, version: 0x50448, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
May 10 19:56:38 jamie-ubuntu kernel: [   50.897126] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
May 10 19:56:38 jamie-ubuntu kernel: [   50.900368] usbcore: registered new interface driver ndiswrapper
May 10 19:56:38 jamie-ubuntu kernel: [   50.995470] Adding 1277128k swap on /dev/hdb5.  Priority:-1 extents:1 across:1277128k
May 10 19:56:38 jamie-ubuntu kernel: [   51.588547] EXT3 FS on hdb1, internal journal
May 10 19:56:38 jamie-ubuntu kernel: [   53.021020] ip_tables: (C) 2000-2006 Netfilter Core Team
May 10 19:56:38 jamie-ubuntu kernel: [   53.674265] No dock devices found.
May 10 19:56:38 jamie-ubuntu kernel: [   54.246403] powernow: No powernow capabilities detected
May 10 19:56:38 jamie-ubuntu NetworkManager: <info>  starting... 
May 10 19:56:38 jamie-ubuntu avahi-daemon[5051]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
May 10 19:56:38 jamie-ubuntu avahi-daemon[5051]: Successfully dropped root privileges.
May 10 19:56:38 jamie-ubuntu avahi-daemon[5051]: avahi-daemon 0.6.22 starting up.
May 10 19:56:38 jamie-ubuntu avahi-daemon[5051]: Successfully called chroot().
May 10 19:56:38 jamie-ubuntu avahi-daemon[5051]: Successfully dropped remaining capabilities.
May 10 19:56:38 jamie-ubuntu avahi-daemon[5051]: No service file found in /etc/avahi/services.
May 10 19:56:38 jamie-ubuntu avahi-daemon[5051]: Network interface enumeration completed.
May 10 19:56:38 jamie-ubuntu avahi-daemon[5051]: Registering HINFO record with values 'I686'/'LINUX'.
May 10 19:56:38 jamie-ubuntu avahi-daemon[5051]: Server startup complete. Host name is jamie-ubuntu.local. Local service cookie is 3553020820.
May 10 19:56:38 jamie-ubuntu kernel: [   55.377780] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 10 19:56:38 jamie-ubuntu kernel: [   55.377791] apm: overridden by ACPI.
May 10 19:56:39 jamie-ubuntu kernel: [   55.516149] ppdev: user-space parallel port driver
May 10 19:56:39 jamie-ubuntu kernel: [   55.689031] audit(1210474599.240:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5091 profile="/usr/sbin/cupsd" namespace="default"
May 10 19:56:39 jamie-ubuntu dhcdbd: Started up.
May 10 19:59:20 jamie-ubuntu syslogd 1.5.0#1ubuntu1: restart.
May 10 19:59:20 jamie-ubuntu kernel: Inspecting /boot/System.map-2.6.24-16-generic
May 10 19:59:20 jamie-ubuntu kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
May 10 19:59:20 jamie-ubuntu kernel: Symbols match kernel version 2.6.24.
May 10 19:59:20 jamie-ubuntu kernel: Loaded 32476 symbols from 81 modules.
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] 511MB LOWMEM available.
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 131052) 0 entries of 256 used
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Zone PFN ranges:
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]   DMA             0 ->     4096
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]   Normal       4096 ->   131052
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]   HighMem    131052 ->   131052
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Movable zone start PFN for each node
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]     0:        0 ->   131052
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] On node 0 totalpages: 131052
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]   Normal zone: 991 pages used for memmap
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]   Normal zone: 125965 pages, LIFO batch:31
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] DMI 2.3 present.
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 ASUS  )
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] ACPI: RSDT 1FFEC000, 002C (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] ACPI: FACP 1FFEC080, 0074 (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] ACPI: DSDT 1FFEC100, 291E (r1   ASUS A7A266       1000 MSFT  100000B)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] ACPI: FACS 1FFFF000, 0040
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] ACPI: BOOT 1FFEC040, 0028 (r1 ASUS   A7A266   42302E31 MSFT 31313031)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130029
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Kernel command line: root=UUID=9f65524a-b784-4baa-b7f6-6e62db2cecf1 ro quiet splash
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] mapped APIC to ffffb000 (0140d000)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Initializing CPU#0
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
May 10 19:59:20 jamie-ubuntu kernel: [    0.000000] Detected 1410.259 MHz processor.
May 10 19:59:20 jamie-ubuntu kernel: [   12.790065] Console: colour VGA+ 80x25
May 10 19:59:20 jamie-ubuntu kernel: [   12.790070] console [tty0] enabled
May 10 19:59:20 jamie-ubuntu kernel: [   12.790667] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
May 10 19:59:20 jamie-ubuntu kernel: [   12.791103] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
May 10 19:59:20 jamie-ubuntu kernel: [   12.817888] Memory: 507300k/524208k available (2157k kernel code, 16308k reserved, 998k data, 364k init, 0k highmem)
May 10 19:59:20 jamie-ubuntu kernel: [   12.817902] virtual kernel memory layout:
May 10 19:59:20 jamie-ubuntu kernel: [   12.817904]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May 10 19:59:20 jamie-ubuntu kernel: [   12.817906]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May 10 19:59:20 jamie-ubuntu kernel: [   12.817907]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
May 10 19:59:20 jamie-ubuntu kernel: [   12.817909]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
May 10 19:59:20 jamie-ubuntu kernel: [   12.817911]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
May 10 19:59:20 jamie-ubuntu kernel: [   12.817913]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
May 10 19:59:20 jamie-ubuntu kernel: [   12.817915]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
May 10 19:59:20 jamie-ubuntu kernel: [   12.817920] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May 10 19:59:20 jamie-ubuntu kernel: [   12.817985] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
May 10 19:59:20 jamie-ubuntu kernel: [   12.898012] Calibrating delay using timer specific routine.. 2822.62 BogoMIPS (lpj=5645257)
May 10 19:59:20 jamie-ubuntu kernel: [   12.898058] Security Framework initialized
May 10 19:59:20 jamie-ubuntu kernel: [   12.898069] SELinux:  Disabled at boot.
May 10 19:59:20 jamie-ubuntu kernel: [   12.898100] AppArmor: AppArmor initialized
May 10 19:59:20 jamie-ubuntu kernel: [   12.898108] Failure registering capabilities with primary security module.
May 10 19:59:20 jamie-ubuntu kernel: [   12.898123] Mount-cache hash table entries: 512
May 10 19:59:20 jamie-ubuntu kernel: [   12.898320] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000 00000000
May 10 19:59:20 jamie-ubuntu kernel: [   12.898334] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May 10 19:59:20 jamie-ubuntu kernel: [   12.898339] CPU: L2 Cache: 256K (64 bytes/line)
May 10 19:59:20 jamie-ubuntu kernel: [   12.898343] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000 00000000
May 10 19:59:20 jamie-ubuntu kernel: [   12.898359] Compat vDSO mapped to ffffe000.
May 10 19:59:20 jamie-ubuntu kernel: [   12.898378] Checking 'hlt' instruction... OK.
May 10 19:59:20 jamie-ubuntu kernel: [   12.914073] SMP alternatives: switching to UP code
May 10 19:59:20 jamie-ubuntu kernel: [   12.915671] Freeing SMP alternatives: 11k freed
May 10 19:59:20 jamie-ubuntu kernel: [   12.915881] Early unpacking initramfs... done
May 10 19:59:20 jamie-ubuntu kernel: [   13.424091] ACPI: Core revision 20070126
May 10 19:59:20 jamie-ubuntu kernel: [   13.424238] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 10 19:59:20 jamie-ubuntu kernel: [   13.425356] ACPI: setting ELCR to 0200 (from 0e60)
May 10 19:59:20 jamie-ubuntu kernel: [   13.425692] CPU0: AMD Athlon(TM)Processor stepping 04
May 10 19:59:20 jamie-ubuntu kernel: [   13.425701] SMP motherboard not detected.
May 10 19:59:20 jamie-ubuntu kernel: [   13.425705] Local APIC not detected. Using dummy APIC emulation.
May 10 19:59:20 jamie-ubuntu kernel: [   13.425788] Brought up 1 CPUs
May 10 19:59:20 jamie-ubuntu kernel: [   13.425832] CPU0 attaching sched-domain:
May 10 19:59:20 jamie-ubuntu kernel: [   13.425837]  domain 0: span 01
May 10 19:59:20 jamie-ubuntu kernel: [   13.425839]   groups: 01
May 10 19:59:20 jamie-ubuntu kernel: [   13.426205] net_namespace: 64 bytes
May 10 19:59:20 jamie-ubuntu kernel: [   13.426218] Booting paravirtualized kernel on bare hardware
May 10 19:59:20 jamie-ubuntu kernel: [   13.426960] Time: 19:58:43  Date: 05/10/08
May 10 19:59:20 jamie-ubuntu kernel: [   13.427014] NET: Registered protocol family 16
May 10 19:59:20 jamie-ubuntu kernel: [   13.427356] EISA bus registered
May 10 19:59:20 jamie-ubuntu kernel: [   13.427376] ACPI: bus type pci registered
May 10 19:59:20 jamie-ubuntu kernel: [   13.429095] PCI: PCI BIOS revision 2.10 entry at 0xf1170, last bus=1
May 10 19:59:20 jamie-ubuntu kernel: [   13.429099] PCI: Using configuration type 1
May 10 19:59:20 jamie-ubuntu kernel: [   13.429101] Setting up standard PCI resources
May 10 19:59:20 jamie-ubuntu kernel: [   13.440673] ACPI: EC: Look up EC in DSDT
May 10 19:59:20 jamie-ubuntu kernel: [   13.444075] ACPI: Interpreter enabled
May 10 19:59:20 jamie-ubuntu kernel: [   13.444081] ACPI: (supports S0 S1 S4 S5)
May 10 19:59:20 jamie-ubuntu kernel: [   13.444100] ACPI: Using PIC for interrupt routing
May 10 19:59:20 jamie-ubuntu kernel: [   13.450759] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 10 19:59:20 jamie-ubuntu kernel: [   13.451319] PCI quirk: region e400-e43f claimed by ali7101 ACPI
May 10 19:59:20 jamie-ubuntu kernel: [   13.451324] PCI quirk: region e800-e81f claimed by ali7101 SMB
May 10 19:59:20 jamie-ubuntu kernel: [   13.451468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 10 19:59:20 jamie-ubuntu kernel: [   13.451704] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
May 10 19:59:20 jamie-ubuntu kernel: [   13.453406] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May 10 19:59:20 jamie-ubuntu kernel: [   13.453566] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
May 10 19:59:20 jamie-ubuntu kernel: [   13.453721] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May 10 19:59:20 jamie-ubuntu kernel: [   13.453873] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
May 10 19:59:20 jamie-ubuntu kernel: [   13.454138] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 19:59:20 jamie-ubuntu kernel: [   13.454295] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 19:59:20 jamie-ubuntu kernel: [   13.454385] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May 10 19:59:20 jamie-ubuntu kernel: [   13.454473] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May 10 19:59:20 jamie-ubuntu kernel: [   13.454627] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 10 19:59:20 jamie-ubuntu kernel: [   13.454940] Linux Plug and Play Support v0.97 (c) Adam Belay
May 10 19:59:20 jamie-ubuntu kernel: [   13.454991] pnp: PnP ACPI init
May 10 19:59:20 jamie-ubuntu kernel: [   13.455008] ACPI: bus type pnp registered
May 10 19:59:20 jamie-ubuntu kernel: [   13.460030] pnp: PnP ACPI: found 14 devices
May 10 19:59:21 jamie-ubuntu kernel: [   13.460034] ACPI: ACPI bus type pnp unregistered
May 10 19:59:21 jamie-ubuntu kernel: [   13.460040] PnPBIOS: Disabled by ACPI PNP
May 10 19:59:21 jamie-ubuntu kernel: [   13.460429] PCI: Using ACPI for IRQ routing
May 10 19:59:21 jamie-ubuntu kernel: [   13.460436] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 10 19:59:21 jamie-ubuntu kernel: [   13.460473] PCI: Cannot allocate resource region 0 of device 0000:00:0c.2
May 10 19:59:21 jamie-ubuntu kernel: [   13.486010] NET: Registered protocol family 8
May 10 19:59:21 jamie-ubuntu kernel: [   13.486013] NET: Registered protocol family 20
May 10 19:59:21 jamie-ubuntu kernel: [   13.486139] AppArmor: AppArmor Filesystem Enabled
May 10 19:59:21 jamie-ubuntu kernel: [   13.489994] Time: tsc clocksource has been installed.
May 10 19:59:21 jamie-ubuntu kernel: [   13.498055] system 00:00: iomem range 0x0-0x9ffff could not be reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.498060] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.498064] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.498068] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.498080] system 00:02: ioport range 0xe400-0xe47f could not be reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.498084] system 00:02: ioport range 0xe800-0xe81f has been reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.498089] system 00:02: ioport range 0x40b-0x40b has been reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.498092] system 00:02: ioport range 0x480-0x48f has been reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.498097] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.498109] system 00:03: iomem range 0xfffe0000-0xffffffff could not be reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.498120] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
May 10 19:59:21 jamie-ubuntu kernel: [   13.528797] PCI: Bridge: 0000:00:01.0
May 10 19:59:21 jamie-ubuntu kernel: [   13.528801]   IO window: disabled.
May 10 19:59:21 jamie-ubuntu kernel: [   13.528807]   MEM window: de000000-dfdfffff
May 10 19:59:21 jamie-ubuntu kernel: [   13.528811]   PREFETCH window: dff00000-efffffff
May 10 19:59:21 jamie-ubuntu kernel: [   13.528827] PCI: Setting latency timer of device 0000:00:01.0 to 64
May 10 19:59:21 jamie-ubuntu kernel: [   13.528847] NET: Registered protocol family 2
May 10 19:59:21 jamie-ubuntu kernel: [   13.566136] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
May 10 19:59:21 jamie-ubuntu kernel: [   13.566496] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
May 10 19:59:21 jamie-ubuntu kernel: [   13.566897] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
May 10 19:59:21 jamie-ubuntu kernel: [   13.567303] TCP: Hash tables configured (established 16384 bind 16384)
May 10 19:59:21 jamie-ubuntu kernel: [   13.567307] TCP reno registered
May 10 19:59:21 jamie-ubuntu kernel: [   13.578239] checking if image is initramfs... it is
May 10 19:59:21 jamie-ubuntu kernel: [   14.030027] Switched to high resolution mode on CPU 0
May 10 19:59:21 jamie-ubuntu kernel: [   14.538908] Freeing initrd memory: 7697k freed
May 10 19:59:21 jamie-ubuntu kernel: [   14.539206] Simple Boot Flag at 0x3a set to 0x1
May 10 19:59:21 jamie-ubuntu kernel: [   14.539957] audit: initializing netlink socket (disabled)
May 10 19:59:21 jamie-ubuntu kernel: [   14.539983] audit(1210449523.724:1): initialized
May 10 19:59:21 jamie-ubuntu kernel: [   14.543105] VFS: Disk quotas dquot_6.5.1
May 10 19:59:21 jamie-ubuntu kernel: [   14.543235] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 10 19:59:21 jamie-ubuntu kernel: [   14.543468] io scheduler noop registered
May 10 19:59:21 jamie-ubuntu kernel: [   14.543472] io scheduler anticipatory registered
May 10 19:59:21 jamie-ubuntu kernel: [   14.543475] io scheduler deadline registered
May 10 19:59:21 jamie-ubuntu kernel: [   14.543490] io scheduler cfq registered (default)
May 10 19:59:21 jamie-ubuntu kernel: [   14.543508] Limiting direct PCI/PCI transfers.
May 10 19:59:21 jamie-ubuntu kernel: [   14.543537] Activating ISA DMA hang workarounds.
May 10 19:59:21 jamie-ubuntu kernel: [   14.543568] Boot video device is 0000:01:00.0
May 10 19:59:21 jamie-ubuntu kernel: [   14.544004] isapnp: Scanning for PnP cards...
May 10 19:59:21 jamie-ubuntu kernel: [   14.898191] isapnp: No Plug & Play device found
May 10 19:59:21 jamie-ubuntu kernel: [   14.944750] Real Time Clock Driver v1.12ac
May 10 19:59:21 jamie-ubuntu kernel: [   14.944923] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 10 19:59:21 jamie-ubuntu kernel: [   14.945154] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 10 19:59:21 jamie-ubuntu kernel: [   14.945399] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 10 19:59:21 jamie-ubuntu kernel: [   14.946415] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 10 19:59:21 jamie-ubuntu kernel: [   14.946995] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 10 19:59:21 jamie-ubuntu kernel: [   14.948327] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 10 19:59:21 jamie-ubuntu kernel: [   14.948440] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 10 19:59:21 jamie-ubuntu kernel: [   14.948602] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May 10 19:59:21 jamie-ubuntu kernel: [   14.951426] serio: i8042 KBD port at 0x60,0x64 irq 1
May 10 19:59:21 jamie-ubuntu kernel: [   14.951434] serio: i8042 AUX port at 0x60,0x64 irq 12
May 10 19:59:21 jamie-ubuntu kernel: [   14.953981] mice: PS/2 mouse device common for all mice
May 10 19:59:21 jamie-ubuntu kernel: [   14.954198] EISA: Probing bus 0 at eisa.0
May 10 19:59:21 jamie-ubuntu kernel: [   14.954257] EISA: Detected 0 cards.
May 10 19:59:21 jamie-ubuntu kernel: [   14.954263] cpuidle: using governor ladder
May 10 19:59:21 jamie-ubuntu kernel: [   14.954266] cpuidle: using governor menu
May 10 19:59:21 jamie-ubuntu kernel: [   14.954493] NET: Registered protocol family 1
May 10 19:59:21 jamie-ubuntu kernel: [   14.954541] Using IPI No-Shortcut mode
May 10 19:59:21 jamie-ubuntu kernel: [   14.954600] registered taskstats version 1
May 10 19:59:21 jamie-ubuntu kernel: [   14.954760]   Magic number: 8:203:1001
May 10 19:59:21 jamie-ubuntu kernel: [   14.954775]   hash matches device ttye0
May 10 19:59:21 jamie-ubuntu kernel: [   14.955004]   hash matches device 00:03
May 10 19:59:21 jamie-ubuntu kernel: [   14.955032] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 10 19:59:21 jamie-ubuntu kernel: [   14.955036] EDD information not available.
May 10 19:59:21 jamie-ubuntu kernel: [   14.955709] Freeing unused kernel memory: 364k freed
May 10 19:59:21 jamie-ubuntu kernel: [   14.981761] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May 10 19:59:21 jamie-ubuntu kernel: [   16.321878] fuse init (API version 7.9)
May 10 19:59:21 jamie-ubuntu kernel: [   16.354131] ACPI: Invalid PBLK length [5]
May 10 19:59:21 jamie-ubuntu kernel: [   17.265406] usbcore: registered new interface driver usbfs
May 10 19:59:21 jamie-ubuntu kernel: [   17.265450] usbcore: registered new interface driver hub
May 10 19:59:21 jamie-ubuntu kernel: [   17.279641] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May 10 19:59:21 jamie-ubuntu kernel: [   17.279653] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May 10 19:59:21 jamie-ubuntu kernel: [   17.297320] usbcore: registered new device driver usb
May 10 19:59:21 jamie-ubuntu kernel: [   17.313190] ALI15X3: IDE controller (0x10b9:0x5229 rev 0xc4) at  PCI slot 0000:00:04.0
May 10 19:59:21 jamie-ubuntu kernel: [   17.313276] ACPI: Unable to derive IRQ for device 0000:00:04.0
May 10 19:59:21 jamie-ubuntu kernel: [   17.313289] ALI15X3: not 100% native mode: will probe irqs later
May 10 19:59:21 jamie-ubuntu kernel: [   17.313315]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:DMA
May 10 19:59:21 jamie-ubuntu kernel: [   17.313334]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:DMA
May 10 19:59:21 jamie-ubuntu kernel: [   17.313351] Probing IDE interface ide0...
May 10 19:59:21 jamie-ubuntu kernel: [   17.356386] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May 10 19:59:21 jamie-ubuntu kernel: [   17.372484] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
May 10 19:59:21 jamie-ubuntu kernel: [   17.601402] hdb: Maxtor 6E030L0, ATA DISK drive
May 10 19:59:21 jamie-ubuntu kernel: [   17.937332] hda: Maxtor 6Y060L0, ATA DISK drive
May 10 19:59:21 jamie-ubuntu kernel: [   17.937358] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 19:59:21 jamie-ubuntu kernel: [   17.937480] hda: UDMA/100 mode selected
May 10 19:59:21 jamie-ubuntu kernel: [   17.937573] hdb: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 19:59:21 jamie-ubuntu kernel: [   17.937677] hdb: UDMA/100 mode selected
May 10 19:59:21 jamie-ubuntu kernel: [   17.937834] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
May 10 19:59:21 jamie-ubuntu kernel: [   17.950718] Probing IDE interface ide1...
May 10 19:59:21 jamie-ubuntu kernel: [   18.741138] hdd: HL-DT-STDVD-ROM GDR8164B, ATAPI CD/DVD-ROM drive
May 10 19:59:21 jamie-ubuntu kernel: [   19.524988] hdc: Hewlett-Packard CD-Writer Plus 8100, ATAPI CD/DVD-ROM drive
May 10 19:59:21 jamie-ubuntu kernel: [   19.525012] hdc: applying conservative PIO "downgrade"
May 10 19:59:21 jamie-ubuntu kernel: [   19.525016] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO2
May 10 19:59:21 jamie-ubuntu kernel: [   19.525560] hdc: MWDMA1 mode selected
May 10 19:59:21 jamie-ubuntu kernel: [   19.526116] hdd: host max PIO5 wanted PIO255(auto-tune) selected PIO4
May 10 19:59:21 jamie-ubuntu kernel: [   19.526546] hdd: UDMA/33 mode selected
May 10 19:59:21 jamie-ubuntu kernel: [   19.527151] ide1 at 0x170-0x177,0x376 on irq 15
May 10 19:59:21 jamie-ubuntu kernel: [   19.548021] ACPI: PCI Interrupt Link [LNKI] enabled at IRQ 9
May 10 19:59:21 jamie-ubuntu kernel: [   19.548029] PCI: setting IRQ 9 as level-triggered
May 10 19:59:21 jamie-ubuntu kernel: [   19.548033] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKI] -> GSI 9 (level, low) -> IRQ 9
May 10 19:59:21 jamie-ubuntu kernel: [   19.548056] ohci_hcd 0000:00:02.0: OHCI Host Controller
May 10 19:59:21 jamie-ubuntu kernel: [   19.548468] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
May 10 19:59:21 jamie-ubuntu kernel: [   19.548495] ohci_hcd 0000:00:02.0: irq 9, io mem 0xdd800000
May 10 19:59:21 jamie-ubuntu kernel: [   19.550385] SCSI subsystem initialized
May 10 19:59:21 jamie-ubuntu kernel: [   19.565618] libata version 3.00 loaded.
May 10 19:59:21 jamie-ubuntu kernel: [   19.603032] usb usb1: configuration #1 chosen from 1 choice
May 10 19:59:21 jamie-ubuntu kernel: [   19.603074] hub 1-0:1.0: USB hub found
May 10 19:59:21 jamie-ubuntu kernel: [   19.603088] hub 1-0:1.0: 4 ports detected
May 10 19:59:21 jamie-ubuntu kernel: [   19.705429] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
May 10 19:59:21 jamie-ubuntu kernel: [   19.705438] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
May 10 19:59:21 jamie-ubuntu kernel: [   19.705464] ohci_hcd 0000:00:06.0: OHCI Host Controller
May 10 19:59:21 jamie-ubuntu kernel: [   19.705510] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 2
May 10 19:59:21 jamie-ubuntu kernel: [   19.705532] ohci_hcd 0000:00:06.0: irq 9, io mem 0xdc800000
May 10 19:59:21 jamie-ubuntu kernel: [   19.762881] usb usb2: configuration #1 chosen from 1 choice
May 10 19:59:21 jamie-ubuntu kernel: [   19.762922] hub 2-0:1.0: USB hub found
May 10 19:59:21 jamie-ubuntu kernel: [   19.762934] hub 2-0:1.0: 2 ports detected
May 10 19:59:21 jamie-ubuntu kernel: [   19.865403] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
May 10 19:59:21 jamie-ubuntu kernel: [   19.865412] PCI: setting IRQ 11 as level-triggered
May 10 19:59:21 jamie-ubuntu kernel: [   19.865416] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
May 10 19:59:21 jamie-ubuntu kernel: [   19.865442] ohci_hcd 0000:00:0c.0: OHCI Host Controller
May 10 19:59:21 jamie-ubuntu kernel: [   19.865491] ohci_hcd 0000:00:0c.0: new USB bus registered, assigned bus number 3
May 10 19:59:21 jamie-ubuntu kernel: [   19.865514] ohci_hcd 0000:00:0c.0: irq 11, io mem 0xda800000
May 10 19:59:21 jamie-ubuntu kernel: [   19.951294] usb usb3: configuration #1 chosen from 1 choice
May 10 19:59:21 jamie-ubuntu kernel: [   19.951527] hub 3-0:1.0: USB hub found
May 10 19:59:21 jamie-ubuntu kernel: [   19.951543] hub 3-0:1.0: 3 ports detected
May 10 19:59:21 jamie-ubuntu kernel: [   20.008688] usb 1-3: new full speed USB device using ohci_hcd and address 2
May 10 19:59:21 jamie-ubuntu kernel: [   20.053351] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
May 10 19:59:21 jamie-ubuntu kernel: [   20.053356] PCI: setting IRQ 10 as level-triggered
May 10 19:59:21 jamie-ubuntu kernel: [   20.053361] ACPI: PCI Interrupt 0000:00:0c.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
May 10 19:59:21 jamie-ubuntu kernel: [   20.053386] ohci_hcd 0000:00:0c.1: OHCI Host Controller
May 10 19:59:21 jamie-ubuntu kernel: [   20.053435] ohci_hcd 0000:00:0c.1: new USB bus registered, assigned bus number 4
May 10 19:59:21 jamie-ubuntu kernel: [   20.053458] ohci_hcd 0000:00:0c.1: irq 10, io mem 0xda000000
May 10 19:59:21 jamie-ubuntu kernel: [   20.140226] usb usb4: configuration #1 chosen from 1 choice
May 10 19:59:21 jamie-ubuntu kernel: [   20.140488] hub 4-0:1.0: USB hub found
May 10 19:59:21 jamie-ubuntu kernel: [   20.140504] hub 4-0:1.0: 2 ports detected
May 10 19:59:21 jamie-ubuntu kernel: [   20.241888] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
May 10 19:59:21 jamie-ubuntu kernel: [   20.241897] PCI: setting IRQ 5 as level-triggered
May 10 19:59:21 jamie-ubuntu kernel: [   20.241901] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
May 10 19:59:21 jamie-ubuntu kernel: [   20.256985] eth0: VIA Rhine at 0xd9800000, 00:50:ba:a1:9f:88, IRQ 5.
May 10 19:59:21 jamie-ubuntu kernel: [   20.265067] ACPI: PCI Interrupt 0000:00:0c.2[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
May 10 19:59:21 jamie-ubuntu kernel: [   20.265096] ehci_hcd 0000:00:0c.2: EHCI Host Controller
May 10 19:59:21 jamie-ubuntu kernel: [   20.265154] ehci_hcd 0000:00:0c.2: new USB bus registered, assigned bus number 5
May 10 19:59:21 jamie-ubuntu kernel: [   20.265233] ehci_hcd 0000:00:0c.2: irq 5, io mem 0x30000000
May 10 19:59:21 jamie-ubuntu kernel: [   20.276648] ehci_hcd 0000:00:0c.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May 10 19:59:21 jamie-ubuntu kernel: [   20.276842] usb usb5: configuration #1 chosen from 1 choice
May 10 19:59:21 jamie-ubuntu kernel: [   20.276895] hub 5-0:1.0: USB hub found
May 10 19:59:21 jamie-ubuntu kernel: [   20.276907] hub 5-0:1.0: 5 ports detected
May 10 19:59:21 jamie-ubuntu kernel: [   20.315824] usb 1-3: configuration #1 chosen from 1 choice
May 10 19:59:21 jamie-ubuntu kernel: [   20.416760] hda: max request size: 128KiB
May 10 19:59:21 jamie-ubuntu kernel: [   20.416996] hda: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63
May 10 19:59:21 jamie-ubuntu kernel: [   20.418748] hda: cache flushes supported
May 10 19:59:21 jamie-ubuntu kernel: [   20.418813]  hda: hda1
May 10 19:59:21 jamie-ubuntu kernel: [   20.423769] hdb: max request size: 128KiB
May 10 19:59:21 jamie-ubuntu kernel: [   20.424205] hdb: 60058656 sectors (30750 MB) w/2048KiB Cache, CHS=59582/16/63
May 10 19:59:21 jamie-ubuntu kernel: [   20.426201] hdb: cache flushes supported
May 10 19:59:21 jamie-ubuntu kernel: [   20.426278]  hdb: hdb1 hdb2 < hdb5 >
May 10 19:59:21 jamie-ubuntu kernel: [   20.464617] hdc: ATAPI 24X CD-ROM CD-R/RW drive, 1024kB Cache
May 10 19:59:21 jamie-ubuntu kernel: [   20.464633] Uniform CD-ROM driver Revision: 3.20
May 10 19:59:21 jamie-ubuntu kernel: [   20.479655] hdd: ATAPI 52X DVD-ROM drive, 256kB Cache
May 10 19:59:21 jamie-ubuntu kernel: [   20.820556] usb 5-1: new high speed USB device using ehci_hcd and address 2
May 10 19:59:21 jamie-ubuntu kernel: [   20.840737] Attempting manual resume
May 10 19:59:21 jamie-ubuntu kernel: [   20.840745] swsusp: Resume From Partition 3:69
May 10 19:59:21 jamie-ubuntu kernel: [   20.840748] PM: Checking swsusp image.
May 10 19:59:21 jamie-ubuntu kernel: [   20.841087] PM: Resume from disk failed.
May 10 19:59:21 jamie-ubuntu kernel: [   20.864734] EXT3-fs: INFO: recovery required on readonly filesystem.
May 10 19:59:21 jamie-ubuntu kernel: [   20.864743] EXT3-fs: write access will be enabled during recovery.
May 10 19:59:21 jamie-ubuntu kernel: [   20.918262] kjournald starting.  Commit interval 5 seconds
May 10 19:59:21 jamie-ubuntu kernel: [   20.918291] EXT3-fs: recovery complete.
May 10 19:59:21 jamie-ubuntu kernel: [   20.918727] EXT3-fs: mounted filesystem with ordered data mode.
May 10 19:59:21 jamie-ubuntu kernel: [   20.954153] usb 5-1: configuration #1 chosen from 1 choice
May 10 19:59:21 jamie-ubuntu kernel: [   21.192450] usb 5-4: new high speed USB device using ehci_hcd and address 3
May 10 19:59:21 jamie-ubuntu kernel: [   21.333600] usb 5-4: configuration #1 chosen from 1 choice
May 10 19:59:21 jamie-ubuntu kernel: [   21.334341] usbcore: registered new interface driver libusual
May 10 19:59:21 jamie-ubuntu kernel: [   22.066565] Initializing USB Mass Storage driver...
May 10 19:59:21 jamie-ubuntu kernel: [   22.066799] scsi0 : SCSI emulation for USB Mass Storage devices
May 10 19:59:21 jamie-ubuntu kernel: [   22.066902] usb-storage: device found at 2
May 10 19:59:21 jamie-ubuntu kernel: [   22.066906] usb-storage: waiting for device to settle before scanning
May 10 19:59:21 jamie-ubuntu kernel: [   22.066951] scsi1 : SCSI emulation for USB Mass Storage devices
May 10 19:59:21 jamie-ubuntu kernel: [   22.067029] usbcore: registered new interface driver usb-storage
May 10 19:59:21 jamie-ubuntu kernel: [   22.067035] USB Mass Storage support registered.
May 10 19:59:21 jamie-ubuntu kernel: [   22.067274] usb-storage: device found at 2
May 10 19:59:21 jamie-ubuntu kernel: [   22.067277] usb-storage: waiting for device to settle before scanning
May 10 19:59:21 jamie-ubuntu kernel: [   27.075928] usb-storage: device scan complete
May 10 19:59:21 jamie-ubuntu kernel: [   27.076699] scsi 1:0:0:0: Direct-Access     ST380021 A                0811 PQ: 0 ANSI: 0
May 10 19:59:21 jamie-ubuntu kernel: [   27.083271] usb-storage: device scan complete
May 10 19:59:21 jamie-ubuntu kernel: [   27.119412] scsi 0:0:0:0: Direct-Access     Generic  2.0 Reader   -CF 1.00 PQ: 0 ANSI: 0 CCS
May 10 19:59:21 jamie-ubuntu kernel: [   29.396549] Linux agpgart interface v0.102
May 10 19:59:21 jamie-ubuntu kernel: [   29.459004] agpgart: Detected ALi M1647 chipset
May 10 19:59:21 jamie-ubuntu kernel: [   29.570826] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 10 19:59:21 jamie-ubuntu kernel: [   29.575387] agpgart: AGP aperture is 128M @ 0xf0000000
May 10 19:59:21 jamie-ubuntu kernel: [   29.641250] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 10 19:59:21 jamie-ubuntu kernel: [   30.538809] input: Power Button (FF) as /devices/virtual/input/input2
May 10 19:59:21 jamie-ubuntu kernel: [   30.554525] ACPI: Power Button (FF) [PWRF]
May 10 19:59:21 jamie-ubuntu kernel: [   30.554753] input: Power Button (CM) as /devices/virtual/input/input3
May 10 19:59:21 jamie-ubuntu kernel: [   30.566513] ACPI: Power Button (CM) [PWRB]
May 10 19:59:21 jamie-ubuntu kernel: [   30.763025] scsi 0:0:0:1: Direct-Access     Generic  2.0 Reader   -SM 1.00 PQ: 0 ANSI: 0 CCS
May 10 19:59:21 jamie-ubuntu kernel: [   30.798605] scsi 0:0:0:2: Direct-Access     Generic  2.0 Reader   -SD 1.00 PQ: 0 ANSI: 0 CCS
May 10 19:59:21 jamie-ubuntu kernel: [   30.833005] scsi 0:0:0:3: Direct-Access     Generic  2.0 Reader   -MS 1.00 PQ: 0 ANSI: 0 CCS
May 10 19:59:21 jamie-ubuntu kernel: [   30.867002] scsi 0:0:0:4: Direct-Access     Generic  2.0 Reader   -xD 1.00 PQ: 0 ANSI: 0 CCS
May 10 19:59:21 jamie-ubuntu kernel: [   33.221510] nvidia: module license 'NVIDIA' taints kernel.
May 10 19:59:21 jamie-ubuntu kernel: [   33.954677] input: PC Speaker as /devices/platform/pcspkr/input/input4
May 10 19:59:21 jamie-ubuntu kernel: [   34.450845] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
May 10 19:59:21 jamie-ubuntu kernel: [   34.450854] PCI: setting IRQ 6 as level-triggered
May 10 19:59:21 jamie-ubuntu kernel: [   34.450859] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
May 10 19:59:21 jamie-ubuntu kernel: [   34.450889] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
May 10 19:59:21 jamie-ubuntu kernel: [   34.748706] logips2pp: Detected unknown logitech mouse model 127
May 10 19:59:21 jamie-ubuntu kernel: [   35.223057] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
May 10 19:59:21 jamie-ubuntu kernel: [   35.244248] parport_pc 00:09: reported by Plug and Play ACPI
May 10 19:59:21 jamie-ubuntu kernel: [   35.244353] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
May 10 19:59:21 jamie-ubuntu kernel: [   35.382190] Driver 'sd' needs updating - please use bus_type methods
May 10 19:59:21 jamie-ubuntu kernel: [   35.384074] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May 10 19:59:21 jamie-ubuntu kernel: [   35.385443] sd 1:0:0:0: [sda] Test WP failed, assume Write Enabled
May 10 19:59:21 jamie-ubuntu kernel: [   35.385448] sd 1:0:0:0: [sda] Assuming drive cache: write through
May 10 19:59:21 jamie-ubuntu kernel: [   35.386591] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
May 10 19:59:21 jamie-ubuntu kernel: [   35.387830] sd 1:0:0:0: [sda] Test WP failed, assume Write Enabled
May 10 19:59:21 jamie-ubuntu kernel: [   35.387837] sd 1:0:0:0: [sda] Assuming drive cache: write through
May 10 19:59:21 jamie-ubuntu kernel: [   35.387845]  sda: unknown partition table
May 10 19:59:21 jamie-ubuntu kernel: [   35.404887] sd 1:0:0:0: [sda] Attached SCSI disk
May 10 19:59:21 jamie-ubuntu kernel: [   35.414995] sd 0:0:0:0: [sdb] Attached SCSI removable disk
May 10 19:59:21 jamie-ubuntu kernel: [   35.425913] sd 0:0:0:1: [sdc] Attached SCSI removable disk
May 10 19:59:21 jamie-ubuntu kernel: [   35.436912] sd 0:0:0:2: [sdd] Attached SCSI removable disk
May 10 19:59:21 jamie-ubuntu kernel: [   35.447916] sd 0:0:0:3: [sde] Attached SCSI removable disk
May 10 19:59:21 jamie-ubuntu kernel: [   35.458891] sd 0:0:0:4: [sdf] Attached SCSI removable disk
May 10 19:59:21 jamie-ubuntu kernel: [   35.487200] sd 1:0:0:0: Attached scsi generic sg0 type 0
May 10 19:59:21 jamie-ubuntu kernel: [   35.487268] sd 0:0:0:0: Attached scsi generic sg1 type 0
May 10 19:59:21 jamie-ubuntu kernel: [   35.487322] sd 0:0:0:1: Attached scsi generic sg2 type 0
May 10 19:59:21 jamie-ubuntu kernel: [   35.487372] sd 0:0:0:2: Attached scsi generic sg3 type 0
May 10 19:59:21 jamie-ubuntu kernel: [   35.487456] sd 0:0:0:3: Attached scsi generic sg4 type 0
May 10 19:59:21 jamie-ubuntu kernel: [   35.487508] sd 0:0:0:4: Attached scsi generic sg5 type 0
May 10 19:59:21 jamie-ubuntu kernel: [   35.537674] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
May 10 19:59:21 jamie-ubuntu kernel: [   35.538626] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
May 10 19:59:21 jamie-ubuntu kernel: [   40.048455] lp0: using parport0 (interrupt-driven).
May 10 19:59:21 jamie-ubuntu kernel: [   40.089094] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
May 10 19:59:21 jamie-ubuntu kernel: [   40.170438] ndiswrapper: driver net8185 (Realtek,01/29/2007,5.1096.0129.2007) loaded
May 10 19:59:21 jamie-ubuntu kernel: [   40.171456] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 9
May 10 19:59:21 jamie-ubuntu kernel: [   40.171462] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKF] -> GSI 9 (level, low) -> IRQ 9
May 10 19:59:21 jamie-ubuntu kernel: [   40.445607] ndiswrapper: using IRQ 9
May 10 19:59:21 jamie-ubuntu kernel: [   46.784809] wlan0: ethernet device 00:14:d1:3e:dd:b8 using NDIS driver: net8185, version: 0x50448, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
May 10 19:59:21 jamie-ubuntu kernel: [   46.784969] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
May 10 19:59:21 jamie-ubuntu kernel: [   46.788226] usbcore: registered new interface driver ndiswrapper
May 10 19:59:21 jamie-ubuntu kernel: [   46.882006] Adding 1277128k swap on /dev/hdb5.  Priority:-1 extents:1 across:1277128k
May 10 19:59:21 jamie-ubuntu kernel: [   47.475071] EXT3 FS on hdb1, internal journal
May 10 19:59:21 jamie-ubuntu kernel: [   48.891001] ip_tables: (C) 2000-2006 Netfilter Core Team
May 10 19:59:21 jamie-ubuntu kernel: [   49.560100] No dock devices found.
May 10 19:59:21 jamie-ubuntu kernel: [   50.124738] powernow: No powernow capabilities detected
May 10 19:59:21 jamie-ubuntu NetworkManager: <info>  starting... 
May 10 19:59:21 jamie-ubuntu avahi-daemon[5016]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
May 10 19:59:21 jamie-ubuntu avahi-daemon[5016]: Successfully dropped root privileges.
May 10 19:59:21 jamie-ubuntu avahi-daemon[5016]: avahi-daemon 0.6.22 starting up.
May 10 19:59:21 jamie-ubuntu avahi-daemon[5016]: Successfully called chroot().
May 10 19:59:21 jamie-ubuntu avahi-daemon[5016]: Successfully dropped remaining capabilities.
May 10 19:59:21 jamie-ubuntu avahi-daemon[5016]: No service file found in /etc/avahi/services.
May 10 19:59:21 jamie-ubuntu avahi-daemon[5016]: Network interface enumeration completed.
May 10 19:59:21 jamie-ubuntu avahi-daemon[5016]: Registering HINFO record with values 'I686'/'LINUX'.
May 10 19:59:21 jamie-ubuntu avahi-daemon[5016]: Server startup complete. Host name is jamie-ubuntu.local. Local service cookie is 1528625692.
May 10 19:59:21 jamie-ubuntu kernel: [   51.272798] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 10 19:59:21 jamie-ubuntu kernel: [   51.272808] apm: overridden by ACPI.
May 10 19:59:21 jamie-ubuntu kernel: [   51.410999] ppdev: user-space parallel port driver
May 10 19:59:21 jamie-ubuntu kernel: [   51.567312] audit(1210474761.640:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5056 profile="/usr/sbin/cupsd" namespace="default"
May 10 19:59:21 jamie-ubuntu dhcdbd: Started up.
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  Deactivating device wlan0. 
May 10 19:59:23 jamie-ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
May 10 19:59:23 jamie-ubuntu hcid[5301]: Bluetooth HCI daemon
May 10 19:59:23 jamie-ubuntu kernel: [   53.477304] eth0: link down
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  eth0: Device is fully-supported using driver 'via-rhine'. 
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  Deactivating device eth0. 
May 10 19:59:23 jamie-ubuntu NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
May 10 19:59:23 jamie-ubuntu kernel: [   53.521746] Bluetooth: Core ver 2.11
May 10 19:59:23 jamie-ubuntu kernel: [   53.525231] NET: Registered protocol family 31
May 10 19:59:23 jamie-ubuntu kernel: [   53.525240] Bluetooth: HCI device and connection manager initialized
May 10 19:59:23 jamie-ubuntu kernel: [   53.525248] Bluetooth: HCI socket layer initialized
May 10 19:59:23 jamie-ubuntu hcid[5301]: Starting SDP server
May 10 19:59:23 jamie-ubuntu kernel: [   53.593869] Bluetooth: L2CAP ver 2.9
May 10 19:59:23 jamie-ubuntu kernel: [   53.593879] Bluetooth: L2CAP socket layer initialized
May 10 19:59:23 jamie-ubuntu hcid[5301]: Created local server at unix:abstract=/var/run/dbus-hGaWfTLcEF,guid=8ad0eee7ac44c98dd595a9764826610b
May 10 19:59:23 jamie-ubuntu input[5331]: Bluetooth Input daemon
May 10 19:59:23 jamie-ubuntu input[5331]: Registered input manager path:/org/bluez/input
May 10 19:59:23 jamie-ubuntu audio[5336]: Bluetooth Audio daemon
May 10 19:59:23 jamie-ubuntu audio[5336]: Unix socket created: 5
May 10 19:59:23 jamie-ubuntu audio[5336]: audio.conf: Key file does not have key 'Enable'
May 10 19:59:23 jamie-ubuntu audio[5336]: audio.conf: Key file does not have key 'Disable'
May 10 19:59:23 jamie-ubuntu NetworkManager: <debug> [1210474763.779235] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 10 19:59:23 jamie-ubuntu kernel: [   53.758348] Bluetooth: RFCOMM socket layer initialized
May 10 19:59:23 jamie-ubuntu audio[5336]: add_service_record: got record id 0x10000
May 10 19:59:23 jamie-ubuntu audio[5336]: audio.conf: Key file does not have key 'Disable'
May 10 19:59:23 jamie-ubuntu kernel: [   53.758377] Bluetooth: RFCOMM TTY layer initialized
May 10 19:59:23 jamie-ubuntu audio[5336]: audio.conf: Key file does not have group 'A2DP'
May 10 19:59:23 jamie-ubuntu last message repeated 2 times
May 10 19:59:23 jamie-ubuntu kernel: [   53.758380] Bluetooth: RFCOMM ver 1.8
May 10 19:59:23 jamie-ubuntu audio[5336]: audio.conf: Key file does not have group 'A2DP'
May 10 19:59:23 jamie-ubuntu audio[5336]: SEP 0x806d658 registered: type:0 codec:0 seid:1
May 10 19:59:23 jamie-ubuntu audio[5336]: add_service_record: got record id 0x10001
May 10 19:59:23 jamie-ubuntu audio[5336]: add_service_record: got record id 0x10002
May 10 19:59:23 jamie-ubuntu audio[5336]: add_service_record: got record id 0x10003
May 10 19:59:23 jamie-ubuntu audio[5336]: Registered manager path:/org/bluez/audio
May 10 19:59:26 jamie-ubuntu anacron[5429]: Anacron 2.3 started on 2008-05-10
May 10 19:59:26 jamie-ubuntu kernel: [   56.200029] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
May 10 19:59:26 jamie-ubuntu kernel: [   56.200050] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
May 10 19:59:26 jamie-ubuntu kernel: [   56.200088] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
May 10 19:59:26 jamie-ubuntu anacron[5429]: Normal exit (0 jobs run)
May 10 19:59:26 jamie-ubuntu /usr/sbin/cron[5460]: (CRON) INFO (pidfile fd = 3)
May 10 19:59:26 jamie-ubuntu /usr/sbin/cron[5462]: (CRON) STARTUP (fork ok)
May 10 19:59:26 jamie-ubuntu /usr/sbin/cron[5462]: (CRON) INFO (Running @reboot jobs)
May 10 19:59:45 jamie-ubuntu kernel: [   75.898728] NET: Registered protocol family 10
May 10 19:59:45 jamie-ubuntu kernel: [   75.899864] lo: Disabled Privacy Extensions
May 10 19:59:45 jamie-ubuntu kernel: [   75.901146] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 10 19:59:46 jamie-ubuntu pulseaudio[5650]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
May 10 19:59:46 jamie-ubuntu pulseaudio[5650]: alsa-util.c: Cannot find fallback mixer control "PCM".
May 10 19:59:47 jamie-ubuntu avahi-daemon[5016]: Registering new address record for fe80::214:d1ff:fe3e:ddb8 on wlan0.*.
May 10 19:59:50 jamie-ubuntu hcid[5301]: Default passkey agent (:1.25, /org/bluez/passkey) registered
May 10 19:59:50 jamie-ubuntu hcid[5301]: Default authorization agent (:1.25, /org/bluez/auth) registered
May 10 19:59:56 jamie-ubuntu kernel: [   85.923164] wlan0: no IPv6 routers present
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
May 10 19:59:57 jamie-ubuntu ntfs-3g[5792]: Version 1.2216 external FUSE 27 
May 10 19:59:57 jamie-ubuntu ntfs-3g[5792]: Mounted /dev/sda (Read-Write, label "External Storage", NTFS 3.1) 
May 10 19:59:57 jamie-ubuntu ntfs-3g[5792]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_CA.UTF-8 
May 10 19:59:57 jamie-ubuntu ntfs-3g[5792]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,noatime,fsname=/dev/sda,blkdev,blksize=4096 
May 10 19:59:57 jamie-ubuntu hald: mounted /dev/sda on behalf of uid 1000
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
May 10 19:59:57 jamie-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Will activate connection 'wlan0/hamiltons'. 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Device wlan0 activation scheduled... 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) started... 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'hamiltons' is encrypted, but NO valid key exists.  New key needed. 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'hamiltons'. 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'hamiltons' received. 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 10 19:59:57 jamie-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'hamiltons' is encrypted, and a key exists.  No new key needed. 
May 10 19:59:58 jamie-ubuntu NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May 10 19:59:59 jamie-ubuntu NetworkManager: <info>  retry to connect to global supplicant socket (try=2) 
May 10 19:59:59 jamie-ubuntu NetworkManager: <info>  retry to connect to global supplicant socket (try=3) 
May 10 19:59:59 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May 10 19:59:59 jamie-ubuntu kernel: [   89.762946] NET: Registered protocol family 17
May 10 19:59:59 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: response was '0' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 68616d696c746f6e73' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 10 20:00:00 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 10 20:00:03 jamie-ubuntu NetworkManager: <info>  Supplicant state changed: 1 
May 10 20:00:03 jamie-ubuntu NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'hamiltons'. 
May 10 20:00:03 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 10 20:00:03 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
May 10 20:00:04 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
May 10 20:00:04 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
May 10 20:00:04 jamie-ubuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
May 10 20:00:04 jamie-ubuntu NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May 10 20:00:05 jamie-ubuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
May 10 20:00:07 jamie-ubuntu dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
May 10 20:00:07 jamie-ubuntu dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May 10 20:00:07 jamie-ubuntu avahi-daemon[5016]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
May 10 20:00:07 jamie-ubuntu avahi-daemon[5016]: New relevant interface wlan0.IPv4 for mDNS.
May 10 20:00:07 jamie-ubuntu avahi-daemon[5016]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
May 10 20:00:07 jamie-ubuntu NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface wlan0 
May 10 20:00:07 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
May 10 20:00:07 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
May 10 20:00:07 jamie-ubuntu dhclient: bound to 192.168.1.101 -- renewal in 41410 seconds.
May 10 20:00:08 jamie-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
May 10 20:00:08 jamie-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>    address 192.168.1.101 
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>    netmask 255.255.255.0 
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>    broadcast 192.168.1.255 
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>    gateway 192.168.1.1 
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>    nameserver 75.154.133.68 
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>    nameserver 75.154.133.100 
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>    hostname 'jamie-ubuntu' 
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>    domain name 'bc.hsia.telus.net' 
May 10 20:00:08 jamie-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
May 10 20:00:08 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
May 10 20:00:08 jamie-ubuntu avahi-daemon[5016]: Withdrawing address record for 192.168.1.101 on wlan0.
May 10 20:00:08 jamie-ubuntu avahi-daemon[5016]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
May 10 20:00:08 jamie-ubuntu avahi-daemon[5016]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 10 20:00:08 jamie-ubuntu avahi-daemon[5016]: Withdrawing address record for fe80::214:d1ff:fe3e:ddb8 on wlan0.
May 10 20:00:08 jamie-ubuntu avahi-daemon[5016]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
May 10 20:00:08 jamie-ubuntu avahi-daemon[5016]: New relevant interface wlan0.IPv4 for mDNS.
May 10 20:00:08 jamie-ubuntu avahi-daemon[5016]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
May 10 20:00:09 jamie-ubuntu NetworkManager: <info>  Clearing nscd hosts cache. 
May 10 20:00:09 jamie-ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May 10 20:00:09 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) successful, device activated. 
May 10 20:00:09 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
May 10 20:00:09 jamie-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
May 10 20:00:10 jamie-ubuntu ntpdate[5896]: step time server 91.189.94.4 offset -0.693230 sec
May 10 20:00:10 jamie-ubuntu avahi-daemon[5016]: Registering new address record for fe80::214:d1ff:fe3e:ddb8 on wlan0.*.
May 10 20:00:19 jamie-ubuntu kernel: [  109.822241] wlan0: no IPv6 routers present
```

---

### Post by Canis familiaris on 2008-05-11
> May 10 16:51:08 jamie-ubuntu kernel: [   49.890246] EXT3-fs: hdb1: orphan cleanup on readonly fs
May 10 16:51:08 jamie-ubuntu kernel: [   49.890261] ext3_orphan_cleanup: deleting unreferenced inode 213078
May 10 16:51:08 jamie-ubuntu kernel: [   49.890316] ext3_orphan_cleanup: deleting unreferenced inode 213079
May 10 16:51:08 jamie-ubuntu kernel: [   49.890328] ext3_orphan_cleanup: deleting unreferenced inode 213080
May 10 16:51:08 jamie-ubuntu kernel: [   49.890339] ext3_orphan_cleanup: deleting unreferenced inode 213077
May 10 16:51:08 jamie-ubuntu kernel: [   49.890352] ext3_orphan_cleanup: deleting unreferenced inode 410429
May 10 16:51:08 jamie-ubuntu kernel: [   49.890394] ext3_orphan_cleanup: deleting unreferenced inode 409882
May 10 16:51:08 jamie-ubuntu kernel: [   49.890459] ext3_orphan_cleanup: deleting unreferenced inode 213063
May 10 16:51:08 jamie-ubuntu kernel: [   49.890471] ext3_orphan_cleanup: deleting unreferenced inode 213054
May 10 16:51:08 jamie-ubuntu kernel: [   49.890485] ext3_orphan_cleanup: deleting unreferenced inode 1131173
May 10 16:51:08 jamie-ubuntu kernel: [   49.922268] ext3_orphan_cleanup: deleting unreferenced inode 1132314
May 10 16:51:08 jamie-ubuntu kernel: [   49.939613] ext3_orphan_cleanup: deleting unreferenced inode 1155479
May 10 16:51:08 jamie-ubuntu kernel: [   49.953243] ext3_orphan_cleanup: deleting unreferenced inode 1155478
May 10 16:51:08 jamie-ubuntu kernel: [   49.959599] ext3_orphan_cleanup: deleting unreferenced inode 1155477
May 10 16:51:08 jamie-ubuntu kernel: [   49.959617] ext3_orphan_cleanup: deleting unreferenced inode 688146
May 10 16:51:08 jamie-ubuntu kernel: [   49.975139] ext3_orphan_cleanup: deleting unreferenced inode 688133
May 10 16:51:08 jamie-ubuntu kernel: [   49.981188] ext3_orphan_cleanup: deleting unreferenced inode 1132310
May 10 16:51:08 jamie-ubuntu kernel: [   50.008687] ext3_orphan_cleanup: deleting unreferenced inode 647224
May 10 16:51:08 jamie-ubuntu kernel: [   50.016984] ext3_orphan_cleanup: deleting unreferenced inode 647205
May 10 16:51:08 jamie-ubuntu kernel: [   50.027181] ext3_orphan_cleanup: deleting unreferenced inode 532485
May 10 16:51:08 jamie-ubuntu kernel: [   50.035393] ext3_orphan_cleanup: deleting unreferenced inode 532484
May 10 16:51:08 jamie-ubuntu kernel: [   50.035411] ext3_orphan_cleanup: deleting unreferenced inode 532482
May 10 16:51:08 jamie-ubuntu kernel: [   50.042007] ext3_orphan_cleanup: deleting unreferenced inode 1130911
May 10 16:51:08 jamie-ubuntu kernel: [   50.058005] ext3_orphan_cleanup: deleting unreferenced inode 1132412
May 10 16:51:08 jamie-ubuntu kernel: [   50.058025] ext3_orphan_cleanup: deleting unreferenced inode 1132171
May 10 16:51:08 jamie-ubuntu kernel: [   50.067261] ext3_orphan_cleanup: deleting unreferenced inode 1163938
May 10 16:51:08 jamie-ubuntu kernel: [   50.081572] ext3_orphan_cleanup: deleting unreferenced inode 1163934
May 10 16:51:08 jamie-ubuntu kernel: [   50.081592] ext3_orphan_cleanup: deleting unreferenced inode 1132459
May 10 16:51:08 jamie-ubuntu kernel: [   50.087479] ext3_orphan_cleanup: deleting unreferenced inode 1132161
May 10 16:51:08 jamie-ubuntu kernel: [   50.092611] ext3_orphan_cleanup: deleting unreferenced inode 1132316
May 10 16:51:08 jamie-ubuntu kernel: [   50.098544] ext3_orphan_cleanup: deleting unreferenced inode 1132035
May 10 16:51:08 jamie-ubuntu kernel: [   50.108126] ext3_orphan_cleanup: deleting unreferenced inode 1132273
May 10 16:51:08 jamie-ubuntu kernel: [   50.117231] ext3_orphan_cleanup: deleting unreferenced inode 1132109
May 10 16:51:08 jamie-ubuntu kernel: [   50.125654] ext3_orphan_cleanup: deleting unreferenced inode 1132107
May 10 16:51:08 jamie-ubuntu kernel: [   50.140748] ext3_orphan_cleanup: deleting unreferenced inode 1155591
May 10 16:51:08 jamie-ubuntu kernel: [   50.149012] ext3_orphan_cleanup: deleting unreferenced inode 1155584
May 10 16:51:08 jamie-ubuntu kernel: [   50.149031] ext3_orphan_cleanup: deleting unreferenced inode 1155582
May 10 16:51:08 jamie-ubuntu kernel: [   50.156824] ext3_orphan_cleanup: deleting unreferenced inode 1147702
May 10 16:51:08 jamie-ubuntu kernel: [   50.172067] ext3_orphan_cleanup: deleting unreferenced inode 1147745
May 10 16:51:08 jamie-ubuntu kernel: [   50.172233] ext3_orphan_cleanup: deleting unreferenced inode 1147731
May 10 16:51:08 jamie-ubuntu kernel: [   50.180959] ext3_orphan_cleanup: deleting unreferenced inode 1147729
May 10 16:51:08 jamie-ubuntu kernel: [   50.184927] ext3_orphan_cleanup: deleting unreferenced inode 1147725
May 10 16:51:08 jamie-ubuntu kernel: [   50.191788] ext3_orphan_cleanup: deleting unreferenced inode 1147723
May 10 16:51:08 jamie-ubuntu kernel: [   50.199911] ext3_orphan_cleanup: deleting unreferenced inode 1147717
May 10 16:51:08 jamie-ubuntu kernel: [   50.207489] ext3_orphan_cleanup: deleting unreferenced inode 1132027
May 10 16:51:08 jamie-ubuntu kernel: [   50.213979] ext3_orphan_cleanup: deleting unreferenced inode 1132025
May 10 16:51:08 jamie-ubuntu kernel: [   50.219162] ext3_orphan_cleanup: deleting unreferenced inode 1131943
May 10 16:51:08 jamie-ubuntu kernel: [   50.225349] ext3_orphan_cleanup: deleting unreferenced inode 1131941
May 10 16:51:08 jamie-ubuntu kernel: [   50.234727] ext3_orphan_cleanup: deleting unreferenced inode 1132033
May 10 16:51:08 jamie-ubuntu kernel: [   50.239129] ext3_orphan_cleanup: deleting unreferenced inode 1132373
May 10 16:51:08 jamie-ubuntu kernel: [   50.247893] ext3_orphan_cleanup: deleting unreferenced inode 1132368
May 10 16:51:08 jamie-ubuntu kernel: [   50.257315] ext3_orphan_cleanup: deleting unreferenced inode 1114157
May 10 16:51:08 jamie-ubuntu kernel: [   50.265620] ext3_orphan_cleanup: deleting unreferenced inode 213004
This surely indicates that something is wrong with your hard disk which has been set as primary slave(hdb).
Try this:
Run Ubuntu in recovery mode:
In the terminal mode:
First Unmount all partitions in that Hard Disk.
```
sudo umount /dev/hdbX
```
Replace X by 1,2,3,4,... or whatever is the disk device
Then check the filesystem:
```
sudo fsck /dev/hdbX
```
Again Replace X by 1,2,3,4,... or whatever is the disk device

---

### Post by jamieh on 2008-05-12
> **Anurag_panda said:**
> Replace X by 1,2,3,4,... or whatever is the disk device

The 30GB drive only has one partitiom, so would I just use "1"?
Thanks

---

### Post by fno on 2008-05-12
That is correct, as in:

sudo fsck /dev/hdb1

---

