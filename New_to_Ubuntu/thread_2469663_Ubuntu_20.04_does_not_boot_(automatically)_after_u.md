---
title: "Ubuntu 20.04 does not boot (automatically) after update"
date: 2021-12-06
forum: New to Ubuntu
---

### Post by maketopsite on 2021-12-06
Problem has occurred after update on August 2021. There is logo Acer on the screen after reboot or power on, laptop is halted. Manually raising boot menu is needed to boot Ubuntu. Ubuntu booted automatically before that update. 

fsck did not find any problem. Reinstalling grub did not help.

Laptop Acer, approx. 5 years old, UEFI. 

Is it please possible to make Ubuntu boot automatically ?

---

### Post by ajgreeny on 2021-12-06
Following the instructions in Boot-Repair in my signature below may help us with a lot more detailed info than we have from your description of the problem,  so please run that and use pastebin as recommended to show us the output of the Boot-info script.

---

### Post by maketopsite on 2021-12-06
> **ajgreeny said:**
> Following the instructions in Boot-Repair in my signature below may help us with a lot more detailed info than we have from your description of the problem,  so please run that and use pastebin as recommended to show us the output of the Boot-info script.

thank you.

```

boot-repair-4ppa130                                              [20211206_1133]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 
    968753152 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt10)/boot/grub. It also embeds following 
    components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/fedora/fwupia32.efi /efi/fedora/fwupx64.efi 
                       /efi/fedora/grubx64.efi /efi/fedora/mmx64.efi 
                       /efi/fedora/shim.efi /efi/fedora/shimx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/fedora/grub.cfg 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub2/grub.cfg

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Fedora 34 (Workstation Edition)
    Boot files:        /etc/fstab /etc/default/grub

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda11: _________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


================================ 2 OS detected =================================

OS#1:   The OS now in use - Ubuntu 20.04.3 LTS CurrentSession on sda10
OS#2:   Fedora 34 (Workstation Edition) on sda8

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.4.0-91-generic root=UUID=3xxxxxxxxxxxxxxxx ro splash=verbose


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled.

efibootmgr -v
BootCurrent: 0003
Timeout: 5 seconds
BootOrder: 0000,0003,0005,0002,0001
Boot0000* Windows Boot Manager    HD(1,GPT,bxxxxxxxxxxxxxxxx,0x800,0xf3800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0001* HDD:     HD(1,GPT,bxxxxxxxxxxxxxxxx,0x800,0xf3800)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0002* Fedora    HD(1,GPT,bxxxxxxxxxxxxxxxx,0x800,0xf3800)/File(\EFI\fedora\shim.efi)
Boot0003* ubuntu    HD(1,GPT,bxxxxxxxxxxxxxxxx,0x800,0xf3800)/File(\EFI\ubuntu\shimx64.efi)
Boot0005* Fedora    HD(1,GPT,bxxxxxxxxxxxxxxxx,0x800,0xf3800)/File(\EFI\fedora\shimx64.efi)
Boot0008* JetFlashTranscend 16GB      BBS(Network,,0x500).......................................................................

7xxxxxxxxxxxxxxxx   sda2/Boot/bootx64.efi
7xxxxxxxxxxxxxxxx   sda2/ubuntu/shimx64.efi
7xxxxxxxxxxxxxxxx   sda2/Microsoft/Boot/bootmgfw.efi
7xxxxxxxxxxxxxxxx   sda2/Microsoft/Boot/bootx64.efi
7xxxxxxxxxxxxxxxx   sda5/Boot/bootx64.efi
7xxxxxxxxxxxxxxxx   sda5/ubuntu/shimx64.efi
7xxxxxxxxxxxxxxxx   sda5/Microsoft/Boot/bootmgfw.efi
7xxxxxxxxxxxxxxxx   sda5/Microsoft/Boot/bootx64.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    hasBIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda10    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sda2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda5    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda6    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda8    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub2-install,    no-grubenv,    grub2-mkconfig -o /boot/grub,    not-far
sda9    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda12    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

sda10    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda8    : isnotESP,    fstab-has-bad-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda9    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda12    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda10    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda2    : is-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda5    : is-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda6    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda8    : not-sepboot,    no-boot,    fstab-has-goodBOOT,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda9    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda12    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: xxxxxxxxxxxxxxxxxxxxxxx
          Start       End   Sectors   Size Type
sda1       2048    999423    997376   487M EFI System
sda2     999424   2023423   1024000   500M Microsoft basic data
sda3  968761344 976771071   8009728   3.8G Linux swap
sda4    2023424   9920511   7897088   3.8G Linux swap
sda5    9920512  10944511   1024000   500M Microsoft basic data
sda6  442927104 545419263 102492160  48.9G Linux filesystem
sda7   10944512  18841599   7897088   3.8G Linux swap
sda8   18841600 154507263 135665664  64.7G Microsoft basic data
sda9  154507264 185980927  31473664    15G Microsoft basic data
sda10 545419264 729145343 183726080  87.6G Linux filesystem
sda11 968753152 968761343      8192     4M BIOS boot
sda12 756015104 968753151 212738048 101.5G Linux filesystem
Partition table entries are not in disk order.
Disk zram0: 938.1 MiB, 983572480 bytes, 240130 sectors
Disk zram1: 938.1 MiB, 983572480 bytes, 240130 sectors

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:4096:gpt:ATA Hitachi xxxxx;
1:1049kB:512MB:511MB:fat32::boot, esp;
2:512MB:1036MB:524MB:ext4::msftdata;
4:1036MB:5079MB:4043MB:linux-swap(v1)::swap;
5:5079MB:5604MB:524MB:ext4::msftdata;
7:5604MB:9647MB:4043MB:linux-swap(v1)::swap;
8:9647MB:79.1GB:69.5GB:ext4::msftdata;
9:79.1GB:95.2GB:16.1GB:ext4:formerfedora:msftdata;
6:227GB:279GB:52.5GB:ext4:fedorahome:;
10:279GB:373GB:94.1GB:ext4:ubuntu:;
12:387GB:496GB:109GB:ext4::;
11:496GB:496GB:4194kB:::bios_grub;
3:496GB:500GB:4101MB:linux-swap(v1)::swap;
zram1:984MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:984MB:984MB:linux-swap(v1)::;
zram0:984MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:984MB:984MB:linux-swap(v1)::;

blkid (filtered): ______________________________________________________________

NAME    FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                              
sda1  vfat     AA22-A94E                            bxxxxxxxxxxxxxxxx       System partition*l EFI
sda2  ext4     8xxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxx       
sda3  swap     5xxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxx       
sda4  swap     dxxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxx       
sda5  ext4     4xxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxx       
sda6  ext4     cxxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxx       fedorahome
sda7  swap     3xxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxx       
sda8  ext4     fxxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxx       
sda9  ext4     1xxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxx       fedora
sda10 ext4     3xxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxx       ubuntu
sda11                                               cxxxxxxxxxxxxxxxx       
sda12 ext4     0xxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxx       
zram0                                                                                            
zram1                                                                                            




```

---

### Post by maketopsite on 2021-12-06
```
df (filtered): _________________________________________________________________

        Avail Use% Mounted on
sda10   30.7G  59% /
sda12     14G  81% /mnt/boot-sav/sda12
sda2   369.9M  16% /mnt/boot-sav/sda2
sda5   249.1M  42% /mnt/boot-sav/sda5
sda6    14.6G  64% /mnt/boot-sav/sda6
sda8    36.8G  38% /mnt/boot-sav/sda8
sda9    13.9G   0% /mnt/boot-sav/sda9

Mount options: __________________________________________________________________

sda10  rw,relatime,errors=remount-ro,stripe=32742
sda12  rw,relatime,stripe=32747
sda2   rw,relatime,stripe=4
sda5   rw,relatime,stripe=4
sda6   rw,relatime
sda8   rw,relatime
sda9   rw,relatime

===================== sda1/efi/fedora/grub.cfg (filtered) ======================

search --no-floppy --fs-uuid --set=dev 4xxxxxxxxxxxxxxxx
set prefix=($dev)/grub2
export $prefix
configfile $prefix/grub.cfg

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 3xxxxxxxxxxxxxxxx root hd0,gpt10
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   0.786036491 = 0.844000256    vmlinuz-0-rescue-6d9631eba0734ea2afe07d7800c9eebc  1
   0.493608475 = 0.530008064    vmlinuz-3.11.10-301.fc20.x86_64                2
   0.485472679 = 0.521272320    initrd-plymouth.img                            1
   0.780732155 = 0.838304768    initramfs-0-rescue-6d9631eba0734ea2afe07d7800c9eebc.img  3
   0.796751022 = 0.855504896    initramfs-3.11.10-301.fc20.x86_64.img          1

================== sda2: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
   0.734380722 = 0.788535296    extlinux/cat.c32                               1
   0.734400749 = 0.788556800    extlinux/chain.c32                             1
   0.734401703 = 0.788557824    extlinux/cmd.c32                               1
   0.734406471 = 0.788562944    extlinux/config.c32                            1
   0.734412193 = 0.788569088    extlinux/cpuid.c32                             1
   0.734436035 = 0.788594688    extlinux/cpuidtest.c32                         1
   0.734417915 = 0.788575232    extlinux/disk.c32                              1
   0.734471321 = 0.788632576    extlinux/dmitest.c32                           1
   0.734498978 = 0.788662272    extlinux/elf.c32                               1
   0.734526634 = 0.788691968    extlinux/ethersel.c32                          1
   0.734547615 = 0.788714496    extlinux/gfxboot.c32                           1
   0.734420776 = 0.788578304    extlinux/gpxecmd.c32                           1
   0.734867096 = 0.789057536    extlinux/hdt.c32                               1
   0.734871864 = 0.789062656    extlinux/host.c32                              1
   0.734892845 = 0.789085184    extlinux/ifcpu.c32                             1
   0.734895706 = 0.789088256    extlinux/ifcpu64.c32                           1
   0.734898567 = 0.789091328    extlinux/ifplop.c32                            1
   0.734904289 = 0.789097472    extlinux/kbdmap.c32                            1
   0.734920502 = 0.789114880    extlinux/linux.c32                             1
   0.734930038 = 0.789125120    extlinux/ls.c32                                1
   0.735163689 = 0.789376000    extlinux/lua.c32                               1
   0.735196114 = 0.789410816    extlinux/mboot.c32                             1
   0.735232353 = 0.789449728    extlinux/meminfo.c32                           1
   0.735284805 = 0.789506048    extlinux/menu.c32                              1
   0.735321045 = 0.789544960    extlinux/pcitest.c32                           1
   0.735333443 = 0.789558272    extlinux/pmload.c32                            1
   0.735286713 = 0.789508096    extlinux/pwd.c32                               1
   0.734930992 = 0.789126144    extlinux/reboot.c32                            1
   0.735353470 = 0.789579776    extlinux/rosh.c32                              1
   0.735289574 = 0.789511168    extlinux/sanboot.c32                           1
   0.735378265 = 0.789606400    extlinux/sdi.c32                               1
   0.735419273 = 0.789650432    extlinux/sysdump.c32                           1
   0.735424995 = 0.789656576    extlinux/vesainfo.c32                          1
   0.735570908 = 0.789813248    extlinux/vesamenu.c32                          1
   0.735576630 = 0.789819392    extlinux/vpdtest.c32                           1
   0.735579491 = 0.789822464    extlinux/whichsys.c32                          1
   0.735589027 = 0.789832704    extlinux/zzjson.c32                            1

=============== sda2: Version of COM32(R) files used by Syslinux ===============

 extlinux/cat.c32                   :  COM32R module (v4.xx)
 extlinux/chain.c32                 :  COM32R module (v4.xx)
 extlinux/cmd.c32                   :  COM32R module (v4.xx)
 extlinux/config.c32                :  COM32R module (v4.xx)
 extlinux/cpuid.c32                 :  COM32R module (v4.xx)
 extlinux/cpuidtest.c32             :  COM32R module (v4.xx)
 extlinux/disk.c32                  :  COM32R module (v4.xx)
 extlinux/dmitest.c32               :  COM32R module (v4.xx)
 extlinux/elf.c32                   :  COM32R module (v4.xx)
 extlinux/ethersel.c32              :  COM32R module (v4.xx)
 extlinux/gfxboot.c32               :  COM32R module (v4.xx)
 extlinux/gpxecmd.c32               :  COM32R module (v4.xx)
 extlinux/hdt.c32                   :  COM32R module (v4.xx)
 extlinux/host.c32                  :  COM32R module (v4.xx)
 extlinux/ifcpu.c32                 :  COM32R module (v4.xx)
 extlinux/ifcpu64.c32               :  COM32R module (v4.xx)
 extlinux/ifplop.c32                :  COM32R module (v4.xx)
 extlinux/kbdmap.c32                :  COM32R module (v4.xx)
 extlinux/linux.c32                 :  COM32R module (v4.xx)
 extlinux/ls.c32                    :  COM32R module (v4.xx)
 extlinux/lua.c32                   :  COM32R module (v4.xx)
 extlinux/mboot.c32                 :  COM32R module (v4.xx)
 extlinux/meminfo.c32               :  COM32R module (v4.xx)
 extlinux/menu.c32                  :  COM32R module (v4.xx)
 extlinux/pcitest.c32               :  COM32R module (v4.xx)
 extlinux/pmload.c32                :  COM32R module (v4.xx)
 extlinux/pwd.c32                   :  COM32R module (v4.xx)
 extlinux/reboot.c32                :  COM32R module (v4.xx)
 extlinux/rosh.c32                  :  COM32R module (v4.xx)
 extlinux/sanboot.c32               :  COM32R module (v4.xx)
 extlinux/sdi.c32                   :  COM32R module (v4.xx)
 extlinux/sysdump.c32               :  COM32R module (v4.xx)
 extlinux/vesainfo.c32              :  COM32R module (v4.xx)
 extlinux/vesamenu.c32              :  COM32R module (v4.xx)
 extlinux/vpdtest.c32               :  COM32R module (v4.xx)
 extlinux/whichsys.c32              :  COM32R module (v4.xx)
 extlinux/zzjson.c32                :  COM32R module (v4.xx)

======================== sda5/grub2/grub.cfg (filtered) ========================

### END /etc/grub.d/30_os-prober ###
System setup   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   5.118659019 = 5.496118272    grub2/grub.cfg                                 1
   5.039942741 = 5.411597312    vmlinuz-0-rescue-075cbeef5cec4492b8ed14f449626f40  1
   4.810999870 = 5.165771776    vmlinuz-5.14.16-201.fc34.x86_64                3
   5.057085991 = 5.430004736    vmlinuz-5.14.9-200.fc34.x86_64                 3
   5.104086876 = 5.480471552    vmlinuz-5.15.4-101.fc34.x86_64                 1
   5.063024521 = 5.436381184    initrd-plymouth.img                            1
   5.034624100 = 5.405886464    initramfs-0-rescue-075cbeef5cec4492b8ed14f449626f40.img  3
   4.849318504 = 5.206916096    initramfs-5.14.16-201.fc34.x86_64.img          1
   5.091341972 = 5.466786816    initramfs-5.14.9-200.fc34.x86_64.img           3
   5.156210899 = 5.536439296    initramfs-5.15.4-101.fc34.x86_64.img           2

================== sda5: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
   5.118581772 = 5.496035328    extlinux/cat.c32                               1
   4.988305092 = 5.356151808    extlinux/chain.c32                             1
   4.988307953 = 5.356154880    extlinux/cmd.c32                               1
   4.988311768 = 5.356158976    extlinux/cmenu.c32                             1
   4.988328934 = 5.356177408    extlinux/config.c32                            1
   4.988797188 = 5.356680192    extlinux/cptime.c32                            1
   4.988339424 = 5.356188672    extlinux/cpu.c32                               1
   4.988342285 = 5.356191744    extlinux/cpuid.c32                             1
   4.988783836 = 5.356665856    extlinux/cpuidtest.c32                         1
   4.988790512 = 5.356673024    extlinux/debug.c32                             1
   4.988788605 = 5.356670976    extlinux/dhcp.c32                              1
   4.988814354 = 5.356698624    extlinux/dir.c32                               1
   4.988809586 = 5.356693504    extlinux/disk.c32                              1
   4.989052773 = 5.356954624    extlinux/dmi.c32                               1
   4.988324165 = 5.356172288    extlinux/dmitest.c32                           1
   4.989135742 = 5.357043712    extlinux/elf.c32                               1
   4.988327026 = 5.356175360    extlinux/ethersel.c32                          1
   4.988352776 = 5.356203008    extlinux/gfxboot.c32                           1
   4.989055634 = 5.356957696    extlinux/gpxecmd.c32                           1
   4.988969803 = 5.356865536    extlinux/hdt.c32                               1
   4.988357544 = 5.356208128    extlinux/hexdump.c32                           1
   4.988971710 = 5.356867584    extlinux/host.c32                              1
   4.988774300 = 5.356655616    extlinux/ifcpu.c32                             1
   4.988777161 = 5.356658688    extlinux/ifcpu64.c32                           1
   4.988804817 = 5.356688384    extlinux/ifmemdsk.c32                          1
   4.988807678 = 5.356691456    extlinux/ifplop.c32                            1
   4.989057541 = 5.356959744    extlinux/kbdmap.c32                            1
   4.988976479 = 5.356872704    extlinux/kontron_wdt.c32                       1
   4.989557266 = 5.357496320    extlinux/ldlinux.c32                           1
   4.988981247 = 5.356877824    extlinux/lfs.c32                               1
   5.041533470 = 5.413305344    extlinux/libcom32.c32                          1
   4.989199638 = 5.357112320    extlinux/libgpl.c32                            1
   4.989653587 = 5.357599744    extlinux/liblua.c32                            1
   4.989005089 = 5.356903424    extlinux/libmenu.c32                           1
   4.989027023 = 5.356926976    extlinux/libutil.c32                           1
   4.989031792 = 5.356932096    extlinux/linux.c32                             1
   4.989034653 = 5.356935168    extlinux/ls.c32                                1
   4.989041328 = 5.356942336    extlinux/lua.c32                               1
   4.989210129 = 5.357123584    extlinux/mboot.c32                             1
   4.989044189 = 5.356945408    extlinux/meminfo.c32                           1
   4.989311218 = 5.357232128    extlinux/menu.c32                              1
   4.989238739 = 5.357154304    extlinux/pci.c32                               1
   4.989284515 = 5.357203456    extlinux/pcitest.c32                           1
   4.989314079 = 5.357235200    extlinux/pmload.c32                            1
   4.989122391 = 5.357029376    extlinux/poweroff.c32                          1
   4.989318848 = 5.357240320    extlinux/prdhcp.c32                            1
   4.989240646 = 5.357156352    extlinux/pwd.c32                               1
   4.989331245 = 5.357253632    extlinux/pxechn.c32                            1
   4.989334106 = 5.357256704    extlinux/reboot.c32                            1
   4.989347458 = 5.357271040    extlinux/rosh.c32                              1
   4.989358902 = 5.357283328    extlinux/sanboot.c32                           1
   4.989444733 = 5.357375488    extlinux/sdi.c32                               1
   4.989667892 = 5.357615104    extlinux/sysdump.c32                           1
   4.989676476 = 5.357624320    extlinux/syslinux.c32                          1
   4.989679337 = 5.357627392    extlinux/vesa.c32                              1
   4.989682198 = 5.357630464    extlinux/vesainfo.c32                          1
   4.989707947 = 5.357658112    extlinux/vesamenu.c32                          1
   4.990737915 = 5.358764032    extlinux/vpdtest.c32                           1
   4.989710808 = 5.357661184    extlinux/whichsys.c32                          1
   4.989715576 = 5.357666304    extlinux/zzjson.c32                            1

=============== sda5: Version of COM32(R) files used by Syslinux ===============

 extlinux/cat.c32                   :  not a COM32/COM32R module
 extlinux/chain.c32                 :  not a COM32/COM32R module
 extlinux/cmd.c32                   :  not a COM32/COM32R module
 extlinux/cmenu.c32                 :  not a COM32/COM32R module
 extlinux/config.c32                :  not a COM32/COM32R module
 extlinux/cptime.c32                :  not a COM32/COM32R module
 extlinux/cpu.c32                   :  not a COM32/COM32R module
 extlinux/cpuid.c32                 :  not a COM32/COM32R module
 extlinux/cpuidtest.c32             :  not a COM32/COM32R module
 extlinux/debug.c32                 :  not a COM32/COM32R module
 extlinux/dhcp.c32                  :  not a COM32/COM32R module
 extlinux/dir.c32                   :  not a COM32/COM32R module
 extlinux/disk.c32                  :  not a COM32/COM32R module
 extlinux/dmi.c32                   :  not a COM32/COM32R module
 extlinux/dmitest.c32               :  not a COM32/COM32R module
 extlinux/elf.c32                   :  not a COM32/COM32R module
 extlinux/ethersel.c32              :  not a COM32/COM32R module
 extlinux/gfxboot.c32               :  not a COM32/COM32R module
 extlinux/gpxecmd.c32               :  not a COM32/COM32R module
 extlinux/hdt.c32                   :  not a COM32/COM32R module
 extlinux/hexdump.c32               :  not a COM32/COM32R module
 extlinux/host.c32                  :  not a COM32/COM32R module
 extlinux/ifcpu.c32                 :  not a COM32/COM32R module
 extlinux/ifcpu64.c32               :  not a COM32/COM32R module
 extlinux/ifmemdsk.c32              :  not a COM32/COM32R module
 extlinux/ifplop.c32                :  not a COM32/COM32R module
 extlinux/kbdmap.c32                :  not a COM32/COM32R module
 extlinux/kontron_wdt.c32           :  not a COM32/COM32R module
 extlinux/ldlinux.c32               :  not a COM32/COM32R module
 extlinux/lfs.c32                   :  not a COM32/COM32R module
 extlinux/libcom32.c32              :  not a COM32/COM32R module
 extlinux/libgpl.c32                :  not a COM32/COM32R module
 extlinux/liblua.c32                :  not a COM32/COM32R module
 extlinux/libmenu.c32               :  not a COM32/COM32R module
 extlinux/libutil.c32               :  not a COM32/COM32R module
 extlinux/linux.c32                 :  not a COM32/COM32R module
 extlinux/ls.c32                    :  not a COM32/COM32R module
 extlinux/lua.c32                   :  not a COM32/COM32R module
 extlinux/mboot.c32                 :  not a COM32/COM32R module
 extlinux/meminfo.c32               :  not a COM32/COM32R module
 extlinux/menu.c32                  :  not a COM32/COM32R module
 extlinux/pci.c32                   :  not a COM32/COM32R module
 extlinux/pcitest.c32               :  not a COM32/COM32R module
 extlinux/pmload.c32                :  not a COM32/COM32R module
 extlinux/poweroff.c32              :  not a COM32/COM32R module
 extlinux/prdhcp.c32                :  not a COM32/COM32R module
 extlinux/pwd.c32                   :  not a COM32/COM32R module
 extlinux/pxechn.c32                :  not a COM32/COM32R module
 extlinux/reboot.c32                :  not a COM32/COM32R module
 extlinux/rosh.c32                  :  not a COM32/COM32R module
 extlinux/sanboot.c32               :  not a COM32/COM32R module
 extlinux/sdi.c32                   :  not a COM32/COM32R module
 extlinux/sysdump.c32               :  not a COM32/COM32R module
 extlinux/syslinux.c32              :  not a COM32/COM32R module
 extlinux/vesa.c32                  :  not a COM32/COM32R module
 extlinux/vesainfo.c32              :  not a COM32/COM32R module
 extlinux/vesamenu.c32              :  not a COM32/COM32R module
 extlinux/vpdtest.c32               :  not a COM32/COM32R module
 extlinux/whichsys.c32              :  not a COM32/COM32R module
 extlinux/zzjson.c32                :  not a COM32/COM32R module



```

---

### Post by maketopsite on 2021-12-06
```
========================== sda8/etc/fstab (filtered) ===========================

UUID=fxxxxxxxxxxxxxxxx /                       ext4    defaults        1 1
UUID=4xxxxxxxxxxxxxxxx /boot                   ext4    defaults        1 2
UUID=AA22-A94E          /boot/efi               vfat    umask=0077,shortname=winnt 0 0
UUID=cxxxxxxxxxxxxxxxx /home                   ext4    defaults        1 2
UUID=3xxxxxxxxxxxxxxxx swap                    swap    defaults        0 0

======================= sda8/etc/default/grub (filtered) =======================

GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
GRUB_DEFAULT=0
GRUB_DISABLE_SUBMENU=true
GRUB_TERMINAL_OUTPUT="console"
GRUB_CMDLINE_LINUX="vconsole.font=latarcyrheb-sun16 $([ -x /usr/sbin/rhcrashkernel-param ] && /usr/sbin/rhcrashkernel-param || :) rhgb splash=verbose"
GRUB_ENABLE_BLSCFG=true

===================== sda8: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root   236 Nov  5 21:56 01_users
-rwxr-xr-x 1 root root   835 Nov  5 21:56 08_fallback_counting
-rwxr-xr-x 1 root root 18669 Nov  5 21:56 10_linux
-rwxr-xr-x 1 root root   833 Nov  5 21:56 10_reset_boot_success
-rwxr-xr-x 1 root root   892 Nov  5 21:56 12_menu_auto_hide
-rwxr-xr-x 1 root root   410 Nov  5 21:56 14_menu_show_once
-rwxr-xr-x 1 root root 13613 Nov  5 21:56 20_linux_xen
-rwxr-xr-x 1 root root  2562 Nov  5 21:56 20_ppc_terminfo
-rwxr-xr-x 1 root root 10869 Nov  5 21:56 30_os-prober
-rwxr-xr-x 1 root root  1122 Nov  5 21:56 30_uefi-firmware
-rwxr-xr-x 1 root root   710 Nov  1 13:39 35_fwupd
-rwxr-xr-x 1 root root   218 Nov  5 21:56 40_custom
-rwxr-xr-x 1 root root   219 Nov  5 21:56 41_custom

=========================== sda8/etc/grub.d/01_users ===========================

#!/usr/bin/sh -e
cat << EOF
if [ -f \${prefix}/user.cfg ]; then
  source \${prefix}/user.cfg
  if [ -n "\${GRUB2_PASSWORD}" ]; then
    set superusers="root"
    export superusers
    password_pbkdf2 root \${GRUB2_PASSWORD}
  fi
fi
EOF

===================== sda8/etc/grub.d/08_fallback_counting =====================

#!/usr/bin/sh -e
# Fallback Countdown
#
# This snippet depends on 10_reset_boot_success and needs to be kept in sync.
#
# The boot_counter env var can be used to count down boot attempts after an
# OSTree upgrade and choose the rollback deployment when 0 is reached.
# Both boot_counter=X and boot_success=1 need to be set from userspace.
cat << EOF
insmod increment
# Check if boot_counter exists and boot_success=0 to activate this behaviour.
if [ -n "\${boot_counter}" -a "\${boot_success}" = "0" ]; then
  # if countdown has ended, choose to boot rollback deployment,
  # i.e. default=1 on OSTree-based systems.
  if  [ "\${boot_counter}" = "0" -o "\${boot_counter}" = "-1" ]; then
    set default=1
    set boot_counter=-1
  # otherwise decrement boot_counter
  else
    decrement boot_counter
  fi
  save_env boot_counter
fi
EOF

==================== sda8/etc/grub.d/10_reset_boot_success =====================

#!/usr/bin/sh -e
# Reset Boot Success
#
# The 08_fallback_counting and 12_menu_auto_hide snippets rely on this one
# and need to be kept in sync.
#
# The boot_success var needs to be set to 1 from userspace to mark a boot successful.
cat << EOF
# Hiding the menu is ok if last boot was ok or if this is a first boot attempt to boot the entry
if [ "\${boot_success}" = "1" -o "\${boot_indeterminate}" = "1" ]; then
  set menu_hide_ok=1
else
  set menu_hide_ok=0
fi
# Reset boot_indeterminate after a successful boot
if [ "\${boot_success}" = "1" ] ; then
  set boot_indeterminate=0
# Avoid boot_indeterminate causing the menu to be hidden more than once
elif [ "\${boot_indeterminate}" = "1" ]; then
  set boot_indeterminate=2
fi
# Reset boot_success for current boot
set boot_success=0
save_env boot_success boot_indeterminate
EOF

====================== sda8/etc/grub.d/12_menu_auto_hide =======================

#!/usr/bin/sh
# Menu Auto Hide
#
# This snippet depends on 10_reset_boot_success and needs to be kept in sync.
#
# Disable / skip generating menu-auto-hide config parts on serial terminals
for x in ${GRUB_TERMINAL_INPUT} ${GRUB_TERMINAL_OUTPUT}; do
  case "$x" in
    serial*)
      exit 0
      ;;
  esac
done
cat << EOF
if [ x\$feature_timeout_style = xy ] ; then
  if [ "\${menu_show_once}" ]; then
    unset menu_show_once
    save_env menu_show_once
    set timeout_style=menu
    set timeout=60
  elif [ "\${menu_auto_hide}" -a "\${menu_hide_ok}" = "1" ]; then
    set orig_timeout_style=\${timeout_style}
    set orig_timeout=\${timeout}
    if [ "\${fastboot}" = "1" ]; then
      # timeout_style=menu + timeout=0 avoids the countdown code keypress check
      set timeout_style=menu
      set timeout=0
    else
      set timeout_style=hidden
      set timeout=1
    fi
  fi
fi
EOF

====================== sda8/etc/grub.d/14_menu_show_once =======================

#!/usr/bin/sh
# Force the menu to be shown once, with a timeout of ${menu_show_once_timeout}
# if requested by ${menu_show_once_timeout} being set in the env.
cat << EOF
if [ x\$feature_timeout_style = xy ]; then
  if [ "\${menu_show_once_timeout}" ]; then
    set timeout_style=menu
    set timeout="\${menu_show_once_timeout}"
    unset menu_show_once_timeout
    save_env menu_show_once_timeout
  fi
fi
EOF

======================= sda8/etc/grub.d/20_ppc_terminfo ========================

#!/usr/bin/sh
set -e
# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.
prefix=/usr
exec_prefix=/usr
bindir=/usr/bin
libdir=/usr/lib
. "/usr/share/grub/grub-mkconfig_lib"
export TEXTDOMAIN=grub
export TEXTDOMAINDIR=/usr/share/locale
X=80
Y=24
TERMINAL=ofconsole
argument () {
  opt=$1
  shift
  if test $# -eq 0; then
      echo "$0: option requires an argument -- '$opt'" 1>&2
      exit 1
  fi
  echo $1
}
check_terminfo () {
  while test $# -gt 0
  do
    option=$1
    shift
    case "$option" in
    terminfo | TERMINFO)
        ;;
    -g)
        NEWXY=`argument $option "$@"`
        NEWX=`echo $NEWXY | cut -d x -f 1`
        NEWY=`echo $NEWXY | cut -d x -f 2`
        if [ ${NEWX} -ge 80 ] ; then
          X=${NEWX}
        else
          echo "Warning: ${NEWX} is less than the minimum size of 80"
        fi
        if [ ${NEWY} -ge 24 ] ; then
          Y=${NEWY}
        else
          echo "Warning: ${NEWY} is less than the minimum size of 24"
        fi
        shift
        ;;
    *)
#       # accept console or ofconsole
#       if [ "$option" != "console" -a "$option" != "ofconsole" ] ; then
#         echo "Error: GRUB_TERMINFO unknown console: $option"
#         exit 1
#       fi
#       # perfer console
#       TERMINAL=console
        # accept ofconsole
        if [ "$option" != "ofconsole" ] ; then
          echo "Error: GRUB_TERMINFO unknown console: $option"
          exit 1
        fi
        # perfer console
        TERMINAL=ofconsole
        ;;
    esac
  done
}
if ! uname -m | grep -q ppc ; then
  exit 0
fi
if [ "x${GRUB_TERMINFO}" != "x" ] ; then
  F1=`echo ${GRUB_TERMINFO} | cut -d " " -f 1`
  if [ "${F1}" != "terminfo" ] ; then
    echo "Error: GRUB_TERMINFO is set to \"${GRUB_TERMINFO}\" The first word should be terminfo."
    exit 1
  fi
  check_terminfo ${GRUB_TERMINFO}
fi
cat << EOF
  terminfo -g ${X}x${Y} ${TERMINAL}
EOF

=========================== sda8/etc/grub.d/35_fwupd ===========================

#!/usr/bin/bash
# SPDX-License-Identifier: LGPL-2.1+
set -e
[ -d ${pkgdatadir:?} ]
# shellcheck source=/dev/null
. "$pkgdatadir/grub-mkconfig_lib"
if [ -f /var/lib/fwupd/uefi_capsule.conf ] &&
   ls /sys/firmware/efi/efivars/fwupd-*-0abba7dc-e516-4167-bbf5-4d9d1c739416 1>/dev/null 2>&1; then
      source /var/lib/fwupd/uefi_capsule.conf
      if [ "${EFI_PATH}" != "" ] && [ "${ESP}" != "" ]; then
      echo "Adding Linux Firmware Updater entry" >&2
cat << EOF
menuentry 'Linux Firmware Updater' \$menuentry_id_option 'fwupd' {
EOF
      ${grub_probe:?}
      prepare_grub_to_access_device '`${grub_probe} --target=device \${ESP}` | sed -e "s/^/\t/"'
cat << EOF
    chainloader ${EFI_PATH}
}
EOF
      fi
fi

===================== sda10/boot/grub/grub.cfg (filtered) ======================

Ubuntu   3xxxxxxxxxxxxxxxx
Ubuntu, with Linux 5.4.0-91-generic   3xxxxxxxxxxxxxxxx
Ubuntu, with Linux 5.4.0-90-generic   3xxxxxxxxxxxxxxxx
Fedora 34 (Workstation Edition) (on sda8)   fxxxxxxxxxxxxxxxx
Fedora 34 (Workstation Edition) (on sda8)   fxxxxxxxxxxxxxxxx
Fedora 34 (Workstation Edition) (on sda8)   fxxxxxxxxxxxxxxxx
Fedora 34 (Workstation Edition) (on sda8)   fxxxxxxxxxxxxxxxx
Fedora 34 (Workstation Edition) (on sda8)   fxxxxxxxxxxxxxxxx
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda10/etc/fstab (filtered) ==========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda10 during installation
UUID=3xxxxxxxxxxxxxxxx /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
# swap was on /dev/sda3 during installation
UUID=5xxxxxxxxxxxxxxxx none            swap    sw              0       0

====================== sda10/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash=verbose"
GRUB_CMDLINE_LINUX=""

=================== sda10: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 296.847759247 = 318.737854464  boot/grub/grub.cfg                             3
 274.327739716 = 294.557167616  boot/grub/i386-pc/core.img                     1
 333.430896759 = 358.018699264  boot/vmlinuz                                   2
 310.563705444 = 333.465239552  boot/vmlinuz-5.4.0-90-generic                  2
 333.430896759 = 358.018699264  boot/vmlinuz-5.4.0-91-generic                  2
 310.563705444 = 333.465239552  boot/vmlinuz.old                               2
 323.220359802 = 347.055218688  boot/initrd.img                                2
 311.529293060 = 334.502031360  boot/initrd.img-5.4.0-90-generic               6
 323.220359802 = 347.055218688  boot/initrd.img-5.4.0-91-generic               2
 311.529293060 = 334.502031360  boot/initrd.img.old                            6

===================== sda10: ls -l /etc/grub.d/ (filtered) =====================

-rwxr-xr-x 1 root root 18151 Aug 12 11:18 10_linux
-rwxr-xr-x 1 root root 42359 Aug 12 11:18 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Aug 12 11:18 20_linux_xen
-rwxr-xr-x 1 root root 12059 Aug 12 11:18 30_os-prober
-rwxr-xr-x 1 root root  1424 Aug 12 11:18 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Aug 12 11:18 40_custom
-rwxr-xr-x 1 root root   216 Aug 12 11:18 41_custom


Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub2 of
sda10 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s      

Confirmation request before suggested repair: __________________________________

The boot of your PC is in EFI mode, but no ESP partition was detected. You may want to retry after creating a ESP partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Are you sure you want to continue anyway?

Final advice in case of suggested repair: ______________________________________


The boot of your PC is in UEFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.


```

---

### Post by oldfred on 2021-12-06
You took out a lot of useful info.
UUIDs & GUIDs are unique to your partitions. And boot process must be tracked from GUID entry in UEFI to GUID of ESP and  from UUID of grub.cfg in ESP to UUID of partition that is your install.

But your issue seems to be just from normal updates.
Each install you have, will with some updates will reset boot order to make it first in UEFI boot menu.
Most systems will recognize changes with efibootmgr. Some like HP can only be changed from within UEFI settings (not UEFI menu).
Or need BCD setting so some sort of sync with UEFI & BCD in Windows has correct boot order.

Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

---

### Post by tea for one on 2021-12-06
You do not have an EFI System Partition (ESP)

[COLOR="#0000FF"]sda    : is-GPT,    hasBIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes[/COLOR]

Edit; Yet **sda1       2048    999423    997376   487M EFI System**

The boot repair report is submitted in three sections and it is supplying conflicting info?
Unable to refer to line numbers because of the way the report is submitted.

---

### Post by maketopsite on 2021-12-06
> **oldfred said:**
> You took out a lot of useful info.
UUIDs & GUIDs are unique to your partitions. And boot process must be tracked from GUID entry in UEFI to GUID of ESP and  from UUID of grub.cfg in ESP to UUID of partition that is your install.

But your issue seems to be just from normal updates.
Each install you have, will with some updates will reset boot order to make it first in UEFI boot menu.
Most systems will recognize changes with efibootmgr. Some like HP can only be changed from within UEFI settings (not UEFI menu).
Or need BCD setting so some sort of sync with UEFI & BCD in Windows has correct boot order.

Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

Excuse me I can provide UUIDs & GUIDs if necessary.

I've tried efibootmgr -o with some combinations but it did not help.

---

### Post by maketopsite on 2021-12-06
> **tea for one said:**
> You do not have an EFI System Partition (ESP)

[COLOR=#0000FF]sda    : is-GPT,    hasBIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes[/COLOR]

Edit; Yet **sda1       2048    999423    997376   487M EFI System**

The boot repair report is submitted in three sections and it is supplying conflicting info?
Unable to refer to line numbers because of the way the report is submitted.

I've submitted report in 3 posts because it was not possible to submit it in one post. Probably because of length.
I'm sorry I'm not aware of conflicting info.
Can I enable somehow line numbers ?

Shall I create ESP ?

---

### Post by tea for one on 2021-12-06
Boot-repair reports are usually uploaded to pastebin rather than direct to the forum thread.
Pastebin retains the line numbers.
Anyway, let's continue.

The conflicting info is:-

Boot repair states no ESP [COLOR="#0000FF"]sda : is-GPT, hasBIOSboot, _has-noESP_, not-usb, not-mmc, has-os, 2048 sectors * 512 bytes[/COLOR]
Yet you have **sda1 2048 999423 997376 487M EFI System **

sda1 is, to all intents and purposes, an [COLOR="#0000FF"]E[/COLOR]FI [COLOR="#0000FF"]S[/COLOR]ystem [COLOR="#0000FF"]P[/COLOR]artition

I've not seen this sort of conflict before hence I'm hesitant to offer concrete advice.

There are some other items worth mentioning:-

[LIST]
[*]You have older BIOS boot partition sda11
[*]Possible EFI partition is sda1
[*]3 swap partitions sda3, sda4 and sda7
[*]3 Microsoft partitions sda2,sda8 and sda9 (although you do not have Windows installed)
[/LIST]
The partitions look like that they have been established over the years as a variety of systems were added and removed?
I would guess that the systems were probably installed in a mixture of BIOS mode and UEFI mode, hence the presence of EFI files and BIOS boot partition.

As Ubuntu does not boot cleanly (although it still boots), it may be an opportunity to think about backing up, starting from scratch and installing in UEFI mode?
This will allow you to tidy up the partitions, swaps etc. and make the management of your systems a little easier.
By the way, Ubuntu now uses a swapfile rather than a partition.

In any event, your personal data backup (from both Ubuntu and Fedora) would be the highest priority.

---

### Post by yancek on 2021-12-07
>  Problem has occurred after update on August 2021.

And what might that update have been as I see you h ave both Ubuntu and Fedora installed. Which OS did you update?  Is there any particular reason you have waited 4 months to pose your question?
Is it because you can boot Ubuntu but it does not automatically boot?  Are you still able to boot Fedora?  Do you have to manually select Fedora and or Ubuntu from a Grub boot menu or dol you select them from your EFI menu in the BIOS firmware?

You indicate that prior to the update (of Ubuntu??), it (Ubuntu booted automatically, is that correct?  Did you have Fedora installed prior to this update?

Your boot repair output shows at the very top that you have Grub in the MBR of sda and it looks for the boot files for a Legacy/CSM install on sda10 which is your Ubuntu.
You have that Legacy/CSM install of all three OS's, includes Ubuntu EFI files on sda1.  Have you disabled Legacy/CSM boot in the BIOS Firmware?

Are you able to use efibootmgr to set the Ubuntu entry to first boot?  Does this show the Grub menu from Ubuntu with Fedora and windows.
What happens if you boot and don't take any action with regard to booting?  Do any of the 3 systems boot?  Do you need to manually make a selection?  Can you make a selection

Disabling Legacy/CSM boot and setting ubuntu to first boot with efibootmgr should bring up the Ubuntu Grub menu.

---

### Post by maketopsite on 2021-12-08
> **yancek said:**
> And what might that update have been as I see you h ave both Ubuntu and Fedora installed. Which OS did you update?  Is there any particular reason you have waited 4 months to pose your question?
Is it because you can boot Ubuntu but it does not automatically boot?  Are you still able to boot Fedora?  Do you have to manually select Fedora and or Ubuntu from a Grub boot menu or dol you select them from your EFI menu in the BIOS firmware?

You indicate that prior to the update (of Ubuntu??), it (Ubuntu booted automatically, is that correct?  Did you have Fedora installed prior to this update?

Your boot repair output shows at the very top that you have Grub in the MBR of sda and it looks for the boot files for a Legacy/CSM install on sda10 which is your Ubuntu.
You have that Legacy/CSM install of all three OS's, includes Ubuntu EFI files on sda1.  Have you disabled Legacy/CSM boot in the BIOS Firmware?

Are you able to use efibootmgr to set the Ubuntu entry to first boot?  Does this show the Grub menu from Ubuntu with Fedora and windows.
What happens if you boot and don't take any action with regard to booting?  Do any of the 3 systems boot?  Do you need to manually make a selection?  Can you make a selection

Disabling Legacy/CSM boot and setting ubuntu to first boot with efibootmgr should bring up the Ubuntu Grub menu.

Thank you, Ubuntu grub menu is shown so **Ubuntu automatically boot when BIOS is switched from UEFI to Legacy**. Some following answers apply to BIOS in UEFI mode:

I did update Ubuntu. No particular reason.

Yes I can boot Ubuntu but it does not automatically boot. I am able to boot Fedora. I have to manually select Fedora and or Ubuntu from a  boot menu. (it's not grub menu, it's not EFI menu in the BIOS firmware).

Prior to the update of Ubuntu, it (Ubuntu) booted automatically. Fedora was installed prior to this update.

I'm able to use efibootmgr to set the Ubuntu entry to be the first in the boot menu. No grub menu is shown.

There is Acer logo on the screen if I boot and don't take any action with regard to booting. Nothing boots. I need manually raise boot menu and select Ubuntu or Fedora.

---

### Post by oldfred on 2021-12-08
ESP looks correct.
But only because Boot-Repair says it has issues reading it, run this. Make sure you have esp,boot flags (using gparted) on ESP.
sudo fsck.vfat -t -a /dev/sda1
man dosfsck

Acer's have always needed "trust" on UEFI boot entries for other than Windows.
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

Then rerun Boot-Repair when booted in UEFI mode & post just the link to the pastebin site, so we get all your info in one place.
Its difficult going back to each of your posts particularly now we are on page 2. 
If you want help you need to make it easy for us to help you.

You should only have two boot menus. First is UEFI and in UEFI menu it just shows the name not the details as efibootmgr -v does.
Or the grub menu. Depending on which system you boot from UEFI, you will get either Ubuntu's grub or Fedora's grub.
And grub only adds Windows to grub menu for working Windows. That means fast start up in Windows must be off and no chkdsk required. Note that Windows may turn fast start up back on with updates and then grub will stop booting Windows.

---

### Post by maketopsite on 2021-12-11
> **oldfred said:**
> ESP looks correct.
But only because Boot-Repair says it has issues reading it, run this. Make sure you have esp,boot flags (using gparted) on ESP.
sudo fsck.vfat -t -a /dev/sda1
man dosfsck

Acer's have always needed "trust" on UEFI boot entries for other than Windows.
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

Then rerun Boot-Repair when booted in UEFI mode & post just the link to the pastebin site, so we get all your info in one place.
Its difficult going back to each of your posts particularly now we are on page 2. 
If you want help you need to make it easy for us to help you.

You should only have two boot menus. First is UEFI and in UEFI menu it just shows the name not the details as efibootmgr -v does.
Or the grub menu. Depending on which system you boot from UEFI, you will get either Ubuntu's grub or Fedora's grub.
And grub only adds Windows to grub menu for working Windows. That means fast start up in Windows must be off and no chkdsk required. Note that Windows may turn fast start up back on with updates and then grub will stop booting Windows.

Thank you, I appreciate very much help of your and of others but current state is satisfactory and I dont want risk any troubles ("UEFI hell") now. Is please safe to use laptop in current state ?

---

