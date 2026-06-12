---
title: "I have Ubuntu 6.06 LTS on my PC, can I replace it with 11.10"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by ask_ on 2011-11-09
Hello.
I have Ubuntu 6.06 and Windows XP  running on my old PC. Regretfully,the PC was a bit neglected over the years , but works fine still. I was wondering whether I can replace the 6.06 LTS with the latest 11.10. To add to my troubles , I have lost the Live CD from which I had installed 6.06 version.Also the old PC does't have an internet connection. Is there a way by which I can uninstall the 6.06 LTS without affecting the Windows XP files. The GRUB version is 0.47 . 

If the uninstall is not possible , then I am also open to another option. Can I run Ubuntu 11.10 version along with the other two OS. Hard Disk space is not an issue. As I have around 25-30 GB free on the hard disk.

Just as the Live CD was able to add Ubuntu 6.06 on Windows XP machine , can the Live CD of 11.10 add Ubuntu 11.10 to the machine. Will the GRUB 0.47 conflict with GRUB 1.99 which usually comes with the Live CD of Ubuntu 11.10.

> Note :- The old PC has 2.93 GHz CPU , 1.24 GB RAM , Intel Pentium 4 processor.
. The graphics specs of it are as follows :-
0000:00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corporation 82915G Express Chipset Family Graphics Controller (rev 04)I would also like to know whether unity desktop will run on above specs.

---

### Post by ask_ on 2011-11-09
Suppose I format the Ubuntu6.06 partition from Windows XP , then I won't be able to boot Windows XP too , since GRUB will be gone.

But will a fresh install of Ubuntu 11.10 , be able to detect the Windows XP OS.

---

### Post by mastablasta on 2011-11-09
that's exactly how you would go about to do it. just back up your important linux files if you have any on that paritition. New Grub will replace the old one on install. grub loads before any OS boots. as a last resort you can always use winxp disk and fixmbr command to repair windows MBR first and then make linux install.
 
also what are your other system specifications? if the computer is quite old you might have better luck with latest Xubuntu. or you might have to use Unity 2D.

---

### Post by robert shearer on 2011-11-09
> **ask_ said:**
> Suppose I format the Ubuntu6.06 partition from Windows XP , then I won't be able to boot Windows XP too , since GRUB will be gone.

But will a fresh install of Ubuntu 11.10 , be able to detect the Windows XP OS.

The 6.06 partition will be formatted from the live cd as part of the install process and yes a new grub will be written which will include your current xp install.

The big question though is have you the hardware resources to run 11.10 ??
Open a terminal and run 
```
sudo lshw
```

 and post the results here wrapped in code tags (simply cut and paste from the terminal then highlight and then click on the # symbol on this message boxes toolbar)

---

### Post by ask_ on 2011-11-09
Thanks for the reply.

> **mastablasta said:**
> that's exactly how you would go about to do it. just back up your important linux files if you have any on that paritition. New Grub will replace the old one on install. grub loads before any OS boots. as a last resort you can always use winxp disk and fixmbr command to repair windows MBR first and then make linux install.
  
Trouble is I don't have WinXP CD , because mine is a HP pc , it comes with 7 recovery disks and  I don't know how to repair MBR using those.

So I need to be sure of this again. Suppose  , I delete Ubuntu partition from Windows XP disk management, and use liveCD for Ubuntu 11.10 , will I be able to get back XP.

By the way , I am also ok if entire PC gets Ubuntu. The PC is quite old and there isn't any data on it as such.

> **mastablasta said:**
> 
also what are your other system specifications? if the computer is quite old you might have better luck with latest Xubuntu. or you might have to use Unity 2D.

I am game even to install Lubuntu or Xubuntu. Could you tell me how Lubuntu would affect my experience. My aim is to just browse the net or use gcc. Anyways , my PC is old surely , but I saw on Ubuntu 11.10 requirements that 1GB RAM is enough and 1GHz CPU. I have no issues with reverting to GNOME mode.

You ask for system specs,  will it do if I post the entire output I get after using lspci command? or is any more info needed.

---

### Post by ask_ on 2011-11-09
> **robert shearer said:**
> The 6.06 partition will be formatted from the live cd as part of the install process and yes a new grub will be written which will include your current xp install.

The big question though is have you the hardware resources to run 11.10 ??
Open a terminal and run 
```
sudo lshw
```

 and post the results here wrapped in code tags (simply cut and paste from the terminal then highlight and then click on the # symbol on this message boxes toolbar)

Thanks , I will do as you say , I am ok with using LUbuntu too.
I will post the hardware resources in 5-10 minutes. Please tell if Lubuntu can work on it if not Ubuntu11.10 .

---

### Post by westie457 on 2011-11-09
Hello, before installing or un-installing anything best recommendation is to test your equipment with a LiveCD to check that everything works. Unity might run in 3d-mode from the cd or it might default to 2d-mode, that is decided by the capabilities of your graphics card. When you are happy with the performance from the CD, suggest you go for an install to the 6.06 partition(s) marking them for formatting. Grub will be replaced with a newer version - Grub2 - and the XP partition will be found.

If unity does not work from the LiveCD then suggest you go for 10.04.3 LTS or Lubuntu 11.10. neither has Unity.

The LTS is for peace of mind as it is known to be stable, Lubuntu is light and very fast. On my laptop with a 1.8Ghz processor with slightly more RAM than your PC the time from pressing Enter at the log in screen to a usable Desktop is 6 seconds.

Hope this helps.

---

### Post by ask_ on 2011-11-09
> **robert shearer said:**
> The 6.06 partition will be formatted from the live cd as part of the install process and yes a new grub will be written which will include your current xp install.

The big question though is have you the hardware resources to run 11.10 ??
Open a terminal and run 
```
sudo lshw
``` and post the results here wrapped in code tags (simply cut and paste from the terminal then highlight and then click on the # symbol on this message boxes toolbar)

```

    description: Desktop Computer
    product: PN216AA-ACJ t730i
    vendor: HP Pavilion 061
    version: 04H0211RE101GROUP10
     width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop 
  *-core
       description: Motherboard
       product: Grouper
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.xx
       serial: X312345678
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3.06 (08/27/2004)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect  socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: CPU 1
          size: 2933MHz
          capacity: 3800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic  sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe  pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KB
             capacity: 16KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MB
             capacity: 1MB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal varies
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 1280MB
        *-bank:0
             description: DIMM DDR Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 915G/P/GV/GL/PL/910GL Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: 82915G/GV/910GL Express Chipset Family Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:cfe00000-cfe7ffff ioport:cc00-cc07 iomemory:d00 00000-dfffffff iomemory:cfdc0000-cfdfffff irq:10
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82915G Express Chipset Family Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 04
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:cfe80000-cfefffff
        *-multimedia
             description: Multimedia controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:cfdb8000-cfdbbfff irq:169
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:c400-c41f irq:209
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:c480-c49f irq:201
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Keyboard
                   product: USB Keykoard
                   vendor: USB
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.10
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
              *-usb:1
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: IBM Corp.
                   physical id: 2
                   bus info: usb@2:2
                   version: 2.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:c800-c81f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:c880-c89f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB Reader
                   physical id: 1
                   bus info: usb@4:1
                   logical name: scsi2
                   version: 1.00
                   serial: 9205291
                   capabilities: usb-1.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB /s
                 *-disk:0
                      description: SCSI Disk
                      product: USB SD Reader
                      vendor: Generic
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdb
                      version: 1.00
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdb
                 *-disk:1
                      description: SCSI Disk
                      product: USB CF Reader
                      vendor: Generic
                      physical id: 0.0.1
                      bus info: scsi@2:0.0.1
                      logical name: /dev/sdc
                      version: 1.01
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdc
                 *-disk:2
                      description: SCSI Disk
                      product: USB SM Reader
                      vendor: Generic
                      physical id: 0.0.2
                      bus info: scsi@2:0.0.2
                      logical name: /dev/sdd
                      version: 1.02
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdd
                 *-disk:3
                      description: SCSI Disk
                      product: USB MS Reader
                      vendor: Generic
                      physical id: 0.0.3
                      bus info: scsi@2:0.0.3
                      logical name: /dev/sde
                      version: 1.03
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sde
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:cfdb7c00-cfdb7fff irq:209
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-26-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@02:01.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:cffff800-cfffffff ioport:ec00-ec7f irq:217
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@02:02.0
                logical name: eth0
                version: 10
                serial: 00:11:2f:a6:54:ae
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=8139too d riverversion=0.9.27 duplex=half ip=10.15.116.66 link=no multicast=yes port=MII s peed=10MB/s
                resources: ioport:e800-e8ff iomemory:cffff400-cffff4ff irq:225
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: Agere Systems
                physical id: 5
                bus info: pci@02:05.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:cffff000-cffff0ff ioport:e480-e487 ioport:e0 00-e0ff irq:255
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:ffa0-ffaf irq:193
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: SONY DVD RW AW-G170A
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 1.75
                   capabilities: packet atapi cdrom removable nonmagnetic dma lb a iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdb
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix
             resources: ioport:c080-c087 ioport:c000-c003 ioport:bc00-bc07 iopor t:b880-b883 ioport:b800-b80f irq:201
           *-disk
                description: SCSI Disk
                product: WDC WD800JD-22JN
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAM91950835
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 20GB
                   capabilities: primary bootable
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 33GB
                   capabilities: primary
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 20GB
                   capabilities: primary
              *-volume:3
                   description: Linux swap / Solaris partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 1026MB
                   capabilities: primary nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             resources: ioport:400-41f irq:10


```

---

### Post by ask_ on 2011-11-09
> **westie457 said:**
> Hello, before installing or un-installing anything best recommendation is to test your equipment with a LiveCD to check that everything works. Unity might run in 3d-mode from the cd or it might default to 2d-mode, that is decided by the capabilities of your graphics card. When you are happy with the performance from the CD, suggest you go for an install to the 6.06 partition(s) marking them for formatting. Grub will be replaced with a newer version - Grub2 - and the XP partition will be found.

If unity does not work from the LiveCD then suggest you go for 10.04.3 LTS or Lubuntu 11.10. neither has Unity.

The LTS is for peace of mind as it is known to be stable, Lubuntu is light and very fast. On my laptop with a 1.8Ghz processor with slightly more RAM than your PC the time from pressing Enter at the log in screen to a usable Desktop is 6 seconds.

Hope this helps.

I am a complete novice in these matters , so I would like to know what difference does Lubuntu make from Ubuntu as such. My main aim is to use gcc (to learn basic C programming), play media files on VLC media player , browse internet , read pdfs. Will Lubuntu support this stuff , and more importantly , is my PC suitable at least for Lubuntu ? 

One more thing , I wanted  Ubuntu 11.10 because , I use mobile broadband . And I recently installed Ubuntu 11.10 on my laptop (not that old as my PC) and I was able to create the broadband connection very easily. The broadband is from an Indian company Reliance Netconnect. People have said on the net that installing it on Ubuntu 10 is very hard but on Ubuntu 11 it is not giving any issues. Will Lubuntu11.10 have similar features of Ubuntu11.10 with regards to creation of new broadband connections?

---

### Post by westie457 on 2011-11-09
> **ask_ said:**
> I am a complete novice in these matters , so I would like to know what difference does Lubuntu make from Ubuntu as such. My main aim is to use gcc (to learn basic C programming), play media files on VLC media player , browse internet , read pdfs. Will Lubuntu support this stuff , and more importantly , is my PC suitable at least for Lubuntu ? 

One more thing , I wanted  Ubuntu 11.10 because , I use mobile broadband . And I recently installed Ubuntu 11.10 on my laptop (not that old as my PC) and I was able to create the broadband connection very easily. The broadband is from an Indian company Reliance Netconnect. People have said on the net that installing it on Ubuntu 10 is very hard but on Ubuntu 11 it is not giving any issues. Will Lubuntu11.10 have similar features of Ubuntu11.10 with regards to creation of new broadband connections?

Take a look at this [sticky]("http://ubuntuforums.org/showthread.php?t=1844755&highlight=lubuntu") for most things to do with Lubuntu.

---

### Post by alco75 on 2011-11-09
> **ask_ said:**
> I am a complete novice in these matters , so I would like to know what difference does Lubuntu make from Ubuntu as such. My main aim is to use gcc (to learn basic C programming), play media files on VLC media player , browse internet , read pdfs. Will Lubuntu support this stuff , and more importantly , is my PC suitable at least for Lubuntu ? 


Lubuntu and Xubuntu have far lower system requirements than Ubuntu. Ubuntu on my Thinkpad idles at 1GB memory usage - most of your memory. Xubuntu on the other hand idles at about 0.5GB.

I'd say 1.25GB and a 3GHz CPU should be fine for Lubuntu and even Xubuntu, but it won't run Ubuntu well.

All of the things you list you'll be able to do just fine on Lubuntu or Xubuntu, probably with the out-of-the-box packages, but it's easy to install what you need. The only thing Ubuntu (i.e. Unity or Gnome shell) offers is bling, really.

---

### Post by robert shearer on 2011-11-09
Looking at the results from lshw I don't see anything that would preclude you running Ubuntu.

I have a unit with a Celeron 2.4 cpu  896 ram and an old Nvidia card that runs 11.10.
It is fine for Web-surfing and low intensity apps but doesn't multi-task well.

As has been suggested try the live cds and see if all your hardware is working before installing.
If Lubuntu works then it would be the better choice if speed and multiple apps open at the same time are important.
If slower but prettier is what you want then Ubuntu will suffice.

---

### Post by ask_ on 2011-11-09
Thanks for all the help to everyone . I will notify in this thread , if and when my old PC gets a new soul.

---

### Post by mastablasta on 2011-11-09
> **ask_ said:**
> Thanks for the reply.
 
 
Trouble is I don't have WinXP CD , because mine is a HP pc , it comes with 7 recovery disks and I don't know how to repair MBR using those.
 
So I need to be sure of this again. Suppose , I delete Ubuntu partition from Windows XP disk management, and use liveCD for Ubuntu 11.10 , will I be able to get back XP.

you can create your own rescue disk there is also rescue disk availbale at Microsoft site, though for some reason i can't find the CD ( i think it might be included in service pack as i read it). and not to worry there are also linux distributuions that can serve the purpose.... if you mess only with your Ubuntu part of disk (and dont' touch the XP) you will be fine. you can always update GRUB to show windows...
 
> 
By the way , I am also ok if entire PC gets Ubuntu. The PC is quite old and there isn't any data on it as such.
 
I am game even to install Lubuntu or Xubuntu. Could you tell me how Lubuntu would affect my experience. My aim is to just browse the net or use gcc. Anyways , my PC is old surely , but I saw on Ubuntu 11.10 requirements that 1GB RAM is enough and 1GHz CPU. I have no issues with reverting to GNOME mode.
 
You ask for system specs, will it do if I post the entire output I get after using lspci command? or is any more info needed.
 
well the only thing low seems to be the graphcis card, but since you won't be gaming... you can choose any of the options available (Kubuntu has KDE interface, Xubuntu has XFCE, and Lubuntu LXDE). they have different desktop environmnets but under the desktop environment they are the same. XFCE and LXDE are much lighter on resource than other two. 
Though i am running Kubuntu on Celeron 2.something Ghz dual core and same ram as you. but my Graphics card is a dedicated one and better than Intel.
 
well since you need it only for internet and programming i think you would benefit if the bling didn't occupy the CPU and RAM. So Xubuntu or Lubuntu might be better choices. Well if the thing works in Ubuntu out of the box it will most likely work in others as well. Xubuntu looks kind of as the old Gnome, while Lubuntu has that windows98 feel to it :-)
 
the difference is just how the windows and all on desktop are drawn and how things are handled (for example changes that user makes, what kind of GUI are there, file browsers and manager...). GNOME for exampel is known to have little GUI choice fo rusers. most advanced stuff can be done but via terminal. it is ment to simplify the use. KDE has GUI for most things, but a lot of choices are maybe not what beginner wants etc.
 
FYI Linus (the guy that "invented Linux) uses XFCE now. but you should try them out and choose the one you like.

---

### Post by ask_ on 2011-11-09
yes!!!!

I was able to install Ubuntu 11.10 itself on the PC. It is a wee bit slower than my laptop , but I am not complaining. My purpose seems to be solved. I was able to create the mobile broadband connection I was referring to. I am posting this from my old PC at this moment.

I would have tried out Lubuntu , but I already had the Ubuntu .iso file downloaded for my laptop , so installed Ubuntu .

For some weird reason , I was unable to configure my Windows XP PC for that broadband (perhaps I didn't use correct settings). But in Ubuntu 11.10 the settings for that particular broadband were already present. Just had to select that Reliance Netconnect ,that's it.

Furthermore , the Live CD very politely asked me if I wanted to erase Ubuntu 6.06 and replace it with 11.10.So there was no question of messing up on a partition. 

Thanks again to everyone of you all. :D


edit:- switched to Lubuntu 11.10 on my old PC as Ubuntu 11.10 though working was using a lot of CPU for multimedia tasks.

---

