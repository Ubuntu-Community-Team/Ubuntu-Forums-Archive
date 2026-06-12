---
title: "ubuntu not finding hp dvd1270i optical drive"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by david476 on 2011-12-26
my bios recognizes the drive but Ubuntu 10.04 can't find it. I have isolated the problem to Ubuntu or the drive itself, although I believe it to be a problem with Ubuntu. The drive was working before I installed Ubuntu. Can anyone offer a suggestion, do I need a driver?

---

### Post by meditatingfrog on 2011-12-26
> **david476 said:**
> my bios recognizes the drive but Ubuntu 10.04 can't find it. I have isolated the problem to Ubuntu or the drive itself, although I believe it to be a problem with Ubuntu. The drive was working before I installed Ubuntu. Can anyone offer a suggestion, do I need a driver?

Have you tried ```
 ls /dev/sr* 
``` ?

---

### Post by david476 on 2011-12-26
these are the results for with* and without. I wasn't sure.


ls: cannot access /dev/sr: No such file or directory

ls: cannot access /dev/sr*: No such file or directory

---

### Post by meditatingfrog on 2011-12-26
> **david476 said:**
> these are the results for with* and without. I wasn't sure.


ls: cannot access /dev/sr: No such file or directory

ls: cannot access /dev/sr*: No such file or directory

My optical drive is on /dev/sr0 , so i thought to check /dev/sr* for it, just in case it was there, but not getting mounted.  

What about ```
sudo lshw
``` ?

EDIT:  is it an ATA device?

---

### Post by david476 on 2011-12-26
It is SATA6gbs. this is what I got:

                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f8000000-f9ffffff memory:d0000000-d7ffffff memory:d8000000-dbffffff ioport:e000(size=128) memory:fa000000-fa07ffff
           *-multimedia
                description: Audio device
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:fa080000-fa083fff
        *-communication UNCLAIMED
             description: Communication controller
             product: Cougar Point HECI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:fa307000-fa30700f
        *-usb:0
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:fa306000-fa3063ff
        *-multimedia
             description: Audio device
             product: Cougar Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:fa300000-fa303fff
        *-pci:1
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17
        *-pci:2
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) ioport:dc100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: 8c:89:a5:10:45:3f
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:41 ioport:d000(size=256) memory:dc104000-dc104fff memory:dc100000-dc103fff
        *-pci:3
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:c000(size=4096) memory:fa200000-fa2fffff
           *-firewire UNCLAIMED
                description: FireWire (IEEE 1394)
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:fa200000-fa2007ff ioport:c000(size=256)
        *-pci:4
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:fa100000-fa1fffff
           *-usb
                description: USB Controller
                product: NEC Corporation
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:fa100000-fa101fff
        *-usb:1
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fa305000-fa3053ff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: Cougar Point 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f090(size=16) ioport:f080(size=16)
           *-disk
                description: ATA Disk
                product: ST31000528AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: CC3E
                serial: 6VPEL0RB
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000cbbdd
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: a626e385-5e8a-4416-b923-ea8cb08b206d
                   size: 920GiB
                   capacity: 920GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-24 01:04:16 filesystem=ext4 lastmountpoint=/&#65533;&#1889;5&#65533;&#65533;&#65533;ZkC&#65533;5&#65533;&#65533;&#65533;&#65533;&#65533;4&#65533;&#65533;&#65533;&#65533;&#1889;5&#65533;&#65533;&#65533;&#65533;5&#65533;&#65533;&#65533;` &#65533;&#65533;&#65533; modified=2011-12-04 18:04:22 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-12-26 12:29:49 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 11GiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: Cougar Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fa304000-fa3040ff ioport:f000(size=32)
        *-ide:1
             description: IDE interface
             product: Cougar Point 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f030(size=16) ioport:f020(size=16)
  *-power:0 UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-power:1 UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 2
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@1:1.3
       logical name: wlan0
       serial: c4:3d:c7:75:4a:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.39-020639-generic firmware=N/A ip=192.168.0.9 link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by meditatingfrog on 2011-12-26
What channel is the optical drive on?  ide1 or ide0?  Looks like your seagate hdd is on ide0, but it doesn't detect any other sata device.  

If it were me, at this point i'd be checking connectors or looking for another computer to try the drive on.

---

### Post by david476 on 2011-12-26
I tryed connectors and as I said, the bios recognizes it by name. it sould be on ide1 if my hard drive is on ide0

---

### Post by meditatingfrog on 2011-12-26
> **david476 said:**
> I tryed connectors and as I said, the bios recognizes it by name. it sould be on ide1 if my hard drive is on ide0

I'm not sure that i'll be able to help you.  I believe the driver is compiled into the kernel (as i don't have any drivers listed in ```
lsmod
``` for my own optical drive or even the ide controllers).  

The only thing i could recommend is trying a different kernel.  Knowing when the drive was manufactured may help anyone else that reads this thread to help though.

My apologies for not being able to do more.

---

### Post by david476 on 2011-12-26
OK. if you know anyone else who could help, please refere them to this thread. Also, do you know if there is anougther way to download the driver(s)?

---

### Post by meditatingfrog on 2011-12-27
I checked with some folks on the IRC channel #ubuntu-beginners.  If you don't get a response right away on the forum, you can head over to irc (either using an irc client like xchat/pidgin or by using [Freenode Webchat for live Ubuntu support]("http://webchat.freenode.net/?channels=ubuntu-beginners&uio=MT11bmRlZmluZWQb1").

---

