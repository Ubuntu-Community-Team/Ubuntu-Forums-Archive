---
title: "help in toshiba laptop"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by mostafabasal on 2012-01-02
hello every bodies
i'm new user in ubuntu system
i've toshiba laptop satellite L655
middle east version 
i've wireles problem in web cracking 
my wireless lan chipset is broadcom 4313
it doesn't go for monitoring mode
this is what i get from command 
```
sudo lshw
             size: 1GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 24
          bus info: cpu@0
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          slot: CPU
          size: 933MHz
          capacity: 933MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=4
        *-cache:0
             description: L3 cache
             physical id: 25
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 27
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 28
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 1.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 1.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 1.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 1.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 1.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 1.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 1.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 1.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 1.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 1.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 1.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 1.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 1.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 1.10
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 26
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:d6000000-d60fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Manhattan [Mobility Radeon HD 5400 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:45 memory:c0000000-cfffffff memory:d6000000-d601ffff ioport:4000(size=256) memory:d6040000-d605ffff
           *-multimedia
                description: Audio device
                product: Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:43 memory:d6020000-d6023fff
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:d6106100-d610610f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d6105c00-d6105fff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:42 memory:d6100000-d6103fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:d5000000-d5ffffff ioport:d0000000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8152 v1.1 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c1
                serial: 00:26:6c:8d:af:20
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:44 memory:d5000000-d503ffff ioport:3000(size=128)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:d4000000-d4ffffff ioport:d1000000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 4c:ed:de:1a:c5:0e
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-14-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:d4000000-d4003fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:d3000000-d3ffffff ioport:d2000000(size=16777216)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d6105800-d6105bff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             logical name: scsi5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:5048(size=8) ioport:5054(size=4) ioport:5040(size=8) ioport:5050(size=4) ioport:5020(size=32) memory:d6105000-d61057ff
           *-disk
                description: ATA Disk
                product: ST9320325AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 0002
                serial: 6VD63K0Q
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b85787ae
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: d024-0ba7
                   size: 398MiB
                   capacity: 400MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-11-03 03:44:35 filesystem=ntfs label=SYSTEM state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: d435c779-0ed9-1f40-ac03-a5cb15b182d2
                   size: 120GiB
                   capacity: 120GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-11-03 03:44:40 filesystem=ntfs label=WINDOWS modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: a692b6f6-1a0b-b348-8098-cf81b0fe37eb
                   size: 148GiB
                   capacity: 148GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-08-11 23:09:28 filesystem=ntfs label=Data state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@1:0.0.0,4
                   logical name: /dev/sda4
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 25GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2997MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT30N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TN08
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d6106000-d61060ff ioport:5000(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@2:1.1
          logical name: scsi9
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/sdb
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
```
so what can i do?

---

### Post by mostafabasal on 2012-01-02
sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firmware-b43-lpphy-installer
The following NEW packages will be installed:
  firmware-b43-installer
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0 B/3,272 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 170841 files and directories currently installed.)
Removing firmware-b43-lpphy-installer ...
Selecting previously deselected package firmware-b43-installer.
(Reading database ... 170838 files and directories currently installed.)
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a014-9_all.deb) ...
Setting up firmware-b43-installer (1:014-9) ...
Unsupported device(s) found: PCI id 14e4:4727 
Aborting.
this what i get after removing sta driver

---

### Post by ts3 on 2012-01-02
> **mostafabasal said:**
> sudo apt-get install firmware-b43-installer

Based on my experience, b43 does not support broadcom 4313 (4727).  I have the same chipset on an hp laptop and it took me a while to figure it out.  My thread on the subject is here: [http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170)

If you have wired connection your best bet is to get bcmwl-kernel-source driver from the Ubuntu Software Center.  You need to make sure that the wl driver is not blacklisted.  Since I am complete newbie (using Ubuntu since November 2011) I had to figure how to do things from first principles (e.g. how to blacklist/un-blacklist) and I tried to describe it in detail in the thread I linked to.  Hope this helps :)

---

### Post by idoitprone on 2012-01-02
```
lspci -v | grep -A 10 -i network
```


let see your card

---

### Post by Rodney9 on 2012-01-02
This Member got their L640 with broadcom 4313 working, see here - 
[http://ubuntuforums.org/archive/index.php/t-1879096.html](http://ubuntuforums.org/archive/index.php/t-1879096.html)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by ts3 on 2012-01-02
> **Rodney9 said:**
> This Member got their L640 with broadcom 4313 working, see here - 
[http://ubuntuforums.org/archive/index.php/t-1879096.html](http://ubuntuforums.org/archive/index.php/t-1879096.html)

I wish I'd seen that back in November, it would have saved me a couple of days of trying to figure things out. :) It should work, my only comment is that if 

```
 lspci -k 
``` 

shows a driver such as brmcsmac then that driver would need to be blacklisted as well, in addition to the bcma driver.

---

### Post by mostafabasal on 2012-01-03
lspci -v | grep -A 10 -i network
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Askey Computer Corp. Device 7175
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: brcmsmac
    Kernel modules: bcma, brcmsmac

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0

---

### Post by mostafabasal on 2012-01-03
```
lspci -k
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series]
    Subsystem: Toshiba America Info Systems Device fd12
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
    Subsystem: Toshiba America Info Systems Device fd12
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: atl1c
    Kernel modules: atl1c
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Askey Computer Corp. Device 7175
    Kernel driver in use: brcmsmac
    Kernel modules: bcma, brcmsmac
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
```

---

### Post by mostafabasal on 2012-01-03
i try many ideas but no one work 
what is the best one to try?

---

### Post by mostafabasal on 2012-01-04
?

---

### Post by idoitprone on 2012-01-04
> **mostafabasal said:**
> lspci -v | grep -A 10 -i network
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Askey Computer Corp. Device 7175
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: brcmsmac
    Kernel modules:** bcma, brcmsmac**

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0

[http://en.gentoo-wiki.com/wiki/Broadcom_43xx](http://en.gentoo-wiki.com/wiki/Broadcom_43xx)

your modules are conflicting each other and it does not seem to be the correct modules

try removing one of the  modules first

```
modprobe -r bcma
```you may have to blacklist if it keep reloading

[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

make a file in 
/etc/modprobe.d/blacklist-custom with these contents ```
#
# Custom blacklist file so I don't mess with any of the files that come with
# the module-init-tools package
blacklist bcma 
```[http://wiki.debian.org/wl](http://wiki.debian.org/wl)

wl modules should be supported 
[https://wiki.archlinux.org/index.php/Broadcom_wireless#brcmsmac.2Fbrcmfmac](https://wiki.archlinux.org/index.php/Broadcom_wireless#brcmsmac.2Fbrcmfmac)
it seems it causes some problems
```
modprobe -r  bcma brcmsmac
``````
modprobe wl
```

---

### Post by ts3 on 2012-01-04
> **idoitprone said:**
> your modules are conflicting each other and it does not seem to be the correct modules

Yes, exactly.  I am by no means an expert but I have the same chipset as the OP - Broadcom BCM 4313[14e4:4727] so perhaps this will help.  The info posted earlier shows that the OP's driver is brcmsmac, there's also bcma installed, neither works with this chipset.  The driver that works is wl (that is WL not w1).  My suggestion is (put briefly)

- Deactivate the STA driver (System Info -> Hardware -> Additional Drivers
- Through Ubuntu Software Center uninstall b43 and similar drivers and any currently installed wl drivers (you'll install wl later)
- Check for conflicts -> open terminal (Ctrl + Alt + T) then type, one by one, the following commands (after the first, the prompt will ask for your password, type the password, ignore the fact that nothing shows on the screen while you type)

```
sudo lsmod | grep ssb 
sudo lsmod | grep bcma
sudo lsmod | grep b43
sudo lsmod | grep wl
sudo lsmod | grep brcmsmac 
```If any of the above shows in red please remove:

```
sudo rmmod bcma
``` (the bcma in last line is example, remove whatever shows up).  Blacklist the drivers you don't want and make sure wl is not blacklisted: open file browser, go to Filesystem -> /etc/modprobe.d/blacklist.conf

Open and read, also check in /etc/modprobe.d/blacklist-local.conf - I had this and it blacklisted wl, so had to remove blacklist (please see thread I linked earlier on how to edit those files with root privileges or google how to blacklist / unblacklist, also known as comment out).  Generally I'd suggest reading all files in /etc/modprobe.d/, it's quite educational.

Restart, run the above commands again to make sure the undesired drivers (bcma, brcmsmac) are gone

Go to Ubuntu Software Center (you'll need wired connection for this) & find bcmwl-kernel-source, install, wireless should be working.  May need to reboot.  

```
lspci -k
``` should show a wl driver somewhere in there

Please read the links in replies others and I posted on your thread, all the advice you need to do this is there.

Sorry for disjointed post, am in a rush.  Google anything you're not sure about and google error messages, if you get any.

P.S. Post here what you try to do and whether it's working.  Take screenshots (Alt + pr t sc) and back up files before changing them (or, again, take screenshots).  Good luck

---

### Post by mostafabasal on 2012-01-05
```
lspci -k
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series]
    Subsystem: Toshiba America Info Systems Device fd12
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
    Subsystem: Toshiba America Info Systems Device fd12
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: atl1c
    Kernel modules: atl1c
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Askey Computer Corp. Device 7175
    Kernel driver in use: wl
    Kernel modules: wl, bcma, brcmsmac
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
```
this is what i got after doing that

---

### Post by mostafabasal on 2012-01-05
my device name i think it changed to eth1
and unable to use airmon-ng and other commands related even monitoring mode

lshw -c network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:8d:af:20
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:44 memory:d5000000-d503ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 4c:ed:de:1a:c5:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 wireless=IEEE 802.11
       resources: irq:17 memory:d4000000-d4003fff

---

### Post by lofarcom on 2012-01-05
if your using a broadcom wireless card (802.11 something something), i found this very helpful. 
$ sudo apt-get update
$ sudo apt-get install firmware-b43-installer
$ sudo apt-get remove bcmwl-kernel-source
$ sudo reboot

when you install ubuntu, they download their own software which renders the card un compatible. but a simple work around will help.

P.S: this command was found from this website. hope it helps. 

[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

---

### Post by mostafabasal on 2012-01-05
they remove the driver and i install them again:(

---

### Post by ts3 on 2012-01-05
> **mostafabasal said:**
> lspci -k
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Askey Computer Corp. Device 7175
    Kernel driver in use: wl
    Kernel modules: wl, bcma, brcmsmac
this is what i got after doing that

Ok, it looks like you have the correct driver (wl) in use; the bcma and bcmsmac are there but not in use.  I am not sure whether this might still be a problem, will look into this but later, sorry :(

A couple of other, simple, suggestions about things that sometimes get overlooked: is there a hardware switch for wireless?  On my hp laptop it's one of the Fn buttons with a light that changes colour depending whether it's on or of.  Take a look at this, toggle a few times.  You can also check this using the terminal:

```
rfkill list all
```
to check, then

```
sudo rfkill unblock all
```

then check the results by running [FONT="Courier New"]rfkill list all[/FONT] again

Another thing, a simple reboot or may help after loading the wl driver and blacklisting the others.  Perhaps you can try to actually remove bcma and brcmsmac by running

```
sudo rmmod bcma
sudo rmmod brcmsmac
```

then reboot again.

About the logical name changing from wlan0 to eth1, sorry about that, not sure what it means.  I googled a bit but didn't find anything definitive.  One ubuntu forums answer suggested that this might change back after a few reboots but I am really not sure.  Anyone else? I am out of ideas right now.

---

### Post by idoitprone on 2012-01-06
> **mostafabasal said:**
> lspci -k

    lspci -k
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Askey Computer Corp. Device 7175
    Kernel driver in use: wl
    Kernel modules:** wl, bcma, brcmsmac**
this is what i got after doing that


Sorry I didnt follow up earlier but you cannot use 3 modules at the same time. I believe I mention that those modules will confict each other and cause ur internet to now work

I believe wl and brcmsmac is supported. Choose either one, but not both.

[http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211)

---

### Post by mostafabasal on 2012-01-09
i can't get them black listed every time i make them they get to run again
what is wrong?

---

### Post by ts3 on 2012-01-09
> **mostafabasal said:**
> i can't get them black listed every time i make them they get to run again
what is wrong?

What is the content of /etc/modprobe.d/blacklist.conf?  Is there a file /etc/modprobe.d/blacklist-local.conf and what's its content?

---

### Post by mostafabasal on 2012-01-09
blacklist.conf


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist bcma
blacklist wl

---

### Post by mostafabasal on 2012-01-09
blacklist-local.conf is empty i delete its content previously
adding wl to blacklist as it shown to me with red
un installing drivers from ubuntu soft mngr
de activating sta driver
removing kernel drivers but ......this what i got when type lspci -k
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series]
    Subsystem: Toshiba America Info Systems Device fd12
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
    Subsystem: Toshiba America Info Systems Device fd12
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: atl1c
    Kernel modules: atl1c
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Askey Computer Corp. Device 7175
    Kernel modules: bcma, brcmsmac
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
sudo apt-get remove brcmsmac-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package brcmsmac-kernel-source

 sudo apt-get remove bcma-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcma-kernel-source
:(

---

### Post by ts3 on 2012-01-09
> **mostafabasal said:**
> blacklist.conf
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist bcma
blacklist wl

WL is blacklisted (see last line) so it cannot load.  You need to comment it out (open the file from terminal with [FONT="Courier New"]gksudo[/FONT] and add # before that line).  

Reboot

If still no internet check for hardware switches (with [FONT="Courier New"]rfkill list all[/FONT])

I'd also suggest going through the other files (through the file manager, not with root privileges) to check that WL is not blacklisted somewhere else in /etc/modprobe.d

---

### Post by ts3 on 2012-01-09
> sudo apt-get remove bcma-kernel-source
sudo apt-get remove brcmsmac-kernel-source

Er, I don't think these are the right commands.  The bcma and brcmsmac drivers are installed/uninstalled in a different way.

I'll try to explain the steps briefly in another post below but in the meantime please check my post #12 from last week.

> adding wl to blacklist as it shown to me with red

Please do not blacklist wl - this is the driver that works.

---

### Post by ts3 on 2012-01-09
OK, I'll try to summarise below:

1) CLEAN OUT all conflicting wireless drivers and prior versions of wl that might be old/incompatible

a) through System Info -> Additional Drivers, then deactivate STA drivers
b) through Ubuntu Software Centre -> in search box (top right) type b43 and remove all drivers that show up as installed (such as firmware-b43-installer or b43-fwcutter)
c) through Ubuntu Software Centre -> in search box type bcmwl and remove the bcmwl-kernel-source.  Please note - you'll install this later

2) CHECK what drivers, if any, are still there and remove if necessary:

```
sudo lsmod | grep ssb
```

Then please replace ssb with the following, one by one: bcma, b43, wl, brcmsmac

If any of these shows please remove

```
sudo rmmod bcma
```
etc.  Even if wl shows please remove temporarily.

3) CHECK, again, /etc/modprobe.d/blacklist.conf

Make sure that bcma, brcmsmac, ssb, etc. ARE blacklisted
Make sure that wl is NOT blacklisted; if blacklisted please comment out by adding # at the beginning of the line.  In addition, please make sure that wl is NOT blacklisted in the other files in /etc/modprobe.d/

4) REBOOT, then go through steps 2) and 3) again to make sure none of the drivers are there.  At this point, if you run [FONT="Courier New"]lspci -k[/FONT] it probably won't show any wireless drivers.

5) INSTALL the driver you need: Go to Ubuntu Software Centre, type "bcm" in search box and install the drivers that appear, bcmwl-kernel-source, broadcom-sta-common and broadcom-sta-source   

6) REBOOT; wireless should be working - if not please run

```
rfkill list all
```

to check for hardware switches.  

Post results :) 
Good luck.

---

### Post by wildmanne39 on 2012-01-09
Hi, does anyone mind if I give it a shot?
If no please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mostafabasal on 2012-01-09
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux sasa-Satellite-L655 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by mostafabasal on 2012-01-09
sudo lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: atl1c
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7175]
    Kernel modules: bcma, brcmsmac

---

### Post by mostafabasal on 2012-01-09
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

---

### Post by ts3 on 2012-01-09
> **wildmanne39 said:**
> Hi, does anyone mind if I give it a shot?

Please do :) I am freshly out of ideas (had only and that did not seem to work too well :) )

---

### Post by mostafabasal on 2012-01-09
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by mostafabasal on 2012-01-09
lsmod
Module                  Size  Used by
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
crc_ccitt              12595  1 ppp_async
option                 25463  2 
usb_wwan               19779  1 option
uas                    17699  0 
usbserial              37203  7 option,usb_wwan
usb_storage            44173  0 
hidp                   22351  0 
hid                    77367  1 hidp
bnep                   17923  2 
rfcomm                 38408  12 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dm_multipath           22771  0 
toshiba_bluetooth      12711  0 
video                  18908  0 
sparse_keymap          13658  0 
fglrx                2595537  107 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
btusb                  18160  2 
bluetooth             148839  24 hidp,bnep,rfcomm,btusb
uvcvideo               67271  0 
psmouse                73673  0 
videodev               85626  1 uvcvideo
serio_raw              12990  0 
soundcore              12600  1 snd
mei                    36466  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
dm_raid45              76451  0 
ahci                   21634  2 
libahci                25727  1 ahci
atl1c                  36638  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash

---

### Post by mostafabasal on 2012-01-09
i don't know why it display the kernel drivers bcma,brcmsmac although  i get all mentioned steps ensuring that bcma and brcma black listed wl not black listed sta driver not installed from additional driver and br43 not installed ,bcmwl kernel source not installed yet and no display of wireless in network connection gained by laptop

---

### Post by wildmanne39 on 2012-01-09
Hi, please make sure you unblacklisted the wl driver, if you created a wireless connection delete it and let network manager detect your network. 
```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
see if it comes on if not reboot now.

This driver may not support monitor mode please set your network to look like this except check auto connect.

Also read my first post please I gave directions on how to post using code tags and always post all the information in one post.
Thanks

---

### Post by mostafabasal on 2012-01-09
now after i install bcmwl my WIRELESS IS DIABLED BY HARDWARE SWITCH
GETTING FROM START POINT:(
:(
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by mostafabasal on 2012-01-09
[QUOTE=wildmanne39;11599905]Hi, please make sure you unblacklisted the wl driver, if you created a wireless connection delete it and let network manager detect your network. 
i'm using vodafone usb stick for connection

---

### Post by wildmanne39 on 2012-01-09
Hi, check and make sure your switch is not physically turned off because that is what this normally means.

Please post:
```
lsmod | grep wl
```
```
iwconfig
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n75
```
```
cat /etc/modprobe.d/blacklist.conf
```
here by clicking on new reply and click # and paste the information between the brackets.

Thank you

---

### Post by wildmanne39 on 2012-01-09
Hi, the vodafone usb stick on the same computer as the one we are trying to get going?
Thanks

---

### Post by mostafabasal on 2012-01-10
```
sasa@sasa-Satellite-L655:~$ lsmod | grep wl
wl                   2646601  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
sasa@sasa-Satellite-L655:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

ppp0      no wireless extensions.

sasa@sasa-Satellite-L655:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n75
[sudo] password for sasa: 
Jan 10 05:23:16 sasa-Satellite-L655 NetworkManager[922]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jan 10 05:23:16 sasa-Satellite-L655 NetworkManager[922]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 10 05:23:16 sasa-Satellite-L655 NetworkManager[922]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1/rfkill1) (driver (unknown))
Jan 10 05:23:27 sasa-Satellite-L655 NetworkManager[922]: <error> [1326165807.9562] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Jan 10 05:23:27 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Jan 10 05:23:27 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Jan 10 05:23:27 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 10 05:23:27 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): now managed
Jan 10 05:23:27 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 10 05:23:27 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): bringing up device.
Jan 10 05:23:27 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): deactivating device (reason 'managed') [2]
Jan 10 05:24:34 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): now unmanaged
Jan 10 05:24:34 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jan 10 05:24:51 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): now managed
Jan 10 05:24:51 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 10 05:24:51 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): bringing up device.
Jan 10 05:24:51 sasa-Satellite-L655 NetworkManager[922]: <info> (eth1): deactivating device (reason 'managed') [2]
Jan 10 05:37:43 sasa-Satellite-L655 kernel: [   16.247562] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 10 05:37:43 sasa-Satellite-L655 kernel: [   16.247572] wl 0000:03:00.0: setting latency timer to 64
Jan 10 05:37:43 sasa-Satellite-L655 kernel: [   16.462586] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
Jan 10 05:37:43 sasa-Satellite-L655 NetworkManager[924]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1)
Jan 10 05:37:43 sasa-Satellite-L655 NetworkManager[924]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jan 10 05:37:43 sasa-Satellite-L655 NetworkManager[924]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 10 05:37:43 sasa-Satellite-L655 NetworkManager[924]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1/rfkill1) (driver (unknown))
Jan 10 05:37:54 sasa-Satellite-L655 NetworkManager[924]: <error> [1326166674.722021] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Jan 10 05:37:54 sasa-Satellite-L655 NetworkManager[924]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Jan 10 05:37:54 sasa-Satellite-L655 NetworkManager[924]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Jan 10 05:37:54 sasa-Satellite-L655 NetworkManager[924]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 10 05:37:54 sasa-Satellite-L655 NetworkManager[924]: <info> (eth1): now managed
Jan 10 05:37:54 sasa-Satellite-L655 NetworkManager[924]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 10 05:37:54 sasa-Satellite-L655 NetworkManager[924]: <info> (eth1): bringing up device.
Jan 10 05:37:54 sasa-Satellite-L655 NetworkManager[924]: <info> (eth1): deactivating device (reason 'managed') [2]
Jan 10 13:44:53 sasa-Satellite-L655 kernel: [   16.474918] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 10 13:44:53 sasa-Satellite-L655 kernel: [   16.474928] wl 0000:03:00.0: setting latency timer to 64
Jan 10 13:44:53 sasa-Satellite-L655 kernel: [   16.680187] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
Jan 10 13:44:53 sasa-Satellite-L655 NetworkManager[952]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1)
Jan 10 13:44:53 sasa-Satellite-L655 NetworkManager[952]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jan 10 13:44:54 sasa-Satellite-L655 NetworkManager[952]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 10 13:44:54 sasa-Satellite-L655 NetworkManager[952]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1/rfkill0) (driver (unknown))
Jan 10 13:44:57 sasa-Satellite-L655 NetworkManager[952]: <error> [1326195898.3861] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Jan 10 13:44:57 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Jan 10 13:44:57 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Jan 10 13:44:57 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 10 13:44:57 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): now managed
Jan 10 13:44:57 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 10 13:44:58 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): bringing up device.
Jan 10 13:44:58 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): preparing device.
Jan 10 13:44:58 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): deactivating device (reason 'managed') [2]
Jan 10 13:44:58 sasa-Satellite-L655 dbus[914]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan 10 13:44:58 sasa-Satellite-L655 dbus[914]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan 10 13:44:58 sasa-Satellite-L655 NetworkManager[952]: <info> wpa_supplicant started
Jan 10 13:44:58 sasa-Satellite-L655 wpa_supplicant[1152]: nl80211: 'nl80211' generic netlink not found
Jan 10 13:44:58 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): supplicant interface state: starting -> ready
Jan 10 13:44:58 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 10 13:44:58 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): supplicant interface state: ready -> inactive
Jan 10 13:44:59 sasa-Satellite-L655 avahi-daemon[953]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::4eed:deff:fe1a:c50e.
Jan 10 13:44:59 sasa-Satellite-L655 avahi-daemon[953]: New relevant interface eth1.IPv6 for mDNS.
Jan 10 13:44:59 sasa-Satellite-L655 avahi-daemon[953]: Registering new address record for fe80::4eed:deff:fe1a:c50e on eth1.*.
Jan 10 13:45:08 sasa-Satellite-L655 kernel: [   39.439842] eth1: no IPv6 routers present
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> Activation (eth1) starting connection 'Drahem'
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> Activation (eth1/wireless): access point 'Drahem' has security, but secrets are required.
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 10 13:45:39 sasa-Satellite-L655 NetworkManager[952]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan 10 13:45:43 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jan 10 13:45:43 sasa-Satellite-L655 NetworkManager[952]: <warn> Activation (eth1) failed for access point (Drahem)
Jan 10 13:45:43 sasa-Satellite-L655 NetworkManager[952]: <warn> Activation (eth1) failed.
Jan 10 13:45:43 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 10 13:45:43 sasa-Satellite-L655 NetworkManager[952]: <info> (eth1): deactivating device (reason 'none') [0]
sasa@sasa-Satellite-L655:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist bcma
blacklist brcm80211
blacklist brcmsma
```

---

### Post by mostafabasal on 2012-01-10
yes i'm connected with internet via usb stick modem not lan
and i check my windows 7 to see if wireless is disabled i found it turned off 
the function key didn't work in ubuntu as my wireless key in keyboard is fn+f8

---

### Post by mostafabasal on 2012-01-10
why my chipset here is unknown?
```
sudo airmon-ng start wlan0
[sudo] password for sasa: 


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
952    NetworkManager
953    avahi-daemon
955    avahi-daemon
1152    wpa_supplicant


Interface    Chipset        Driver

eth1        Unknown         wl

```
and i didn't know it wlan0 or eth1
```
sudo airmon-ng start eth1
[sudo] password for sasa: 


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
952    NetworkManager
953    avahi-daemon
955    avahi-daemon
1152    wpa_supplicant


Interface    Chipset        Driver

eth1        Unknown         wl (monitor mode enabled)

```

---

### Post by wildmanne39 on 2012-01-10
Hi, first to get your wireless working you have to disconnect your usb adapter they can not both be connected at the same time.

Also if I am correct you want this to use monitor mode as I said this driver will not use monitor mode.

You can change the driver and see if that helps.

Have you had this card working before but you just can not get it to work in monitor mode so you can crack networks?
Thanks

---

### Post by mostafabasal on 2012-01-12
thanks but what driver i can download ?
my wireless lan was working in windows  normally 
its first time to use linux system "i like this system but i feel it still need to upgrades that fill the gap from transferring from win 7

---

### Post by wildmanne39 on 2012-01-12
Hi, the b43 should be able to work with this card, with this kernel version however not all functions may be supported yet.

Let's stick to this driver and see if we can work it through. I hope you have not changed any settings since you posted the information I asked for.

Your system file shows ipv6 is still enabled, did you change your settings to match the screenshots in post 34?

Please do this:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit.
```
rmmod -f wl
rfkill unblock all
modprobe wl
```
Then save and close gedit.
Then unplug your usb adapter and reboot.
Thanks

---

### Post by mostafabasal on 2012-01-22
sorry [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") thanks for your help and support so much 
but i lost my control for a while on my nervous system:) erasing ubuntu system from lap
i just wait a period to calm down and trying again with this useless chipset 

i think to buy an external usb wifi is it good idea?

---

### Post by samanx on 2012-11-14
> **lofarcom said:**
> if your using a broadcom wireless card (802.11 something something), i found this very helpful. 
$ sudo apt-get update
$ sudo apt-get install firmware-b43-installer
$ sudo apt-get remove bcmwl-kernel-source
$ sudo reboot

when you install ubuntu, they download their own software which renders the card un compatible. but a simple work around will help.

P.S: this command was found from this website. hope it helps. 

[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

Thank you lofarcom, this was the solution for me, I upgraded to a new kernel in linux mint and my wireless broke after following the steps you posted above everything worked like charm, sorry for my english i'm not a native english speaker. :D

---

