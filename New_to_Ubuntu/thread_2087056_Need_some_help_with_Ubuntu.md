---
title: "Need some help with Ubuntu"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by Firstimer3 on 2012-11-22
Hi everyone, I'm new to Ubuntu / Linux. Anyways, I decided I try out Ubuntu as it seems a good place to start. So I downloaded Ubuntu through "Linux Live USB Creator", and put it on my laptop. This laptop previously had Windows Vista on it, so I chose the option of replacing Windows Vista with Ubuntu. 

Anyways, on the initial 2 tries, Ubuntu wasn't loading up, it would just go to a blank screen. So I booted with "nomodeset" instead from a recommendation online. Once I got it installed, and I did a reboot, it wouldn't load into Ubuntu. So I searched around on my other computer, and someone said to replace "quiet splash" with "nomodeset" which I did. And then it seemed to load into Ubuntu just fine. 

However, here is where I'm asking for help. For some reason, my computer seems "slow" with Ubuntu. I thought it would be a bit snappier, but it just feels slow. Maybe it's my computer, but I'll post my computer specs here in just a bit. 

Also from someone that's coming from Windows, I realized that my screen felt too "large". In Windows, I could see my entire desktop and everything, and web browsers would fit within the entire screen. In Ubuntu, the web browser takes up the entire screen (except for the task bar to the left), but it still doesn't show me everything. Is there a way to make stuff "smaller"?

And one last thing. Even after booting today again, my computer seems to crash on Ubuntu the first time it loads up, but the 2nd time it puts me into the GRUB(?) screen, and from there I have to change the "quiet splash" to "nomodeset" all over again. 

Sorry guys for the long post, but I'm really new to Ubuntu, and I'm hoping you guys can help me out. Thanks! :)

P.S. Computer Specs:

Memory: 5.9 GB

Processor: Intel Core 2 Quad Q9000 @ 2.00GHz  x 4

Graphics: VESA: G94 Board - 056962b1

OS Type: 32 Bit

Disk: 308.7 GB

---

### Post by mastablasta on 2012-11-22
that graphics card is not any good information...
open terminal , copy and paste this command in 
```
lshw
```
and then copy the output and paste it here. mark the text and use code tags (the # sign) so it will line up nicer and make it easier to read.
the command will list recognised hardware.

if you have nvidia graphics card you might need to install proprietary drivers.

also making nomodeset permanent: [http://askubuntu.com/questions/131125/ubuntu-12-04-64-bit-after-installation-help](http://askubuntu.com/questions/131125/ubuntu-12-04-64-bit-after-installation-help)

---

### Post by Firstimer3 on 2012-11-22
```
description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             capabilities: logical
     *-cpu:3
          physical id: 3
          bus info: cpu@3
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             capabilities: logical
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:a000(size=4096) memory:f7f00000-fdffffff ioport:bdb00000(size=536870912)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G94 [GeForce 9800M GS]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:fd000000-fdffffff memory:c0000000-cfffffff memory:fa000000-fbffffff ioport:ac00(size=128) memory:fcf80000-fcffffff
        *-usb:0
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:dc00(size=32)
        *-usb:1
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:e000(size=32)
        *-usb:2
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e080(size=32)
        *-usb:3
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:febff400-febff7ff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:49 memory:febf8000-febfbfff
        *-pci:1
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:b0000000-b03fffff ioport:dfe00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:fe900000-fe9fffff ioport:b0400000(size=2097152)
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 01
                serial: 00:15:af:e0:00:96
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.5.0-18-generic firmware=N/A ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:fe9f0000-fe9fffff
        *-pci:3
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:c000(size=4096) memory:fe100000-fe8fffff ioport:dde00000(size=33554432)
        *-pci:4
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:3000(size=4096) memory:b0600000-b09fffff ioport:ddd00000(size=1048576)
        *-pci:5
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:b000(size=4096) memory:fe000000-fe0fffff ioport:ddc00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:24:8c:2d:10:b2
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:48 ioport:b800(size=256) memory:ddcff000-ddcfffff memory:ddce0000-ddceffff memory:fe0f0000-fe0fffff
        *-pci:6
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 ioport:4000(size=4096) memory:b0a00000-b0dfffff ioport:ddb00000(size=1048576)
        *-usb:4
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d480(size=32)
        *-usb:5
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d800(size=32)
        *-usb:6
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d880(size=32)
        *-usb:7
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:febff000-febff3ff
        *-pci:7
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:fea00000-feafffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:09:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:16 memory:feafe800-feafefff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:09:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:17 memory:feaff000-feaff0ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:09:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r592 latency=64
                resources: irq:17 memory:feaff800-feaff8ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:09:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:17 memory:feaffc00-feaffcff
        *-isa
             description: ISA bridge
             product: 82801JIB (ICH10) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801JI (ICH10 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:47 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=32) memory:febff800-febfffff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:febfec00-febfecff ioport:400(size=32)
     *-scsi:0
          physical id: 5
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9320421AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: SD14
             serial: 5TJ0EQ9M
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000e09ea
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 92a98a0b-ec45-4464-9285-3fe40858c7cb
                size: 292GiB
                capacity: 292GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-11-22 00:14:52 filesystem=ext4 lastmountpoint=/ modified=2012-11-22 11:46:42 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2012-11-22 11:46:42 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 6142MiB
                capacity: 6142MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 6142MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 6
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: BD ROM BC-5500S
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.C0
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 7
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9320421AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: SD14
             serial: 5TJ0GNN9
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=1d244217
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/saini/0622FC4022FC35F1
                version: 3.1
                serial: 6418d4fc-0ae3-a344-922e-db944ec0069b
                size: 149GiB
                capacity: 149GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-10-01 23:56:00 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                logical name: /media/saini[CODE][CODE][CODE][HTML][HTML][/HTML][/HTML]
```[/CODE][/CODE]/924EBA2F4EBA0BCB
                version: 3.1
                serial: 266fa0c5-949e-d64f-8521-d34f5bb0e988
                size: 149GiB
                capacity: 149GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2007-12-10 02:45:03 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted 
[/CODE]

I hope I did this right. I do have NVIDIA drivers. Do you mean by going to the website, and downloading them from there? Thanks again!

---

### Post by offgridguy on 2012-11-22
Just a couple of things.  If you grab your browser window and move it over a bit
it should shrink it a bit,  thats what i do.  It will usually load to that size the next 
time you use it.
          Ubuntu is faster than windows, but from my perspective , only marginally.

---

### Post by Impavidus on 2012-11-23
> **Firstimer3 said:**
> 
P.S. Computer Specs:
Memory: 5.9 GB
...
OS Type: 32 Bit
Am I missing something or is a 32 bit OS incapable of addressing this memory? Wouldn't it be better to use a 64 bit OS?

---

### Post by mastablasta on 2012-11-23
> **Firstimer3 said:**
> ```

           *-display UNCLAIMED
                description: VGA compatible controller
                product: G94 [GeForce 9800M GS]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:fd000000-fdffffff memory:c0000000-cfffffff memory:fa000000-fbffffff ioport:ac00(size=128) memory:fcf80000-fcffffff
       

```I hope I did this right. I do have NVIDIA drivers. Do you mean by going to the website, and downloading them from there? Thanks again!

yes you did it correcttly. well without drivers nothing would display :-). only by default the opensource drivers are loaded which are not always ideal. 

yah you can go download them manually and install them manually. the latest version of the drivers has some fixes. 

however you can also just use GUI to install  additional (i.e. proprietary) drivers.
there were some issues with nvidia drivers via GUI (installing via  the menu) in 12.10. before the GUI was called jockey, but the new programme is now called  ubuntu-drivers-common:
[http://www.webupd8.org/2012/07/a-new-interface-for-handling-third.html](http://www.webupd8.org/2012/07/a-new-interface-for-handling-third.html)

also you can have a look for a few tips here if you already installed drivers via GUI: [http://techhamlet.com/2012/11/install-nvidia-drivers-in-ubuntu-12-10/](http://techhamlet.com/2012/11/install-nvidia-drivers-in-ubuntu-12-10/)

if you use Ubuntu 12.04 however the jockey (GUI to install drivers) should work fine.

> **Impavidus said:**
> Am I missing something or is a 32 bit OS incapable of addressing this memory? Wouldn't it be better to use a 64 bit OS?

Ubuntu comes with PAE kernel as default. PAE kernel can address up to 64GB ram. 

however, as this is a 64bit CPU it might indeed be better to install 64bit operating system on it to unleash CPU's full potential. the decision which version (32bit of 64 bit) to use is in this case up to the user.

64bit OS is marked as AMD64 in the image file. I think because AMD was the first with 64bit CPU.

---

