---
title: "another bcm 43227 wifi problems with sta driver"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by nutpants on 2012-10-26
i have a new acer timeline 1830tz-4472

i should be useing the sta driver
some times i boot and it works with wpa psk
other times i boot and it will not accept the password but will work
with an open system. 
some time i modprobe -r wl && modeprobe wl and it works flawless
other times nothing..
some times sudo rmmod wl && sudo depmod && sudo modprobe wl works

i am going crasy reading 

fresh install on 12.04.01 and updated today.
i am close to pulling my hair out over this
i have checked and followed every broadcom thread i can find
i have apt get install or remove everything but im still stuck with hit or miss wifi..

please help..


 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:6a:8a:40:19:42
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:d3400000-d343ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 00
       serial: c0:f8:da:40:50:7c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d2403fff



lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]


 rfkill list all
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

dmesg | grep wl
[   39.353339] wl: module license 'MIXED/Proprietary' taints kernel.
[   39.359676] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   39.359688] wl 0000:02:00.0: setting latency timer to 64
[  236.747740] wl 0000:02:00.0: PCI INT A disabled
[  243.134561] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  243.134577] wl 0000:02:00.0: setting latency timer to 64

 iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.


i have no errors when i 
sudo modprobe wl


i would like to stay with the sta driver if possibile as i dont want to use ndiswrapper if i can avoid it.

thank you for any help

---

### Post by nutpants on 2012-10-29
*******not working*******
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:6a:8a:40:19:42
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:d3400000-d343ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 00
       serial: c0:f8:da:40:50:7a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d2403fff

 sudo lspci -nn|grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

sudo rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

sudo dmesg | grep wl
[   37.549917] wl: module license 'MIXED/Proprietary' taints kernel.
[   37.558115] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   37.558127] wl 0000:02:00.0: setting latency timer to 64

sudo iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bgn  ESSID:"Nutpantz ap1"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:18:D1:79:65:D0   
          Bit Rate=11 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=4/5  Signal level=-67 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


sudo rmmod wl
sudo modprobe wl   *********now it works  *********
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:6a:8a:40:19:42
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:d3400000-d343ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 00
       serial: c0:f8:da:40:50:7a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.7 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d2403fff

 sudo lspci -nn|grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

 sudo rfkill list all
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

 sudo dmesg | grep wl
[   37.549917] wl: module license 'MIXED/Proprietary' taints kernel.
[   37.558115] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   37.558127] wl 0000:02:00.0: setting latency timer to 64
[  317.690233] wl 0000:02:00.0: PCI INT A disabled
[  325.973781] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  325.973797] wl 0000:02:00.0: setting latency timer to 64


what am i missing???
what do i need to fix this so i dont have to rmmod wl  and modeprobe wl each time i boot

---

### Post by Hadaka on 2012-10-29
Hi, your  card does indeed require the sta driver
lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358] <<- *

have you been to this link ?
[https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29)

looks like you need to blacklist b43 and wl

also if you continue reading..it takes you to another link with the sta driver file

hope this helps.

---

### Post by nutpants on 2012-10-30
this might be a stupid question...  but...

is not "wl" the broadcom sta driver???

i have found a link here and will try out some of the things it suggests.

[http://ubuntuforums.org/showthread.php?t=1049761](http://ubuntuforums.org/showthread.php?t=1049761)

BUT it appear that it is just adding a script
to automagicly rmmod wl and modprobe wl
each time the computer starts....

which is not a fix but only a sticky bandaid...

i may also try building the driver from source..

if i solve it i will post what works best..

---

### Post by Hadaka on 2012-10-30
Hi, I think the blacklisting was to move them out while
the driver loads kinda like rmmod moves the modules
from the kernel on startup. Have you written anything
to /etc/modules ?

---

### Post by nutpants on 2012-11-01
my etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
wl

# Generated by sensors-detect on Thu Oct 25 14:29:45 2012
# Chip drivers
coretemp

---

### Post by nutpants on 2012-11-01
trying to build the driver myself failed..

make clean
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  CLEAN   /home/me/Downloads/hybridwl/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
me@testmachine:~/Downloads/hybridwl$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  LD      /home/me/Downloads/hybridwl/built-in.o
  CC [M]  /home/me/Downloads/hybridwl/src/shared/linux_osl.o
  CC [M]  /home/me/Downloads/hybridwl/src/wl/sys/wl_linux.o
/home/me/Downloads/hybridwl/src/wl/sys/wl_linux.c:388:2: error: unknown field &#8216;ndo_set_multicast_list&#8217; specified in initializer
/home/me/Downloads/hybridwl/src/wl/sys/wl_linux.c:388:2: warning: initialization from incompatible pointer type [enabled by default]
/home/me/Downloads/hybridwl/src/wl/sys/wl_linux.c:388:2: warning: (near initialization for &#8216;wl_netdev_ops.ndo_validate_addr&#8217;) [enabled by default]
make[2]: *** [/home/me/Downloads/hybridwl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/me/Downloads/hybridwl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make: *** [all] Error 2
me@testmachine:~/Downloads/hybridwl$ 


trying to figure out to get it to build


found this
[http://www.linuxquestions.org/questions/slackware-14/compiling-broadcom-driver-947294/](http://www.linuxquestions.org/questions/slackware-14/compiling-broadcom-driver-947294/)

so i deleted the line at 388
and the driver built..

followed the directions for moving the driver 
and it seemed to work at boot..
so i will test it and report back if this is solved.

---

### Post by nutpants on 2012-11-13
nope still not working..

still works when i rmmod and modeprobe...

cant auto magically do it with a script at startup.
what a pain


here is my dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-32-generic (buildd@batsu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 (Ubuntu 3.2.0-32.51-generic 3.2.30)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.2.0-32-generic root=/dev/mapper/secure-securetime ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b363f000 (usable)
[    0.000000]  BIOS-e820: 00000000b363f000 - 00000000b36bf000 (reserved)
[    0.000000]  BIOS-e820: 00000000b36bf000 - 00000000b37bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b37bf000 - 00000000b37ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b37ff000 - 00000000b3800000 (usable)
[    0.000000]  BIOS-e820: 00000000b3800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Acer Aspire 1830T/JV10_CS, BIOS V1.24 05/06/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x138000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   4 base 0B4000000 mask FFC000000 uncachable
[    0.000000]   5 base 0B3800000 mask FFF800000 uncachable
[    0.000000]   6 base 100000000 mask FC0000000 write-back
[    0.000000]   7 base 138000000 mask FF8000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xb3800 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000b3800000
[    0.000000]  0000000000 - 00b3800000 page 2M
[    0.000000] kernel direct mapping tables up to b3800000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000138000000
[    0.000000]  0100000000 - 0138000000 page 2M
[    0.000000] kernel direct mapping tables up to 138000000 @ b3639000-b363f000
[    0.000000] RAMDISK: 3572a000 - 36b8d000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 00000000b37fe120 00074 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 00000000b37fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: DSDT 00000000b37ea000 0EC3D (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: FACS 00000000b376e000 00040
[    0.000000] ACPI: ASF! 00000000b37fd000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: HPET 00000000b37fb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 00000000b37fa000 0008C (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 00000000b37f9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 00000000b37e9000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 00000000b37e5000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: ASPT 00000000b37e2000 00034 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: WDAT 00000000b37e1000 00224 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SSDT 00000000b37e0000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000138000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000138000000
[    0.000000]   NODE_DATA [0000000137ffb000 - 0000000137ffffff]
[    0.000000]  [ffffea0000000000-ffffea0004dfffff] PMD -> [ffff880133a00000-ffff8801375fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00138000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b363f
[    0.000000]     0: 0x000b37ff -> 0x000b3800
[    0.000000]     0: 0x00100000 -> 0x00138000
[    0.000000] On node 0 totalpages: 964045
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 714368 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 225792 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000b363f000 - 00000000b36bf000
[    0.000000] PM: Registered nosave memory: 00000000b36bf000 - 00000000b37bf000
[    0.000000] PM: Registered nosave memory: 00000000b37bf000 - 00000000b37ff000
[    0.000000] PM: Registered nosave memory: 00000000b3800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1b000
[    0.000000] PM: Registered nosave memory: 00000000fed1b000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880137c00000 s83136 r8192 d23360 u262144
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 944072
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-32-generic root=/dev/mapper/secure-securetime ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3691084k/5111808k available (6560k kernel code, 1255628k absent, 165096k reserved, 6639k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 31457280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 1329.842 MHz processor.
[    0.000005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2659.68 BogoMIPS (lpj=5319368)
[    0.000012] pid_max: default: 32768 minimum: 301
[    0.000051] Security Framework initialized
[    0.000075] AppArmor: AppArmor initialized
[    0.000078] Yama: becoming mindful.
[    0.000658] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002187] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002814] Mount-cache hash table entries: 256
[    0.003044] Initializing cgroup subsys cpuacct
[    0.003052] Initializing cgroup subsys memory
[    0.003064] Initializing cgroup subsys devices
[    0.003069] Initializing cgroup subsys freezer
[    0.003072] Initializing cgroup subsys blkio
[    0.003081] Initializing cgroup subsys perf_event
[    0.003127] CPU: Physical Processor ID: 0
[    0.003129] CPU: Processor Core ID: 0
[    0.003138] mce: CPU supports 9 MCE banks
[    0.003157] CPU0: Thermal monitoring enabled (TM1)
[    0.003169] using mwait in idle threads.
[    0.006884] ACPI: Core revision 20110623
[    0.046019] ftrace: allocating 27014 entries in 106 pages
[    0.060397] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.100085] CPU0: Intel(R) Pentium(R) CPU        U5600  @ 1.33GHz stepping 05
[    0.206920] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.206931] ... version:                3
[    0.206933] ... bit width:              48
[    0.206935] ... generic registers:      4
[    0.206938] ... value mask:             0000ffffffffffff
[    0.206940] ... max period:             000000007fffffff
[    0.206943] ... fixed-purpose events:   3
[    0.206945] ... event mask:             000000070000000f
[    0.207238] NMI watchdog enabled, takes one hw-pmu counter.
[    0.207370] Booting Node   0, Processors  #1
[    0.207375] smpboot cpu 1: start_ip = 98000
[    0.315129] NMI watchdog enabled, takes one hw-pmu counter.
[    0.315190] Brought up 2 CPUs
[    0.315194] Total of 2 processors activated (5319.56 BogoMIPS).
[    0.317104] devtmpfs: initialized
[    0.318684] EVM: security.selinux
[    0.318687] EVM: security.SMACK64
[    0.318689] EVM: security.capability
[    0.318735] PM: Registering ACPI NVS region at b36bf000 (1048576 bytes)
[    0.320227] print_constraints: dummy: 
[    0.320266] RTC time: 13:51:45, date: 11/13/12
[    0.320320] NET: Registered protocol family 16
[    0.320438] Trying to unpack rootfs image as initramfs...
[    0.320520] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.320525] ACPI: bus type pci registered
[    0.320648] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.320654] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.383855] PCI: Using configuration type 1 for base access
[    0.385426] bio: create slab <bio-0> at 0
[    0.385568] ACPI: Added _OSI(Module Device)
[    0.385572] ACPI: Added _OSI(Processor Device)
[    0.385575] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.385578] ACPI: Added _OSI(Processor Aggregator Device)
[    0.389653] ACPI: EC: Look up EC in DSDT
[    0.393762] ACPI: Executed 1 blocks of module-level executable AML code
[    0.467233] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.468030] ACPI: SSDT 00000000b3691c18 002A6 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.469009] ACPI: Dynamic OEM Table Load:
[    0.469013] ACPI: SSDT           (null) 002A6 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.469320] ACPI: SSDT 00000000b368f018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.470312] ACPI: Dynamic OEM Table Load:
[    0.470316] ACPI: SSDT           (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.499644] ACPI: SSDT 00000000b3690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.500748] ACPI: Dynamic OEM Table Load:
[    0.500752] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.531407] ACPI: SSDT 00000000b368ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.532407] ACPI: Dynamic OEM Table Load:
[    0.532411] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.980501] Freeing initrd memory: 20876k freed
[    1.088114] ACPI: Interpreter enabled
[    1.088124] ACPI: (supports S0 S3 S4 S5)
[    1.088200] ACPI: Using IOAPIC for interrupt routing
[    1.102078] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.102440] ACPI: No dock devices found.
[    1.102443] HEST: Table not found.
[    1.102448] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.103075] \_SB_.PCI0:_OSC invalid UUID
[    1.103078] _OSC request data:1 8 1f 
[    1.103085] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.104092] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.104097] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.104101] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.104106] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfeafffff]
[    1.104126] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    1.104158] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    1.104193] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    1.104211] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd03fffff 64bit]
[    1.104222] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.104231] pci 0000:00:02.0: reg 20: [io  0x3050-0x3057]
[    1.104329] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    1.104366] pci 0000:00:16.0: reg 10: [mem 0xd4406100-0xd440610f 64bit]
[    1.104497] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.104505] pci 0000:00:16.0: PME# disabled
[    1.104559] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    1.105002] pci 0000:00:1a.0: reg 10: [mem 0xd4405c00-0xd4405fff]
[    1.107493] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.107500] pci 0000:00:1a.0: PME# disabled
[    1.107544] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    1.107572] pci 0000:00:1b.0: reg 10: [mem 0xd4400000-0xd4403fff 64bit]
[    1.107693] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.107700] pci 0000:00:1b.0: PME# disabled
[    1.107736] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    1.107862] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.107869] pci 0000:00:1c.0: PME# disabled
[    1.107906] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    1.108031] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.108038] pci 0000:00:1c.1: PME# disabled
[    1.108092] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    1.108517] pci 0000:00:1d.0: reg 10: [mem 0xd4405800-0xd4405bff]
[    1.111003] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.111009] pci 0000:00:1d.0: PME# disabled
[    1.111041] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    1.111150] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
[    1.111313] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
[    1.111349] pci 0000:00:1f.2: reg 10: [io  0x3048-0x304f]
[    1.111363] pci 0000:00:1f.2: reg 14: [io  0x305c-0x305f]
[    1.111378] pci 0000:00:1f.2: reg 18: [io  0x3040-0x3047]
[    1.111393] pci 0000:00:1f.2: reg 1c: [io  0x3058-0x305b]
[    1.111408] pci 0000:00:1f.2: reg 20: [io  0x3020-0x303f]
[    1.111424] pci 0000:00:1f.2: reg 24: [mem 0xd4405000-0xd44057ff]
[    1.111507] pci 0000:00:1f.2: PME# supported from D3hot
[    1.111514] pci 0000:00:1f.2: PME# disabled
[    1.111544] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    1.111570] pci 0000:00:1f.3: reg 10: [mem 0xd4406000-0xd44060ff 64bit]
[    1.111608] pci 0000:00:1f.3: reg 20: [io  0x3000-0x301f]
[    1.111675] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    1.111712] pci 0000:00:1f.6: reg 10: [mem 0xd4404000-0xd4404fff 64bit]
[    1.111929] pci 0000:01:00.0: [1969:1073] type 0 class 0x000200
[    1.111963] pci 0000:01:00.0: reg 10: [mem 0xd3400000-0xd343ffff 64bit]
[    1.111983] pci 0000:01:00.0: reg 18: [io  0x2000-0x207f]
[    1.112132] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.112141] pci 0000:01:00.0: PME# disabled
[    1.118997] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.119009] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.119021] pci 0000:00:1c.0:   bridge window [mem 0xd3400000-0xd43fffff]
[    1.119036] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    1.119171] pci 0000:02:00.0: [14e4:4358] type 0 class 0x000280
[    1.119207] pci 0000:02:00.0: reg 10: [mem 0xd2400000-0xd2403fff 64bit]
[    1.119395] pci 0000:02:00.0: supports D1 D2
[    1.119398] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.119406] pci 0000:02:00.0: PME# disabled
[    1.127021] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.127032] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    1.127039] pci 0000:00:1c.1:   bridge window [mem 0xd2400000-0xd33fffff]
[    1.127050] pci 0000:00:1c.1:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    1.127153] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    1.127170] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.127175] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.127178] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.127182] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
[    1.127212] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.127450] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.127573] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.127634] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.127783] \_SB_.PCI0:_OSC invalid UUID
[    1.127786] _OSC request data:1 1f 1f 
[    1.127793]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.127847] \_SB_.PCI0:_OSC invalid UUID
[    1.127849] _OSC request data:1 0 1d 
[    1.127856]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.127859] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.134857] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    1.134982] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    1.135016] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    1.135050] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    1.135080] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    1.135109] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    1.135142] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    1.135197]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
[    1.135201]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    1.135204] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.135580] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.135653] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.135725] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.135796] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.135866] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.135937] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.136010] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.136081] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    1.136254] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.136269] vgaarb: loaded
[    1.136271] vgaarb: bridge control possible 0000:00:02.0
[    1.136435] i2c-core: driver [aat2870] using legacy suspend method
[    1.136438] i2c-core: driver [aat2870] using legacy resume method
[    1.136539] SCSI subsystem initialized
[    1.136622] libata version 3.00 loaded.
[    1.136691] usbcore: registered new interface driver usbfs
[    1.136707] usbcore: registered new interface driver hub
[    1.136748] usbcore: registered new device driver usb
[    1.136892] PCI: Using ACPI for IRQ routing
[    1.148792] PCI: pci_cache_line_size set to 64 bytes
[    1.148925] reserve RAM buffer: 000000000009d000 - 000000000009ffff 
[    1.148929] reserve RAM buffer: 00000000b363f000 - 00000000b3ffffff 
[    1.148933] reserve RAM buffer: 00000000b3800000 - 00000000b3ffffff 
[    1.149078] NetLabel: Initializing
[    1.149080] NetLabel:  domain hash size = 128
[    1.149082] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.149100] NetLabel:  unlabeled traffic allowed by default
[    1.149185] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.149195] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.151228] Switching to clocksource hpet
[    1.161309] AppArmor: AppArmor Filesystem Enabled
[    1.161354] pnp: PnP ACPI init
[    1.161379] ACPI: bus type pnp registered
[    1.161954] pnp 00:00: [bus 00-fe]
[    1.161959] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.161962] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.161965] pnp 00:00: [io  0x0d00-0xffff window]
[    1.161969] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.161972] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.161976] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.161979] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.161982] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.161985] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.161988] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.161992] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.161995] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.161998] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.162001] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.162004] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.162007] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.162011] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.162017] pnp 00:00: [mem 0xc0000000-0xfeafffff window]
[    1.162020] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.162154] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.162257] pnp 00:01: [io  0x0000-0x001f]
[    1.162260] pnp 00:01: [io  0x0081-0x0091]
[    1.162263] pnp 00:01: [io  0x0093-0x009f]
[    1.162266] pnp 00:01: [io  0x00c0-0x00df]
[    1.162269] pnp 00:01: [dma 4]
[    1.162314] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.162327] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.162365] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.162524] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.162570] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.162587] pnp 00:04: [io  0x00f0]
[    1.162603] pnp 00:04: [irq 13]
[    1.162645] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.162663] pnp 00:05: [io  0x002e-0x002f]
[    1.162666] pnp 00:05: [io  0x004e-0x004f]
[    1.162669] pnp 00:05: [io  0x0061]
[    1.162671] pnp 00:05: [io  0x0063]
[    1.162674] pnp 00:05: [io  0x0065]
[    1.162676] pnp 00:05: [io  0x0067]
[    1.162679] pnp 00:05: [io  0x0062]
[    1.162681] pnp 00:05: [io  0x0066]
[    1.162684] pnp 00:05: [io  0x0068-0x006f]
[    1.162686] pnp 00:05: [io  0x0070]
[    1.162689] pnp 00:05: [io  0x0080]
[    1.162691] pnp 00:05: [io  0x0092]
[    1.162694] pnp 00:05: [io  0x00b2-0x00b3]
[    1.162697] pnp 00:05: [io  0x0680-0x069f]
[    1.162700] pnp 00:05: [io  0x0800-0x080f]
[    1.162702] pnp 00:05: [io  0xffff]
[    1.162705] pnp 00:05: [io  0xffff]
[    1.162707] pnp 00:05: [io  0x0400-0x047f]
[    1.162710] pnp 00:05: [io  0x0500-0x057f]
[    1.162713] pnp 00:05: [io  0x164e-0x164f]
[    1.162734] pnp 00:05: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.1 BAR 13 [io  0x1000-0x1fff]
[    1.162807] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.162811] system 00:05: [io  0x0800-0x080f] has been reserved
[    1.162815] system 00:05: [io  0xffff] has been reserved
[    1.162818] system 00:05: [io  0xffff] has been reserved
[    1.162822] system 00:05: [io  0x0400-0x047f] has been reserved
[    1.162826] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.162831] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.162849] pnp 00:06: [io  0x0070-0x0077]
[    1.162857] pnp 00:06: [irq 8]
[    1.162900] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.162916] pnp 00:07: [io  0x0060]
[    1.162918] pnp 00:07: [io  0x0064]
[    1.162926] pnp 00:07: [irq 1]
[    1.162968] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.162986] pnp 00:08: [irq 12]
[    1.163031] pnp 00:08: Plug and Play ACPI device, IDs SYN1b22 SYN1b00 SYN0002 PNP0f13 (active)
[    1.163535] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    1.163539] pnp 00:09: [mem 0xfed10000-0xfed13fff]
[    1.163542] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    1.163545] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    1.163547] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    1.163553] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    1.163557] pnp 00:09: [mem 0xfed90000-0xfed8ffff disabled]
[    1.163560] pnp 00:09: [mem 0xfed45000-0xfed8ffff]
[    1.163563] pnp 00:09: [mem 0xff000000-0xffffffff]
[    1.163565] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    1.163568] pnp 00:09: [mem 0xd4500000-0xd4500fff]
[    1.163665] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.163669] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    1.163674] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.163678] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.163682] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    1.163686] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.163690] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.163694] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    1.163698] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.163703] system 00:09: [mem 0xd4500000-0xd4500fff] has been reserved
[    1.163708] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.163923] pnp 00:0a: [bus ff]
[    1.163997] pnp 00:0a: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.164024] pnp: PnP ACPI: found 11 devices
[    1.164026] ACPI: ACPI bus type pnp unregistered
[    1.172043] PCI: max bus depth: 1 pci_try_num: 2
[    1.172089] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.172094] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.172103] pci 0000:00:1c.0:   bridge window [mem 0xd3400000-0xd43fffff]
[    1.172111] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    1.172122] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.172127] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    1.172136] pci 0000:00:1c.1:   bridge window [mem 0xd2400000-0xd33fffff]
[    1.172143] pci 0000:00:1c.1:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    1.172154] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    1.172195] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.172204] pci 0000:00:1c.0: setting latency timer to 64
[    1.172221] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.172228] pci 0000:00:1c.1: setting latency timer to 64
[    1.172240] pci 0000:00:1e.0: setting latency timer to 64
[    1.172247] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.172250] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.172254] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.172258] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfeafffff]
[    1.172261] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    1.172265] pci_bus 0000:01: resource 1 [mem 0xd3400000-0xd43fffff]
[    1.172269] pci_bus 0000:01: resource 2 [mem 0xd0400000-0xd13fffff 64bit pref]
[    1.172274] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    1.172277] pci_bus 0000:02: resource 1 [mem 0xd2400000-0xd33fffff]
[    1.172281] pci_bus 0000:02: resource 2 [mem 0xd1400000-0xd23fffff 64bit pref]
[    1.172286] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    1.172290] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    1.172293] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    1.172297] pci_bus 0000:03: resource 7 [mem 0xc0000000-0xfeafffff]
[    1.172354] NET: Registered protocol family 2
[    1.172555] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.173823] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.176372] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.176643] TCP: Hash tables configured (established 524288 bind 65536)
[    1.176646] TCP reno registered
[    1.176661] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.176695] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.176859] NET: Registered protocol family 1
[    1.176883] pci 0000:00:02.0: Boot video device
[    1.176909] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.191256] pci 0000:00:1a.0: PCI INT A disabled
[    1.191296] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.207235] pci 0000:00:1d.0: PCI INT A disabled
[    1.207321] PCI: CLS 64 bytes, default 64
[    1.207324] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.207328] Placing 64MB software IO TLB between ffff8800af639000 - ffff8800b3639000
[    1.207331] software IO TLB at phys 0xaf639000 - 0xb3639000
[    1.207346] Simple Boot Flag at 0x44 set to 0x1
[    1.207893] audit: initializing netlink socket (disabled)
[    1.207910] type=2000 audit(1352814706.056:1): initialized
[    1.248913] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.252161] VFS: Disk quotas dquot_6.5.2
[    1.252247] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.253039] fuse init (API version 7.17)
[    1.253185] msgmni has been set to 7249
[    1.253694] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.253732] io scheduler noop registered
[    1.253735] io scheduler deadline registered
[    1.253793] io scheduler cfq registered (default)
[    1.254109] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.254143] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.254220] intel_idle: MWAIT substates: 0x1120
[    1.254223] intel_idle: v0.4 model 0x25
[    1.254225] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.255276] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.257305] ACPI: AC Adapter [ADP1] (off-line)
[    1.257471] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    1.257480] ACPI: Sleep Button [SLPB]
[    1.257545] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.261627] ACPI: Lid Switch [LID0]
[    1.261701] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.261707] ACPI: Power Button [PWRF]
[    1.290902] thermal LNXTHERM:00: registered as thermal_zone0
[    1.290906] ACPI: Thermal Zone [TZS0] (47 C)
[    1.302283] thermal LNXTHERM:01: registered as thermal_zone1
[    1.302287] ACPI: Thermal Zone [TZS1] (36 C)
[    1.302316] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.302328] ACPI: Battery Slot [BAT0] (battery present)
[    1.302372] ERST: Table is not found!
[    1.302375] GHES: HEST is not enabled!
[    1.302477] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.453403] ACPI: Battery Slot [BAT0] (battery present)
[    1.483741] Linux agpgart interface v0.103
[    1.483863] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.484037] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.485037] agpgart-intel 0000:00:00.0: detected 131072K stolen memory
[    1.485267] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.487472] brd: module loaded
[    1.488685] loop: module loaded
[    1.488884] ahci 0000:00:1f.2: version 3.0
[    1.488917] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.488992] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.489065] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    1.489071] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    1.489079] ahci 0000:00:1f.2: setting latency timer to 64
[    1.489679] scsi0 : ahci
[    1.489826] scsi1 : ahci
[    1.489942] scsi2 : ahci
[    1.490062] scsi3 : ahci
[    1.490140] ata1: SATA max UDMA/133 abar m2048@0xd4405000 port 0xd4405100 irq 40
[    1.490143] ata2: DUMMY
[    1.490145] ata3: DUMMY
[    1.490147] ata4: DUMMY
[    1.490681] Fixed MDIO Bus: probed
[    1.490713] tun: Universal TUN/TAP device driver, 1.6
[    1.490716] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.490807] PPP generic driver version 2.4.2
[    1.490971] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.490997] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.491020] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.491025] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.491100] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.491139] ehci_hcd 0000:00:1a.0: debug port 2
[    1.495038] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.495060] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xd4405c00
[    1.507240] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.507454] hub 1-0:1.0: USB hub found
[    1.507461] hub 1-0:1.0: 3 ports detected
[    1.507559] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.507581] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.507586] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.507658] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.507691] ehci_hcd 0000:00:1d.0: debug port 2
[    1.511610] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.511630] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xd4405800
[    1.527239] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.527424] hub 2-0:1.0: USB hub found
[    1.527430] hub 2-0:1.0: 3 ports detected
[    1.527527] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.527546] uhci_hcd: USB Universal Host Controller Interface driver
[    1.527613] usbcore: registered new interface driver libusual
[    1.527668] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.552901] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.552911] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.553095] mousedev: PS/2 mouse device common for all mice
[    1.554282] rtc_cmos 00:06: RTC can wake from S4
[    1.554430] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.554467] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.554582] device-mapper: uevent: version 1.0.3
[    1.554689] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    1.554777] cpuidle: using governor ladder
[    1.554897] cpuidle: using governor menu
[    1.554900] EFI Variables Facility v0.08 2004-May-17
[    1.555261] TCP cubic registered
[    1.555423] NET: Registered protocol family 10
[    1.556170] NET: Registered protocol family 17
[    1.556177] Registering the dns_resolver key type
[    1.556644] PM: Hibernation image not present or could not be loaded.
[    1.556661] registered taskstats version 1
[    1.567779]   Magic number: 4:724:887
[    1.567854] pci 0000:00:1f.0: hash matches
[    1.567957] rtc_cmos 00:06: setting system clock to 2012-11-13 13:51:46 UTC (1352814706)
[    1.568654] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.568657] EDD information not available.
[    1.582682] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.807332] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.809828] ata1.00: ATA-8: WDC WD5000BEVT-22A0RT0, 01.01A01, max UDMA/133
[    1.809834] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.812455] ata1.00: configured for UDMA/133
[    1.812805] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-2 01.0 PQ: 0 ANSI: 5
[    1.813046] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.813093] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.813308] sd 0:0:0:0: [sda] Write Protect is off
[    1.813314] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.813495] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.819375] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.874917]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.876549] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.879203] Freeing unused kernel memory: 924k freed
[    1.879439] Write protecting the kernel read-only data: 12288k
[    1.888392] Freeing unused kernel memory: 1612k freed
[    1.895247] Freeing unused kernel memory: 1200k freed
[    1.924840] udevd[93]: starting version 175
[    1.951968] hub 1-1:1.0: USB hub found
[    1.952034] hub 1-1:1.0: 6 ports detected
[    1.982322] [drm] Initialized drm 1.1.0 20060810
[    1.996663] atl1c 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.996680] atl1c 0000:01:00.0: setting latency timer to 64
[    2.000508] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.000515] i915 0000:00:02.0: setting latency timer to 64
[    2.089697] wmi: Mapper loaded
[    2.096194] mtrr: no more MTRRs available
[    2.096199] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    2.096732] i915 0000:00:02.0: irq 41 for MSI/MSI-X
[    2.096740] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.096742] [drm] Driver supports precise vblank timestamp query.
[    2.096792] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.158682] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.207321] Refined TSC clocksource calibration: 1329.950 MHz.
[    2.207336] Switching to clocksource tsc
[    2.228256] atl1c 0000:01:00.0: version 1.0.1.0-NAPI
[    2.288539] hub 2-1:1.0: USB hub found
[    2.288779] hub 2-1:1.0: 8 ports detected
[    2.359586] usb 1-1.4: new full-speed USB device number 3 using ehci_hcd
[    2.559533] usb 2-1.5: new high-speed USB device number 3 using ehci_hcd
[    2.748975] fbcon: inteldrmfb (fb0) is primary device
[    2.749063] Console: switching to colour frame buffer device 170x48
[    2.749103] fb0: inteldrmfb frame buffer device
[    2.749105] drm: registered panic notifier
[    2.770085] acpi device:02: registered as cooling_device2
[    2.770603] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    2.770664] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.770715] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.794672] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   35.788356] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.811359] udevd[450]: starting version 175
[   35.837142] lp: driver loaded but no devices found
[   35.844081] lib80211: common routines for IEEE802.11 drivers
[   35.844086] lib80211_crypt: registered algorithm 'NULL'
[   35.846883] wl: module license 'unspecified' taints kernel.
[   35.846889] Disabling lock debugging due to kernel taint
[   35.859914] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   35.859926] wl 0000:02:00.0: setting latency timer to 64
[   35.907278] lib80211_crypt: registered algorithm 'TKIP'
[   35.992579] eth1: Broadcom BCM4358 802.11 Hybrid Wireless Controller 5.100.82.112
[   36.114013] type=1400 audit(1352843541.042:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=563 comm="apparmor_parser"
[   36.114680] type=1400 audit(1352843541.042:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=563 comm="apparmor_parser"
[   36.115068] type=1400 audit(1352843541.042:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=563 comm="apparmor_parser"
[   36.162392] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   36.178389] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   36.179475] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   36.179486] mei 0000:00:16.0: setting latency timer to 64
[   36.183689] mei 0000:00:16.0: irq 42 for MSI/MSI-X
[   36.216773] Bluetooth: Core ver 2.16
[   36.216856] NET: Registered protocol family 31
[   36.216860] Bluetooth: HCI device and connection manager initialized
[   36.216864] Bluetooth: HCI socket layer initialized
[   36.216867] Bluetooth: L2CAP socket layer initialized
[   36.216876] Bluetooth: SCO socket layer initialized
[   36.217525] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   36.220728] usbcore: registered new interface driver btusb
[   36.305153] intel ips 0000:00:1f.6: No CPUID match found.
[   36.305159] intel ips 0000:00:1f.6: IPS not supported on this CPU
[   36.325924] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   36.418469] Linux video capture interface: v2.00
[   36.419274] uvcvideo: Found UVC 1.00 device 1.3M WebCam (04f2:b1d8)
[   36.520898] input: 1.3M WebCam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input5
[   36.521068] usbcore: registered new interface driver uvcvideo
[   36.521072] USB Video Class driver (1.1.1)
[   36.607374] acer_wmi: Acer Laptop ACPI-WMI Extras
[   36.607397] acer_wmi: Function bitmap for Communication Button: 0x801
[   36.625372] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   36.625456] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   36.625494] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   36.632577] acer_wmi: Brightness must be controlled by generic video driver
[   36.635843] input: Acer WMI hotkeys as /devices/virtual/input/input6
[   36.677575] HDMI status: Codec=3 Pin=4 Presence_Detect=0 ELD_Valid=0
[   36.677688] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   36.677809] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   36.677915] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   36.721944] init: failsafe main process (840) killed by TERM signal
[   36.748324] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.748329] Bluetooth: BNEP filters: protocol multicast
[   36.754247] Bluetooth: RFCOMM TTY layer initialized
[   36.754255] Bluetooth: RFCOMM socket layer initialized
[   36.754258] Bluetooth: RFCOMM ver 1.11
[   36.758360] ppdev: user-space parallel port driver
[   37.027456] type=1400 audit(1352843541.954:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1004 comm="apparmor_parser"
[   37.031823] type=1400 audit(1352843541.958:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1004 comm="apparmor_parser"
[   37.089839] type=1400 audit(1352843542.018:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1032 comm="apparmor_parser"
[   37.093015] type=1400 audit(1352843542.018:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1031 comm="apparmor_parser"
[   37.094885] type=1400 audit(1352843542.022:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1032 comm="apparmor_parser"
[   37.095276] type=1400 audit(1352843542.022:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1032 comm="apparmor_parser"
[   37.116080] type=1400 audit(1352843542.042:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1036 comm="apparmor_parser"
[   37.172407] atl1c 0000:01:00.0: irq 44 for MSI/MSI-X
[   37.259095] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.264313] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.268185] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0400
[   37.327455] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   38.915022] init: anacron main process (1202) killed by TERM signal
[   39.547910] wl 0000:02:00.0: PCI INT A disabled
[   39.567508] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   39.567524] wl 0000:02:00.0: setting latency timer to 64
[   39.690456] eth1: Broadcom BCM4358 802.11 Hybrid Wireless Controller 5.100.82.112
[   39.753091] init: plymouth-stop pre-start process (1659) terminated with status 1
[   40.809455] Adding 4886524k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:4886524k 
[   52.078292] eth1: no IPv6 routers present
[  162.363245] wl 0000:02:00.0: PCI INT A disabled
[  172.966312] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  172.966327] wl 0000:02:00.0: setting latency timer to 64
[  173.052810] eth1: Broadcom BCM4358 802.11 Hybrid Wireless Controller 5.100.82.112
[  205.023488] eth1: no IPv6 routers present

---

