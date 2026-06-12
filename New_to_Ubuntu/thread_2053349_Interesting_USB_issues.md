---
title: "Interesting USB issues"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by Darth Matthias on 2012-09-05
To keep it short and simple:
I have a Ralink RT2070 network adapter that works just fine, I didn't compile drivers for it. But, as soon as I plug in my USB webcam, I loose my connection, and the network card refuses to operate at all. I then am forced to unplug said camera and restart the computer so that I can re connect to the internet.

---

### Post by Darth Matthias on 2012-09-06
I am not sure how to post my system info. I am looking it up right now....

---

### Post by Darth Matthias on 2012-09-06
I am still looking for the info on the camera.

System Info:

fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 49926 MHz (0.0 ns) [empty]
             physical id: 0
             slot: A0
             width: 64 bits
             clock: 2681MHz (0.4ns)
        *-bank:1
             description: DIMM 49926 MHz (0.0 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 2681MHz (0.4ns)
        *-bank:2
             description: DIMM 49926 MHz (0.0 ns)
             physical id: 2
             slot: A2
             size: 2GiB
             width: 64 bits
             clock: 2681MHz (0.4ns)
        *-bank:3
             description: DIMM 49926 MHz (0.0 ns)
             physical id: 3
             slot: A3
             size: 2GiB
             width: 64 bits
             clock: 2681MHz (0.4ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fdf00000-fdffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV710 [Radeon HD 4350]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:44 memory:d0000000-dfffffff memory:fdfe0000-fdfeffff ioport:ee00(size=256) memory:fdf00000-fdf1ffff
           *-multimedia
                description: Audio device
                product: RV710/730 HDMI Audio [Radeon HD 4000 series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:43 memory:fdffc000-fdffffff
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fde00000-fdefffff ioport:fdb00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: 6c:f0:49:16:b7:65
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdbf8000-fdbfbfff memory:fdb00000-fdb1ffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:22 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f3ff
           *-disk:0
                description: ATA Disk
                product: WDC WD800JD-75MS
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WMAM9FX07162
                size: 74GiB (79GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000eabce
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: 0ed86903-5392-4090-a9dd-78a328975144
                   size: 1952MiB
                   capacity: 1952MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-09-02 19:54:26 filesystem=ext4 lastmountpoint=/boot modified=2012-09-05 12:51:25 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered mounted=2012-09-05 12:11:44 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 72GiB
                   capacity: 72GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 72GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
           *-disk:1
                description: ATA Disk
                product: SAMSUNG HD103UJ
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 1AA0
                serial: S13PJ90SB21315
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00066893
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1
                   serial: b542052e-4cbd-418d-953f-b301dac9e94b
                   size: 7812MiB
                   capacity: 7812MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   size: 923GiB
                   capacity: 923GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /home
                      capacity: 923GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe02e000-fe02efff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe02d000-fe02dfff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fe02c000-fe02c0ff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02b000-fe02bfff
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02a000-fe02afff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:19 memory:fe029000-fe0290ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=32
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
           *-cdrom:0
                description: DVD-RAM writer
                product: CD/DVDW SH-S182D
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/sr0
                version: SB04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD-RAM writer
                product: DVD RW DRU-840A
                vendor: SONY
                physical id: 0.1.0
                bus info: scsi@4:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr1
                version: SS01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:fe024000-fe027fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:c000(size=4096) memory:fdd00000-fddfffff memory:fdc00000-fdcfffff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe028000-fe028fff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@1:6
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:mac
           *-volume:0
                description: Apple partition map
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdc1
                capacity: 31KiB
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@6:0.0.0,2
                logical name: /dev/sdc2
                logical name: /media/externalhdd
                version: 3.1
                serial: 1996-68db
                size: 465GiB
                capacity: 465GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2012-06-29 13:08:01 filesystem=ntfs label=externalhdd mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:2
                description: Apple Free
                physical id: 3
                bus info: scsi@6:0.0.0,3
                logical name: /dev/sdc3
                capacity: 8KiB
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: c8:3a:35:c7:2a:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-30-generic firmware=0.29 ip=10.0.0.6 link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by shreepads on 2012-09-06
Any errors in dmesg/ syslog when you plugin the USB device?

---

### Post by Darth Matthias on 2012-09-06
I don't know. I plug in the device and I loose access to my External HDD and my USB network adapter. How would I check?

---

### Post by anewguy on 2012-09-06
Reboot your PC with just the wireless adapter.  Now plug in your USB web cam.  Next, using the file explorer, navigate to /var/log.  Look there for the sys log - something like Syslog-0 (I'm not on Ubuntu right now so I don't remember the exact name).  Open that file in an editor such as gedit, scroll to the end, then look at the last 30 lines or so - somewhere in there it should show it detected your web cam.  Check for error messages at this point.

Another possibility, depending on the PC, is that the one set of USB ports, particularly such things as front of case ports, are connected internally in such a manner that when you have a device active on those ports it may disable another set of "built-in" ports.  I haven't seen this in quite a long time now, but I suppose it's still possible there are PC's still out there that do it.  It's been so long I don't remember the exact details now, but I believe it had something to do with the 2 controllers being mapped the same in the hardware.

---

### Post by Epodx64 on 2012-09-07
Is your wireless a USB card? I'm confused maybe im off base here but if you have a USB network card, a USB HDD, and USB Webcam all plugged into the same "set" of USB connectors it will disperse the bandwidth between all three evenly so instead of 3GB/s you'd be getting 1GB/s which could be causing the errors simply because the systems not getting the information fast enough.

---

### Post by NikTh on 2012-09-07
Hello , 

You can see whats going on , with dmesg . 

When you plug the usb camera , and the problem occurs  , then open a terminal and 

```
dmesg >> dmesg.txt
```Attach the dmesg.txt file here , or open it and copy-paste the results here 
BUT 
If you paste the results here : 
[SIZE=2]**put the results  between the brackets ****[SIZE=3][noparse]```
HERE
```[/noparse][/SIZE]  so can be readable.** [/SIZE]
Personally cannot read anything from your 3rd post. 

Thanks

---

### Post by anewguy on 2012-09-07
Usually it's best using tail with dmesg so you don't see the entire huge log file.  That was the only reason I suggested using an editor, looking back from the to see any errors - some times even experienced people start to drift when looking through the entire log.  For someone new or relatively new, I always like to try the last 30 lines or so of the file - saves a lot of looking.  ;)

---

### Post by Darth Matthias on 2012-09-14
Well, I plugged the camera into another computer and it turns out that the camera is actually broken. I have had this camera for years in a box and couldn't remember why I wasn't using it. That you for all your help.

---

