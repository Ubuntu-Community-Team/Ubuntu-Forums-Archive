---
title: "[SOLVED] Processes don't stop when Firefox closes."
date: 2008-08-28
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-08-28
At least three times in the last week on my own computer I've closed Firefox and had processes keep running. Most recently it was the Xubuntu "handbook" pdf running in Adobe. 

Another time it was a Youtube video that froze on playback. I don't recall what the first was (I'm thinking a video in Totem). But each time I can fix it just by going to System Monitor (gui) and choosing to "kill" the process.

I notice this because I have "computertemp" in my panel and I watch it! I can see if something is running just by looking at the temp! (it's not overheating but I can tell if something is running)

Something that may or may not have anything to do with this is that I recently resized nearly all partitions on my machine and had to synch the UUID between blkid, initramfs, fstab, etc. (All is working well there now as far as I can tell, swap is swappy, usplash is splashy,:))

Something else I should mention is that while searching for a Vista fix for a friends box I clicked on a link that started running some auto-launch spyware search crap that wouldn't let me even close Firefox so I had to "kill-all" and restart. I did report it as a "dangerous site". But that was a few weeks ago.

Maybe I should also say that there is no internet or hard drive activity when this happens.

Can't think of anything else to add.

---

### Post by Crafty Kisses on 2008-08-28
I've had this happen to me a couple of times, when you close FireFox, you might want to try this, go into Terminal, and type:```
top
```
See if you see FireFox in there, it probably will be, but it's another way of looking. I also would like to know your system specs, I remember my friend had 1GB of RAM in Ubuntu and the same issue was happening, I put another stick of RAM in his computer and it was fine.

You might also want to check your error logs in FireFox, see if you can see anything in there that's out of the ordinary.

---

### Post by nicedude on 2008-08-28
And I also would not worry about the pop-up spyware search crap since that stuff is all targeted at Windows users and even if it is one of the ultra crappy ones that tries to install something it will be trying to install Windows based spyware and wont effect your Ubuntu at all.

---

### Post by Crafty Kisses on 2008-08-28
Yeah all that stuff, especially on a Vista website, you don't even have to worry about it.

---

### Post by kansasnoob on 2008-08-28
> **Codename said:**
> I've had this happen to me a couple of times, when you close FireFox, you might want to try this, go into Terminal, and type:```
top
```
See if you see FireFox in there, it probably will be, but it's another way of looking. I also would like to know your system specs, I remember my friend had 1GB of RAM in Ubuntu and the same issue was happening, I put another stick of RAM in his computer and it was fine.

You might also want to check your error logs in FireFox, see if you can see anything in there that's out of the ordinary.

This is huge!

> lance@lance-desktop:~$ sudo lshw
[sudo] password for lance: 
lance-desktop             
    description: Desktop Computer
    product: ID-PCM7E PC2500
    vendor: IDOT
    version: 1.x
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: ID-PCM7E PC2500
       vendor: IDOT
       physical id: 0
       version: 1.x
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (09/26/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: VIA Esther processor 1500MHz
          vendor: CentaurHauls
          physical id: 4
          bus info: cpu@0
          version: 6.10.9
          slot: Socket 370
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx up pni rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1 DISABLED
             description: L2 cache
             physical id: 9
             slot: External Cache
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
     *-pci:0
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: UniChrome Pro IGP
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=64 mingnt=2
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=64 module=sata_via
           *-cdrom
                description: DVD-RAM writer
                product: DVDRW LH-20A1S
                vendor: LITE-ON
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 9L08
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi2
             logical name: scsi3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64 module=pata_via
           *-disk
                description: ATA Disk
                product: WDC WD800JB-00JJ
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCAM9V620494
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=63056305
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 38c5aa95-12f1-8349-8b57-22b0e73dfec3
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-04-28 02:15:43 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 45GiB
                   capacity: 45GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 23GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1890MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 19GiB
           *-cdrom
                description: DVD reader
                product: DVD-ROM DDU1615
                vendor: SONY
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: GYS5
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:1b:b9:6d:d3:7a
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=75.27.226.60 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
lance@lance-desktop:~$ 



---

### Post by Crafty Kisses on 2008-08-28
Yeah, next time use the Code tags. 

Try this, kill FireFox, then check if FireFox is still running by using the following command: ```
ps -ef grep firefox
``` If it is still there, you can use:
```
sudo kill -9 24213
```
I'm pretty sure that's the process number, but that should kill it.

---

### Post by kansasnoob on 2008-08-28
I know how to kill the process. I'd just like to stop it from happening.

---

### Post by kansasnoob on 2008-08-28
Ah, I did find a problem! I still have parts and pieces of Flash 9 installed even though I'm using Flash 10.

I'll clean up and see if that helps, but it's infrequent anyway!

I'll mark this solved for now and repost later if necessary.

---

