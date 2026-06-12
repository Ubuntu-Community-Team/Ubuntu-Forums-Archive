---
title: "Ubuntu 20.04 new install - ACPI BIOS Error (bug)"
date: 2020-06-09
forum: New to Ubuntu
---

### Post by cryptokevin on 2020-06-09
i have tried to search to find similar error for Ubuntu 20.04 per forum recommendations to no avail.  As a result, I am posting new message to address an ACPI BIOS Error that is appearing in logs.  

Please note I am a newbie transitioning from Windows 10 on my HP Spectre.  The following is posted in order for you to provide assistance to me:


lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal


root@cyrptokevin:/# uname
Linux


root@cyrptokevin:/# inxi -Fz
System:    Kernel: 5.4.0-33-generic x86_64 bits: 64 Desktop: Gnome 3.36.2 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Convertible System: HP product: HP Spectre x360 Convertible 15-df0xxx v: N/A serial: <filter> 
           Mobo: HP model: 8518 v: 10.47 serial: <filter> UEFI: AMI v: F.28 date: 04/08/2019 
Battery:   ID-1: BAT0 charge: 81.3 Wh condition: 81.3/81.3 Wh (100%) 
CPU:       Topology: Quad Core model: Intel Core i7-8565U bits: 64 type: MT MCP L2 cache: 8192 KiB 
           Speed: 1467 MHz min/max: 400/4600 MHz Core speeds (MHz): 1: 1613 2: 1751 3: 3409 4: 3633 5: 3741 6: 3836 7: 3043 
           8: 2476 
Graphics:  Device-1: Intel UHD Graphics 620 driver: i915 v: kernel 
           Device-2: NVIDIA GP108M [GeForce MX150] driver: N/A 
           Display: server: X.Org 1.20.8 driver: modesetting,nvidia unloaded: fbdev,nouveau,vesa resolution: 3840x2160~60Hz 
           OpenGL: renderer: Mesa Intel UHD Graphics 620 (WHL GT2) v: 4.6 Mesa 20.0.4 
Audio:     Device-1: Intel Cannon Point-LP High Definition Audio driver: sof-audio-pci 
           Sound Server: ALSA v: k5.4.0-33-generic 
Network:   Device-1: Intel Cannon Point-LP CNVi [Wireless-AC] driver: iwlwifi 
           IF: wlp0s20f3 state: up mac: <filter> 
Drives:    Local Storage: total: 476.94 GiB used: 10.26 GiB (2.2%) 
           ID-1: /dev/nvme0n1 vendor: Toshiba model: N/A size: 476.94 GiB 
Partition: ID-1: / size: 467.96 GiB used: 10.25 GiB (2.2%) fs: ext4 dev: /dev/nvme0n1p2 
Sensors:   System Temperatures: cpu: 47.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 276 Uptime: 1h 27m Memory: 15.30 GiB used: 1.98 GiB (12.9%) Shell: bash inxi: 3.0.38 


root@cyrptokevin:/# dmesg | grep -i -e "Error"
[    0.193990] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.XDCI], AE_NOT_FOUND (20190816/dswload2-159)
[    0.193994] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20190816/psobject-220)
[    0.194464] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.I2C1.TPL1], AE_NOT_FOUND (20190816/dswload2-159)
[    0.194467] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20190816/psobject-220)
[    0.194971] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.GPLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.194973] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.194975] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.TPLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.194977] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.194979] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.GUPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.194980] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.194983] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.TUPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.194985] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.195009] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS01._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.195011] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.195013] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS01._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.195015] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.196503] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS02._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.196505] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.196507] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS02._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.196509] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.197926] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS03._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.197929] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.197931] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS03._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.197932] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.199413] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS04._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.199415] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.199417] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS04._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.199419] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.200899] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS05._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.200901] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.200903] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS05._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.200905] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.202388] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS06._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.202391] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.202392] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS06._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.202394] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.203873] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS07._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.203875] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.203877] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS07._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.203879] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.205365] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS08._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.205367] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.205369] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS08._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.205371] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.206851] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS09._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.206853] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.206854] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS09._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.206856] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.208338] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS10._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.208340] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.208341] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS10._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.208343] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.209878] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.USR1._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.209880] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.209882] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.USR1._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.209884] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.209887] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.USR2._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.209888] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.209890] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.USR2._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.209892] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.209919] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS01._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.209920] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.209922] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS01._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.209924] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.209951] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS02._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.209953] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.209954] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS02._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.209956] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.209983] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS03._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.209985] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.209986] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS03._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.209988] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.210014] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS04._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.210016] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.210018] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS04._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.210020] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.210046] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS05._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.210048] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.210050] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS05._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.210051] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.210078] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS06._UPC], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.210079] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.210081] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS06._PLD], AE_ALREADY_EXISTS (20190816/dswload2-323)
[    0.210083] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.210161] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.XDCI], AE_NOT_FOUND (20190816/dswload2-159)
[    0.210163] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20190816/psobject-220)
[    0.287611] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.I2C1.TPL1.TDX], AE_NOT_FOUND (20190816/psargs-330)
[    0.287625] ACPI Error: Aborting method \_SB.PCI0.I2C1.INC1 due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
[    0.287631] ACPI Error: Aborting method \_SB.PCI0.I2C1._INI due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
[    0.759243] RAS: Correctable Errors collector initialized.
[    1.964796] EXT4-fs (nvme0n1p2): re-mounted. Opts: errors=remount-ro
[    2.947984] sof-audio-pci 0000:00:1f.3: error: no reply expected, received 0x0
[ 2687.683299] sof-audio-pci 0000:00:1f.3: error: no reply expected, received 0x0


root@cyrptokevin:/# acpidump -s
ACPI: SSDT 0x0000000000000000 002FB0 (v02 HPQOEM 8518     00001000 ACPI 20160527)
ACPI: MCFG 0x0000000000000000 00003C (v01 HPQOEM 8518     01072009 HP   00000097)
ACPI: APIC 0x0000000000000000 0000BC (v04 HPQOEM 8518     01072009 HP   00010013)
ACPI: SSDT 0x0000000000000000 001B1C (v02 HPQOEM 8518     00003000 ACPI 20160527)
ACPI: TPM2 0x0000000000000000 000034 (v04 HPQOEM 8518     00000001 HP   00000000)
ACPI: SSDT 0x0000000000000000 000144 (v02 HPQOEM 8518     00001000 ACPI 20160527)
ACPI: NHLT 0x0000000000000000 0017B0 (v00 HPQOEM 8518     00000002 HP   01000013)
ACPI: SSDT 0x0000000000000000 0000F4 (v02 PmRef  Cpu0Psd  00003000 INTL 20160527)
ACPI: UEFI 0x0000000000000000 000042 (v01 HPQOEM 8518     00000002 HP   01000013)
ACPI: DSDT 0x0000000000000000 04D89C (v02 HPQOEM 8518     01072009 ACPI 20160527)
ACPI: SSDT 0x0000000000000000 0005D0 (v02 HPQOEM 8518     00000000 ACPI 20160527)
ACPI: WSMT 0x0000000000000000 000028 (v01 HPQOEM 8518     01072009 HP   00010013)
ACPI: SSDT 0x0000000000000000 000060 (v01 HPQOEM 8518     00000001 ACPI 20160527)
ACPI: LPIT 0x0000000000000000 00005C (v01 HPQOEM 8518     00000002 HP   01000013)
ACPI: SSDT 0x0000000000000000 003047 (v02 HPQOEM 8518     00000000 ACPI 20160527)
ACPI: DBG2 0x0000000000000000 000054 (v00 HPQOEM 8518     00000002 HP   01000013)
ACPI: SSDT 0x0000000000000000 000539 (v02 HPQOEM 8518     00001000 ACPI 20160527)
ACPI: SSDT 0x0000000000000000 0031C6 (v02 HPQOEM 8518     00003000 ACPI 20160527)
ACPI: DMAR 0x0000000000000000 0000A8 (v01 HPQOEM 8518     00000002 HP   01000013)
ACPI: FACP 0x0000000000000000 000114 (v06 HPQOEM SLIC-MPC 01072009 HP   00010013)
ACPI: FPDT 0x0000000000000000 000044 (v01 HPQOEM 8518     01072009 HP   00010013)
ACPI: SSDT 0x0000000000000000 004923 (v02 HPQOEM 8518     00001000 ACPI 20160527)
ACPI: MSDM 0x0000000000000000 000055 (v03 HPQOEM SLIC-MPC 00000001 HP   00010013)
ACPI: SSDT 0x0000000000000000 000DCF (v02 HPQOEM 8518     00001000 ACPI 20160527)
ACPI: DBGP 0x0000000000000000 000034 (v01 HPQOEM 8518     00000002 HP   01000013)
ACPI: SSDT 0x0000000000000000 002347 (v01 HPQOEM 8518     00001000 ACPI 20160527)
ACPI: HPET 0x0000000000000000 000038 (v01 HPQOEM 8518     00000002 HP   01000013)
ACPI: SSDT 0x0000000000000000 001423 (v02 HPQOEM 8518     00001000 ACPI 20160527)
ACPI: FIDT 0x0000000000000000 00009C (v01 HPQOEM 8518     01072009 HP   00010013)
ACPI: FACS 0x0000000000000000 000040
ACPI: BGRT 0x0000000000000000 000038 (v01 HPQOEM 8518     01072009 HP   00010013)
ACPI: SSDT 0x0000000000000000 00009D (v01 HPQOEM 8518     00000001 ACPI 20160527)
ACPI: SSDT 0x0000000000000000 000724 (v02 PmRef  HwpLvt   00003000 INTL 20160527)
ACPI: SSDT 0x0000000000000000 00053F (v02 PmRef  Cpu0Ist  00003000 INTL 20160527)
ACPI: SSDT 0x0000000000000000 00030A (v02 PmRef  ApCst    00003000 INTL 20160527)
ACPI: SSDT 0x0000000000000000 000317 (v02 PmRef  ApHwp    00003000 INTL 20160527)
ACPI: SSDT 0x0000000000000000 0005FC (v02 PmRef  ApIst    00003000 INTL 20160527)
ACPI: SSDT 0x0000000000000000 00011B (v02 PmRef  Cpu0Hwp  00003000 INTL 20160527)
ACPI: SSDT 0x0000000000000000 000400 (v02 PmRef  Cpu0Cst  00003001 INTL 20160527)
ACPI: SSDT 0x0000000000000000 000AB0 (v02 PmRef  ApPsd    00003000 INTL 20160527)


Please let me know if you need additional info to resolve.

Thanks for your help.

Kevin

---

### Post by dino99 on 2020-06-10
Quite harmless; but check if you can upgrade your bios in case a new one is proposed for your model brand.

---

### Post by cryptokevin on 2020-06-10
> **dino99 said:**
> Quite harmless; but check if you can upgrade your bios in case a new one is proposed for your model brand.

As a result, of your response.  I will not worry about the error message anymore.  Thanks so much.

With respect to updating my bios, a friend made the same suggestion to do so.  I have searched for how to do update the bios, but I am at a loss for how to accomplish doing so.  Can you provide some direction on how to do it.    This is the link I went to initially:  [https://help.ubuntu.com/community/BIOSUpdate](https://help.ubuntu.com/community/BIOSUpdate)

Here is output from dmidecode:

# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.2.1 present.
# SMBIOS implementations newer than version 3.2.0 are not
# fully supported by this version of dmidecode.
Table at 0x4FA89000.

Handle 0x0000, DMI type 0, 26 bytes
BIOS Information
    Vendor: AMI
    Version: F.28
    Release Date: 04/08/2019
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 13312 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        Smart battery is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 15.28
    Firmware Revision: 10.47

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: HP
    Product Name: HP Spectre x360 Convertible 15-df0xxx
    Version:  
    Serial Number: 5CD9035ZD6
    UUID: 39444335-3330-5a35-4436-365a33304435
    Wake-up Type: Power Switch
    SKU Number: 4WW36UA#ABA
    Family: 103C_5335KV HP Spectre

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: HP
    Product Name: 8518
    Version: 10.47
    Serial Number: PHSKL048JBT20V
    Asset Tag: Base Board Asset Tag
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Base Board Chassis Location
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
    Manufacturer: HP
    Type: Convertible
    Lock: Not Present
    Version: Chassis Version
    Serial Number: Chassis Serial Number
    Asset Tag: Not Specified
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0
    SKU Number: Not Specified

Handle 0x0004, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Mouse
    Internal Connector Type: None
    External Reference Designator: PS2Mouse
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0005, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Keyboard
    Internal Connector Type: None
    External Reference Designator: Keyboard
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x0006, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Micro SD
    Internal Connector Type: None
    External Reference Designator: Micro SD
    External Connector Type: Mini Centronics Type-14
    Port Type: Other

Handle 0x0007, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: HDMI
    Internal Connector Type: None
    External Reference Designator: HDMI
    External Connector Type: None
    Port Type: Video Port

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio Jack
    Internal Connector Type: None
    External Reference Designator: Audio Jack
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Right USB 3.1 GEN2
    Internal Connector Type: None
    External Reference Designator: Right Type C
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Right USB 3.1 GEN2
    Internal Connector Type: None
    External Reference Designator: Right Type C
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Right USB 3.1 GEN1
    Internal Connector Type: None
    External Reference Designator: Right Type A
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB4
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000E, DMI type 9, 17 bytes
System Slot Information
    Designation: J6B2
    Type: x16 PCI Express
    Current Usage: In Use
    Length: Long
    ID: 0
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:01.0

Handle 0x000F, DMI type 11, 5 bytes
OEM Strings
    String 1: $HP$
    String 2: ABS 70/71 79 7A 7B 7C
    String 3: BCU_Y
    String 4: BATT_CARE
    String 5: FBYTE#3K6b7B7N7WaBaHapaqasawbVbhbzcbd6dUdpdqfPhZj6.5h;BUILDID#18
    String 6: WW2S5T604#SABA#DABA;
    String 7:  
    String 8:  
    String 9:  
    String 10:  
    String 11:  
    String 12:  
    String 13:  

Handle 0x0010, DMI type 22, 26 bytes
Portable Battery
    Location: Primary
    Manufacturer: 333-27-09-A
    Name: SU06084XL
    Design Capacity: 84080 mWh
    Design Voltage: 11550 mV
    SBDS Version: 1.1
    Maximum Error: Unknown
    SBDS Serial Number: 0469
    SBDS Manufacture Date: 2018-11-09
    SBDS Chemistry: LION
    OEM-specific Information: 0x0008050A

Handle 0x0011, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x0012, DMI type 34, 11 bytes
Management Device
    Description: LM78-1
    Type: LM78
    Address: 0x00000000
    Address Type: I/O Port

Handle 0x0013, DMI type 28, 22 bytes
Temperature Probe
    Description: LM78A
    Location: Motherboard
    Status: OK
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0014, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0015, DMI type 35, 11 bytes
Management Device Component
    Description: Default string
    Management Device Handle: 0x0012
    Component Handle: 0x0013
    Threshold Handle: 0x0014

Handle 0x0016, DMI type 27, 15 bytes
Cooling Device
    Temperature Probe Handle: 0x0013
    Type: Power Supply Fan
    Status: OK
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating
    Description: Cooling Dev 1

Handle 0x0017, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0018, DMI type 35, 11 bytes
Management Device Component
    Description: Default string
    Management Device Handle: 0x0012
    Component Handle: 0x0016
    Threshold Handle: 0x0017

Handle 0x0019, DMI type 27, 15 bytes
Cooling Device
    Temperature Probe Handle: 0x0013
    Type: Power Supply Fan
    Status: OK
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating
    Description: Not Specified

Handle 0x001A, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x001B, DMI type 35, 11 bytes
Management Device Component
    Description: Default string
    Management Device Handle: 0x0012
    Component Handle: 0x0019
    Threshold Handle: 0x001A

Handle 0x001C, DMI type 41, 11 bytes
Onboard Device
    Reference Designation:  Onboard IGD
    Type: Video
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:00:02.0

Handle 0x001D, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x001E, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: SODIMM
    Set: None
    Locator: Bottom - Slot 1 (left)
    Bank Locator: BANK 0
    Type: DDR4
    Type Detail: Synchronous
    Speed: 2667 MT/s
    Manufacturer: Samsung
    Serial Number: 94A66FB5
    Asset Tag: 9876543210
    Part Number: M471A1K43DB1-CTD    
    Rank: 1
    Configured Memory Speed: 2400 MT/s
    Minimum Voltage: 1.2 V
    Maximum Voltage: 1.2 V
    Configured Voltage: 1.2 V

Handle 0x001F, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: SODIMM
    Set: None
    Locator: Bottom - Slot 2 (right)
    Bank Locator: BANK 2
    Type: DDR4
    Type Detail: Synchronous
    Speed: 2667 MT/s
    Manufacturer: Samsung
    Serial Number: 94A66F00
    Asset Tag: 9876543210
    Part Number: M471A1K43DB1-CTD    
    Rank: 1
    Configured Memory Speed: 2400 MT/s
    Minimum Voltage: 1.2 V
    Maximum Voltage: 1.2 V
    Configured Voltage: 1.2 V

Handle 0x0020, DMI type 19, 31 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x003FFFFFFFF
    Range Size: 16 GB
    Physical Array Handle: 0x001D
    Partition Width: 2

Handle 0x0021, DMI type 43, 31 bytes
TPM Device
    Vendor ID: 
    Specification Version: 2.0    Firmware Revision: 7.63
    Description: INFINEON    Characteristics:
        Family configurable via platform software support
    OEM-specific Information: 0x00000000

Handle 0x0022, DMI type 221, 26 bytes
HP BIOS iSCSI NIC PCI and MAC Information
    NIC 1: PCI device 01:00.3, MAC address 00:07:00:47:50:00
    NIC 2: PCI device 00:00.2, MAC address 00:00:00:9A:00:03

Handle 0x0023, DMI type 221, 26 bytes
HP BIOS iSCSI NIC PCI and MAC Information
    NIC 1: PCI device 01:00.3, MAC address 00:07:00:47:50:00
    NIC 2: PCI device 00:00.2, MAC address 00:00:00:00:00:03

Handle 0x0024, DMI type 221, 89 bytes
HP BIOS iSCSI NIC PCI and MAC Information
    NIC 1: PCI device 01:01.4, MAC address 00:07:00:47:50:00
    NIC 2: PCI device 03:00.2, MAC address FF:FF:FF:FF:FF:04
    NIC 3: PCI device ff:00.0, MAC address FF:FF:30:00:05:00
    NIC 4: Not Installed
    NIC 5: Not Installed
    NIC 6: Disabled
    NIC 7: Disabled
    NIC 8: PCI device 0a:00.0, MAC address 00:13:00:00:00:00
    NIC 9: PCI device 00:01.3, MAC address 07:00:00:00:00:0C
    NIC 10: PCI device 06:00.0, MAC address 00:00:00:00:0D:00

Handle 0x0025, DMI type 221, 54 bytes
HP BIOS iSCSI NIC PCI and MAC Information
    NIC 1: PCI device 01:00.7, MAC address 00:07:00:47:50:00
    NIC 2: PCI device 00:00.2, MAC address 00:07:01:57:00:03
    NIC 3: PCI device 07:00.0, MAC address 00:47:50:00:04:05
    NIC 4: Not Installed
    NIC 5: Disabled
    NIC 6: PCI device 0b:00.0, MAC address 00:08:00:FF:FF:FF

Handle 0x0026, DMI type 221, 12 bytes
HP BIOS iSCSI NIC PCI and MAC Information
    NIC 1: PCI device 01:00.1, MAC address 00:04:00:00:00:00

Handle 0x0027, DMI type 7, 27 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Parity
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0028, DMI type 7, 27 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 1024 kB
    Maximum Size: 1024 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x0029, DMI type 7, 27 bytes
Cache Information
    Socket Designation: L3 Cache
    Configuration: Enabled, Not Socketed, Level 3
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 8192 kB
    Maximum Size: 8192 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Multi-bit ECC
    System Type: Unified
    Associativity: 16-way Set-associative

Handle 0x002A, DMI type 4, 48 bytes
Processor Information
    Socket Designation: U3E1
    Type: Central Processor
    Family: Core i7
    Manufacturer: Intel(R) Corporation
    ID: EB 06 08 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 142, Stepping 11
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Multi-threading)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz
    Voltage: 0.8 V
    External Clock: 100 MHz
    Max Speed: 8300 MHz
    Current Speed: 2574 MHz
    Status: Populated, Enabled
    Upgrade: Socket BGA1528
    L1 Cache Handle: 0x0027
    L2 Cache Handle: 0x0028
    L3 Cache Handle: 0x0029
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.
    Core Count: 4
    Core Enabled: 4
    Thread Count: 8
    Characteristics:
        64-bit capable
        Multi-Core
        Hardware Thread
        Execute Protection
        Enhanced Virtualization
        Power/Performance Control

Handle 0x002B, DMI type 20, 35 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 8 GB
    Physical Device Handle: 0x001E
    Memory Array Mapped Address Handle: 0x0020
    Partition Row Position: 1

Handle 0x002C, DMI type 20, 35 bytes
Memory Device Mapped Address
    Starting Address: 0x00200000000
    Ending Address: 0x003FFFFFFFF
    Range Size: 8 GB
    Physical Device Handle: 0x001F
    Memory Array Mapped Address Handle: 0x0020
    Partition Row Position: 1

Handle 0x002D, DMI type 131, 64 bytes
OEM-specific Type
    Header and Data:
        83 40 2D 00 31 00 00 00 00 00 00 00 00 00 00 00
        F8 00 84 9D 00 00 00 00 01 00 00 00 00 00 0C 00
        15 05 14 00 00 00 00 00 FE 00 FF FF 00 00 00 00
        00 00 00 00 22 00 00 00 76 50 72 6F 00 00 00 00

Handle 0x002E, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Long
    Installable Languages: 5
        en|US|iso8859-1
        fr|FR|iso8859-1
        es|ES|iso8859-1
        zh|TW|unicode
        zh|CN|unicode
    Currently Installed Language: en|US|iso8859-1

Handle 0x002F, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Intel Dual Band Wireless-AC 9560 802.11 AC 2x2 WiFi + BT 5 Combo Adapter
    Type: Other
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:00:00.0

Handle 0x0030, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Realtek PCIE CardReader
    Type: Other
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:01:00.0

Handle 0x0031, DMI type 221, 89 bytes
HP BIOS iSCSI NIC PCI and MAC Information
    NIC 1: PCI device 01:01.4, MAC address 00:FF:FF:FF:FF:FF
    NIC 2: PCI device 00:00.2, MAC address FF:FF:FF:FF:FF:03
    NIC 3: PCI device ff:00.4, MAC address FF:FF:FF:FF:05:06
    NIC 4: Not Installed
    NIC 5: Not Installed
    NIC 6: Disabled
    NIC 7: Not Installed
    NIC 8: PCI device 0c:00.0, MAC address 00:00:09:00:01:20
    NIC 9: PCI device 0e:01.5, MAC address 01:04:03:00:00:0F
    NIC 10: Disabled

Handle 0x0032, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Ctrl0Port1
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Primary HDD Bay
    External Connector Type: SAS/SATA Plug Receptacle
    Port Type: SATA

Handle 0x0033, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Ctrl0Port4
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Secondary HDD Bay
    External Connector Type: SAS/SATA Plug Receptacle
    Port Type: SATA

Handle 0x0034, DMI type 27, 15 bytes
Cooling Device
    Type: Fan
    Status: OK
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating
    Description: Cooling Dev 1

Handle 0x0035, DMI type 136, 6 bytes
OEM-specific Type
    Header and Data:
        88 06 35 00 00 00

Handle 0x0036, DMI type 14, 23 bytes
Group Associations
    Name: Firmware Version Info
    Items: 6
        0x0022 (OEM-specific)
        0x0023 (OEM-specific)
        0x0024 (OEM-specific)
        0x0025 (OEM-specific)
        0x0026 (OEM-specific)
        0x0031 (OEM-specific)

Handle 0x0037, DMI type 14, 8 bytes
Group Associations
    Name: $MEI
    Items: 1
        0x002B (OEM-specific)

Handle 0x0038, DMI type 219, 106 bytes
HP ProLiant Information
    Power Features: 0x45010401
    Omega Features: 0x06a00002
    Misc. Features: 0x00000000
        iCRU: No
        UEFI: No

Handle 0x0039, DMI type 127, 4 bytes
End Of Table


By the way, I went to AMI's website and all of the update firmware options are for Windows.

Please remember i am a newbie to linux and just trying to read up as much as possible. 

Thanks in advance for your continued support.

Kevin

---

