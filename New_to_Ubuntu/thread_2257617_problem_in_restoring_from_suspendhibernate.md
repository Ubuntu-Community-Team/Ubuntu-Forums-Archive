---
title: "problem in restoring from suspend/hibernate"
date: 2014-12-21
forum: New to Ubuntu
---

### Post by marco70 on 2014-12-21
Hi everybondy!

I've recently installed lubuntu 14.04 on my family's desktop computer. The only problem i have is that suspend, hibernate and suspend-hybrid don't work.
More specifically, if i do sudo pm-suspend the computer suspends with no problems, then it immediately awakes (i think this is because input devices can resume from suspend, i still have to find out how to avoid this), but no signal comes to the monitor. I can't do anything. I have nothing to do but forcing shutdown.
Regarding pm-hibernate the pc hibernates correctly, but then it doesn't resume. After the grub screen i only get an error message (ata2:ACPI set timing mode failed) and nothing else. I have to force shutdown.
For suspend-hybrid... well, the result is not different form suspend.

Once, when i restarted the computer after the forced shutdown, i got the window which allowed me to send the error report. Looking in the details i found out that the error was an Xorg crash.

I post the result of lshw|less

```
familiare-desktop
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=50F6F55E-105A-DA11-8827-0C7418F4F53B
  *-core
       description: Motherboard
       product: P4S800D-X
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1005.001
          date: 09/07/2005
          size: 64KiB
          capacity: 448KiB
           capabilities: isa pci pnp apm upgrade shadowing escd cdboot  bootselect socketedrom edd int13floppy1200 int13floppy720  int13floppy2880 int5printscreen int9keyboard int14serial int17printer  int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: PGA 478
          size: 3200MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 200MHz
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse  sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid  xtpr
          configuration: id=0
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
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 32
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 655 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 50
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fca00000-feafffff memory:d7f00000-f7efffff
           *-display
                description: VGA compatible controller
                product: NV36 [GeForce FX 5700LE]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff memory:feae0000-feafffff
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-multimedia
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=64 maxlatency=11 mingnt=52
             resources: irq:18 ioport:e800(size=256) ioport:ec00(size=128)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:20 memory:febfc000-febfcfff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:21 memory:febfd000-febfdfff
        *-usb:2
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:22 memory:febfe000-febfefff
        *-usb:3
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64 maxlatency=80
             resources: irq:23 memory:febff000-febfffff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:15:f2:2e:15:10
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
              configuration: autonegotiation=on broadcast=yes  driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full  ip=192.168.1.35 latency=64 link=yes maxlatency=11 mingnt=52  multicast=yes port=MII speed=100Mbit/s
             resources: irq:19 ioport:e400(size=256) memory:febfb000-febfbfff memory:febc0000-febdffff
        *-storage
             description: RAID bus controller
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master
             configuration: driver=sata_sis latency=128
              resources: irq:17 ioport:eff0(size=8) ioport:efe4(size=4)  ioport:efa8(size=8) ioport:efe0(size=4) ioport:ef90(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom:0
             description: SCSI CD-ROM
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             capabilities: audio
             configuration: status=nodisc
        *-cdrom:1
             description: DVD-RAM writer
             product: CD/DVDW SH-S162L
             vendor: TSSTcorp
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sr1
             version: TS04
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Maxtor 6Y120L0
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: YAR4
             serial: Y3M5CL0E
             size: 114GiB (122GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=95759575
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/windows
                version: 3.1
                serial: b0fe-0216
                size: 79GiB
                capacity: 79GiB
                capabilities: primary bootable ntfs initialized
                 configuration: clustersize=4096 created=2012-11-15  15:53:31 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk  mount.options=rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096  mounted_on_nt4=true resize_log_file=true state=mounted  upgrade_on_mount=true
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: 395fe2a5-0c94-43a7-b93e-b56ac6ad304f
                size: 30GiB
                capacity: 30GiB
                 capabilities: primary journaled extended_attributes  large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                 configuration: created=2014-12-06 12:36:11  filesystem=ext4 lastmountpoint=/ modified=2014-12-14 15:08:25  mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,data=ordered  mounted=2014-12-14 15:08:25 state=mounted
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: eb3b08ab-589e-4c9c-906c-ff7201ab3679
                size: 3999MiB
                capacity: 3999MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
```

and the three logs of suspend, hibernate and suspend-hybrid:

Suspend:
```
Initial commandline parameters: 
dom 14 dic 2014, 14.53.54, CET: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux familiare-desktop 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:56:26 UTC 2014 i686 i686 i686 GNU/Linux
Module                  Size  Used by
usblp                  18277  0 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
joydev                 17101  0 
snd_intel8x0           33110  4 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
nvidia               7108418  24 
snd                    60939  16 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
serio_raw              13230  0 
soundcore              12600  1 snd
i2c_sis630             13819  0 
parport_pc             31981  1 
ppdev                  17391  0 
shpchp                 32128  0 
mac_hid                13037  0 
lp                     13299  0 
sis_agp                13091  1 
parport                40836  3 lp,ppdev,parport_pc
hid_logitech           22181  0 
ff_memless             13325  1 hid_logitech
usbhid                 47070  0 
hid                    87604  2 hid_logitech,usbhid
psmouse                91357  0 
sis900                 26518  0 
sata_sis               12711  0 
mii                    13654  1 sis900
floppy                 55416  0 
             total       used       free     shared    buffers     cached
Mem:       2063972    1273400     790572       3552     106448     874680
-/+ buffers/cache:     292272    1771700
Swap:      4094972          0    4094972
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

dom 14 dic 2014, 14.53.55, CET: performing suspend
dom 14 dic 2014, 14.54.05, CET: Awake.
dom 14 dic 2014, 14.54.05, CET: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level   = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

dom 14 dic 2014, 14.54.06, CET: Finished.
```

Hibernate
```
Initial commandline parameters: 
dom  7 dic 2014, 16.04.39, CET: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux familiare-desktop 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:56:26 UTC 2014 i686 i686 i686 GNU/Linux
Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
usblp                  18277  0 
joydev                 17101  0 
snd_intel8x0           33110  1 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60939  10 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
nvidia               7108418  24 
serio_raw              13230  0 
soundcore              12600  1 snd
shpchp                 32128  0 
i2c_sis630             13819  0 
mac_hid                13037  0 
parport_pc             31981  1 
sis_agp                13091  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_logitech           22181  0 
ff_memless             13325  1 hid_logitech
usbhid                 47070  0 
hid                    87604  2 hid_logitech,usbhid
psmouse                91357  0 
sis900                 26518  0 
mii                    13654  1 sis900
sata_sis               12711  0 
floppy                 55416  0 
             total       used       free     shared    buffers     cached
Mem:       2063972     437116    1626856       1872      58836     201676
-/+ buffers/cache:     176604    1887368
Swap:      4094972          0    4094972
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.

dom  7 dic 2014, 16.04.41, CET: performing hibernate
dom  7 dic 2014, 16.05.39, CET: Awake.
dom  7 dic 2014, 16.05.39, CET: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level   = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx thaw hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx thaw hibernate: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status thaw hibernate:
/usr/lib/pm-utils/sleep.d/000record-status thaw hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.

dom  7 dic 2014, 16.05.40, CET: Finished.

```

and suspend-hybrid
```
Initial commandline parameters: 
dom 14 dic 2014, 15.05.08, CET: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend_hybrid:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend_hybrid:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend_hybrid:
Linux familiare-desktop 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:56:26 UTC 2014 i686 i686 i686 GNU/Linux
Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
joydev                 17101  0 
snd_intel8x0           33110  2 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60939  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
serio_raw              13230  0 
soundcore              12600  1 snd
nvidia               7108418  24 
ppdev                  17391  0 
parport_pc             31981  1 
i2c_sis630             13819  0 
shpchp                 32128  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
sis_agp                13091  1 
hid_logitech           22181  0 
ff_memless             13325  1 hid_logitech
usbhid                 47070  0 
hid                    87604  2 hid_logitech,usbhid
psmouse                91357  0 
sis900                 26518  0 
sata_sis               12711  0 
mii                    13654  1 sis900
floppy                 55416  0 
             total       used       free     shared    buffers     cached
Mem:       2063972     463596    1600376       2112      58768     203360
-/+ buffers/cache:     201468    1862504
Swap:      4094972          0    4094972
/usr/lib/pm-utils/sleep.d/00logging suspend suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend_hybrid:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend_hybrid: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend_hybrid:
/etc/pm/sleep.d/10_grub-common suspend suspend_hybrid: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend_hybrid:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend_hybrid:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend_hybrid:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend_hybrid:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend_hybrid: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend_hybrid:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend_hybrid: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend_hybrid:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend_hybrid:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend_hybrid:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend_hybrid: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend_hybrid:
/usr/lib/pm-utils/sleep.d/95led suspend suspend_hybrid: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend_hybrid:
/usr/lib/pm-utils/sleep.d/95led suspend suspend_hybrid: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend_hybrid:
nVidia binary video drive detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend_hybrid:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend_hybrid: success.

dom 14 dic 2014, 15.05.09, CET: performing suspend_hybrid
sh: echo: I/O error
dom 14 dic 2014, 15.05.27, CET: Awake.
dom 14 dic 2014, 15.05.27, CET: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/99video resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/95led resume suspend_hybrid: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend_hybrid:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level   = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/90clock resume suspend_hybrid: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend_hybrid:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend_hybrid:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend_hybrid: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend_hybrid:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend_hybrid: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend_hybrid:
/etc/pm/sleep.d/10_grub-common resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/00logging resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend_hybrid: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend_hybrid:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend_hybrid: success.

dom 14 dic 2014, 15.05.27, CET: Finished.

```


One thing that surprises me is the fact that none of the three logs seem to have any error... I hope someone can help me, i really need at least one of this commands to work!

Thank you very much in advance!

---

