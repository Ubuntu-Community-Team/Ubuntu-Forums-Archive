---
title: "Display issues with ubuntu unity."
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sasanka_g_v on 2011-09-30
Hi everyone, I have a weird problem with the screen. I am attaching the screenshot of my screen. Its a bit difficult to explain. I shall give a try.

Background is displaced from upper left corner. Further, once I close any application, the window doesn;t vanish, rather there is a trail of it appearing on the screen. 

This happens only if I choose session to be Ubuntu rather than ubuntu 2d at login. I presume its a issue with unity3d.

Can someone suggest me what needs to be done.

---

### Post by clivejo on 2011-09-30
+1

Ever since I did a unity --reset and reboot I get a screen like this.  

My graphic is Nvidia, using 280.13 driver from the Nvidia website.  OpenGL is working (glxgears)

---

### Post by scottstensland on 2011-09-30
I also have this same issue.  

ubuntu 11.10 fully updated daily

this problem started after yesterday's big update - Sept 29th
which included over 100 package updates so not sure
of which is offending package.

app windows can be placed anywhere as normal, however when I
move a window it leaves behind a trail of its contents which are
not getting auto erased - guess some display driver issue.
My ubuntu 11.10 is fully standard starting from a base of alpha 1 with no absurd ppa so many others probably share this same issue

ASUS F70SL laptop

```


 glxinfo | grep "renderer string"
OpenGL renderer string: GeForce 9300M GS/PCI/SSE2


sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.t34YpJyo+N0
  Hardware Class: framebuffer
  Model: "NVIDIA G98 Board - 05666e90"
  Vendor: "NVIDIA Corporation"
  Device: "G98 Board - 05666e90"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xfb000000-0xfbdfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

sudo lshw

```
 
khamchatka                
    description: Notebook
    version: 1.0
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: chassis=notebook cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=0011BACF-512E-DE81-2DED-00248CA236D6
  *-core
       description: Motherboard
       product: F70SL
       vendor: ASUS CORPORATION
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 211
          date: 02/18/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: CPU 1
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 267MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
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
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 2400MHz
          capabilities: vmx ht
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:d000(size=4096) memory:fa000000-fdefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G98 [GeForce 9300M GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fc000000-fcffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc00(size=128) memory:fdee0000-fdefffff
        *-isa
             description: ISA bridge
             product: SiS968 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fff0(size=16)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:f9fff000-f9ffffff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:f9ffe000-f9ffefff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:22 memory:f9ffd000-f9ffdfff
        *-network
             description: Ethernet interface
             product: 191 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 02
             serial: 00:24:8c:a2:36:d6
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.4 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
             resources: irq:19 memory:f9ffcc00-f9ffcc7f ioport:cc00(size=128)
        *-ide:1
             description: IDE interface
             product: SATA Controller / IDE mode
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi2
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_sis latency=64
             resources: irq:17 ioport:c800(size=8) ioport:c400(size=4) ioport:c000(size=8) ioport:bc00(size=4) ioport:b800(size=16) ioport:b400(size=128)
           *-disk
                description: ATA Disk
                product: ST9500325AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0002
                serial: 5VE1A3QW
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b066f
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 4b62fe24-0fe1-44c2-a4cf-5e314abd894b
                   size: 462GiB
                   capacity: 462GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-09-09 00:05:26 filesystem=ext4 lastmountpoint=/ modified=2011-09-21 11:30:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-09-30 08:58:47 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 3070MiB
                   capacity: 3070MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3070MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T50N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RR07
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 memory:fdf00000-fdffffff
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:22:43:99:f1:04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:fdff0000-fdffffff
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:e000(size=4096) memory:fe000000-febfffff ioport:f6000000(size=50331648)
        *-multimedia
             description: Audio device
             product: Azalia Audio Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52
             resources: irq:18 memory:f9ff4000-f9ff7fff
     *-scsi
          physical id: 2
          bus info: usb@1:8
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb

```




Anyone know of cmds I can run to help t/s this problem ?
Please advise

---

### Post by clivejo on 2011-09-30
I have just disabled the Unity plugin in the Compiz Settings Manager.  Logged out and then re-enabled the plugin, seems to have got rid of that bar down the desktop which leaves shadows.

There was an issue with the left reveal which I reset back to Unity which seems to have fixed it.

Someone else try this and see if it works?


PS : I can now re-size the icons on the dash !!! Happy days!

---

### Post by Blasphemist on 2011-09-30
Try these commands that reset compiz. One at a time of course.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```
Clivejo, wouldn't it be more accurate to say that you disabled and re-enabled the unity plugin in compiz? I don't know how much difference there is in that and a reset of it as shown in a post above.

---

### Post by ratcheer on 2011-09-30
My system was messed up like that, this morning. I installed all the latest updates, now things are back to normal.

Tim

---

### Post by clivejo on 2011-09-30
> **Blasphemist said:**
> Clivejo, wouldn't it be more accurate to say that you disabled and re-enabled the unity plugin in compiz? I don't know how much difference there is in that and a reset of it as shown in a post above.

Yes your right. I've corrected my post.

I dont know, but it has fixed the problems I was having.

---

