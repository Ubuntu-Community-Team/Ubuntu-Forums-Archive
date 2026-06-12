---
title: "Terratec remote howto (Jaunty/Karmic/Lucid):"
date: 2010-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by bui_a on 2010-05-19
(Perhaps this guide also applies to other brands, Terratec is the only one I have tested.)

Having had a rather frustrating experience of getting my Terratec Cinergy-T XXS USB dvb-t adapter to work in Ubuntu Jaunty/Karmic, I decided to write this walkthrough for others in the same situation, hope you find it useful!



1. ```
user@host:~$ sudo aptitude install lirc lirc-x
```



2. ```
user@host:~$ sudo nano /etc/lirc/hardware.conf
```

insert:

	```
#Chosen Remote Control
	REMOTE="Custom"
	REMOTE_MODULES=""
	REMOTE_DRIVER="devinput"
	REMOTE_DEVICE="/dev/input/eventX"
	REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
	REMOTE_LIRCD_ARGS=""
```

	/dev/input/eventX should be renamed to the appropriate event on your 		system, you can find this by issuing the command:

	```
user@host:~$ ls -la /dev/input/by-path
```

	The relevant part of the output (event-ir) should look something 		like this:

	```
lrwxrwxrwx 1 root root   9 2009-10-03 17:09 pci-0000:00:02.1-event-ir -> ..event5
```

	so in this case the above would be:

	```
REMOTE_DEVICE="/dev/input/event5"
```

	Leave everything else as is




3. ```
user@host:~$ sudo nano /etc/lirc/lircd.conf
```
	
	Insert:	

	```
# Please make this file available to others
	# by sending it to <lirc@bartelmus.de>
	#
	# this config file was automatically generated
	# using lirc-0.8.2-CVS(dev/input) on Tue May  8 23:40:09 2007
	#
	# contributed by Heinrich Schwietering
	#
	# brand:Terratec_
	# model no. of remote control:
	# devices being controlled by this remote: Cinergy_Hybrid_t_USB_XS
	#

	begin remote

	  name  Cinergy_Hybrid_t_USB_XS
	  bits           16
	  eps            30
	  aeps          100

	  one             0     0
	  zero            0     0
	  pre_data_bits   16
	  pre_data       0x1
	  gap          135987
	  toggle_bit_mask 0x80000000

	      begin codes
		  onoff                    0x0074
		  home                     0x0066
		  dvdmenu                  0x008B
		  subtitles                0x0172
		  teletext                 0x0184
		  delete                   0x006F
		  1                        0x0002
		  2                        0x0003
		  3                        0x0004
		  4                        0x0005
		  5                        0x0006
		  6                        0x0007
		  7                        0x0008
		  8                        0x0009
		  9                        0x000A
		  0                        0x000B
		  av                       0x0182
		  ab                       0x00AD
		  tv                       0x0179
		  dvd                      0x0185
		  video                    0x0189
		  music                    0x0188
		  pic                      0x0177
		  up                       0x0067
		  down                     0x006C
		  left                     0x0069
		  right                    0x006A
		  ok                       0x0160
		  epg                      0x016D
		  info                     0x0166
		  back                     0x009E
		  vol+                     0x0073
		  vol-                     0x0072
		  play                     0x00CF
		  mute                     0x0071
		  ch+                      0x0192
		  ch-                      0x0193
		  red                      0x018E
		  green                    0x018F
		  yellow                   0x0190
		  blue                     0x0191
		  rec                      0x00A7
		  stop                     0x0080
		  pause                    0x0077
		  last                     0x019C
		  fr                       0x00A8
		  ff                       0x00D0
		  next                     0x0197
	      end codes

	end remote
```

	(NB: some of the key codes are different for the older versions of 		this DVB-set)




4. Make the file dvbir.conf: ```
user@host:~$ sudo nano /etc/modprobe.d/dvbir.conf
```

	Insert:

	```
options dvb_usb_dib0700 dvb_usb_dib0700_ir_proto=0

	options dvb_usb_dib0700 force_lna_activation=1
```

	(NB: the line "options dvb_usb_dib0700 force_lna_activation=1" is 		not strictly related to the remote, but rather to the actually dvb 		signal, whether it is necessary or not may vary.



5. Restart LIRC: ```
user@host:~$ sudo /etc/init.d/lirc restart
```



6. run 		

	```
user@host:~$ irw
```

to test whether you receive any signals from your remote. In some cases, including mine, two signals will be received every time you press a button. In some programs (MythTV, for example) this can be mitigated via the .lircrc, but in other sadly not. I am not sure what the cause of the problem is, but it might be a firmware bug or similar. Luckily, in some apps, this is not a problem, and XBMC/Boxee will act normally despite the double signals.



Concluding notes: To actually make your remote useful in X (i.e. gnome/KDE/etc.) you should create a .lircrc file in your home directory and run a irxevent daemon which will allow you to map various keys to the remote buttons. There are plenty of websites that demonstrate how this is done, so have at it!

---

### Post by calande on 2010-05-23
Hi  there,

I'm trying to make my Terratec remote work, but I don't know what event # to use:
> ls -la /dev/input/by-path
total 0
drwxr-xr-x 2 root root 120 2010-05-23 12:05 .
drwxr-xr-x 4 root root 280 2010-05-23 12:05 ..
lrwxrwxrwx 1 root root   9 2010-05-23 12:05 pci-0000:00:10.1-usb-0:1:1.0-event-kbd -> ../event5
lrwxrwxrwx 1 root root   9 2010-05-23 12:05 pci-0000:00:10.1-usb-0:1:1.1-event -> ../event6
lrwxrwxrwx 1 root root   9 2010-05-23 12:05 pci-0000:00:10.1-usb-0:2:1.0-event-mouse -> ../event4
lrwxrwxrwx 1 root root   9 2010-05-23 12:05 pci-0000:00:10.1-usb-0:2:1.0-mouse -> ../mouse1
I have tried 4 and then 6 but none of them work after restarting lirc. When running irw, and pressing remote control keys, I see no output in the terminal. Could you help me please? Thanks.

---

### Post by bui_a on 2010-05-30
hmm, it doesn't seem to have detected that you have an ir-device connected. Which Terratec remote/receiver are you using? is it USB?

---

### Post by calande on 2010-05-30
Thank you, it's a PCI one. I'm using a Terratec Cinergy HT PCI:
[IMG]http://i.testfreaks.com/images/products/600x400/170/terratec-cinergy-ht-pci.1825194.jpg[/IMG]
There's the remote control sensor that has a white wire that is plugged into the PCI board.
[IMG]http://www.dinokomp.si/images/TerraTec%20Cinergy%20HT%20PCI.png[/IMG]

---

### Post by bui_a on 2010-05-30
Type

```
dmesg
```

and post the output, and then:

```
lspci
```

and the output from that.

---

### Post by calande on 2010-06-01
Hi there, here's the output:

```
$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:09.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:09.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0d.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
00:0e.0 Ethernet controller: Belkin Device 700f (rev 20)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
$
```

And:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000009ffb0000 - 000000009ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009ffc0000 - 000000009fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fff0000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x9ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00E4000000 mask FFFC000000 write-combining
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000009ffb0000 (usable)
[    0.000000]  modified: 000000009ffb0000 - 000000009ffc0000 (ACPI data)
[    0.000000]  modified: 000000009ffc0000 - 000000009fff0000 (ACPI NVS)
[    0.000000]  modified: 000000009fff0000 - 00000000a0000000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37859000 - 37fefc3c
[    0.000000] Allocated new RAMDISK: 008de000 - 01074c3c
[    0.000000] Move RAMDISK from 0000000037859000 - 0000000037fefc3b to 008de000 - 01074c3b
[    0.000000] ACPI: RSDP 000fa7c0 00021 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 9ffb0100 0003C (v01 A M I  OEMXSDT  05000519 MSFT 00000097)
[    0.000000] ACPI: FACP 9ffb0290 000F4 (v03 A M I  OEMFACP  05000519 MSFT 00000097)
[    0.000000] ACPI: DSDT 9ffb03f0 03A3E (v01  A0036 A0036001 00000001 MSFT 0100000D)
[    0.000000] ACPI: FACS 9ffc0000 00040
[    0.000000] ACPI: APIC 9ffb0390 00052 (v01 A M I  OEMAPIC  05000519 MSFT 00000097)
[    0.000000] ACPI: OEMB 9ffc0040 0003F (v01 A M I  OEMBIOS  05000519 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1671MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd234]              BRK ==> [00008da000 - 00008dd234]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008de000 - 0001074c3c]      NEW RAMDISK ==> [00008de000 - 0001074c3c]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0009ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0009ffb0
[    0.000000] On node 0 totalpages: 655167
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1076200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3344 pages used for memmap
[    0.000000]   HighMem zone: 424610 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:5f780000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2800000 s36024 r0 d21320 u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 650047
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=b86eb121-0104-4329-a9bc-6aad1d0004ed ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 13105280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0009ffb0)
[    0.000000] Memory: 2569476k/2621120k available (4673k kernel code, 50088k reserved, 2121k data, 656k init, 1711816k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590653 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590653   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2002.504 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4005.00 BogoMIPS (lpj=8010016)
[    0.004030] Security Framework initialized
[    0.004058] AppArmor: AppArmor initialized
[    0.004066] Mount-cache hash table entries: 512
[    0.004229] Initializing cgroup subsys ns
[    0.004234] Initializing cgroup subsys cpuacct
[    0.004238] Initializing cgroup subsys memory
[    0.004246] Initializing cgroup subsys devices
[    0.004249] Initializing cgroup subsys freezer
[    0.004252] Initializing cgroup subsys net_cls
[    0.004273] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004276] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004281] mce: CPU supports 5 MCE banks
[    0.004304] Performance Events: AMD PMU driver.
[    0.004311] ... version:                0
[    0.004313] ... bit width:              48
[    0.004315] ... generic registers:      4
[    0.004317] ... value mask:             0000ffffffffffff
[    0.004320] ... max period:             00007fffffffffff
[    0.004322] ... fixed-purpose events:   0
[    0.004324] ... event mask:             000000000000000f
[    0.004329] Checking 'hlt' instruction... OK.
[    0.020725] SMP alternatives: switching to UP code
[    0.026749] ACPI: Core revision 20090903
[    0.032644] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032651] ftrace: allocating 21771 entries in 43 pages
[    0.036125] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036946] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.079273] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[    0.080001] Brought up 1 CPUs
[    0.080001] Total of 1 processors activated (4005.00 BogoMIPS).
[    0.080001] CPU0 attaching NULL sched-domain.
[    0.080001] devtmpfs: initialized
[    0.080001] regulator: core version 0.5
[    0.080001] Time: 19:02:38  Date: 06/01/10
[    0.080001] NET: Registered protocol family 16
[    0.080001] EISA bus registered
[    0.080001] ACPI: bus type pci registered
[    0.080001] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.080001] PCI: Using configuration type 1 for base access
[    0.080001] bio: create slab <bio-0> at 0
[    0.080001] ACPI: EC: Look up EC in DSDT
[    0.081423] ACPI: Executed 1 blocks of module-level executable AML code
[    0.084810] ACPI: Interpreter enabled
[    0.084817] ACPI: (supports S0 S1 S3 S4 S5)
[    0.084839] ACPI: Using IOAPIC for interrupt routing
[    0.090063] ACPI: No dock devices found.
[    0.090183] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.090230] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe4000000-0xe7ffffff]
[    0.090489] pci 0000:00:01.0: supports D1
[    0.090528] pci 0000:00:09.0: reg 10 32bit mmio: [0xf7000000-0xf7ffffff]
[    0.090593] pci 0000:00:09.1: reg 10 32bit mmio: [0xf8000000-0xf8ffffff]
[    0.090652] pci 0000:00:09.2: reg 10 32bit mmio: [0xf9000000-0xf9ffffff]
[    0.090724] pci 0000:00:0a.0: reg 10 32bit mmio: [0xfaa00000-0xfaa03fff]
[    0.090731] pci 0000:00:0a.0: reg 14 io port: [0xa400-0xa4ff]
[    0.090752] pci 0000:00:0a.0: reg 30 32bit mmio pref: [0xfa900000-0xfa91ffff]
[    0.090773] pci 0000:00:0a.0: supports D1 D2
[    0.090776] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090780] pci 0000:00:0a.0: PME# disabled
[    0.090814] pci 0000:00:0d.0: reg 10 32bit mmio: [0xfab00000-0xfab00fff]
[    0.090821] pci 0000:00:0d.0: reg 14 io port: [0xa800-0xa8ff]
[    0.090857] pci 0000:00:0d.0: PME# supported from D0 D3hot D3cold
[    0.090861] pci 0000:00:0d.0: PME# disabled
[    0.090891] pci 0000:00:0e.0: reg 10 io port: [0xb000-0xb0ff]
[    0.090898] pci 0000:00:0e.0: reg 14 32bit mmio: [0xfac00000-0xfac001ff]
[    0.090933] pci 0000:00:0e.0: supports D1 D2
[    0.090935] pci 0000:00:0e.0: PME# supported from D1 D2 D3hot D3cold
[    0.090939] pci 0000:00:0e.0: PME# disabled
[    0.090971] pci 0000:00:0f.0: reg 10 io port: [0xd000-0xd007]
[    0.090978] pci 0000:00:0f.0: reg 14 io port: [0xc800-0xc803]
[    0.090984] pci 0000:00:0f.0: reg 18 io port: [0xc400-0xc407]
[    0.090990] pci 0000:00:0f.0: reg 1c io port: [0xc000-0xc003]
[    0.090996] pci 0000:00:0f.0: reg 20 io port: [0xb800-0xb80f]
[    0.091002] pci 0000:00:0f.0: reg 24 io port: [0xb400-0xb4ff]
[    0.091065] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.091139] pci 0000:00:10.0: reg 20 io port: [0xd400-0xd41f]
[    0.091162] pci 0000:00:10.0: supports D1 D2
[    0.091164] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091168] pci 0000:00:10.0: PME# disabled
[    0.091213] pci 0000:00:10.1: reg 20 io port: [0xd800-0xd81f]
[    0.091236] pci 0000:00:10.1: supports D1 D2
[    0.091239] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091242] pci 0000:00:10.1: PME# disabled
[    0.091287] pci 0000:00:10.2: reg 20 io port: [0xe000-0xe01f]
[    0.091310] pci 0000:00:10.2: supports D1 D2
[    0.091312] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091316] pci 0000:00:10.2: PME# disabled
[    0.091361] pci 0000:00:10.3: reg 20 io port: [0xe400-0xe41f]
[    0.091384] pci 0000:00:10.3: supports D1 D2
[    0.091386] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091390] pci 0000:00:10.3: PME# disabled
[    0.091420] pci 0000:00:10.4: reg 10 32bit mmio: [0xfae00000-0xfae000ff]
[    0.091458] pci 0000:00:10.4: supports D1 D2
[    0.091461] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091464] pci 0000:00:10.4: PME# disabled
[    0.091520] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.091525] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.091574] pci 0000:00:11.5: reg 10 io port: [0xe800-0xe8ff]
[    0.091613] pci 0000:00:11.5: supports D1 D2
[    0.091643] pci 0000:00:11.6: reg 10 io port: [0x00-0xff]
[    0.091779] pci 0000:01:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.091784] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.091797] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfaf00000-0xfaf1ffff]
[    0.091840] pci 0000:00:01.0: bridge 32bit mmio: [0xfaf00000-0xfbffffff]
[    0.091845] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe8000000-0xf6ffffff]
[    0.091852] pci_bus 0000:00: on NUMA node 0
[    0.091856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.100570] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.100656] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[    0.100740] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.100824] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 14 15)
[    0.100907] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.100992] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.101077] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.101162] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.101273] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.101277] vgaarb: loaded
[    0.101401] SCSI subsystem initialized
[    0.101482] libata version 3.00 loaded.
[    0.101552] usbcore: registered new interface driver usbfs
[    0.101565] usbcore: registered new interface driver hub
[    0.101590] usbcore: registered new device driver usb
[    0.101706] ACPI: WMI: Mapper loaded
[    0.101709] PCI: Using ACPI for IRQ routing
[    0.101885] NetLabel: Initializing
[    0.101887] NetLabel:  domain hash size = 128
[    0.101889] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.101904] NetLabel:  unlabeled traffic allowed by default
[    0.103792] AppArmor: AppArmor Filesystem Enabled
[    0.103814] pnp: PnP ACPI init
[    0.103833] ACPI: bus type pnp registered
[    0.104976] pnp 00:06: io resource (0x10-0x1f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104980] pnp 00:06: io resource (0x22-0x3f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104983] pnp 00:06: io resource (0x44-0x5f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104987] pnp 00:06: io resource (0x62-0x63) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104991] pnp 00:06: io resource (0x65-0x6f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104994] pnp 00:06: io resource (0x72-0x7f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104998] pnp 00:06: io resource (0x80-0x80) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.105001] pnp 00:06: io resource (0x84-0x86) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.105005] pnp 00:06: io resource (0x88-0x88) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.105008] pnp 00:06: io resource (0x8c-0x8e) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.105012] pnp 00:06: io resource (0x90-0x9f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.105016] pnp 00:06: io resource (0xa2-0xbf) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.105019] pnp 00:06: io resource (0xe0-0xef) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.106374] pnp: PnP ACPI: found 9 devices
[    0.106376] ACPI: ACPI bus type pnp unregistered
[    0.106380] PnPBIOS: Disabled by ACPI PNP
[    0.106394] system 00:05: ioport range 0x680-0x6ff has been reserved
[    0.106397] system 00:05: ioport range 0x290-0x297 has been reserved
[    0.106403] system 00:06: ioport range 0x3e1-0x3e7 has been reserved
[    0.106406] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.106409] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.106412] system 00:06: ioport range 0x400-0x41f has been reserved
[    0.106419] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.106422] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.106426] system 00:07: iomem range 0xfff80000-0xffffffff has been reserved
[    0.106431] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[    0.106435] system 00:08: iomem range 0xc0000-0xdffff could not be reserved
[    0.106438] system 00:08: iomem range 0xe0000-0xfffff could not be reserved
[    0.106442] system 00:08: iomem range 0x100000-0x9ffeffff could not be reserved
[    0.141128] Switching to clocksource acpi_pm
[    0.141257] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.141260] pci 0000:00:01.0:   IO window: disabled
[    0.141264] pci 0000:00:01.0:   MEM window: 0xfaf00000-0xfbffffff
[    0.141268] pci 0000:00:01.0:   PREFETCH window: 0xe8000000-0xf6ffffff
[    0.141284] pci 0000:00:01.0: setting latency timer to 64
[    0.141289] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.141292] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.141295] pci_bus 0000:01: resource 1 mem: [0xfaf00000-0xfbffffff]
[    0.141298] pci_bus 0000:01: resource 2 pref mem [0xe8000000-0xf6ffffff]
[    0.141337] NET: Registered protocol family 2
[    0.141435] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.141826] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.142918] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.143539] TCP: Hash tables configured (established 131072 bind 65536)
[    0.143542] TCP reno registered
[    0.143660] NET: Registered protocol family 1
[    0.143684] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    1.740013] pci 0000:00:10.4: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    1.740137] pci 0000:01:00.0: Boot video device
[    1.740350] cpufreq-nforce2: No nForce2 chipset.
[    1.740378] Scanning for low memory corruption every 60 seconds
[    1.740488] audit: initializing netlink socket (disabled)
[    1.740500] type=2000 audit(1275418958.740:1): initialized
[    1.750613] Trying to unpack rootfs image as initramfs...
[    1.764370] highmem bounce pool size: 64 pages
[    1.764378] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.765828] VFS: Disk quotas dquot_6.5.2
[    1.765897] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.766486] fuse init (API version 7.13)
[    1.766569] msgmni has been set to 1677
[    1.772236] alg: No test for stdrng (krng)
[    1.772343] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.772346] io scheduler noop registered
[    1.772348] io scheduler anticipatory registered
[    1.772350] io scheduler deadline registered
[    1.772389] io scheduler cfq registered (default)
[    1.772520] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.772541] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.772648] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.772658] ACPI: Power Button [PWRB]
[    1.772705] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.772709] ACPI: Sleep Button [SLPB]
[    1.772754] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.772756] ACPI: Power Button [PWRF]
[    1.773112] processor LNXCPU:00: registered as cooling_device0
[    1.776793] isapnp: Scanning for PnP cards...
[    1.782461] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.782731]   alloc irq_desc for 18 on node -1
[    1.782734]   alloc kstat_irqs on node -1
[    1.782742] serial 0000:00:0d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.782861] 0000:00:0d.0: ttyS0 at I/O 0xa808 (irq = 18) is a 16450
[    1.782926] 0000:00:0d.0: ttyS1 at I/O 0xa810 (irq = 18) is a 8250
[    1.782988] 0000:00:0d.0: ttyS2 at I/O 0xa818 (irq = 18) is a 16450
[    1.783050] 0000:00:0d.0: ttyS3 at I/O 0xa820 (irq = 18) is a 8250
[    1.783071] Couldn't register serial port 0000:00:0d.0: -28
[    1.788290] brd: module loaded
[    1.788784] loop: module loaded
[    1.788897] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.789074]   alloc irq_desc for 20 on node -1
[    1.789077]   alloc kstat_irqs on node -1
[    1.789085] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.789157] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    1.789448] Fixed MDIO Bus: probed
[    1.789481] PPP generic driver version 2.4.2
[    1.789527] tun: Universal TUN/TAP device driver, 1.6
[    1.789530] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.789606] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.789623]   alloc irq_desc for 21 on node -1
[    1.789625]   alloc kstat_irqs on node -1
[    1.789629] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    1.789650] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    1.789680] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    1.789749] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfae00000
[    1.839822] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    1.839969] usb usb1: configuration #1 chosen from 1 choice
[    1.840016] hub 1-0:1.0: USB hub found
[    1.840029] hub 1-0:1.0: 8 ports detected
[    1.840093] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.840113] uhci_hcd: USB Universal Host Controller Interface driver
[    1.840177] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.840187] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    1.840223] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    1.840247] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[    1.840344] usb usb2: configuration #1 chosen from 1 choice
[    1.840368] hub 2-0:1.0: USB hub found
[    1.840377] hub 2-0:1.0: 2 ports detected
[    1.840417] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.840425] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    1.840453] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    1.840472] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[    1.840564] usb usb3: configuration #1 chosen from 1 choice
[    1.840587] hub 3-0:1.0: USB hub found
[    1.840595] hub 3-0:1.0: 2 ports detected
[    1.840635] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.840641] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    1.840679] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    1.840698] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[    1.840800] usb usb4: configuration #1 chosen from 1 choice
[    1.840824] hub 4-0:1.0: USB hub found
[    1.840831] hub 4-0:1.0: 2 ports detected
[    1.840869] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.840874] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    1.840902] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    1.840921] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e400
[    1.841017] usb usb5: configuration #1 chosen from 1 choice
[    1.841042] hub 5-0:1.0: USB hub found
[    1.841050] hub 5-0:1.0: 2 ports detected
[    1.841142] PNP: No PS/2 controller found. Probing ports directly.
[    1.841630] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.841636] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.841710] mice: PS/2 mouse device common for all mice
[    1.841823] rtc_cmos 00:02: RTC can wake from S4
[    1.841865] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.841916] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.842022] device-mapper: uevent: version 1.0.3
[    1.844217] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.848132] device-mapper: multipath: version 1.1.0 loaded
[    1.848137] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.848330] EISA: Probing bus 0 at eisa.0
[    1.848338] Cannot allocate resource for EISA slot 1
[    1.848351] Cannot allocate resource for EISA slot 5
[    1.848364] EISA: Detected 0 cards.
[    1.852291] cpuidle: using governor ladder
[    1.852295] cpuidle: using governor menu
[    1.852779] TCP cubic registered
[    1.852936] NET: Registered protocol family 10
[    1.853390] lo: Disabled Privacy Extensions
[    1.853689] NET: Registered protocol family 17
[    1.853728] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[    1.854911] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    1.854930] Using IPI No-Shortcut mode
[    1.855038] PM: Resume from disk failed.
[    1.855052] registered taskstats version 1
[    1.855413]   Magic number: 14:51:40
[    1.855430] bdi 7:5: hash matches
[    1.855539] rtc_cmos 00:02: setting system clock to 2010-06-01 19:02:39 UTC (1275418959)
[    1.855544] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.855546] EDD information not available.
[    2.218242] Freeing initrd memory: 7771k freed
[    2.358205] isapnp: No Plug & Play device found
[    2.358218] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    2.358244] Freeing unused kernel memory: 656k freed
[    2.359147] Write protecting the kernel text: 4676k
[    2.359181] Write protecting the kernel read-only data: 1840k
[    2.379784] udev: starting version 151
[    2.493482] usb 1-5: configuration #1 chosen from 1 choice
[    2.596622] sata_via 0000:00:0f.0: version 2.4
[    2.596641] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    2.596688] sata_via 0000:00:0f.0: routed to hard irq line 10
[    2.605776] scsi0 : sata_via
[    2.605968] scsi1 : sata_via
[    2.606006] ata1: SATA max UDMA/133 cmd 0xd000 ctl 0xc800 bmdma 0xb800 irq 20
[    2.606010] ata2: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma 0xb808 irq 20
[    2.606065] pata_via 0000:00:0f.1: version 0.3.4
[    2.606078] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.606359] scsi2 : pata_via
[    2.606452] scsi3 : pata_via
[    2.607650] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    2.607653] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.607703]   alloc irq_desc for 17 on node -1
[    2.607706]   alloc kstat_irqs on node -1
[    2.607713] skge 0000:00:0a.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.607724] skge 0000:00:0a.0: PCI: Disallowing DAC for device
[    2.607756] skge 1.13 addr 0xfaa00000 irq 17 chip Yukon-Lite rev 9
[    2.608445] skge eth0: addr 00:13:d4:78:a3:e0
[    2.608894] Initializing USB Mass Storage driver...
[    2.609117] scsi4 : SCSI emulation for USB Mass Storage devices
[    2.609248] usbcore: registered new interface driver usb-storage
[    2.609254] USB Mass Storage support registered.
[    2.609333] usb-storage: device found at 4
[    2.609334] usb-storage: waiting for device to settle before scanning
[    2.732015] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.808016] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.889437] usb 3-1: configuration #1 chosen from 1 choice
[    2.906705] usbcore: registered new interface driver hiddev
[    2.907090] usbcore: registered new interface driver usbhid
[    2.907168] usbhid: v2.6:USB HID core driver
[    3.108203] ata1.00: ATA-7: Kingston SSDNow V Series 64GB, B090522a, max UDMA/133
[    3.108206] ata1.00: 125045424 sectors, multi 1: LBA 
[    3.116214] ata1.00: configured for UDMA/133
[    3.116336] scsi 0:0:0:0: Direct-Access     ATA      Kingston SSDNow  B090 PQ: 0 ANSI: 5
[    3.116498] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.116746] sd 0:0:0:0: [sda] 125045424 512-byte logical blocks: (64.0 GB/59.6 GiB)
[    3.116790] sd 0:0:0:0: [sda] Write Protect is off
[    3.116793] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.116816] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.116945]  sda: sda1 < sda5 sda6 > sda2
[    3.118173] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.132017] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    3.308347] usb 3-2: configuration #1 chosen from 1 choice
[    3.320016] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.330973] input: Kensington USB/PS2 Wheel Mouse  as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input4
[    3.331075] generic-usb 0003:047D:1002.0003: input,hidraw0: USB HID v1.00 Mouse [Kensington USB/PS2 Wheel Mouse ] on usb-0000:00:10.1-2/input0
[    3.518017] input: HID 046a:0023 as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input5
[    3.518110] cherry 0003:046A:0023.0001: input,hidraw1: USB HID v1.11 Keyboard [HID 046a:0023] on usb-0000:00:10.1-1/input0
[    3.541451] input: HID 046a:0023 as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.1/input/input6
[    3.541553] cherry 0003:046A:0023.0002: input,hidraw2: USB HID v1.11 Device [HID 046a:0023] on usb-0000:00:10.1-1/input1
[    3.560405] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    3.882707] Adding 1317288k swap on /dev/sda6.  Priority:-1 extents:1 across:1317288k SS
[    3.933701] udev: starting version 151
[    4.377323] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.378289] Linux agpgart interface v0.103
[    4.441824] lp: driver loaded but no devices found
[    4.582662] cfg80211: Calling CRDA to update world regulatory domain
[    4.608193] cfg80211: World regulatory domain updated:
[    4.608198] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.608202] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.608205] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.608208] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.608211] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.608214] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.631327] Linux video capture interface: v2.00
[    4.646916] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0282]
[    4.672506] type=1505 audit(1275411762.316:2):  operation="profile_load" pid=545 name="/sbin/dhclient3"
[    4.672794] type=1505 audit(1275411762.316:3):  operation="profile_load" pid=545 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    4.672954] type=1505 audit(1275411762.316:4):  operation="profile_load" pid=545 name="/usr/lib/connman/scripts/dhclient-script"
[    4.690796] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xe4000000
[    4.749157]   alloc irq_desc for 19 on node -1
[    4.749161]   alloc kstat_irqs on node -1
[    4.749230] rtl8180 0000:00:0e.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.750735] vga16fb: initializing
[    4.750740] vga16fb: mapped to 0xc00a0000
[    4.755876] fb0: VGA16 VGA frame buffer device
[    4.970834] nvidia: module license 'NVIDIA' taints kernel.
[    4.970839] Disabling lock debugging due to kernel taint
[    5.795288] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[    5.795923] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[    5.826755] ip_tables: (C) 2000-2006 Netfilter Core Team
[    5.839447] phy0: Selected rate control algorithm 'minstrel'
[    5.840330] phy0: hwaddr 00:17:3f:2e:ef:0b, RTL8185vD + rtl8225z2
[    5.841096] cx88[0]: subsystem: 153b:1177, board: Terratec Cinergy HT PCI MKII [card=79,autodetected], frontend(s): 1
[    5.841100] cx88[0]: TV tuner type 71, Radio tuner type 71
[    6.004432] cx2388x alsa driver version 0.0.7 loaded
[    6.049806] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[    6.170611] skge eth0: enabling interface
[    6.236459] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.276074] xc2028 1-0061: creating new instance
[    6.276078] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[    6.276084] xc2028 1-0061: destroying instance
[    6.276170] xc2028 1-0061: creating new instance
[    6.276172] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[    6.276176] cx88[0]: Asking xc2028/3028 to load firmware xc3028-v27.fw
[    6.283010] Console: switching to colour frame buffer device 80x30
[    6.309977] cx88[0]/2: cx2388x 8802 Driver Manager
[    6.309998]   alloc irq_desc for 16 on node -1
[    6.310000]   alloc kstat_irqs on node -1
[    6.310009] cx88-mpeg driver manager 0000:00:09.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.310022] cx88[0]/2: found at 0000:00:09.2, rev: 5, irq: 16, latency: 64, mmio: 0xf9000000
[    6.310029] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    6.310620] cx8800 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.310630] cx88[0]/0: found at 0000:00:09.0, rev: 5, irq: 16, latency: 64, mmio: 0xf7000000
[    6.310646] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    6.310729] cx88[0]/0: registered device video0 [v4l2]
[    6.310754] cx88[0]/0: registered device vbi0
[    6.310779] cx88[0]/0: registered device radio0
[    6.310842] cx88-mpeg driver manager 0000:00:09.2: firmware: requesting xc3028-v27.fw
[    6.334497] xc2028 1-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[    6.334616] cx88[0]: Calling XC2028/3028 callback
[    6.334618] cx88[0]: setting GPIO to TV!
[    7.078651] xc2028 1-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
[    7.078656] cx88[0]: Calling XC2028/3028 callback
[    7.078658] cx88[0]: setting GPIO to TV!
[    7.828088] usb-storage: device scan complete
[    7.831883] scsi 4:0:0:0: Direct-Access     TS32GSSD 25-M             0811 PQ: 0 ANSI: 0
[    7.834459] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    7.848709] sd 4:0:0:0: [sdb] 62652416 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    7.849962] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    7.849967] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.852855] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    7.852860] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.853123]  sdb: sdb1
[    7.861629] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    7.861635] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.861898] sd 4:0:0:0: [sdb] Attached SCSI disk
[    7.865347] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[    7.930679] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[    7.930684] cx88/2: registering cx8802 driver, type: dvb access: shared
[    7.930688] cx88[0]/2: subsystem: 153b:1177, board: Terratec Cinergy HT PCI MKII [card=79]
[    7.930692] cx88[0]/2: cx2388x based DVB/ATSC card
[    7.930694] cx8802_alloc_frontends() allocating 1 frontend(s)
[    7.975136] xc2028 1-0061: attaching existing instance
[    7.975140] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[    8.031962] type=1505 audit(1275411765.675:5):  operation="profile_load" pid=771 name="/usr/share/gdm/guest-session/Xsession"
[    8.035078] type=1505 audit(1275411765.676:6):  operation="profile_replace" pid=826 name="/sbin/dhclient3"
[    8.035497] type=1505 audit(1275411765.676:7):  operation="profile_replace" pid=826 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    8.035665] type=1505 audit(1275411765.676:8):  operation="profile_replace" pid=826 name="/usr/lib/connman/scripts/dhclient-script"
[    8.055774] type=1505 audit(1275411765.696:9):  operation="profile_load" pid=827 name="/usr/bin/evince"
[    8.082275] type=1505 audit(1275411765.724:10):  operation="profile_load" pid=827 name="/usr/bin/evince-previewer"
[    8.090270] type=1505 audit(1275411765.732:11):  operation="profile_load" pid=827 name="/usr/bin/evince-thumbnailer"
[    8.131233] type=1505 audit(1275411765.773:12):  operation="profile_load" pid=841 name="/usr/lib/cups/backend/cups-pdf"
[    8.131603] type=1505 audit(1275411765.773:13):  operation="profile_load" pid=841 name="/usr/sbin/cupsd"
[    8.143231] type=1505 audit(1275411765.784:14):  operation="profile_load" pid=843 name="/usr/sbin/mysqld-akonadi"
[    8.174517] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.176279] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
[   10.001703] xc2028 1-0061: Loading firmware for type=MTS (4), id 000000000000b700.
[   10.041059] xc2028 1-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.
[   10.104040] cx88[0]: Calling XC2028/3028 callback
[   10.224045] cx88[0]/2: xc3028 attached
[   10.228367] cx88_audio 0000:00:09.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.228378] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.228401] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   10.229335] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   10.229342]   alloc irq_desc for 22 on node -1
[   10.229345]   alloc kstat_irqs on node -1
[   10.229353] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   10.240048] DVB: registering new adapter (cx88[0])
[   10.240055] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   10.250951] cx88[0]: Calling XC2028/3028 callback
[   10.250957] cx88[0]: setting GPIO to TV!
[   10.994990] xc2028 1-0061: Loading firmware for type=BASE FM (401), id 0000000000000000.
[   10.994996] cx88[0]: Calling XC2028/3028 callback
[   10.994997] cx88[0]: setting GPIO to TV!
[   11.739102] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   13.448368] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.451172] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   13.483086] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   13.483105] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   13.483303] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   13.483458] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   13.819308] xc2028 1-0061: Loading firmware for type=FM (400), id 0000000000000000.
[   13.880024] cx88[0]: Calling XC2028/3028 callback
[   13.894794] ppdev: user-space parallel port driver
[   14.487755] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   14.487770] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   14.487865] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   24.068017] eth0: no IPv6 routers present
```

Thank you in advance! :)

---

### Post by bui_a on 2010-06-02
Hmm, it seems your ir-receiver isn't being recognized by ubuntu. Have you checked out whether it is supported by the kernel? If there is no support there is little hope of getting it to work.

---

### Post by calande on 2010-06-02
Thanks, do you know how to find out if it's supported by the kernel?

---

### Post by bui_a on 2010-06-05
I'd say googling around would be your best bet. I've tried some (admittedy superficial) searches, but have not been able to figure out which remote component your card uses. I am sorry that I am unable to help further!:/

---

