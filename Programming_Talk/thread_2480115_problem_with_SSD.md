---
title: "problem with SSD"
date: 2022-10-19
forum: Programming Talk
---

### Post by phillip1882 on 2022-10-19
so i just installed ubuntu today and i'm going through the setup process.
when i look at my available drives, i see my two hard drives and my cd drive as i should.
it says my second hard drive is encrypted. and when i try my encryption password, my hard drive disappears.
i have to resat my computer to get it back.
can you help?

---

### Post by TheFu on 2022-10-19
Probably best to get you to run some information gathering tools to get a more complete picture of the issue rather than guessing 50 things that could be wrong.
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

---

### Post by phillip1882 on 2022-10-19
OS: Ubuntu 20.04.5 LTS x86_64 
Kernel: 5.15.0-52-generic 
Uptime: 19 mins 
Packages: 1670 (dpkg), 14 (snap) 
Shell: bash 5.0.17 
Resolution: 1680x1050 
DE: GNOME 
WM: Mutter 
WM Theme: Adwaita 
Theme: Yaru [GTK2/3] 
cons: Yaru [GTK2/3] 
Terminal: gnome-terminal 
CPU: AMD Ryzen 5 2400G (8) @ 3.600GH 
GPU: NVIDIA GeForce GTX 1050 Ti 
 Memory: 1530MiB / 32034MiB

---

### Post by TheFu on 2022-10-20
Thanks for that, but it is nowhere near the 300+ lines we need to see the storage layout and be helpful.
Get the script and run it.

Or you could bet boot-repair and run the "boot information" script that it provides.  DO NOT attempt the repair. You've been warned.

---

### Post by phillip1882 on 2022-10-20
what's the file name that it produces and where does it put it?

---

### Post by phillip1882 on 2022-10-20
i went through the command line prompt and copy pasted the info
```
Starting the Ubuntu Forums 'system-info' Report: 2022-10-20  12:00:55 EDT (-0400
)
        Part of the Ama-gi Project
        Version: 02.00-00, Script Date: 2022.08.28

---------------------------------------------------------------
Main Complaint: ssd not showing
Problem Description:  when i first start my computer, i see two hard drives and acd drive as i should in file manager. it says my second hard drive in encrypted, and when i try an ecryption password, the drive disappers. i have to restart my cpu to see it again,
 Product: AMD Ryzen 5 2400G with Radeon Vega Graphics
    Vendor: Advanced Micro Devices [AMD]
    Physical id: 28
    Bus info: cpu@0
    Version: AMD Ryzen 5 2400G with Radeon Vega Graphics
    Serial: Unknown
    Slot: AM4
    Size: 1540MHz
    Capacity: 3900MHz
    Width: 64 bits
    Clock: 100MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht 
        syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good 
        nopl nonstop_tsc cpuid extd_apicid aperfmperf rapl pni pclmulqdq 
        monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c 
        rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 
        3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb 
        bpext perfctr_llc mwaitx cpb hw_pstate ssbd ibpb vmmcall fsgsbase bmi1 
        avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec 
        xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv svm_lock 
        nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter 
        pfthreshold avic v_vmsave_vmload vgif overflow_recov succor smca sme 
        sev sev_es cpufreq
    Configuration: cores=4 enabledcores=4 threads=8

phillip1882-spn
    Description: Desktop Computer
    Product: System Product Name (SKU)
    Vendor: System manufacturer
    Version: System Version
    Serial: System Serial Number
    Width: 64 bits
    Capabilities: smbios-3.1.1 dmi-3.1.1 smp vsyscall32
    Configuration:
        boot=normal
        chassis=desktop
        family=To be filled by O.E.M.
        sku=SKU
        uuid=249B70F1-9662-7F4A-8256-4CEDFB3ED871

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         American Megatrends Inc.
Bios Version:        4011
Bios Release:        5.13
Board Vendor:        ASUSTeK COMPUTER INC.
Board Name:          PRIME A320M-K
Board Version:       Rev X.0x
Board Serial:        180321904900416
Board Asset Tag:     Default string

Current boot mode:   UEFI Firmware mode
   --- SecureBoot Status from 'mokutil':
SecureBoot disabled


---------- Memory Information:
              total        used        free      shared  buff/cache   available
Mem:          32034        1579       26830          19        3623       29998
Swap:          2047           0        2047

---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
2: enp6s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
3: wlp7s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    inet 192.168.254.66/24 brd 192.168.254.255 scope global dynamic noprefixroute wlp7s0
    inet6 fe80::2c4b:5a0a:b0c:3ea3/64 scope link noprefixroute 

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
3: wlp7s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: phillip1882-spn


---------- Storage Controller Information From 'lspci':
02:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43b8 (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: ASMedia Technology Inc. Device 1062
        Flags: bus master, fast devsel, latency 0, IRQ 39
        Memory at f7880000 (32-bit, non-prefetchable) [size=128K]
        Expansion ROM at f7800000 [disabled] [size=512K]
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [78] Power Management version 3
        Capabilities: [80] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Kernel driver in use: ahci
        
        09:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61) (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. FCH SATA Controller [AHCI mode]
        Flags: bus master, fast devsel, latency 0, IRQ 41
        Memory at f7900000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [48] Vendor Specific Information: Len=08 <?>
        Capabilities: [50] Power Management version 3
        Capabilities: [64] Express Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=2/2 Maskable- 64bit+
        Capabilities: [d0] SATA HBA v1.0
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [270] Secondary PCI Express
        Kernel driver in use: ahci
        Kernel modules: ahci


---------- File system specs from 'df -h':
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb2      ext4      109G   14G   91G  13% /
/dev/sda1      vfat      511M  5.3M  506M   2% /boot/efi

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1ER1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6FBDB84A-E707-4900-94E3-3523A7AC20F2

Device       Start        End    Sectors   Size Type
/dev/sda1     2048    1050623    1048576   512M EFI System
/dev/sda2  1050624    2549759    1499136   732M Linux filesystem
/dev/sda3  2549760 1953523711 1950973952 930.3G Linux filesystem

Disk /dev/sdb: 111.82 GiB, 120040980480 bytes, 234455040 sectors
Disk model: WDC WDS120G2G0B-
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 25131E3C-D14C-44B7-9CF9-386E8A4CAF06

Device       Start       End   Sectors   Size Type
/dev/sdb1     2048   1050623   1048576   512M EFI System
/dev/sdb2  1050624 234452991 233402368 111.3G Linux filesystem

Disk /dev/mapper/luks-0b07df86-e30b-429e-a3f6-27ba16fc4818: 930.29 GiB, 998881886208 bytes, 1950941184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

---------- Disk/Partition Information From 'lsblk':
NAME                                            SIZE FSTYPE      LABEL MOUNTPOINT                                   MODEL
sda                                           931.5G                                                                ST1000DM003-1ER162
|_sda1                                          512M vfat              /boot/efi                                    
|_sda2                                          732M ext4                                                           
|_sda3                                        930.3G crypto_LUKS                                                    
  `-luks-0b07df86-e30b-429e-a3f6-27ba16fc4818 930.3G LVM2_member                                                    
sdb                                           111.8G
                                    WDC_WDS120G2G0B-00EPW0
|_sdb1                                          512M vfat                                                           
|_sdb2                                        111.3G ext4              /                                            
sr0                                            1024M                                                                TSSTcorp_DVD+_-RW_SH-216DB
   ------- 'lsblk' information continued ...
NAME                                          HOTPLUG PARTUUID
          UUID
sda                                                 0                                      
|_sda1                                              0 ad3b34eb-ffec-4020-bc12-b0b2adbc92c0 4D30-01A0
|_sda2                                              0 cfe496ca-9f4c-4590-a65b-f7ea889162ad 6cbbbe63-ba5c-4f29-9e74-0dba51fd39fa
|_sda3                                              0 f54f3896-1b35-4ab2-99a7-61fbb4f7a3cc 0b07df86-e30b-429e-a3f6-27ba16fc4818
  `-luks-0b07df86-e30b-429e-a3f6-27ba16fc4818       0                                      J1vDLJ-Ev3z-CIz7-rOUN-0qCF-pjtV-P3JnGp
sdb                                                 0                                      
|_sdb1                                              0 296cf2d8-835c-4264-8e8a-61e4b6a0419a A9F9-CEE0
|_sdb2                                              0 63ecefbf-251d-49ac-839d-67f2d7d01eb2 bab1d672-c9ab-42cd-9fef-75440871ee5d
sr0
----------  LUKS Information:
System has a LUKS encrypted filesystem.

---------- Mount Details of '/etc/fstab':
UUID=bab1d672-c9ab-42cd-9fef-75440871ee5d /               ext4    errors=remount-ro 0       1
UUID=4D30-01A0  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
---------- Current Mount Details of 'mount':
/dev/fuse on /run/user/1000/doc type fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro)

---------- USB Information from 'lsusb -t -v':
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/3p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/9p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 7: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
           ID 046d:c52b Logitech, Inc. Unifying Receiver

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: GP107 [GeForce GTX 1050 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: 
           irq:66 
           memory:f6000000-f6ffffff 
           memory:e0000000-efffffff 
           memory:f0000000-f1ffffff
              --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: ubuntu:GNOME 
The Current Desktop Session is: ubuntu 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 16384 x 16384
DVI-D-1 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
The Current Session Type is: x11 
The Current Display Manager is: gdm3
The Current Desktop Theme: 'Yaru'
The Current Virtual TTY's being used are:
        TTY#    Used By
        tty2    gdm-x-session
        tty2    Xorg
        tty2    gnome-session-b
        pts/0   bash
        pts/0   system-info
        pts/0   system-info
        pts/0   less
        pts/0   system-info
        pts/0   ps
        pts/0   awk

---------- Sound Device Information From 'lspci':
01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controlle
r (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] GP107GL High Definit
ion Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 67
        Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel


08:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. Family 17h (Models 10h-1fh) HD Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 68
        Memory at f7500000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [48] Vendor Specific Information: Len=08 <?>
        Capabilities: [50] Power Management version 3
        Capabilities: [64] Express Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
        or more detailed audio information, get and run the script at: http://www.alsa-project.org/alsa-info.sh 
---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal universe
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse

Sources List from SourcesD:

---------- Other Details from 'Various':
The current kernel version is:       5.15.0-52-generic 
    --- Operating System Release Description --- 
The current release description is:  Ubuntu 20.04.5 LTS 

Original Installation Date:          2022-10-18+22:19:23 
Original Installation Media: Ubuntu 20.04.3 LTS "Focal Fossa" - Release amd64 (20210819)
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'

   --- Hardware Enablement Stack (HWE) Informationt:
These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.15.0.52.58
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.4.0.26.32

   --- HWE Package Status from 'dpkg':
Package linux-generic-hwe-20.04 is installed.

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).
   --- User Installed Package List:
curl
neofetch
pastebinit
steam:i386

   --- Installed Snap Package List:
bare
bitwarden
canonical-livepatch
core
core18
core20
gnome-3-28-1804
gnome-3-34-1804
gnome-3-38-2004
gtk-common-themes
kde-frameworks-5-96-qt-5-15-5-core20
kigo
snap-store
snapd
vlc

   --- Installed Flatpak Package List:
Flatpak is not installed

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
phillip1882 :0           Oct 19 19:55 (:0)

The User running this script was: phillip1882
uid=1000(phillip1882)
gid=1000(phillip1882)
groups=1000(phillip1882),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),
120(lpadmin),132(lxd),133(sambashare)

The 'system-info' script was booted from an installed system

The 'system-info' script seems to be running locally

The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=/boot/vmlinuz-5.15.0-52-generic root=UUID=bab1d672-c9ab-42cd-9fef-75440871ee5d ro quiet splash vt.handoff=7
```

---

### Post by TheFu on 2022-10-20
For storage. we see this from the output:
```

UUID=bab1d672-c9ab-42cd-9fef-75440871ee5d /               ext4    errors=remount-ro 0       1
UUID=4D30-01A0  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

---------- File system specs from 'df -h':
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb2      ext4      109G   14G   91G  13% /
/dev/sda1      vfat      511M  5.3M  506M   2% /boot/efi

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1ER1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6FBDB84A-E707-4900-94E3-3523A7AC20F2

Device       Start        End    Sectors   Size Type
/dev/sda1     2048    1050623    1048576   512M EFI System
/dev/sda2  1050624    2549759    1499136   732M Linux filesystem
/dev/sda3  2549760 1953523711 1950973952 930.3G Linux filesystem

Disk /dev/sdb: 111.82 GiB, 120040980480 bytes, 234455040 sectors
Disk model: WDC WDS120G2G0B-
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 25131E3C-D14C-44B7-9CF9-386E8A4CAF06

Device       Start       End   Sectors   Size Type
/dev/sdb1     2048   1050623   1048576   512M EFI System
/dev/sdb2  1050624 234452991 233402368 111.3G Linux filesystem

Disk /dev/mapper/luks-0b07df86-e30b-429e-a3f6-27ba16fc4818: 930.29 GiB, 998881886208 bytes, 1950941184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

---------- Disk/Partition Information From 'lsblk':
NAME                                            SIZE FSTYPE      LABEL MOUNTPOINT                                   MODEL
sda                                           931.5G                                                                ST1000DM003-1ER162
|_sda1                                          512M vfat              /boot/efi                                    
|_sda2                                          732M ext4                                                           
|_sda3                                        930.3G crypto_LUKS                                                    
  `-luks-0b07df86-e30b-429e-a3f6-27ba16fc4818 930.3G LVM2_member                                                    
sdb                                           111.8G
                                    WDC_WDS120G2G0B-00EPW0
|_sdb1                                          512M vfat                                                           
|_sdb2                                        111.3G ext4              /                                            
sr0                                            1024M                                                                TSSTcorp_DVD+_-RW_SH-216DB
   ------- 'lsblk' information continued ...
NAME                                          HOTPLUG PARTUUID
          UUID
sda                                                 0                                      
|_sda1                                              0 ad3b34eb-ffec-4020-bc12-b0b2adbc92c0 4D30-01A0
|_sda2                                              0 cfe496ca-9f4c-4590-a65b-f7ea889162ad 6cbbbe63-ba5c-4f29-9e74-0dba51fd39fa
|_sda3                                              0 f54f3896-1b35-4ab2-99a7-61fbb4f7a3cc 0b07df86-e30b-429e-a3f6-27ba16fc4818
  `-luks-0b07df86-e30b-429e-a3f6-27ba16fc4818       0                                      J1vDLJ-Ev3z-CIz7-rOUN-0qCF-pjtV-P3JnGp
sdb                                                 0                                      
|_sdb1                                              0 296cf2d8-835c-4264-8e8a-61e4b6a0419a A9F9-CEE0
|_sdb2                                              0 63ecefbf-251d-49ac-839d-67f2d7d01eb2 bab1d672-c9ab-42cd-9fef-75440871ee5d
sr0
----------  LUKS Information:
System has a LUKS encrypted filesystem.

---------- Mount Details of '/etc/fstab':
---------- Current Mount Details of 'mount':
/dev/fuse on /run/user/1000/doc type fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro)

```

It appears to me that you have 2 partitions as EFI when there should only be 1 in a system.  Those 2 partitions are on different storage devices.  Also, you are booting with EFI, which I know little about.  

But I do know about using whole disk encryption. The normal way that gets setup is with LVM and a separate /boot partition, which I'm not seeing.
Further, the / partition being used when you ran this script was on sdb2 when it should be inside the encrypted contain sda3 as a separate logical volume that was mounted.

I don't know the fix, but I do have a suggestion to try:
1) remove/disconnect sdb from the system and reboot.  
2) Ensure that the EFI partition on sda1 is part of the boot process.  As a sort of reference, here's what my encrypted laptop using LUKS looks like, it is EFI booting and a single-disk setup:
```
$ df -Th
Filesystem                   Size  Used Avail Use% Mounted on
/dev/sda1                    511M  4.5M  507M   1% /boot/efi
/dev/sda2                    721M  261M  424M  39% /boot
/dev/mapper/ubuntu--vg-root   25G   19G  4.3G  82% /
/dev/mapper/ubuntu--vg-home   74G   23G   48G  33% /home
/dev/mapper/ubuntu--vg-stuff  99G   65G   30G  69% /stuff

$ blkid
/dev/sda1: UUID="E7E6-D023" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="8cd37b7a-fdc2-4f65-ac40-e8936f30012b"
/dev/sda2: UUID="d62de6a2-5b69-4d3a-8a31-91040d274d9e" TYPE="ext2" PARTUUID="4e8fd15d-e089-42b9-903f-9743b9b32cbd"
[b]/dev/sda3: UUID="f67e63db-8777-4836-aff8-f2dcb9bb32fc" TYPE="crypto_LUKS" PARTUUID="c9fcab8a-e310-4e60-9dc9-08b3853a4d40"
/dev/mapper/sda3_crypt: UUID="M3j3pO-VrTd-DmUc-kjwt-lA2B-52Se-a52mf8" TYPE="LVM2_member"[/b]
/dev/mapper/ubuntu--vg-root: UUID="71cbf64b-728a-434b-809a-2700f34c699f" TYPE="ext4"
/dev/mapper/ubuntu--vg-home: UUID="fcdd553f-1edf-4c07-9cf8-541f9c7ace44" TYPE="ext4"
/dev/mapper/ubuntu--vg-stuff: UUID="3261fa78-ef7e-460f-b7ff-1f50cf0c793b" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="eb20b030-a7e8-4a1a-a9a9-5f5d668e2e0f" TYPE="swap"

/etc/fstab:
UUID=E7E6-D023  /boot/efi       vfat    umask=0077      0 1
UUID=d62de6a2-5b69-4d3a-8a31-91040d274d9e /boot   ext2 defaults,noatime 0 2
/dev/mapper/ubuntu--vg-root   /      ext4 noatime,errors=remount-ro 0 1
/dev/mapper/ubuntu--vg-home   /home  ext4 errors=remount-ro,noatime 0 2
/dev/mapper/ubuntu--vg-stuff  /stuff ext4 errors=remount-ro,noatime 0 2 
/dev/mapper/ubuntu--vg-swap_1 none   swap sw              0       0 
```

See how all the LVM LVs are contained inside the sda3 crypt_LUKS container?  To see the connections, maybe getting out a few colored highlighters to show which UUIDs go where would be helpful?

After you unlock the LUKs container, it should boot using the OS and partitions/LVs inside the LUKS container.
I'm a little confused by there being a / on a different device, outside the LUKS container.  That isn't how Ubuntu sets up LUKS.

In my sample output, I removed all the junk file systems and loop devices which don't count and just junk up the output.

Anyway, hope this is helpful.  Don't forget to disconnect the sdb drive.  It looks like a SATA SSD. I have no idea how two EFI partitions happened.  That isn't the standard and it causes issues, if you aren't expert.  There are EFI boot tools, which I've not used that allow picking which EFI partition and which OS that EFI partition knows about to be booted. Maybe someone else can slurp through all this and provide suggestions.

---

### Post by phillip1882 on 2022-10-20
ok, yeah i have no idea what our talking about. should i format my drive and start over?
i just installed it so i won't lose anything with the format.
if this would be the best option in terms of ease, what setting should i use with the install?

---

### Post by oldfred on 2022-10-20
You can have an ESP - efi system partition on every drive.
It just Ubuntu's Ubquity installer will only install grub2's UEFI boot files to whatever drive is seen as first. Other distributions and BIOS installs of Ubuntu let you choose.
Old but valid bug with various work arounds, if you do not want first drive's ESP as default.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

You can use Boot-Repair to reinstall grub and in advanced mode the option to choose which ESP then works.
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & 


UEFI uses GUID or partuuid to know which ESP to use. Then in that ESP is a 3 line grub.cfg that uses configfile type grub entry to load the full grub.cfg that is in your install.

You can see partuuid & uuids with this:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
This will show which guid is used to find grub in ESP.
sudo efibootmgr -v

For secuity reasons Ubuntu now mounts ESP with umask=0077 preventing access.
And it is not default mounted with live installer.
but file is /EFI/ubuntu/grub.cfg and mounted at /boot/efi. This is mine with my UUID of my install.

```
[FONT=monospace][COLOR=#54ff54]**fred**[/COLOR][/FONT][FONT=monospace][COLOR=#54ff54]**@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /boot/efi/EFI/ubuntu/grub.cfg [/COLOR]
search.fs_uuid 3c01cc90-636c-4a7e-aa12-fe610d95d5f3 root 
set prefix=($root)'/boot/grub' 
configfile $prefix/grub.cfg
[/FONT]
```

---

### Post by TheFu on 2022-10-21
> **phillip1882 said:**
> ok, yeah i have no idea what our talking about. should i format my drive and start over?
i just installed it so i won't lose anything with the format.
if this would be the best option in terms of ease, what setting should i use with the install?

If there is nothing you want/need on the system, if it were me, I'd leave just the SSD connected, disconnect the other HDD, and do a fresh install.  You can choose if you want LVM or whole disk encryption and the installer (and you) won't get confused by having too many choices.  If you choose "whole disk encryption" (or whatever the installer calls it), then the entire SSD will be wiped, EFI, /boot, and / will be setup during the installation.  / will be created inside the encrypted container which is usually sda3.    

Before doing too much, if it were me, I'd reduce the / logical volume to 40G, create a swap LV of 4.1G, and make a 20G LV for /home.  That's about the minimal I'd do, though I'd probably make an LV for /var of 4-10G, depending on how many snap packages will be used.  All of that will easily fit in the 100G+ SSD.  However, the learning curve for LVM can be steep if you aren't already familar with enterprise volume managers like Veritas.  OTOH, if you know Veritas Volume Manager, it is essentially the same in Linux with LVM.  Any LVM tutorial you find, regardless of the linux distro is fine.  It hasn't really changed in 15 yrs unless you want to do some more advanced things like RAID.  LVM is LVM regardless of the linux distro.

After all that is addressed and the system is booting with each LV as you like mounted, then it is time to reconnect the spinning HDD and mount any partitions you have in that device, as you wish.  Use the /etc/fstab file for this. Don't just point-n-click to cause a mount.  I think gnome-disks has a GUI which can help setup the fstab file and mounts. I've never used it. For a long time it didn't create the best options, especially for non-native file systems like NTFS or whatever other file systems non-linux OSes use.

If this all seems complex, you can ignore the last 3 paragraphs in this post and have a less organized setup with some security issues.  Splitting up mounts is a way to control some mount security options that help protect the entire system.  Also, if /var fills up and isn't shared, that isn't a way to gain a back door like it is when the whole OS is on the same file system and gets full.  Unix security is full of subtle considerations.  As a home user, doing only home user stuff, the risks are fairly small for the issues that separate mounts with different options can protect against.

---

### Post by phillip1882 on 2022-10-22
> Before doing too much, if it were me, I'd reduce the / logical volume to 40G, create a swap LV of 4.1G, and make a 20G LV for /home. That's about the minimal I'd do, though I'd probably make an LV for /var of 4-10G, depending on how many snap packages will be used. All of that will easily fit in the 100G+ SSD. However, the learning curve for LVM can be steep if you aren't already familar with enterprise volume managers like Veritas. OTOH, if you know Veritas Volume Manager, it is essentially the same in Linux with LVM. Any LVM tutorial you find, regardless of the linux distro is fine. It hasn't really changed in 15 yrs unless you want to do some more advanced things like RAID. LVM is LVM regardless of the linux distro.

yeah i dont think i want LVM. can you give me step by step instructions on how to do everything in this paragraph?

---

### Post by phillip1882 on 2022-10-22
> If this all seems complex, you can ignore the last 3 paragraphs in this post and have a less organized setup with some security issues. Splitting up mounts is a way to control some mount security options that help protect the entire system. Also, if /var fills up and isn't shared, that isn't a way to gain a back door like it is when the whole OS is on the same file system and gets full. Unix security is full of subtle considerations. As a home user, doing only home user stuff, the risks are fairly small for the issues that separate mounts with different options can protect against. 
can you be more specific on what i should do?

---

### Post by TheFu on 2022-10-22
> **phillip1882 said:**
> can you be more specific on what i should do?

Straight partitions and file systems can work great, but flexibility is lost and changing things later is harder. It is a pay me now vs pay me later problem.  Perhaps later would be easier?  IDK.  

LVM is required to have whole drive encryption in Ubuntu. It is easy to request at installation time.  Check the box.  That's it. If having 1 big logical volume works for you, great.  It isn't the end of the world NOT to split off separate LVs for specific users.  It is just easier to do that right after an install, not later after the LV has lots of files and is very full.

If you'd like to see how others setup their systems with LVM, I think LHammons posts his server setup steps somewhere.  [https://hammondslegacy.com/forum/viewtopic.php?p=811#p811](https://hammondslegacy.com/forum/viewtopic.php?p=811#p811)  The instructions are from 2020, so I think they should work, though for a desktop, the "root" LV needs to start with 35G size, perhaps 40G. I'd suggest making the other LVs the sizes I listed too, just to make for each LV starting allocation closer to the likely needed size, but not wasteful.  Extending an LV size is 5 seconds, provided the VG has available room and ext4 is the file system used. 1 command. No reboot.   'lvextend' is the command to look up.  To add 1G more to an existing LV, say with the VG name "vg00" and LV name "home", use this command:
```
$ sudo    lvextend     --resizefs       --size +1G      /dev/vg00/home     /dev/nvme0n1p3
  Size of logical volume vg00/home changed from 25.00 GiB (6400 extents) to 26.00 GiB (6656 extents).
  Logical volume vg00/home successfully resized.
resize2fs 1.45.5 (07-Jan-2020)
Filesystem at /dev/mapper/vg00-home is mounted on /home; on-line resizing required
old_desc_blocks = 4, new_desc_blocks = 4
The filesystem on /dev/mapper/vg00-home is now 6815744 (4k) blocks long.
```
Worked perfectly, as expected.  The lvextend man page has the detailed for each option.  

```
$ df -Th  /home
Filesystem      Size  Used Avail Use% Mounted on
/dev/vg00/home   26G  9.8G   15G  41% /home
```
It was 25GB, now it is 26GB

No screwing around with partitions, gparted, fdisk, parted, gnome-disks whatever. Just that single command, lvextend, to resize the LV and the file system. The command took under 2 seconds to complete. It wouldn't matter if it was 1GB or 500GB.  Size doesn't matter for the command run time.

---

### Post by Dennis N on 2022-10-23
**_A case where LVM would serve you better:_**

3 OS + 1 shared data partition. Standard installs to partitions:

sda1 OS 1 with  5 GB free
sda2 OS 2 with  2 GB free
sda3 OS 3 with 10 GB free
sda4 Data Partition with  40 GB free

Suppose I need 10 GB additional space for OS 2. I can't easily enlarge this partition.

If the 3 OS and data partition had been installed in logical volumes in a volume group, then the 57 GB of free space is available to any of the OS (or the Data logical volume) for space expansion with a  terminal command. If there is some free space on your storage disk, you can also create another physical volume and add it to the existing volume group to provide new available space.
---------------------------------------------
I started learning LVM with the tutorial linked just below. There are many other tutorial type articles on LVM.

[https://tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](https://tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

Even though written in the era of Ubuntu 12.10, the terminal commands have not changed. But the GUI tool mentioned no longer is available. 
The only GUI tool I know of for LVM is **blivet-gui** available on Fedora.

---

### Post by phillip1882 on 2022-10-24
i just want a clean simple install with no hassles. no encryption, the ability to access both drives from the file manager.
what should i do during the installation process of the operating system to get this?

---

### Post by Dennis N on 2022-10-24
If you only plan to have one operating system installed, I would let the installer take care of setting up the disk. Just use the "Erase disk and install Ubuntu" choice for Installation type. The installer will complete the install and use the entire disk. 

If you think you might add a second Linux later (dual boot), then you have to use the "Something Else" optiion for Installation type and select the partition for the installation on the next screen. You can do all the partitioning needed from this screen, or prepare the disk with gparted before you start the installer. Either way. 

You can have the second disk be mounted in the /etc/fstab table on startup, or do it yourself from the file manager (You can change to the first method later on).

---

### Post by phillip1882 on 2022-10-24
i thought i did that the first time. what i mean is i don't think i tried to modify how data is stored with that efi thing that seems to be the cause of my problem now.

---

### Post by TheFu on 2022-10-24
I'd still suggest only having 1 disk connected to the computer during the install, since there seems to be confusion about which disk is being used, when.

When you do the install, do not check the encryption box or use LVM box.

Post install, you can connect the other disk and mount it via the /etc/fstab.  There are lots of threads here about doing that.  Please don't use the file manager to do it, since it wouldn't mount after any reboot until you go and select it.  That's sub-optimal.  1 line in the /etc/fstab will mount a file system and you get to decide where that mount will be.

Looking over the prior disk information, it seems that in that install, someone selected to have at least 1 partition encrypted. This isn't automatic. It requires positive action by the installer (human).

---

### Post by phillip1882 on 2022-10-25
ok i disconnected the second hard drive and have done a complete format and reinstall of ubuntu.
where can i find how to add my second hard drive?

---

### Post by TheFu on 2022-10-25
> **phillip1882 said:**
> ok i disconnected the second hard drive and have done a complete format and reinstall of ubuntu.
where can i find how to add my second hard drive?

As said previously, 
> Post install, you can connect the other disk and mount it via the /etc/fstab. **There are lots of threads here about doing that.** 
[Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843) is one of those posts, I think.

You can also google for 'ubuntu mount /etc/fstab'   Pretty much all Linux systems work the same.

---

