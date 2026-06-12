---
title: "[SOLVED] UBUNTU 8.10 Help needed for the list of problems"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by babloo75 on 2008-11-04
Hi frenz, I am new to the linux community, so please help me out in the problems i m encountering since the time i installed this...
1. my computer works very slow... even slower than the most slowest form of windows vista i have ever seen.. sometimes it takes 5-7 minutes to boot.. and once it boots then the sound during booting appears broken... like k...k...k...k...
2. whenever i use internet by mozilla firefox, if i open one tab its fine.. but the moment 3rd or 4th tab is opened, it stops responding or responds after 20- 30 seconds. and while working on internet if i open any song or video.. thats the time ubuntu stops working at all.. the video freezes.. sounds appear broken.. at this time even force quit application doesn't work.
3. earlier i installed azureus vuze, but after installing vuze, ubuntu refused to shut down, a pop up window appeared stating update notifier is running and below that was written not responding.. later another application appears nautilus has stopped responding.. bodonga application server is active, killing the application may resolve problem....
therefore i have removed vuze from ubuntu
4. and now i m typing in this forum,,, the alphabets appear 2 seconds after i type on the keyboard...
please help me in solving these problems...

(my computer has 160 GB HD, 2GB Ram, Intel Centrino, 110 GB partition for windows and 42 GB for ubuntu) 

Please help me.................

---

### Post by RequinB4 on 2008-11-04
can you post the output of applications - accessories - terminal

```

top

```

---

### Post by babloo75 on 2008-11-05
[QUOTE=RequinB4;6108426]can you post the output of applications - accessories - terminal

```

top

```[babloo@babloo-laptop:~$ top

top - 11:49:10 up 21 min,  2 users,  load average: 0.12, 0.21, 0.25
Tasks: 112 total,   2 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.5%us,  1.0%sy,  0.0%ni, 94.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2063652k total,   578652k used,  1485000k free,    18916k buffers
Swap:  1831368k total,        0k used,  1831368k free,   237288k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 5098 root      20   0  371m  36m 8184 S  5.7  1.8   0:51.20 Xorg                                                            
 6635 babloo    20   0 78552  22m  11m R  2.4  1.1   0:00.88 gnome-terminal                                                  
 6036 babloo    20   0  198m  81m  23m S  0.7  4.1   1:15.41 firefox                                                         
 5539 babloo    20   0 24256  16m 6144 S  0.5  0.8   0:10.38 compiz.real                                                     
 6659 babloo    20   0  2416 1148  884 R  0.5  0.1   0:00.20 top                                                             
    1 root      20   0  3056 1888  564 S  0.0  0.1   0:02.44 init                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                                         
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                   
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0                                                       
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.34 kacpid                                                          
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 kacpi_notify                                                    
  132 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                          
  136 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 kseriod                                                         
  177 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                         
  178 root      20   0     0    0    0 S  0.0  0.0   0:00.06 pdflush                                                         
  179 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                         
  221 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                           
 1164 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                   
 1166 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                           
 1226 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                        
 1240 root      15  -5     0    0    0 S  0.0  0.0   0:00.22 ata/0                                                           
 1242 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                         
 1297 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                     
 1432 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                       
 1434 root      15  -5     0    0    0 S  0.0  0.0   0:00.38 scsi_eh_1                                                       
 2123 root      15  -5     0    0    0 S  0.0  0.0   0:00.20 kjournald                                                       
 2297 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.78 udevd    ]

---

### Post by babloo75 on 2008-11-05
the details mentioned above are changing every second or two... what i copied was the one at that moment... (just one program is open right now- mozilla firefox, besides terminal, and i m sure if i open media file like audio/video it will hang..)

---

### Post by mapes12 on 2008-11-05
I'm assuming the machine can dual boot into both Ubuntu and Windoze? Does windoze function OK? If it does then the problem is with your Ubuntu installation.

Is your Ubuntu OS a fresh install or an upgarde and which version are you running?

Have you been able to run Ubuntu OK previously? If you did what has changed since then e.g. have you downloaded any updates or other application packages?

Can you post the output to ```
sudo lshw 
```for us to take a look at your machines spec please.

---

### Post by babloo75 on 2008-11-06
Thanks for coming to this topic and helping me.. 
yes I have always faced problems with linux.. the story is very long and i will try to keep it short..
My windows xp installation runs very fine..
last month i heard about the existence of linux software. was quite curious about it so i installed fedora 9 along with windows xp. it ran fine till i updated fedora. then my computer used to hang.. i mean mouse freezed repeatedly so i formatted system.. reinstalled fedora with windowsxp. the same problem persisted. then again formatted HD. 
next i installed ubuntu 8.04 along with win xp. even in ubuntu 8.04 the mouse used to freeze (at that time also win xp was running fine). formatted it again and reinstalled it.. failed this time again..
next i tried mandriva.. it gave strange problems too.. mouse never froze but programs took long time to open..
and here am i now with UBUNTU 8.10.(fresh install)  there is no mouse freeze but the above mentioned problems have erupted.. i don't understand if win xp can run fine why can't linux...
Please my fren, help me in this matter.. i love linux and don't like MS windows.. but am not able to use it..

---

### Post by babloo75 on 2008-11-06
> **mapes12 said:**
> I'm assuming the machine can dual boot into both Ubuntu and Windoze? Does windoze function OK? If it does then the problem is with your Ubuntu installation.

Is your Ubuntu OS a fresh install or an upgarde and which version are you running?

Have you been able to run Ubuntu OK previously? If you did what has changed since then e.g. have you downloaded any updates or other application packages?

Can you post the output to ```
sudo lshw 
```for us to take a look at your machines spec please.

babloo@babloo-laptop:~$ sudo lshw
[sudo] password for babloo: 
babloo-laptop             
    description: Notebook
    product: 8922A18
    vendor: LENOVO
    version: 3000 C200
    serial: L3DW575
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=5A4E8601-798D-11DB-B4F7-000FB0CEEADC
  *-core
       description: Motherboard
       product: CAPELL VALLEY(NAPA) CRB
       vendor: LENOVO
       physical id: 0
       version: Not Applicable
       serial: 41W1388Z1ZC4T6C270F
       slot: PCI Express Slot J7C1
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 63ET62WW (04/30/07)
          size: 95KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T1350  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U2E1
          size: 1867MHz
          capacity: 2048MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts pni monitor est tm2 xtpr cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 2GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: M2
             size: 1GiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 02
                serial: 00:19:d2:05:e7:cc
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:ce:ea:dc
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:05:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:05:06.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:05:06.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:05:06.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 6.4
                bus info: pci@0000:05:06.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST9160821AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AL
                serial: 5MAAD50A
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=54900f6c
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 74a63cbf-c943-4349-a62c-c80b9486f82c
                   size: 34GiB
                   capacity: 34GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-19 22:09:39 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 114GiB
                   capacity: 114GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 34GiB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 39GiB
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 39GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 1788MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD/CDRW UJDA770
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.30
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:1c:10:3c:7a:a4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
babloo@babloo-laptop:~$

---

### Post by mapes12 on 2008-11-06
Your partitioning looks odd:

volume 0 - Primary NTFS partition
volume 1 - Extended partition 
logical volume 0 - inside the Extended partition
logical volume 1 - again, inside Extended partition
logical volume 2 - again, inside Extended partition but where Linux has been installed
logical volume 3 - again, inside Extended partition where the Linux Swap area is located

My understanding is that Linux should be installed on a primary partition. You have it installed on an a logical volume inside an Extended partition. This may be the problem because Extended partitions are a throw back to MS DOS. Therefore, Linux may not be able to function properly on a volume originally designed for DOS.

My solution would be to delete all partitions then restructure it with 4 partitions as follows:

volume 0 - Primary partition formatted for NTFS for Windoze
volume 1 - Primary partition formatted for Linux EXT3 file system and where the /(root) file system should be installed
volume 2 - Primary partition formatted for Linux EXT3 file system and where the /home file system should be installed
volume 3 - For the Linux Swap file system

Use a GParted Live CD to make the job easier: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

and boot your system with the Live CD.

This is how I've structured my HDD:
```

 *-disk:0
                description: ATA Disk
                product: Maxtor 6Y080L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y2D958VE
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=7f247f24
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 40823567-9a9c-453d-bd4a-d23256943a47
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-06 09:28:53 filesystem=ext3 modified=2008-11-06 11:29:52 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-11-06 11:25:05 state=mounted
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 182ad22f-1719-4cc4-9a4e-3fdf601bbee3
                   size: 58GiB
                   capacity: 58GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-20 17:52:33 filesystem=ext3 modified=2008-11-06 13:02:43 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-11-06 13:02:43 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 1
                   serial: 05a5e1c0-05a8-47b2-9145-8cefa29e722c
                   size: 3169MiB
                   capacity: 3169MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
```

I don't have Windoze on this machine. That's why I have one less partition than you would.

Hope that helps you out.

---

### Post by mapes12 on 2008-11-06
Me again.

Have a look at this excellent guide:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

:lolflag:

---

### Post by babloo75 on 2008-11-07
> **mapes12 said:**
> Me again.

Have a look at this excellent guide:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

:lolflag:

Tons and Tons of Thanks to you..
U R a GENIUS..
I have reinstalled the whole system as per the instructions given by you.. (as there were on the web site psychocats.net--- the photographic illustrations)
But i couldn't undersatand anything about the partitions terminology.. as i have little knowledge of computers.. can u plz do me a favour again.. i am posting the result of (sudo slhw) command here under.. can you plz check it again that this configuration is correct...
its here under... (Thanks once again..)

babloo@babloo-laptop:~$ sudo lshw
[sudo] password for babloo: 
babloo-laptop             
    description: Notebook
    product: 8922A18
    vendor: LENOVO
    version: 3000 C200
    serial: L3DW575
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=5A4E8601-798D-11DB-B4F7-000FB0CEEADC
  *-core
       description: Motherboard
       product: CAPELL VALLEY(NAPA) CRB
       vendor: LENOVO
       physical id: 0
       version: Not Applicable
       serial: 41W1388Z1ZC4T6C270F
       slot: PCI Express Slot J7C1
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 63ET62WW (04/30/07)
          size: 95KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T1350  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U2E1
          size: 1867MHz
          capacity: 2048MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts pni monitor est tm2 xtpr cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 2GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: M2
             size: 1GiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 02
                serial: 00:19:d2:05:e7:cc
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:ce:ea:dc
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:05:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:05:06.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:05:06.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:05:06.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 6.4
                bus info: pci@0000:05:06.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST9160821AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AL
                serial: 5MAAD50A
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=54900f6c
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 68f7d146-5c32-5c44-927e-6e16819a815d
                   size: 57GiB
                   capacity: 57GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-11-07 06:26:59 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 91GiB
                   capacity: 91GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 31GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 57GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 2557MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD/CDRW UJDA770
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.30
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:4a:91:b7:ed:bb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
babloo@babloo-laptop:~$

---

### Post by starcannon on 2008-11-07
A shorter and easier method for displaying and reading your partition list would be to use:
```
sudo fdisk -l
```

lshw is great but a little more info than needed ;)

Hows the machine running now? Is it responsive and stable?

GL and have fun.

---

### Post by mapes12 on 2008-11-07
> But i couldn't undersatand anything about the partitions terminology.. as i have little knowledge of computers.. 

Does this mean you did not do anything about changing your partitions? Because in looking down your lshw output the same configuration is in place that you posted before.

Anyway, now that you have reinstalled everything does Ubuntu run without the problems you experienced previously?

---

### Post by babloo75 on 2008-11-08
> **mapes12 said:**
> Does this mean you did not do anything about changing your partitions? Because in looking down your lshw output the same configuration is in place that you posted before.

Anyway, now that you have reinstalled everything does Ubuntu run without the problems you experienced previously?

Yes the problems have been solved after reinstallation of windows and ubuntu.. i followed the pictorial instructions given on website psychocats.net

---

### Post by babloo75 on 2008-11-08
> **starcannon said:**
> A shorter and easier method for displaying and reading your partition list would be to use:
```
sudo fdisk -l
```

lshw is great but a little more info than needed ;)

Hows the machine running now? Is it responsive and stable?

GL and have fun.

The machine is running ok.. but has hanged twice since yesterday..otherwise old problems are not emerging as of now.. 
but as stated by Mapes12- the odd partitions on my disk still remain.. (but frankly speaking its out of my scope/skills to correct that odd order)
 here is the output for sudo fdisk -l

babloo@babloo-laptop:~$ sudo fdisk -l
[sudo] password for babloo: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54900f6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7451    59850126    7  HPFS/NTFS
/dev/sda2            7452       19456    96430162+   f  W95 Ext'd (LBA)
/dev/sda5           15299       19456    33399103+   7  HPFS/NTFS
/dev/sda6            7452       14972    60412369+  83  Linux
/dev/sda7           14973       15298     2618563+  82  Linux swap / Solaris

Partition table entries are not in disk order
babloo@babloo-laptop:~$ 

as i see the partition table entries are not in disk order.. what does it mean and whats the way to put it in order

(thanks for help and support)

---

### Post by babloo75 on 2008-11-08
> **mapes12 said:**
> Does this mean you did not do anything about changing your partitions? Because in looking down your lshw output the same configuration is in place that you posted before.

Anyway, now that you have reinstalled everything does Ubuntu run without the problems you experienced previously?



Hello Mapes12, how r u.
U r a gr8 guide for the linux community.. and i must thank you for the same.. I have a request to you.-- can you plz post pictorial illustrations of 'How to install ubuntu/ Linux on a computer which already has windows xp installed on it.' 
That will be a gr8 addition to the community service u already r doing to us.. as you remember u guided me to the website psychocats.net and i exactly followed the pictorial illustrations for installing ubuntu on my computer, but later on when u checked the configuration of my computer, it was still wrong as far as partitions on the hard disk were considered.
So i request ur good self to please post a pictorial guide of the same on the internet so that millions are benefitted from ur expert comments and experience.
Thanks in advance

---

