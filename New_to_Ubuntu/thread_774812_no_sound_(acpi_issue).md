---
title: "no sound (acpi issue)"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by jakelute on 2008-04-29
Hello,

I'm experiencing a problem with sound which is outlined in the thread below (sorry it's so long!)

[http://ubuntuforums.org/showthread.php?t=688813](http://ubuntuforums.org/showthread.php?t=688813)

The problem is this: I've had endless trouble (not just in 8.04, but also in the previous two versions of Ubuntu) with temporary freeze-ups of my system. With the help of a very generous member of the community (thank you Unutbu), I have now worked out that when I add acpi=off or acpi=ht to /boot/grub/menu.lst, the freezing problem disappears. 

This is wonderful, after so many weeks of trying to figure it out. (I've been trying to solve this since the beginning of February!)

But.....it's not all good news, because I lose my sound when I gain a system which doesn't freeze. There's no sound at all when acpi=off or when acpi=ht.

It's great to be able to work on my computer without freezing up all the time, and I love Ubuntu and hope to stay with it, but can anyone possibly give me some assistance with getting my sound back? Just to repeat, the only way I've found to have a system which doesn't freeze is to use acpi=off or acpi=ht, and both of these cause my sound to disappear. (And I've tried a lot of things!)

If you read the thread referenced above, you'll see the various vital statistics about my system.

Many thanks in advance for any help!

Best wishes.

---

### Post by unutbu on 2008-04-30
As I understand it, you've reinstalled 8.04 and now, while running with kernel option acpi=off you do hear the "drum beat" sound at the gdm login window, but it just never quits. (LOL, sorry.) 

Well, while this is no fix of your overall sound problem, at least you can shut off the drum beat by doing the following:

```
gksudo gedit /etc/gdm/gdm.conf
```

Search for "SoundOnLogin=true" and change that  line to 

```
SoundOnLogin=false
```

Make sure there is no pound sign (#) in front of that line either.

---

### Post by jakelute on 2008-05-01
Thanks for this. One tiny correction to what you say:

"As I understand it, you've reinstalled 8.04 and now, while running with kernel option acpi=off you do hear the "drum beat" sound at the gdm login window, but it just never quits."

I'm actually now running with kernel option "acpi=off pci=noacpi" (all typed onto one line -- is this correct?)

I'm going to study the sound troubleshooting pages now to see if any of that is useful to me in my predicament!

Since the reinstall, by the way, I can't shut down my computer anymore, or restart it, except with the normal generic kernel options (where I get freezes). In the other modes ("acpi=off pci=noacpi", and also in "acpi=ht"), I'm unable to shut down, despite having put in the apm tweaks that you suggested some time ago.

---

### Post by jakelute on 2008-05-01
Update: I've been looking at the sound troubleshooting guide, and running into some questions. I don't really understand what I'm doing, but I'm following the steps outlined there.

"aplay -l" gives this:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

"lspci -v" gives this:

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
	Memory at <ignored> (64-bit, non-prefetchable)
	Capabilities: <access denied>

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Memory at 40000000 (32-bit, prefetchable) [size=64M]
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: d8000000-dfffffff
	Capabilities: <access denied>

00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fdffe000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 44000000 [disabled] [size=512K]
	Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at fa00 [size=8]
	I/O ports at f900 [size=4]
	I/O ports at f800 [size=8]
	I/O ports at f700 [size=4]
	I/O ports at f600 [size=16]
	Memory at fdffd000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 44080000 [disabled] [size=512K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fdffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fdffb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fdffa000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: 66MHz, medium devsel
	I/O ports at 0500 [size=16]
	Memory at fdff9000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f400 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at fdff0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200] (prog-if 00 [VGA controller])
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 17
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at ee00 [size=256]
	Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fde00000 [disabled] [size=128K]
	Capabilities: <access denied>

02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
	Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
	Flags: bus master, stepping, medium devsel, latency 64, IRQ 20
	Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at df00 [size=128]
	Capabilities: <access denied>

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
	Subsystem: Foxconn International, Inc. Unknown device 0c81
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at dc00 [size=256]
	Memory at fddfe000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
	Capabilities: <access denied>

Looking here [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) I can't find Realtek or ATI or ALC880 listed. Not sure what I'm supposed to be looking for or finding.

This is about as far as I've got. I'm afraid I'm just not sure what I'm supposed to be doing.

---

### Post by unutbu on 2008-05-01
Jake, would you please post the output to 
```

dmesg
```

---

### Post by jakelute on 2008-05-01
jake@jake:~$ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4080
[    0.000000] Entering add_active_range(0, 0, 245488) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245488
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245488
[    0.000000] On node 0 totalpages: 245488
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 125 pages used for memmap
[    0.000000]   HighMem zone: 15987 pages, LIFO batch:3
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] Processor #0 6:8 APIC version 17
[    0.000000] Processor #1 6:1 APIC version 17
[    0.000000] I/O APIC #4 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3bf00000:a4100000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243571
[    0.000000] Kernel command line: root=UUID=a66a15a3-094b-403f-9923-e6324ba8677f ro acpi=off pci=noacpi
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3400.000 MHz processor.
[   15.244444] Console: colour VGA+ 80x25
[   15.244449] console [tty0] enabled
[   15.247169] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.247888] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.269300] Memory: 961056k/981952k available (2157k kernel code, 20320k reserved, 998k data, 364k init, 64448k highmem)
[   15.269362] virtual kernel memory layout:
[   15.269363]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   15.269364]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.269365]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.269366]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.269367]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   15.269368]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   15.269369]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   15.269725] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.269845] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   15.349869] Calibrating delay using timer specific routine.. 6807.31 BogoMIPS (lpj=13614626)
[   15.349979] Security Framework initialized
[   15.350027] SELinux:  Disabled at boot.
[   15.350082] AppArmor: AppArmor initialized
[   15.350130] Failure registering capabilities with primary security module.
[   15.350183] Mount-cache hash table entries: 512
[   15.350339] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001 00000000
[   15.350348] monitor/mwait feature present.
[   15.350393] using mwait in idle threads.
[   15.350441] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.350524] CPU: L2 cache: 2048K
[   15.350569] CPU: Physical Processor ID: 0
[   15.350614] CPU: Processor Core ID: 0
[   15.350659] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e49d 00000000 00000001 00000000
[   15.350668] Compat vDSO mapped to ffffe000.
[   15.350726] Checking 'hlt' instruction... OK.
[   15.366323] SMP alternatives: switching to UP code
[   15.368071] Early unpacking initramfs... done
[   15.643265] CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 05
[   15.643401] SMP alternatives: switching to SMP code
[   15.644218] Booting processor 1/1 eip 3000
[   15.654608] Initializing CPU#1
[   15.733621] Calibrating delay using timer specific routine.. 6799.91 BogoMIPS (lpj=13599829)
[   15.733630] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001 00000000
[   15.733636] monitor/mwait feature present.
[   15.733641] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.733643] CPU: L2 cache: 2048K
[   15.733645] CPU: Physical Processor ID: 0
[   15.733646] CPU: Processor Core ID: 1
[   15.733647] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e49d 00000000 00000001 00000000
[   15.734157] CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 05
[   15.734603] Total of 2 processors activated (13607.22 BogoMIPS).
[   15.734732] ExtINT not setup in hardware but reported by MP table
[   15.734864] ENABLING IO-APIC IRQs
[   15.735097] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   15.989553] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   16.009646] Brought up 2 CPUs
[   16.009723] CPU0 attaching sched-domain:
[   16.009726]  domain 0: span 03
[   16.009728]   groups: 01 02
[   16.009731] CPU1 attaching sched-domain:
[   16.009733]  domain 0: span 03
[   16.009735]   groups: 02 01
[   16.009933] net_namespace: 64 bytes
[   16.009983] Booting paravirtualized kernel on bare hardware
[   16.010611] Time:  8:18:20  Date: 05/01/08
[   16.010678] NET: Registered protocol family 16
[   16.010934] EISA bus registered
[   16.046468] PCI: PCI BIOS revision 3.00 entry at 0xfb170, last bus=2
[   16.046515] PCI: Using configuration type 1
[   16.046560] Setting up standard PCI resources
[   16.049933] mtrr: your CPUs had inconsistent variable MTRR settings
[   16.049981] mtrr: probably your BIOS does not setup all CPUs.
[   16.050027] mtrr: corrected configuration.
[   16.050683] ACPI: Interpreter disabled.
[   16.050730] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.050809] pnp: PnP ACPI: disabled
[   16.050856] PnPBIOS: Scanning system for PnP BIOS support...
[   16.051241] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbce0
[   16.051289] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbd10, dseg 0xf0000
[   16.052151] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[   16.052429] PCI: Probing PCI hardware
[   16.052478] PCI: Probing PCI hardware (bus 00)
[   16.053973] PCI: Transparent bridge - 0000:00:14.4
[   16.055259] PCI->APIC IRQ transform: 0000:00:11.0[A] -> IRQ 23
[   16.055309] PCI->APIC IRQ transform: 0000:00:12.0[A] -> IRQ 22
[   16.055358] PCI->APIC IRQ transform: 0000:00:13.0[A] -> IRQ 19
[   16.055407] PCI->APIC IRQ transform: 0000:00:13.1[A] -> IRQ 19
[   16.055455] PCI->APIC IRQ transform: 0000:00:13.2[A] -> IRQ 19
[   16.055505] PCI->APIC IRQ transform: 0000:00:14.1[A] -> IRQ 17
[   16.055554] PCI->APIC IRQ transform: 0000:00:14.2[A] -> IRQ 17
[   16.055605] PCI->APIC IRQ transform: 0000:01:05.0[A] -> IRQ 17
[   16.055654] PCI->APIC IRQ transform: 0000:02:05.0[A] -> IRQ 20
[   16.055703] PCI->APIC IRQ transform: 0000:02:07.0[A] -> IRQ 22
[   16.055753] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   16.055801] PCI: Cannot allocate resource region 0 of device 0000:00:01.0
[   16.089430] NET: Registered protocol family 8
[   16.089480] NET: Registered protocol family 20
[   16.089594] AppArmor: AppArmor Filesystem Enabled
[   16.089676] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[   16.089725] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[   16.089778] system 00:07: iomem range 0xfff80000-0xfffdffff could not be reserved
[   16.089831] system 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   16.089883] system 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   16.089937] system 00:07: iomem range 0x100000-0xffffff could not be reserved
[   16.089988] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[   16.090036] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[   16.090084] system 00:08: iomem range 0xf8000-0xfffff could not be reserved
[   16.090131] system 00:08: iomem range 0xd0000-0xd3fff has been reserved
[   16.090592] PCI: Bridge: 0000:00:01.0
[   16.090639]   IO window: e000-efff
[   16.090685]   MEM window: fde00000-fdefffff
[   16.090731]   PREFETCH window: d8000000-dfffffff
[   16.090779] PCI: Bridge: 0000:00:14.4
[   16.090826]   IO window: d000-dfff
[   16.090875]   MEM window: fdd00000-fddfffff
[   16.090924]   PREFETCH window: fdc00000-fdcfffff
[   16.091001] NET: Registered protocol family 2
[   16.093425] Time: tsc clocksource has been installed.
[   16.125508] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.125861] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.126610] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.127038] TCP: Hash tables configured (established 131072 bind 65536)
[   16.127086] TCP reno registered
[   16.137574] checking if image is initramfs... it is
[   16.684322] Freeing initrd memory: 7698k freed
[   16.685495] audit: initializing netlink socket (disabled)
[   16.685566] audit(1209629900.296:1): initialized
[   16.685869] highmem bounce pool size: 64 pages
[   16.688726] VFS: Disk quotas dquot_6.5.1
[   16.688876] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.689181] io scheduler noop registered
[   16.689233] io scheduler anticipatory registered
[   16.689281] io scheduler deadline registered
[   16.689344] io scheduler cfq registered (default)
[   16.689394] PCI: MSI quirk detected. MSI deactivated.
[   24.748072] 0000:00:13.2 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   24.748143] Boot video device is 0000:01:05.0
[   24.748501] isapnp: Scanning for PnP cards...
[   25.099950] isapnp: No Plug & Play device found
[   25.145721] Real Time Clock Driver v1.12ac
[   25.145882] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.146114] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.147144] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.148371] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.148521] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.148734] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   25.149218] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.149273] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.162892] mice: PS/2 mouse device common for all mice
[   25.163081] EISA: Probing bus 0 at eisa.0
[   25.163169] EISA: Detected 0 cards.
[   25.163216] cpuidle: using governor ladder
[   25.163261] cpuidle: using governor menu
[   25.163403] NET: Registered protocol family 1
[   25.163484] Using IPI No-Shortcut mode
[   25.163563] registered taskstats version 1
[   25.163695]   Magic number: 8:185:320
[   25.164442]   hash matches device tty45
[   25.164516] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.164562] EDD information not available.
[   25.165026] Freeing unused kernel memory: 364k freed
[   25.186682] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   25.360098] fuse init (API version 7.9)
[   25.425135] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   25.526972] SCSI subsystem initialized
[   25.552103] libata version 3.00 loaded.
[   25.554006] usbcore: registered new interface driver usbfs
[   25.554077] usbcore: registered new interface driver hub
[   25.565369] usbcore: registered new device driver usb
[   25.576784] sata_sil 0000:00:11.0: version 2.3
[   25.578691] scsi0 : sata_sil
[   25.578835] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.584715] scsi1 : sata_sil
[   25.584795] ata1: SATA max UDMA/100 mmio m512@0xfdffe000 tf 0xfdffe080 irq 23
[   25.584844] ata2: SATA max UDMA/100 mmio m512@0xfdffe000 tf 0xfdffe0c0 irq 23
[   25.681927] Floppy drive(s): fd0 is 1.44M
[   25.701677] FDC 0 is a post-1991 82077
[   25.896634] ata1: SATA link down (SStatus 0 SControl 310)
[   26.208650] ata2: SATA link down (SStatus 0 SControl 310)
[   26.208888] scsi2 : sata_sil
[   26.209106] scsi3 : sata_sil
[   26.209181] ata3: SATA max UDMA/100 mmio m512@0xfdffd000 tf 0xfdffd080 irq 22
[   26.209232] ata4: SATA max UDMA/100 mmio m512@0xfdffd000 tf 0xfdffd0c0 irq 22
[   26.676494] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   26.729483] ata3.00: ATA-7: ST3320620AS, 3.AAJ, max UDMA/133
[   26.729532] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   26.796078] ata3.00: configured for UDMA/100
[   27.104348] ata4: SATA link down (SStatus 0 SControl 310)
[   27.104528] scsi 2:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[   27.104679] r8169 Gigabit Ethernet driver 2.2LK loaded
[   27.104931] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   27.105088] eth0: RTL8110s at 0xf884e000, 00:15:58:76:e0:c2, XID 04000000 IRQ 22
[   27.105261] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   27.105335] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfdffc000
[   27.164481] usb usb1: configuration #1 chosen from 1 choice
[   27.164556] hub 1-0:1.0: USB hub found
[   27.164610] hub 1-0:1.0: 4 ports detected
[   27.268433] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   27.268500] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   27.268565] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfdffb000
[   27.328363] usb usb2: configuration #1 chosen from 1 choice
[   27.328433] hub 2-0:1.0: USB hub found
[   27.328486] hub 2-0:1.0: 4 ports detected
[   27.432640] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   27.432716] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   27.432825] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfdffa000
[   27.444265] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.444418] usb usb3: configuration #1 chosen from 1 choice
[   27.444493] hub 3-0:1.0: USB hub found
[   27.444545] hub 3-0:1.0: 8 ports detected
[   27.549283] scsi4 : pata_atiixp
[   27.549886] scsi5 : pata_atiixp
[   27.549964] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[   27.550012] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[   28.188643] ata6.00: ATAPI: CD-RW BCE4816IM, VER 482S, max UDMA/33
[   28.188713] ata6.01: ATAPI: ASUS    DRW-1608P3S, 1.24, max UDMA/33
[   28.360542] ata6.00: configured for UDMA/33
[   28.532536] ata6.01: configured for UDMA/33
[   28.532963] scsi 5:0:0:0: CD-ROM            BTC      BCE4816IM        482S PQ: 0 ANSI: 5
[   28.539651] scsi 5:0:1:0: CD-ROM            ASUS     DRW-1608P3S      1.24 PQ: 0 ANSI: 5
[   28.600135] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   28.608258] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   28.608314] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.620368] Driver 'sd' needs updating - please use bus_type methods
[   28.621532] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   28.621594] sd 2:0:0:0: [sda] Write Protect is off
[   28.621640] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.621661] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.621763] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   28.621820] sd 2:0:0:0: [sda] Write Protect is off
[   28.621867] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.621887] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.621943]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   28.641955]  sda1 sda2 < sda5 >
[   28.663280] sd 2:0:0:0: [sda] Attached SCSI disk
[   28.668084] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   28.668144] Uniform CD-ROM driver Revision: 3.20
[   28.668250] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   28.669038] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   28.669110] sr 5:0:0:0: Attached scsi generic sg1 type 5
[   28.669173] sr 5:0:1:0: Attached scsi generic sg2 type 5
[   28.699596] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   28.699718] sr 5:0:1:0: Attached scsi CD-ROM sr1
[   28.848386] Attempting manual resume
[   28.848434] swsusp: Resume From Partition 8:5
[   28.848436] PM: Checking swsusp image.
[   28.848589] PM: Resume from disk failed.
[   28.870247] EXT3-fs: INFO: recovery required on readonly filesystem.
[   28.870298] EXT3-fs: write access will be enabled during recovery.
[   29.690145] kjournald starting.  Commit interval 5 seconds
[   29.690164] EXT3-fs: sda1: orphan cleanup on readonly fs
[   29.690174] ext3_orphan_cleanup: deleting unreferenced inode 12279865
[   29.690222] ext3_orphan_cleanup: deleting unreferenced inode 16163080
[   29.690245] ext3_orphan_cleanup: deleting unreferenced inode 12279829
[   29.690253] EXT3-fs: sda1: 3 orphan inodes deleted
[   29.690254] EXT3-fs: recovery complete.
[   29.717631] EXT3-fs: mounted filesystem with ordered data mode.
[   29.882264] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001206000000133f]
[   36.100961] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.160973] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.226380] Linux agpgart interface v0.102
[   36.262478] agpgart: Unsupported Ati chipset (device id: 5a33)
[   36.388746] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   36.452367] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   36.747177] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   36.799008] [fglrx] Maximum main memory to use for locked dma buffers: 865 MBytes.
[   36.799113] [fglrx] ASYNCIO init succeed!
[   36.800916] [fglrx] PAT is enabled successfully!
[   36.801010] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   37.358162] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   38.086548] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
[   38.088263] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   38.784151] lp: driver loaded but no devices found
[   38.853669] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   38.853749] apm: disabled - APM is not SMP safe (power off active).
[   38.890588] Adding 2835432k swap on /dev/sda5.  Priority:-1 extents:1 across:2835432k
[   39.315057] EXT3 FS on sda1, internal journal
[   39.769904] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.402255] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   40.402312] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   40.402505] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   40.402590] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   41.130887] ppdev: user-space parallel port driver
[   41.198810] audit(1209629925.499:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4796 profile="/usr/sbin/cupsd" namespace="default"
[   41.967389] r8169: eth0: link up
[   42.036859] Bluetooth: Core ver 2.11
[   42.037593] NET: Registered protocol family 31
[   42.037599] Bluetooth: HCI device and connection manager initialized
[   42.037603] Bluetooth: HCI socket layer initialized
[   42.077350] Bluetooth: L2CAP ver 2.9
[   42.077356] Bluetooth: L2CAP socket layer initialized
[   42.145133] Bluetooth: RFCOMM socket layer initialized
[   42.145152] Bluetooth: RFCOMM TTY layer initialized
[   42.145154] Bluetooth: RFCOMM ver 1.8
[   43.425710] [fglrx] GART Table is not in FRAME_BUFFER range 
[   43.425719] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   43.425722] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   43.563562] [fglrx] interrupt source 10000000 successfully enabled
[   43.563568] [fglrx] enable ID = 0x00000004
[   43.564736] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   46.156874] NET: Registered protocol family 17
[   49.919306] NET: Registered protocol family 10
[   49.919634] lo: Disabled Privacy Extensions
[   53.536064] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:600: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x306f000a
[   60.052769] eth0: no IPv6 routers present
[  498.714151] audit(1209630385.054:3): type=1503 operation="capable" name="dac_override" pid=5688 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
[  498.714161] audit(1209630385.054:4): type=1503 operation="capable" name="dac_read_search" pid=5688 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
[  511.152339] ieee1394: Error parsing configrom for node 0-00:1023
[  511.152401] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[  519.787828] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0030e0f4e0204b47]
[  519.789130] scsi6 : SBP-2 IEEE-1394
[  520.792715] ieee1394: sbp2: Logged into SBP-2 device
[  520.793108] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  520.797032] scsi 6:0:0:0: Direct-Access-RBC ST312002 6A               8.01 PQ: 0 ANSI: 4
[  520.813389] sd 6:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[  520.813772] sd 6:0:0:0: [sdb] Write Protect is off
[  520.813776] sd 6:0:0:0: [sdb] Mode Sense: 11 00 00 00
[  520.814537] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  520.815845] sd 6:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[  520.816240] sd 6:0:0:0: [sdb] Write Protect is off
[  520.816243] sd 6:0:0:0: [sdb] Mode Sense: 11 00 00 00
[  520.817026] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  520.817031]  sdb: sdb1
[  520.820184] sd 6:0:0:0: [sdb] Attached SCSI disk
[  520.820229] sd 6:0:0:0: Attached scsi generic sg3 type 14
[  597.131944] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[  597.131955] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0030e0f4e0204b47]
[  597.132209] sd 6:0:0:0: [sdb] Synchronizing SCSI cache
[  597.133303] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
jake@jake:~$

---

### Post by unutbu on 2008-05-01
Ok, thanks. Now could you post dmesg again while booting without any special kernel options (so ACPI is on)?

---

### Post by jakelute on 2008-05-01
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4080
[    0.000000] Entering add_active_range(0, 0, 245488) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245488
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245488
[    0.000000] On node 0 totalpages: 245488
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 125 pages used for memmap
[    0.000000]   HighMem zone: 15987 pages, LIFO batch:3
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F87E0 checksum 0
[    0.000000] ACPI: RSDP 000F87E0, 0014 (r0 RS400 )
[    0.000000] ACPI: RSDT 3BEF3040, 0038 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3BEF30C0, 0074 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3BEF3180, 416F (r1 RS400  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BEF0000, 0040
[    0.000000] ACPI: MCFG 3BEF7440, 003C (r1 RS400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3BEF7340, 0084 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 3BEF74C0, 019E (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[    0.000000] ACPI: SSDT 3BEF7950, 022A (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3bf00000:a4100000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243571
[    0.000000] Kernel command line: root=UUID=a66a15a3-094b-403f-9923-e6324ba8677f ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3399.862 MHz processor.
[   16.048566] Console: colour VGA+ 80x25
[   16.048571] console [tty0] enabled
[   16.049404] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.050095] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.071532] Memory: 961056k/981952k available (2157k kernel code, 20320k reserved, 998k data, 364k init, 64448k highmem)
[   16.071539] virtual kernel memory layout:
[   16.071540]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   16.071541]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.071542]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.071543]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.071544]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   16.071545]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   16.071545]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   16.071548] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.071580] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   16.151554] Calibrating delay using timer specific routine.. 6807.35 BogoMIPS (lpj=13614711)
[   16.151576] Security Framework initialized
[   16.151581] SELinux:  Disabled at boot.
[   16.151593] AppArmor: AppArmor initialized
[   16.151596] Failure registering capabilities with primary security module.
[   16.151604] Mount-cache hash table entries: 512
[   16.151715] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001 00000000
[   16.151724] monitor/mwait feature present.
[   16.151726] using mwait in idle threads.
[   16.151731] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   16.151733] CPU: L2 cache: 2048K
[   16.151736] CPU: Physical Processor ID: 0
[   16.151737] CPU: Processor Core ID: 0
[   16.151739] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e49d 00000000 00000001 00000000
[   16.151749] Compat vDSO mapped to ffffe000.
[   16.151763] Checking 'hlt' instruction... OK.
[   16.167972] SMP alternatives: switching to UP code
[   16.169678] Early unpacking initramfs... done
[   16.444565] ACPI: Core revision 20070126
[   16.444617] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.472308] CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 05
[   16.472333] SMP alternatives: switching to SMP code
[   16.473108] Booting processor 1/1 eip 3000
[   16.483474] Initializing CPU#1
[   16.563287] Calibrating delay using timer specific routine.. 6799.90 BogoMIPS (lpj=13599800)
[   16.563297] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001 00000000
[   16.563303] monitor/mwait feature present.
[   16.563308] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   16.563310] CPU: L2 cache: 2048K
[   16.563312] CPU: Physical Processor ID: 0
[   16.563313] CPU: Processor Core ID: 1
[   16.563314] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e49d 00000000 00000001 00000000
[   16.563798] CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 05
[   16.563830] Total of 2 processors activated (13607.25 BogoMIPS).
[   16.564002] ENABLING IO-APIC IRQs
[   16.564188] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.711295] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   16.731307] Brought up 2 CPUs
[   16.731344] CPU0 attaching sched-domain:
[   16.731347]  domain 0: span 03
[   16.731349]   groups: 01 02
[   16.731352] CPU1 attaching sched-domain:
[   16.731354]  domain 0: span 03
[   16.731356]   groups: 02 01
[   16.731545] net_namespace: 64 bytes
[   16.731552] Booting paravirtualized kernel on bare hardware
[   16.732144] Time: 11:13:04  Date: 05/01/08
[   16.732167] NET: Registered protocol family 16
[   16.732375] EISA bus registered
[   16.732381] ACPI: bus type pci registered
[   16.734578] PCI: PCI BIOS revision 3.00 entry at 0xfb170, last bus=2
[   16.734580] PCI: Using configuration type 1
[   16.734582] Setting up standard PCI resources
[   16.737819] mtrr: your CPUs had inconsistent variable MTRR settings
[   16.737822] mtrr: probably your BIOS does not setup all CPUs.
[   16.737823] mtrr: corrected configuration.
[   16.738980] ACPI: EC: Look up EC in DSDT
[   16.743547] ACPI: Interpreter enabled
[   16.743550] ACPI: (supports S0 S1 S4 S5)
[   16.743565] ACPI: Using IOAPIC for interrupt routing
[   16.747991] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.749470] PCI: Transparent bridge - 0000:00:14.4
[   16.749506] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.749725] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   16.749853] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   16.764393] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   16.764491] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   16.764589] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   16.764686] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   16.764786] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11)
[   16.764883] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   16.764982] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
[   16.765079] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *10 11)
[   16.765215] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.765249] pnp: PnP ACPI init
[   16.765256] ACPI: bus type pnp registered
[   16.767906] pnp: PnP ACPI: found 13 devices
[   16.767908] ACPI: ACPI bus type pnp unregistered
[   16.767912] PnPBIOS: Disabled by ACPI PNP
[   16.768149] PCI: Using ACPI for IRQ routing
[   16.768152] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.768160] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   16.768163] PCI: Cannot allocate resource region 0 of device 0000:00:01.0
[   16.803168] NET: Registered protocol family 8
[   16.803171] NET: Registered protocol family 20
[   16.803259] AppArmor: AppArmor Filesystem Enabled
[   16.807162] Time: tsc clocksource has been installed.
[   16.815212] system 00:01: ioport range 0x140-0x15f has been reserved
[   16.815216] system 00:01: ioport range 0x228-0x22f has been reserved
[   16.815220] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   16.815223] system 00:01: ioport range 0xc00-0xc01 has been reserved
[   16.815226] system 00:01: ioport range 0xc14-0xc14 has been reserved
[   16.815229] system 00:01: ioport range 0xc50-0xc52 has been reserved
[   16.815232] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[   16.815238] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[   16.815245] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[   16.815248] system 00:01: ioport range 0x4000-0x40fe has been reserved
[   16.815250] system 00:01: ioport range 0x4210-0x4217 has been reserved
[   16.815258] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   16.815261] system 00:06: ioport range 0x220-0x225 has been reserved
[   16.815263] system 00:06: ioport range 0x40b-0x41a has been reserved
[   16.815265] system 00:06: ioport range 0x880-0x88f has been reserved
[   16.815274] system 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.815280] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[   16.815282] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   16.815285] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   16.815287] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   16.815290] system 00:0c: iomem range 0x3bf00000-0x3bffffff has been reserved
[   16.815292] system 00:0c: iomem range 0x3bef0000-0x3befffff could not be reserved
[   16.815295] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[   16.815297] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   16.815300] system 00:0c: iomem range 0x100000-0x3beeffff could not be reserved
[   16.815302] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   16.815305] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   16.815307] system 00:0c: iomem range 0xfff80000-0xfffeffff could not be reserved
[   16.845750] PCI: Bridge: 0000:00:01.0
[   16.845753]   IO window: e000-efff
[   16.845757]   MEM window: fde00000-fdefffff
[   16.845760]   PREFETCH window: d8000000-dfffffff
[   16.845765] PCI: Bridge: 0000:00:14.4
[   16.845768]   IO window: d000-dfff
[   16.845775]   MEM window: fdd00000-fddfffff
[   16.845780]   PREFETCH window: fdc00000-fdcfffff
[   16.845813] NET: Registered protocol family 2
[   16.883223] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.883544] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.884237] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.884637] TCP: Hash tables configured (established 131072 bind 65536)
[   16.884639] TCP reno registered
[   16.895294] checking if image is initramfs... it is
[   17.342930] Switched to high resolution mode on CPU 1
[   17.346842] Switched to high resolution mode on CPU 0
[   17.442253] Freeing initrd memory: 7698k freed
[   17.443422] audit: initializing netlink socket (disabled)
[   17.443439] audit(1209640384.228:1): initialized
[   17.443721] highmem bounce pool size: 64 pages
[   17.446687] VFS: Disk quotas dquot_6.5.1
[   17.446799] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.446968] io scheduler noop registered
[   17.446971] io scheduler anticipatory registered
[   17.446973] io scheduler deadline registered
[   17.446988] io scheduler cfq registered (default)
[   17.446997] PCI: MSI quirk detected. MSI deactivated.
[   25.497220] 0000:00:13.2 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   25.497247] Boot video device is 0000:01:05.0
[   25.497678] isapnp: Scanning for PnP cards...
[   25.849088] isapnp: No Plug & Play device found
[   25.895064] Real Time Clock Driver v1.12ac
[   25.895208] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.895387] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.896328] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.897571] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.897668] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.897818] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   25.898248] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.898256] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.909107] mice: PS/2 mouse device common for all mice
[   25.909252] EISA: Probing bus 0 at eisa.0
[   25.909276] Cannot allocate resource for EISA slot 4
[   25.909297] EISA: Detected 0 cards.
[   25.909301] cpuidle: using governor ladder
[   25.909303] cpuidle: using governor menu
[   25.909401] NET: Registered protocol family 1
[   25.909436] Using IPI No-Shortcut mode
[   25.909474] registered taskstats version 1
[   25.909584]   Magic number: 8:400:225
[   25.909660]   hash matches device ttyu9
[   25.909677]   hash matches device ttyrc
[   25.909858] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.909860] EDD information not available.
[   25.910258] Freeing unused kernel memory: 364k freed
[   25.932893] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.126916] fuse init (API version 7.9)
[   27.143501] ACPI: Fan [FAN] (on)
[   27.149482] ACPI: SSDT 3BEF78C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[   27.149622] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.149634] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.151085] ACPI: Thermal Zone [THRM] (40 C)
[   27.314123] SCSI subsystem initialized
[   27.338739] libata version 3.00 loaded.
[   27.348638] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 16
[   27.348710] ACPI: PCI interrupt for device 0000:00:11.0 disabled
[   27.348744] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[   27.348778] ACPI: PCI interrupt for device 0000:00:12.0 disabled
[   27.348802] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   27.348834] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   27.400332] sata_sil 0000:00:11.0: version 2.3
[   27.400373] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 16
[   27.400464] scsi0 : sata_sil
[   27.400516] scsi1 : sata_sil
[   27.400662] ata1: SATA max UDMA/100 mmio m512@0xfdffe000 tf 0xfdffe080 irq 16
[   27.400666] ata2: SATA max UDMA/100 mmio m512@0xfdffe000 tf 0xfdffe0c0 irq 16
[   27.482955] usbcore: registered new interface driver usbfs
[   27.482982] usbcore: registered new interface driver hub
[   27.483323] usbcore: registered new device driver usb
[   27.484527] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.557603] Floppy drive(s): fd0 is 1.44M
[   27.576715] FDC 0 is a post-1991 82077
[   27.711719] ata1: SATA link down (SStatus 0 SControl 310)
[   28.023507] ata2: SATA link down (SStatus 0 SControl 310)
[   28.023620] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[   28.023702] scsi2 : sata_sil
[   28.023769] scsi3 : sata_sil
[   28.023919] ata3: SATA max UDMA/100 mmio m512@0xfdffd000 tf 0xfdffd080 irq 17
[   28.023923] ata4: SATA max UDMA/100 mmio m512@0xfdffd000 tf 0xfdffd0c0 irq 17
[   28.491207] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   28.538517] ata3.00: ATA-7: ST3320620AS, 3.AAJ, max UDMA/133
[   28.538523] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   28.605102] ata3.00: configured for UDMA/100
[   28.915897] ata4: SATA link down (SStatus 0 SControl 310)
[   28.916043] scsi 2:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[   28.916184] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   28.916317] scsi4 : pata_atiixp
[   28.916378] scsi5 : pata_atiixp
[   28.917228] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[   28.917231] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[   28.924165] Driver 'sd' needs updating - please use bus_type methods
[   28.924262] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   28.924276] sd 2:0:0:0: [sda] Write Protect is off
[   28.924279] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.924300] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.924354] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   28.924366] sd 2:0:0:0: [sda] Write Protect is off
[   28.924369] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.924389] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.924393]  sda: sda1 sda2 < sda5 >
[   28.965614] sd 2:0:0:0: [sda] Attached SCSI disk
[   28.970379] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   29.172902] Attempting manual resume
[   29.172906] swsusp: Resume From Partition 8:5
[   29.172907] PM: Checking swsusp image.
[   29.173060] PM: Resume from disk failed.
[   29.215503] kjournald starting.  Commit interval 5 seconds
[   29.215525] EXT3-fs: mounted filesystem with ordered data mode.
[   29.555987] ata6.00: ATAPI: CD-RW BCE4816IM, VER 482S, max UDMA/33
[   29.556011] ata6.01: ATAPI: ASUS    DRW-1608P3S, 1.24, max UDMA/33
[   29.726867] ata6.00: configured for UDMA/33
[   29.899768] ata6.01: configured for UDMA/33
[   29.900181] scsi 5:0:0:0: CD-ROM            BTC      BCE4816IM        482S PQ: 0 ANSI: 5
[   29.900273] scsi 5:0:0:0: Attached scsi generic sg1 type 5
[   29.906133] scsi 5:0:1:0: CD-ROM            ASUS     DRW-1608P3S      1.24 PQ: 0 ANSI: 5
[   29.906240] scsi 5:0:1:0: Attached scsi generic sg2 type 5
[   29.906344] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   29.906372] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   29.906753] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   29.906779] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfdffc000
[   29.967287] usb usb1: configuration #1 chosen from 1 choice
[   29.967314] hub 1-0:1.0: USB hub found
[   29.967324] hub 1-0:1.0: 4 ports detected
[   30.071224] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   30.071240] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   30.071265] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   30.071280] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfdffb000
[   30.130141] usb usb2: configuration #1 chosen from 1 choice
[   30.130165] hub 2-0:1.0: USB hub found
[   30.130175] hub 2-0:1.0: 4 ports detected
[   30.235107] r8169 Gigabit Ethernet driver 2.2LK loaded
[   30.235153] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 22 (level, low) -> IRQ 17
[   30.235472] eth0: RTL8110s at 0xf8824000, 00:15:58:76:e0:c2, XID 04000000 IRQ 17
[   30.238813] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 20
[   30.239256] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   30.239269] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   30.239293] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   30.239346] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfdffa000
[   30.250971] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.251096] usb usb3: configuration #1 chosen from 1 choice
[   30.251126] hub 3-0:1.0: USB hub found
[   30.251132] hub 3-0:1.0: 8 ports detected
[   30.291608] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   31.566252] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001206000000133f]
[   35.478467] Linux agpgart interface v0.102
[   35.506512] agpgart: Unsupported Ati chipset (device id: 5a33)
[   35.531055] input: Power Button (FF) as /devices/virtual/input/input2
[   35.566333] ACPI: Power Button (FF) [PWRF]
[   35.566420] input: Power Button (CM) as /devices/virtual/input/input3
[   35.582520] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.594317] ACPI: Power Button (CM) [PWRB]
[   35.610424] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.655395] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   35.655403] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   35.803320] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   36.285930] Driver 'sr' needs updating - please use bus_type methods
[   36.301695] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   36.301699] Uniform CD-ROM driver Revision: 3.20
[   36.301753] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   36.332838] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   36.332903] sr 5:0:1:0: Attached scsi CD-ROM sr1
[   36.378952] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   36.577771] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
[   36.587793] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   36.608621] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   36.692522] [fglrx] Maximum main memory to use for locked dma buffers: 865 MBytes.
[   36.692563] [fglrx] ASYNCIO init succeed!
[   36.694042] [fglrx] PAT is enabled successfully!
[   36.694068] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   37.075844] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   38.036677] lp: driver loaded but no devices found
[   38.098855] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   38.098859] apm: overridden by ACPI.
[   38.155897] Adding 2835432k swap on /dev/sda5.  Priority:-1 extents:1 across:2835432k
[   38.692317] EXT3 FS on sda1, internal journal
[   39.731031] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.039823] No dock devices found.
[   40.973005] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   40.973011] apm: disabled on user request.
[   41.200107] ppdev: user-space parallel port driver
[   41.280312] audit(1209640409.331:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4812 profile="/usr/sbin/cupsd" namespace="default"
[   42.144081] r8169: eth0: link up
[   42.208785] Bluetooth: Core ver 2.11
[   42.208975] NET: Registered protocol family 31
[   42.208978] Bluetooth: HCI device and connection manager initialized
[   42.208983] Bluetooth: HCI socket layer initialized
[   42.231835] Bluetooth: L2CAP ver 2.9
[   42.231843] Bluetooth: L2CAP socket layer initialized
[   42.315573] Bluetooth: RFCOMM socket layer initialized
[   42.315593] Bluetooth: RFCOMM TTY layer initialized
[   42.315596] Bluetooth: RFCOMM ver 1.8
[   44.193137] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 21
[   44.608473] [fglrx] GART Table is not in FRAME_BUFFER range 
[   44.608485] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   44.608487] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   44.764960] [fglrx] interrupt source 10000000 successfully enabled
[   44.764967] [fglrx] enable ID = 0x00000004
[   44.764976] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   46.483997] NET: Registered protocol family 17
[   51.760387] NET: Registered protocol family 10
[   51.760760] lo: Disabled Privacy Extensions
[   52.903972] hda-intel: Invalid position buffer, using LPIB read method instead.
[   62.399975] eth0: no IPv6 routers present

---

### Post by unutbu on 2008-05-01
Options (in no particular order)

1) Upgrade BIOS.
Pros: Maybe this is the missing piece?
Maybe it would fix this error reported in dmseg:
[ 24.748072] 0000:00:13.2 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
(I am not positive this is related to the primary problem, however.)

Cons: 
1a) Upgrading BIOS can be dangerous
1b) You have to get the BIOS upgrade from your computer manufacturer or motherboard manufacturer. I don't know how easy that would be for you.

If you go this route, here is a guide on how to do it.
[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

Instead of using cdrecord (near the end fo the guide), you can burn the .iso file by right-clicking on the file in nautilus and saying 'Write to Disc'.

2) Compile/try the latest linux kernel. 
Pros: 
2a) If your problem can be fixed with the latest ACPI code (which is part of the kernel) then this should solve the problem. If it doesn't solve the problem, then at least you'll make the ACPI code developers happy that you tried the latest version when/if you file a bug report at [http://bugzilla.kernel.org/](http://bugzilla.kernel.org/).

2b) It's not dangerous. (Similar to booting with kernel options.)

Cons: 
2c) I'll need to learn how to compile a kernel under Ubuntu first. I've done it under RedHat, but never under Ubuntu. It wasn't hard under RedHat, so I figure it should be the same under Ubuntu. Except for one thing, the instructions I would give you would probably be almost identical to [https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html).

3) Try other distros. 
Pros:
3a) Its easy. Takes some time, but relatively painless. And it may work...
This thread, [http://ubuntuforums.org/showthread.php?t=769492&page=3](http://ubuntuforums.org/showthread.php?t=769492&page=3),
has a post by a user who says sound worked out of the box under Debian but does not work under Ubuntu 8.04. 

Cons:
3b) It's a completely untargeted approach to solving the problem.

4) Go back to the old 8.04. It seemed we were closer to a solution there?

5) Go back to 7.10. A lot of people have been reporting problems with 8.04. There are probably still some kinks being worked out. 

6) Give this thread some more time

7) Post a report at [http://bugzilla.kernel.org/](http://bugzilla.kernel.org/). You'll have to create an account there; not hard.
This may be your best bet. Your problem certainly seems to be ACPI-related. I would describe the 10minute freeze problem you were having before running with acpi=off.

---

### Post by jakelute on 2008-05-01
Thanks for this! I'm thinking about it....

---

### Post by jakelute on 2008-05-01
Hi Unutbu,

I've been thinking about your various suggestions. I think it would be useful to file a bug report, of course. But I'd still be without a properly working system for the forseeable. So I'm not sure.

I must admit that the two options which look most attractive at the moment are the BIOS upgrade or the latest linux kernel. And looking briefly at the two guides you linked to, the BIOS instructions look easier to me than the kernel ones, which appear to me to be way over my head!

As for trying other distros -- I'll do it as a last resort before returning to Windows, but would rather not do it until I'm sure Ubuntu won't work on this system.

As for going back to the previous 8.04 I was using -- I'm not sure it was that much better. 7.10 was no better either -- I had all the same freeze issues.

So I think it's BIOS or kernel. Would be prepared to try the kernel thing first if you think it's wiser than going straight into a BIOS upgrade, but I'm afraid I'd probably need more guidance than the link you sent me can provide. I'm not convinced I'm up to it!

---

### Post by unutbu on 2008-05-02
Hi Jake, I compiled a kernel last night so hopefully my information is now fresh.

Actually, all I did was follow the instructions at
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158).

When you compile a kernel, you have to make a whole bunch of yes/no type decisions about what you want in your kernel. Fortunately, these decisions are saved in a config file. Your current 
2.6.24-16-generic kernel's config is /boot/config-2.6.24-16-generic.

Step 8 copies this config as a default starting point so if you do nothing the kernel you compile should be similar to your current kernel. Linus Torvalds and his crew are frequently adding new configuration options to the kernel and in step 8 you will be quizzed (yes/no) about each new option.

Let me state up front: I do not understand half of what they are talking about. If I'm curious, I press ? and a few lines of explanation appear. I'm often still confused about what they are asking. At the end they usually include a newbie line which says something like, "If you don't know what we are talking about, press Y". I press Y :)

If in doubt, it has been my experience that just pressing return (thus getting the default choice) through the copious questions will do no harm. At worst, a piece of hardware might not work because I forgot to compile the right module.

Ah yes, modules: Modules are like clothes for your kernel. It can put them on or take them off. Some questions are not yes/no questions, they are yes/module/no questions. If you press m for module, the kernel will compile the requested feature as a module. This allows your kernel to be smaller, as it only has to load a module as directed at boot or when it is needed. Hard drive space is abundant compared to RAM, so it is good to let modules sit around on the hard drive when not needed and only load them into the kernel (and RAM) when needed.

So when you get to step 8 (the 'make oldconfig' line) the computer will start asking you a bunch of configuration questions. It's safe to press return through all of them -- at least to my knowledge -- that's what I do and it seems to work.

Step 9 gives you a second whack at the same questions now in graphical form. Try make xconfig.
Here you get to see all the options in a tree diagram. There are little boxes next to the options. A check means yes (obviously), blank means no, and a dot means compile as a module (maybe not so obvious).

In the left panel, under Power management options you will see ACPI. There should be a check mark in the box. In the panel on the upper right there are more config options. The only one that I see that really looks promising is 'Debug Statements' When you selected Debug Statements, an additional option underneath it will appear entitled "... ACPI function tracing". Since we're trying all we can to debug an ACPI question, I don't think it would hurt to enable this one too. Once we figure out how to fix the problem we can compile a new kernel without the debug statements (if you wish). 

Go to File->Save to save your new config file. 

Step 10 compiles your kernel. It will probably take the computer 30mins--1hr to compile. 

Step 10 installs the kernel. It will make the new kernel the default boot option! If for any reason the new kernel does not work and you want to go back to your current setup, reboot and press escape to get to the GRUB boot menu. You'll find the old boot options there. I can tell you (or you can edit /boot/grub/menu.lst) if you want to change the default.

When booting a new kernel there is the possibility that some piece of hardware that used to work no longer works. (My X display became lo-res because I needed to reinstall nvidia drivers). 

Don't panic. Slow down, take good notes on everything you do, every command you type. There is almost always a way to get back to "normal" and eventually to improve things (with the right config options), but it can be a bumpy ride, and it might seem to get worse before it gets better.

Good luck.

---

### Post by jakelute on 2008-05-02
Many many thanks for this!
It may be a few days before you hear from me again.....

---

### Post by unutbu on 2008-05-02
I hope this gets to you before you start. It looks like master_kernel also wrote a program called KernelCheck to automate much of the process:

[http://ubuntuforums.org/showthread.php?t=618563&highlight=KernelCheck](http://ubuntuforums.org/showthread.php?t=618563&highlight=KernelCheck)

---

### Post by jakelute on 2008-05-02
Hey, that's useful! I hadn't started yet. Things have got a bit busy at home, and it may be a couple of days before I start. But when I do, I'll start with that.
Thanks again. Will report back. Fingers crossed!

---

### Post by unutbu on 2008-05-02
Okay, best of luck!

---

### Post by jakelute on 2008-05-03
Compiled kernel (2.6.25.1) using KernelCheck --
rebooted -- message "decompressing Linux" followed by "booting kernel" (or something like that) -- normal quiet splash, but with some disturbances in the graphics (stray bits of colour) -- then briefly the usual tan colours, followed by black screen, followed by a blank white screen, and nothing more -- pressed restart button a couple of times, and got more or less the same thing every time, including the message about "decompressing Linux" -- some variation each time -- one time I got a red screen with some white stripes....
Did it three times. Gave up. Rebooted with previous kernel.
Is it a graphics thing?

---

### Post by jakelute on 2008-05-04
Further update:

I've managed to get it going, by disabling the ATI proprietary graphics card driver.
But....
a) no sound card detected (I imagine that's not to difficult to fix)
b) the freezes are still happening!

Meanwhile, the other day I did a little experiment: I installed Mandriva, and it works out of the box for me, with no freezes (yet), and just one little screen resolution problem that I could probably resolve eventually.

I much prefer the look and feel of Ubuntu, but what do you think? Is it time to move on? I've invested a lot of time and energy on this, and I'd be sorry to move on, but.....

Or are there further experiments I could do? The only one I can think of is flashing the BIOS

---

### Post by jakelute on 2008-05-04
PS I'm logged in now with the new kernel, but with a funny screen resolution and no sound, and with acpi=off

---

### Post by unutbu on 2008-05-04
Wow! That's great news. I would keep running Mandriva long enough to build confidence that there is no freezing problem there. You may end up liking it enough that you'd be happy switching over. 

Or, to stick with Ubuntu, *if* Mandriva really does not freeze, then I have a lot of hope that by comparing how Mandriva does certain things with Ubuntu, we should be able to get Ubuntu working properly.

Also, in an attempt to find out more about where the original freezes are coming from, would you try the following:

Since the new kernel was compiled with ACPI debugging on,reboot without the kernel option "acpi=off", wait for a freeze, and then do 
```
grep ACPI /var/log/* | grep "May  4" > acpi.log
dmesg | grep ACPI >> acpi.log

```

The output of the above commands will be in a file called acpi.log. Please post acpi.log either as an attachment or in a post. If you put the contents in a post, select the contents and then press the pound sign button (#) above the text field to format it nicely.

---

### Post by jakelute on 2008-05-04
Hi Unutbu,
I've got an acpi.log as you requested. It's so long that when I paste it into a reply, it won't send. I can't attach it, because .log is not a valid extension for attachments in posts to this forum.

So here is a tiny fraction of the log. I'll be more than happy to email you the whole thing privately if you like.

The freeze occured at 22:04:48 today (4 May 2008).

This is the first little bit of the log.



```


/var/log/debug:May  4 08:37:22 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/debug:May  4 08:37:22 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/debug:May  4 08:37:22 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/debug:May  4 08:37:22 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/debug:May  4 08:37:22 jake kernel: [   19.138091] ACPI: EC: Look up EC in DSDT
/var/log/debug:May  4 08:37:22 jake kernel: [   19.148593] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/debug:May  4 08:37:22 jake kernel: [   19.148811] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/debug:May  4 08:37:22 jake kernel: [   19.148940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/debug:May  4 10:59:23 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/debug:May  4 10:59:23 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/debug:May  4 10:59:23 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/debug:May  4 10:59:23 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/debug:May  4 10:59:23 jake kernel: [    0.258413] ACPI: EC: Look up EC in DSDT
/var/log/debug:May  4 10:59:23 jake kernel: [    0.280299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/debug:May  4 10:59:23 jake kernel: [    0.280680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/debug:May  4 10:59:23 jake kernel: [    0.280912] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/debug:May  4 13:36:16 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/debug:May  4 13:36:16 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/debug:May  4 13:36:16 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/debug:May  4 13:36:16 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/debug:May  4 13:36:16 jake kernel: [    0.258357] ACPI: EC: Look up EC in DSDT
/var/log/debug:May  4 13:36:16 jake kernel: [    0.280284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/debug:May  4 13:36:16 jake kernel: [    0.280664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/debug:May  4 13:36:16 jake kernel: [    0.280895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/debug:May  4 13:52:19 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/debug:May  4 13:52:19 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/debug:May  4 13:52:19 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/debug:May  4 13:52:19 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/debug:May  4 13:52:19 jake kernel: [    0.258391] ACPI: EC: Look up EC in DSDT
/var/log/debug:May  4 13:52:19 jake kernel: [    0.280204] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/debug:May  4 13:52:19 jake kernel: [    0.280583] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/debug:May  4 13:52:19 jake kernel: [    0.280814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/debug:May  4 13:53:41 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/debug:May  4 13:53:41 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/debug:May  4 13:53:41 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/debug:May  4 13:53:41 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/debug:May  4 13:53:41 jake kernel: [   18.527581] ACPI: EC: Look up EC in DSDT
/var/log/debug:May  4 13:53:41 jake kernel: [   18.538105] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/debug:May  4 13:53:41 jake kernel: [   18.538324] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/debug:May  4 13:53:41 jake kernel: [   18.538452] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/debug:May  4 13:55:43 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/debug:May  4 13:55:43 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/debug:May  4 13:55:43 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/debug:May  4 13:55:43 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/debug:May  4 13:55:43 jake kernel: [    0.258394] ACPI: EC: Look up EC in DSDT
/var/log/debug:May  4 13:55:43 jake kernel: [    0.280210] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/debug:May  4 13:55:43 jake kernel: [    0.280589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/debug:May  4 13:55:43 jake kernel: [    0.280821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/debug:May  4 13:58:07 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/debug:May  4 13:58:07 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/debug:May  4 13:58:07 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/debug:May  4 13:58:07 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/debug:May  4 13:58:07 jake kernel: [    0.258380] ACPI: EC: Look up EC in DSDT
/var/log/debug:May  4 13:58:07 jake kernel: [    0.280188] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/debug:May  4 13:58:07 jake kernel: [    0.280568] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/debug:May  4 13:58:07 jake kernel: [    0.280800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/debug:May  4 14:53:42 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/debug:May  4 14:53:42 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/debug:May  4 14:53:42 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/debug:May  4 14:53:42 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/debug:May  4 14:53:42 jake kernel: [    0.258343] ACPI: EC: Look up EC in DSDT
/var/log/debug:May  4 14:53:42 jake kernel: [    0.280239] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/debug:May  4 14:53:42 jake kernel: [    0.280619] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/debug:May  4 14:53:42 jake kernel: [    0.280850] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/debug:May  4 17:04:05 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/debug:May  4 17:04:05 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/debug:May  4 17:04:05 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/debug:May  4 17:04:05 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/debug:May  4 17:04:05 jake kernel: [    0.258376] ACPI: EC: Look up EC in DSDT
/var/log/debug:May  4 17:04:05 jake kernel: [    0.280233] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/debug:May  4 17:04:05 jake kernel: [    0.280614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/debug:May  4 17:04:05 jake kernel: [    0.280845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/debug:May  4 22:04:06 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/debug:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/debug:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/debug:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/debug:May  4 22:04:06 jake kernel: [    0.258388] ACPI: EC: Look up EC in DSDT
/var/log/debug:May  4 22:04:06 jake kernel: [    0.280203] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/debug:May  4 22:04:06 jake kernel: [    0.280582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/debug:May  4 22:04:06 jake kernel: [    0.280814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F87E0 checksum 0
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: RSDP 000F87E0, 0014 (r0 RS400 )
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: RSDT 3BEF3040, 0038 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: FACP 3BEF30C0, 0074 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: DSDT 3BEF3180, 416F (r1 RS400  AWRDACPI     1000 MSFT  100000E)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: FACS 3BEF0000, 0040
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: MCFG 3BEF7440, 003C (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: APIC 3BEF7340, 0084 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: SSDT 3BEF74C0, 019E (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: SSDT 3BEF7950, 022A (r1  PmRef    CpuPm     3000 INTL 20041203)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/kern.log:May  4 08:37:22 jake kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
```


Here is the very last little bit:


```


/var/log/syslog.0:May  4 08:37:22 jake kernel: [   30.347862] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
/var/log/syslog.0:May  4 08:37:22 jake kernel: [   30.462774] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
/var/log/syslog.0:May  4 08:37:22 jake kernel: [   31.457371] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 20
/var/log/syslog.0:May  4 08:37:22 jake kernel: [   32.081559] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 16
/var/log/syslog.0:May  4 08:37:22 jake kernel: [   38.549042] ACPI: Power Button (FF) [PWRF]
/var/log/syslog.0:May  4 08:37:22 jake kernel: [   38.576977] ACPI: Power Button (CM) [PWRB]
/var/log/syslog.0:May  4 08:37:22 jake kernel: [   39.962895] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
/var/log/syslog.0:May  4 08:37:26 jake kernel: [   47.148849] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 21
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
[    0.000000] ACPI: RSDP 000F87E0, 0014 (r0 RS400 )
[    0.000000] ACPI: RSDT 3BEF3040, 0038 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3BEF30C0, 0074 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3BEF3180, 416F (r1 RS400  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BEF0000, 0040
[    0.000000] ACPI: MCFG 3BEF7440, 003C (r1 RS400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3BEF7340, 0084 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 3BEF74C0, 019E (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[    0.000000] ACPI: SSDT 3BEF7950, 022A (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.101439] ACPI: Core revision 20070126
[    0.112961]  tbxface-0598 [02] tb_load_namespace     : ACPI Tables successfully acquired
[    0.116014] evxfevnt-0091 [02] enable                : Transition to ACPI mode successful
[    0.252782] ACPI: bus type pci registered
[    0.258388] ACPI: EC: Look up EC in DSDT
[    0.270200] ACPI: Interpreter enabled
[    0.270203] ACPI: (supports S0 S1 S4 S5)
[    0.270225] ACPI: Using IOAPIC for interrupt routing
[    0.278495] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.280203] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.280582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.280814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.311514] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.311703] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.312076] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.312264] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.312451] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11)
[    0.312636] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.312823] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
[    0.313011] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *10 11)
[    0.313330] pnp: PnP ACPI init
[    0.313338] ACPI: bus type pnp registered
[    0.318835] pnp: PnP ACPI: found 13 devices
[    0.318837] ACPI: ACPI bus type pnp unregistered
[    0.318841] PnPBIOS: Disabled by ACPI PNP
[    0.319157] PCI: Using ACPI for IRQ routing
[   12.994850] ACPI: PNP0C0B:00 is registered as cooling_device0
[   12.994858] ACPI: Fan [FAN] (on)
[   13.287364] ACPI: ACPI0007:00 is registered as cooling_device1
[   13.287664] ACPI: SSDT 3BEF78C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[   13.287982] ACPI: ACPI0007:01 is registered as cooling_device2
[   13.290298] ACPI: LNXTHERM:01 is registered as thermal_zone0
[   13.290541] ACPI: Thermal Zone [THRM] (40 C)
[   13.835736] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 23
[   14.470936] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   15.084447] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   16.099446] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   16.218360] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   16.386258] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   16.819789] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 22 (level, low) -> IRQ 22
[   16.561434] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 20
[   22.477524] ACPI: Power Button (FF) [PWRF]
[   22.541493] ACPI: Power Button (CM) [PWRB]
```

---

### Post by jakelute on 2008-05-04
Here's another bit from later on in the log which I assume is relevant because it's from 22:04
```

/var/log/kern.log:May  4 21:33:44 jake kernel: [   23.959165] ACPI: Interpreter disabled.
/var/log/kern.log:May  4 21:33:44 jake kernel: [   23.959290] pnp: PnP ACPI: disabled
/var/log/kern.log:May  4 22:01:57 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
/var/log/kern.log:May  4 22:01:57 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
/var/log/kern.log:May  4 22:01:57 jake kernel: [   34.013584] ACPI: Interpreter disabled.
/var/log/kern.log:May  4 22:01:57 jake kernel: [   34.013709] pnp: PnP ACPI: disabled
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: RSDP 000F87E0, 0014 (r0 RS400 )
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: RSDT 3BEF3040, 0038 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: FACP 3BEF30C0, 0074 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: DSDT 3BEF3180, 416F (r1 RS400  AWRDACPI     1000 MSFT  100000E)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: FACS 3BEF0000, 0040
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: MCFG 3BEF7440, 003C (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: APIC 3BEF7340, 0084 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: SSDT 3BEF74C0, 019E (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: SSDT 3BEF7950, 022A (r1  PmRef    CpuPm     3000 INTL 20041203)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.101439] ACPI: Core revision 20070126
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.112961]  tbxface-0598 [02] tb_load_namespace     : ACPI Tables successfully acquired
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.116014] evxfevnt-0091 [02] enable                : Transition to ACPI mode successful
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.252782] ACPI: bus type pci registered
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.258388] ACPI: EC: Look up EC in DSDT
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.270200] ACPI: Interpreter enabled
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.270203] ACPI: (supports S0 S1 S4 S5)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.270225] ACPI: Using IOAPIC for interrupt routing
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.278495] ACPI: PCI Root Bridge [PCI0] (0000:00)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.280203] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.280582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.280814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.311514] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.311703] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.312076] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.312264] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.312451] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.312636] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.312823] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.313011] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *10 11)
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.313330] pnp: PnP ACPI init
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.313338] ACPI: bus type pnp registered
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.318835] pnp: PnP ACPI: found 13 devices
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.318837] ACPI: ACPI bus type pnp unregistered
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.318841] PnPBIOS: Disabled by ACPI PNP
/var/log/kern.log:May  4 22:04:06 jake kernel: [    0.319157] PCI: Using ACPI for IRQ routing
/var/log/kern.log:May  4 22:04:06 jake kernel: [   12.994850] ACPI: PNP0C0B:00 is registered as cooling_device0
/var/log/kern.log:May  4 22:04:06 jake kernel: [   12.994858] ACPI: Fan [FAN] (on)
/var/log/kern.log:May  4 22:04:06 jake kernel: [   13.287364] ACPI: ACPI0007:00 is registered as cooling_device1
/var/log/kern.log:May  4 22:04:06 jake kernel: [   13.287664] ACPI: SSDT 3BEF78C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
/var/log/kern.log:May  4 22:04:06 jake kernel: [   13.287982] ACPI: ACPI0007:01 is registered as cooling_device2
/var/log/kern.log:May  4 22:04:06 jake kernel: [   13.290298] ACPI: LNXTHERM:01 is registered as thermal_zone0
/var/log/kern.log:May  4 22:04:06 jake kernel: [   13.290541] ACPI: Thermal Zone [THRM] (40 C)
/var/log/kern.log:May  4 22:04:06 jake kernel: [   13.835736] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 23
/var/log/kern.log:May  4 22:04:06 jake kernel: [   14.470936] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
/var/log/kern.log:May  4 22:04:06 jake kernel: [   15.084447] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
/var/log/kern.log:May  4 22:04:06 jake kernel: [   16.099446] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
/var/log/kern.log:May  4 22:04:06 jake kernel: [   16.218360] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
/var/log/kern.log:May  4 22:04:06 jake kernel: [   16.386258] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
/var/log/kern.log:May  4 22:04:06 jake kernel: [   16.819789] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 22 (level, low) -> IRQ 22
/var/log/kern.log:May  4 22:04:06 jake kernel: [   16.561434] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 20
/var/log/kern.log:May  4 22:04:06 jake kernel: [   22.477524] ACPI: Power Button (FF) [PWRF]
/var/log/kern.log:May  4 22:04:06 jake kernel: [   22.541493] ACPI: Power Button (CM) [PWRB]
/var/log/messages:May  4 08:37:22 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
/var/log/messages:May  4 08:37:22 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
```

and another section from still later in the log:

```
/var/log/messages:May  4 21:33:44 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
/var/log/messages:May  4 21:33:44 jake kernel: [   23.959165] ACPI: Interpreter disabled.
/var/log/messages:May  4 21:33:44 jake kernel: [   23.959290] pnp: PnP ACPI: disabled
/var/log/messages:May  4 22:01:57 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
/var/log/messages:May  4 22:01:57 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
/var/log/messages:May  4 22:01:57 jake kernel: [   34.013584] ACPI: Interpreter disabled.
/var/log/messages:May  4 22:01:57 jake kernel: [   34.013709] pnp: PnP ACPI: disabled
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: RSDP 000F87E0, 0014 (r0 RS400 )
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: RSDT 3BEF3040, 0038 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: FACP 3BEF30C0, 0074 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: DSDT 3BEF3180, 416F (r1 RS400  AWRDACPI     1000 MSFT  100000E)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: FACS 3BEF0000, 0040
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: MCFG 3BEF7440, 003C (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: APIC 3BEF7340, 0084 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: SSDT 3BEF74C0, 019E (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: SSDT 3BEF7950, 022A (r1  PmRef    CpuPm     3000 INTL 20041203)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
/var/log/messages:May  4 22:04:06 jake kernel: [    0.101439] ACPI: Core revision 20070126
/var/log/messages:May  4 22:04:06 jake kernel: [    0.112961]  tbxface-0598 [02] tb_load_namespace     : ACPI Tables successfully acquired
/var/log/messages:May  4 22:04:06 jake kernel: [    0.116014] evxfevnt-0091 [02] enable                : Transition to ACPI mode successful
/var/log/messages:May  4 22:04:06 jake kernel: [    0.252782] ACPI: bus type pci registered
/var/log/messages:May  4 22:04:06 jake kernel: [    0.270200] ACPI: Interpreter enabled
/var/log/messages:May  4 22:04:06 jake kernel: [    0.270203] ACPI: (supports S0 S1 S4 S5)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.270225] ACPI: Using IOAPIC for interrupt routing
/var/log/messages:May  4 22:04:06 jake kernel: [    0.278495] ACPI: PCI Root Bridge [PCI0] (0000:00)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.311514] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/messages:May  4 22:04:06 jake kernel: [    0.311703] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/messages:May  4 22:04:06 jake kernel: [    0.312076] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/messages:May  4 22:04:06 jake kernel: [    0.312264] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/messages:May  4 22:04:06 jake kernel: [    0.312451] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.312636] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/messages:May  4 22:04:06 jake kernel: [    0.312823] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.313011] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *10 11)
/var/log/messages:May  4 22:04:06 jake kernel: [    0.313330] pnp: PnP ACPI init
/var/log/messages:May  4 22:04:06 jake kernel: [    0.313338] ACPI: bus type pnp registered
/var/log/messages:May  4 22:04:06 jake kernel: [    0.318835] pnp: PnP ACPI: found 13 devices
/var/log/messages:May  4 22:04:06 jake kernel: [    0.318837] ACPI: ACPI bus type pnp unregistered
/var/log/messages:May  4 22:04:06 jake kernel: [    0.318841] PnPBIOS: Disabled by ACPI PNP
/var/log/messages:May  4 22:04:06 jake kernel: [    0.319157] PCI: Using ACPI for IRQ routing
/var/log/messages:May  4 22:04:06 jake kernel: [   12.994850] ACPI: PNP0C0B:00 is registered as cooling_device0
/var/log/messages:May  4 22:04:06 jake kernel: [   12.994858] ACPI: Fan [FAN] (on)
/var/log/messages:May  4 22:04:06 jake kernel: [   13.287364] ACPI: ACPI0007:00 is registered as cooling_device1
/var/log/messages:May  4 22:04:06 jake kernel: [   13.287664] ACPI: SSDT 3BEF78C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
/var/log/messages:May  4 22:04:06 jake kernel: [   13.287982] ACPI: ACPI0007:01 is registered as cooling_device2
/var/log/messages:May  4 22:04:06 jake kernel: [   13.290298] ACPI: LNXTHERM:01 is registered as thermal_zone0
/var/log/messages:May  4 22:04:06 jake kernel: [   13.290541] ACPI: Thermal Zone [THRM] (40 C)
/var/log/messages:May  4 22:04:06 jake kernel: [   13.835736] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 23
/var/log/messages:May  4 22:04:06 jake kernel: [   14.470936] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
/var/log/messages:May  4 22:04:06 jake kernel: [   15.084447] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
/var/log/messages:May  4 22:04:06 jake kernel: [   16.099446] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
/var/log/messages:May  4 22:04:06 jake kernel: [   16.218360] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
/var/log/messages:May  4 22:04:06 jake kernel: [   16.386258] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
/var/log/messages:May  4 22:04:06 jake kernel: [   16.819789] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 22 (level, low) -> IRQ 22
/var/log/messages:May  4 22:04:06 jake kernel: [   16.561434] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 20
/var/log/messages:May  4 22:04:06 jake kernel: [   22.477524] ACPI: Power Button (FF) [PWRF]
/var/log/messages:May  4 22:04:06 jake kernel: [   22.541493] ACPI: Power Button (CM) [PWRB]
/var/log/syslog:May  4 10:59:23 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
```

and another:```


/var/log/syslog:May  4 21:33:44 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
/var/log/syslog:May  4 21:33:44 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
/var/log/syslog:May  4 21:33:44 jake kernel: [   23.959165] ACPI: Interpreter disabled.
/var/log/syslog:May  4 21:33:44 jake kernel: [   23.959290] pnp: PnP ACPI: disabled
/var/log/syslog:May  4 22:01:57 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
/var/log/syslog:May  4 22:01:57 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
/var/log/syslog:May  4 22:01:57 jake kernel: [   34.013584] ACPI: Interpreter disabled.
/var/log/syslog:May  4 22:01:57 jake kernel: [   34.013709] pnp: PnP ACPI: disabled
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: RSDP 000F87E0, 0014 (r0 RS400 )
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: RSDT 3BEF3040, 0038 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: FACP 3BEF30C0, 0074 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: DSDT 3BEF3180, 416F (r1 RS400  AWRDACPI     1000 MSFT  100000E)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: FACS 3BEF0000, 0040
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: MCFG 3BEF7440, 003C (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: APIC 3BEF7340, 0084 (r1 RS400  AWRDACPI 42302E31 AWRD        0)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: SSDT 3BEF74C0, 019E (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: SSDT 3BEF7950, 022A (r1  PmRef    CpuPm     3000 INTL 20041203)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IRQ0 used by override.
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IRQ2 used by override.
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] ACPI: IRQ9 used by override.
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.101439] ACPI: Core revision 20070126
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.112961]  tbxface-0598 [02] tb_load_namespace     : ACPI Tables successfully acquired
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.116014] evxfevnt-0091 [02] enable                : Transition to ACPI mode successful
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.252782] ACPI: bus type pci registered
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.258388] ACPI: EC: Look up EC in DSDT
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.270200] ACPI: Interpreter enabled
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.270203] ACPI: (supports S0 S1 S4 S5)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.270225] ACPI: Using IOAPIC for interrupt routing
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.278495] ACPI: PCI Root Bridge [PCI0] (0000:00)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.280203] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.280582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.280814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.311514] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.311703] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.312076] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.312264] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.312451] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.312636] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.312823] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.313011] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *10 11)
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.313330] pnp: PnP ACPI init
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.313338] ACPI: bus type pnp registered
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.318835] pnp: PnP ACPI: found 13 devices
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.318837] ACPI: ACPI bus type pnp unregistered
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.318841] PnPBIOS: Disabled by ACPI PNP
/var/log/syslog:May  4 22:04:06 jake kernel: [    0.319157] PCI: Using ACPI for IRQ routing
/var/log/syslog:May  4 22:04:06 jake kernel: [   12.994850] ACPI: PNP0C0B:00 is registered as cooling_device0
/var/log/syslog:May  4 22:04:06 jake kernel: [   12.994858] ACPI: Fan [FAN] (on)
/var/log/syslog:May  4 22:04:06 jake kernel: [   13.287364] ACPI: ACPI0007:00 is registered as cooling_device1
/var/log/syslog:May  4 22:04:06 jake kernel: [   13.287664] ACPI: SSDT 3BEF78C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
/var/log/syslog:May  4 22:04:06 jake kernel: [   13.287982] ACPI: ACPI0007:01 is registered as cooling_device2
/var/log/syslog:May  4 22:04:06 jake kernel: [   13.290298] ACPI: LNXTHERM:01 is registered as thermal_zone0
/var/log/syslog:May  4 22:04:06 jake kernel: [   13.290541] ACPI: Thermal Zone [THRM] (40 C)
/var/log/syslog:May  4 22:04:06 jake kernel: [   13.835736] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 23
/var/log/syslog:May  4 22:04:06 jake kernel: [   14.470936] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
/var/log/syslog:May  4 22:04:06 jake kernel: [   15.084447] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
/var/log/syslog:May  4 22:04:06 jake kernel: [   16.099446] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
/var/log/syslog:May  4 22:04:06 jake kernel: [   16.218360] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
/var/log/syslog:May  4 22:04:06 jake kernel: [   16.386258] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
/var/log/syslog:May  4 22:04:06 jake kernel: [   16.819789] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 22 (level, low) -> IRQ 22
/var/log/syslog:May  4 22:04:06 jake kernel: [   16.561434] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 20
/var/log/syslog:May  4 22:04:06 jake kernel: [   22.477524] ACPI: Power Button (FF) [PWRF]
/var/log/syslog:May  4 22:04:06 jake kernel: [   22.541493] ACPI: Power Button (CM) [PWRB]
/var/log/syslog.0:May  4 08:37:22 jake kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
/var/log/syslog.0:May  4 08:37:22 jake kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
```

---

### Post by jakelute on 2008-05-06
Hi again, Unutbu --

I've been using Mandriva for a couple of days, and it really does work extremely well with no need for any adjustments, so I'll probably stick with it for the time being.

I look at it this way: Ubuntu worked "out of the box" on my wife's Dell laptop, but has been very problematic on my system. Mandriva works "out of the box" on my system with none of the problems I had in Ubuntu. It seems like an uphill struggle, so I'm giving in and sticking with Mandriva for the moment, just because it's been so time-consuming to try to resolve my problems with Ubuntu (though I've learned a lot!). 

However, having said that, two further thoughts come to mind:

1. If these problems ever could be resolved, I'd rather be with Ubuntu, which has been my first introduction to Linux, and a very positive one overall.

2. All this work that you and I have done to try to make my system work: how can I put it to use for the benefit of the Ubuntu community? Shall I file a bug report with Ubuntu even though I'm now using Mandriva? If so, I might need to consult you about what exactly to put in it.

Meanwhile, many many thanks for all your invaluable and generous help. I am very grateful.

All best,

J

---

### Post by unutbu on 2008-05-06
Hi Jakelute,

Thank you for maintaining such a positive attitude about Ubuntu despite this very daunting problem. I wish I had more knowledge and could have helped you more practically.  Your patience and tenacity are the true heroes of this story.

I suggest we let our forum posts stand in place of a formal bug report. I don't think we've drilled down far enough to file a really good bug report -- one that a developer could readily translate into a fix. Hopefully, the threads will give someone else the benefit of our experience if they find themselves in a similar fix.

Sticking with Mandriva for the present makes a lot of sense. There is a lot of value in just being able to get things done! Moreover, by comparing your Mandriva system with your wife's Ubuntu, you'll gain perspective on what makes all Linux systems the same and what parts a distro brings to the table. I think you'll find that the similarities far outweigh the differences.

Until our paths meet again,
Unutbu

---

### Post by jakelute on 2008-05-06
Once again, I want to thank you for giving so much of you time, and for being so patient. I've learned a lot from all of this.

Very best wishes,

Jake

---

### Post by jakelute on 2008-05-11
Hello again, Unutbu (if you happen to see this!).
This is probably a stupid question, but....my freeze problem -- would it make any difference to try Kubuntu, or is it irrelevant to the problem whether I'm using Gnome or KDE?
Thanks!

---

### Post by unutbu on 2008-05-11
Hi Jakelute, nice to hear from you. Hope all's well.
The only honest answer I can give to your question is... I don't know. I don't want to get your hopes up, but it might be worth a shot. (I was surprised that Mandrake worked out of the box and I'm still wondering what the difference is. If Mandrake works, why not Kubuntu?) If you try Kubuntu, please keep me posted on how it goes.

---

### Post by jakelute on 2008-05-11
OK, thanks. I'll think about it for a day or two first, because I'm not sure I can face the hassle. But I must say I'm curious to see what happens!

---

### Post by jakelute on 2008-05-16
Four days later: I spent a day or so running Kubuntu, without any freezes. But I made the mistake of using the KDE 4 version, which had all sorts of things in it which didn't work very well on my system. Clearly, I should try the more stable Kubuntu with KDE 3 on it. But it seemed quite encouraging that there were no crashes in a day of trying it out. This encourages me to experiment a bit more with Kubuntu (with KDE 3). Will report back if I get a chance to do this.
Meanwhile, I must say that Mandriva's been extremely good, if less elegant.
All best, jake

---

### Post by spiderbatdad on 2008-05-16
lapic pci=routeirq
Goes back to original issue.

---

### Post by jakelute on 2008-05-16
thank you for that

---

### Post by unutbu on 2008-06-14
Jake, what was the result of the Kubuntu with KDE 3 test?

---

### Post by jakelute on 2008-06-14
I must admit that I haven't tried it yet. It's been a busy time and I have yet to do this. I will at some point! Will report back!
All best, Jake

---

### Post by unutbu on 2008-06-15
Since Mandriva works and Ubuntu 8.04 didn't, I suspect the difference is in the version of the kernel -- in particular the configuration options used when the kernel was compiled. 

If you want to get Ubuntu working and are up for a bit more work, you could try the following:

1) While in Mandriva, run 
```
uname -r
``` This will give us the version of the kernel Mandriva uses.
2) Make a partition for Ubuntu.
3) Install Ubuntu on that partition
4) Boot up in Ubuntu.
5) Download the linux kernel source code (same version that Mandriva uses). Unpack the kernel in /usr/src/linux
6) Mount the Mandriva partition while in Ubuntu
7) Copy Mandriva's /boot/config to /usr/src/linux.
8) Use Mandriva's config file to compile a kernel for Ubuntu. Using the directions at [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) to do the compiling.)
9) Install the kernel, and see if it works.

I realize it would take some time to do, and I'd totally understand if you'd rather not go through all this. Anyway, I just thought I'd mention it.

---

### Post by jakelute on 2008-06-16
Hi unutbu,
Thanks very much for this sensible suggestion. 
I'm not very confident about finding the time to go through this in the near future. I'm having to take an if-it-ain't-broke-don't-fix-it approach at the moment. However, having said that, I would very much like to return to Ubuntu at some point, and will keep your suggestion in mind for a rainy day.
By the way, here's the result of uname -r in Mandriva: 2.6.24.5-desktop586-2mnb

Thanks and all best,

jake

---

### Post by jakelute on 2008-06-16
PS
Also want to remind you that I had the problem of freezing in the two versions of Ubuntu prior to 8.04. Never tried anything older than that.

---

### Post by unutbu on 2008-06-16
Yes, that's very reasonable, especially since I'm not certain it would work.

Best regards,
unutbu

---

### Post by jakelute on 2008-07-20
Hi Unutbu,

Long time no speak! I've finally had a little time to install Kubuntu (KDE 3.5) in a dual boot with my existing Mandriva installation (which, by the way, is still working very well). The disc was error free and Kubuntu appeared to install fine, but when I boot in Kubuntu I end up endlessly stuck in the login screen! I'm typing the correct password and username and so on, but when I log on, I get a black screen for a moment, and then the login screen reappears. And so on! Is there a way to enable autologin using terminal mode so that I can see where there's a way past this problem? Only then will I be able to test Kubuntu and see if it works on this machine.

Many thanks!

Jake

---

### Post by unutbu on 2008-07-20
Hi Jake! Nice to hear from you.

When you get to the graphical login screen (gdm), login in, and then the screen goes black and then you are popped back to the login screen, it usually means there is an error in a configuration file in your home directory (maybe ~/.bashrc or ~/.profile).

Are you using your Mandriva home directory as your Kubuntu home directory?

Oh -- and to answer your question --
Press Ctrl-Alt-F2. This will take you to a text terminal. Login there, and then you can poke around in your system from the command-line.

You can also reboot, press ESC to get to the GRUB menu, select Recovery Mode. This will drop you to a root shell.

Edit: There is a way to enable autologin, 
but I don't know how to set that up...
Here is a page describing how to do it
[https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin)
but you'd need to be able to login to the graphical environment to set that up. LOL...

---

### Post by jakelute on 2008-07-20
Hi. Thanks for that. To answer your question, I think the answer is that in my Kubuntu installation (which is on a separate internal hard disk), there is a Home directory, which contains an empty folder called "Jake". If I understand your question correctly, that means that I do have a Kubuntu home directory, albeit empty at the moment.
As for getting past this little problem -- the only hope I can see is finding a way to enable autologin using terminal, since I'm stuck and unable to enter KDE at the moment. I must admit that there's little incentive to delve too deeply, as Mandriva is working so well, but it would be really nice to find out whether Kubuntu works well on this machine with KDE 3.5....
Is there a useful site somewhere which lists all the various commands that one can execute in terminal mode?
Many thanks!

---

### Post by unutbu on 2008-07-20
Here are some good resources on using the command-line:
[http://www.tldp.org/LDP/intro-linux/html/index.html](http://www.tldp.org/LDP/intro-linux/html/index.html)
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
> 
[M]y Kubuntu installation (which is on a separate internal hard disk), there is a Home directory, which contains an empty folder called "Jake"

When you installed Kubuntu, it should have asked you for a username. I suppose you supplied it with the name Jake. When this account is created a number of files and directories are automatically created in /home/Jake: .bashrc, .profile, Desktop, Documents, Examples, Music, Picures, etc. The directory /home/Jake should definitely not be completely empty. A completely empty directory might cause the symptom you describe however (black screen, then bounce back to gdm).

(1) To check if /home/Jake is really empty:
Boot to Kubuntu recovery mode. This will drop you to a root terminal prompt. Type
```
cd /home/Jake
ls -la

```
If it is completely empty you'll see
```
% ls -la
total 8
drwxr-xr-x  2 Jake Jake 4096 2008-07-20 16:22 .
drwxr-xr-x 10 Jake Jake 4096 2008-07-20 16:22 ..
```

otherwise, you'll see the files and directories that are present.
The 'a' flag in 'ls -la' tells the ls command to show files that begin with a dot like .bashrc. These are otherwise hidden by default, which can make you think a directory is empty when it really is not.

Please post the output of
```
ls -la
su Jake                  # Allows root to become Jake. 
id                       # shows what groups Jake belongs to
grep Jake /etc/passwd    # feel free to wipe out any personal info. 
```


The last command will allow us to check that the home directory and default shell has been set.

---

### Post by jakelute on 2008-07-20
Hi again. Many thanks for this! I was able to do all the things you asked me to, and I got all the information. Unfortunately, I've no way of copying it and pasting it into a post on this forum because I can't get into KDE! I can't even print it because the printer is not yet installed in Kubuntu. I can't print to pdf or ps either -- it won't let me. But one thing I found is that home/jake is not empty -- it's got various hidden files in it, including the ones you mentioned (though nothing that's not hidden -- i.e., no "documents", "pictures", "music", etc.).

All the other commands yielded results too, which -- short of copying them on a piece of paper by hand and retyping them -- I can't unfortunately share with you. It sound as if the last of the commands might have been the most important. Perhaps I'll just go back and get that one, and write it on a piece of paper and retype it. 

Other than that, can you think of a way in which I can get this information to you?

Thanks!

---

### Post by jakelute on 2008-07-20
PS I can view the Kubuntu home/jake folder in Mandriva, and its contents, by choosing "show hidden files" -- might that be the route to solving this problem?

---

### Post by jakelute on 2008-07-20
found a way to do it!
in terminal mode (after failsafe login), I went to help/get help online -- the konqueror browswer opened, and I visited the forum and pasted in the info below!


jake@jake:~$ ls -la
total 64
drwxr-xr-x 6 jake jake 4096 2008-07-20 22:40 .
drwxr-xr-x 3 root root 4096 2008-07-19 17:03 ..
-rw------- 1 jake jake 1470 2008-07-20 22:27 .bash_history
-rw-r--r-- 1 jake jake  220 2008-07-19 17:03 .bash_logout
-rw-r--r-- 1 jake jake 2940 2008-07-19 17:03 .bashrc
-rw-r--r-- 1 jake jake   51 2008-07-20 22:40 .DCOPserver_jake__0
lrwxrwxrwx 1 jake jake   30 2008-07-20 22:40 .DCOPserver_jake_:0 -> /home/jake/.DCOPserver_jake__0
-rw------- 1 jake jake   27 2008-07-20 22:40 .dmrc
-rw------- 1 jake jake  370 2008-07-20 22:40 .ICEauthority
drwx------ 3 jake jake 4096 2008-07-19 22:54 .kde
drwxr-xr-x 3 jake jake 4096 2008-07-19 22:57 .mcop
-rw------- 1 jake jake   31 2008-07-20 22:09 .mcoprc
drwx------ 3 jake jake 4096 2008-07-20 22:25 .openoffice.org2
-rw-r--r-- 1 jake jake  586 2008-07-19 17:03 .profile
drwxr-xr-x 2 jake jake 4096 2008-07-19 22:54 .qt
-rw-r--r-- 1 jake jake    0 2008-07-19 22:55 .sudo_as_admin_successful
-rw------- 1 jake jake  159 2008-07-20 22:40 .Xauthority
-rw------- 1 jake jake  138 2008-07-20 22:40 .xsession-errors
jake@jake:~$ su jake
Password:
jake@jake:~$ id
uid=1000(jake) gid=1000(jake) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),114(admin),1000(jake)
jake@jake:~$ grep jake /etc/passwd
jake:x:1000:1000:Jacob Heringman,,,:/home/jake:/bin/bash
jake@jake:~$

---

### Post by unutbu on 2008-07-20
Okay, great. Now please post the contents of Kubuntu's
/home/jake/.xsession-errors.

---

### Post by jakelute on 2008-07-21
Can you remind me what the command is to view the contents of a file? 
I can see the file when I'm logged into Mandriva, by visiting the home folder of my Kubuntu installation, and asking to see hidden files -- but I can't open it, copy it, or view its contents.
Thanks!

---

### Post by pmsumner on 2008-07-21
> **jakelute said:**
> Can you remind me what the command is to view the contents of a file? 
I can see the file when I'm logged into Mandriva, by visiting the home folder of my Kubuntu installation, and asking to see hidden files -- but I can't open it, copy it, or view its contents.
Thanks!

Using the command line:

```
cat /home/Jake/.xsession-errors
```

Should do what you want.

---

### Post by jakelute on 2008-07-21
Thank you very much, pmsumner -- I'll give it a try!

---

### Post by jakelute on 2008-07-21
Here's what I get:

```
jake@jake:~$ cat /home/jake/.xsession-errors
Xsession: X session started for jake at Mon Jul 21 11:11:35 BST 2008
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
kdecore (KProcess): WARNING: _attachPty() 10
```

---

### Post by jakelute on 2008-07-21
Tried three or four times and got the same thing. Tried a fifth time, and got this:

```

jake@jake:~$ cat /home/jake/.xsession-errors
Xsession: X session started for jake at Mon Jul 21 11:11:35 BST 2008
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
kdecore (KProcess): WARNING: _attachPty() 10
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
konqueror: WARNING: non-standard scrollIntoView() not implemented
jake@jake:~$  
```

Might it be an idea to try reinstalling once again?

Thanks.

---

### Post by unutbu on 2008-07-21
I have a feeling this might be Mandriva-jake's .xsession-errors.
So that we can give you the right command-line commands, I think we need some more background information. Please post

While in Mandriva, please run these commands, and post the output:
```
sudo fdisk -l
mount
id
```

---

### Post by jakelute on 2008-07-21
```
[jake@localhost ~]$ sudo fdisk -l
bash: sudo: command not found
[jake@localhost ~]$ mount
/dev/sda1 on / type ext3 (rw)
none on /proc type proc (rw)
/dev/sda6 on /home type ext3 (rw)
/dev/hda1 on /media/hd type ext3 (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
[jake@localhost ~]$ id
uid=500(jake) gid=500(jake) groups=500(jake)
[jake@localhost ~]$     

```

---

### Post by unutbu on 2008-07-21
```
[jake@localhost ~]$ sudo fdisk -l
bash: sudo: command not found
```

My mistake -- apparently Mandriva uses su, not sudo.
This line in the output of mount
```

/dev/hda1 on /media/hd type ext3 (rw)
```

shows Kubuntu is mounted at /media/hd.

Okay, now try
```

cat /media/hd/home/jake/.xsession-errors
```

---

### Post by jakelute on 2008-07-21
PS as far as I know, Mandriva is installed on /dev/sda6 and Kubuntu is installed on /dev/hda1 -- no, let me correct that: /dev/sda1 and /dev/sda6 have Mandriva on them (Mandriva subdived my 300 GB intenal HD into those two components, sda6 being very large and sda1 being very small (I guess the latter is the "system" and the former is all of my stuff?

To put this more simply, when I visit my media folder in Mandriva, I see three devices: 

1. /dev/hda1 -- this is where I installed Kubuntu, and it's a 120 GB internal HD (though it's here showing 117 GB)
2. /dev/sda6 showing as 307 GB
3. /dev/sda1  showing as 8.4 GB

No. 2 and 3 are both part of the 300-GB internal HD where I installed Mandriva

---

### Post by jakelute on 2008-07-21
```
[root@localhost jake]# cat /media/hd/home/jake/.xsession-errors
Xsession: X session started for jake at Mon Jul 21 11:11:35 BST 2008
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
kdecore (KProcess): WARNING: _attachPty() 10
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
konqueror: WARNING: non-standard scrollIntoView() not implemented
konqueror: WARNING: non-standard scrollIntoView() not implemented
kded: Fatal IO error: client killed
kdeinit: Fatal IO error: client killed
klauncher: Exiting on signal 15
klauncher: Fatal IO error: client killed

```

---

### Post by unutbu on 2008-07-21
Jake, I don't know what these errors mean:

```
kded: Fatal IO error: client killed
kdeinit: Fatal IO error: client killed
klauncher: Exiting on signal 15
klauncher: Fatal IO error: client killed
```

I've started google searching, but so far that's come up donuts. I'll continue doing research but I've got to warn you that right now I'm clueless.

Since I have no familiarity with KDE and this seems to be a KDE issue, perhaps you should start a new thread. There is a Beginner's team and Unanswered Posts team that do an amazing job of fielding questions posted in the Absolute Beginners section. I'll find your thread and try to chip in if I have something useful, but I'll try to wait so the Unanswered Posts team will find you first.

---

### Post by jakelute on 2008-07-21
OK, many thanks!
But what about trying a reinstall first, just to see if the same problems occur again?

---

### Post by unutbu on 2008-07-21
Well, since it's easy and it may work, I'd say... why not? Give it a try.

---

### Post by jakelute on 2008-07-21
I attempted a reinstall, and, for some reason, lost my Mandriva installation this time (unlike last time -- a mystery!). Luckily everything was backed up.
Now I've reinstalled Mandriva. The Kubuntu installation has exactly the same problem as before. I'm going to take a break from experimenting, as I'm getting busy again. But I'll pursue it further when I get time. As I say, the incentive isn't that great, as Mandriva is working well.
Thanks for all the help!

---

### Post by unutbu on 2008-07-21
> **jakelute said:**
> I attempted a reinstall, and, for some reason, lost my Mandriva installation
Oh my gosh! Heart attack city! Well, I'm really glad you had backups.

I usually feel the urge to take a nice long walk after something like that happens. 

Anyway, I completely agree that having a computer that works is the main goal, and since Mandriva satifies that criteria, then... that's great.

Nice hearing from you.
Happy journeys,
Unutbu.

---

### Post by jakelute on 2008-07-21
Thank you, and same to you!
No doubt the discussion will continue one day......

---

