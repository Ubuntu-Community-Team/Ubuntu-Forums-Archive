---
title: "can't connect to internet- help protocol did not work"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by Jennyplayswu on 2011-09-13
Hello!
I installed meerkat 10.10 on my computer 4 months ago using a CD that was apart of Ubuntu magazine. I built my computer with help from my ex 4 years ago, we had windows XP and an older version of Ubuntu. At that time I accessed the internet with my wireless card. With my current set up, I am running only ubuntu and I want to connect to the internet with a wired LAN connection. My computer tells me I am connected- icon in top right with "connection established," but when I open firefox it cannot connect. I know my LAN "card" works because that is how I was getting internet for the last year using XP. My ethernet LAN "card" is  apart of my motherboard, as opposed to beinging plugged into it. I have been surfing forums on and off for two months and have gone through all the help protocols in ubuntu for network connection.
I can't procrastinate anymore, school starts in a week- any help would be greatly appreciated!
Sorry my thoughts aren't more organized!
This what I was able to find out via the terminal:

jenny@Utopia:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0
    Memory at <ignored> (32-bit, prefetchable)
    Capabilities: <access denied>
    Kernel driver in use: agpgart-amd64

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: 66MHz, fast devsel, IRQ 12
    I/O ports at 9000 [size=32]
    I/O ports at 4c00 [size=64]
    I/O ports at 4c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at e3003000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at e3004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at e3005000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 2501
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at e3000000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 9c00 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
    Subsystem: Biostar Microtech Int'l Corp Device 8212
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    I/O ports at a000 [size=256]
    I/O ports at a400 [size=128]
    Memory at e3001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at f000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Biostar Microtech Int'l Corp Device 5400
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at c000 [size=16]
    I/O ports at c400 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
    Memory behind bridge: e0000000-e1ffffff
    Prefetchable memory behind bridge: d8000000-dfffffff
    Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
    Memory behind bridge: e2000000-e2ffffff
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2) (prog-if 00 [VGA controller])
    Subsystem: VISIONTEK Device 002c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    [virtual] Expansion ROM at e1000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb, rivafb

02:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
    Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
    Memory at e2000000 (32-bit, non-prefetchable) [size=64K]
    Memory at e2010000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

jenny@Utopia:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:ec:29:2a:5b  
          inet6 addr: fe80::216:ecff:fe29:2a5b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1305947 (1.3 MB)  TX bytes:113341 (113.3 KB)
          Interrupt:21 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

---

### Post by JD8182 on 2011-09-13
Do you still have a Wifi card or adapter still hooked up and possibly in use while being plugged into your lan connection? if so disable one or the other.






> **Jennyplayswu said:**
> Hello!
I installed meerkat 10.10 on my computer 4 months ago using a CD that was apart of Ubuntu magazine. I built my computer with help from my ex 4 years ago, we had windows XP and an older version of Ubuntu. At that time I accessed the internet with my wireless card. With my current set up, I am running only ubuntu and I want to connect to the internet with a wired LAN connection. My computer tells me I am connected- icon in top right with "connection established," but when I open firefox it cannot connect. I know my LAN "card" works because that is how I was getting internet for the last year using XP. My ethernet LAN "card" is  apart of my motherboard, as opposed to beinging plugged into it. I have been surfing forums on and off for two months and have gone through all the help protocols in ubuntu for network connection.
I can't procrastinate anymore, school starts in a week- any help would be greatly appreciated!
Sorry my thoughts aren't more organized!
This what I was able to find out via the terminal:

jenny@Utopia:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0
    Memory at <ignored> (32-bit, prefetchable)
    Capabilities: <access denied>
    Kernel driver in use: agpgart-amd64

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: 66MHz, fast devsel, IRQ 12
    I/O ports at 9000 [size=32]
    I/O ports at 4c00 [size=64]
    I/O ports at 4c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at e3003000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at e3004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at e3005000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 2501
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at e3000000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 9c00 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
    Subsystem: Biostar Microtech Int'l Corp Device 8212
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    I/O ports at a000 [size=256]
    I/O ports at a400 [size=128]
    Memory at e3001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: Biostar Microtech Int'l Corp Device 3401
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at f000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Biostar Microtech Int'l Corp Device 5400
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at c000 [size=16]
    I/O ports at c400 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
    Memory behind bridge: e0000000-e1ffffff
    Prefetchable memory behind bridge: d8000000-dfffffff
    Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
    Memory behind bridge: e2000000-e2ffffff
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2) (prog-if 00 [VGA controller])
    Subsystem: VISIONTEK Device 002c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    [virtual] Expansion ROM at e1000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb, rivafb

02:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
    Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
    Memory at e2000000 (32-bit, non-prefetchable) [size=64K]
    Memory at e2010000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

jenny@Utopia:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:ec:29:2a:5b  
          inet6 addr: fe80::216:ecff:fe29:2a5b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1305947 (1.3 MB)  TX bytes:113341 (113.3 KB)
          Interrupt:21 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

---

### Post by Jennyplayswu on 2011-09-13
Thank you responding to my post.

From what I can tell, my wireless card is disabled

system>preferences>network connections> wired 
has wired connection 1 and auto eth0

>wireless
has nothing set up

I am completely a newbie

---

### Post by JD8182 on 2011-09-14
I had a very similar issue once before, what I did to correct this issue was to delete the connections/reboot and re-add the connection which was I believe automatic.. Try this system/preferences/network connections and delete the values in the box both wired connection 1 and auto eth0, then reboot and if it does not automatically come back up repeat the steps, only this time add the auto eth0 in the network connections.




> **Jennyplayswu said:**
> Thank you responding to my post.

From what I can tell, my wireless card is disabled

system>preferences>network connections> wired 
has wired connection 1 and auto eth0

>wireless
has nothing set up

I am completely a newbie

---

### Post by Jennyplayswu on 2011-09-14
THANK YOU!
I am posting this using with my 100% Ubuntu computer-- the internet works!
I love success in the morning! YES!!!

---

### Post by JD8182 on 2011-09-14
Glad it worked, have a good day.



> **Jennyplayswu said:**
> THANK YOU!
I am posting this using with my 100% Ubuntu computer-- the internet works!
I love success in the morning! YES!!!

---

