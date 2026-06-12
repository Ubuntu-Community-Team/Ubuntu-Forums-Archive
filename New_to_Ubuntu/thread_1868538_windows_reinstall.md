---
title: "windows reinstall"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by Lsh36 on 2011-10-24
I need to reinstall windows on my computer and want to leave ubuntu on there also, my system is not able to do the virtual windows.

---

### Post by sanderd17 on 2011-10-24
see this: [https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

---

### Post by Elfy on 2011-10-24
Is the ubuntu install a dual boot or a wubi install.

---

### Post by sanderd17 on 2011-10-24
@forestpiskie: good point, my link only works for non-wubi installations.

---

### Post by JayKay3OOO on 2011-10-24
First backup all of your files because I've chosen the idiot proof method (no offence, but you were quite vague)

1) I would wipe out Linux and re-install windows using the Windows disk if you have it. (got it? Great! Skip to 4)

2) If you don't then most computers have a system restore key (check your computers manual) something like F8 or F10 or F5 that you press during the early start stages of the computer. This will activate the an app that will restore your computer to factory settings. It does this by having a spare partition on the disk that contains factory data. However, you may have destroyed this partition when you put Linux on there and if you did then this won't work.

3) Lastly, if your machine is a factory one then you probably had to make system restore disks. When you put these in at boot they should restore windows to the point where you made the disks.

If you don't have a Windows disk and the system restore option does not work via hard drive or disks then you are screwed as there is no way to pull windows in by magic.

4)If you managed re-install windows using the disk or system restore options then Linux is gone. 

You can now install Linux via Wubi that installs it inside windows and adds and un-install option within windows. This is easiest if you have low tech level. Saves faffing with separate partitions.

Wubi can be found by opening the Ubuntu .iso disk image file using an application such as 7 Zip. Open it and follow the instructions.

5) If everything worked then you can now select between Ubuntu and Windows at boot.

---

### Post by Lsh36 on 2011-10-27
Thanks for all the replies, sorry that I am an idiot

---

### Post by Elfy on 2011-10-27
You're not an idiot - there are no idiotic questions - a bit more detail was all that was needed :)

Do you still need help?

Have a look at this - but don't on the other hand be put off :)
[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

---

### Post by Lsh36 on 2012-02-08
Yes, I still need help.  I don't know what type of information is needed, I don't know much about this, I didn't install it, someone else did.
This is what I have under Disk Utility:

Drive

Firmware:V320A6AE
Location: P1 of PATA Host Adapter
Write Cache:Enabled
Partitioning: Master Boot
Device: /dev/sda
Connection: ATA

Volumes

Usage: Filesystem
Partition Type: Linux(0x83)
Partition Flags: Bootable
Type: Ext 4 (version 1.0)
Device /dev/sda1
Mount Point: Mounted at /

I have clicked on unmount and it didn't work.
I have clicked on format and got the following error:
   One or more partitions are busy on /dev/sda

I have two drives on this computer and they seem to be set up identical with the exception of the device on the second HD it is /dev/sdb.
This was supposed to be set up with Windows on one drive and linux on the other and I cannot get in contact with the individual that set it up to get it fixed. I just want to go back to windows so I can use my printer again.
Here is some more information about my computer, since I don't know what is needed to solve this problem.
```


    description: Desktop Computer
    product: MS-6743
    vendor: MICRO-STAR INTL, CO.,LTD.
    version: Ver1.1A
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: MS-6743
       vendor: MICRO-STAR INTL, CO.,LTD.
       physical id: 0
       version: Ver1.1A
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/13/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: Socket 478
          size: 2666MHz
          capacity: 3066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             physical id: 0
             slot: A0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             physical id: 1
             slot: A1
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             physical id: 2
             slot: A2
             size: 256MiB
             width: 64 bits
        *-bank:3
             description: DIMM SDRAM Synchronous
             physical id: 3
             slot: A3
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e0000000-efffffff(prefetchable)
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff(prefetchable) memory:f8100000-f817ffff ioport:c000(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:b000(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b400(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:b800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:bc00(size=32)
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f8180000-f81803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:a000(size=4096) memory:f8000000-f80fffff
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 02
                serial: 00:11:09:02:23:58
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:20 memory:f8010000-f8010fff ioport:a000(size=64)
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant Systems, Inc.
                physical id: c
                bus info: pci@0000:01:0c.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: memory:f8000000-f800ffff ioport:a400(size=8)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
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
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:40000000-400003ff
           *-disk:0
                description: ATA Disk
                product: HDS722580VLAT20
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: V32O
                serial: VN42BECBE2RX7D
                size: 57GiB (61GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009cfcf
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 16155d54-df09-4c52-ae65-3494174297fb
                   size: 54GiB
                   capacity: 54GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-09-28 14:15:06 filesystem=ext4 lastmountpoint=/^(&#65533;b&#65533;#&#65533;&#65533;&#65533;&#65533;&#65533;OF&#65533;&#65533;1&#65533;&#65533;>&#65533;&#65533;U&#65533; &#65533;&#65533;SF%&#65533;/&#65533;&#65533;>&#65533;&#65533;PE&#65533;&#65533;PE&#65533;&#65533;&#65533;#&#65533;&#65533;&#65533;&#65533;&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2012-01-19 08:51:44 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2012-02-08 10:23:04 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2438MiB
                   capacity: 2438MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2438MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: WDC WD153BA
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 16.1
                serial: WD-WMA1U1089513
                size: 14GiB (15GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6c966c96
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/old_hdd
                   version: 3.1
                   serial: bc0b71e5-8abe-024f-ada4-e3e3088774e7
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-09-08 19:59:58 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: CD-R/CD-RW writer
                product: LTR-48327S
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: PTS1
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:c400(size=8) ioport:c800(size=4) ioport:cc00(size=8) ioport:d000(size=4) ioport:d400(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:dc00(size=256) ioport:e000(size=64) memory:f8181000-f81811ff memory:f8182000-f81820ff
     *-scsi
          physical id: 1
          bus info: usb@5:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sdf
```

---

### Post by Elfy on 2012-02-08
Hi - can you boot ubuntu and follow this page please, paste the result here.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

What printer is it that you can;t get to work?

---

### Post by Mark Phelps on 2012-02-09
You said you have two drives (sda and sdb) but there isn't any sdb listed.  

If you do have two physical drives, if you physically disconnect the Ubuntu drive, and the machine was set up CORRECTLY, you should then be able to boot from the Windows drive directly.

---

### Post by Lsh36 on 2012-02-09
Mark, windows is not on either drive and I tried to install window on the second drive after disconnecting the main drive.  It didn't work

---

### Post by Lsh36 on 2012-02-09
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   115,107,839   115,105,792  83 Linux
/dev/sda2         115,109,886   120,102,911     4,993,026   5 Extended
/dev/sda5         115,109,888   120,102,911     4,993,024  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.4 GB, 15382241280 bytes
255 heads, 63 sectors/track, 1870 cylinders, total 30043440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    30,025,484    30,025,422   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        16155d54-df09-4c52-ae65-3494174297fb   ext4       
/dev/sda5        0741a943-2bfc-4b52-9b8d-6ae2c92e40a4   swap       
/dev/sdb1        98386CF5386CD432                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/old_hdd           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	echo	'Loading Linux 2.6.32-38-generic ...'
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	echo	'Loading Linux 2.6.32-37-generic ...'
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	linux	/boot/vmlinuz-2.6.32-36-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	echo	'Loading Linux 2.6.32-36-generic ...'
	linux	/boot/vmlinuz-2.6.32-36-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	linux	/boot/vmlinuz-2.6.32-35-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	echo	'Loading Linux 2.6.32-35-generic ...'
	linux	/boot/vmlinuz-2.6.32-35-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	linux	/boot/vmlinuz-2.6.32-34-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	echo	'Loading Linux 2.6.32-34-generic ...'
	linux	/boot/vmlinuz-2.6.32-34-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=16155d54-df09-4c52-ae65-3494174297fb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 16155d54-df09-4c52-ae65-3494174297fb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0741a943-2bfc-4b52-9b8d-6ae2c92e40a4 none            swap    sw              0       0
/dev/sdb1 /media/old_hdd ntfs defualts 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  44.137855530 = 47.392661504   boot/grub/core.img                             1
  44.502964020 = 47.784693760   boot/grub/grub.cfg                             1
  44.195896149 = 47.454982144   boot/initrd.img-2.6.32-24-generic              1
  44.203346252 = 47.462981632   boot/initrd.img-2.6.32-33-generic              1
   1.281864166 = 1.376391168    boot/initrd.img-2.6.32-34-generic              1
  48.798812866 = 52.397326336   boot/initrd.img-2.6.32-35-generic              2
   1.010585785 = 1.085108224    boot/initrd.img-2.6.32-36-generic              2
   2.045536041 = 2.196377600    boot/initrd.img-2.6.32-37-generic              2
   1.137397766 = 1.221271552    boot/initrd.img-2.6.32-38-generic              2
  44.144767761 = 47.400083456   boot/vmlinuz-2.6.32-24-generic                 1
  44.132186890 = 47.386574848   boot/vmlinuz-2.6.32-33-generic                 1
  44.254741669 = 47.518167040   boot/vmlinuz-2.6.32-34-generic                 1
  44.835208893 = 48.141438976   boot/vmlinuz-2.6.32-35-generic                 1
  45.420261383 = 48.769634304   boot/vmlinuz-2.6.32-36-generic                 1
  45.664962769 = 49.032380416   boot/vmlinuz-2.6.32-37-generic                 1
  44.520374298 = 47.803387904   boot/vmlinuz-2.6.32-38-generic                 1
   1.137397766 = 1.221271552    initrd.img                                     2
   2.045536041 = 2.196377600    initrd.img.old                                 2
  44.520374298 = 47.803387904   vmlinuz                                        1
  45.664962769 = 49.032380416   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  14 12 12 c2 17 15 15 06  1a 18 18 1f 1d 1d 1b 1b  |................|
00000010  1b 13 13 13 18 18 18 15  15 15 c2 18 18 18 08 1e  |................|
00000020  1c 1c 1b 19 19 12 10 10  03 01 01 11 0c 0d 1a 15  |................|
00000030  16 1d 18 19 17 12 13 c2  1c 1a 1a 1a 1f 1d 1d 21  |...............!|
00000040  1f 1f 20 20 20 29 29 29  1d 1d 1d 12 12 12 10 10  |..   )))........|
00000050  10 0f 0f 0f 13 13 13 12  12 12 13 13 13 15 15 15  |................|
00000060  13 13 13 12 12 12 0c 0c  0c 0d 0d 0d 10 10 10 11  |................|
00000070  11 11 10 10 10 0e 0e 0e  0d 0d 0d 10 10 10 11 11  |................|
00000080  11 0d 0d 0d 0a 0a 0a 0d  0d 0d c2 0a 0a 0a 06 0b  |................|
00000090  0b 0b 09 09 09 0f 0f 0f  0e 0e 0e 0a 0a 0a 07 07  |................|
000000a0  07 c2 0b 0b 0b 03 05 05  05 02 02 02 05 05 05 c2  |................|
000000b0  06 06 06 01 03 03 03 c2  02 02 02 c2 03 03 03 02  |................|
000000c0  02 02 02 03 03 03 c2 01  01 01 02 00 00 00 03 03  |................|
000000d0  03 c4 05 05 05 c3 03 03  03 07 04 04 04 05 05 05  |................|
000000e0  03 03 03 02 02 02 03 03  03 05 05 05 06 06 06 c2  |................|
000000f0  07 07 07 04 09 09 09 0b  0b 0b 0a 0a 0a 09 09 09  |................|
00000100  c2 08 08 08 0b 09 09 09  0a 0a 0a 08 08 08 07 07  |................|
00000110  07 08 08 08 0a 0a 0a 0b  0b 0b 0c 0c 0c 09 09 09  |................|
00000120  0a 0a 0a 0c 0c 0c c4 0f  0f 0f 03 10 10 10 0c 0d  |................|
00000130  0b 0b 0c 0a c2 0c 0c 0c  02 12 12 12 16 16 16 c2  |................|
00000140  15 15 15 0a 19 19 19 17  17 17 1b 1b 1b 1c 1c 1c  |................|
00000150  17 17 17 15 15 15 18 18  18 17 17 17 15 16 14 13  |................|
00000160  14 12 c3 15 16 14 13 16  17 15 1a 1b 19 1b 1c 1a  |................|
00000170  1d 1d 1d 17 17 17 18 18  18 16 16 16 17 17 17 14  |................|
00000180  14 14 16 16 16 1c 1c 1c  1e 1e 1e 1c 1c 1c 1e 1e  |................|
00000190  1e 1f 1f 1f 22 22 22 1a  1a 1a 16 16 16 14 14 14  |....""".........|
000001a0  c2 12 12 12 07 15 15 15  18 18 18 11 11 11 0f 0f  |................|
000001b0  0f 10 0e 0e 13 11 11 13  13 13 c3 15 15 15 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 30 4c 00 00 00  |...........0L...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 


```

After starting to look at this (even though I'm not sure what it all means) I do see that windows is on the system somewhere.  I don't know if it has been on here from the time I had someone work on this or after said person told me that I should be able to just boot it by restarting the computer. When that didn't work I physically unplugged the larger hd to try and install windows on the smaller hd. I hope this makes sense to someone.

---

### Post by Mark Phelps on 2012-02-09
> **Lsh36 said:**
> Mark, windows is not on either drive and I tried to install window on the second drive after disconnecting the main drive.  It didn't work

Sorry ... misunderstood.  Though that you had WinXP on the second drive.

But ... it appears that while you DO, there are no boot files there.

What you can try is the following:
1) From the link below, download and burn the Boot-Repair CD image to a CD.
2) Disconnect the Ubuntu drive
3) Boot from the Boot-Repair CD and see if it will repair the WinXP boot.
4) Reboot using only the WinXP drive.  If the repair works, it will now boot into XP.
5) If that works, reconnect the Ubuntu drive -- but boot from it.  Then, once at the Ubuntu desktop, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB config file, and when you then reboot, you should get a GRUB menu.

Good Luck

---

### Post by Lsh36 on 2012-02-12
What is the link that I have to follow?

---

### Post by Mark Phelps on 2012-02-13
> **Lsh36 said:**
> What is the link that I have to follow?


Sorry ... forgot the link:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

