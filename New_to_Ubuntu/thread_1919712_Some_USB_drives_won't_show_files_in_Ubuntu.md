---
title: "Some USB drives won't show files in Ubuntu"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by medusa569 on 2012-02-03
[SIZE=3]:confused:Greetings all....  My current problem is that I have one  external USB  Sony DVD RW that works with Ubuntu.  I have my internal CD drive doesn't seem to show files anymore. I hear the power still functioning.    I also have been trying to view contents of 3 other hard drives (IDE)  that were formerly in Windows machines.  Plugged into my USB adapter it may be identified as 4 other generic USB drives in Computer listing but I cannot see the files on any of these drives. The USB adapter shows up under mass storage devices, 1 external USB ATA disk does not. Help please! Why so difficult to see contents on any disk/drive?


medusa
[/SIZE]

---

### Post by kevdog on 2012-02-03
Please don't post using that font -- its like you are yelling -- really annoying.

Ok I don't quite understand your setup.  If you could explain it a little bit more thorougly.

If you could also post
lshw
lspci

That would be great.Its likely just a mounting/udev issue.

---

### Post by medusa569 on 2012-02-05
[FONT=Comic Sans MS][SIZE=3][COLOR=Black]Sometimes I have to use a bigger font because my eyesight is worse. It wasn't all caps but I'll try a different font.  To  answer your queries..the results of the 2 commands are below:

with a multiport USB adapter plugged in with ide disk
[/COLOR][/SIZE][/FONT]
```
 root@medusa569:/home/medusa569# lshw
medusa569                 
    description: Desktop Computer
    product: E-4600
    vendor: Gateway
    version: 4000656
    serial: 0023110178
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=80743A32-E61D-B211-8000-DC427992FC8B
  *-core
       description: Motherboard
       product: D850GB
       vendor: Intel Corporation
       physical id: 0
       version: AAA22957-306
       serial: IUGB10603910
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: GB85010A.15A.A017.P06.0102201104 (02/20/2001)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1300MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.0.7
          slot: J4K1
          size: 1300MHz
          capacity: 1300MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 8KiB
             capacity: 8KiB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: RIMM RAMBUS 400 MHz (2.5 ns)
             physical id: 0
             slot: J7J1
             size: 256MiB
             width: 16 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: RIMM RAMBUS 400 MHz (2.5 ns)
             physical id: 1
             slot: J7J2
             size: 256MiB
             width: 16 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: RIMM RAMBUS 400 MHz (2.5 ns)
             physical id: 2
             slot: J8J1
             size: 256MiB
             width: 16 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: RIMM RAMBUS 400 MHz (2.5 ns)
             physical id: 3
             slot: J8J2
             size: 256MiB
             width: 16 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82850 850 (Tehama) Chipset Host Bridge (MCH)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff
        *-pci:0
             description: PCI bridge
             product: 82850 850 (Tehama) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fc900000-fe9fffff memory:f0600000-f46fffff
           *-display
                description: VGA compatible controller
                product: NV6 [Vanta/Vanta LT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 15
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:11 memory:fd000000-fdffffff memory:f2000000-f3ffffff memory:fe9f0000-fe9fffff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fea00000-feafffff memory:f4700000-f47fffff
           *-network
                description: Ethernet interface
                product: 21x4x DEC-Tulip compatible 10/100 Ethernet
                vendor: Davicom Semiconductor, Inc.
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth0
                version: 31
                serial: 00:80:ad:71:bb:4d
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=dmfe driverversion=1.36.4 ip=192.168.0.102 latency=32 link=yes maxlatency=40 mingnt=20 multicast=yes
                resources: irq:4 ioport:d800(size=256) memory:feaffc00-feaffcff memory:fea80000-feabffff
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1
                resources: irq:9 memory:feafd000-feafdfff
           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: b.1
                bus info: pci@0000:02:0b.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1
                resources: irq:10 memory:feafe000-feafefff
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: b.2
                bus info: pci@0000:02:0b.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ehci bus_master cap_list
                configuration: driver=ehci_hcd latency=32 maxlatency=34 mingnt=16
                resources: irq:11 memory:feaff800-feaff8ff
           *-communication UNCLAIMED
                description: Communication controller
                product: HCF 56k Data/Fax Modem
                vendor: Conexant Systems, Inc.
                physical id: c
                bus info: pci@0000:02:0c.0
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: memory:feae0000-feaeffff ioport:dfe0(size=8)
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: d
                bus info: pci@0000:02:0d.0
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
                resources: irq:11 ioport:df80(size=32)
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: d.1
                bus info: pci@0000:02:0d.1
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32
                resources: irq:0 ioport:dff0(size=8)
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
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
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk:0
                description: ATA Disk
                product: QUANTUM FIREBALL
                vendor: Quantum
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: APL.
                serial: 552107834309
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00099e5c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: b1fddc85-c2d0-4824-99f7-484b2ddb4cf7
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-09 22:06:14 filesystem=ext4 lastmountpoint=/&#65533;U0&#65533;&#65533;u&#65533;H&#65533;&#65533;&#65533;&#65533;Y&#65533;P~&#65533;&#65533;"&#65533;H&#65533;&#65533;@~&#65533;&#65533;@,&#65533;&#65533;@,&#65533;&#65533;&#65533;u&#65533;h~&#65533;&#65533;"&#65533; modified=2012-01-30 18:20:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2012-02-05 10:36:41 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 854MiB
                   capacity: 854MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 854MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST320413A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 3.39
                serial: 5ED39WV8
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=baa9764d
              *-volume
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/HD #2
                   version: FAT32
                   serial: a8b2-0392
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=OS mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
           *-cdrom
                description: SCSI CD-ROM
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:5 ioport:ef40(size=32)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:efa0(size=16)
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:ef80(size=32)
root@medusa569:/home/medusa569# 

```


root@medusa569:/home/medusa569# lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
02:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
02:0b.0 USB Controller: NEC Corporation USB (rev 43)
02:0b.1 USB Controller: NEC Corporation USB (rev 43)
02:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:0c.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax Modem (rev 08)
02:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
root@medusa569:/home/medusa569#

---

### Post by Bodsda on 2012-02-05
An output of
```

sudo fdisk -l

```Whilst the usb hdd is atached may also be useful. And perhaps these as well

```

cat /etc/fstab

```
```

lsusb

```
Thanks,
Bodsda

---

### Post by medusa569 on 2012-02-05
[FONT=Comic Sans MS][SIZE=3]Again while USB adapter is attached..be advised I have 2 internal hard disks...
[/SIZE][/FONT]
[SIZE=3]fdisk -l :[/SIZE]

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099e5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2374    19060736   83  Linux
/dev/sda2            2374        2483      874497    5  Extended
/dev/sda5            2374        2483      874496   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbaa9764d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2433    19543041    c  W95 FAT32 (LBA)

[SIZE=3]
medusa569@medusa569:~$ cat /etc/fstab[/SIZE]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b1fddc85-c2d0-4824-99f7-484b2ddb4cf7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8bfd464f-0d5a-48ae-aad7-1078f760db7f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/mnt/1024Mb.swap  none  swap  sw  0 0

[SIZE=3]medusa569@medusa569:~$ lsusb[/SIZE]

Bus 005 Device 003: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 005 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c50d Logitech, Inc. Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04a9:1056 Canon, Inc. BJC-2110 Color Printer
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

hopes this helps you..

---

