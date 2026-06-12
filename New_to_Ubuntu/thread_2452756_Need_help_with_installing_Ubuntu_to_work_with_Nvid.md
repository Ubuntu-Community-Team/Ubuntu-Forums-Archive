---
title: "Need help with installing Ubuntu to work with Nvidia graphics card"
date: 2020-10-27
forum: New to Ubuntu
---

### Post by jwoodruff on 2020-10-27
Hi everyone/anyone. I decided to install Ubuntu on my pc after windows 7 sundown. I've used Ubuntu before, but I'm having trouble with system stability and it seems to be due to a compatibility issue with the graphics hardware.
Graphics card: (output from Lspci | grep VGA) in terminal), 00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

I've installed Ubuntu on my "e-Machines" desktop computer, which ran 64 bit windows 7 previously and remains on a partition created when I first installed Ubuntu. I initially tried Ubuntu 18.04 after having graphics trouble when running 20.04 from a USB stick, but had similar problems with 18.04, so after installing it to run along side windows, I decided to try upgrading to Ubuntu 20.04.
I've been struggling to try and get a "compatible" graphics driver to work - with both 18.04 and 20.04 versions. I'm using a Samsung flatscreen monitor ("SyncMaster S19B420") - graphics are garbled and open windows continually becoming distorted to the point of unusable. 
Can someone please tell me if there is a way to correct this? I've read conflicting suggestions on internet searches - some suggest using generic drivers others suggest using propietary drivers. When I had 18.04 installed I tried installing the driver I downloaded off Nvidia website and the screen wouldn't even appear.
Thanks for any help offered.
Some system details:

 ```
Processor Type:
$ uname -p
x86_64

System Info:
    description: Desktop Computer
    product: EL1352 (To Be Filled By O.E.M.)
    vendor: eMachines
    serial: PTNBT020060161515F2700
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=eMachines Desktop frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=To Be Filled By O.E.M. uuid=00262D2E-25FD-2010-0423-063349000000
  *-core
       description: Motherboard
       product: EL1350
       vendor: eMachines
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends, Inc.
          physical id: 0
          version: P01-A1
          date: 01/28/2010
          size: 64KiB
          capacity: 1MiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II X2 215 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) II X2 215 Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2100MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate vmmcall npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies
             configuration: level=2
     *-memory:0
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: ACR256X64D3U1333C9
             vendor: Kingston
             physical id: 0
             serial: C72D0651
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: ACR256X64D3U1333C9
             vendor: Kingston
             physical id: 1
             serial: C7160651
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:4f00(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:febff000-febfffff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 5.4.0-52-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 5.04
             capabilities: usb-1.10
             configuration: driver=hub slots=10 speed=12Mbit/s
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:febfec00-febfecff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 5.4.0-52-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 5.04
             capabilities: usb-2.00
             configuration: driver=hub slots=10 speed=480Mbit/s
           *-usb:0
                description: Mass storage device
                product: Mass Storage Device
                vendor: Generic
                physical id: 5
                bus info: usb@1:5
                logical name: scsi6
                version: 1.00
                serial: 058F63616476
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=250mA speed=480Mbit/s
              *-disk:0
                   description: SCSI Disk
                   product: Compact Flash
                   vendor: Generic-
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/sdb
                   version: 1.01
                   capabilities: removable
                   configuration: logicalsectorsize=512 sectorsize=512
                 *-medium
                      physical id: 0
                      logical name: /dev/sdb
              *-disk:1
                   description: SCSI Disk
                   product: Flash Reader
                   vendor: Multiple
                   physical id: 0.0.1
                   bus info: scsi@6:0.0.1
                   logical name: /dev/sdc
                   version: 1.05
                   capabilities: removable
                   configuration: logicalsectorsize=512 sectorsize=512
                 *-medium
                      physical id: 0
                      logical name: /dev/sdc
           *-usb:1
                description: Generic USB device
                product: ASUS EZ N Network Adapter
                vendor: Manufacturer Realtek
                physical id: 8
                bus info: usb@1:8
                version: 2.00
                serial: 00e04c000001
                capabilities: usb-2.00
                configuration: driver=r8712u maxpower=500mA speed=480Mbit/s
           *-usb:2
                description: USB hub
                product: USB2.0 Hub
                vendor: Genesys Logic, Inc.
                physical id: a
                bus info: usb@1:a
                version: 32.98
                capabilities: usb-2.00
                configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
              *-usb
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 4
                   bus info: usb@1:a.4
                   version: 7.03
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:febf8000-febfbfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm isa_compat_mode pci_native_mode bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: enp0s7
          version: a2
          serial: 00:26:2d:2e:25:fd
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:27 memory:febfd000-febfdfff ioport:e480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi1
          logical name: scsi2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht pci_native_mode bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:e400(size=8) ioport:e080(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d880(size=16) memory:febfc000-febfcfff
        *-disk
             description: ATA Disk
             product: ST3500418AS
             physical id: 0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: CC44
             serial: 6VMD2K71
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=88f05a58
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: fa24-b036
                size: 17GiB
                capacity: 18GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-10-08 16:26:51 filesystem=ntfs label=PQSERVICE state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: be27-4136
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-10-08 16:26:56 filesystem=ntfs label=SYSTEM RESERVED state=clean
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: 5caa7e2a-6c42-4848-993b-bcbd4b48f7b2
                size: 233GiB
                capacity: 233GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2020-10-25 19:18:40 filesystem=ntfs label=eMachines state=clean
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sda4
                size: 213GiB
                capacity: 213GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   version: 1.0
                   serial: 4589861b-b403-4322-84e8-382b1210173d
                   size: 213GiB
                   capacity: 213GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration: created=2020-10-25 22:09:03 filesystem=ext4 lastmountpoint=/ modified=2020-10-27 19:14:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2020-10-27 19:14:31 state=mounted
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DH16AASH
             vendor: ATAPI
             physical id: 1
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: SA15
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht pci_native_mode bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=16) memory:febf3000-febf3fff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:22 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fa000000-faffffff memory:c0000-dffff
     *-pci:4
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pnp00:00
          product: PnP device PNP0b00
          physical id: a
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: e
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: f
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0f03
          physical id: 11
          capabilities: pnp
          configuration: driver=i8042 aux
     *-pnp00:04
          product: PnP device PNP0c02
          physical id: 12
          capabilities: pnp
          configuration: driver=system
     *-pnp00:05
          product: PnP device PNP0c02
          physical id: 13
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device PNP0c01
          physical id: 14
          capabilities: pnp
          configuration: driver=system
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlx5404a6e02941
       serial: 54:04:a6:e0:29:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.1.141 multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by wildmanne39 on 2020-10-27
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by jwoodruff on 2020-10-28
Can you tell me how to obtain a code tag please?

---

### Post by vbdanl-yahoo on 2020-10-28
i think its the last icon in the Reply to Thread box.  Just select it and put your text in between the tags

---

### Post by CelticWarrior on 2020-10-28
It isn't.

Instructions given above should be enough. You can - also as already instructed - click the Go Advanced buuton to get the full editor. There click on "#" and past inside.

Now, regarding you problem, I'm afraid there are bad news. The Nvidia legacy driver is no longer available, be it for Linux or any supported Windows version (Windows 7 isn't and SHOULDN'T DE USED).
In Ubuntu either it works with the open-source driver or it doesn't, end of story.

---

### Post by ActionParsnip on 2020-10-28
I had a system with a GeForce 6150SE onboard. Solid GPU but the opensource driver is all you will get on it. This is named "nouveau" as shown in your output. You can see JUST the video hardware with
```

sudo lshw -C display

```
You may find a BIOS update helps as well as testing your RAM health using Memtest86 from GRUB. Bad RAM will give issues

---

### Post by jwoodruff on 2020-10-28
Can anyone suggest a suitable graphics card to substitute with my system?
Or alternatively should I use an earlier version of Ubuntu. If so, any recommendation would be appreciated.
I just want to use this for OpenOffice / email and internet browsing purposes, so doesn't have to be anything fancy.

---

### Post by ActionParsnip on 2020-10-28
[https://certification.ubuntu.com/](https://certification.ubuntu.com/)
I'd suggest a mid range Nvidia or AMD GPU personally

---

### Post by sdsurfer on 2020-11-03
Sorry for the late reply, I have Nvidias in all my machines and they can be a pain. This may or may not solve your problem, it has been a frequent winner in my environments.

First in a command line run **ubuntu-drivers devices**. Here is mine on this machine.
```

ubuntu-drivers devices

== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00002191sv00001558sd00008550bc03sc00i00
vendor   : NVIDIA Corporation
model    : TU116M [GeForce GTX 1660 Ti Mobile]
driver   : nvidia-driver-450 - distro non-free recommended
driver   : nvidia-driver-440-server - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-435 - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```

Note the "recommended." Go to Software and Updates, additional drivers, let it load. You should see all of the drivers from the command. Select the recommended radio button and let it install. Restart is probably not required but I always do anyway.

A side note, I have another thread here about "black boxes" and black window panes under 20.04 in some apps. These were not a problem in 18.04. This is application-specific, if you experience that disable hardware acceleration in those apps.

---

### Post by CelticWarrior on 2020-11-03
@sdsurfer

The problem here is with legacy hardware for which there are no proprietary drivers.

---

### Post by T6&amp;sfpER35% on 2020-11-03
> [COLOR=#000000][INDENT]Can anyone suggest a suitable graphics card to substitute with my system?
Or alternatively should I use an earlier version of Ubuntu. If so, any recommendation would be appreciated.
I just want to use this for OpenOffice / email and internet browsing purposes, so doesn't have to be anything fancy.[/INDENT]


[/COLOR]


i'm on xubuntu with theses graphics and have no problems at all...if it'll help.

```
Graphics:  Device-1: NVIDIA GT218 [GeForce 210] vendor: ASUSTeK EN210 SILENT driver: nvidia v: 340.108 bus ID: 01:00.0            Display: x11 server: X.Org 1.20.8 driver: nvidia unloaded: fbdev,modesetting,nouveau,vesa resolution: 1600x900~60Hz 
           OpenGL: renderer: GeForce 210/PCIe/SSE2 v: 3.3.0 NVIDIA 340.108 direct render: Yes 
```

also i use this driver

[ATTACH=CONFIG]287308[/ATTACH]

---

### Post by mastablasta on 2020-11-04
> **jwoodruff said:**
> Can anyone suggest a suitable graphics card to substitute with my system?
Or alternatively should I use an earlier version of Ubuntu. If so, any recommendation would be appreciated.
I just want to use this for OpenOffice / email and internet browsing purposes, so doesn't have to be anything fancy.

Nvidia GT 710 will do what you need it to do. if you can find a simliarly priced AMD card which should be AMD Radeon R7 240 you can also get that. 

they are often low profile with no fan on them. mostly these are used for watching videos and basic tasks. 

if you have a bit more money then get Nvidia GT 1030 or similarly priced Radeon from AMD which i think is Radeon RX550.

i suggest Radeon here simply because they use opensoruce drivers now and offer longer term support. i am not sure how long GT710 will still be supported, but it will fit your needs and  doesn't cost much. after nvidia support expires there is only opensource nouveau driver which again should be good enough for your needs. but does not offer same performance as closed source drivers.

edit - if card has Fermi cbhip architecture it is in legacy support, if it has newer it is not yet in legacy:
[https://nvidia.custhelp.com/app/answers/detail/a_id/4656](https://nvidia.custhelp.com/app/answers/detail/a_id/4656)

so 710 is still normally supported.

---

### Post by Yellow Pasque on 2020-11-04
You may be able to hack in the 304.xx driver with Ubuntu 18.04**.1**:
[https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic](https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic)

---

### Post by rsteinmetz70112 on 2020-11-06
The hardware is:

```
description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: NVIDIA Corporation
```

There may be tweeks to get the nouveau driver to work acceptably. 
That may be the only option other than installing a new GPU.

---

### Post by jwoodruff on 2020-11-06
Thanks to all for the assistance. I elected to purchase a new GPU and that did the trick. Able to run 20.04 and better graphics too.

---

### Post by mastablasta on 2020-11-08
what GPU did you end up buying?

---

