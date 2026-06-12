---
title: "Slave Drive not recognized."
date: 2008-08-04
forum: New to Ubuntu
---

### Post by hbah427 on 2008-08-04
k so I am running Gutsy Gibbon after my Winblows HDD corrupted itself.
I used a slave drive at the time, which had most (if not all) of my media on it.
How would I Go about setting up my slave drive WITHOUT using gParted to format it?
Any help is....well...helpful!
Thanks in advance!
-hbah427
[Www.YouTube.com/users/hbah427](Www.YouTube.com/users/hbah427)

---

### Post by ingeva on 2008-08-04
> **hbah427 said:**
> k so I am running Gutsy Gibbon after my Winblows HDD corrupted itself.
I used a slave drive at the time, which had most (if not all) of my media on it.
How would I Go about setting up my slave drive WITHOUT using gParted to format it?
Any help is....well...helpful!
Thanks in advance!
-hbah427
[Www.YouTube.com/users/hbah427]("http://Www.YouTube.com/users/hbah427")

You probably only need to connect the disk. If the volume shows up on your screen, just double-click the icon and you see the files. This, of course, depends on whether the file system on it is compatible. It probably is.

If the filesystem is corrupt on it, that's another matter but let's take one problem at a time.

---

### Post by hbah427 on 2008-08-04
> **ingeva said:**
> You probably only need to connect the disk. If the volume shows up on your screen, just double-click the icon and you see the files. This, of course, depends on whether the file system on it is compatible. It probably is.

If the filesystem is corrupt on it, that's another matter but let's take one problem at a time.

Thank you
But linux doesn't recognize the disk for some odd reason...
Maybe it's because Win XP was installed on it before I got another computer..
Basically I had one computer running XP
It crashed (motherboard problems) and I used my brothers old xp with my old HDD as a slave so I wouldn't have to transfer stuff.
The new hdd crashed while partitioning for a Hackintosh
The old one is still intact.
For some reason I can't boot from the other HDD on my new pc but I still can on the old one which restarts every 10 seconds.

Now I'm just trying I transfer my documents and settings folder to my Linux.

---

### Post by phidia on 2008-08-04
What type of drive are you asking about (the drive that isn't being recognized)? If it's an ATA/IDE drive, which would have big flat ribbon cable connections, and the drive was set to single/master in it's previous spot you can't just throw it in another computer without changing the jumpers. 
Anyway is this an ATA/IDE drive and if so check your jumper settings.

OK I re-read and saw you mentioned the old drive set as slave-you also mentioned something about the macintosh FS
which is hfsplus. Did you complete partitioning of that filesystem? Linux doesn't write to hfsplus. 

At this point you may want to be sure of all your jumper settings run a livecd and then check your hardware.
> sudo fdisk -lu > lshw

---

### Post by ingeva on 2008-08-04
> **phidia said:**
> and the drive was set to single/master in it's previous spot you can't just throw it in another computer without changing the jumpers. 
Anyway is this an ATA/IDE drive and if so check your jumper settings.
...
At this point you may want to be sure of all your jumper settings run a livecd and then check your hardware.

Very good points. hba427, you should check this. The hardware must be right first. :)

---

### Post by hbah427 on 2008-08-04
> **phidia said:**
> What type of drive are you asking about (the drive that isn't being recognized)? If it's an ATA/IDE drive, which would have big flat ribbon cable connections, and the drive was set to single/master in it's previous spot you can't just throw it in another computer without changing the jumpers. 
Anyway is this an ATA/IDE drive and if so check your jumper settings.

OK I re-read and saw you mentioned the old drive set as slave-you also mentioned something about the macintosh FS
which is hfsplus. Did you complete partitioning of that filesystem? Linux doesn't write to hfsplus. 

At this point you may want to be sure of all your jumper settings run a livecd and then check your hardware.

sorry, i didn't give enough info about the Hackintosh

I never got to the installation point of OSX
the old HDD crashed while Windows was partitioning it.

there is no Macintosh anything (well, maybe iTunes ;) )

its an NTFS file system, and  ubuntu doesn't recognize it.

---

### Post by hbah427 on 2008-08-04
oh and that was the first thing i did (check the jumpers) everything should work (but it doesnt) 
the jumper is set to CS (seagate, for some reason, doesnt provide a slave only jumper setting)
plus everything is plugged in correctly (and firmly)

ive tried everything

i have no idea why Linux

---

### Post by hbah427 on 2008-08-04
> **phidia said:**
> What type of drive are you asking about (the drive that isn't being recognized)? If it's an ATA/IDE drive, which would have big flat ribbon cable connections, and the drive was set to single/master in it's previous spot you can't just throw it in another computer without changing the jumpers. 
Anyway is this an ATA/IDE drive and if so check your jumper settings.

OK I re-read and saw you mentioned the old drive set as slave-you also mentioned something about the macintosh FS
which is hfsplus. Did you complete partitioning of that filesystem? Linux doesn't write to hfsplus. 

At this point you may want to be sure of all your jumper settings run a livecd and then check your hardware.

when i ran fdisk -l using root terminal i got:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf31cf31c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150288074    75144006   83  Linux
/dev/sda2       150288075   156296384     3004155    5  Extended
/dev/sda5       150288138   156296384     3004123+  82  Linux swap / Solaris

when i ran lshw i got this info (hard drive info in bold)
harlans-computer          
    description: Computer
    product: DF214A-ABA S4100NX NA210
    vendor: Compaq Presario 061
    version: 0n41411RE101GLEND10
    serial: CNC3250TFX
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=C0D191DF-A8A2-D711-83FA-FFDB012E07DD
  *-core
       description: Motherboard
       product: Glendale motherboard
       vendor: TriGem Computer Inc.
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          physical id: 0
          version: 3.24 (10/14/2003)
          size: 108KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: WMT478/NWD
          size: 2500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 8KB
             capacity: 16KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 128KB
             capacity: 512KB
             capabilities: burst internal write-back
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 128KB
          capacity: 512KB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: J5G3
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             physical id: 1
             slot: J5G2
             size: 512MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:40:2b:66:ed:e0
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
           *-communication UNCLAIMED
                description: Communication controller
                product: LT WinModem
                vendor: Agere Systems
                physical id: a
                bus info: pci@0000:02:0a.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=14 mingnt=252
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           [B]*-disk
                description: SCSI Disk
                product: WDC WD800BB-00CA
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 17.0
                serial: WD-WMA8E2005338
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 71GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2933MB
                   capacity: 2933MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2933MB
                      capabilities: nofs[/B]
           *-cdrom:0
                description: DVD writer
                product: DVDRRW GWA-4083B
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.09
                serial: [HL-DT-STDVDRRW GWA-4083B1.0904/07/30
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
           *-cdrom:1
                description: DVD reader
                product: COMBO LTC-48161H
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: KPH9
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:a3:d5:ee
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2870 driverversion=1.45+Belkin International, Inc., ip=**CENSORED** link=yes multicast=yes wireless=IEEE 802.11g

nowhere dows linux even recognize my slave drive. :(

---

### Post by raptor2552 on 2008-08-04
Is the slave disk shown in your bios setup? That will at least confirm it's being seen.

---

### Post by hbah427 on 2008-08-04
I am an idiot.
It does not show up in my BIOS
Ive tried with slave drives and master (with the jumpers set to cable select)
Bios doesn't recognize it...
Very bad.
I have about 80GB of files on there...
It gives me two rapid clicks, pauses, then does it again...
It is NOT the click of death though (I analyzed the noise)
Is there any way to get it working or at least transfer the files?

---

### Post by ingeva on 2008-08-05
> **hbah427 said:**
> I am an idiot.
It does not show up in my BIOS


First: No you are not. You are here, right? :)
Besides, I just thought of that myself, and I'm NOT an idiot. :)

Try this:
Disconnect the same disk on the controller, and strap your slave drive as master. Then check if it's visible from the BIOS setup. If it is, install the old master again and then set the old slave back to slave. You might also try to do the opposite; change roles for the two disks just so you can see if both come up in the BIOS.

I suspect that your strapping for the slave drive may be wrong. On some disks it's easy to make a mistake. If necessary experiment a little with the settings.

I know that time flies for you, but try this and maybe you can fix it within your deadline.

---

### Post by hbah427 on 2008-08-05
> **ingeva said:**
> First: No you are not. You are here, right? :)
Besides, I just thought of that myself, and I'm NOT an idiot. :)

Try this:
Disconnect the same disk on the controller, and strap your slave drive as master. Then check if it's visible from the BIOS setup. If it is, install the old master again and then set the old slave back to slave. You might also try to do the opposite; change roles for the two disks just so you can see if both come up in the BIOS.

I suspect that your strapping for the slave drive may be wrong. On some disks it's easy to make a mistake. If necessary experiment a little with the settings.

I know that time flies for you, but try this and maybe you can fix it within your deadline.

1. thank you! you have been one of the biggest helps.
2. my mobo *for some reason* will not boot from my HDD
idk why
it gives me this random error message that says that the monitor cant display that video mode (and i tried with another monitor, it didnt show up.)
i tried with master but that didnt show up as well :(
im guessing that my HDD is shot...
also, are "clean rooms" just a myth to try to sell data recovery services or are they real...?

BTW my slave drive didnt show up in the BIOS when i was booting from my old HDD (XP) Yet it still worked...
also, i re-checked my jumper settings...nothing wrong.
also i have a very good knowledge of Windows and the Computer base, i came here for linux support, becuase i'm not too familiar with it but there is still absolutely no way i am going back to windows [except in virtualbox for ipod touch syncing {the reason i needed to work my slave drive}])

wow i have never used more than 2 types of parentheses at one time before ;)

also, I am 13 and on Summer break so i have at the very least a 2-week deadline, so dont worry about time-consuming things ;)

---

### Post by ingeva on 2008-08-05
> **hbah427 said:**
> 1. thank you! you have been one of the biggest helps.
2. my mobo *for some reason* will not boot from my HDD

mobo????

> **hbah427 said:**
> 
it gives me this random error message that says that the monitor cant display that video mode (and i tried with another monitor, it didnt show up.)

Your video settings may be out of range for that monitor.

> **hbah427 said:**
> 
i tried with master but that didnt show up as well :(
im guessing that my HDD is shot...
also, are "clean rooms" just a myth to try to sell data recovery services or are they real...?

Haven't heard the expression "clean rooms" but I know about disk salvage companies and they are not only very real, but they are also doing very good work. At least one of them, IBAS here in Norway, which is quite famous.

> **hbah427 said:**
> BTW my slave drive didnt show up in the BIOS when i was booting from my old HDD (XP) Yet it still worked...

Windows from 2000 and up actually don't use the BIOS to detect the disks. They have replaced with their own software because BIOS would interrupt OS operations. I have experienced this before.

> **hbah427 said:**
> also i have a very good knowledge of Windows and the Computer base, i came here for linux support, becuase i'm not too familiar with it but there is still absolutely no way i am going back to windows [except in virtualbox for ipod touch syncing {the reason i needed to work my slave drive}])

wow i have never used more than 2 types of parentheses at one time before ;)

also, I am 13 and on Summer break so i have at the very least a 2-week deadline, so dont worry about time-consuming things ;)

I'm 60 and I admire your knowledge and everything I've seen from you so far. Don't give up on your disk, I think you can find a solution. Try it in another computer, perhaps, if you can borrow one?

---

### Post by cariboo on 2008-08-05
Have you tried setting your slave drive as a master and connecting it to the cdrom cable. If this works, just leave it hooked up long enough to transfer the files and then you can hook your cdrom drive up again.

Jim

---

### Post by hbah427 on 2008-08-05
> **cariboo907 said:**
> Have you tried setting your slave drive as a master and connecting it to the cdrom cable. If this works, just leave it hooked up long enough to transfer the files and then you can hook your cdrom drive up again.

Jim

Wow. I have not ever thought of that...
VERY good idea!
I just realized it but cdrom drives are pretty must just hdds with a removable disk...
Hmm that might work!!

[EDIT]: it didnt.
i got the same clicking
and nothing worked right...

---

### Post by raptor2552 on 2008-08-05
You're sure the jumpers are correct and the cable isn't reversed? I believe it makes a difference which plug goes to which drive and the cable should be marked something like disk 0 or disk 1. Note that I've switched to SATA a long time ago to eliminate these troubles.

Do you have 2 ide channels, set the jumpers on each drive to be master then put one drive on ide0 as master, the other on ide1 as master. Of course this means you'll have to share the channel with a slave optical device.

Edit: Oops; posted this with noticing the second page of replies... Sorry, didn't mean to step one anyones toes.

---

