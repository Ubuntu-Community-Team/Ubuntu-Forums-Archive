---
title: "Suspend not behaving properly"
date: 2024-09-10
forum: New to Ubuntu
---

### Post by saltyconnection on 2024-09-10
I've searched multiple forum posts. Some from 2011 up to 2022.
I've been having issues when i suspend my computer. The fans don't turn off (unsure if its graphics card or case fans) I will investigate this when i turn of my computer soon. Also the keyboard dosn't wake up the computer from suspend. (edit) This error only seems to happen when the computer goes to suspend after a period of inactivity, rather than when you suspend the computer manually (/edit)
The only way to get the computer to do anything is to hold down the power button to force a shutdown, it then powers off, and continues to boot up, when it should just keep the power off. 

I've done a system-info (i hope i've done it right) Couldn't find the file that is safe to read, so i've just redacted the IP information.
I recently bought a new graphics card because i thought this might be the issue. I've tried to reinstall radeon drivers. (it was another forum post i've read) But this didn't work. I downloaded the .deb package from radeon and installed it. Unsure if i managed to uninstall the previous package.  

Any help anyone can offer is much appreciated. Thank you.

```
                          ---------------------------------------------------------------
 Main Complaint: Suspend not working
 Problem Description:  Fan remains on when suspended and keyboard dosn't wake up
 ---------- General Computer Specifications:
 
 
   --- Computer/CPU Information from 'lshw -C cpu' ---  
 *-Cpu
     Description: CPU
     Product: Intel(R) Core(TM) i5-10600 CPU @ 3.30GHz
     Vendor: Intel Corp.
     Physical id: 20
     Bus info: cpu@0
     Version: 6.165.3
     Serial: To Be Filled By O.E.M.
     Slot: CPUSocket
     Size: 4685MHz
     Capacity: 4800MHz
     Width: 64 bits
     Clock: 100MHz
     Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8  
         apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse  
         sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art  
         arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid  
         aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3  
         sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt  
         tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch  
         cpuid_fault epb ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow  
         flexpriority ept vpid ept_ad fsgsbase tsc_adjust sgx bmi1 avx2 smep  
         bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt  
         xsavec xgetbv1 xsaves dtherm ida arat pln pts vnmi sgx_lc md_clear  
         flush_l1d arch_capabilities cpufreq
     Configuration: cores=6 enabledcores=6 microcode=252 threads=12
 
 
 mark-desktop
     Description: Desktop Computer
     Product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
     Vendor: To Be Filled By O.E.M.
     Version: To Be Filled By O.E.M.
     Serial: To Be Filled By O.E.M.
     Width: 64 bits
     Capabilities: smbios-3.2.0 dmi-3.2.0 smp vsyscall32
     Configuration:
         boot=normal
         chassis=desktop
         family=To Be Filled By O.E.M.
         sku=To Be Filled By O.E.M.
         uuid=5f59a1a8-40d4-0000-0000-000000000000
 ----------------- SMBIOS Information from '/sys/class/dmi/id/'  
 Bios Vendor:         American Megatrends Inc.
 Bios Version:        P1.60
 Bios Release:        5.17
 Board Vendor:        ASRock
 Board Name:          B460 Pro4
 Board Version:       
 Board Serial:        M80-DB003500182
 Board Asset Tag:     
 
 
 Current boot mode:   UEFI Firmware mode
    --- SecureBoot Status from 'mokutil':
 SecureBoot disabled
 Platform is in Setup Mode
 
 
 
 
 ---------- Memory Information:
                total        used        free      shared  buff/cache   available
 Mem:           31894        4499       25126         217        2913       27395
 Swap:           8191           0        8191
 
 
 ---------- Swap Information:
   --- Info from 'fstab'
 /swap.img       none    swap    sw      0       0
 
 
   --- Info from '/proc/swaps'
 Filename                                Type            Size            Used            Priority
 /swap.img                               file            8388604         0               -2
 
 
   --- System Swapiness Settings
 Valid swappiness settings are from 10 - 60 .  
 Current setting in '/proc/sys/vm/swappiness': 60  
 Current configuration setting in '/etc/sysctl.conf file:  
 
 
 
 
 ---------- IP Address Information:
   --- IP Address Information from 'ip addr' ---  
 information redacted
 
 
 ---------- Storage Controller Information From 'lspci':
 00:17.0 SATA controller: Intel Corporation 400 Series Chipset Family SATA AHCI Controller (prog-if 01 [AHCI 1.0])
         DeviceName: Onboard - SATA
         Subsystem: ASRock Incorporation 400 Series Chipset Family SATA AHCI Controller
         Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 125, IOMMU group 4
         Memory at 99648000 (32-bit, non-prefetchable) [size=8K]
         Memory at 9964c000 (32-bit, non-prefetchable) [size=256]
         I/O ports at 4050 [size=8]
         I/O ports at 4040 [size=4]
         I/O ports at 4020 [size=32]
         Memory at 9964b000 (32-bit, non-prefetchable) [size=2K]
         Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
         Capabilities: [70] Power Management version 3
         Capabilities: [a8] SATA HBA v1.0
         Kernel driver in use: ahci
         Kernel modules: ahci
 
 
 
 
 04:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller PM9A1/PM9A3/980PRO (prog-if 02 [NVM Express])
         Subsystem: Samsung Electronics Co Ltd SSD 980 PRO
         Flags: bus master, fast devsel, latency 0, IRQ 16, IOMMU group 5
         Memory at 99500000 (64-bit, non-prefetchable) [size=16K]
         Capabilities: [40] Power Management version 3
         Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
         Capabilities: [70] Express Endpoint, MSI 00
         Capabilities: [b0] MSI-X: Enable+ Count=130 Masked-
         Capabilities: [100] Advanced Error Reporting
         Capabilities: [168] Alternative Routing-ID Interpretation (ARI)
         Capabilities: [178] Secondary PCI Express
         Capabilities: [198] Physical Layer 16.0 GT/s <?>
         Capabilities: [1bc] Lane Margining at the Receiver <?>
         Capabilities: [214] Latency Tolerance Reporting
         Capabilities: [21c] L1 PM Substates
         Capabilities: [3a0] Data Link Feature <?>
         Kernel driver in use: nvme
         Kernel modules: nvme
 
 
 
 
 05:00.0 Non-Volatile memory controller: Kingston Technology Company, Inc. A2000 NVMe SSD SM2263EN (rev 03) (prog-if 02 [NVM Express])
         Subsystem: Kingston Technology Company, Inc. A2000 NVMe SSD SM2263EN
         Flags: bus master, fast devsel, latency 0, IRQ 16, IOMMU group 6
         Memory at 99400000 (64-bit, non-prefetchable) [size=16K]
         Capabilities: [40] Power Management version 3
         Capabilities: [50] MSI: Enable- Count=1/8 Maskable+ 64bit+
         Capabilities: [70] Express Endpoint, MSI 00
         Capabilities: [b0] MSI-X: Enable+ Count=16 Masked-
         Capabilities: [100] Advanced Error Reporting
         Capabilities: [158] Secondary PCI Express
         Capabilities: [178] Latency Tolerance Reporting
         Capabilities: [180] L1 PM Substates
         Kernel driver in use: nvme
         Kernel modules: nvme
 
 
 
 
 ---------- File system specs from 'df -h':
 Filesystem     Type      Size  Used Avail Use% Mounted on
 /dev/nvme1n1p2 ext4      915G  261G  608G  31% /
 efivarfs       efivarfs  192K   46K  142K  25% /sys/firmware/efi/efivars
 /dev/nvme1n1p1 vfat      1.1G  6.2M  1.1G   1% /boot/efi
 
 
 ---------- Disk/Partition Information From 'fdisk':
 
 
 Disk /dev/nvme0n1: 465.76 GiB, 500107862016 bytes, 976773168 sectors
 Disk model: KINGSTON SA2000M8500G                    
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 Disk /dev/nvme1n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
 Disk model: Samsung SSD 980 PRO 1TB                  
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 Disklabel type: gpt
 Disk identifier: 503ED438-6C71-436C-A0AA-FCFC5B8D9D81
 
 
 Device           Start        End    Sectors   Size Type
 /dev/nvme1n1p1    2048    2203647    2201600     1G EFI System
 /dev/nvme1n1p2 2203648 1953521663 1951318016 930.5G Linux filesystem
 
 
 
 
 ---------- Disk/Partition Information From 'lsblk':
 NAME          SIZE FSTYPE   LABEL MOUNTPOINT                          MODEL
 nvme0n1     465.8G ext3                                               KINGSTON SA2000M8500G
 nvme1n1     931.5G                                                    Samsung SSD 980 PRO 1TB
 |_nvme1n1p1     1G vfat           /boot/efi                            
 |_nvme1n1p2 930.5G ext4           /                                    
    ------- 'lsblk' information continued ...
 NAME        HOTPLUG PARTUUID                             UUID
 nvme0n1           0                                      f121d9fa-7766-4eaf-9439-6929d2859475
 nvme1n1           0                                       
 |_nvme1n1p1       0 17939175-e362-4070-9749-f73f278662bf 08FA-1AF1
 |_nvme1n1p2       0 fbc6e154-98f6-421b-9921-ea0ccca19cfa 78f3f185-925b-47b1-b807-dda0238131c3
 
 
 ----------  BTRFS Information:
 There are no BTRFS vdev's present.
 
 
 ----------  LVM2 Information:
 There are no LVM2 volumes present.
 
 
 ----------  mdadm RAID Information:
 No active md devices present.
 ---------- Mount Details of '/etc/fstab':
 /dev/disk/by-uuid/78f3f185-925b-47b1-b807-dda0238131c3 / ext4 defaults 0 1
 /dev/disk/by-uuid/08FA-1AF1 /boot/efi vfat defaults 0 1
 /swap.img       none    swap    sw      0       0
 
 
 ---------- Current Mount Details of 'mount':
 /dev/nvme1n1p1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
 /dev/nvme1n1p2 on / type ext4 (rw,relatime)
 
 
 For more detailed disk Information, please run the 'boot-info' script  
 from: (STABLE) [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)  
 
 
 ---------- USB Information from 'lsusb -t -v':
 /:  Bus 001.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/12p, 480M
     ID 1d6b:0002 Linux Foundation 2.0 root hub
     |__ Port 007: Dev 002, If 0, Class=Audio, Driver=snd-usb-audio, 12M
         ID 17a0:0311 Samson Technologies Corp. Satellite condenser microphone
     |__ Port 007: Dev 002, If 1, Class=Audio, Driver=snd-usb-audio, 12M
         ID 17a0:0311 Samson Technologies Corp. Satellite condenser microphone
     |__ Port 007: Dev 002, If 2, Class=Audio, Driver=snd-usb-audio, 12M
         ID 17a0:0311 Samson Technologies Corp. Satellite condenser microphone
     |__ Port 009: Dev 003, If 0, Class=Human Interface Device, Driver=usbhid, 12M
         ID 046d:c33c Logitech, Inc.  
     |__ Port 009: Dev 003, If 1, Class=Human Interface Device, Driver=usbhid, 12M
         ID 046d:c33c Logitech, Inc.  
     |__ Port 010: Dev 004, If 0, Class=Human Interface Device, Driver=usbhid, 12M
         ID 26ce:01a2   
     |__ Port 011: Dev 005, If 0, Class=Human Interface Device, Driver=usbhid, 12M
         ID 046d:c246 Logitech, Inc. Gaming Mouse G300
     |__ Port 011: Dev 005, If 1, Class=Human Interface Device, Driver=usbhid, 12M
         ID 046d:c246 Logitech, Inc. Gaming Mouse G300
     |__ Port 012: Dev 006, If 0, Class=Hub, Driver=hub/4p, 480M
         ID 05e3:0610 Genesys Logic, Inc. Hub
 /:  Bus 002.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/8p, 5000M
     ID 1d6b:0003 Linux Foundation 3.0 root hub
 ---------- Video Details from 'lshw':
 
 
   *-display
        description: VGA compatible controller
        product: Navi 32 [Radeon RX 7700 XT / 7800 XT]
        vendor: Advanced Micro Devices, Inc. [AMD/ATI]
        physical id: 0
        bus info: pci@0000:03:00.0
        logical name: /dev/fb0
        version: ff
        width: 64 bits
        clock: 33MHz
        capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
        configuration: depth=32 driver=amdgpu latency=0 resolution=3840,2160
        resources:  
            irq:164  
            memory:a0000000-afffffff  
            memory:b0000000-b01fffff  
            ioport:3000(size=256)  
            memory:99100000-991fffff  
            memory:99200000-9921ffff
 
 
    --- Graphics Environment Continued from 'various graphics ENVs' ----
 The Current Configured Destop is: ubuntu:GNOME  
 The Current Desktop Session is: ubuntu  
 The Current X Desktop Information Details from 'xrandr' are:  
 Screen 0: minimum 16 x 16, current 3840 x 2160, maximum 32767 x 32767
 HDMI-1 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 700mm x 390mm
 The Current Session Type is: wayland  
 The Current Display Manager is: gdm3
 The Current Desktop Theme: 'Yaru-dark'
 The Current Virtual TTY's being used are:
         TTY#    Used By
         tty2    gdm-wayland-ses
         tty2    gnome-session-b
         pts/0   bash
         pts/0   system-info
         pts/0   less
         pts/1   system-info
         pts/1   system-info
         pts/1   less
         pts/1   system-info
         pts/1   ps
         pts/1   awk
 
 
 ---------- Sound Device Information From 'lspci':
 00:1f.3 Audio device: Intel Corporation Comet Lake PCH-V cAVS
         DeviceName: Onboard - Sound
         Subsystem: ASRock Incorporation Comet Lake PCH-V cAVS
         Flags: bus master, fast devsel, latency 32, IRQ 162, IOMMU group 7
         Memory at 99640000 (64-bit, non-prefetchable) [size=16K]
         Memory at 99620000 (64-bit, non-prefetchable) [size=64K]
         Capabilities: [50] Power Management version 3
         Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
         Kernel driver in use: snd_hda_intel
         Kernel modules: snd_hda_intel, snd_soc_avs, snd_sof_pci_intel_cnl
 
 
 
 
 03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Navi 31 HDMI/DP Audio
         Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Navi 31 HDMI/DP Audio
         Flags: bus master, fast devsel, latency 0, IRQ 163, IOMMU group 1
         Memory at 99220000 (32-bit, non-prefetchable) [size=16K]
         Capabilities: [48] Vendor Specific Information: Len=08 <?>
         Capabilities: [50] Power Management version 3
         Capabilities: [64] Express Legacy Endpoint, MSI 00
         Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
         Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
         Capabilities: [150] Advanced Error Reporting
         Capabilities: [2a0] Access Control Services
         Kernel driver in use: snd_hda_intel
 Kernel modules: snd_hda_intel
 
 
 
 
 For more detailed audio information, get and run the script at: [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)  
 
 
 ---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':
 
 
 Sources List:
 
 
 
 
 Sources List from SourcesD:
 /etc/apt/sources.list.d/rocm.list:
 deb [arch=amd64] [https://repo.radeon.com/rocm/apt/6.1.3](https://repo.radeon.com/rocm/apt/6.1.3) jammy main
 /etc/apt/sources.list.d/ubuntu-esm-infra.sources.save:
 Types: deb
 URIs: [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu)
 Suites: noble-infra-security noble-infra-updates
 Components: main
 Signed-By: /usr/share/keyrings/ubuntu-pro-esm-infra.gpg
 /etc/apt/sources.list.d/ubuntu.sources.curtin.orig:
 Types: deb
 URIs: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
 Suites: noble noble-updates noble-backports
 Components: main universe restricted multiverse
 Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
 Types: deb
 URIs: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
 Suites: noble-security
 Components: main universe restricted multiverse
 Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
 /etc/apt/sources.list.d/rocm.list.save:
 deb [arch=amd64] [https://repo.radeon.com/rocm/apt/6.1.3](https://repo.radeon.com/rocm/apt/6.1.3) jammy main
 /etc/apt/sources.list.d/amdgpu-proprietary.list.save:
 deb [https://repo.radeon.com/amdgpu/6.1.3/ubuntu](https://repo.radeon.com/amdgpu/6.1.3/ubuntu) jammy proprietary
 /etc/apt/sources.list.d/amdgpu-proprietary.list:
 File had no entries.
 /etc/apt/sources.list.d/ubuntu-esm-infra.sources:
 Types: deb
 URIs: [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu)
 Suites: noble-infra-security noble-infra-updates
 Components: main
 Signed-By: /usr/share/keyrings/ubuntu-pro-esm-infra.gpg
 /etc/apt/sources.list.d/amdgpu.list:
 deb [https://repo.radeon.com/amdgpu/6.1.3/ubuntu](https://repo.radeon.com/amdgpu/6.1.3/ubuntu) jammy main
 deb-src [https://repo.radeon.com/amdgpu/6.1.3/ubuntu](https://repo.radeon.com/amdgpu/6.1.3/ubuntu) jammy main
 /etc/apt/sources.list.d/ubuntu.sources.save:
 Types: deb
 URIs: [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/)
 Suites: noble noble-updates noble-backports
 Components: main restricted universe multiverse
 Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
 Types: deb
 URIs: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
 Suites: noble-security
 Components: main restricted universe multiverse
 Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
 /etc/apt/sources.list.d/amdgpu.list.save:
 deb [https://repo.radeon.com/amdgpu/6.1.3/ubuntu](https://repo.radeon.com/amdgpu/6.1.3/ubuntu) jammy main
 deb-src [https://repo.radeon.com/amdgpu/6.1.3/ubuntu](https://repo.radeon.com/amdgpu/6.1.3/ubuntu) jammy main
 /etc/apt/sources.list.d/ubuntu-esm-apps.sources:
 Types: deb
 URIs: [https://esm.ubuntu.com/apps/ubuntu](https://esm.ubuntu.com/apps/ubuntu)
 Suites: noble-apps-security noble-apps-updates
 Components: main
 Signed-By: /usr/share/keyrings/ubuntu-pro-esm-apps.gpg
 /etc/apt/sources.list.d/ubuntu-esm-apps.sources.save:
 Types: deb
 URIs: [https://esm.ubuntu.com/apps/ubuntu](https://esm.ubuntu.com/apps/ubuntu)
 Suites: noble-apps-security noble-apps-updates
 Components: main
 Signed-By: /usr/share/keyrings/ubuntu-pro-esm-apps.gpg
 /etc/apt/sources.list.d/ubuntu.sources:
 Types: deb
 URIs: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
 Suites: noble-security
 Components: main restricted universe multiverse
 Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
 /etc/apt/sources.list.d/mafoelffen-ubuntu-system-info-noble.sources:
 Types: deb
 URIs: [https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu/](https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu/)
 Suites: noble
 Components: main
 Signed-By: -----BEGIN PGP PUBLIC KEY BLOCK-----
  .
  mQINBGQTcJ0BEADj3+0EqqMGqudLX/HG1U648V0f4Alkn5D1Lc5UdDLK4PsjD8vE
  ELEMhe5SADBZInv6KgIMTar8nnqlX4jmlZ00KtahlLkUizArUtBRp8oVwgKCxUC9
  JBzf2f/ir0xh+o5NB1fKER8AklpR2mQzitFZ4iM+pxrolEduUjup2u1vChgNFuG4
  Ul1f7EtgrWTsbyROucMw/B7BfTFCM/w+NW7gQuoxX6JZMeYwAYHtCQU2no3REa7P
  t2A7XHzuUDx1iBksYNbhFzMYeY1w8lGPsvo0KHwdYnL8YTb1s5ie6guuZry0G80s
  eDAVA/l7AkYDDJ0AfR2HBF4ln+Xjrn1AIqImS6qXPSbdXXg4CHMLZwdDVpkhNIi7
  GAxyuTxb/nY/OKg3Odd5tIT6UpQ7+u1r89rOvybJY9rUK8a0qnLmmlV9cdlg2W9E
  uN2EAcrrzK+/fwrE07t3cjyKXBtufmq8rd3yjJwWVj52L4yKizak0bxD1XitUC+7
  1lTxeZlWJphYpzWfdb6nOVztC1YBl8LXitAELD2Xtn/+CoLYEzmkddVaKa9hDgW6
  1abYnjNPSj0DUwzVEe145v5IQm/yCTIvF94nQPMGqzqnuXD4tPt11S7zNQ1wGTGD
  GniaI2PztfCP+Svip/+ULboHUNcsPbVTXSmNCna7UcuqO7SbtLeu3GUMJwARAQAB
  tB9MYXVuY2hwYWQgUFBBIGZvciBNaWtlIEZlcnJlaXJhiQJOBBMBCgA4FiEEgneH
  GlZjlArvhl2sq8aGfLsigK8FAmQTcJ0CGwMFCwkIBwIGFQoJCAsCBBYCAwECHgEC
  F4AACgkQq8aGfLsigK+U9RAAg72rMi8a6jmcNFF3sRNJVuSxi7Kg3/rX0WKZnqS6
  tk++Y/P1pw8PUZNKWOLqokr0XumGvVH6VLJ0retqipSebBi9TbeRnWAKxJ2amwGy
  +oEdp5FInUeV4gCSpF/8xCVjvO96zI3eg6f5iyXsppzqPe170bv16ZtGVsVi1n83
  7J2RcsXHHq/bUb/aS6d15tmx3MohCakdONuSa0L5nuDlUvuulkFEJiM+OP+wOy8o
  owWYV6iZeiS6eUuBaasWo3JJwnBOGL4F3BA2FJPBIgXOQFhj8JWFo856LRHtg/72
  M6qUY2/xf/hQv5at2HNZfCXqrZ6C4inKBn2V41wwkxV8obwUK4s1N+OOxR9YGEJf
  uoSmnNlumckplKWwV8/gKG+9RDuaNOfAg2nohFyHTfXExHwzlnJkLPgF8Mt9YW+/
  ymueftb5ELvJSwxUbfcrujoYN05+rssaQHayCk+z8rPnYT4BQD6ci0tysrIuVtNy
  V36uBaiXvccn92UBxPs7g221qbGExiue+nlBT2LqKVOD9H6QkXlzpBcMdPaTtnq5
  ulsNZzwK6twfeP4TWy2VMw0/eF51A+0hPuJc5Jii5hS1oDUnc3ZUMVTOIafj0PKu
  LV8xRAair/e/qrbIlyod//JocP4pr9+ti/AKin9L8cnhVPtmZ/67C0KfFwPJc+Ly
  6Mk=
  =2QB0
  -----END PGP PUBLIC KEY BLOCK-----
 
 
 ---------- KeyMap and Locale Information from from various sources:
    --- Keymap Info from 'setxkbmap' ----
 rules:      evdev
 model:      pc105
 layout:     us
 
 
    --- Locale Info from 'localectl' ----
 System Locale: LANG=en_US.UTF-8
     VC Keymap: (unset)
    X11 Layout: au
     X11 Model: pc105
 --------- Other Details from 'Various':
 The current kernel version is:       6.8.0-41-generic  
     --- Operating System Release Description ---  
 The current release description is:  Ubuntu 24.04.1 LTS  
 
 
 Original Installation Date:          2024-09-05+21:02:55  
 Original Installation Media: Ubuntu 24.04.1 LTS "Noble Numbat" - Release amd64 (20240827.1)
 Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'
 
 
    --- Hardware Enablement Stack (HWE) Informationt:
 These are the current kernel ranges for HWE kernels for this release.
    --- HWE Kernel Reference from 'apt-cache show':
 For HWE Package: linux-image-generic-hwe-24.04, Kernel Version: 6.8.0-41.41
 For HWE Package: linux-image-generic-hwe-24.04, Kernel Version: 6.8.0-31.31
 
 
    --- HWE Package Status from 'dpkg':
 Package linux-generic-hwe-24.04 is installed.
 
 
    --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
 Ubuntu Certified Hardware Platform. Safe to install  
 the Hardware Enablement Stack (HWE).
 
 
    --- User Installed Package List:
 amdgpu-install
 bsdutils
 dash
 diffutils
 efibootmgr
 findutils
 grep
 grub-efi-amd64
 grub-efi-amd64-signed
 gzip
 hostname
 hyphen-en-ca
 hyphen-en-gb
 hyphen-en-us
 ibus-table-cangjie-big
 ibus-table-cangjie3
 ibus-table-cangjie5
 init
 language-pack-en
 language-pack-en-base
 language-pack-gnome-en
 language-pack-gnome-en-base
 libchewing3
 libchewing3-data
 libm17n-0
 libmarisa0
 libopencc-data
 libopencc1.1
 libotf1
 libpinyin-data
 libpinyin15
 libreoffice-help-common
 libreoffice-help-en-gb
 libreoffice-help-en-us
 libreoffice-l10n-en-gb
 libreoffice-l10n-en-za
 linux-generic-hwe-24.04
 linux-modules-nvidia-550-generic-hwe-24.04
 login
 m17n-db
 mythes-en-au
 mythes-en-us
 ncurses-base
 ncurses-bin
 nvidia-driver-550
 shim-signed
 thunderbird-locale-en
 thunderbird-locale-en-gbthunderbird-locale-en-us
 ubuntu-desktop
 ubuntu-desktop-minimal
 ubuntu-minimal
 ubuntu-restricted-addons
 ubuntu-standard
 ubuntu-wallpapers
 
 
    --- Installed Snap Package List:
 bare
 canonical-livepatch
 core20
 core22
 core24
 discord
 firefox
 firmware-updater
 gaming-graphics-core22
 gnome-42-2204
 gnome-46-2404
 gtk-common-themes
 mesa-2404
 qbittorrent-arnatious
 snap-store
 snapd
 snapd-desktop-integration
 steam
 thunderbird
 
 
    --- Installed Flatpak Package List:
 Flatpak is not installed
 
 
 Currently logged in User(s):
 NAME     LINE         TIME         COMMENT
 mark     seat0        Sep 10 16:34 (login screen)
 mark     tty2         Sep 10 16:34 (tty2)
 
 
 The User running this script was: mark
 uid=1000(mark)
 gid=1000(mark)
 groups=1000(mark),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),
 100(users),114(lpadmin)
 
 
 The 'system-info' script was booted from an installed system
 
 
 The 'system-info' script seems to be running locally
 
 
 The Linux Kernel Command Line use to boot was:  
 BOOT_IMAGE=/boot/vmlinuz-6.8.0-41-generic root=UUID=78f3f185-925b-47b1-b807-dda0238131c3 ro quiet splash vt.handoff=7
 
 
 *** End Of Report ***
  
```

---

### Post by mrdc76 on 2024-09-12
> **saltyconnection said:**
> 
I recently bought a new graphics card because i thought this might be the issue. I've tried to reinstall radeon drivers. (it was another forum post i've read) But this didn't work. I downloaded the .deb package from radeon and installed it. Unsure if i managed to uninstall the previous package.  

You don't need to install any extra Radeon drivers and should remove them. 

My laptop has failed to suspend properly because of a connected USB device, so trying to remove all unnecessary devices for debugging might be a good starting point.

---

### Post by saltyconnection on 2024-09-13
[https://imgur.com/a/HWPXVOB](https://imgur.com/a/HWPXVOB)  

Does this look like the right drivers?  

In any case, it turns out its an inclement problem. Sometimes it behaves like normal. But like last night, it didn't behave normally. With the same thing happening, fans are on, and couldn't get it to wake up with keybaord, had to hold down power button then it just restarted itself. I thought steam might have something to do with it but now i'm unsure.  

[https://unix.stackexchange.com/questions/28097/how-to-debug-a-suspend-problem](https://unix.stackexchange.com/questions/28097/how-to-debug-a-suspend-problem)  

I've followed instructions here to create a pm-suspend log in var/log and see if i can shed any light on the issue.

---

### Post by gurgel2 on 2024-11-17
I got the same or similar problem after a fresh install of 24.04.1. Ran 22.04 prior to that with no problem.. Have a Ryzen 5 - 3600, AMG Radeon RX 7600, ASUS Prime X570-P ATX. When i suspend, ca 1/10 times the fans go into some max out mode while computer irresponsive, black screen and the only remedy is pressing the powerbutton for a complete shutdown.

This big problem is that I discover this 8 hours later when I go to bed and I'm afraid fan bearings are wearing out due to the high speed and the long period it stays in this mode. Will need to stay around for each suspend from now on to assert it doesn't enter this mode.

---

### Post by him610 on 2024-11-17
> 
The only way to get the computer to do anything is to hold down the power button to force a shutdown, it then powers off, and continues to boot up, when it should just keep the power off. 

You can shutdown your machine from a terminal. ```
shutdown now
```
If you want to power down using on/off button, you need to depress it for at least 4 seconds.

---

