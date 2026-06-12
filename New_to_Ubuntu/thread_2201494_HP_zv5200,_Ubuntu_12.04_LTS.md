---
title: "HP zv5200, Ubuntu 12.04 LTS"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by Thomas_J._Schmidt on 2014-01-24
For months now I've been trying to install Ubuntu 12.04 lts from the LiveCd packaged with _The Official Ubuntu Book_ (7th Edition, authored by Helmke & Graner) on an HP Pavilion zv5000z (hp service tag zv5320us). Early on I must have taken a wrong turn somewhere to end up trapped in this loop: 

"Intel UNDI, PXE-2.0 (Build 082) REALTEK RTL8139/8130/8104 PCI Fast Ethernet Client Mac ADDR: 000F B00A CDBC GUID:14B14323-F39D-11D8-84DF-00FB00ACDBC
DHCP...[twirling / ]
No Boot FileName Received.
PXE-M0F-Exiting PXE ROM" (repeats until canceled by keystrokes) :confused: ](*,)

This laptop used to have MS Windows XP Home Edition installed. With every update it ran boggier and boggier, so already very happy with the way my Sony PCG-GRX550 ran various distros of Ubuntu, I bought the book/LiveCd to put Ubuntu on the HP as well. "Try Ubuntu Without Installing" runs wonderfully on the HP particularly now that its RAM's been maxed out to 2 gigs. I've installed from the desktop icon; I've installed from the "Install Ubuntu" prompt on the CD; I've experimented with the pre-installation boot settings and re-installed yet again--all to no avail. Boot fails every time, taunting "Intel UNDI, et cetera...Exiting PXE ROM". I've been *so* tempted to pitch the HP into the nearest dumpster. ](*,)

I've searched and searched in my now-dogeared book and online for solutions. Today I found the Boot-Info thread and very carefully followed the instructions there. Boot-Repair generated the summary URL:

< [http://paste.ubuntu.com/6808518](http://paste.ubuntu.com/6808518) >

From that I printed out the nine-page report (_*nine pages!*_ aeiiii, where does a noob start...?) to look over, hoping to find a simple adjustment or two to enable this HP to boot without bricking. :confused::( But seriously, I told myself, this (like this initial posting) is taking much too much of my time and energy to complete. 

The _PhoenixBIOS Setup Utility/Main_ screen identifies the HP laptop as:

Notebook Model: Pavilion zv5200 (PL995UA#ABA)
System Board ID: 08A0
Processor Type: AMD Athlon(tm) XP Processor
Processor Speed: 1600 MHz
System Memory: 2048 Mb
BIOS Version: F.21
KBC Version: 32.30
Serial Number: CND4317PQB
UUID Number: 14B14E23F39D11D884DF000FB00ACDBC

_CNET_ reviews of the zv5000z lists these specs:

_Processor/Chipset_
CPU: AMD Athlon XP-M 3000+ / 1.6 GHz
Cache: L2 cache - 256.0 KB
Features PowerNow! technology

_Memory_
RAM: 256.0 MB
Max RAM Supported: 2.0 GB
Technology: DDR SDRAM, 2 slots/1 empty

_Storage_
Hard Drive: 40 GB HDD/4200.0 rpm, Type: "standard"
Optical Drive: CD-ROM 24x

_Display_
Type: 15.0 inch
Max Resolution: 1024x768 (XGA)

_Audio & Video_
Graphics Processor: AGP - NVIDIA GeForce 440 Go - 64.0 MB DDR SDRAM
Compliant Standards: Sound Blaster Pro

_Interfaces_
3.0 x Network - Ethernet 10Base-T100Base-TX - 15 pin HD D-Sub(HD-15)
Broadcom WiFi model BCM4306MPSG
56 kbps modem
CardBus slot (empty)
5 in 1 Memory Card Reader

Please, *please* help me install whatever lts distro of Ubuntu works best, load the missing WiFi firmware, then boot the system with the hard drive.

---

### Post by mörgæs on 2014-01-24
Hi, welcome to the fora.

You have a very old graphics card, and there's no way Ubuntu will work. I suggest the [alternate Lubuntu ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO").

---

### Post by Thomas_J._Schmidt on 2014-01-24
Thank you! Thank you! for your response. I thought it very likely I would have to substitute Xubuntu or Lubuntu; I will follow through with your suggestion and let you know how that turns out.

Just one "puzzled noob" question, though: the LiveCd Ubuntu 12.04 LTS runs fine, graphics and all, on this HP laptop with its embedded Very Old Graphics Card in "Try Ubuntu without Installing" mode. May I ask why you say "no way [COLOR=#000000]Ubuntu will work[/COLOR]" due to a very old graphics card? Can LiveCd run in spite of/independently of VOGCs?

---

### Post by mörgæs on 2014-01-24
It was maybe too strong an expression. What I meant is that Ubuntu will be a painfully slow experience on this graphics card compared to lighter alternatives when installed on the hard disk, if you are able to make it boot at all. Boot options like *nomodeset* could be necessary.

When you run a live boot everything will be slow due to the limited bandwidth when reading from the CD. That hides the delay which comes from the desktop environment itself.

---

### Post by Thomas_J._Schmidt on 2014-01-24
Ok, I get it. Funny how our "pain thresholds" must be very different, then--I don't mind much what lag there is, from what I've seen so far of this LiveCD/laptop combination, compared to what I had to deal with running morbidly bloated WinXP on the same system. On the other hand, I suspect you would find the same lag intolerable, given your level of experience (grinning).

Thanks again for your guidance and support. I've enjoyed working with the Lubuntu LXDE desktop before, so I will likely try that on the HP and get back to you/anyone else it can help.

---

### Post by Thomas_J._Schmidt on 2014-01-24
I burned an Alternate Lubuntu ISO CD; it installed Lubuntu on the HP; the first time booting up, it is STILL stuck in that "Intel UNDI, PXE-2.0" netbooting loop. 
:mad: ](*,)

How can UNDI be disabled???

It's 11 pm local time, and those [unprintable] UNDIs are still in a knot! I'm going to bed....

---

### Post by mörgæs on 2014-01-25
There are some strange things here.

First, the output of Boot-Info (hard disk is 160 GB) does not match your hardware description as mentioned in first post (hard disk is 40 GB). Please run 

```
sudo lshw -sanitize > lshw.txt 
```

and post lshw.txt in CODE tags. This can be done in a live boot.


Second, Boot-Info talks about 

```
Error: Can't have a partition outside the disk!
```

Please reinstall using the alternate ISO selecting 'guided - use entire disk' in the process. Nothing should be reused from the previous install, especially not the partitioning scheme.

After that please run Boot-Info again and post the results.


Third, regarding the PXE boot problem please post the boot order as seen in BIOS.

---

### Post by Thomas_J._Schmidt on 2014-01-25
Yeah, sorry about mis-stating the hard drive size. My brother-in-law was the original owner, and must have upgraded to 160 GB when he had it. 

I'll follow through with your requests and post the results.

---

### Post by Thomas_J._Schmidt on 2014-01-25
OK, here's <lshw.txt> (sorry I don't know yet how to post it per your request "in code"):

```
computer
    description: Notebook
    product: Pavilion zv5200 (PL996UA#ABA)
    vendor: Hewlett-Packard
    version: F.21
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 08A0
       vendor: Compal
       physical id: 0
       version: 32.30
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.21
          date: 09/02/2004
          size: 114KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP Processor 3000+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.12.0
          slot: Socket A
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 512KiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: S1
             size: 1GiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: S2
             size: 1GiB
             width: 32 bits
     *-pci:0
          description: Host bridge
          product: nForce3 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a4
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64
          resources: irq:0 memory:f0000000-f7ffffff
        *-isa
             description: ISA bridge
             product: nForce3 LPC Bridge
             vendor: NVIDIA Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a6
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce3 SMBus
             vendor: NVIDIA Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:10 ioport:2040(size=64) ioport:2000(size=64)
        *-usb:0
             description: USB controller
             product: nForce3 USB 1.1
             vendor: NVIDIA Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a5
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:e8000000-e8000fff
        *-usb:1
             description: USB controller
             product: nForce3 USB 1.1
             vendor: NVIDIA Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a5
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:e8001000-e8001fff
        *-usb:2
             description: USB controller
             product: nForce3 USB 2.0
             vendor: NVIDIA Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:e8004000-e80040ff
        *-multimedia
             description: Multimedia audio controller
             product: nForce3 Audio
             vendor: NVIDIA Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0 maxlatency=5 mingnt=2
             resources: irq:21 ioport:1400(size=256) ioport:1c00(size=128) memory:e8002000-e8002fff
        *-communication UNCLAIMED
             description: Modem
             product: nForce3 Audio
             vendor: NVIDIA Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm generic cap_list
             configuration: latency=0 maxlatency=5 mingnt=2
             resources: ioport:1800(size=256) ioport:1c80(size=128) memory:e8003000-e8003fff
        *-ide
             description: IDE interface
             product: nForce3 IDE
             vendor: NVIDIA Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: scsi0
             logical name: scsi1
             version: a5
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2080(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD1600BEVE-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: [REMOVED]
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003e0cc
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: [REMOVED]
                   size: 147GiB
                   capacity: 147GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2014-01-25 02:58:06 filesystem=ext4 lastmountpoint=/target modified=2014-01-25 04:23:32 mounted=2014-01-25 04:22:14 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2046MiB
                   capacity: 2046MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2046MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-R2512
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/sr0
                logical name: /cdrom
                version: 1A04
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   capabilities: partitioned partitioned:dos
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=1ff05b67 state=mounted
                 *-volume UNCLAIMED
                      description: Hidden HPFS/NTFS partition
                      physical id: 1
                      capacity: 1579MiB
                      capabilities: primary bootable hidden
        *-pci:0
             description: PCI bridge
             product: nForce3 PCI Bridge
             vendor: NVIDIA Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=20480) memory:e8100000-e97fffff memory:80000000-87ffffff
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:18 ioport:7000(size=256) memory:e8104000-e81040ff
           *-network:1
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64
                resources: irq:17 memory:e8100000-e8101fff
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1620 PC Card Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:e8102000-e8102fff ioport:3c00(size=256) ioport:3800(size=256) memory:84000000-87ffffff memory:e8400000-e87fffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1620 PC Card Controller
                vendor: Texas Instruments
                physical id: 4.1
                bus info: pci@0000:02:04.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:18 memory:e8103000-e8103fff ioport:3400(size=256) ioport:3000(size=256) memory:80000000-83ffffff memory:e8c00000-e8ffffff
           *-generic UNCLAIMED
                description: System peripheral
                product: PCI1620 Firmware Loading Function
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:02:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=7
                resources: ioport:7400(size=64)
        *-pci:1
             description: PCI bridge
             product: nForce3 AGP Bridge
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:ea000000-eaffffff memory:f8000000-fc0fffff
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 420 Go 32M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
                resources: irq:16 memory:ea000000-eaffffff memory:f8000000-fbffffff memory:fc000000-fc07ffff memory:fc080000-fc09ffff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-23-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```
<end of lshw.txt>

The boot order that shows in the boot menu (press esc or F10) often leaves out the hard drive (?!). Booting up the HP just 20 minutes or so ago to resume work on this conundrum brought up a window displaying 

2. ATAPI CD-ROM Drive
3. Floppy Diskette Drive
4. Network Adaptor

<Enter Setup>

Entering the PhoenixBIOS Setup/Advanced/Boot Order usually shows

!-Hard Drive
  ! WDC WD1600BEVE-00UYT0
 ATAPI CD-ROM Drive
 Floppy Diskette Drive
 Network Adaptor

There are no apparent options to enable or disable the network adaptor by changing BIOS settings. Nor can I run a hard drive test in BIOS; the HP diagnostics in BIOS won't acknowledge the 160GB HD as an IDE drive.

I'll go reinstall the alternate ISO per your instructions, run Boot-Info, and let you know what comes of that.

---

### Post by QIII on 2014-01-25
Hello!

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header.

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks.

---

### Post by Thomas_J._Schmidt on 2014-01-25
Thanks, QIII for the edit and the code tag pointers.

Morgaes, I reinstalled with "guided--use entire disk", and the Intel UNDIs are still looping through

```

PXE-E53: No Boot Filename Received
PXE-M0F: Exiting PXE-ROM

```

Will go run Boot-Info and post results.

---

### Post by Thomas_J._Schmidt on 2014-01-26
Here we are, the Boot-Info (Boot-Repair URL):

[http://paste.ubuntu.com/6818404/](http://paste.ubuntu.com/6818404/)

Also, these warnings showed up in Terminal:

```

(glade2script:4822): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.4RT49W': No such file or directory

(glade2script:4822): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

---

### Post by Thomas_J._Schmidt on 2014-01-26
I googled the PXE error code and found this on the Hewlett-Packard site:

"&#8226;                             PXE-E53: No boot filename received.
               The client received at least one valid DHCP/BOOTP offer, but does not have a boot filename to download.                There are several possible causes:                                   [TABLE]
[TR]
[TD]&#8226;[/TD]
[TD]                         The DHCP Server and the PXE Server were located on the same server,                         but one of them was moved to a different server.                         This would result in an incorrect PXE Server configuration.                         

                        To resolve this issue, reinstall the PXE Server component of the Altiris Deployment Solution.[/TD]
[/TR]
[TR]
[TD]&#8226;[/TD]
[TD]                         The DHCP relay agent, either a Proxy DHCP Server or a switch configured with                         helper addresses, is not configured correctly. For example, if DHCP and PXE                         are on separate servers, the DHCP relay agent needs to have both addresses                         in its configuration.                         

                        To resolve this issue, correct the DHCP relay agent configuration.[/TD]
[/TR]
[TR]
[TD]&#8226;[/TD]
[TD]                         If the Microsoft DHCP service is installed on                         the PXE server, but is disabled or unconfigured, Altiris PXE Setup configures                         PXE to work with the local DHCP service (even if the DHCP service is disabled).                         This causes the PXE server to not respond to PXE clients that get a DHCP                         address from DHCP services running elsewhere on the network.                         

                        To resolve this issue, remove Microsoft DHCP services from the PXE server and reinstall                         the PXE Server component of the Altiris Deployment Solution."[/TD]
[/TR]
[/TABLE]
Might this be the problem, or part of it, that prevents Ubuntu distros from booting on my HP zv5320us? If so, where is this PXE-ROM? How can it be removed or disabled?

---

### Post by Thomas_J._Schmidt on 2014-01-27
I'll admit I'm impatient to get this HP zv5320us laptop up and running some flavor of ubuntu. Having already run boot-repair and posted the summary-report url of Sunday 26 Jan but no instructions from anyone since, I'm ready to run boot-repair again, this time experimentally trying the recommended repairs. I'll post what comes of the experiments.

---

