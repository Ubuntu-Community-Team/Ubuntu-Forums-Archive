---
title: "Computer (1215N) won't stop"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by Strikeiron on 2012-06-01
Hello,
I've been looking for a section fitting for my problems but i can't post into because I'm a "newbye".
I've got an Asus 1215N with Precise pangolin, I tried the passage with kernel 3.2 etc... but It gave me error so now I've got:

[PHP]samuele@samuele-1215N:/etc/pm/config.d$ uname -a
Linux samuele-1215N 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 i686 i386 GNU/Linux
[/PHP]

When I shut down the computer won't stop but remains stuck on ubuntu desktop, with ctr alt F2 I read:

[PHP]nouveau 000:04:00.0 INVALID ROM contents
[drm] Pointer to BIT loadval table invalid
[drm] Failed parsing init table opcode: INIT_ZM_I2C_BYTE-6[/PHP]

I suppose It's a problem with nvidia....

Thanks in advance!

---

### Post by Strikeiron on 2012-06-01
In case you need it to understand It better:

> samuele@samuele-1215N:/etc/pm/config.d$ sudo lshw
[sudo] password for samuele: 
PCI (sysfs)  
samuele-1215n             
    description: Notebook
    product: 1215N (1215N)
    vendor: ASUSTeK Computer INC.
    version: x.x
    serial: AAOAAS459180
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 family=Eee PC sku=1215N uuid=808C66F5-8ACC-5C81-3E5E-BCAEC507DDE4
  *-core
       description: Motherboard
       product: 1215N
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: x.xx
       serial: EeePC-0123456789
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0503
          date: 09/07/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Atom(TM) CPU D525   @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.10
          serial: 0001-06CA-0000-0000-0000-0000
          slot: CPU 1
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
          configuration: cores=2 enabledcores=2 id=0 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 48KiB
             capacity: 48KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 800 MHz (1,2 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 800 MHz (1,2 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.12.10
          serial: 0001-06CA-0000-0000-0000-0000
          size: 1800MHz
          capabilities: ht
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
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:f5e00000-f5e7ffff ioport:cc00(size=8) memory:b0000000-bfffffff memory:f5d00000-f5dfffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f5e80000-f5efffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:f5cf8000-f5cfbfff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fa000000-fbffffff ioport:ce000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:ec00(size=128) memory:fbf00000-fbf7ffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:f6000000-f9ffffff ioport:c8000000(size=100663296)
           *-network
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 01
                serial: 48:5d:60:55:1e:1b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.39 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:f9ffc000-f9ffffff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:f5f00000-f5ffffff ioport:7f700000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8152 v2.0 Fast Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: c1
                serial: bc:ae:c5:07:dd:e4
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:46 memory:f5fc0000-f5ffffff ioport:dc00(size=128)
        *-usb:0
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c400(size=32)
        *-usb:1
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c480(size=32)
        *-usb:2
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c800(size=32)
        *-usb:3
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c880(size=32)
        *-usb:4
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f5cf7c00-f5cf7fff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: N10/ICH7 Family SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=32) memory:f5cf7800-f5cf7bff
           *-disk
                description: ATA Disk
                product: ST9320325AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0003
                serial: 6VD6Y31N
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=41257aac
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 88359b17-05c3-e045-9e66-f8e87544587a
                   size: 99GiB
                   capacity: 99GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-01-01 21:12:50 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: FAT32
                   serial: 76a8-4c64
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 183GiB
                   capacity: 183GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 173GiB
                      configuration: mount.fstype=ext2 mount.options=rw,relatime,errors=remount-ro state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 10236MiB
                      capabilities: nofs
              *-volume:3
                   description: EFI (FAT-12/16/32) partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 16MiB
                   capabilities: primary boot
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
samuele@samuele-1215N:/etc/pm/config.d$ 
samuele@samuele-1215N:/etc/pm/config.d$ lsmod
Module                  Size  Used by
michael_mic             1744  4 
arc4                    1165  2 
sco                     7998  2 
bnep                    9542  2 
rfcomm                 33811  0 
l2cap                  37008  6 bnep,rfcomm
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
dm_crypt               11385  0 
nouveau               517274  0 
snd_hda_codec_realtek   218492  1 
ttm                    56633  1 nouveau
snd_hda_intel          22203  2 
i915                  295243  4 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
uvcvideo               55847  0 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
joydev                  8767  0 
drm_kms_helper         30200  2 nouveau,i915
drm                   168092  6 nouveau,ttm,i915,drm_kms_helper
usbhid                 36882  0 
snd_seq_midi            4588  0 
eeepc_wmi               2899  0 
videodev               43098  1 uvcvideo
hid                    67742  1 usbhid
lib80211_crypt_tkip     7736  0 
snd_rawmidi            17783  1 snd_seq_midi
wl                   1959533  0 
snd_seq_midi_event      6047  1 snd_seq_midi
v4l1_compat            13359  2 uvcvideo,videodev
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  10969  1 
i2c_algo_bit            5168  2 nouveau,i915
sparse_keymap           3145  1 eeepc_wmi
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
bluetooth              50500  9 sco,bnep,rfcomm,l2cap,btusb
lib80211                5058  2 lib80211_crypt_tkip,wl
intel_agp              26566  2 i915
video                  18712  1 i915
agpgart                32011  3 ttm,drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
libahci                21728  1 ahci
atl1c                  29949  0 
samuele@samuele-1215N:/etc/pm/config.d$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
04:00.0 VGA compatible controller: NVIDIA Corporation Device 0a76 (rev a2)
samuele@samuele-1215N:/etc/pm/config.d$

---

### Post by jmore9 on 2012-06-01
Thwe last post has something about this :

[http://ubuntuforums.org/showthread.php?t=1534369](http://ubuntuforums.org/showthread.php?t=1534369)

---

### Post by Strikeiron on 2012-06-01
> **jmore9 said:**
> Thwe last post has something about this :

[http://ubuntuforums.org/showthread.php?t=1534369](http://ubuntuforums.org/showthread.php?t=1534369)

Thanks, I'll have a look. The question is: can I trust nvidia drivers? Once I tried and I wan't able to start the computer anymore...

---

### Post by Strikeiron on 2012-06-01
Cut

---

### Post by Strikeiron on 2012-06-05
Now I know what's wrong, but I don't know how to have it fixed... when I shut down computer blocks with this message:

[PHP]Stopping landscape-client daemon [FAIL]
Stopping Mail Transport Agent (MTA) sendmail
no crontab for root - using an empty one
Select an editor. To change later run "select editor"
1 /bin/ed
2 /bin/nano <---------------------- easiest
3 /usr/bin/vimtiny
choose 1-3 [2][/PHP]

Has anyone some idea?
Thanks

---

