---
title: "/dev/scd0 not found"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by tsWAN on 2008-07-19
I've been using Ubuntu for a couple of months. Not until a recent update have I had any issues with mounting my DVD drive. I tried to find the solution through numerous google searches, but was just baffled by all of the tech talk. So I just need a nice detailed walk through of how to fix this :)

Thank you.

---

### Post by bhadotia on 2008-07-19
Please be a little more descriptive . 
Tell us: what you are trying to do, exactly what errors do you come across , post terminal outputs, what updates you are talking about , etc.

---

### Post by bumanie on 2008-07-19
Post the output of > cat /etc/fstab

---

### Post by tsWAN on 2008-07-19
I'm not sure of which update, but it was within the last month.
when i try to mount my drive it returns with an error reading:
mount: special device /dev/scd0/ does not exist.

and
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d90bd2d7-b8b6-447c-a5ac-9af827c1fe1f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=97d08f3a-e708-48c0-a499-c4037a65de4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by sisco311 on 2008-07-19
post:
```
lshw -C disk
```

---

### Post by tsWAN on 2008-07-19
```
*-disk                  
       description: ATA Disk
       product: ST94813AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 7.24
       serial: 5PJ1J21G
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=4d384d37
```

---

### Post by sisco311 on 2008-07-19
EDIT: 
First try to run the command as root and post the output:
```
sudo lshw -C disk
```

Is the device recognized in bios?
If not, then check the power and the data cable.

---

### Post by philinux on 2008-07-19
I've just re-installed last week and I've not tweaked anything.

This is the systems entry in my fstab for the DVD writer.

```
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0
```

---

### Post by tsWAN on 2008-07-19
sisco:
the first time I ran that command was in root, because it wouldn't run in normal terminal. 
and I am not tech savvy in the least, so I don't know where to find bios.

---

### Post by philinux on 2008-07-19
Just to test the dvd player, put the livecd in and see if it boots.

---

### Post by tsWAN on 2008-07-19
Sounds like the drive reads the disk, but nothing on the interface end.

---

### Post by philinux on 2008-07-19
> **tsWAN said:**
> Sounds like the drive reads the disk, but nothing on the interface end.

What does "but nothing on the interface end" mean.

Do you get to see the livecd menu. I assume you used one to install?

---

### Post by tsWAN on 2008-07-19
As in nothing happens.
Nothing shows up on the screen.
The drive isn't mounted.
I cannot access the files on the disk.

And yes, I used the same disk as I had used to install ubuntu, as that is what I assumed you meant by livecd.

---

### Post by philinux on 2008-07-19
> **tsWAN said:**
> As in nothing happens.
Nothing shows up on the screen.
The drive isn't mounted.
I cannot access the files on the disk.

And yes, I used the same disk as I had used to install ubuntu, as that is what I assumed you meant by livecd.


Ok I think a misunderstanding.

I was asking you to put the livecd in the drive and reboot the pc.
If the drive is working it will boot up the livecd.

---

### Post by tsWAN on 2008-07-19
Did not boot from livecd.
So am i to assume this is a hardware issue then?

---

### Post by philinux on 2008-07-19
> **tsWAN said:**
> Did not boot from livecd.
So am i to assume this is a hardware issue then?

Ok, well I guess it did boot when you installed Ubuntu and you haven't changed the bios settings since then?

To check the bios you have to be quick when you boot the pc.

On mine I have to press the Del key. I know this because the Asus motherboard splash screen says so. Yours might be the esc key or F1. Google your motherboard if you're not sure.

Once in the bios you use the cursor keys to navigate. Find the boot order.
Mine is set to cdrom first then hard drive.

---

### Post by tsWAN on 2008-07-19
drive is recognized in bios
tried rearranging boot order but livecd still didn't load

---

### Post by sisco311 on 2008-07-19
post:
```
dmesg
```

---

### Post by tsWAN on 2008-07-19
```
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127635
[    0.000000] Kernel command line: root=UUID=d90bd2d7-b8b6-447c-a5ac-9af827c1fe1f ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1463.084 MHz processor.
[    8.302989] Console: colour VGA+ 80x25
[    8.302993] console [tty0] enabled
[    8.303152] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.303367] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.314491] Memory: 497668k/514560k available (2177k kernel code, 16304k reserved, 1006k data, 368k init, 0k highmem)
[    8.314501] virtual kernel memory layout:
[    8.314502]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.314504]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.314505]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    8.314507]     lowmem  : 0xc0000000 - 0xdf680000   ( 502 MB)
[    8.314508]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.314510]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[    8.314511]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[    8.314515] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.314556] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.314723] hpet clockevent registered
[    8.394624] Calibrating delay using timer specific routine.. 2929.55 BogoMIPS (lpj=5859119)
[    8.394649] Security Framework initialized
[    8.394657] SELinux:  Disabled at boot.
[    8.394673] AppArmor: AppArmor initialized
[    8.394678] Failure registering capabilities with primary security module.
[    8.394688] Mount-cache hash table entries: 512
[    8.394818] Initializing cgroup subsys ns
[    8.394823] Initializing cgroup subsys cpuacct
[    8.394834] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000 00000000
[    8.394843] monitor/mwait feature present.
[    8.394846] using mwait in idle threads.
[    8.394850] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.394853] CPU: L2 cache: 1024K
[    8.394857] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000 00000000
[    8.394867] Compat vDSO mapped to ffffe000.
[    8.394882] Checking 'hlt' instruction... OK.
[    8.411085] SMP alternatives: switching to UP code
[    8.413161] Freeing SMP alternatives: 11k freed
[    8.413286] Early unpacking initramfs... done
[    8.849472] ACPI: Core revision 20070126
[    8.849551] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.882783] CPU0: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
[    8.882811] Total of 1 processors activated (2929.55 BogoMIPS).
[    8.883008] ENABLING IO-APIC IRQs
[    8.883207] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.029823] Brought up 1 CPUs
[    9.029849] CPU0 attaching sched-domain:
[    9.029852]  domain 0: span 01
[    9.029854]   groups: 01
[    9.030041] net_namespace: 64 bytes
[    9.030053] Booting paravirtualized kernel on bare hardware
[    9.030587] Time: 12:44:36  Date: 07/19/08
[    9.030616] NET: Registered protocol family 16
[    9.030840] EISA bus registered
[    9.030846] ACPI: bus type pci registered
[    9.031073] PCI: PCI BIOS revision 2.10 entry at 0xfd873, last bus=8
[    9.031076] PCI: Using configuration type 1
[    9.031092] Setting up standard PCI resources
[    9.033656] ACPI: EC: Look up EC in DSDT
[    9.035727] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    9.036195] ACPI: Interpreter enabled
[    9.036199] ACPI: (supports S0 S3 S4 S5)
[    9.036215] ACPI: Using IOAPIC for interrupt routing
[    9.039766] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.078925] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    9.078928] ACPI: EC: driver started in interrupt mode
[    9.078975] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.079836] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.079841] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    9.080838] PCI: Transparent bridge - 0000:00:1e.0
[    9.080886] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.081238] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.081378] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.081517] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    9.081669] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.085061] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.085167] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    9.085270] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    9.085372] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    9.085474] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 *6 7 10 12 14 15)
[    9.085576] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    9.085679] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    9.085788] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    9.085932] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.085969] pnp: PnP ACPI init
[    9.085977] ACPI: bus type pnp registered
[    9.106338] pnp: PnP ACPI: found 10 devices
[    9.106341] ACPI: ACPI bus type pnp unregistered
[    9.106345] PnPBIOS: Disabled by ACPI PNP
[    9.106595] PCI: Using ACPI for IRQ routing
[    9.106599] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.106604] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[    9.106606] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[    9.106609] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[    9.106612] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[    9.106615] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[    9.106617] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[    9.106658] PCI: Cannot allocate resource region 0 of device 0000:06:00.0
[    9.141633] NET: Registered protocol family 8
[    9.141636] NET: Registered protocol family 20
[    9.141678] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.141683] hpet0: 3 64-bit timers, 14318180 Hz
[    9.142727] AppArmor: AppArmor Filesystem Enabled
[    9.145619] Time: tsc clocksource has been installed.
[    9.145637] Switched to high resolution mode on CPU 0
[    9.153614] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    9.153618] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    9.153622] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    9.153626] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    9.153630] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    9.153633] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    9.153637] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[    9.153641] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    9.153649] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    9.153656] system 00:06: ioport range 0x800-0x80f has been reserved
[    9.153660] system 00:06: ioport range 0x1000-0x107f has been reserved
[    9.153663] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    9.153666] system 00:06: ioport range 0x1640-0x164f has been reserved
[    9.184132] PCI: Bridge: 0000:00:1c.0
[    9.184135]   IO window: disabled.
[    9.184140]   MEM window: disabled.
[    9.184145]   PREFETCH window: disabled.
[    9.184151] PCI: Bridge: 0000:00:1c.1
[    9.184153]   IO window: disabled.
[    9.184159]   MEM window: disabled.
[    9.184163]   PREFETCH window: disabled.
[    9.184183] PCI: Bridge: 0000:00:1c.2
[    9.184185]   IO window: disabled.
[    9.184191]   MEM window: 30000000-300fffff
[    9.184196]   PREFETCH window: disabled.
[    9.184202] PCI: Bridge: 0000:00:1e.0
[    9.184206]   IO window: 2000-2fff
[    9.184212]   MEM window: d0100000-d01fffff
[    9.184217]   PREFETCH window: disabled.
[    9.184253] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    9.184262] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.184288] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    9.184296] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.184321] PCI: Enabling device 0000:00:1c.2 (0100 -> 0102)
[    9.184326] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    9.184334] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.184349] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.184367] NET: Registered protocol family 2
[    9.221552] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    9.221775] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    9.221887] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    9.222000] TCP: Hash tables configured (established 16384 bind 16384)
[    9.222003] TCP reno registered
[    9.233601] checking if image is initramfs... it is
[   10.089279] Freeing initrd memory: 7731k freed
[   10.089471] Simple Boot Flag at 0x36 set to 0x1
[   10.090055] audit: initializing netlink socket (disabled)
[   10.090071] audit(1216471476.640:1): initialized
[   10.092421] VFS: Disk quotas dquot_6.5.1
[   10.092506] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.092660] io scheduler noop registered
[   10.092663] io scheduler anticipatory registered
[   10.092665] io scheduler deadline registered
[   10.092679] io scheduler cfq registered (default)
[   10.092692] Boot video device is 0000:00:02.0
[   18.081707] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   18.081830] PCI: Firmware left 0000:08:08.0 e100 interrupts enabled, disabling
[   18.081960] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.082021] assign_interrupt_mode Found MSI capability
[   18.082073] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.082115] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.082224] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.082284] assign_interrupt_mode Found MSI capability
[   18.082331] Allocate Port Service[0000:00:1c.1:pcie00]
[   18.082369] Allocate Port Service[0000:00:1c.1:pcie02]
[   18.082476] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   18.082536] assign_interrupt_mode Found MSI capability
[   18.082583] Allocate Port Service[0000:00:1c.2:pcie00]
[   18.082623] Allocate Port Service[0000:00:1c.2:pcie02]
[   18.082903] isapnp: Scanning for PnP cards...
[   18.436914] isapnp: No Plug & Play device found
[   18.470404] Real Time Clock Driver v1.12ac
[   18.470649] hpet_resources: 0xfed00000 is busy
[   18.470677] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.472087] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.472175] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.472288] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.490643] i8042.c: Detected active multiplexing controller, rev 1.1.
[   18.506625] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.506630] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.506633] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.506636] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.506639] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.517212] mice: PS/2 mouse device common for all mice
[   18.517342] EISA: Probing bus 0 at eisa.0
[   18.517351] Cannot allocate resource for EISA slot 1
[   18.517354] Cannot allocate resource for EISA slot 2
[   18.517382] EISA: Detected 0 cards.
[   18.517385] cpuidle: using governor ladder
[   18.517389] cpuidle: using governor menu
[   18.517491] NET: Registered protocol family 1
[   18.517522] Using IPI No-Shortcut mode
[   18.517559] registered taskstats version 1
[   18.517667]   Magic number: 0:390:734
[   18.517794] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.517797] EDD information not available.
[   18.517975] Freeing unused kernel memory: 368k freed
[   18.537125] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.774905] fuse init (API version 7.9)
[   19.803319] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.803327] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.803345] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.809153] ACPI: Thermal Zone [TZ01] (72 C)
[   19.809291] ACPI: Thermal Zone [TZ02] (27 C)
[   20.614497] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   20.614517] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   20.637823] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   20.637849] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   20.637873] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   20.637892] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   20.674396] ssb: Sonics Silicon Backplane found on PCI device 0000:06:00.0
[   20.702837] usbcore: registered new interface driver usbfs
[   20.702865] usbcore: registered new interface driver hub
[   20.718546] usbcore: registered new device driver usb
[   20.729772] USB Universal Host Controller Interface driver v3.0
[   20.729846] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   20.729858] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.729863] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.730138] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   20.730208] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   20.730370] usb usb1: configuration #1 chosen from 1 choice
[   20.730398] hub 1-0:1.0: USB hub found
[   20.730404] hub 1-0:1.0: 2 ports detected
[   20.804882] SCSI subsystem initialized
[   20.834173] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   20.834188] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.834193] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.834219] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   20.834256] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   20.834392] usb usb2: configuration #1 chosen from 1 choice
[   20.834418] hub 2-0:1.0: USB hub found
[   20.834425] hub 2-0:1.0: 2 ports detected
[   20.900677] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   20.900682] e100: Copyright(c) 1999-2006 Intel Corporation
[   20.906931] libata version 3.00 loaded.
[   20.938017] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.938032] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.938038] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.938074] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   20.938110] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   20.938234] usb usb3: configuration #1 chosen from 1 choice
[   20.938262] hub 3-0:1.0: USB hub found
[   20.938268] hub 3-0:1.0: 2 ports detected
[   21.041910] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   21.041925] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   21.041931] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   21.041957] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   21.041994] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   21.042123] usb usb4: configuration #1 chosen from 1 choice
[   21.042150] hub 4-0:1.0: USB hub found
[   21.042156] hub 4-0:1.0: 2 ports detected
[   21.145881] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   21.145900] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   21.145905] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.145941] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   21.149863] ehci_hcd 0000:00:1d.7: debug port 1
[   21.149871] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   21.149879] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd0544000
[   21.177629] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   21.189588] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.189740] usb usb5: configuration #1 chosen from 1 choice
[   21.189768] hub 5-0:1.0: USB hub found
[   21.189775] hub 5-0:1.0: 8 ports detected
[   21.293775] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   21.321396] e100: eth0: e100_probe: addr 0xd0100000, irq 21, MAC addr 00:16:d4:3e:0c:5a
[   21.321416] ahci 0000:00:1f.2: version 3.0
[   21.321442] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   21.321493] ahci 0000:00:1f.2: nr_ports (4) and implemented port map (0x5) don't match, using nr_ports
[   21.321497] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0xf
[   21.720874] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   21.861537] usb 2-2: configuration #1 chosen from 1 choice
[   21.882174] usbcore: registered new interface driver hiddev
[   21.889062] input:     Rocketfish Wireless Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input2
[   21.904678] input,hidraw0: USB HID v1.10 Mouse [    Rocketfish Wireless Mouse] on usb-0000:00:1d.1-2
[   21.904697] usbcore: registered new interface driver usbhid
[   21.904701] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   21.932586] Clocksource tsc unstable (delta = -834008161 ns)
[   21.939846] Time: hpet clocksource has been installed.
[   22.003923] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[   22.003929] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   22.003936] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   22.004220] scsi0 : ahci
[   22.004492] scsi1 : ahci
[   22.004648] scsi2 : ahci
[   22.004803] scsi3 : ahci
[   22.004904] ata1: SATA max UDMA/133 abar m1024@0xd0544400 port 0xd0544500 irq 220
[   22.004909] ata2: SATA max UDMA/133 abar m1024@0xd0544400 port 0xd0544580 irq 220
[   22.004913] ata3: SATA max UDMA/133 abar m1024@0xd0544400 port 0xd0544600 irq 220
[   22.004917] ata4: SATA max UDMA/133 abar m1024@0xd0544400 port 0xd0544680 irq 220
[   22.101376] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.102643] ata1.00: ATA-7: ST94813AS, 7.24, max UDMA/100
[   22.102647] ata1.00: 78165360 sectors, multi 16: LBA48 
[   22.104167] ata1.00: configured for UDMA/100
[   22.146621] ata2: SATA link down (SStatus 0 SControl 0)
[   22.190631] ata3: SATA link down (SStatus 0 SControl 300)
[   22.234206] ata4: SATA link down (SStatus 0 SControl 0)
[   22.234343] scsi 0:0:0:0: Direct-Access     ATA      ST94813AS        7.24 PQ: 0 ANSI: 5
[   22.236822] ata_piix 0000:00:1f.1: version 2.12
[   22.236844] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 20
[   22.236882] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.237611] scsi4 : ata_piix
[   22.237973] scsi5 : ata_piix
[   22.238509] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   22.238513] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   22.245897] Driver 'sd' needs updating - please use bus_type methods
[   22.247586] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   22.247603] sd 0:0:0:0: [sda] Write Protect is off
[   22.247606] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.247625] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.247684] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   22.247696] sd 0:0:0:0: [sda] Write Protect is off
[   22.247699] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.247717] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.247721]  sda: sda1 sda2 < sda5 >
[   22.283298] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.289163] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.403429] ata6: port disabled. ignoring.
[   22.564193] Attempting manual resume
[   22.564197] swsusp: Resume From Partition 8:5
[   22.564199] PM: Checking swsusp image.
[   22.564371] PM: Resume from disk failed.
[   22.599751] kjournald starting.  Commit interval 5 seconds
[   22.599766] EXT3-fs: mounted filesystem with ordered data mode.
[   36.854659] Linux agpgart interface v0.102
[   37.021827] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.089761] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.270071] agpgart: Detected an Intel 945GM Chipset.
[   37.270424] agpgart: Detected 7932K stolen memory.
[   37.289595] agpgart: AGP aperture is 256M @ 0xc0000000
[   37.411213] intel_rng: FWH not detected
[   37.754751] input: Power Button (FF) as /devices/virtual/input/input3
[   37.764759] ACPI: Power Button (FF) [PWRF]
[   37.764801] ACPI Error (evxfevnt-0186): Could not enable SleepButton event [20070126]
[   37.764807] ACPI Warning (evxface-0145): Could not enable fixed event 3 [20070126]
[   37.764889] input: Lid Switch as /devices/virtual/input/input4
[   37.764962] ACPI: Lid Switch [LID]
[   37.765016] input: Power Button (CM) as /devices/virtual/input/input5
[   37.780713] ACPI: Power Button (CM) [PWRB]
[   37.887119] iTCO_vendor_support: vendor-support=0
[   37.936529] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   37.936638] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   37.936680] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   38.008520] ACPI: WMI-Acer: Mapper loaded
[   38.593597] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   39.460194] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   39.470386] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   39.470640] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   39.486359] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   39.546374] ACPI: AC Adapter [ACAD] (on-line)
[   40.077652] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   40.077687] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   40.302716] ACPI: Battery Slot [BAT1] (battery present)
[   41.212085] b43-phy0: Broadcom 4311 WLAN found
[   41.255894] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
[   41.255925] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   41.314429] phy0: Selected rate control algorithm 'simple'
[   41.949279] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   42.013656] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   43.331036] udev: renamed network interface wlan0 to eth1
[   43.732258] lp: driver loaded but no devices found
[   43.952600] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k
[   44.296639] EXT3 FS on sda1, internal journal
[   44.466219] device-mapper: uevent: version 1.0.3
[   44.466254] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   45.491603] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.140896] No dock devices found.
[   47.480900] ppdev: user-space parallel port driver
[   47.781122] audit(1216471517.985:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5018 profile="/usr/sbin/cupsd" namespace="default"
[   47.848686] apm: BIOS not found.
[   49.385163] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   49.461214] input: b43-phy0 as /devices/virtual/input/input10
[   49.580809] Bluetooth: Core ver 2.11
[   49.592839] NET: Registered protocol family 31
[   49.592844] Bluetooth: HCI device and connection manager initialized
[   49.592848] Bluetooth: HCI socket layer initialized
[   49.644156] Bluetooth: L2CAP ver 2.9
[   49.644162] Bluetooth: L2CAP socket layer initialized
[   49.817177] Bluetooth: RFCOMM socket layer initialized
[   49.817192] Bluetooth: RFCOMM TTY layer initialized
[   49.817195] Bluetooth: RFCOMM ver 1.8
[   49.882632] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   51.091463] b43-phy0 debug: Chip initialized
[   51.091968] b43-phy0 debug: 32-bit DMA initialized
[   51.112682] Registered led device: b43-phy0:tx
[   51.112913] Registered led device: b43-phy0:rx
[   51.113068] Registered led device: b43-phy0:radio
[   51.113154] b43-phy0 debug: Wireless interface started
[   51.151027] b43-phy0 debug: Adding Interface type 2
[   53.712705] [drm] Initialized drm 1.1.0 20060810
[   53.775975] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   53.775986] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   53.776074] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   54.829761] NET: Registered protocol family 17
[   55.486310] NET: Registered protocol family 10
[   55.486796] lo: Disabled Privacy Extensions
[   55.487927] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   65.553681] eth0: no IPv6 routers present
[   79.342733] b43-phy0 debug: Removing Interface type 2
[   79.398812] b43-phy0 debug: Wireless interface stopped
[   79.398936] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 1/64
[   79.398994] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[   79.406634] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[   79.414597] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[   79.422580] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[   79.430569] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 2/128
[   79.438569] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128

```

---

### Post by chrisccoulson on 2008-07-19
According to your dmesg output, no CD drive is being detected. If you can't boot from the live CD using this drive, then it is likely to be hardware related.

Have you made sure all the cables are firmly connected inside your box?

---

### Post by tsWAN on 2008-07-19
I have a laptop, and no I have yet to open it up.

---

### Post by jjongsma on 2009-08-15
I have the exact same issue after upgrading to Jaunty, on a Dell Vostro 1710.  Not a hardware issue - Ubuntu lost it after the upgrade.  Any other ideas?

---

