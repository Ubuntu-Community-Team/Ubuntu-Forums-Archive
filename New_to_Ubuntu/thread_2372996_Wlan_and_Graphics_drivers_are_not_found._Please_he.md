---
title: "Wlan and Graphics drivers are not found. Please help"
date: 2017-10-01
forum: New to Ubuntu
---

### Post by fly2sbn on 2017-10-01
I have an HP laptop with windows, I would like to switch to ubuntu permanently (which I already did several times with this laptop). The only two things prevent me from doing so are
1. I cant find a driver for my network card - realtek RTL8723BE 802.11 b/g/n wi-fi adapter.
2.Cant find a driver for my display adapter -  AMD Radeon R5 M330

Can anyone help me ? Thanks in advance.

---

### Post by ian-weisser on 2017-10-01
What did you use last time(s)?

Does the LiveUSB work?

---

### Post by fly2sbn on 2017-10-01
I tried ubuntu, mint, mate, fedora. Nothing works.

---

### Post by jeremy31 on 2017-10-01
What model HP is this?  It must boot up Ubuntu.  What version are you trying?

---

### Post by fly2sbn on 2017-10-01
Its booting up and all works fine. Exept wifi and graphics card. I tried ubuntu 16.04 and 17.04.

---

### Post by jeremy31 on 2017-10-01
Some HP computers with RTL8723BE wifi cards are known to use only one antenna wire, in terminal try this
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|level'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|level'
```

If there is a big difference in wireless access points found with the iwlist scan command depending on the ant_sel setting you have a card with one antenna and it can be fixed

---

### Post by fly2sbn on 2017-10-01
Thanks bro.. awsome.. that works for wifi. Can coin out something for my graphics driver ?

---

### Post by jeremy31 on 2017-10-01
I only have Intel graphics and don't know the normal fixes for AMD Radeon.  If you do install Ubuntu you will want to do
```
echo "options rtl8723be ant_sel=X" | sudo tee /etc/modprobe.d/rtlopts.conf
```
Replace X with the value that worked best in the test and then it will use the right antenna automatically after boot

---

### Post by mastablasta on 2017-10-02
do you have dual graphics? intel+AMD?

in fact this might be the time when you post the result of:
```
sudo lshw -sanitize
```

and wrap it in the code tags (the # icon in forums advanced answer.

alternatively you can output your hardware setup to a file in various GUI hardware managers and then attach the file here or post it on pastebin.

---

### Post by fly2sbn on 2017-10-02
> **mastablasta said:**
> do you have dual graphics? intel+AMD?

in fact this might be the time when you post the result of:
```
sudo lshw -sanitize
```

and wrap it in the code tags (the # icon in forums advanced answer.

alternatively you can output your hardware setup to a file in various GUI hardware managers and then attach the file here or post it on pastebin.


```
880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
          serial: [REMOVED]
          slot: U3E1
          size: 685MHz
          capacity: 2800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 8
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: 5
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M471B5674EB0-YK0
             vendor: Samsung
             physical id: 0
             serial: [REMOVED]
             slot: Bottom-slot 1(top)
             size: 2GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HP687515-H66-MCN
             vendor: Kingston
             physical id: 1
             serial: [REMOVED]
             slot: Bottom-slot 2(under)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Skylake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: HD Graphics 520
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:125 memory:a0000000-a0ffffff memory:90000000-9fffffff ioport:6000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Skylake Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 08
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:a1420000-a1427fff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:122 memory:a1400000-a140ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.10.0-35-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.10
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB OPTICAL MOUSE
                   vendor: Trust International B.V.
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:1
                   description: Generic USB device
                   product: 802.11n NIC
                   vendor: Realtek
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.00
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=r8188eu maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   product: Bluetooth Radio
                   vendor: Realtek
                   physical id: 4
                   bus info: usb@1:4
                   version: 2.00
                   serial: [REMOVED]
                   capabilities: bluetooth usb-2.10
                   configuration: driver=btusb maxpower=500mA speed=12Mbit/s
              *-usb:3
                   description: Video
                   product: HP Truevision HD
                   vendor: Generic
                   physical id: 5
                   bus info: usb@1:5
                   version: 19.17
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:4
                   description: Mass storage device
                   product: USB2.0-CRW
                   vendor: Generic
                   physical id: 7
                   bus info: usb@1:7
                   logical name: scsi2
                   version: 77.11
                   serial: [REMOVED]
                   capabilities: usb-2.01 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: SD/MMC/MS PRO
                      vendor: Generic-
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdb
                      version: 1.00
                      serial: [REMOVED]
                      size: 14GiB (15GB)
                      capabilities: removable
                      configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sdb
                         size: 14GiB (15GB)
                         capabilities: partitioned partitioned:dos
                         configuration: signature=0270e294
                       *-volume
                            description: Windows FAT volume
                            vendor: SYSLINUX
                            physical id: 1
                            logical name: /dev/sdb1
                            logical name: /media/subin/49EC-B435
                            version: FAT32
                            serial: [REMOVED]
                            size: 14GiB
                            capacity: 14GiB
                            capabilities: primary bootable fat initialized
                            configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.10.0-35-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.10
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:1
             description: Signal processing controller
             product: Sunrise Point-LP Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:a1432000-a1432fff
        *-communication
             description: Communication controller
             product: Sunrise Point-LP CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:127 memory:a1433000-a1433fff
        *-storage
             description: SATA controller
             product: Sunrise Point-LP SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:123 memory:a1430000-a1431fff memory:a1436000-a14360ff ioport:6080(size=8) ioport:6088(size=4) ioport:6060(size=32) memory:a1434000-a14347ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:5000(size=4096) memory:a1300000-a13fffff ioport:80000000(size=268435456)
           *-display
                description: Display controller
                product: Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 83
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:126 memory:80000000-8fffffff memory:a1300000-a133ffff ioport:5000(size=256) memory:a1340000-a135ffff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:4000(size=4096) memory:a1200000-a12fffff ioport:a1000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 07
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:124 ioport:4000(size=256) memory:a1200000-a1200fff memory:a1000000-a1003fff
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:a1100000-a11fffff
           *-network
                description: Wireless interface
                product: RTL8723BE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 00
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8723be driverversion=4.10.0-35-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:17 ioport:3000(size=256) memory:a1100000-a1103fff
        *-isa
             description: ISA bridge
             product: Sunrise Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory
             description: Memory controller
             product: Sunrise Point-LP PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: driver=intel_pmc_core latency=0
             resources: irq:0 memory:a142c000-a142ffff
        *-multimedia
             description: Audio device
             product: Sunrise Point-LP HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:128 memory:a1428000-a142bfff memory:a1410000-a141ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-LP SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:a1435000-a14350ff ioport:6040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10JPVX-60J
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A01
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=7cd416bc-5e24-411f-9ebc-6e84d4ecc4c9 logicalsectorsize=512 sectorsize=4096
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: [REMOVED]
                size: 474MiB
                capacity: 475MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 219GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2017-10-01 22:13:26 filesystem=ext4 lastmountpoint=/ modified=2017-10-02 13:36:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-10-02 13:36:36 state=mounted
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                logical name: /mnt/065676EE5676DE3D
                version: 3.1
                serial: [REMOVED]
                size: 711GiB
                capacity: 711GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2017-09-22 11:07:32 filesystem=ntfs label=New Volume mount.fstype=fuseblk mount.options=ro,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 name=Basic data partition state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW GUD1N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: MD00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: HS04041
       vendor: 131-42-6E
       physical id: 1
       version: 0
       serial: [REMOVED]
       slot: Primary
       capacity: 41610mWh
       configuration: voltage=14.6V
  *-power UNCLAIMED
       description: OEM Define 1
       product: OEM Define 5
       vendor: OEM Define 2
       physical id: 2
       version: OEM Define 6
       serial: [REMOVED]
       capacity: 75mWh
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@1:3
       logical name: wlxc4e984171096
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu ip=[REMOVED] multicast=yes wireless=IEEE 802.11bgn
subin@subin-HP-Notebook:~$ 


```

---

### Post by mastablasta on 2017-10-03
based on this: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)

you should benefit form latest kernel (so install 17.04 or 16.04 with latest kernel); i recomend 16.04 because...

...you might need to install the amdgpu-PRO driver: [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx)

for swtiching GPU chips (you have intel and AMD) read more here (and links in answer): [https://askubuntu.com/questions/760879/amdgpu-with-hybrid-graphics-16-04](https://askubuntu.com/questions/760879/amdgpu-with-hybrid-graphics-16-04)

i am not sure how it is now, but the pro version might have some other method (maybe even a GUI?!).

---

### Post by genericvii143 on 2017-10-06
Yes, i had the same issues and I end up buying this: 

[https://www.amazon.com/Panda-300Mbps-Wireless-USB-Adapter/dp/B00EQT0YK2/ref=sr_1_2?ie=UTF8&qid=1506871300&sr=8-2&keywords=panda+wifi+usb+adapter](https://www.amazon.com/Panda-300Mbps-Wireless-USB-Adapter/dp/B00EQT0YK2/ref=sr_1_2?ie=UTF8&qid=1506871300&sr=8-2&keywords=panda+wifi+usb+adapter)  

All you need to do is the plug it in your laptop no drivers need it. it works perfect.

---

