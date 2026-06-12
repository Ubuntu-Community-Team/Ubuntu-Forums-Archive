---
title: "[SOLVED] Need help regarding sound"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by halovivek on 2008-11-25
hi
i have searched command to show all the devices in my computer and i got this. i could not hear any sound from my system.
below i have given:-
halovivek@halovivek-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Unknown device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
06:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)

----------
Processor :- AMD Turion RM70 64 bit
Memory:- 4 GB (2x2) RAM DDR2 667 MHz
Hard Drive:- 320GB
Graphics Card :- ATI HD3200
video card:-  HDMI, VGA
Screen :- 15.4  WXGA
Sound card :- HD Audio
Optical drive:-  DVD +-RW DL
PC-card-express-Mini No / Yes / Yes
Wlan-Network-Bluetoo 11g/10-1000/No
USB-Firewire-Modem 4/No/No
web cam:- Built in- crystal clear
Operating system:-  Vista ultimate 64 bit, ubuntu 8.10 and kubuntu 8.10
Weight:-  2,9 kg ( too Heavy)
--------------------------
please help me to install sound. i have started using ubuntu for all. if sound also comes i will love to hear songs and movies also.

---

### Post by diablo75 on 2008-11-25
Have you installed all available updates since installing Ubuntu?  (System>Administration>Update Manager>Check For Updates).

If so, check System>Administration>Hardware Drivers to see if any are available that need to be enabled.

---

### Post by halovivek on 2008-11-25
yes i have done all the updates also. but till now no sound output

---

### Post by diablo75 on 2008-11-25
Eeek, this sounds like it's going to be a tad bit tricky.  Someone other than myself will have to take a shot at this one; I can't help you.  Be patient, a solution may be around the corner with the next reply.  I'll be watching this thread to see what happens.  Good luck!

---

### Post by kostkon on 2008-11-25
Please, open a terminal, give the following command
```
aplay -l
```
and paste the output here.

---

### Post by nhasian on 2008-11-25
my post here may help you:

[http://ubuntuforums.org/showpost.php?p=6205010&postcount=4](http://ubuntuforums.org/showpost.php?p=6205010&postcount=4)

---

### Post by ndefontenay on 2008-11-25
also

```
sudo lshw
```

will give you a list of all your hardware. 
If your sound works it will be listed.

---

### Post by halovivek on 2008-11-25
hi i have run the command and it displayed this one. please help
root@halovivek-laptop:/home/halovivek# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@halovivek-laptop:/home/halovivek# sudo lshw
halovivek-laptop
    description: Notebook
    product: Aspire 5530
    vendor: Acer
    version: V1.06
    serial: LXAPV0X07183009B961601
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=1 uuid=66373764-3365-3635-6261-001EEC4BE0F7
  *-core
       description: Motherboard
       product: Cinder Cone
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXAPV0X07183009B961601
       slot: ATI RS780MN
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.06 (06/27/2008)
          size: 115KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) X2 Dual-Core Mobile RM-70
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.3.1
          slot: Socket S1G2
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: S1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: S2
             size: 2GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: Acer Incorporated [ALI]
             vendor: Acer Incorporated [ALI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth1
                version: 01
                serial: 00:1f:e2:ae:88:cc
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5764M Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 10
                serial: 00:1e:ec:4b:e0:f7
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=82.182.221.135 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
        *-pci:4
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 4)
             vendor: Advanced Micro Devices [AMD]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXH408609065
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6cabdd5d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 02b5da3e-3c3e-1444-8fd3-557bd5303560
                   size: 79GiB
                   capacity: 79GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-05-23 12:01:27 filesystem=ntfs label=ACER state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 218GiB
                   capacity: 218GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 39GiB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 39GiB
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 69GiB
                 *-logicalvolume:3
                      description: HPFS/NTFS partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 34GiB
                 *-logicalvolume:4
                      description: Linux filesystem partition
                      physical id: 9
                      logical name: /dev/sda9
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 25GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:5
                      description: Linux swap / Solaris partition
                      physical id: a
                      logical name: /dev/sda10
                      capacity: 9538MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DS8A2S
                vendor: Slimtype
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 6A11
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB700/SB800 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB700/SB800 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:5
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: Family 11h HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 11h DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 11h Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
root@halovivek-laptop:/home/halovivek#

---

### Post by halovivek on 2008-11-26
hallo please help . i have posted what you requested.

---

### Post by halovivek on 2008-11-26
i have followed the pulse audio and i am posting the results.
till now no sound
halovivek@halovivek-laptop:~$ sudo su
[sudo] password for halovivek:
root@halovivek-laptop:/home/halovivek# $ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
bash: $: command not found
root@halovivek-laptop:/home/halovivek# $ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
bash: $: command not found
root@halovivek-laptop:/home/halovivek# mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
cp: cannot stat `/root/.pulse': No such file or directory
cp: cannot stat `/root/.asound*': No such file or directory
cp: cannot stat `/etc/asound.conf': No such file or directory
root@halovivek-laptop:/home/halovivek# sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
padevchooser is already the newest version.
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libsdl1.2debian-alsa
The following NEW packages will be installed:
  libao-pulse libasound2-plugins libsdl1.2debian-pulseaudio
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 327kB of archives.
After this operation, 594kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/universe libao-pulse 0.9.3-1 [7428B]
Get:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/main libasound2-plugins 1.0.15-1ubuntu3 [117kB]
Get:3 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/universe libsdl1.2debian-pulseaudio 1.2.13-1ubuntu1 [203kB]
Fetched 327kB in 0s (975kB/s)
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-1ubuntu1) | libsdl1.2debian-all (= 1.2.13-1ubuntu1) | libsdl1.2debian-esd (= 1.2.13-1ubuntu1) | libsdl1.2debian-arts (= 1.2.13-1ubuntu1) | libsdl1.2debian-oss (= 1.2.13-1ubuntu1) | libsdl1.2debian-nas (= 1.2.13-1ubuntu1) | libsdl1.2debian-pulseaudio (= 1.2.13-1ubuntu1); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-arts is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... 156668 files and directories currently installed.)
Removing libsdl1.2debian-alsa ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libao-pulse.
(Reading database ... 156660 files and directories currently installed.)
Unpacking libao-pulse (from .../libao-pulse_0.9.3-1_amd64.deb) ...
Replaced by files in installed package libao2 ...
Selecting previously deselected package libasound2-plugins.
Unpacking libasound2-plugins (from .../libasound2-plugins_1.0.15-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libsdl1.2debian-pulseaudio.
Unpacking libsdl1.2debian-pulseaudio (from .../libsdl1.2debian-pulseaudio_1.2.13-1ubuntu1_amd64.deb) ...
Setting up libao-pulse (0.9.3-1) ...
Setting up libasound2-plugins (1.0.15-1ubuntu3) ...
Setting up libsdl1.2debian-pulseaudio (1.2.13-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

root@halovivek-laptop:/home/halovivek# sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libflashsupport is not installed, so not removed
E: Couldn't find package flashplugin-nonfree-extrasound

root@halovivek-laptop:/home/halovivek# pulseaudio & pavucontrol
W: main.c: This program is not intended to be run as root (unless --system is specified).
[1] 7673
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

(pavucontrol:7674): Gtk-CRITICAL **: gtk_widget_get_clipboard: assertion `gtk_widget_has_screen (widget)' failed

(pavucontrol:7674): Gtk-CRITICAL **: gtk_clipboard_set_with_owner: assertion `clipboard != NULL' failed

root@halovivek-laptop:/home/halovivek# sudo apt-get update && sudo apt-get dist-upgrade
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy Release.gpg
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports Release
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/universe Sources
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/main Packages
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1300B]
Ign [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Get:5 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [966B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages [5161B]
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources [1237B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources
Fetched 36.5kB in 3s (11.5kB/s)
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom tomake this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

root@halovivek-laptop:/home/halovivek# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by darksideforge on 2008-11-28
> **kostkon said:**
> Please, open a terminal, give the following command
```
aplay -l
```
and paste the output here.



Response:

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Also, under lshw:
```

cs Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```



Still no sound :(

---

### Post by halitech on 2008-11-28
this might be taken as a dumb question but please don't take offense. Have you checked to make sure the speakers/headphones are plugged in to the right socket and they are turned on?

---

### Post by darksideforge on 2008-11-28
> **halitech said:**
> this might be taken as a dumb question but please don't take offense. Have you checked to make sure the speakers/headphones are plugged in to the right socket and they are turned on?

No speakers or headphones at all. Waiting for sound through built-in/onboard speakers.

---

### Post by halitech on 2008-11-28
I missed that this was a laptop :(  just for curiousities sake, do you have a set of headphones to see if its directing it to the jack instead of using the builtin speakers?

---

### Post by markbuntu on 2008-11-28
Try these links below, most likely you need to add the option hda_intel = acer or something like that but anyway something in there will tell you exactly how to do that:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If you need more help, go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by darksideforge on 2008-11-29
> **halitech said:**
> I missed that this was a laptop :(  just for curiousities sake, do you have a set of headphones to see if its directing it to the jack instead of using the builtin speakers?

I used to have a pair of cheap headphones around but I can't find them. I have downloaded and updated with all relevant ALSA drivers/lib/util but still don't have sound. Hmm...then again, I haven't re-booted yet so I'll go try that.

---

### Post by halitech on 2008-11-29
try the reboot and see if you can find something to plug into the speaker jack and see if you have sound there. I'm almost thinking its sending sound there as everything seems to be recognized properly.

---

### Post by darksideforge on 2008-11-29
> **halitech said:**
> try the reboot and see if you can find something to plug into the speaker jack and see if you have sound there. I'm almost thinking its sending sound there as everything seems to be recognized properly.

Still no sound after the re-boot. I'll look around some more for the headphones.

---

### Post by darksideforge on 2008-11-29
After 45 minutes of searching, I still can't find any headphones. Nor are my external speakers here at this house. I'll go into town later today and try to find a cheap pair to buy or borrow.

---

### Post by halovivek on 2008-12-04
Till now i dont get any sound in the head phones. i got in system speakers and it is too low voice.

---

### Post by halovivek on 2008-12-29
hi 
i have solved the sound problem.
thanks

---

### Post by indecisive on 2008-12-29
I am having a similar problem.  So what did you do?

---

### Post by halovivek on 2008-12-29
> **indecisive said:**
> I am having a similar problem.  So what did you do?

using this threat i have solved the problem.
[http://ubuntuforums.org/showthread.php?t=1005416](http://ubuntuforums.org/showthread.php?t=1005416)

the solution is 
i have the code as below
Code:
sudo gedit /etc/modprobe.d/alsa-base
Add this to the end:

Code:
# added by myself
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

Reboot and it then works.

---

### Post by xero_alpha on 2009-01-06
> the solution is
i have the code as below
Code:
sudo gedit /etc/modprobe.d/alsa-base
Add this to the end:

Code:
# added by myself
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

Reboot and it then works.
Speakers and headphones work perfectly. Great post.

---

### Post by halovivek on 2009-01-07
> **xero_alpha said:**
> Speakers and headphones work perfectly. Great post.

so now you enjoy the work? with sound:)

---

