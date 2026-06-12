---
title: "Freezing of Mouse in Ubuntu Mate 19.10"
date: 2019-11-28
forum: New to Ubuntu
---

### Post by gbk1960 on 2019-11-28
Hi to all

1. I am from India and quite new to Ubuntu
2. I have been using Linux MINT - Mate Edition for many years now. 
3. I was facing system crashes in Linux MINT Mate 19.x due to the Open Source Driver for Nvidia Graphics (NOUVEAU) . Was not able to download proprietary Nvidia drivers for my graphics card, as I found it difficult for a layman like me. Since the machine was very old, I decided to buy a new one with non-Nvidia graphics, say Radeon or Intel.
4. I recently purchased a New Computer with Asus Prime 450M-A motherboard and AMD Ryzen 3 220G with Radeon Vega Graphics
5. Linux MINT (Mate) 19.x is based on Ubuntu 18.4.LTS and was having Linux Kernel 4.x . This kernel DOES NOT support my new computer's CPU/APU/GPU. Hence, tried to switch over to Ubuntu 19.10 Mate edition which has Linux Kernel 5.x series and support for my CPU/APU/GPU
6. Now the PROBLEM - In this Ubuntu 19.10, I face mouse freeze quite often. Most of the times in Firefox. But freeze happens in many other applications like LibreOffice (Writer/calc/etc)
7. Many people have reported such freeze of mouse (which gets released after a while automatically) in Forums. But their environments and mine do not match.
8. Some people also have said that THERE IS A PROBLEM in Kernel 5.3.x and has been rectified in 5.4

HELP Required

I really do not know why the mouse freeze happens. My OS has the latest updates. Currently it shows the version as 5.3,0-23-generic. My Video driver shows as "amdgpu"

In order to help me, I am ready to provide output of relevant commands. Please let me know how I can copy/paste my screen in this Forum Post. 

This Computer has 8 GB (4 x 2) DDR4 memory. Linux shows only 6 GB for it and 2 GB for graphics card. UEFI BIOS shows 8 GB. ( I found the split-up of 8GB as 6 plus 2 in Windows 10, which runs in another partition)

Regards
G Balakrishnan
India
Timezone GMT+5.30
(A newbie with respect to Ubuntu.....

---

### Post by gbk1960 on 2019-11-29
Please help

> **gbk1960 said:**
> Hi to all

1. I am from India and quite new to Ubuntu
2. I have been using Linux MINT - Mate Edition for many years now. 
3. I was facing system crashes in Linux MINT Mate 19.x due to the Open Source Driver for Nvidia Graphics (NOUVEAU) . Was not able to download proprietary Nvidia drivers for my graphics card, as I found it difficult for a layman like me. Since the machine was very old, I decided to buy a new one with non-Nvidia graphics, say Radeon or Intel.
4. I recently purchased a New Computer with Asus Prime 450M-A motherboard and AMD Ryzen 3 220G with Radeon Vega Graphics
5. Linux MINT (Mate) 19.x is based on Ubuntu 18.4.LTS and was having Linux Kernel 4.x . This kernel DOES NOT support my new computer's CPU/APU/GPU. Hence, tried to switch over to Ubuntu 19.10 Mate edition which has Linux Kernel 5.x series and support for my CPU/APU/GPU
6. Now the PROBLEM - In this Ubuntu 19.10, I face mouse freeze quite often. Most of the times in Firefox. But freeze happens in many other applications like LibreOffice (Writer/calc/etc)
7. Many people have reported such freeze of mouse (which gets released after a while automatically) in Forums. But their environments and mine do not match.
8. Some people also have said that THERE IS A PROBLEM in Kernel 5.3.x and has been rectified in 5.4

HELP Required

I really do not know why the mouse freeze happens. My OS has the latest updates. Currently it shows the version as 5.3,0-23-generic. My Video driver shows as "amdgpu"

In order to help me, I am ready to provide output of relevant commands. Please let me know how I can copy/paste my screen in this Forum Post. 

This Computer has 8 GB (4 x 2) DDR4 memory. Linux shows only 6 GB for it and 2 GB for graphics card. UEFI BIOS shows 8 GB. ( I found the split-up of 8GB as 6 plus 2 in Windows 10, which runs in another partition)

Regards
G Balakrishnan
India
Timezone GMT+5.30
(A newbie with respect to Ubuntu.....

---

### Post by adynouni on 2019-12-04
Check that your mouse is working, maybe the reason is not in the system (Ubuntu). Then check the connectors. The connectors must be clean, the contacts must not be bent. Then reboot the system again.

---

### Post by gbk1960 on 2019-12-08
> **adynouni said:**
> Check that your mouse is working, maybe the reason is not in the system (Ubuntu). Then check the connectors. The connectors must be clean, the contacts must not be bent. Then reboot the system again.

Hello

Good to see a reply

The mouse is quite clean. It works fine in (dual boot) windows 10 on the same machine

It looks like the problem is Open Source Video Driver "amdgpu" . 

Even though the drivers provided by AMD for Windows 10 supports 1920x1080 resolution, and smooth, the Open Source driver in Ubuntu 19.10 (kernel 5.30.0-24-generic) is quite laggy and makes mouse freeze at 1920x1080. 

When I reduced the resolution to 1600x800, it is much better - of course, the mouse freeze occasionally happens

Proprietary driver amdgpu-pro MAY SOLVE the issue - however, people have reported that due to a hard-coding, it supports ONLY 18.04.x and NOT 19.10

I am ALMOST sure the problem is amdgpu Open Source Driver

Any suggestion to overcome the issue and help me use 1920x1080 without mouse freeze is welcome

Regards
GB
India

---

### Post by gbk1960 on 2019-12-08
Hello

Since I am ALMOST SURE the problem is due to amdgpu video driver, I want to post this thread in a more relevant and appropriate sub-forum

Can someone help in this regards (to move this thread)

Regards
GB
India

---

### Post by mörgæs on 2019-12-09
If you click 'report' you can ask a moderator to move it.

---

### Post by oldrocker99 on 2019-12-09
Millions of Linux users use the amdgpu drivers with no problems, FWIW.

---

### Post by mörgæs on 2019-12-09
A detailed hardware description might give someone an idea. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags.

---

### Post by gbk1960 on 2019-12-10
Thanks to all those who replied

1. I have Windows 10 and Ubuntu 19.10 (MATE) as dual boot in the same machine. The monitor is from a renowned company (BenQ) capable of 1920x1080

2. There is NO problem of mouse freezing in Windows 10 in 1920x1080 in the same machine. However, under Linux, using amdgpu supplied with Ubuntu 19.10 MATE (currently kernel 5.3.0-24-generic) at 1920x1080 freezes the mouse VERY OFTEN. It happens in Firefox as well as many other applications like LibreOffice Calc

3. When the resolution is 1600x800, the mouse freeze practically goes away (of course, it does freeze once a while)

4. I have the output of lshw -sanitize. However, I am not able to attach that file (sanitize.txt) due to some file size restrictions. I have zipped it and attached as an attachment

5. I DO UNDERSTAND that many are using Open Source amdgpu without problem. But their environment and mine may be different

Regards
GB
India

---

### Post by mörgæs on 2019-12-11
Yes, it's a long file. Posting a shortened version here hoping that it will give someone an idea.

```
computer    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.1.1 dmi-3.1.1 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=[REMOVED]
  *-core
       description: Motherboard
       product: PRIME B450M-A
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: [REMOVED]
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1002
          date: 03/07/2019
          size: 64KiB
          capacity: 16MiB
          capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 8GiB
        *-bank:1
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: CMK4GX4M1A2400C16
             vendor: Corsair
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_A2
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:3
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: CMK4GX4M1A2400C16
             vendor: Corsair
             physical id: 3
             serial: [REMOVED]
             slot: DIMM_B2
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
     *-cpu
          description: CPU
          product: AMD Ryzen 3 2200G with Radeon Vega Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 2e
          bus info: cpu@0
          version: AMD Ryzen 3 2200G with Radeon Vega Graphics
          serial: [REMOVED]
          slot: AM4
          size: 3560MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb hw_pstate sme ssbd sev ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov succor smca cpufreq
          configuration: cores=4 enabledcores=4 threads=4
           *-sata
                description: SATA controller
                product: 400 Series Chipset SATA Controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                logical name: scsi0
                logical name: scsi1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: sata msi pm pciexpress ahci_1.0 bus_master cap_list rom emulated
                configuration: driver=ahci latency=0
                resources: irq:52 memory:fce80000-fce9ffff memory:fce00000-fce7ffff
              *-disk:0
                   description: ATA Disk
                   product: ST1000DM010-2EP1
                   physical id: 0
                   bus info: scsi@0:0.0.0
                   logical name: /dev/sda
                   version: CC43
                   serial: [REMOVED]
                   size: 931GiB (1TB)
                   capabilities: gpt-1.00 partitioned partitioned:gpt
                   configuration: ansiversion=5 guid=4add2dc1-51f9-4ec7-8495-06c6a547a8b3 logicalsectorsize=512 sectorsize=4096
                 *-volume:0
                      description: Windows NTFS volume
                      vendor: Windows
                      physical id: 1
                      bus info: scsi@0:0.0.0,1
                      logical name: /dev/sda1
                      version: 3.1
                      serial: [REMOVED]
                      size: 527MiB
                      capacity: 528MiB
                      capabilities: boot precious nomount ntfs initialized
                      configuration: clustersize=4096 created=2019-10-26 05:20:17 filesystem=ntfs label=Recovery name=Basic data partition state=clean
                 *-volume:1
                      description: Windows FAT volume
                      vendor: MSDOS5.0
                      physical id: 2
                      bus info: scsi@0:0.0.0,2
                      logical name: /dev/sda2
                      logical name: /boot/efi
                      version: FAT32
                      serial: [REMOVED]
                      size: 77MiB
                      capacity: 98MiB
                      capabilities: boot nomount fat initialized
                      configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
                 *-volume:2
                      description: reserved partition
                      vendor: Windows
                      physical id: 3
                      bus info: scsi@0:0.0.0,3
                      logical name: /dev/sda3
                      serial: [REMOVED]
                      capacity: 15MiB
                      capabilities: nofs nomount
                      configuration: name=Microsoft reserved partition
                 *-volume:3
                      description: Windows NTFS volume
                      vendor: Windows
                      physical id: 4
                      bus info: scsi@0:0.0.0,4
                      logical name: /dev/sda4
                      version: 3.1
                      serial: [REMOVED]
                      size: 255GiB
                      capacity: 255GiB
                      capabilities: ntfs initialized
                      configuration: clustersize=4096 created=2019-10-26 05:22:55 filesystem=ntfs name=Basic data partition state=clean
              *-disk:1
                   description: ATA Disk
                   product: ST1000VX000-1ES1
                   physical id: 1
                   bus info: scsi@1:0.0.0
                   logical name: /dev/sdb
                   version: CV27
                   serial: [REMOVED]
                   size: 931GiB (1TB)
                   capabilities: gpt-1.00 partitioned partitioned:gpt
                   configuration: ansiversion=5 guid=3abe31c3-e84e-4281-95bd-4e073fe77150 logicalsectorsize=512 sectorsize=4096
                 *-volume:0
                      description: Windows FAT volume
                      vendor: mkfs.fat
                      physical id: 1
                      bus info: scsi@1:0.0.0,1
                      logical name: /dev/sdb1
                      version: FAT32
                      serial: [REMOVED]
                      size: 509MiB
                      capacity: 510MiB
                      capabilities: boot fat initialized
                      configuration: FATs=2 filesystem=fat
                 *-volume:1
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 2
                      bus info: scsi@1:0.0.0,2
                      logical name: /dev/sdb2
                      logical name: /
                      version: 1.0
                      serial: [REMOVED]
                      size: 244GiB
                      capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                      configuration: created=2019-11-06 21:02:40 filesystem=ext4 lastmountpoint=/ modified=2019-12-10 18:23:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-12-10 18:23:52 state=mounted
                 *-volume:2
                      description: Linux swap volume
                      vendor: Linux
                      physical id: 3
                      bus info: scsi@1:0.0.0,3
                      logical name: /dev/sdb3
                      version: 1
                      serial: [REMOVED]
                      size: 3999MiB
                      capacity: 3999MiB
                      capabilities: nofs swap initialized
                      configuration: filesystem=swap pagesize=4095
                 *-volume:3
                      description: data partition
                      vendor: Windows
                      physical id: 4
                      bus info: scsi@1:0.0.0,4
                      logical name: /dev/sdb4
                      serial: [REMOVED]
                      capacity: 244GiB
                 *-volume:4
                      description: data partition
                      vendor: Windows
                      physical id: 5
                      bus info: scsi@1:0.0.0,5
                      logical name: /dev/sdb5
                      serial: [REMOVED]
                      capacity: 213GiB
                 *-volume:5
                      description: data partition
                      vendor: Windows
                      physical id: 6
                      bus info: scsi@1:0.0.0,6
                      logical name: /dev/sdb6
                      serial: [REMOVED]
                      capacity: 224GiB
           *-pci
                description: PCI bridge
                product: 400 Series Chipset PCIe Bridge
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:01:00.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:30 ioport:f000(size=4096) memory:fcd00000-fcdfffff
              *-pci:0
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 0
                   bus info: pci@0000:02:00.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:32
              *-pci:1
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 4
                   bus info: pci@0000:02:04.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:33
              *-pci:2
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 5
                   bus info: pci@0000:02:05.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:35
              *-pci:3
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 6
                   bus info: pci@0000:02:06.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:36
              *-pci:4
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 7
                   bus info: pci@0000:02:07.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:38 ioport:f000(size=4096) memory:fcd00000-fcdfffff
                 *-network
                      description: Ethernet interface
                      product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                      vendor: Realtek Semiconductor Co., Ltd.
                      physical id: 0
                      bus info: pci@0000:07:00.0
                      logical name: enp7s0
                      version: 15
                      serial: [REMOVED]
                      capacity: 1Gbit/s
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII
                      resources: irq:37 ioport:f000(size=256) memory:fcd04000-fcd04fff memory:fcd00000-fcd03fff
        *-pci:1
             description: PCI bridge
             product: Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus A
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:e000(size=4096) memory:fc900000-fccfffff ioport:e0000000(size=270532608)
           *-display
                description: VGA compatible controller
                product: Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:08:00.0
                version: c8
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix vga_controller bus_master cap_list rom
                configuration: driver=amdgpu latency=0
                resources: irq:56 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fcc00000-fcc7ffff memory:c0000-dffff
           *-multimedia:0
                description: Audio device
                product: Raven/Raven2/Fenghuang HDMI/DP Audio Controller
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:08:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:58 memory:fcc88000-fcc8bfff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:8
       logical name: enp1s0f0u8
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=[REMOVED] link=yes multicast=yes



```

---

### Post by gbk1960 on 2019-12-15
Hi all

Have been expecting some help....but not received any...

Since 1920x1080 works fine under windows 10 in the same machine (dual boot) and mouse freezing happens under ubuntu mate  19.10 with amdgpu video driver at 1920x1080, I am at a loss as to what to do...

Unlike Mint Mate, which comes with Compiz, this ubuntu 19.10 does not even have that for me to suspect it 

I forcibly stopped hardware video acceleration in firefox.

Still, I don't mind waiting for a few days to get some help

Else, will be forced to switch to another distribution which supports my hardware at 1920x1080

Thanks

---

### Post by mörgæs on 2019-12-15
Asus has released many [BIOS updates]("https://www.asus.com/us/Motherboards/PRIME-B450M-A/HelpDesk_BIOS/") since version 1002. I suggest that you try to see if a new BIOS helps.

---

### Post by gbk1960 on 2019-12-15
Thanks for the suggestion.

I am NOT that brave to update/upgrade BIOS. Anyway, let me read about updating/upgrading  BIOS. 

However,  my worry has always been this - when it works under Windows 10 but not in Linux in the same machine,  what to suspect? Logically speaking the video driver,  window manager, etc, is it not?

Sir/Madam

Do you suggest to post my queries as a separate post in a more appropriate sub-forum? And if yes, please suggest such a sub-forum

Regards 
GB
India

---

### Post by gbk1960 on 2019-12-16
Hi All

1. When I was using my old computer, I was using ps/2 keyboard and ps/2 mouse
2. In the new computer (the whole thread is about the new computer - full details of hardware and software available in the previous posts) I started using Logitech K220  wireless keyboard with mouse
3. I removed the Logitech wireless keyboard and mouse and replaced them with my old ps/2 keyboard and ps/2 mouse
4. In Control panel - under the MOUSE option, the acceleration and sensitivity are approximately 50%. (I don't know whether these parameters are of any significance)
5. The mouse freezing PRACTICALLY STOPPED to my surprise
6. I changed resolution to 1920x1080 - even then NO FREEZING of mouse
7. I reverted to  hardware video acceleration in Firefox (version 71) under preferences. Again NO FREEZING of mouse
8. I will wait for a day or two before closing the thread - and ensure that the Mouse Freezing does not happen again

Thanks to all

Regards
GB
India

---

