---
title: "Right mouse click does not work (Ubuntu 18.04.5.LTS)"
date: 2021-08-01
forum: New to Ubuntu
---

### Post by r2020r on 2021-08-01
**Problem**
From past two weeks I am facing these issues intermittently and only solution is reboot in Ubuntu 18.04.
1) R-mouse click and press does not work. 
2) Mouse click does not change the focus another window. Alt-TAB is needed.
3) Machine response becomes slow as if cpu has clogged.


[B]I have tried these
[/B]1) Disabled graphics card usage in Mozilla and Chrome
2) Tried both NVIDIA graphics driver and Ubuntu's opensource driver
3) Formatted the machine and installed 18.04 from scratch
4) I upgraded to 20.04 and same issue. (also wifi and audio did not work)
5) Changed the mouse, different USB ports

**Machine & OS**
1) Lenovo P50(Intel Xeon E3-1505M v5) @ 2.80Ghx QUADCore
2) RAM 24GB
3) Ubuntu 18.04.5.LTS ( tried ubuntu 20.04.1 also)

**Please help debug this.**
a) should I change over to KDE shell and try
b) are there any logs that i can post here for debug
c) My last option is to go back to Win10.

Thanks
Ramesh

---

### Post by r2020r on 2021-08-01
More info "uname -a" output

"afterwin-2020@afterwin2020:~$ uname -a
Linux afterwin2020 5.4.0-80-generic #90~18.04.1-Ubuntu SMP Tue Jul 13 19:40:02 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by mIk3_08 on 2021-08-01
Actually, we have the same Operating System Ubuntu 18.04.5.LTS But different hardware.
You have a powerful device one. It is very amazing. But that's a minor problem to switch back to 
another O.S. and I haven't encountered this kind of scenario maybe try another light weight desktop 
configuration that might solve your System Problem. Did you try some desktop like;
Xfce
Xubuntu 
Mate
Lubuntu
KDE Plasma 
Cinnamon 
LXQt 
If only I have same hardware as you do, I am sure I can debug it myself and show it to you 
how I did it. :-D

---

### Post by r2020r on 2021-08-01
Thanks mike_8

This problem started from last 15days. Before that everything was fine. Some update must have caused this.

I was planning to try KDE desktop. Last night I installed 18.0.5 Lts and took a backup using Clonezilla. I will restore that backup and install KDE. I really hope that works. 
Before this I will try memtest once.  

Regards

---

### Post by mIk3_08 on 2021-08-01
Kubuntu is one of the good looking for home and office desktop. 
Actually, there are a lot lightweight flavored Ubuntu out there that can be mixed up with your Ubuntu Operating System.
So, Its up to you which is best of your choice. [Click Here]("https://wiki.ubuntu.com/UbuntuFlavors") if you need more options and good luck.

---

### Post by ajgreeny on 2021-08-01
I wonder if the upgrade to the 5.4.0-80 from the previous version has caused this.

Assuming you have the previous kernel in the system try booting to that from grub.

---

### Post by ActionParsnip on 2021-08-01
If you use a USB mouse is it OK?

---

### Post by r2020r on 2021-08-01
> **ActionParsnip said:**
> If you use a USB mouse is it OK?
I am using wired mouse. I even changed the mouse too. Mouse works fine with other OS. 



> **ajgreeny said:**
> I wonder if the upgrade to the 5.4.0-80 from the previous version has caused this.

Assuming you have the previous kernel in the system try booting to that from grub.? 

Good idea. I read about Grub menu just now and will try. [B]I need one more help.
[/B]
PhysicalDisk1 had 18.04 and it exhibited mouse click problem. I removed PhysicalDisk1 to have a backup. Put PhysicalDisk2 in to machine and installed fresh copy of 18.05 LTS.
Both PhysicalDisk1 and PhysicalDisk2 exhibit same problem. To try out the old kernel, should I go back to PhysicalDisk1 or can select the old-kernel in PhysicalDisk2?
I hope my question is clear.


> **mIk3_08 said:**
> Kubuntu is one of the good looking for home and office desktop. 
Actually, there are a lot lightweight flavored Ubuntu out there that can be mixed up with your Ubuntu Operating System.
So, Its up to you which is best of your choice. [Click Here]("https://wiki.ubuntu.com/UbuntuFlavors") if you need more options and good luck
Thanks, I will try if older-kernel solution fail.

---

### Post by mIk3_08 on 2021-08-01
> **r2020r said:**
>  Good idea. I read about Grub menu just now and will try. [B]I need one more help.
[/B]PhysicalDisk1 had 18.04 and it exhibited mouse click problem. I removed PhysicalDisk1 to have a backup. Put PhysicalDisk2 in to machine and installed fresh copy of 18.05 LTS.
Both PhysicalDisk1 and PhysicalDisk2 exhibit same problem. To try out the old kernel, should I go back to PhysicalDisk1 or can select the old-kernel in PhysicalDisk2?
I hope my question is clear.
 Don't do this. I remind you; Linux is very different from Microsoft.
In my case, Here's my 
Operating System: Ubuntu 18.04.5 LTS
Kernel: Linux 5.4.0-80
And my system now is working well with no errors or etc. Have you installed neofetch in your system if you do try to run 
neofetch in your terminal and paste the result here in thread and wrap with code.
```
neofetch
```
Let me ask you something, where did you download your Ubuntu 18.04.5 LTS set-up iso copy?
and run this command;
```
sudo lshw
``` and this command ```
hostnamectl status
```
Also paste the result here in thread and wrap with code.

---

### Post by r2020r on 2021-08-01
> **ajgreeny said:**
>  wonder if the upgrade to the 5.4.0-80 from the previous version has caused this.
Assuming you have the previous kernel in the system try booting to that from grub. 
I downgraded to **5.4.0-42-generic** and that did not make any difference.


> **mIk3_08 said:**
>  if you do try to run 
neofetch in your terminal and paste the result here in thread and wrap with code.
```
neofetch
```
Let me ask you something, where did you download your Ubuntu 18.04.5 LTS set-up iso copy?
and run this command;
```
sudo lshw
``` and this command ```
hostnamectl status
```
Also paste the result here in thread and wrap with code.

Thank you very much mIk3_08. I think I downloaded the installer from standard site [https://releases.ubuntu.com/18.04.5/](https://releases.ubuntu.com/18.04.5/) I had downgraded the kernel for testing. But I had made the backup of original 18.0.5LTS installation with Nouveau driver. I restored it for the sake of getting this data. I think there are two graphics cards and also two audio cards. Not sure if I have disable one. Do not know how :-) 
```
afterwin-2020@afterwin2020:~$ sudo lshw
afterwin2020
    description: Notebook
    product: 20ENCTO1WW (LENOVO_MT_20EN_BU_Think_FM_ThinkPad P50)
    vendor: LENOVO
    version: ThinkPad P50
    serial: PC0K7E63
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: administrator_password=disabled chassis=notebook family=ThinkPad P50 power-on_password=disabled sku=LENOVO_MT_20EN_BU_Think_FM_ThinkPad P50 uuid=CCB3A54F-0C20-B211-A85C-982681808BB6
  *-core
       description: Motherboard
       product: 20ENCTO1WW
       vendor: LENOVO
       physical id: 0
       version: SDK0J40697 WIN
       serial: L1HF6CT00G3
       slot: Not Available
     *-cache:0
          description: L1 cache
          physical id: 3
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: 4
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          physical id: 5
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          physical id: 6
          slot: L3 Cache
          size: 8MiB
          capacity: 8MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
          vendor: Intel Corp.
          physical id: 7
          bus info: cpu@0
          version: Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
          serial: None
          slot: U3E1
          size: 3563MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 24GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: HMA81GS6AFR8N-UH
             vendor: SK Hynix
             physical id: 0
             serial: 2A4B6AFA
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: HMA81GS6AFR8N-UH
             vendor: SK Hynix
             physical id: 2
             serial: 28A99FBC
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:3
             description: SODIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: HMA81GS6AFR8N-UH
             vendor: SK Hynix
             physical id: 3
             serial: 92090795
             slot: ChannelB-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: e
          version: N1EET62W (1.35 )
          date: 11/10/2016
          size: 128KiB
          capacity: 15MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification uefi
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:4000(size=4096) memory:c3000000-c40fffff ioport:b0000000(size=301989888)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GM107GLM [Quadro M2000M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller cap_list
                configuration: latency=0
                resources: memory:c3000000-c3ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:4000(size=128) memory:c4080000-c40fffff
           *-multimedia
                description: Audio device
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:c4000000-c4003fff
        *-display
             description: VGA compatible controller
             product: HD Graphics P530
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:133 memory:c2000000-c2ffffff memory:60000000-6fffffff ioport:5000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:127 memory:c5720000-c572ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.4.0-80-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 63.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:1
                   description: Video
                   product: Integrated Camera
                   vendor: SunplusIT Inc
                   physical id: 8
                   bus info: usb@1:8
                   version: 0.12
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2 UNCLAIMED
                   description: Generic USB device
                   vendor: Validity Sensors, Inc.
                   physical id: 9
                   bus info: usb@1:9
                   version: 1.64
                   serial: 534e8cb91495
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=12Mbit/s
              *-usb:3 UNCLAIMED
                   description: Smart card reader
                   product: EMV Smartcard Reader
                   vendor: Generic
                   physical id: b
                   bus info: usb@1:b
                   version: 1.20
                   capabilities: usb-2.01
                   configuration: maxpower=50mA speed=12Mbit/s
              *-usb:4
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: e
                   bus info: usb@1:e
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.4.0-80-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.04
                capabilities: usb-3.00
                configuration: driver=hub slots=10 speed=5000Mbit/s
        *-generic
             description: Signal processing controller
             product: 100 Series/C230 Series Chipset Family Thermal Subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:19 memory:c574a000-c574afff
        *-communication:0
             description: Communication controller
             product: 100 Series/C230 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:131 memory:c574b000-c574bfff
        *-communication:1
             description: Serial controller
             product: 100 Series/C230 Series Chipset Family KT Redirection
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 31
             width: 32 bits
             clock: 66MHz
             capabilities: msi pm 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:19 ioport:5080(size=8) memory:c574f000-c574ffff
        *-storage
             description: SATA controller
             product: Q170/Q150/B150/H170/H110/Z170/CM236 Chipset SATA Controller [AHCI Mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 31
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:129 memory:c5748000-c5749fff memory:c574e000-c574e0ff ioport:5088(size=8) ioport:5090(size=4) ioport:5060(size=32) memory:c574c000-c574c7ff
        *-pci:1
             description: PCI bridge
             product: 100 Series/C230 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:3000(size=4096) memory:c4d00000-c56fffff ioport:c4100000(size=10485760)
        *-pci:2
             description: PCI bridge
             product: 100 Series/C230 Series Chipset Family PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:c4c00000-c4cfffff
           *-network
                description: Wireless interface
                product: Wireless 8260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlp4s0
                version: 3a
                serial: f4:8c:50:82:76:75
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-80-generic firmware=36.e91976c0.0 ip=192.168.0.124 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:132 memory:c4c00000-c4c01fff
        *-pci:3
             description: PCI bridge
             product: 100 Series/C230 Series Chipset Family PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 ioport:2000(size=4096) memory:94000000-aa0fffff ioport:70000000(size=570425344)
        *-pci:4
             description: PCI bridge
             product: 100 Series/C230 Series Chipset Family PCI Express Root Port #13
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:126 memory:c4b00000-c4bfffff
           *-generic
                description: Unassigned class
                product: RTS525A PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:3e:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:128 memory:c4b00000-c4b00fff
        *-isa
             description: ISA bridge
             product: CM236 Chipset LPC/eSPI Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: 100 Series/C230 Series Chipset Family Power Management Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 31
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:c5744000-c5747fff
        *-multimedia
             description: Audio device
             product: 100 Series/C230 Series Chipset Family HD Audio Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:134 memory:c5740000-c5743fff memory:c5730000-c573ffff
        *-serial UNCLAIMED
             description: SMBus
             product: 100 Series/C230 Series Chipset Family SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 31
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c574d000-c574d0ff ioport:efa0(size=32)
        *-network
             description: Ethernet interface
             product: Ethernet Connection (2) I219-LM
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: enp0s31f6
             version: 31
             serial: c8:5b:76:c3:54:e1
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.8-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:130 memory:c5700000-c571ffff
     *-scsi:0
          physical id: 0
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST2000LM015-2E81
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: SDM1
             serial: WDZ28ZAY
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=1a39cb3c-93b6-46d5-8356-2eb5b289e5a3 logicalsectorsize=512 sectorsize=4096
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/afterwin-2020/hdd2
                version: 1.0
                serial: 9b729b5b-ac94-4f2b-bf68-9586ae638aac
                size: 1863GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2019-12-21 23:25:13 filesystem=ext4 lastmountpoint=/home/partimag modified=2021-08-02 00:11:07 mount.fstype=ext4 mount.options=rw,relatime mounted=2021-08-02 00:11:07 name=P50data state=mounted
     *-scsi:1
          physical id: 1
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000LPVX-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 1A01
             serial: WD-WXE1A2561T6V
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=f52b813e
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: f9b5d85d-1026-40d3-90a8-33bdc726d5cc
                size: 465GiB
                capacity: 465GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2021-07-26 23:31:02 filesystem=ext4 lastmountpoint=/tmp/root_reinst.pbF79r modified=2021-08-02 00:10:42 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2021-08-02 00:09:05 state=mounted
```

```
afterwin-2020@afterwin2020:~$ neofetch
                                           afterwin-2020@afterwin2020 
        `:+ssssssssssssssssss+:`           -------------------------- 
      -+ssssssssssssssssssyyssss+-         OS: Ubuntu 18.04.5 LTS x86_64 
    .ossssssssssssssssssdMMMNysssso.       Host: 20ENCTO1WW ThinkPad P50 
   /ssssssssssshdmmNNmmyNMMMMhssssss/      Kernel: 5.4.0-80-generic 
  +ssssssssshmydMMMMMMMNddddyssssssss+     Uptime: 5 mins 
 /sssssssshNMMMyhhyyyyhmNMMMNhssssssss/    Packages: 2100 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Shell: bash 4.4.20 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Resolution: 1920x1080 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   DE: GNOME 3.28.4 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   WM: GNOME Shell 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   WM Theme: Adwaita 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Theme: Ambiance [GTK2/3] 
 /sssssssshNMMMyhhyyyyhdNMMMNhssssssss/    Icons: Ubuntu-mono-dark [GTK2/3] 
  +sssssssssdmydMMMMMMMMddddyssssssss+     Terminal: gnome-terminal 
   /ssssssssssshdmNNNNmyNMMMMhssssss/      CPU: Intel Xeon E3-1505M v5 (8) @ 3. 
    .ossssssssssssssssssdMMMNysssso.       GPU: NVIDIA Quadro M2000M 
      -+sssssssssssssssssyyyssss+-         GPU: Intel HD Graphics P530 
        `:+ssssssssssssssssss+:`           Memory: 1806MiB / 23439MiB 

```

```
afterwin-2020@afterwin2020:~$ hostnamectl status
   Static hostname: afterwin2020
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: e1a419450535417e8da980112fc95e22
           Boot ID: bb3500cd21714cc48fe461dc2a5a506b
  Operating System: Ubuntu 18.04.5 LTS
            Kernel: Linux 5.4.0-80-generic
      Architecture: x86-64
```

I installed KDE-plasma and removed Gnome for the sake of testing. KDE-plasma was hanging very badly.

Please let me know if you are able to figure out something.  

Regards

---

### Post by r2020r on 2021-08-01
I read Secure boot may lead to UNCLAIMED devices "lshw" output, so I providing following data.

No EFI folder
```
afterwin-2020@afterwin2020:/boot$ ls
config-5.3.0-1045-gke        memtest86+.elf
config-5.4.0-42-generic      memtest86+_multiboot.bin
config-5.4.0-80-generic      System.map-5.3.0-1045-gke
grub                         System.map-5.4.0-42-generic
initrd.img-5.3.0-1045-gke    System.map-5.4.0-80-generic
initrd.img-5.4.0-42-generic  vmlinuz-5.3.0-1045-gke
initrd.img-5.4.0-80-generic  vmlinuz-5.4.0-42-generic
memtest86+.bin               vmlinuz-5.4.0-80-generic

```

Secure boot command output
```
afterwin-2020@afterwin2020:~$ sudo mokutil --sb-state&#8203;
EFI variables are not supported on this system
```


```
afterwin-2020@afterwin2020:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0 243.9M  1 loop /snap/gnome-3-38-2004/39
loop1    7:1    0   2.2M  1 loop /snap/gnome-system-monitor/148
loop2    7:2    0   2.5M  1 loop /snap/gnome-calculator/884
loop3    7:3    0   956K  1 loop /snap/gnome-logs/100
loop4    7:4    0 255.6M  1 loop /snap/gnome-3-34-1804/36
loop5    7:5    0  65.1M  1 loop /snap/gtk-common-themes/1515
loop6    7:6    0   2.5M  1 loop /snap/gnome-system-monitor/163
loop7    7:7    0   219M  1 loop /snap/gnome-3-34-1804/72
loop8    7:8    0  62.1M  1 loop /snap/gtk-common-themes/1506
loop9    7:9    0  61.8M  1 loop /snap/core20/1081
loop10   7:10   0  32.3M  1 loop /snap/snapd/12704
loop11   7:11   0   704K  1 loop /snap/gnome-characters/726
loop12   7:12   0   548K  1 loop /snap/gnome-logs/106
loop13   7:13   0  55.5M  1 loop /snap/core18/2074
loop14   7:14   0 101.5M  1 loop /snap/p7zip-desktop/220
loop15   7:15   0   276K  1 loop /snap/gnome-characters/550
loop16   7:16   0  29.9M  1 loop /snap/snapd/8542
loop17   7:17   0  99.4M  1 loop /snap/core/11420
loop18   7:18   0   140K  1 loop /snap/gtk2-common-themes/13
loop19   7:19   0  55.3M  1 loop /snap/core18/1885
loop20   7:20   0   2.4M  1 loop /snap/gnome-calculator/748
loop21   7:21   0 323.5M  1 loop /snap/kde-frameworks-5-qt-5-15-core20/14
sda      8:0    0   1.8T  0 disk 
&#9492;&#9472;sda1   8:1    0   1.8T  0 part /media/afterwin-2020/hdd2
sdb      8:16   0 465.8G  0 disk 
&#9492;&#9472;sdb1   8:17   0 465.8G  0 part /
```

---

### Post by mIk3_08 on 2021-08-02
> **r2020r said:**
> I removed Gnome
I don't think you have successfully remove the GNOME desktop. I still see it in your desktop information result.
Maybe you have messed up the mix of your desktop with the kde and gnome that causes the system to hang very bad. 
I haven't seen any plasma desktop as what you've showed us in the results here in thread.
> **r2020r said:**
> I  installed KDE-plasma and removed Gnome for the sake of testing.  KDE-plasma was hanging very badly.
This KDE-plasma is highly configurable it is very nice and pretty. If we need an actual light solution, 
and I'm sure it will run smoothly even in the old hardware, you should go for an Xfce, or more likely, LXDE. 
These are not that so good looking but its more lightweight than KDE-Plasma 
> **r2020r said:**
>   To try out the old kernel, should I go back to PhysicalDisk1 or can  select the old-kernel in PhysicalDisk2?
I hope my question is clear..
Don't try to attempt to use the old kernel. If I where you;
use the command 
```
sudo apt update
```
and
```
sudo apt upgrade
```

---

### Post by ActionParsnip on 2021-08-02
If you make a fresh user and log in as that, is it OK there?

---

### Post by r2020r on 2021-08-02
> **mIk3_08 said:**
> I don't think you have successfully remove the GNOME desktop. I still see it in your desktop information result. 
These screenshots are taken after **restoring** the backup that had **18.0.5 + Gnome**. That is why these screen shots still show Gnome. 
Before restoring, i did KDE experiment. I have the image of **18.0.5 + Gnome. **Before any experiment I restore the image and try. 

> **mIk3_08 said:**
> 
If I where you;
use the command 
```
sudo apt update
```
and
```
sudo apt upgrade
```


I will try and let you know.

Thanks

---

### Post by r2020r on 2021-08-02
> **ActionParsnip said:**
> If you make a fresh user and log in as that, is it OK there?
I will try and let you know.

Thanks

---

