---
title: "Bumblebee, Soundcard, conflicting Processes, howto locate Problems."
date: 2013-06-12
forum: New to Ubuntu
---

### Post by tillitus on 2013-06-12
Hi there, 
I hope posting my problem here is the right place to do so, otherwise i feel sorry.

I have Ubuntu installed on a Dell XPS 15 502 machine. Because of The optimus Graphic-card i had to install bumblebee successfully.
Everything worked fine.

I am an explorer so i tried many things to improve ubuntu... but thats not good if you try out something when you don't know what problems can resolute.

SO NOW: I got no sound working and i don't know why. Sometimes it's happening that i can't move a window, or when i click on it there's no reaction. (SOMETIMES)

My Question: I think there are a few processes (or drivers/packages/...) running that are conflicting each other. How can I locate and fix these Conflicts?

Would be very thankfull for any Answers/solutions...

I know that you need more informations... but i don't know in which direction they should go.

---

### Post by zero2xiii on 2013-06-12
Hay,

Please start [here]("http://ubuntuforums.org/showthread.php?t=2140012") (help us help you; also in my signature).

Some useful commands' output can include:

```
sudo lshw
lsmod
```

Cheers

---

### Post by tillitus on 2013-06-12
Thanks for The two commands: here are the outputs: 


```
dell                      
    description: Portable Computer
    product: Dell System XPS L502X (System SKUNumber)
    vendor: Winbond Electronics
    version: 0.1
    serial: 4LB40Q1
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: administrator_password=unknown boot=normal chassis=portable family=HuronRiver System frontpanel_password=unknown keyboard_password=unknown power-on_password=unknown sku=System SKUNumber uuid=44454C4C-4C00-1042-8034-B4C04F305131
  *-core
       description: Motherboard
       product: 0NJT03
       vendor: Winbond Electronics
       physical id: 0
       version: A00
       serial: .4LB40Q1.CN486431590224.
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A10
          date: 02/20/2012
          size: 128KiB
          capacity: 2496KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
          vendor: Intel Corp.
          physical id: 19
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
          serial: Not Supported by CPU
          slot: CPU
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 1a
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 1b
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through data
        *-cache:2
             description: L3 cache
             physical id: 1c
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 0
             serial: 649B08EA
             slot: ChannelA-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 1
             serial: EB9A08E7
             slot: ChannelB-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:f0000000-f10fffff ioport:c0000000(size=301989888)
           *-generic UNCLAIMED
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
                resources: memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:f1000000-f107ffff
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:54 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:51 memory:f1c05000-f1c0500f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f1c0a000-f1c0a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:53 memory:f1c00000-f1c03fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f1b00000-f1bfffff
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1000
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 8c:a9:82:84:be:e6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-45-generic firmware=39.31.5.1 build 35138 ip=192.168.178.24 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:52 memory:f1b00000-f1b01fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:f1a00000-f1afffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:f1a00000-f1a01fff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f1900000-f19fffff
        *-pci:5
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) ioport:f1800000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 06
                serial: 14:fe:b5:ab:c4:1a
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:50 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f1c09000-f1c093ff
        *-isa
             description: ISA bridge
             product: HM67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4060(size=32) memory:f1c08000-f1c087ff
           *-disk
                description: ATA Disk
                product: WDC WD7500BPKT-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX31EC0P8807
                size: 698GiB (750GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003753a
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /mnt/sda1
                   version: 3.1
                   serial: 7c4d-ff44
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-11-23 10:45:43 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /mnt/sda2
                   version: 3.1
                   serial: 684b8961-ed09-f54d-a700-eeead0ced060
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-11-23 10:45:33 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 6cd7cf45-9e2a-0843-b1c9-a2dcd9a82c1a
                   size: 398GiB
                   capacity: 398GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-11-23 10:45:21 filesystem=ntfs state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /boot
                      capacity: 976MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 38GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 102GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 7812MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW AD-7717H
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 102A
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f1c04000-f1c040ff ioport:efa0(size=32)
  *-battery
       product: DELL
       vendor: UNKNOW
       physical id: 1
       version: 2008
       serial: 1.0
       slot: Rear
       capacity: 57720mWh
       configuration: voltage=11,1V
tilman@DELL:~$ 





**_[COLOR="#008000"]Output of lsmod:[/COLOR]_**


Module                  Size  Used by
bbswitch               13611  0 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
binfmt_misc            17540  1 
joydev                 17693  0 
i915                  478189  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
arc4                   12529  2 
snd_hda_intel          33719  1 
snd_hda_codec         127706  1 snd_hda_intel
iwlwifi               401125  0 
mac80211              506862  1 iwlwifi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_hwdep              17764  1 snd_hda_codec
dell_laptop            18119  0 
cfg80211              205774  2 iwlwifi,mac80211
psmouse                97485  0 
i2c_algo_bit           13423  1 i915
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dcdbas                 14490  1 dell_laptop
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
v4l2_compat_ioctl32    17128  1 videodev
serio_raw              13211  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19651  1 i915
mac_hid                13253  0 
snd                    79041  10 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
wmi                    19256  1 dell_wmi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0
```

---

### Post by tillitus on 2013-06-12
Here are a few other outputs where i would search for the problems:

Software/packages i installed before: (with command: cat /var/log/apt/term.log)
(sry that it's in german)

```
Vormals nicht ausgewähltes Paket openjdk-6-jre-headless wird gewählt.
Entpacken von openjdk-6-jre-headless (aus .../openjdk-6-jre-headless_6b27-1.12.5-0ubuntu0.12.04.1_amd64.deb) ...
Vormals nicht ausgewähltes Paket default-jre-headless wird gewählt.
Entpacken von default-jre-headless (aus .../default-jre-headless_1%3a1.6-43ubuntu2_amd64.deb) ...
Vormals nicht ausgewähltes Paket openjdk-6-jre wird gewählt.
Entpacken von openjdk-6-jre (aus .../openjdk-6-jre_6b27-1.12.5-0ubuntu0.12.04.1_amd64.deb) ...
Vormals nicht ausgewähltes Paket default-jre wird gewählt.
Entpacken von default-jre (aus .../default-jre_1%3a1.6-43ubuntu2_amd64.deb) ...
Vormals nicht ausgewähltes Paket libatk-wrapper-java wird gewählt.
Entpacken von libatk-wrapper-java (aus .../libatk-wrapper-java_0.30.4-0ubuntu2_all.deb) ...
Vormals nicht ausgewähltes Paket libatk-wrapper-java-jni wird gewählt.
Entpacken von libatk-wrapper-java-jni (aus .../libatk-wrapper-java-jni_0.30.4-0ubuntu2_amd64.deb) ...
Vormals nicht ausgewähltes Paket jdownloader-installer wird gewählt.
Entpacken von jdownloader-installer (aus .../jdownloader-installer_0.5-0jd3~ubuntu12.04.1~ppa1_all.deb) ...
Vormals nicht ausgewähltes Paket ttf-dejavu-extra wird gewählt.
Entpacken von ttf-dejavu-extra (aus .../ttf-dejavu-extra_2.33-2ubuntu1_all.deb) ...
Vormals nicht ausgewähltes Paket icedtea-6-jre-cacao wird gewählt.
Entpacken von icedtea-6-jre-cacao (aus .../icedtea-6-jre-cacao_6b27-1.12.5-0ubuntu0.12.04.1_amd64.deb) ...
Vormals nicht ausgewähltes Paket icedtea-6-jre-jamvm wird gewählt.
Entpacken von icedtea-6-jre-jamvm (aus .../icedtea-6-jre-jamvm_6b27-1.12.5-0ubuntu0.12.04.1_amd64.deb) ...
Vormals nicht ausgewähltes Paket icedtea-netx-common wird gewählt.
Entpacken von icedtea-netx-common (aus .../icedtea-netx-common_1.2.3-0ubuntu0.12.04.2_all.deb) ...
Vormals nicht ausgewähltes Paket icedtea-netx wird gewählt.
Entpacken von icedtea-netx (aus .../icedtea-netx_1.2.3-0ubuntu0.12.04.2_amd64.deb) ...
Vormals nicht ausgewähltes Paket jdownloader wird gewählt.
Entpacken von jdownloader (aus .../jdownloader_0.5-0jd3~ubuntu12.04.1~ppa1_all.deb) ...
Trigger für doc-base werden verarbeitet ...
Processing 2 added doc-base files...
Registering documents with scrollkeeper...
Trigger für man-db werden verarbeitet ...
Trigger für bamfdaemon werden verarbeitet ...
Rebuilding /usr/share/applications/bamf.index...
Trigger für desktop-file-utils werden verarbeitet ...
Trigger für gnome-menus werden verarbeitet ...
Trigger für hicolor-icon-theme werden verarbeitet ...
Trigger für fontconfig werden verarbeitet ...
java-common (0.43ubuntu2) wird eingerichtet ...
tzdata-java (2012e-0ubuntu0.12.04.1) wird eingerichtet ...
ttf-dejavu-extra (2.33-2ubuntu1) wird eingerichtet ...
icedtea-netx-common (1.2.3-0ubuntu0.12.04.2) wird eingerichtet ...
openjdk-6-jre-lib (6b27-1.12.5-0ubuntu0.12.04.1) wird eingerichtet ...
openjdk-6-jre-headless (6b27-1.12.5-0ubuntu0.12.04.1) wird eingerichtet ...
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java wird verwendet, um /usr/bin/java (java) im Auto-Modus bereitzustellen.
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/keytool wird verwendet, um /usr/bin/keytool (keytool) im Auto-Modus bereitzustellen.
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/pack200 wird verwendet, um /usr/bin/pack200 (pack200) im Auto-Modus bereitzustellen.
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/rmid wird verwendet, um /usr/bin/rmid (rmid) im Auto-Modus bereitzustellen.
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/rmiregistry wird verwendet, um /usr/bin/rmiregistry (rmiregistry) im Auto-Modus bereitzustellen.
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/unpack200 wird verwendet, um /usr/bin/unpack200 (unpack200) im Auto-Modus bereitzustellen.
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/orbd wird verwendet, um /usr/bin/orbd (orbd) im Auto-Modus bereitzustellen.
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/servertool wird verwendet, um /usr/bin/servertool (servertool) im Auto-Modus bereitzustellen.
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/tnameserv wird verwendet, um /usr/bin/tnameserv (tnameserv) im Auto-Modus bereitzustellen.
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/lib/jexec wird verwendet, um /usr/bin/jexec (jexec) im Auto-Modus bereitzustellen.
default-jre-headless (1:1.6-43ubuntu2) wird eingerichtet ...
openjdk-6-jre (6b27-1.12.5-0ubuntu0.12.04.1) wird eingerichtet ...
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/policytool wird verwendet, um /usr/bin/policytool (policytool) im Auto-Modus bereitzustellen.
default-jre (1:1.6-43ubuntu2) wird eingerichtet ...
jdownloader-installer (0.5-0jd3~ubuntu12.04.1~ppa1) wird eingerichtet ...
icedtea-6-jre-cacao (6b27-1.12.5-0ubuntu0.12.04.1) wird eingerichtet ...
icedtea-6-jre-jamvm (6b27-1.12.5-0ubuntu0.12.04.1) wird eingerichtet ...
icedtea-netx (1.2.3-0ubuntu0.12.04.2) wird eingerichtet ...
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/javaws wird verwendet, um /usr/bin/javaws (javaws) im Auto-Modus bereitzustellen.
update-alternatives: /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/itweb-settings wird verwendet, um /usr/bin/itweb-settings (itweb-settings) im Auto-Modus bereitzustellen.
jdownloader (0.5-0jd3~ubuntu12.04.1~ppa1) wird eingerichtet ...
ca-certificates-java (20110912ubuntu6) wird eingerichtet ...
Adding debian:Deutsche_Telekom_Root_CA_2.pem
Adding debian:Comodo_Secure_Services_root.pem
Adding debian:DigiCert_Assured_ID_Root_CA.pem
Adding debian:Secure_Global_CA.pem
Adding debian:Certinomis_-_Autorité_Racine.pem
Adding debian:Staat_der_Nederlanden_Root_CA.pem
Adding debian:VeriSign_Class_3_Public_Primary_Certification_Authority_-_G5.pem
Adding debian:Verisign_Class_2_Public_Primary_Certification_Authority.pem
Adding debian:thawte_Primary_Root_CA_-_G3.pem
Adding debian:TC_TrustCenter__Germany__Class_3_CA.pem
Adding debian:GeoTrust_Global_CA_2.pem
Adding debian:Camerfirma_Chambers_of_Commerce_Root.pem
Adding debian:Digital_Signature_Trust_Co._Global_CA_3.pem
Adding debian:GlobalSign_Root_CA_-_R3.pem
Adding debian:Thawte_Premium_Server_CA.pem
Adding debian:Autoridad_de_Certificacion_Firmaprofesional_CIF_A62634068.pem
Adding debian:spi-cacert-2008.pem
Adding debian:Certplus_Class_2_Primary_CA.pem
Adding debian:GeoTrust_Primary_Certification_Authority.pem
Adding debian:ePKI_Root_Certification_Authority.pem
Adding debian:NetLock_Express_=Class_C=_Root.pem
Adding debian:WellsSecure_Public_Root_Certificate_Authority.pem
Adding debian:GlobalSign_Root_CA_-_R2.pem
Adding debian:Verisign_Class_1_Public_Primary_Certification_Authority.pem
Adding debian:Buypass_Class_3_CA_1.pem
Adding debian:ApplicationCA_-_Japanese_Government.pem
Adding debian:TC_TrustCenter_Universal_CA_I.pem
Adding debian:Security_Communication_EV_RootCA1.pem
Adding debian:GeoTrust_Universal_CA.pem
Adding debian:UTN_DATACorp_SGC_Root_CA.pem
Adding debian:Firmaprofesional_Root_CA.pem
Adding debian:Certum_Root_CA.pem
Adding debian:Baltimore_CyberTrust_Root.pem
Adding debian:QuoVadis_Root_CA_2.pem
Adding debian:TÜB&#304;TAK_UEKAE_Kök_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;_-_Sürüm_3.pem
Adding debian:Camerfirma_Global_Chambersign_Root.pem
Adding debian:GeoTrust_Universal_CA_2.pem
Adding debian:Go_Daddy_Root_Certificate_Authority_-_G2.pem
Adding debian:ssl-cert-snakeoil.pem
Adding debian:Staat_der_Nederlanden_Root_CA_-_G2.pem
Adding debian:ComSign_CA.pem
Adding debian:Juur-SK.pem
Adding debian:COMODO_ECC_Certification_Authority.pem
Adding debian:QuoVadis_Root_CA_3.pem
Adding debian:cacert.org.pem
Adding debian:VeriSign_Universal_Root_Certification_Authority.pem
Adding debian:EBG_Elektronik_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;.pem
Adding debian:SecureTrust_CA.pem
Adding debian:TURKTRUST_Certificate_Services_Provider_Root_2.pem
Adding debian:Global_Chambersign_Root_-_2008.pem
Adding debian:Buypass_Class_2_CA_1.pem
Adding debian:NetLock_Qualified_=Class_QA=_Root.pem
Adding debian:NetLock_Arany_=Class_Gold=_F&#337;tanúsítvány.pem
Adding debian:SwissSign_Silver_CA_-_G2.pem
Adding debian:Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:NetLock_Notary_=Class_A=_Root.pem
Adding debian:Visa_eCommerce_Root.pem
Adding debian:TWCA_Root_Certification_Authority.pem
Adding debian:Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:Equifax_Secure_eBusiness_CA_2.pem
Adding debian:Chambers_of_Commerce_Root_-_2008.pem
Adding debian:SwissSign_Platinum_CA_-_G2.pem
Adding debian:GlobalSign_Root_CA.pem
Adding debian:Verisign_Class_3_Public_Primary_Certification_Authority.pem
Adding debian:AffirmTrust_Commercial.pem
Adding debian:E-Guven_Kok_Elektronik_Sertifika_Hizmet_Saglayicisi.pem
Adding debian:thawte_Primary_Root_CA.pem
Adding debian:Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:Equifax_Secure_Global_eBusiness_CA.pem
Adding debian:UbuntuOne-Go_Daddy_CA.pem
Adding debian:Izenpe.com.pem
Adding debian:RSA_Security_2048_v3.pem
Adding debian:Digital_Signature_Trust_Co._Global_CA_1.pem
Adding debian:Starfield_Class_2_CA.pem
Adding debian:TURKTRUST_Certificate_Services_Provider_Root_1.pem
Adding debian:TC_TrustCenter_Universal_CA_III.pem
Adding debian:CNNIC_ROOT.pem
Adding debian:TC_TrustCenter_Class_3_CA_II.pem
Adding debian:Equifax_Secure_CA.pem
Adding debian:DigiCert_Global_Root_CA.pem
Adding debian:Microsec_e-Szigno_Root_CA.pem
Adding debian:Hongkong_Post_Root_CA_1.pem
Adding debian:Network_Solutions_Certificate_Authority.pem
Adding debian:Certum_Trusted_Network_CA.pem
Adding debian:UTN_USERFirst_Hardware_Root_CA.pem
Adding debian:Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:AddTrust_Low-Value_Services_Root.pem
Adding debian:Sonera_Class_2_Root_CA.pem
Adding debian:Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:StartCom_Certification_Authority.pem
Adding debian:DST_ACES_CA_X6.pem
Adding debian:IGC_A.pem
Adding debian:Root_CA_Generalitat_Valenciana.pem
Adding debian:Thawte_Server_CA.pem
Adding debian:UTN_USERFirst_Email_Root_CA.pem
Adding debian:RSA_Root_Certificate_1.pem
Adding debian:GeoTrust_Primary_Certification_Authority_-_G3.pem
Adding debian:AddTrust_External_Root.pem
Adding debian:Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:America_Online_Root_Certification_Authority_2.pem
Adding debian:SecureSign_RootCA11.pem
Adding debian:thawte_Primary_Root_CA_-_G2.pem
Adding debian:GeoTrust_Global_CA.pem
Adding debian:DST_Root_CA_X3.pem
Adding debian:ValiCert_Class_2_VA.pem
Adding debian:Starfield_Services_Root_Certificate_Authority_-_G2.pem
Adding debian:spi-ca-2003.pem
Adding debian:GTE_CyberTrust_Global_Root.pem
Adding debian:COMODO_Certification_Authority.pem
Adding debian:Swisscom_Root_CA_1.pem
Adding debian:ComSign_Secured_CA.pem
Adding debian:Verisign_Class_4_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:XRamp_Global_CA_Root.pem
Adding debian:AffirmTrust_Premium.pem
Adding debian:A-Trust-nQual-03.pem
Adding debian:certSIGN_ROOT_CA.pem
Adding debian:Sonera_Class_1_Root_CA.pem
Adding debian:AddTrust_Public_Services_Root.pem
Adding debian:NetLock_Business_=Class_B=_Root.pem
Adding debian:Certigna.pem
Adding debian:TDC_OCES_Root_CA.pem
Adding debian:Entrust.net_Premium_2048_Secure_Server_CA.pem
Adding debian:CA_Disig.pem
Adding debian:Comodo_Trusted_Services_root.pem
Adding debian:Go_Daddy_Class_2_CA.pem
Adding debian:ca.pem
Adding debian:America_Online_Root_Certification_Authority_1.pem
Adding debian:Entrust.net_Secure_Server_CA.pem
Adding debian:TDC_Internet_Root_CA.pem
Adding debian:Security_Communication_Root_CA.pem
Adding debian:VeriSign_Class_3_Public_Primary_Certification_Authority_-_G4.pem
Adding debian:AffirmTrust_Networking.pem
Adding debian:DigiCert_High_Assurance_EV_Root_CA.pem
Adding debian:AffirmTrust_Premium_ECC.pem
Adding debian:Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:ACEDICOM_Root.pem
Adding debian:OISTE_WISeKey_Global_Root_GA_CA.pem
Adding debian:UbuntuOne-Go_Daddy_Class_2_CA.pem
Adding debian:QuoVadis_Root_CA.pem
Adding debian:Comodo_AAA_Services_root.pem
Adding debian:Entrust_Root_Certification_Authority.pem
Adding debian:AC_Raíz_Certicámara_S.A..pem
Adding debian:ValiCert_Class_1_VA.pem
Adding debian:SwissSign_Gold_CA_-_G2.pem
Adding debian:TC_TrustCenter_Class_2_CA_II.pem
Adding debian:Taiwan_GRCA.pem
Adding debian:TC_TrustCenter__Germany__Class_2_CA.pem
Adding debian:Equifax_Secure_eBusiness_CA_1.pem
Adding debian:Microsec_e-Szigno_Root_CA_2009.pem
Adding debian:GeoTrust_Primary_Certification_Authority_-_G2.pem
Adding debian:Wells_Fargo_Root_CA.pem
Adding debian:AddTrust_Qualified_Certificates_Root.pem
Adding debian:S-TRUST_Authentication_and_Encryption_Root_CA_2005_PN.pem
Adding debian:Cybertrust_Global_Root.pem
Adding debian:Starfield_Root_Certificate_Authority_-_G2.pem
done.
libatk-wrapper-java (0.30.4-0ubuntu2) wird eingerichtet ...
libatk-wrapper-java-jni (0.30.4-0ubuntu2) wird eingerichtet ...
Trigger für libc-bin werden verarbeitet ...
ldconfig deferred processing now taking place
Log ended: 2013-06-09  12:05:53

Log started: 2013-06-10  14:44:30
Selecting previously unselected package samba.
(Reading database ... 214144 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.6.3-2ubuntu2.6_amd64.deb) ...
Selecting previously unselected package tdb-tools.
Unpacking tdb-tools (from .../tdb-tools_1.2.9-4_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Setting up samba (2:3.6.3-2ubuntu2.6) ...
Generating /etc/default/samba...
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
smbd start/running, process 26441
nmbd start/running, process 26475
Setting up tdb-tools (1.2.9-4) ...
update-alternatives: using /usr/bin/tdbbackup.tdbtools to provide /usr/bin/tdbbackup (tdbbackup) in auto mode.
Log ended: 2013-06-10  14:44:43

Log started: 2013-06-10  14:44:59
Selecting previously unselected package libpam-smbpass.
(Reading database ... 214239 files and directories currently installed.)
Unpacking libpam-smbpass (from .../libpam-smbpass_2%3a3.6.3-2ubuntu2.6_amd64.deb) ...
Setting up libpam-smbpass (2:3.6.3-2ubuntu2.6) ...
Log ended: 2013-06-10  14:45:03

Log started: 2013-06-10  15:46:51
Selecting previously unselected package libwxbase2.8-0.
(Reading database ... 214254 files and directories currently installed.)
Unpacking libwxbase2.8-0 (from .../libwxbase2.8-0_2.8.12.1-6ubuntu2_amd64.deb) ...
Selecting previously unselected package libwxgtk2.8-0.
Unpacking libwxgtk2.8-0 (from .../libwxgtk2.8-0_2.8.12.1-6ubuntu2_amd64.deb) ...
Selecting previously unselected package python-wxversion.
Unpacking python-wxversion (from .../python-wxversion_2.8.12.1-6ubuntu2_all.deb) ...
Selecting previously unselected package python-wxgtk2.8.
Unpacking python-wxgtk2.8 (from .../python-wxgtk2.8_2.8.12.1-6ubuntu2_amd64.deb) ...
Selecting previously unselected package mesa-utils.
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_amd64.deb) ...
Selecting previously unselected package playonlinux.
Unpacking playonlinux (from .../playonlinux_4.0.14-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up libwxbase2.8-0 (2.8.12.1-6ubuntu2) ...
Setting up libwxgtk2.8-0 (2.8.12.1-6ubuntu2) ...
Setting up python-wxversion (2.8.12.1-6ubuntu2) ...
Setting up python-wxgtk2.8 (2.8.12.1-6ubuntu2) ...
update-alternatives: using /usr/lib/wx/python/wx2.8.pth to provide /usr/lib/wx/python/wx.pth (wx.pth) in auto mode.
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
Setting up playonlinux (4.0.14-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Log ended: 2013-06-10  15:47:06

Log started: 2013-06-10  15:56:08
Vormals nicht ausgewähltes Paket p7zip-full wird gewählt.
(Lese Datenbank ... 215722 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von p7zip-full (aus .../p7zip-full_9.20.1~dfsg.1-4_amd64.deb) ...
Vorbereitung zum Ersetzen von playonlinux 4.0.14-1 (durch .../playonlinux_4.2.1_all.deb) ...
Ersatz für playonlinux wird entpackt ...
Trigger für man-db werden verarbeitet ...
Trigger für bamfdaemon werden verarbeitet ...
Rebuilding /usr/share/applications/bamf.index...
Trigger für desktop-file-utils werden verarbeitet ...
Trigger für gnome-menus werden verarbeitet ...
Trigger für gconf2 werden verarbeitet ...
p7zip-full (9.20.1~dfsg.1-4) wird eingerichtet ...
playonlinux (4.2.1) wird eingerichtet ...
gconf-schemas is /usr/sbin/gconf-schemas
Log ended: 2013-06-10  15:56:19

Log started: 2013-06-10  15:57:14
(Reading database ... 216008 files and directories currently installed.)
Removing playonlinux ...
Processing triggers for gconf2 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Log ended: 2013-06-10  15:57:20

Log started: 2013-06-10  15:59:10
Vormals nicht ausgewähltes Paket playonlinux wird gewählt.
(Lese Datenbank ... 215462 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von playonlinux (aus .../playonlinux_4.2.1_all.deb) ...
Trigger für man-db werden verarbeitet ...
Trigger für bamfdaemon werden verarbeitet ...
Rebuilding /usr/share/applications/bamf.index...
Trigger für desktop-file-utils werden verarbeitet ...
Trigger für gnome-menus werden verarbeitet ...
Trigger für gconf2 werden verarbeitet ...
playonlinux (4.2.1) wird eingerichtet ...
gconf-schemas is /usr/sbin/gconf-schemas
Log ended: 2013-06-10  15:59:18

Log started: 2013-06-10  16:00:15
(Reading database ... 216008 files and directories currently installed.)
Removing playonlinux ...
Processing triggers for gconf2 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Log ended: 2013-06-10  16:00:21

Log started: 2013-06-10  17:23:42
Vormals nicht ausgewähltes Paket libasyncns0:i386 wird gewählt.
(Lese Datenbank ... 215462 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von libasyncns0:i386 (aus .../libasyncns0_0.8-4_i386.deb) ...
Vormals nicht ausgewähltes Paket libogg0:i386 wird gewählt.
Entpacken von libogg0:i386 (aus .../libogg0_1.2.2~dfsg-1ubuntu1_i386.deb) ...
Vormals nicht ausgewähltes Paket libflac8:i386 wird gewählt.
Entpacken von libflac8:i386 (aus .../libflac8_1.2.1-6_i386.deb) ...
Vormals nicht ausgewähltes Paket libsamplerate0:i386 wird gewählt.
Entpacken von libsamplerate0:i386 (aus .../libsamplerate0_0.1.8-4_i386.deb) ...
Vormals nicht ausgewähltes Paket libjack-jackd2-0:i386 wird gewählt.
Entpacken von libjack-jackd2-0:i386 (aus .../libjack-jackd2-0_1.9.8~dfsg.1-1ubuntu2_i386.deb) ...
Vormals nicht ausgewähltes Paket libjson0:i386 wird gewählt.
Entpacken von libjson0:i386 (aus .../libjson0_0.9-1ubuntu1_i386.deb) ...
Vormals nicht ausgewähltes Paket libvorbis0a:i386 wird gewählt.
Entpacken von libvorbis0a:i386 (aus .../libvorbis0a_1.3.2-1ubuntu3_i386.deb) ...
Vormals nicht ausgewähltes Paket libvorbisenc2:i386 wird gewählt.
Entpacken von libvorbisenc2:i386 (aus .../libvorbisenc2_1.3.2-1ubuntu3_i386.deb) ...
Vormals nicht ausgewähltes Paket libsndfile1:i386 wird gewählt.
Entpacken von libsndfile1:i386 (aus .../libsndfile1_1.0.25-4_i386.deb) ...
Vormals nicht ausgewähltes Paket libwrap0:i386 wird gewählt.
Entpacken von libwrap0:i386 (aus .../libwrap0_7.6.q-21_i386.deb) ...
Vormals nicht ausgewähltes Paket libpulse0:i386 wird gewählt.
Entpacken von libpulse0:i386 (aus .../libpulse0_1%3a2.0-0ubuntu1~precise2_i386.deb) ...
Vormals nicht ausgewähltes Paket libspeexdsp1:i386 wird gewählt.
Entpacken von libspeexdsp1:i386 (aus .../libspeexdsp1_1.2~rc1-3ubuntu2_i386.deb) ...
Vorbereitung zum Ersetzen von wine1.4-i386:i386 1.4-0ubuntu4.1 (durch .../wine1.4-i386_1.4.1-0ubuntu1~precise1~ppa4_i386.deb) ...
Ersatz für wine1.4-i386:i386 wird entpackt ...
Vorbereitung zum Ersetzen von wine1.4-common 1.4-0ubuntu4.1 (durch .../wine1.4-common_1.4.1-0ubuntu1~precise1~ppa4_all.deb) ...
Ersatz für wine1.4-common wird entpackt ...
Vorbereitung zum Ersetzen von wine1.4 1.4-0ubuntu4.1 (durch .../wine1.4_1.4.1-0ubuntu1~precise1~ppa4_amd64.deb) ...
Ersatz für wine1.4 wird entpackt ...
Vorbereitung zum Ersetzen von wine1.4-amd64 1.4-0ubuntu4.1 (durch .../wine1.4-amd64_1.4.1-0ubuntu1~precise1~ppa4_amd64.deb) ...
Ersatz für wine1.4-amd64 wird entpackt ...
Vorbereitung zum Ersetzen von winetricks 0.0+20120308 (durch .../winetricks_0.0+20120912~precise1~ppa1_amd64.deb) ...
Ersatz für winetricks wird entpackt ...
Vormals nicht ausgewähltes Paket libasound2-plugins:i386 wird gewählt.
Entpacken von libasound2-plugins:i386 (aus .../libasound2-plugins_1.0.25-1ubuntu1_i386.deb) ...
Trigger für man-db werden verarbeitet ...
Trigger für hicolor-icon-theme werden verarbeitet ...
Trigger für bamfdaemon werden verarbeitet ...
Rebuilding /usr/share/applications/bamf.index...
Trigger für desktop-file-utils werden verarbeitet ...
Trigger für gnome-menus werden verarbeitet ...
libasyncns0:i386 (0.8-4) wird eingerichtet ...
libogg0:i386 (1.2.2~dfsg-1ubuntu1) wird eingerichtet ...
libflac8:i386 (1.2.1-6) wird eingerichtet ...
libsamplerate0:i386 (0.1.8-4) wird eingerichtet ...
libjack-jackd2-0:i386 (1.9.8~dfsg.1-1ubuntu2) wird eingerichtet ...
libjson0:i386 (0.9-1ubuntu1) wird eingerichtet ...
libvorbis0a:i386 (1.3.2-1ubuntu3) wird eingerichtet ...
libvorbisenc2:i386 (1.3.2-1ubuntu3) wird eingerichtet ...
libsndfile1:i386 (1.0.25-4) wird eingerichtet ...
libwrap0:i386 (7.6.q-21) wird eingerichtet ...
libpulse0:i386 (1:2.0-0ubuntu1~precise2) wird eingerichtet ...
libspeexdsp1:i386 (1.2~rc1-3ubuntu2) wird eingerichtet ...
winetricks (0.0+20120912~precise1~ppa1) wird eingerichtet ...
libasound2-plugins:i386 (1.0.25-1ubuntu1) wird eingerichtet ...
wine1.4-common (1.4.1-0ubuntu1~precise1~ppa4) wird eingerichtet ...
wine1.4-amd64 (1.4.1-0ubuntu1~precise1~ppa4) wird eingerichtet ...
wine1.4-i386:i386 (1.4.1-0ubuntu1~precise1~ppa4) wird eingerichtet ...
wine1.4 (1.4.1-0ubuntu1~precise1~ppa4) wird eingerichtet ...
Trigger für libc-bin werden verarbeitet ...
ldconfig deferred processing now taking place
Log ended: 2013-06-10  17:24:09

Log started: 2013-06-11  01:02:35
Vormals nicht ausgewähltes Paket playonlinux wird gewählt.
(Lese Datenbank ... 215514 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von playonlinux (aus .../playonlinux_4.2.1_all.deb) ...
Trigger für man-db werden verarbeitet ...
Trigger für bamfdaemon werden verarbeitet ...
Rebuilding /usr/share/applications/bamf.index...
Trigger für desktop-file-utils werden verarbeitet ...
Trigger für gnome-menus werden verarbeitet ...
Trigger für gconf2 werden verarbeitet ...
playonlinux (4.2.1) wird eingerichtet ...
gconf-schemas is /usr/sbin/gconf-schemas
Log ended: 2013-06-11  01:02:42

Log started: 2013-06-11  01:08:42
(Lese Datenbank ... 216061 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von xserver-xorg-video-openchrome 1:0.2.904+svn1050-1 (durch .../xserver-xorg-video-openchrome_1%3a0.2.904+svn1050-1ubuntu0.1_amd64.deb) ...
Ersatz für xserver-xorg-video-openchrome wird entpackt ...
Trigger für man-db werden verarbeitet ...
xserver-xorg-video-openchrome (1:0.2.904+svn1050-1ubuntu0.1) wird eingerichtet ...
Trigger für libc-bin werden verarbeitet ...
ldconfig deferred processing now taking place
Log ended: 2013-06-11  01:08:46

Log started: 2013-06-11  01:11:05
Vormals nicht ausgewähltes Paket curl wird gewählt.
(Lese Datenbank ... 216061 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von curl (aus .../curl_7.22.0-3ubuntu4.1_amd64.deb) ...
Trigger für man-db werden verarbeitet ...
curl (7.22.0-3ubuntu4.1) wird eingerichtet ...
Log ended: 2013-06-11  01:11:08

Log started: 2013-06-12  00:11:58
Vormals nicht ausgewähltes Paket gir1.2-gtop-2.0 wird gewählt.
(Lese Datenbank ... 216077 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von gir1.2-gtop-2.0 (aus .../gir1.2-gtop-2.0_2.28.4-2_amd64.deb) ...
Vormals nicht ausgewähltes Paket gnome-shell-extensions wird gewählt.
Entpacken von gnome-shell-extensions (aus .../gnome-shell-extensions_3.4.1~git20120508.dfd7191a-0ubuntu1~12.04~ricotz0_all.deb) ...
Vormals nicht ausgewähltes Paket gnome-shell-extensions-common wird gewählt.
Entpacken von gnome-shell-extensions-common (aus .../gnome-shell-extensions-common_3.4.1~git20120508.dfd7191a-0ubuntu1~12.04~ricotz0_all.deb) ...
Trigger für libglib2.0-0:i386 werden verarbeitet ...
Trigger für libglib2.0-0 werden verarbeitet ...
gir1.2-gtop-2.0 (2.28.4-2) wird eingerichtet ...
gnome-shell-extensions (3.4.1~git20120508.dfd7191a-0ubuntu1~12.04~ricotz0) wird eingerichtet ...
gnome-shell-extensions-common (3.4.1~git20120508.dfd7191a-0ubuntu1~12.04~ricotz0) wird eingerichtet ...
Log ended: 2013-06-12  00:12:05

Log started: 2013-06-12  14:36:06
Vormals nicht ausgewähltes Paket libatm1 wird gewählt.
(Lese Datenbank ... 216208 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von libatm1 (aus .../libatm1_1%3a2.5.1-1.3_amd64.deb) ...
Vormals nicht ausgewähltes Paket iproute-doc wird gewählt.
Entpacken von iproute-doc (aus .../iproute-doc_20111117-1ubuntu2_all.deb) ...
libatm1 (1:2.5.1-1.3) wird eingerichtet ...
iproute-doc (20111117-1ubuntu2) wird eingerichtet ...
Trigger für libc-bin werden verarbeitet ...
ldconfig deferred processing now taking place
Log ended: 2013-06-12  14:36:12



[COLOR=#0000cd]**Soundcard: **[/COLOR]

sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Sound modules installed: 

/lib/modules/3.2.0-45-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/snd.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.2.0-45-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.2.0-45-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.2.0-45-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.2.0-45-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.2.0-45-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.2.0-45-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/3.2.0-45-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.2.0-45-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.2.0-45-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.2.0-45-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm2000.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8985.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-da7210.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm9090.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-adav80x.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-max9850.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm5100.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8782.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8991.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-max98095.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm1250-ev1.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8995.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-ad193x.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic32x4.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-cx20442.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-ak4641.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8955.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-dfbmcs320.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-max98088.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8996.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wl1273.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8727.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8994.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-sta32x.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8983.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-ak4671.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-adau1373.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-88pm860x.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-lm4857.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-ads117x.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-jz4740-codec.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/3.2.0-45-generic/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/3.2.0-45-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.2.0-45-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/3.2.0-45-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.2.0-45-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.2.0-45-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.2.0-45-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.2.0-45-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.2.0-45-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.2.0-45-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.2.0-45-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.2.0-45-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.2.0-45-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.2.0-45-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.2.0-45-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.2.0-45-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko



**[COLOR=#0000ff]Soundcard Physically installed:[/COLOR]**

    Subsystem: Dell Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at f1c00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

**[COLOR=#0000cd]PCI Devices:[/COLOR]**

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Dell Device 050e
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0000000-f10fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 54
    Memory at f1400000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Dell Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at f1c05000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Device 050e
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f1c0a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: Dell Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at f1c00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f1b00000-f1bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: f1a00000-f1afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Memory behind bridge: f1900000-f19fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 00000000f1800000-00000000f18fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Device 050e
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f1c09000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
    Subsystem: Dell Device 050e
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 050e
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at f1c08000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Dell Device 050e
    Flags: medium devsel, IRQ 10
    Memory at f1c04000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff) (prog-if ff)
    !!! Unknown header type 7f

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at f1b00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Dell Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f1a00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Dell Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 50
    I/O ports at 2000 [size=256]
    Memory at f1804000 (64-bit, prefetchable) [size=4K]
    Memory at f1800000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169
```



Hope that'll help?! could not add a smiley, but i would

---

### Post by zero2xiii on 2013-06-12
Hay,

Can you please read that link again and format your reply properly, this is REALLY hard to read and follow....

> _**First things first:**_
Posting any output from a command should be in code brackets. The brackets are added to a post at the current cursor position by clicking the # sign at the top of a post sections. This should generate tags that look like this:
[CODE ][/CODE ]
Only without the spaces.
Put all the output generated by a command inside like so:
[CODE ]Here is some sample output[/CODE ]

It is useful to put the output of each command seperately such as:
ls
```
Some ls output
```
some other command
```
Some more output
```
This help us greatly when referencing back and forth.


Thanks

EDIT:

Just saw a admin added it for you, Thanks admin! :)

EDIT 2:
I have gone through all that, and honestly I see NO reason why your sound would not work, and freeze the system... Try going into terminal and running "alsamixer" and make sure all volumes are set correctly.

Maybe some one else can see something I missed...

---

