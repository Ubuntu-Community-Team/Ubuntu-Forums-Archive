---
title: "plymouth splash screen: No splash?"
date: 2014-12-30
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2014-12-30
Hello once again Ubuntu forums community!

Fresh install of Ubuntu GNOME 14.10, no updates installed, sometimes shows splash screen.
Updated kernel, along with other packages: Never shows splash screen.

Screenshot of the Additional Drivers section in "Software and Updates":
[attach]258888[/attach]

lshw as root:
```
owner@owner-HP-2000-Notebook-PC:~$ sudo -i lshw
owner-hp-2000-notebook-pc 
    description: Notebook
    product: HP 2000 Notebook PC (D1E89UA#ABA)
    vendor: Hewlett-Packard
    version: 088B110000305910000620100
    serial: 5CG3231KXZ
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PRE X=MIN sku=D1E89UA#ABA uuid=9E88ECBE-D2CA-9118-1582-110669DEB62A
  *-core
       description: Motherboard
       product: 188B
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 69.14
       serial: PCVAA00WD4QEE3
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.25
          date: 02/21/2013
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb uefi
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 0
             serial: Empty
             slot: Bottom-Slot 1(top)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: 16KTF51264HZ-1G6M1
             vendor: Micron Technology
             physical id: 1
             serial: E375E0B6
             slot: Bottom-Slot 2(under)
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-cpu
          description: CPU
          product: AMD E-300 APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 2d
          bus info: cpu@0
          version: AMD E-300 APU with Radeon(tm) HD Graphics
          serial: NotSupport
          slot: Socket FT1
          size: 1300MHz
          capacity: 1300MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat hw_pstate npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 2e
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 2f
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-pci:0
          description: Host bridge
          product: Family 14h Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-display
             description: VGA compatible controller
             product: Wrestler [Radeon HD 6310]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:45 memory:e0000000-efffffff ioport:3000(size=256) memory:f0400000-f043ffff
        *-multimedia:0
             description: Audio device
             product: Wrestler HDMI Audio
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f0444000-f0447fff
        *-pci:0
             description: PCI bridge
             product: Family 14h Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:1000(size=4096) memory:f0500000-f06fffff ioport:f0700000(size=2097152)
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:41 ioport:3118(size=8) ioport:3124(size=4) ioport:3110(size=8) ioport:3120(size=4) ioport:3100(size=16) memory:f044c000-f044c7ff
        *-usb:0
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f044b000-f044bfff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f044a000-f044a0ff
        *-usb:2
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f0449000-f0449fff
        *-usb:3
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f0448000-f04480ff
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:f0440000-f0443fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-pci:2
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:f0300000-f03fffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 05
                serial: d4:c9:ef:81:0f:7f
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
        *-pci:3
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f0200000-f02fffff
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 01
                serial: 24:fd:52:62:ac:58
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.16.0-28-generic firmware=N/A ip=192.168.1.107 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f0200000-f027ffff memory:f0280000-f028ffff
        *-pci:4
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f0100000-f01fffff
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:43 memory:f0100000-f0100fff
     *-pci:1
          description: Host bridge
          product: Family 12h/14h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 43
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 12h/14h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 12h/14h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 12h/14h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 12h/14h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 12h/14h Processor Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 12h/14h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 12h/14h Processor Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54505
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: A7A0
             serial: TM8514ZN3Z031P
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=910b8f56-78ed-4709-a1e5-da669e458ca7 sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: f23f-54f5
                size: 398MiB
                capacity: 399MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2013-06-05 13:35:22 filesystem=ntfs label=WINRE modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: 92d5-36e6
                size: 239MiB
                capacity: 259MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: a45ae17e-f6ae-48f3-ba64-79aae854044f
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                logical name: /media/owner/Windows
                version: 3.1
                serial: 4e0078d0-57f9-0d4e-b71c-f0cde561e22e
                size: 280GiB
                capacity: 280GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2012-08-17 12:39:31 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 name=Basic data partition state=mounted
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: fb67-89c0
                size: 329MiB
                capacity: 349MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2013-10-26 22:45:29 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:5
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: a0d8d897-e885-8a43-8594-82bd60746d1b
                size: 23GiB
                capacity: 23GiB
                capabilities: precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2013-06-05 13:35:14 filesystem=ntfs label=RECOVERY modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:6
                description: Linux swap volume
                vendor: Linux
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                version: 1
                serial: 7e245636-9974-40f1-9c66-2a4447e010cb
                size: 6142MiB
                capacity: 6143MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:7
                description: EXT4 volume
                vendor: Linux
                physical id: 8
                bus info: scsi@0:0.0.0,8
                logical name: /dev/sda8
                logical name: /
                version: 1.0
                serial: 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
                size: 155GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-24 14:41:31 filesystem=ext4 label=Ubun2 GNOME Root lastmountpoint=/ modified=2014-12-28 18:02:13 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-28 18:02:14 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SN-208DB
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: HH01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       product: MU06047
       vendor: 13-42
       physical id: 1
       slot: Primary
       capacity: 47520mWh
       configuration: voltage=10.8V
```

cat /boot/grub/grub.cfg:
```
owner@owner-HP-2000-Notebook-PC:~$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
else
  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
set linux_gfx_mode=None
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt8'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
	else
	  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
	fi
	linux	/boot/vmlinuz-3.16.0-28-generic.efi.signed root=UUID=7e71d5e5-ca26-4477-95ab-de7fcf12b39b ro  plymouth:debug splash quiet drm.debug=0xe $vt_handoff
	initrd	/boot/initrd.img-3.16.0-28-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
	menuentry 'Ubuntu, with Linux 3.16.0-28-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-28-generic-advanced-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		else
		  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		fi
		echo	'Loading Linux 3.16.0-28-generic ...'
		linux	/boot/vmlinuz-3.16.0-28-generic.efi.signed root=UUID=7e71d5e5-ca26-4477-95ab-de7fcf12b39b ro  plymouth:debug splash quiet drm.debug=0xe $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-28-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-28-generic-recovery-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
		recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		else
		  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		fi
		echo	'Loading Linux 3.16.0-28-generic ...'
		linux	/boot/vmlinuz-3.16.0-28-generic.efi.signed root=UUID=7e71d5e5-ca26-4477-95ab-de7fcf12b39b ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-28-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-23-generic-advanced-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		else
		  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		fi
		echo	'Loading Linux 3.16.0-23-generic ...'
		linux	/boot/vmlinuz-3.16.0-23-generic root=UUID=7e71d5e5-ca26-4477-95ab-de7fcf12b39b ro  plymouth:debug splash quiet drm.debug=0xe $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-23-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-23-generic-recovery-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
		recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		else
		  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		fi
		echo	'Loading Linux 3.16.0-23-generic ...'
		linux	/boot/vmlinuz-3.16.0-23-generic root=UUID=7e71d5e5-ca26-4477-95ab-de7fcf12b39b ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-23-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-92D5-36E6' {
	insmod part_gpt
	insmod fat
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  92D5-36E6
	else
	  search --no-floppy --fs-uuid --set=root 92D5-36E6
	fi
	chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

cat /etc/default/grub:
```
owner@owner-HP-2000-Notebook-PC:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="plymouth:debug splash quiet drm.debug=0xe"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXPAYLOAD_LINUX=None
```

Any ideas of what may be happening?

-Jonathan

---

### Post by Dennis N on 2014-12-30
This could help. I used to apply this solution for the spash screen appearing very briefly or not at all.  In recent installs I haven't needed it.
-----------------------------------
Problem:
Plymouth splash starts very late or not at all, with a black screen otherwise displaying until the log-in screen appears.

A solution was offered by Scott Remnant of Canonical:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2)

These steps are based on his method, and do the same thing:

1) Create a text file named splash containing the line FRAMEBUFFER=y and copy it (with sudo) into
the folder [B]/etc/initramfs-tools/conf.d/
2[/B]) Execute in the terminal: **sudo update-initramfs -u**
3) Reboot.

After this, the splash starts in 3 or 4 seconds.

This is less likely to help much if you have an NVidia driver.

Your results may vary!

---

### Post by Jonathan Precise on 2014-12-31
Hello Dennis N, thanks for the reply.

After running that, there is still no splash screen at all on the new kernel. A bit more searching found me this:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1356513](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1356513)

Neither removing vt_handoff or pressing a key during startup shows it.

Any other ideas?

---

### Post by Dennis N on 2014-12-31
It failed to work for me on too on the 14.04 kernel and an NVidia Card. I ended up just taking "splash" out of the grub command line, giving just a black screen rather than the weird text splash I was getting. An AMD system I have and Intel were ok - And I see you have AMD. Thats why I added "your results may vary!" 

You can remove the file named splash, and rerun the command to undo it all. Sorry I don't have another idea. I did a lot of searching at the time.

---

### Post by Jonathan Precise on 2014-12-31
Hello Dennis N.

I normally just get a black screen with/without FRAMEBUFFER=y on the splash file, and I don't mind that too much. Yes, I'd prefer the splash screen, but I prefer black screen than the text splash I used to get on an old machine I had.

For now, I shall mark this thread as solved.

P.S. Thanks Dennis N for trying to help me with this.

---

### Post by Jonathan Precise on 2015-01-01
I think I found the culprit:

> **Jonathan Precise said:**
> 
```
...
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt8'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
	else
	  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
	fi
	linux	/boot/vmlinuz-3.16.0-28-generic.efi.signed root=UUID=7e71d5e5-ca26-4477-95ab-de7fcf12b39b [COLOR="#FF0000"]ro  plymouth:debug splash quiet drm.debug=0xe $vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.16.0-28-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
	menuentry 'Ubuntu, with Linux 3.16.0-28-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-28-generic-advanced-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		else
		  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		fi
		echo	'Loading Linux 3.16.0-28-generic ...'
		linux	/boot/vmlinuz-3.16.0-28-generic.efi.signed root=UUID=7e71d5e5-ca26-4477-95ab-de7fcf12b39b [COLOR="#FF0000"]ro  plymouth:debug splash quiet drm.debug=0xe $vt_handoff[/COLOR]
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-28-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-28-generic-recovery-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
		recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		else
		  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		fi
		echo	'Loading Linux 3.16.0-28-generic ...'
		linux	/boot/vmlinuz-3.16.0-28-generic.efi.signed root=UUID=7e71d5e5-ca26-4477-95ab-de7fcf12b39b ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-28-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-23-generic-advanced-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		else
		  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		fi
		echo	'Loading Linux 3.16.0-23-generic ...'
		linux	/boot/vmlinuz-3.16.0-23-generic root=UUID=7e71d5e5-ca26-4477-95ab-de7fcf12b39b [COLOR="#FF0000"]ro  plymouth:debug splash quiet drm.debug=0xe $vt_handoff[/COLOR]
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-23-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-23-generic-recovery-7e71d5e5-ca26-4477-95ab-de7fcf12b39b' {
		recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt8'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		else
		  search --no-floppy --fs-uuid --set=root 7e71d5e5-ca26-4477-95ab-de7fcf12b39b
		fi
		echo	'Loading Linux 3.16.0-23-generic ...'
		linux	/boot/vmlinuz-3.16.0-23-generic root=UUID=7e71d5e5-ca26-4477-95ab-de7fcf12b39b ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.16.0-23-generic
	}
}
...

```


Changing the text in [COLOR="#FF0000"]red[/COLOR] to [FONT=Courier New]ro quiet splash[/FONT] + the FRAMEBUFFER=y fixed it for me!

Thanks Dennis N for the FRAMEBUFFER=y

---

### Post by Dennis N on 2015-01-02
Thanks for the feedback. Glad to know that this little framebuffer fix worked again!

---

