---
title: "Internet going slow?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by dsurge on 2008-10-31
I read online that others in 8.10 are also having this problem.

I followed this [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744) but it didn't work... my internet is still slow as balls. Off of synaptics I'm lucky for b/s and google takes 20 seconds to load... Help anyone? As always much appreciated:)

---

### Post by SunnyRabbiera on 2008-10-31
> **dsurge said:**
> I read online that others in 8.10 are also having this problem.

I followed this [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744) but it didn't work... my internet is still slow as balls. Off of synaptics I'm lucky for b/s and google takes 20 seconds to load... Help anyone? As always much appreciated:)

Is it just internet or are you having issues with other web stuff too like synaptic?
if you are browsing the main ubuntu pages i am not surprised you would have issues.

---

### Post by dsurge on 2008-10-31
its all synaptic, all webpages, everything not just the linux pages... that I would understand seeing as how they should be loaded up, but google taking over 20 seconds to load now? Something has to be wrong, I just dont know what.

---

### Post by Crafty Kisses on 2008-10-31
You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:
```
sudo ifdown wlan0
sudo ifup wlan0
```
You may diagnose the network adapter status with commands:
```
ifconfig
iwconfig
dmesg
/var/log/messages
```

I also want to see the results of this command:
```
lshw -C network

```
I'm thinking it could also be packet loss, it certainly sounds like it.

Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

You might want to check if there is any interference with like a phone or a microwave or even possibly a lamp. I know it sounds stupid but my lamp for some reason was causing some interference with my router, that can all lead to packet loss.

I also wouldn't be surprised if it was because the servers are really busy today, you have to put that into consideration, if the problems still continue after 48 hours then it is probably a network problem, please let us know.

---

### Post by dsurge on 2008-10-31
to reply to all the commands you asked:

```
surge@tsurge:~$ sudo ifdown wlan0
sudo: unable to resolve host tsurge
ifdown: interface wlan0 not configured
surge@tsurge:~$ sudo ifup wlan0
sudo: unable to resolve host tsurge
Ignoring unknown interface wlan0=wlan0.
surge@tsurge:~$ 

```

```
surge@tsurge:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:84:1c:9f  
          inet addr:142.151.136.61  Bcast:142.151.136.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe84:1c9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:40691504 (40.6 MB)  TX bytes:3173273 (3.1 MB)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23148 (23.1 KB)  TX bytes:23148 (23.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:21:6d:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-21-6D-81-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

this is all I can copy for dsemg

```
[    0.618726] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.618731] pci 0000:00:1c.2: setting latency timer to 64
[    0.618747] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.618755] pci 0000:00:1c.3: setting latency timer to 64
[    0.618765] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.618774] pci 0000:00:1c.4: setting latency timer to 64
[    0.618784] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    0.618792] pci 0000:00:1e.0: setting latency timer to 64
[    0.618807] pci 0000:15:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.618817] pci 0000:15:00.0: setting latency timer to 64
[    0.618823] bus: 00 index 0 io port: [0, ffff]
[    0.618824] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.618826] bus: 01 index 0 io port: [2000, 2fff]
[    0.618828] bus: 01 index 1 mmio: [d0000000, d2ffffff]
[    0.618830] bus: 01 index 2 mmio: [e0000000, efffffff]
[    0.618831] bus: 01 index 3 mmio: [0, 0]
[    0.618833] bus: 02 index 0 io port: [3000, 3fff]
[    0.618835] bus: 02 index 1 mmio: [dc100000, df2fffff]
[    0.618836] bus: 02 index 2 mmio: [dfd00000, dfdfffff]
[    0.618838] bus: 02 index 3 mmio: [0, 0]
[    0.618840] bus: 03 index 0 io port: [4000, 4fff]
[    0.618841] bus: 03 index 1 mmio: [d4000000, d7dfffff]
[    0.618843] bus: 03 index 2 mmio: [dfa00000, dfafffff]
[    0.618844] bus: 03 index 3 mmio: [0, 0]
[    0.618846] bus: 04 index 0 io port: [5000, 5fff]
[    0.618848] bus: 04 index 1 mmio: [fc000000, fdffffff]
[    0.618849] bus: 04 index 2 mmio: [f8000000, f80fffff]
[    0.618851] bus: 04 index 3 mmio: [0, 0]
[    0.618852] bus: 05 index 0 io port: [6000, 6fff]
[    0.618854] bus: 05 index 1 mmio: [d8000000, d9ffffff]
[    0.618856] bus: 05 index 2 mmio: [df700000, df7fffff]
[    0.618857] bus: 05 index 3 mmio: [0, 0]
[    0.618859] bus: 0d index 0 io port: [7000, 7fff]
[    0.618861] bus: 0d index 1 mmio: [cc000000, cdffffff]
[    0.618862] bus: 0d index 2 mmio: [df400000, df4fffff]
[    0.618864] bus: 0d index 3 mmio: [0, 0]
[    0.618865] bus: 15 index 0 io port: [8000, bfff]
[    0.618867] bus: 15 index 1 mmio: [f8100000, fbffffff]
[    0.618869] bus: 15 index 2 mmio: [f4000000, f7ffffff]
[    0.618870] bus: 15 index 3 io port: [0, ffff]
[    0.618872] bus: 15 index 4 mmio: [0, ffffffffffffffff]
[    0.618874] bus: 16 index 0 io port: [8000, 80ff]
[    0.618875] bus: 16 index 1 io port: [8400, 84ff]
[    0.618877] bus: 16 index 2 mmio: [f4000000, f7ffffff]
[    0.618879] bus: 16 index 3 mmio: [80000000, 83ffffff]
[    0.618888] NET: Registered protocol family 2
[    0.657117] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.657886] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.659648] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.660251] TCP: Hash tables configured (established 262144 bind 65536)
[    0.660253] TCP reno registered
[    0.669121] NET: Registered protocol family 1
[    0.669235] checking if image is initramfs... it is
[    1.444292] Freeing initrd memory: 8438k freed
[    1.448727] Simple Boot Flag at 0x35 set to 0x1
[    1.450102] audit: initializing netlink socket (disabled)
[    1.450119] type=2000 audit(1225418627.448:1): initialized
[    1.456165] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.459248] VFS: Disk quotas dquot_6.5.1
[    1.459346] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.459459] msgmni has been set to 3950
[    1.459588] io scheduler noop registered
[    1.459590] io scheduler anticipatory registered
[    1.459591] io scheduler deadline registered
[    1.459737] io scheduler cfq registered (default)
[    1.459951] pci 0000:01:00.0: Boot video device
[    1.460109] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.460143] pcieport-driver 0000:00:01.0: found MSI capability
[    1.460173] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.460228] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.460281] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.460387] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.460475] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.460561] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.460614] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.460667] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.460846] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.460933] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.461030] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.461085] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.461138] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.461316] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.461400] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.461479] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.461531] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.461583] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.461772] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.461868] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.461951] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.462008] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.462058] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.462240] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.462330] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.462418] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.462471] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.462521] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.502327] hpet_resources: 0xfed00000 is busy
[    1.502426] Linux agpgart interface v0.103
[    1.502431] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.505271] brd: module loaded
[    1.505350] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.505494] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.515141] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.515149] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.532153] mice: PS/2 mouse device common for all mice
[    1.532297] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.532335] rtc0: alarms up to one month, y3k, hpet irqs
[    1.532386] cpuidle: using governor ladder
[    1.532388] cpuidle: using governor menu
[    1.532739] TCP cubic registered
[    1.532974] registered taskstats version 1
[    1.533120]   Magic number: 12:77:57
[    1.533269] rtc_cmos 00:07: setting system clock to 2008-10-31 02:03:48 UTC (1225418628)
[    1.533272] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.533273] EDD information not available.
[    1.533321] Freeing unused kernel memory: 536k freed
[    1.533564] Write protecting the kernel read-only data: 4348k
[    1.538179] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.673422] fuse init (API version 7.9)
[    1.751328] ACPI: SSDT 7DEE1D72, 02C4 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[    1.752029] ACPI: SSDT 7DEE20BB, 061E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[    1.755764] Monitor-Mwait will be used to enter C-1 state
[    1.755767] Monitor-Mwait will be used to enter C-2 state
[    1.755769] Monitor-Mwait will be used to enter C-3 state
[    1.775837] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.775913] processor ACPI0007:00: registered as cooling_device0
[    1.775917] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.776313] ACPI: SSDT 7DEE1CAA, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[    1.776855] ACPI: SSDT 7DEE2036, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[    1.779486] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.779568] processor ACPI0007:01: registered as cooling_device1
[    1.779572] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.804225] thermal LNXTHERM:01: registered as thermal_zone0
[    1.807994] ACPI: Thermal Zone [THM0] (56 C)
[    1.809276] thermal LNXTHERM:02: registered as thermal_zone1
[    1.810719] ACPI: Thermal Zone [THM1] (56 C)
[    1.945023] ACPI: ACPI Dock Station Driver
[    2.115935] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.115939] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.124726] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.124751] e1000e 0000:00:19.0: setting latency timer to 64
[    2.184459] usbcore: registered new interface driver usbfs
[    2.184481] usbcore: registered new interface driver hub
[    2.192574] usbcore: registered new device driver usb
[    2.231501] USB Universal Host Controller Interface driver v3.0
[    2.256767] SCSI subsystem initialized
[    2.271719] libata version 3.00 loaded.
[    2.343578] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:15:58:84:1c:9f
[    2.343582] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.343621] 0000:00:19.0: eth0: MAC: 4, PHY: 6, PBA No: ffffff-0ff
[    2.343864] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.343875] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.343881] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.343922] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.343970] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    2.344119] usb usb1: configuration #1 chosen from 1 choice
[    2.344147] hub 1-0:1.0: USB hub found
[    2.344154] hub 1-0:1.0: 2 ports detected
[    2.550028] uhci_hcd 0000:00:1a.1: power state changed by ACPI to D0
[    2.550039] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.550051] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.550056] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.550087] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.550140] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    2.550236] usb usb2: configuration #1 chosen from 1 choice
[    2.550262] hub 2-0:1.0: USB hub found
[    2.550269] hub 2-0:1.0: 2 ports detected
[    2.653988] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    2.654003] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.654023] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.654029] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.654056] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    2.657981] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.658003] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfe226c00
[    2.661900] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    2.673066] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.673174] usb usb3: configuration #1 chosen from 1 choice
[    2.673203] hub 3-0:1.0: USB hub found
[    2.673209] hub 3-0:1.0: 4 ports detected
[    2.729127] hub 1-0:1.0: unable to enumerate USB device on port 2
[    2.883043] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.883054] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.883067] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.883075] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.883111] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    2.883167] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    2.883284] usb usb4: configuration #1 chosen from 1 choice
[    2.883316] hub 4-0:1.0: USB hub found
[    2.883325] hub 4-0:1.0: 2 ports detected
[    3.000062] Clocksource tsc unstable (delta = -138388244 ns)
[    3.088962] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.088973] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.088979] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.089010] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    3.089055] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    3.089138] usb usb5: configuration #1 chosen from 1 choice
[    3.089165] hub 5-0:1.0: USB hub found
[    3.089171] hub 5-0:1.0: 2 ports detected
[    3.197578] uhci_hcd 0000:00:1d.2: power state changed by ACPI to D0
[    3.197586] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.197592] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.197598] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.197633] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    3.197670] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    3.197747] usb usb6: configuration #1 chosen from 1 choice
[    3.197769] hub 6-0:1.0: USB hub found
[    3.197774] hub 6-0:1.0: 2 ports detected
[    3.201068] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    3.302669] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    3.302679] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.302695] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.302701] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.302730] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.306660] ehci_hcd 0000:00:1d.7: debug port 1
[    3.306673] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.306688] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe227000
[    3.325025] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.325204] usb usb7: configuration #1 chosen from 1 choice
[    3.325232] hub 7-0:1.0: USB hub found
[    3.325239] hub 7-0:1.0: 6 ports detected
[    3.534220] pata_acpi 0000:00:1f.1: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    3.534248] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.534265] pata_acpi 0000:00:1f.1: PCI INT C disabled
[    3.534485] ahci 0000:00:1f.2: version 3.0
[    3.534496] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    3.534605] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x1 impl SATA mode
[    3.534607] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    3.534614] ahci 0000:00:1f.2: setting latency timer to 64
[    3.535567] scsi0 : ahci
[    3.535920] scsi1 : ahci
[    3.536048] scsi2 : ahci
[    3.536121] ata1: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 2297
[    3.536124] ata2: DUMMY
[    3.536125] ata3: DUMMY
[    3.720067] usb 4-1: device not accepting address 2, error -71
[    3.776104] hub 4-0:1.0: unable to enumerate USB device on port 1
[    3.852075] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.854623] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    3.854626] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.856493] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 succeeded
[    3.856496] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.860184] ata1.00: ATA-7: ST9120822AS, 3.CLF, max UDMA/100
[    3.860187] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.865722] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    3.865724] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.867596] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 succeeded
[    3.867598] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.871289] ata1.00: configured for UDMA/100
[    3.893489] ata1.00: configured for UDMA/100
[    3.893492] ata1: EH complete
[    3.893747] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CL PQ: 0 ANSI: 5
[    3.893957] ohci1394 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.893968] ohci1394 0000:15:00.1: setting latency timer to 64
[    3.946676] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.955121] ata_piix 0000:00:1f.1: version 2.12
[    3.955136] ata_piix 0000:00:1f.1: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    3.955178] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.955310] scsi3 : ata_piix
[    3.955431] scsi4 : ata_piix
[    3.956410] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1830 irq 14
[    3.956412] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1838 irq 15
[    3.972927] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.984751] Driver 'sd' needs updating - please use bus_type methods
[    3.984856] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    3.984879] sd 0:0:0:0: [sda] Write Protect is off
[    3.984882] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.984921] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.984997] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    3.985020] sd 0:0:0:0: [sda] Write Protect is off
[    3.985022] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.985060] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.985063]  sda:<6>usb 1-2: new full speed USB device using uhci_hcd and address 3
[    4.036565]  sda1 sda2 < sda5 sda6 >
[    4.064255] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.120655] ata4.00: ATAPI: MATSHITADVD-RAM UJ-852, RB01, max UDMA/33
[    4.136514] ata4.00: configured for UDMA/33
[    4.136645] ata5: port disabled. ignoring.
[    4.136711] isa bounce pool size: 16 pages
[    4.138717] scsi 3:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-852   RB01 PQ: 0 ANSI: 5
[    4.138857] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[    4.160252] Driver 'sr' needs updating - please use bus_type methods
[    4.164939] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.164943] Uniform CD-ROM driver Revision: 3.20
[    4.165031] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    4.196696] usb 1-2: configuration #1 chosen from 1 choice
[    4.308064] usb 7-1: new high speed USB device using ehci_hcd and address 2
[    4.443896] usb 7-1: configuration #1 chosen from 1 choice
[    4.455025] usbcore: registered new interface driver libusual
[    4.460409] Initializing USB Mass Storage driver...
[    4.461051] scsi5 : SCSI emulation for USB Mass Storage devices
[    4.462170] usbcore: registered new interface driver usb-storage
[    4.462173] USB Mass Storage support registered.
[    4.462298] usb-storage: device found at 2
[    4.462301] usb-storage: waiting for device to settle before scanning
[    4.622238] kjournald starting.  Commit interval 5 seconds
[    4.622256] EXT3-fs: mounted filesystem with ordered data mode.
[    5.224383] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c20001592ba]
[    9.460463] usb-storage: device scan complete
[    9.464056] scsi 5:0:0:0: Direct-Access     ST310003 40AS                  PQ: 0 ANSI: 2
[    9.465334] sd 5:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[    9.467686] sd 5:0:0:0: [sdb] Write Protect is off
[    9.467688] sd 5:0:0:0: [sdb] Mode Sense: 38 00 00 00
[    9.467690] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    9.468684] sd 5:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[    9.470916] sd 5:0:0:0: [sdb] Write Protect is off
[    9.470919] sd 5:0:0:0: [sdb] Mode Sense: 38 00 00 00
[    9.470920] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    9.470924]  sdb:<6>udevd version 124 started
[   12.437232] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.601562] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.627347] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.653051] ACPI: Power Button (FF) [PWRF]
[   12.653163] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   12.654259] ACPI: Lid Switch [LID]
[   12.654328] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   12.681065] ACPI: Sleep Button (CM) [SLPB]
[   12.685981] ACPI: WMI: Mapper loaded
[   12.968311] ACPI: AC Adapter [AC] (on-line)
[   12.970488] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   12.970493] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   12.970886] ACPI: Error installing bay notify handler
[   13.028299] ACPI: Battery Slot [BAT0] (battery present)
[   13.030606] acpi device:03: registered as cooling_device2
[   13.030974] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input5
[   13.053043] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   13.054977] acpi device:08: registered as cooling_device3
[   13.055216] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/device:07/input/input6
[   13.085029] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   13.682941] nvidia: module license 'NVIDIA' taints kernel.
[   13.938248] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   13.938262] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.938271] nvidia 0000:01:00.0: setting latency timer to 64
[   13.938440] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   13.996399] Non-volatile memory driver v1.2
[   14.063136] iTCO_vendor_support: vendor-support=0
[   14.082720] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   14.197389] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.246628] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   14.374100] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   14.374107] Socket status: 30000006
[   14.374110] pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
[   14.374180] pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
[   14.374183] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   14.512135] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   14.512139] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   14.515551] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.515583] iwlagn 0000:03:00.0: setting latency timer to 64
[   14.515621] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   14.562650] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.586075] iwlagn 0000:03:00.0: PCI INT A disabled
[   14.587334] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.785596] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   14.785601] serio: Synaptics pass-through port at isa0060/serio1/input0
[   14.829397] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.829402] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   14.829425] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.832841] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   14.892432] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   14.892489] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.892582] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   14.892584] thinkpad_acpi: http://ibm-acpi.sf.net/
[   14.892585] thinkpad_acpi: ThinkPad BIOS 7LET51WW (1.21 ), EC 7KHT22WW-1.06
[   14.892587] thinkpad_acpi: Lenovo ThinkPad T61, model 766416U
[   14.893466] thinkpad_acpi: radio switch found; radios are disabled
[   14.893609] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   14.893612] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   14.902885] Registered led device: tpacpi::thinklight
[   14.902960] Registered led device: tpacpi::power
[   14.902995] Registered led device: tpacpi:orange:batt
[   14.903026] Registered led device: tpacpi:green:batt
[   14.903059] Registered led device: tpacpi::dock_active
[   14.903094] Registered led device: tpacpi::bay_active
[   14.903126] Registered led device: tpacpi::dock_batt
[   14.903172] Registered led device: tpacpi::unknown_led
[   14.903206] Registered led device: tpacpi::standby
[   14.908085] thinkpad_acpi: Lenovo BIOS switched to ACPI backlight control mode
[   14.908087] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   14.914365] input: ThinkPad Extra Buttons as /devices/virtual/input/input9
[   16.135377] lp: driver loaded but no devices found
[   16.824830] EXT3 FS on sda6, internal journal
[   17.022069]  sdb1
[   17.024266] sd 5:0:0:0: [sdb] Attached SCSI disk
[   17.024381] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   17.834720] type=1505 audit(1225433044.877:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4508
[   17.957295] type=1505 audit(1225433045.001:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4513
[   17.957481] type=1505 audit(1225433045.001:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4513
[   18.124277] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.563598] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   18.563603] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   18.563631] ACPI: Error installing bay notify handler
[   19.646125] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.862274] ppdev: user-space parallel port driver
[   20.162972] NET: Registered protocol family 10
[   20.163868] lo: Disabled Privacy Extensions
[   20.816321] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   21.072681] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input10
[   22.946493] Bluetooth: Core ver 2.13
[   22.947156] NET: Registered protocol family 31
[   22.947169] Bluetooth: HCI device and connection manager initialized
[   22.947175] Bluetooth: HCI socket layer initialized
[   22.980730] Bluetooth: L2CAP ver 2.11
[   22.980744] Bluetooth: L2CAP socket layer initialized
[   23.036476] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.036492] Bluetooth: BNEP filters: protocol multicast
[   23.126139] Bridge firewalling registered
[   23.126471] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   23.165139] Bluetooth: RFCOMM socket layer initialized
[   23.167066] Bluetooth: RFCOMM TTY layer initialized
[   23.167079] Bluetooth: RFCOMM ver 1.10
[   23.170566] Bluetooth: SCO (Voice Link) ver 0.6
[   23.170581] Bluetooth: SCO socket layer initialized
[   27.522383] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.524671] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.524765] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x40100102, writing 0x40100106)
[   27.528049] firmware: requesting iwlwifi-4965-2.ucode
[   27.617281] iwlagn: Radio disabled by HW RF Kill switch
[   27.725815] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.876374] NET: Registered protocol family 17
[   29.207348] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   29.207357] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   29.207983] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   39.668078] eth0: no IPv6 routers present
[   56.258936] CPU0 attaching NULL sched-domain.
[   56.258952] CPU1 attaching NULL sched-domain.
[   56.268118] CPU0 attaching sched-domain:
[   56.268127]  domain 0: span 0-1 level MC
[   56.268130]   groups: 0 1
[   56.268134]   domain 1: span 0-1 level NODE
[   56.268136]    groups: 0-1
[   56.268140] CPU1 attaching sched-domain:
[   56.268142]  domain 0: span 0-1 level MC
[   56.268144]   groups: 1 0
[   56.268147]   domain 1: span 0-1 level NODE
[   56.268148]    groups: 0-1
[  118.693041] CE: hpet increasing min_delta_ns to 15000 nsec
[  129.630678] type=1503 audit(1225433156.674:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6257/net/" pid=6257 profile="/usr/sbin/cupsd"
[  130.881450] type=1503 audit(1225433157.926:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6261/net/" pid=6261 profile="/usr/sbin/cupsd"
[  130.881527] type=1503 audit(1225433157.926:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6261 profile="/usr/sbin/cupsd"
[  130.881541] type=1503 audit(1225433157.926:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6261 profile="/usr/sbin/cupsd"
[  130.881553] type=1503 audit(1225433157.926:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6261 profile="/usr/sbin/cupsd"
[  130.881566] type=1503 audit(1225433157.926:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6261 profile="/usr/sbin/cupsd"
[  130.881578] type=1503 audit(1225433157.926:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6261 profile="/usr/sbin/cupsd"
[  130.881591] type=1503 audit(1225433157.926:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6261 profile="/usr/sbin/cupsd"
[  130.881603] type=1503 audit(1225433157.926:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6261 profile="/usr/sbin/cupsd"
[  130.881616] type=1503 audit(1225433157.926:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6261 profile="/usr/sbin/cupsd"

```

```
surge@tsurge:~$ sudo/var/log/messages
bash: sudo/var/log/messages: No such file or directory

```

```
surge@tsurge:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:15:58:84:1c:9f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.3-0 ip=142.151.136.61 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:21:6d:81
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f6:67:8c:5d:be:4b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```


I forgot to mention, it's not wireless, its ethernet cable connecting it so I know its not a wireless issue. My internet also works fine when i boot into windows xp...

---

### Post by LookTJ on 2008-10-31
Edit this file: 
```
/etc/sysctl.conf
```Insert the following lines```

# Tweaks for faster broadband...
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 2072576
net.ipv4.tcp_rmem = 4096 87380 2072576
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1

```Either reboot or 
```
sudo /sbin/sysctl -p
```I got these from a website.

T.

---

### Post by dsurge on 2008-10-31
Tried your code, but it didn't work. Might I also add (although I think this is a separate issue) that my entire linux is slow (terminal takes 4 seconds to come up, mozilla about 8, when i start video files i can hear audio but dont see video for about 10 seconds). I have a T61 T7300 2.0ghz with 2 gigs of ram, nvs140m, 160gig hdd 5400rpm so I don't think its the fact that i'm on 64 bit, but you guys are the experts... just putting it out there.

Thanks for the help everyone so far

---

### Post by LookTJ on 2008-10-31
> **dsurge said:**
> Tried your code, but it didn't work. Might I also add (although I think this is a separate issue) that my entire linux is slow (terminal takes 4 seconds to come up, mozilla about 8, when i start video files i can hear audio but dont see video for about 10 seconds). I have a T61 T7300 2.0ghz with 2 gigs of ram, nvs140m, 160gig hdd 5400rpm so I don't think its the fact that i'm on 64 bit, but you guys are the experts... just putting it out there.

Thanks for the help everyone so farInteresting, I would like to assume a bad hard drive. But I'm stuck since I don't have a 64bit computer. 

Do you by any chance hear your hard drive click(making strange noise). Have you tested your RAM. Oh before you answer all that, does Windows run fine on that same computer? If so, then it is probably a bad video card driver in Linux that was installed.

---

### Post by dsurge on 2008-11-01
Yes windows runs fine on the same computer. The ram and the hdd are solid and have no errors. I have the proprietary nvidia 177 driver installed (the one ubuntu recommended)

---

### Post by ludu900 on 2008-11-01
I'm running 8.04 and I had the same problem. Try changing to open servers. Follow the instructions here: [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

It worked for 8.04 and I dont know if it will work for you but its worth a shot.

---

### Post by redbob on 2008-11-01
Hi,
If you tell me that everything is lazy... tell me the size of your swap memory. Swap must be at least 500Mb. When I faced this situation, I figured that my /home partition is with 100% full. I just emptied it and - voilà!!

---

### Post by redbob on 2008-11-01
Let me correct it - "not" emptied, but "sweeping". :)

---

### Post by Tom--d on 2008-11-01
Sounds to me it could be a driver issue.

Disable IPV6?

---

### Post by richg on 2008-11-01
For me, it is slow only in Ubuntu since the 8.10 upgrade started.

Rich

---

### Post by dsurge on 2008-11-01
IPV6 is diabled, my swap file is 1024mb and I did the DNS thing and I'm noticing significant differences in speeds but its still not par. Thanks for all the tips so far guys!:)

---

### Post by rhenium3 on 2008-11-02
> **richg said:**
> For me, it is slow only in Ubuntu since the 8.10 upgrade started.

Rich

Same here :( internet, everything seems to be running slower, worked fine before i upgraded...

---

### Post by dsurge on 2008-11-03
Anyone find a solution to their issues?

---

