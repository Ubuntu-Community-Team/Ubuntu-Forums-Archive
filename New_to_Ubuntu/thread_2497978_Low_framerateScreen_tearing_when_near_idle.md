---
title: "Low framerate/Screen tearing when near idle"
date: 2024-05-24
forum: New to Ubuntu
---

### Post by youbuntnoob on 2024-05-24
Hello,

I am very new to Ubuntu/linux but have just installed Ubuntu on an asus laptop. 
I'm seeing severe framerate drops and screen tearing when just moving the mouse around the desktop HOWEVER this completely goes away if I have any video playing, even just in browser youtube on firefox. 

I've updated the bios on the laptop, and the amd firmware.

Any help is much appreciated


System info script output below:

```
Starting the Ubuntu Forums 'system-info' Report: 2024-05-24  20:56:46 BST (+0100)
    Part of the Ama-gi Project
    Version: 02.00-09, Script Date: 2023.11.28

---------------------------------------------------------------
Main Complaint: Low Framerate and screen tearing when moving mouse EXCEPT during video playback
Problem Description:  New to Ubuntu/linux - just installed on an asus tuf gaming advantage efdition laptop. When moving the mouse (touchpad) or scrolling on the desktop there is stuttering/extreme framerate drops with screen tearing. This is completely solved when any video playback is occurring, even just a youtube video in firefox off in a corner of the screen
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: AMD Ryzen 7 7435HS
    Vendor: Advanced Micro Devices [AMD]
    Physical id: d
    Bus info: cpu@0
    Version: 25.68.1
    Serial: [REMOVED]
    Slot: FP7r2
    Size: 1468MHz
    Capacity: 4553MHz
    Width: 64 bits
    Clock: 100MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht 
        syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good 
        nopl nonstop_tsc cpuid extd_apicid aperfmperf rapl pni pclmulqdq 
        monitor ssse3 fma cx16 sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx 
        f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 
        misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core 
        perfctr_nb bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate ssbd 
        mba ibrs ibpb stibp vmmcall fsgsbase bmi1 avx2 smep bmi2 erms invpcid 
        cqm rdt_a rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec 
        xgetbv1 xsaves cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local 
        user_shstk clzero irperf xsaveerptr rdpru wbnoinvd cppc arat npt lbrv 
        svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists 
        pausefilter pfthreshold avic v_vmsave_vmload vgif v_spec_ctrl umip pku 
        ospke vaes vpclmulqdq rdpid overflow_recov succor smca fsrm debug_swap 
        cpufreq
    Configuration: cores=8 enabledcores=8 microcode=171983109 
        threads=16

computer
    Description: Notebook
    Product: ASUS TUF Gaming A16 FA617NTR_FA617NTR
    Vendor: ASUSTeK COMPUTER INC.
    Version: 1.0
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-3.4.0 dmi-3.4.0 smp vsyscall32
    Configuration:
        boot=normal
        chassis=notebook
        family=ASUS TUF Gaming A16
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         American Megatrends International LLC.
Bios Version:        FA617NTR.305
Bios Release:        5.24
Board Vendor:        ASUSTeK COMPUTER INC.
Board Name:          FA617NTR
Board Version:       1.0
Board Serial:        CUZ43M20010
Board Asset Tag:     ATN12345678901234567

Current boot mode:   UEFI Firmware mode
   --- SecureBoot Status from 'mokutil':
SecureBoot disabled


---------- Memory Information:
               total        used        free      shared  buff/cache   available
Mem:           15730        4226        9738          96        2161       11503
Swap:           4095           0        4095

---------- Swap Information:
  --- Info from 'fstab'
/swap.img    none    swap    sw    0    0

  --- Info from '/proc/swaps'
Filename                Type        Size        Used        Priority
/swap.img                               file        4194300        0        -2

  --- System Swapiness Settings
Valid swappiness settings are from 10 - 60 . 
Current setting in '/proc/sys/vm/swappiness': 60 
Current configuration setting in '/etc/sysctl.conf file: 


---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
3: wlp6s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
3: wlp6s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000

For more detailed wireless information, get and run the script at [https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info) 

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: LarryLaptop


---------- Storage Controller Information From 'lspci':
04:00.0 Non-Volatile memory controller: Sandisk Corp WD Black SN770 / PC SN740 256GB / PC SN560 (DRAM-less) NVMe SSD (rev 01) (prog-if 02 [NVM Express])
    Subsystem: Sandisk Corp WD Black SN770 / PC SN740 256GB / PC SN560 (DRAM-less) NVMe SSD
    Flags: bus master, fast devsel, latency 0, IRQ 47, IOMMU group 17
    Memory at fcf00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [b0] MSI-X: Enable+ Count=65 Masked-
    Capabilities: [c0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [1b8] Latency Tolerance Reporting
    Capabilities: [300] Secondary PCI Express
    Capabilities: [900] L1 PM Substates
    Capabilities: [910] Data Link Feature <?>
    Capabilities: [920] Lane Margining at the Receiver <?>
    Capabilities: [9c0] Physical Layer 16.0 GT/s <?>
    Kernel driver in use: nvme
    Kernel modules: nvme


---------- File system specs from 'df -h':
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/nvme0n1p2 ext4      937G   13G  877G   2% /
efivarfs       efivarfs  128K   61K   63K  49% /sys/firmware/efi/efivars
/dev/nvme0n1p1 vfat      1.1G  6.2M  1.1G   1% /boot/efi

---------- Disk/Partition Information From 'fdisk':

Disk /dev/nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: WD PC SN560 SDDPNQE-1T00-1002           
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A0B0B930-6370-47EE-88D5-84B3C1DB102C

Device           Start        End    Sectors   Size Type
/dev/nvme0n1p1    2048    2203647    2201600     1G EFI System
/dev/nvme0n1p2 2203648 2000406527 1998202880 952.8G Linux filesystem


---------- Disk/Partition Information From 'lsblk':
NAME          SIZE FSTYPE   LABEL MOUNTPOINT                          MODEL
nvme0n1     953.9G                                                    WD PC SN560 SDDPNQE-1T00-1002
|_nvme0n1p1     1G vfat           /boot/efi                           
|_nvme0n1p2 952.8G ext4           /                                   
   ------- 'lsblk' information continued ...
NAME        HOTPLUG PARTUUID                             UUID
nvme0n1           0                                      
|_nvme0n1p1       0 cf1719c2-35a7-41c3-95cf-d8416d62e65c F163-156E
|_nvme0n1p2       0 b6b9b666-0f28-4630-8ce6-bc1b34a1b95e ef5ce500-4d17-4827-9d52-e508a495f0fe

----------  BTRFS Information:
There are no BTRFS vdev's present.

----------  LVM2 Information:
There are no LVM2 volumes present.

----------  mdadm RAID Information:
No active md devices present.
---------- Mount Details of '/etc/fstab':
/dev/disk/by-uuid/ef5ce500-4d17-4827-9d52-e508a495f0fe / ext4 defaults 0 1
/dev/disk/by-uuid/F163-156E /boot/efi vfat defaults 0 1
/swap.img    none    swap    sw    0    0

---------- Current Mount Details of 'mount':
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p2 on / type ext4 (rw,relatime)
/dev/nvme0n1p2 on /var/snap/firefox/common/host-hunspell type ext4 (ro,noexec,noatime)

For more detailed disk Information, please run the 'boot-info' script 
from: (STABLE) [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair) 

---------- USB Information from 'lsusb -t -v':
/:  Bus 001.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 002.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/2p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 003.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/3p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 003: Dev 002, If 0, Class=Video, Driver=uvcvideo, 480M
        ID 13d3:56a2 IMC Networks 
    |__ Port 003: Dev 002, If 1, Class=Video, Driver=uvcvideo, 480M
        ID 13d3:56a2 IMC Networks 
/:  Bus 004.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/2p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 005.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 001: Dev 002, If 0, Class=Wireless, Driver=btusb, 480M
        ID 13d3:3563 IMC Networks 
    |__ Port 001: Dev 002, If 1, Class=Wireless, Driver=btusb, 480M
        ID 13d3:3563 IMC Networks 
    |__ Port 001: Dev 002, If 2, Class=Wireless, Driver=[none], 480M
        ID 13d3:3563 IMC Networks 
/:  Bus 006.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/0p, 5000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 007.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 008.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 009.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 010.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: Navi 33 [Radeon RX 7700S/7600/7600S/7600M XT/PRO W7600]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: /dev/fb0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=amdgpu latency=0 mode=1920x1200 resolution=1920,1200 visual=truecolor xres=1920 yres=1200
       resources: 
           iomemory:7c0-7bf 
           iomemory:7e0-7df 
           irq:79 
           memory:7c00000000-7dffffffff 
           memory:7e00000000-7e0fffffff 
           ioport:f000(size=256) 
           memory:fcb00000-fcbfffff 
           memory:fcc00000-fcc1ffff

   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: ubuntu:GNOME 
The Current Desktop Session is: ubuntu 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 16 x 16, current 1920 x 1200, maximum 32767 x 32767
eDP-1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 340mm x 210mm
The Current Session Type is: wayland 
The Current Display Manager is: gdm3
The Current Desktop Theme: 'Yaru-dark'
The Current Virtual TTY's being used are:
    TTY#    Used By
    tty2    gdm-wayland-ses
    tty2    gnome-session-b
    pts/0    system-info
    pts/0    system-info
    pts/0    sed
    pts/0    system-info
    pts/0    ps
    pts/0    awk

---------- Sound Device Information From 'lspci':
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Navi 31 HDMI/DP Audio
    Subsystem: ASUSTeK Computer Inc. Navi 31 HDMI/DP Audio
    Flags: bus master, fast devsel, latency 0, IRQ 76, IOMMU group 16
    Memory at fcc20000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Capabilities: [2a0] Access Control Services
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


07:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] ACP/ACP3X/ACP6x Audio Coprocessor (rev 60)
    Subsystem: ASUSTeK Computer Inc. ACP/ACP3X/ACP6x Audio Coprocessor
    Flags: bus master, fast devsel, latency 0, IRQ 75, IOMMU group 24
    Memory at fc700000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [2a0] Access Control Services
    Kernel driver in use: snd_pci_acp6x
    Kernel modules: snd_pci_acp3x, snd_rn_pci_acp3x, snd_pci_acp5x, snd_pci_acp6x, snd_acp_pci, snd_rpl_pci_acp6x, snd_pci_ps, snd_sof_amd_renoir, snd_sof_amd_rembrandt, snd_sof_amd_vangogh, snd_sof_amd_acp63


07:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h/19h HD Audio Controller
    DeviceName: HD Audio Controller
    Subsystem: ASUSTeK Computer Inc. Family 17h/19h HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 78, IOMMU group 25
    Memory at fc740000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [2a0] Access Control Services
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


For more detailed audio information, get and run the script at: [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) 

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:


Sources List from SourcesD:
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
/etc/apt/sources.list.d/ubuntu.sources.save:
Types: deb
URIs: [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)
Suites: noble noble-updates noble-backports noble-proposed
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
Types: deb
URIs: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
Suites: noble-security
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
/etc/apt/sources.list.d/ubuntu.sources:
Types: deb
URIs: [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)
Suites: noble noble-updates noble-backports
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
Types: deb
URIs: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
Suites: noble-security
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg

---------- KeyMap and Locale Information from from various sources:
   --- Keymap Info from 'setxkbmap' ----
rules:      evdev
model:      pc105
layout:     us

   --- Locale Info from 'localectl' ----
System Locale: LANG=en_US.UTF-8
    VC Keymap: (unset)
   X11 Layout: gb
    X11 Model: pc105

---------- Other Details from 'Various':
The current kernel version is:       6.8.0-31-generic 
    --- Operating System Release Description --- 
The current release description is:  Ubuntu 24.04 LTS 

Original Installation Date:          2024-05-24+19:34:30 
Original Installation Media: Ubuntu 24.04 LTS "Noble Numbat" - Release amd64 (20240424)
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'

   --- Hardware Enablement Stack (HWE) Informationt:
These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-24.04, Kernel Version: 6.8.0-31.31

   --- HWE Package Status from 'dpkg':
Package linux-generic-hwe-24.04 is installed.

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

   --- User Installed Package List:
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
login
m17n-db
mythes-en-au
mythes-en-us
ncurses-base
ncurses-bin
shim-signed
thunderbird-locale-en
thunderbird-locale-en-gb
thunderbird-locale-en-us
ubuntu-desktop
ubuntu-desktop-minimal
ubuntu-minimal
ubuntu-restricted-addons
ubuntu-standard
ubuntu-wallpapers
wpasupplicant

   --- Installed Snap Package List:
bare
core20
core22
curl
firefox
firmware-updater
gnome-42-2204
gtk-common-themes
snap-store
snapd
snapd-desktop-integration
thunderbird

   --- Installed Flatpak Package List:
Flatpak is not installed

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
dad      seat0        May 24 20:19 (login screen)
dad      tty2         May 24 20:19 (tty2)

The User running this script was: dad
uid=1000(dad)
gid=1000(dad)
groups=1000(dad),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),
100(users),114(lpadmin)

The 'system-info' script was booted from an installed system

The 'system-info' script seems to be running locally

The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=/boot/vmlinuz-6.8.0-31-generic root=UUID=ef5ce500-4d17-4827-9d52-e508a495f0fe ro quiet splash vt.handoff=7

---- Required Programs For Report.
    --- Some Programs This Script Uses Were Missing --- 
    pastebinit

*** End Of Report ***
```

---

### Post by youbuntnoob on 2024-05-25
Slight update - I've tried connecting to an external monitor via HDMI and that also solves the problem, *but only for the external monitor* - if I then mouse back over to the laptop screen the stuttering/screen tearing resumes. I've tried various different resolutions and refresh rates, with Variable Refresh Rate on and off, problem persists.

---

### Post by youbuntnoob on 2024-05-27
A further update: I've tried installiong asusctrl/supergfxctl and changing the mode but the issue persists.
I believe I have the same issue as is listed here: [https://old.reddit.com/r/linuxquestions/comments/1ctnyj1/asus_tuf_a16_fa617_linux_flickering/](https://old.reddit.com/r/linuxquestions/comments/1ctnyj1/asus_tuf_a16_fa617_linux_flickering/)
But as you can see it's unsolved.

Should I be moving this post to a hardware forum?

---

### Post by gezzer2 on 2024-05-27
have a look here on the Linux Mint forum ..

[https://forums.linuxmint.com/viewtopic.php?t=409861](https://forums.linuxmint.com/viewtopic.php?t=409861)

as it maybe the settings for the monitor that are causing the problems ..

---

