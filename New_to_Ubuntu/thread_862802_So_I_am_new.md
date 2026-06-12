---
title: "So I am new"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by dave.com on 2008-07-17
Okay, my history with Linux goes hot and cold over some years. I have installed different distros, Gentoo 2.6.19-r6 dual boot with XP was about my last it has been like 18 months since I forgot my user ID and p/w LoL and a shot at Slackware years before that which never really followed thru.

My problem is one of confusion in new kernel, new distro and I never really learned all the command-line stuff I just manage to navigate thru the system and search sort p'raps. Here's where the Ubuntu LiveCD installation has gone so far: 

> root@ubuntu:/# fdisk -lu

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4c264c25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   117226304    58613121    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d2ac042

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   409545044   204772491    7  HPFS/NTFS
/dev/sdb2       409545045   625137344   107796150    b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004868a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   604156517   302078227+  83  Linux
/dev/sdc2       612976140   625137344     6080602+   5  Extended
/dev/sdc3       604172520   612976139     4401810   83  Linux
/dev/sdc5       612976203   625137344     6080571   82  Linux swap / Solaris

Partition table entries are not in disk order

Result for mount:

> root@ubuntu:/# mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
root@ubuntu:/# 

So much for the partition table, now here is the box:

> root@ubuntu:/# sudo lshw
ubuntu                    
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=90C4D7AB-74FE-D511-8D30-2833ADAF4735
  *-core
       description: Motherboard
       product: P5LD2-VM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1303 (03/19/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          slot: LGA 775
          size: 2800MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
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
          physical id: 35
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          size: 18EHz
          capabilities: ht
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
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GeForce 8800 GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-storage
                description: Mass storage controller
                product: ITE 8211F Single Channel UDMA 133
                vendor: Integrated Technology Express, Inc.
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 11
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=pata_it821x latency=64 maxlatency=8 mingnt=8 module=pata_it821x
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@0000:01:0a.0
                logical name: eth0
                version: 10
                serial: 00:0a:cd:0c:49:b8
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.1.1.99 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST360015A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.53
                serial: 3KA1JD9Q
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4c264c25
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 642ac9c2-f70a-8c4a-83b7-56208f841e21
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-07-15 17:20:20 filesystem=ntfs label=Dead state=clean
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi4
             logical name: scsi5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: ST3320620AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@4:0.0.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 5QF2KS59
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4d2ac042
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: a685d395-0a84-8448-9615-b47bdadcd2ca
                   size: 195GiB
                   capacity: 195GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-02-10 17:14:12 filesystem=ntfs label=SATA-1A state=clean
              *-volume:1
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sdb2
                   version: FAT32
                   serial: e55f-722f
                   size: 102GiB
                   capacity: 102GiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-S223F
                vendor: TSSTcorp
                physical id: 0.1.0
                bus info: scsi@4:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: SB00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
           *-disk:1
                description: ATA Disk
                product: ST3320620AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/sdc
                version: 3.AA
                serial: 5QF2GHK2
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0004868a
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sdc1
                   logical name: /media/disk-1
                   version: 3.6
                   serial: 38198900-8c5b-4a66-b09c-c4ed2b24c2ea
                   size: 288GiB
                   capacity: 288GiB
                   capabilities: primary bootable journaled reiserfs initialized
                   configuration: filesystem=reiserfs hash=r5 mount.fstype=reiserfs mount.options=rw,nosuid,nodev,relatime state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   size: 5938MiB
                   capacity: 5938MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdc5
                      capacity: 5938MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@5:0.0.0,3
                   logical name: /dev/sdc3
                   logical name: /media/disk
                   version: 1.0
                   serial: 046f715a-568b-4a98-aabc-c9bbd78d11b0
                   size: 4298MiB
                   capacity: 4298MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-07-17 06:29:54 filesystem=ext3 modified=2008-07-17 19:43:23 mount.fstype=ext3 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2008-07-17 18:08:12 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
root@ubuntu:/# 

As you can see in the partition table Linux is installed on a 320Gb sata hdd with swap fs in its own Extended partition, /boot in its own ext3 fs Primary Partition, and / on reiserfs fs in a 3rd partition being a Primary partition. The comp is my own rig, there's no Maker stamps and the case is a generic piece of Chinese tin. Made ..in China. Pulled it all together starting from there. The table is pretty much an old Gentoo layout which happened to work for me in the past.

My confusion grew when I saw menu.lst after installation. It has completely changed from anything I dimly knew, the old Gentoo dual boot menu.lst is not required for reference I have to relearn and re-aquire the grub stuff. But first where do I start? Not kidding, where is the very beginning of this next stage? What directory path do I mount my drives? Do I need to set make.profile link, or a /usr/src/linux<string> link to /usr/src/linux? Do I need to link the System.map file to anything? Is there anything else?

Gentoo has probably changed too ..I missed the memo; now I am at LiveCD ubuntu@ubuntu command line while I want to boot Linux natively. BTW the 8.04.1 LTS Desktop LiveCD environment is a great piece of work, I am kinda looking forward to getting this up.

---

### Post by drs305 on 2008-07-17
I'm about to leave my computer, but as far as menu.lst goes, there is a great gui app called StartUp-Manager that will allow you to tweak your grub boot options. Once you have installed ubuntu via the liveCD I highly recommend you install 'startupmanager' and make any changes to the menu.lst via this app. Of course you can also play with it in liveCD.

To install:
```
sudo aptitude install startupmanager
```

To run it, System, Administration, StartUp-Manager

To learn more about it:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")


Most importantly: Welcome to Ubuntu!

---

### Post by Inxsible on 2008-07-17
> **dave.com said:**
> ....... now I am at LiveCD ubuntu@ubuntu command line while I want to boot Linux natively. BTW the 8.04.1 LTS Desktop LiveCD environment is a great piece of work, I am kinda looking forward to getting this up.First thing would be to install the OS. I am not sure why you are trying to mount the drives while in Live CD mode.

---

### Post by lisati on 2008-07-17
I'm not sure as to why the OP is using sudo when already in root mode.....

---

### Post by Inxsible on 2008-07-17
@ OP: Next time you paste code on the forum, please use the code tags. Makes the post shorter and much more readable

---

### Post by Dutch70 on 2008-07-17
You should start here...
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

also more people will probobly read your post, if you edit it and put the info part in code...just click edit, go advanced, and cut and paste it using the button that looks like this "#"

Dutch
Edit: lol, I was a 3 seconds too late.

---

### Post by LowSky on 2008-07-17
Wow, for someone who has used Linux before you really made an Ubuntu LiveCD look like quantum physics... see the button labeled _**install**_, click on that!

---

### Post by dave.com on 2008-07-17
> First thing would be to install the OS. I am not sure why you are trying to mount the drives while in Live CD mod

You have to assume I haven't installed it?

So far, I am trying to get a bootstrap into the native desktop. The menu.lst is foreign to me, and so I get grub errors booting into Linux but it's installed and everything works fine for launching Windows. To correct my bootstrapped environment for root and /boot I consider mounting the partions in the correct path. So I wanna mount 'em right in LiveCD root@ubuntu and start correcting the initial setup. With me? 

As for sudo in root, I am just following suggested command lines to the letter from reading other threads in these forums. Once I memorise something it sticks, but I do respect your expertise and community standing - I clarify what needs to be asked only. 

Thank you all for the rapid responses there's some stuff I have to look into there now. And apologies in advance when my legibilty gets bad, I have issues with writing when I am too fatigued to concentrate.

---

