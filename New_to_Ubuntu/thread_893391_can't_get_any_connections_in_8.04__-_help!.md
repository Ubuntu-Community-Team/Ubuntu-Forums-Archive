---
title: "can't get any connections in 8.04  - help!"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Confused Vorlon on 2008-08-18
I couldn't get 8.04 to run in live cd mode, so I started with 6.02lts

in 6.02 I was able to connect by ethernet and wireless (open network only)

I hit the update button and updated to 8.04.

delighted to see that it works ok on my laptop (averatec 3200 3225hs) however I can't get any network connection at all.

I have tried various combinations for ethernet
-dhcp
-static
-roaming (not sure what this is!)

it seems that the os just isn't talking to the network card though as I can't even ping my gateway

network is cable connected to wrt54g (the wrt54g isn't seeing the laptop, or at least isn't giving it a dhcp lease)

I get a similar story for wireless, I can specify a network (that was previously working in 6.02) but the laptop doesn't seem to negotiate a lease and I see zero bars.

I tried turning off ipv6 but that didn't seem to make any difference.

I'm new to this. My laptop is now ubuntu only (and unconnected).

Help appreciated.

as requested in the 'how to get help post', here are some details

rob@rob-laptop:~$ ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:40:45:19:70:a2  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x2e00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2000 (1.9 KB)  TX bytes:2000 (1.9 KB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:07:d5:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-09-07-D5-4D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
rob@rob-laptop:~$ lspci
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 20)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
rob@rob-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

rob@rob-laptop:~$ lshw -C network

```

WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wmaster0
       version: 01
       serial: 00:11:09:07:d5:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:19:70:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes

```

---

### Post by hyper_ch on 2008-08-18
(1) when posting content of files or output from the terminal put it in [noparse]```

```[/noparse] brackets. Makes it easier to read.

(2) what's the output of
```

iwconfig

```
and
```

ifconfig

```

---

### Post by Confused Vorlon on 2008-08-18
ok, I have updated my original post.

ifconfig is above iwconfig follows

rob@rob-laptop:~$ iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

ra0       IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by hyper_ch on 2008-08-18
there we go ;) you did not specify a ESSID in the wifi setup.

---

### Post by Confused Vorlon on 2008-08-18
> **hyper_ch said:**
> there we go ;) you did not specify a ESSID in the wifi setup.

thanks, but that's not the issue. At the moment, the wifi settings were on roaming, just because that is the last thing I tried. 

The pressing issue is that I can't even connect on ethernet. 

I'll repost my settings with wifi set up for my local network anyway.

---

### Post by hyper_ch on 2008-08-18
why don't you set a ESSID?

---

### Post by Confused Vorlon on 2008-08-18
well one interesting thing on the repost. 
when I set my ssid as Kruschev and give the wpa key, then I get no essid in iwconfig

when I set as homenet17013 and leave the hex password blank (there is no password - is this the correct way to specify an open network?) then I do get an essid

latter posted below. Note this is the wireless network that I was able to connect to on 6.02

rob@rob-laptop:~$ iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

ra0       IEEE 802.11g  ESSID:"homenet17013"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

rob@rob-laptop:~$ ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:40:45:19:70:a2  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:44 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x2e00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4288 (4.1 KB)  TX bytes:4288 (4.1 KB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:07:d5:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ra0:avahi Link encap:Ethernet  HWaddr 00:11:09:07:d5:4d  
          inet addr:169.254.5.14  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-11-09-07-D5-4D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by Confused Vorlon on 2008-08-18
anyone have any ideas?

specifically - can I make use of the fact that 6.02 worked to get 8.04 working?

I currently have no ethernet and no wifi

---

### Post by hyper_ch on 2008-08-18
try to connect without any encryption first

---

### Post by Confused Vorlon on 2008-08-18
> **hyper_ch said:**
> try to connect without any encryption first


How would that help me to get an ethernet connection????

fwiw - I do not think I have any encryption on my ethernet network.

I assume though that you are still referring to the wifi connection.

1) the network I am trying to connect to _is_ open

when I configure it in the network app, there is no option for 'no encryption' so I have selected hex wep and entered no password as described in the post/question above

> 
when I set as homenet17013 and leave the hex password blank (there is no password - is this the correct way to specify an open network?)


forgive me if I sound testy. I realise you are helping me out of the goodness of your heart. I'm just getting a bit frustrated that the assumption seems to be that I'm setting up my wifi wrong when my main desire is just to get ethernet working. I may be making a basic error on the wifi setting, but that was why I posed the question above (some posts back)

---

### Post by Confused Vorlon on 2008-08-18
anyone else got any ideas?

why would ethernet and wifi work on 6.02 but both die as soon as I upgrade to 8.04

---

### Post by Confused Vorlon on 2008-08-18
anyone?

---

### Post by Confused Vorlon on 2008-08-18
fwiw - here is the output of dmesg too

```

[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-386 (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 Fri Jul 11 22:45:14 UTC 2008 (Ubuntu 2.6.24-19.36-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003dff0000 (usable)
[    0.000000]  BIOS-e820: 000000003dff0000 - 000000003dff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003dff8000 - 000000003e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 95MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 253936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   253936
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   253936
[    0.000000] On node 0 totalpages: 253936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 191 pages used for memmap
[    0.000000]   HighMem zone: 24369 pages, LIFO batch:3
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA2D0 checksum 0
[    0.000000] ACPI: RSDP 000FA2D0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 3DFF0000, 0028 (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 3DFF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 3DFF00C0, 46E7 (r1    VIA   VIA_K7     1000 INTL  2002024)
[    0.000000] ACPI: FACS 3DFF8000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3e000000:c1f80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 00000000000d6000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d6000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 251953
[    0.000000] Kernel command line: root=UUID=2db6b4a0-499b-4ac0-8f62-a0ccb4a63666 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (017c4000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1525.877 MHz processor.
[   14.868507] Console: colour VGA+ 80x25
[   14.868513] console [tty0] enabled
[   14.869779] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.870616] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.911555] Memory: 994424k/1015744k available (2079k kernel code, 20716k reserved, 973k data, 364k init, 98240k highmem)
[   14.911567] virtual kernel memory layout:
[   14.911568]     fixmap  : 0xfffa6000 - 0xfffff000   ( 356 kB)
[   14.911570]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.911571]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.911573]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.911575]       .init : 0xc03fe000 - 0xc0459000   ( 364 kB)
[   14.911576]       .data : 0xc0307d94 - 0xc03fb3a4   ( 973 kB)
[   14.911578]       .text : 0xc0100000 - 0xc0307d94   (2079 kB)
[   14.911582] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.911670] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.991697] Calibrating delay using timer specific routine.. 3055.49 BogoMIPS (lpj=6110994)
[   14.991746] Security Framework initialized
[   14.991762] SELinux:  Disabled at boot.
[   14.991786] AppArmor: AppArmor initialized
[   14.991794] Failure registering capabilities with primary security module.
[   14.991804] Mount-cache hash table entries: 512
[   14.992001] Initializing cgroup subsys ns
[   14.992007] Initializing cgroup subsys cpuacct
[   14.992022] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   14.992033] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.992037] CPU: L2 Cache: 512K (64 bytes/line)
[   14.992040] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000 00000000
[   14.992057] Compat vDSO mapped to ffffe000.
[   14.992075] CPU: AMD mobile AMD Athlon(tm) XP-M (LV) 2000+ stepping 00
[   14.992084] Checking 'hlt' instruction... OK.
[   15.009361] Freeing SMP alternatives: 0k freed
[   15.009536] Early unpacking initramfs... done
[   15.484728] ACPI: Core revision 20070126
[   15.484891] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.486907] ACPI: setting ELCR to 0200 (from 0c00)
[   15.499120] net_namespace: 64 bytes
[   15.499132] Booting paravirtualized kernel on bare hardware
[   15.499764] Time: 12:14:58  Date: 08/18/08
[   15.499813] NET: Registered protocol family 16
[   15.500092] EISA bus registered
[   15.500113] ACPI: bus type pci registered
[   15.501785] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[   15.501788] PCI: Using configuration type 1
[   15.501796] Setting up standard PCI resources
[   15.516975] ACPI: EC: Look up EC in DSDT
[   15.520329] ACPI: Interpreter enabled
[   15.520333] ACPI: (supports S0 S3 S4 S5)
[   15.520350] ACPI: Using PIC for interrupt routing
[   15.522193] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.524459] ACPI: EC: GPE = 0x4, I/O: command/status = 0x66, data = 0x62
[   15.524463] ACPI: EC: driver started in interrupt mode
[   15.524515] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.525028] PCI quirk: region 0800-087f claimed by vt8235 PM
[   15.525033] PCI quirk: region 0400-040f claimed by vt8235 SMB
[   15.525459] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.525613] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   15.529279] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *11 14 15)
[   15.529390] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 5 9 14 15) *0, disabled.
[   15.529500] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 12)
[   15.529607] ACPI: PCI Interrupt Link [LNKD] (IRQs 6 7) *0, disabled.
[   15.529738] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.529780] pnp: PnP ACPI init
[   15.529790] ACPI: bus type pnp registered
[   15.531392] pnp: PnP ACPI: found 9 devices
[   15.531395] ACPI: ACPI bus type pnp unregistered
[   15.531401] PnPBIOS: Disabled by ACPI PNP
[   15.531829] PCI: Using ACPI for IRQ routing
[   15.531833] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.547654] NET: Registered protocol family 8
[   15.547657] NET: Registered protocol family 20
[   15.547757] AppArmor: AppArmor Filesystem Enabled
[   15.551641] Time: tsc clocksource has been installed.
[   15.559685] system 00:01: ioport range 0x3f0-0x3f1 has been reserved
[   15.559689] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   15.559693] system 00:01: ioport range 0x400-0x40f has been reserved
[   15.559697] system 00:01: ioport range 0x820-0x821 has been reserved
[   15.559700] system 00:01: ioport range 0x862-0x862 has been reserved
[   15.559704] system 00:01: ioport range 0x866-0x866 has been reserved
[   15.559714] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[   15.559718] system 00:08: iomem range 0xd0000-0xd5fff could not be reserved
[   15.559721] system 00:08: iomem range 0xf0000-0xfffff could not be reserved
[   15.559725] system 00:08: iomem range 0x100000-0x3fffffff could not be reserved
[   15.559729] system 00:08: iomem range 0xfff80000-0xffffffff could not be reserved
[   15.590265] PCI: Bridge: 0000:00:01.0
[   15.590268]   IO window: disabled.
[   15.590273]   MEM window: dde00000-dfefffff
[   15.590277]   PREFETCH window: d5d00000-ddcfffff
[   15.590283] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[   15.590286]   IO window: 00001000-000010ff
[   15.590290]   IO window: 00001400-000014ff
[   15.590294]   PREFETCH window: 40000000-43ffffff
[   15.590298]   MEM window: 44000000-47ffffff
[   15.590322] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.590497] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   15.590502] PCI: setting IRQ 10 as level-triggered
[   15.590508] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   15.590528] NET: Registered protocol family 2
[   15.627720] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.628297] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.630823] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   15.631587] TCP: Hash tables configured (established 131072 bind 65536)
[   15.631591] TCP reno registered
[   15.639866] checking if image is initramfs... it is
[   16.091618] Switched to high resolution mode on CPU 0
[   16.535229] Freeing initrd memory: 8125k freed
[   16.536083] audit: initializing netlink socket (disabled)
[   16.536108] audit(1219061698.620:1): initialized
[   16.536322] highmem bounce pool size: 64 pages
[   16.538585] VFS: Disk quotas dquot_6.5.1
[   16.538616] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.538807] io scheduler noop registered
[   16.538810] io scheduler anticipatory registered
[   16.538813] io scheduler deadline registered
[   16.538826] io scheduler cfq registered (default)
[   16.538841] PCI: VIA PCI bridge detected. Disabling DAC.
[   16.538909] Boot video device is 0000:01:00.0
[   16.539261] isapnp: Scanning for PnP cards...
[   16.893443] isapnp: No Plug & Play device found
[   16.930537] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.932001] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.932095] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.932211] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.934694] i8042.c: Detected active multiplexing controller, rev 1.1.
[   16.935874] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.935880] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   16.935884] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   16.935887] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   16.935890] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   16.947445] mice: PS/2 mouse device common for all mice
[   16.947586] EISA: Probing bus 0 at eisa.0
[   16.947597] Cannot allocate resource for EISA slot 1
[   16.947628] EISA: Detected 0 cards.
[   16.947633] cpuidle: using governor ladder
[   16.947829] NET: Registered protocol family 1
[   16.947865] Using IPI Shortcut mode
[   16.947919] registered taskstats version 1
[   16.948045]   Magic number: 4:803:228
[   16.948146]   hash matches device ttyrf
[   16.948369] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.948372] EDD information not available.
[   16.949068] Freeing unused kernel memory: 364k freed
[   16.983383] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   18.239254] fuse init (API version 7.9)
[   18.271036] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.398325] ACPI: Thermal Zone [THRM] (0 C)
[   18.422260] device-mapper: uevent: version 1.0.3
[   18.422330] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   18.447835] md: linear personality registered for level -1
[   18.454904] md: multipath personality registered for level -4
[   18.461699] md: raid0 personality registered for level 0
[   18.469463] md: raid1 personality registered for level 1
[   18.476269] xor: automatically using best checksumming function: pIII_sse
[   18.495068]    pIII_sse  :  2530.000 MB/sec
[   18.495072] xor: using function: pIII_sse (2530.000 MB/sec)
[   18.496323] async_tx: api initialized (async)
[   18.567146] raid6: int32x1    511 MB/s
[   18.635069] raid6: int32x2    590 MB/s
[   18.703066] raid6: int32x4    537 MB/s
[   18.771089] raid6: int32x8    485 MB/s
[   18.839041] raid6: mmxx1     1215 MB/s
[   18.906993] raid6: mmxx2     2048 MB/s
[   18.975017] raid6: sse1x1    1174 MB/s
[   19.042977] raid6: sse1x2    1617 MB/s
[   19.042980] raid6: using algorithm sse1x2 (1617 MB/s)
[   19.042984] md: raid6 personality registered for level 6
[   19.042986] md: raid5 personality registered for level 5
[   19.042989] md: raid4 personality registered for level 4
[   19.084671] md: raid10 personality registered for level 10
[   19.814981] usbcore: registered new interface driver usbfs
[   19.815016] usbcore: registered new interface driver hub
[   19.830892] usbcore: registered new device driver usb
[   19.832333] USB Universal Host Controller Interface driver v3.0
[   19.832675] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
[   19.832680] PCI: setting IRQ 7 as level-triggered
[   19.832687] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[   19.832696] PCI: VIA VLink IRQ fixup for 0000:00:10.0, from 0 to 7
[   19.832724] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   19.833171] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   19.833205] uhci_hcd 0000:00:10.0: irq 7, io base 0x0000e400
[   19.833402] usb usb1: configuration #1 chosen from 1 choice
[   19.833435] hub 1-0:1.0: USB hub found
[   19.833445] hub 1-0:1.0: 2 ports detected
[   19.911206] SCSI subsystem initialized
[   19.934989] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[   19.935001] PCI: VIA VLink IRQ fixup for 0000:00:10.1, from 0 to 7
[   19.935032] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   19.935063] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   19.935092] uhci_hcd 0000:00:10.1: irq 7, io base 0x0000e800
[   19.935251] usb usb2: configuration #1 chosen from 1 choice
[   19.935287] hub 2-0:1.0: USB hub found
[   19.935296] hub 2-0:1.0: 2 ports detected
[   19.952808] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   19.973537] libata version 3.00 loaded.
[   20.038963] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[   20.038974] PCI: VIA VLink IRQ fixup for 0000:00:10.2, from 0 to 7
[   20.039006] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   20.039045] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   20.039074] uhci_hcd 0000:00:10.2: irq 7, io base 0x0000ec00
[   20.039240] usb usb3: configuration #1 chosen from 1 choice
[   20.039271] hub 3-0:1.0: USB hub found
[   20.039280] hub 3-0:1.0: 2 ports detected
[   20.143120] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[   20.143132] PCI: VIA VLink IRQ fixup for 0000:00:10.3, from 0 to 7
[   20.143167] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   20.143201] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   20.143266] ehci_hcd 0000:00:10.3: irq 7, io mem 0xdfffdf00
[   20.154780] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.154949] usb usb4: configuration #1 chosen from 1 choice
[   20.154992] hub 4-0:1.0: USB hub found
[   20.155002] hub 4-0:1.0: 6 ports detected
[   20.259292] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   20.259299] PCI: setting IRQ 11 as level-triggered
[   20.259306] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   20.263607] eth0: VIA Rhine II at 0xdfffde00, 00:40:45:19:70:a2, IRQ 11.
[   20.264322] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link cde1.
[   20.268166] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   20.268257] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   20.271886] pata_via 0000:00:11.1: version 0.3.3
[   20.271905] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   20.273042] scsi0 : pata_via
[   20.274019] scsi1 : pata_via
[   20.275823] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   20.275828] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   20.459326] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD4A, max UDMA/100
[   20.459334] ata1.00: 78140160 sectors, multi 16: LBA48 
[   20.459350] ata1.00: limited to UDMA/33 due to 40-wire cable
[   20.475156] ata1.00: configured for UDMA/33
[   20.795012] ata2.00: ATAPI: Slimtype COMBO SOSC-2483K, KKD1, max UDMA/33
[   20.966842] ata2.00: configured for UDMA/33
[   20.967018] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5
[   20.968059] scsi 1:0:0:0: CD-ROM            Slimtype COMBO SOSC-2483K KKD1 PQ: 0 ANSI: 5
[   20.975885] Driver 'sd' needs updating - please use bus_type methods
[   20.976030] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   20.976051] sd 0:0:0:0: [sda] Write Protect is off
[   20.976055] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.976079] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.976145] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   20.976157] sd 0:0:0:0: [sda] Write Protect is off
[   20.976161] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.976179] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.976185]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   21.006163]  sda1 sda2 < sda5 >
[   21.032688] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.038564] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.038622] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   21.043206] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[   21.043216] Uniform CD-ROM driver Revision: 3.20
[   21.043305] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.441523] EXT3-fs: INFO: recovery required on readonly filesystem.
[   21.441529] EXT3-fs: write access will be enabled during recovery.
[   21.931292] kjournald starting.  Commit interval 5 seconds
[   21.931318] EXT3-fs: sda1: orphan cleanup on readonly fs
[   21.931328] ext3_orphan_cleanup: deleting unreferenced inode 2064434
[   21.931395] ext3_orphan_cleanup: deleting unreferenced inode 2064397
[   21.931403] EXT3-fs: sda1: 2 orphan inodes deleted
[   21.931405] EXT3-fs: recovery complete.
[   21.934646] EXT3-fs: mounted filesystem with ordered data mode.
[   37.451508] Real Time Clock Driver v1.12ac
[   37.544031] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   37.952963] Yenta: CardBus bridge found at 0000:00:0a.0 [14ff:c602]
[   37.952989] Yenta O2: res at 0x94/0xD4: 00/ea
[   37.952992] Yenta O2: enabling read prefetch/write burst
[   38.080112] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[   38.080120] Socket status: 30000006
[   38.081839] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.121894] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.126335] Linux agpgart interface v0.102
[   38.194852] irda_init()
[   38.194894] NET: Registered protocol family 23
[   38.244185] agpgart: Detected VIA KM400/KM400A chipset
[   38.250436] agpgart: AGP aperture is 64M @ 0xe0000000
[   38.428996] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[   38.466507] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input3
[   38.503507] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   38.591799] phy0: Selected rate control algorithm 'simple'
[   39.066055] input: Power Button (FF) as /devices/virtual/input/input4
[   39.079200] ACPI: Power Button (FF) [PWRF]
[   39.079350] input: Power Button (CM) as /devices/virtual/input/input5
[   39.095169] ACPI: Power Button (CM) [PWRB]
[   39.095359] input: Sleep Button (CM) as /devices/virtual/input/input6
[   39.111148] ACPI: Sleep Button (CM) [SLPB]
[   39.111230] input: Lid Switch as /devices/virtual/input/input7
[   39.111336] ACPI: Lid Switch [LIDD]
[   39.648063] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   39.651069] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   40.179561] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   40.179714] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   41.268176] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:06/LNXVIDEO:00/input/input8
[   41.294827] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   41.427067] ACPI: AC Adapter [AC] (on-line)
[   41.525277] ACPI: Battery Slot [BAT0] (battery present)
[   43.190736] udev: renamed network interface wlan0 to ra0
[   43.216933] cs: IO port probe 0x100-0x3af: clean.
[   43.219019] cs: IO port probe 0x3e0-0x4ff: clean.
[   43.219837] cs: IO port probe 0x820-0x8ff: clean.
[   43.220274] cs: IO port probe 0xc00-0xcf7: clean.
[   43.221191] cs: IO port probe 0xa00-0xaff: clean.
[   43.995489] lp: driver loaded but no devices found
[   44.366586] Adding 1622524k swap on /dev/sda5.  Priority:-1 extents:1 across:1622524k
[   44.932300] EXT3 FS on sda1, internal journal
[   46.094794] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.706169] NET: Registered protocol family 17
[   52.325849] No dock devices found.
[   52.846577] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[   52.940478] powernow: SGTC: 13333
[   52.940481] powernow: Minimum speed 398 MHz. Maximum speed 1525 MHz.
[   55.129488] [drm] Initialized drm 1.1.0 20060810
[   55.173812] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   55.173822] PCI: setting IRQ 9 as level-triggered
[   55.173827] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   55.174055] [drm] Initialized via 2.11.1 20070202 on minor 0
[   55.220368] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   55.220390] agpgart: BIOS bug. AGP bridge claims to only support x4 rateFixing up support for x2 & x1
[   55.220398] agpgart: Device is in legacy mode, falling back to 2.x
[   55.220406] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   55.220468] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   55.519449] ppdev: user-space parallel port driver
[   56.076994] audit(1219061739.231:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5005 profile="/usr/sbin/cupsd" namespace="default"
[   56.163478] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   56.163488] apm: overridden by ACPI.
[   81.205871] Marking TSC unstable due to: cpufreq changes.
[   81.211349] Time: acpi_pm clocksource has been installed.
[   56.872170] Clocksource tsc unstable (delta = -191766735 ns)
[   83.818190] irq 11: nobody cared (try booting with the "irqpoll" option)
[   83.818207] Pid: 4862, comm: NetworkManager Not tainted 2.6.24-19-386 #1
[   83.818252]  [<c0154da4>] __report_bad_irq+0x24/0x80
[   83.818274]  [<c0155014>] note_interrupt+0x214/0x250
[   83.818289]  [<c01543c0>] handle_IRQ_event+0x30/0x60
[   83.818302]  [<c0155a38>] handle_level_irq+0x58/0xa0
[   83.818312]  [<c0106527>] do_IRQ+0x37/0x70
[   83.818322]  [<f88c1e38>] rhine_interrupt+0x3b8/0x730 [via_rhine]
[   83.818347]  [<c0105183>] common_interrupt+0x23/0x30
[   83.818368]  [<c0124192>] __do_softirq+0x32/0xa0
[   83.818386]  [<c0124245>] do_softirq+0x45/0x50
[   83.818394]  [<c010652c>] do_IRQ+0x3c/0x70
[   83.818409]  [<c0105183>] common_interrupt+0x23/0x30
[   83.818430]  [<c01548de>] setup_irq+0xce/0x1a0
[   83.818440]  [<c0186470>] poll_freewait+0x20/0x60
[   83.818448]  [<c01194ff>] update_curr+0x9f/0x150
[   83.818466]  [<f88c1a80>] rhine_interrupt+0x0/0x730 [via_rhine]
[   83.818477]  [<c0154a4f>] request_irq+0x9f/0xc0
[   83.818491]  [<f88c3297>] rhine_open+0x47/0x1e0 [via_rhine]
[   83.818505]  [<c0103199>] __switch_to+0x89/0x140
[   83.818520]  [<c029740c>] dev_open+0x4c/0x80
[   83.818529]  [<c0296031>] dev_change_flags+0x81/0x190
[   83.818545]  [<c029e2ea>] do_setlink+0x27a/0x330
[   83.818553]  [<c01279d0>] process_timeout+0x0/0x10
[   83.818576]  [<c029f7c3>] rtnl_setlink+0xf3/0x120
[   83.818615]  [<c02aec1a>] netlink_dump_start+0xfa/0x120
[   83.818628]  [<c029f6d0>] rtnl_setlink+0x0/0x120
[   83.818634]  [<c029f3d2>] rtnetlink_rcv_msg+0x1d2/0x210
[   83.818641]  [<c029eb30>] rtnl_dump_ifinfo+0x0/0xa0
[   83.818657]  [<c029f200>] rtnetlink_rcv_msg+0x0/0x210
[   83.818663]  [<c029f1e0>] rtnetlink_rcv+0x0/0x20
[   83.818669]  [<c02ad98d>] netlink_rcv_skb+0x6d/0x90
[   83.818679]  [<c029f1f4>] rtnetlink_rcv+0x14/0x20
[   83.818687]  [<c02ad75b>] netlink_unicast+0x1cb/0x200
[   83.818692]  [<c01fd80e>] copy_from_user+0x2e/0x70
[   83.818715]  [<c02adfb2>] netlink_sendmsg+0x222/0x2f0
[   83.818743]  [<c028a321>] sock_sendmsg+0x111/0x130
[   83.818771]  [<c01316d0>] autoremove_wake_function+0x0/0x40
[   83.818793]  [<c01316d0>] autoremove_wake_function+0x0/0x40
[   83.818802]  [<c02983c7>] ethtool_get_value+0x37/0x50
[   83.818814]  [<c02992b1>] dev_ethtool+0xc51/0x1250
[   83.818820]  [<f88c35c0>] netdev_get_link+0x0/0x10 [via_rhine]
[   83.818842]  [<c01fd80e>] copy_from_user+0x2e/0x70
[   83.818851]  [<c01fd80e>] copy_from_user+0x2e/0x70
[   83.818868]  [<c028a499>] sys_sendmsg+0x159/0x270
[   83.818885]  [<c028b2fd>] sys_recvmsg+0x17d/0x230
[   83.818901]  [<c015df23>] get_page_from_freelist+0x263/0x3f0
[   83.818912]  [<c015b255>] filemap_fault+0x1b5/0x3b0
[   83.818946]  [<c028c609>] lock_sock_nested+0x79/0x80
[   83.818965]  [<c0118840>] kunmap_atomic+0x30/0xa0
[   83.818977]  [<c01672c4>] handle_mm_fault+0x354/0x680
[   83.819013]  [<c028b9d4>] sys_socketcall+0xb4/0x2b0
[   83.819039]  [<c0104132>] sysenter_past_esp+0x6b/0xa9
[   83.819070]  =======================
[   83.819072] handlers:
[   83.819075] [<f88c1a80>] (rhine_interrupt+0x0/0x730 [via_rhine])
[   83.819086] Disabling IRQ #11
[   83.819814] eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[   58.383082] input: Unspecified device as /devices/virtual/input/input9
[  636.198950] usb 1-2: new full speed USB device using uhci_hcd and address 2
[  636.353252] usb 1-2: configuration #1 chosen from 1 choice
[  166.131105] usbcore: registered new interface driver libusual
[  166.170681] Initializing USB Mass Storage driver...
[  166.184635] scsi2 : SCSI emulation for USB Mass Storage devices
[  166.193113] usbcore: registered new interface driver usb-storage
[  166.193126] USB Mass Storage support registered.
[  166.193715] usb-storage: device found at 2
[  166.193719] usb-storage: waiting for device to settle before scanning
[  647.268039] usb-storage: device scan complete
[  647.271032] scsi 2:0:0:0: Direct-Access     Generic  USB Flash Drive  1.04 PQ: 0 ANSI: 2
[  647.288243] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  647.288408] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  768.919460] usb 1-2: USB disconnect, address 2
[  782.689583] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  782.871856] usb 1-1: configuration #1 chosen from 1 choice
[  782.964785] scsi3 : SCSI emulation for USB Mass Storage devices
[  782.977521] usb-storage: device found at 3
[  782.977539] usb-storage: waiting for device to settle before scanning
[  296.249404] usb-storage: device scan complete
[  296.252895] scsi 3:0:0:0: Direct-Access     USB-DISK FREEDIK-LWFORMAT 2.23 PQ: 0 ANSI: 2
[  296.273853] sd 3:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[  296.276881] sd 3:0:0:0: [sdb] Write Protect is off
[  296.276892] sd 3:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  296.276897] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  296.288848] sd 3:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[  296.291828] sd 3:0:0:0: [sdb] Write Protect is off
[  296.291835] sd 3:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  296.291839] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  296.291849]  sdb: unknown partition table
[  296.317931] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  296.318011] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  827.031514] usb 1-1: USB disconnect, address 3
[  827.032562] Buffer I/O error on device sdb, logical block 1
[  827.032578] lost page write due to I/O error on sdb
[  827.032609] Buffer I/O error on device sdb, logical block 2040
[  827.032619] lost page write due to I/O error on sdb
[ 1668.578843] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 1668.761127] usb 1-1: configuration #1 chosen from 1 choice
[ 1668.854311] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1668.860996] usb-storage: device found at 4
[ 1668.861015] usb-storage: waiting for device to settle before scanning
[ 1677.257017] usb-storage: device scan complete
[ 1677.260994] scsi 4:0:0:0: Direct-Access     USB-DISK FREEDIK-LWFORMAT 2.23 PQ: 0 ANSI: 2
[ 1677.282937] sd 4:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[ 1677.285929] sd 4:0:0:0: [sdb] Write Protect is off
[ 1677.285947] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1677.285959] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1677.297923] sd 4:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[ 1677.300958] sd 4:0:0:0: [sdb] Write Protect is off
[ 1677.300979] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1677.300990] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1677.301011]  sdb: unknown partition table
[ 1677.320156] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1677.320356] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1703.657515] usb 1-1: USB disconnect, address 4
[ 1703.658626] Buffer I/O error on device sdb, logical block 1
[ 1703.658641] lost page write due to I/O error on sdb
[ 1703.658672] Buffer I/O error on device sdb, logical block 2040
[ 1703.658683] lost page write due to I/O error on sdb
[ 1703.658700] Buffer I/O error on device sdb, logical block 50792
[ 1703.658710] lost page write due to I/O error on sdb
[ 1745.696349] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 1745.878643] usb 1-1: configuration #1 chosen from 1 choice
[ 1745.970788] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1745.977844] usb-storage: device found at 5
[ 1745.977863] usb-storage: waiting for device to settle before scanning
[ 1754.708443] usb-storage: device scan complete
[ 1754.712438] scsi 5:0:0:0: Direct-Access     USB-DISK FREEDIK-LWFORMAT 2.23 PQ: 0 ANSI: 2
[ 1754.737361] sd 5:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[ 1754.740350] sd 5:0:0:0: [sdb] Write Protect is off
[ 1754.740368] sd 5:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1754.740380] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1754.752366] sd 5:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[ 1754.755350] sd 5:0:0:0: [sdb] Write Protect is off
[ 1754.755369] sd 5:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1754.755380] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1754.755399]  sdb: unknown partition table
[ 1754.773551] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 1754.773717] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 1797.337817] usb 1-1: USB disconnect, address 5
[ 1797.338883] Buffer I/O error on device sdb, logical block 1
[ 1797.338898] lost page write due to I/O error on sdb
[ 1797.338925] Buffer I/O error on device sdb, logical block 2040
[ 1797.338936] lost page write due to I/O error on sdb
[ 4358.963886] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 4359.146180] usb 1-1: configuration #1 chosen from 1 choice
[ 4359.242419] scsi6 : SCSI emulation for USB Mass Storage devices
[ 4359.247551] usb-storage: device found at 6
[ 4359.247568] usb-storage: waiting for device to settle before scanning
[ 4365.376109] usb-storage: device scan complete
[ 4365.380087] scsi 6:0:0:0: Direct-Access     USB-DISK FREEDIK-LWFORMAT 2.23 PQ: 0 ANSI: 2
[ 4365.402027] sd 6:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[ 4365.405019] sd 6:0:0:0: [sdb] Write Protect is off
[ 4365.405038] sd 6:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 4365.405049] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4365.417012] sd 6:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[ 4365.420010] sd 6:0:0:0: [sdb] Write Protect is off
[ 4365.420028] sd 6:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 4365.420038] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4365.420056]  sdb: unknown partition table
[ 4365.438212] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 4365.438389] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1207.884997] ACPI: EC: missing OBF confirmation, don't expect it any longer.
[ 1281.685574] eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[ 5106.449101] usb 1-1: USB disconnect, address 6
[ 5106.450207] Buffer I/O error on device sdb, logical block 1
[ 5106.450222] lost page write due to I/O error on sdb
[ 5106.450253] Buffer I/O error on device sdb, logical block 2040
[ 5106.450264] lost page write due to I/O error on sdb
[ 5149.249170] usb 1-1: new full speed USB device using uhci_hcd and address 7
[ 5149.431456] usb 1-1: configuration #1 chosen from 1 choice
[ 5149.522698] scsi7 : SCSI emulation for USB Mass Storage devices
[ 5149.532636] usb-storage: device found at 7
[ 5149.532654] usb-storage: waiting for device to settle before scanning
[ 1934.085876] usb-storage: device scan complete
[ 1934.088872] scsi 7:0:0:0: Direct-Access     USB-DISK FREEDIK-LWFORMAT 2.23 PQ: 0 ANSI: 2
[ 1934.106820] sd 7:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[ 1934.109852] sd 7:0:0:0: [sdb] Write Protect is off
[ 1934.109859] sd 7:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1934.109863] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1934.121801] sd 7:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[ 1934.124794] sd 7:0:0:0: [sdb] Write Protect is off
[ 1934.124801] sd 7:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1934.124805] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1934.124815]  sdb: unknown partition table
[ 1934.151908] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 1934.151988] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 5194.504889] usb 1-1: USB disconnect, address 7
[ 5194.506007] Buffer I/O error on device sdb, logical block 1
[ 5194.506023] lost page write due to I/O error on sdb
[ 5194.506056] Buffer I/O error on device sdb, logical block 2040
[ 5194.506066] lost page write due to I/O error on sdb
[ 5194.506084] Buffer I/O error on device sdb, logical block 50794
[ 5194.506094] lost page write due to I/O error on sdb
[26192.635003] usb 1-1: new full speed USB device using uhci_hcd and address 8
[26192.817285] usb 1-1: configuration #1 chosen from 1 choice
[26192.908620] scsi8 : SCSI emulation for USB Mass Storage devices
[26192.915730] usb-storage: device found at 8
[26192.915748] usb-storage: waiting for device to settle before scanning
[ 6836.255055] usb-storage: device scan complete
[ 6836.259933] scsi 8:0:0:0: Direct-Access     USB-DISK FREEDIK-LWFORMAT 2.23 PQ: 0 ANSI: 2
[ 6836.280046] sd 8:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[ 6836.283034] sd 8:0:0:0: [sdb] Write Protect is off
[ 6836.283043] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 6836.283047] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 6836.295999] sd 8:0:0:0: [sdb] 130400 512-byte hardware sectors (67 MB)
[ 6836.298994] sd 8:0:0:0: [sdb] Write Protect is off
[ 6836.298999] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 6836.299003] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 6836.299014]  sdb: unknown partition table
[ 6836.318162] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 6836.318232] sd 8:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by Confused Vorlon on 2008-08-19
Bueller  ?

---

### Post by Dougie187 on 2008-08-19
What kind of network card do you have in your laptop? ( Post the output of lspci )

can you post the output of ifconfig when you have an ethernet cable plugged in?

Also, just so you know. The forums prohibit bumpping threads prior to 1 day activity. So, you might not bump so often if you don't want to get in trouble.

---

### Post by Confused Vorlon on 2008-08-19
thanks for the response.

output of lscpi is in the first post (second block of code)

ifconfig in the first post is with the ethernet cable plugged in.

does that give any clues?

---

### Post by Dougie187 on 2008-08-19
I don't know off the top of my head. I will see if I can come up for something, but it looks like your cards are both picked up fine, you're just getting some weird issue. It also looks like a few other people are having a similar issue, and they have yet to resolve their issues.

---

### Post by yashugrover on 2008-08-19
even I can not access internet, I have also got 8.04 version...I would like to add that till yesterday night everything was fine, but suddenly net got disconnected and since then I am trying to connect to internet but in vain... I have installed ubuntu inside windows n I can access net thru windows but not ubuntu....so plz help, m a noob...

---

