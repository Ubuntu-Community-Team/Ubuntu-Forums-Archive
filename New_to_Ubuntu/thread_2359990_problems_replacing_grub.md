---
title: "problems replacing grub"
date: 2017-04-30
forum: New to Ubuntu
---

### Post by 3tyson on 2017-04-30
Hey im really new to linux.

I use to run windows 10 on my laptop but it started giving me some problems afther i started dual booting so i decited to whipe windows and just go with ubuntu.
so i created a bootable ubuntu stick sticked it in my computer and started the install everything seemed to go right.

afther a litle while it gives me some warning about the bios stil being in uefi mode and if I go on its supose to make it hard to get into anny bios mode, i figured theres really no way back now so i pressed ignore and went on. 
So far so good it keeps the install going all the way to where its supose to get somewhere in grub and re-write it i think ? And it tells me the grub failed to install this is a fatal error, if i try to pick a different location to install it it just freez if  i continue without it it will freez. 

so i tried using boot repair to repair grub, but it said it didnt have permisions
[IMG]https://ibb.co/gg3ST5[/IMG] [URL="https://ibb.co/gg3ST5"]https://ibb.co/gg3ST5
[/URL]
 went to permisions and than i realized i have no clue what im doing and could proberlty start  doing some seriouse dmg to my system from here on.

so could anny of you maybe like tell me how to set permisions so that i could use boot repair to repair grub ?
that would be really great 

thanks

---

### Post by Bucky Ball on 2017-04-30
Welcome. Are you trying to install the grub to sda, not sda1 or sda*? You want to install it to the disk, not a partition. What method of partitioning are you going for? Use whole disk or manually partitioning using 'Something Else'?

How are you using Boot Repair? Running it from the Boot Repair CD or USB or installing the repo in the live session? Try the latter. See the Boot Repair link in the signature at the bottom of my post (at end of first line).

Once you get BRepair going, launch it and run the 'bootinfo' option, not the recommended repair, and post the link that spits out back here, please.

---

### Post by 3tyson on 2017-05-01
Welcome. thanks
 Are you trying to install the grub to sda, not sda1 or sda*? I think im trying to install it to sda1 because that seems to be what the auto installer did, i just want ubuntu to be my only operating system because right now i have none
[URL="https://ibb.co/cEDaGQ"]https://ibb.co/cEDaGQ
[/URL]
[https://ibb.co/my9CVk](https://ibb.co/my9CVk)

You want to install it to the disk, not a partition. What method of partitioning are you going for? Use whole disk or manually partitioning using 'Something Else'? just using the whole disk since i dont have anny other operating systems on it ? 

How are you using Boot Repair? Running it from the Boot Repair CD or USB or installing the repo in the live session? Try the latter. See the Boot Repair link in the signature at the bottom of my post (at end of first line).
using usb i got no external disk reader

Once you get BRepair going, launch it and run the 'bootinfo' option, not the recommended repair, and post the link that spits out back here, please.


got it 

```
Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => libparted MBR boot code is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04-4.07) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.2 LTS
    Boot files:        /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 8512 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   960,184,319   960,182,272  83 Linux
/dev/sda2         960,186,366   976,771,071    16,584,706   5 Extended
/dev/sda5         960,186,368   976,771,071    16,584,704  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 14.9 GiB, 15980298240 bytes, 31211520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192    31,198,229    31,190,038   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9ae6132a-dc32-4a17-8eca-46555b627003   ext4       
/dev/sda5        71d4a1c4-0a6f-49c3-9fab-9cca2c9ce628   swap       
/dev/sdb1        6AAD-E3F0                              vfat       UUI

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 May  1 12:09 ata-TOSHIBA_MQ01ABF050_6443C1T2T -> ../../sda
lrwxrwxrwx 1 root root 10 May  1 12:09 ata-TOSHIBA_MQ01ABF050_6443C1T2T-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 May  1 12:09 ata-TOSHIBA_MQ01ABF050_6443C1T2T-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 May  1 12:09 ata-TOSHIBA_MQ01ABF050_6443C1T2T-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 May  1 12:09 usb-Generic_Flash_Disk_6B366983-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 May  1 12:09 usb-Generic_Flash_Disk_6B366983-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 May  1 12:09 wwn-0x5000039593401692 -> ../../sda
lrwxrwxrwx 1 root root 10 May  1 12:09 wwn-0x5000039593401692-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 May  1 12:09 wwn-0x5000039593401692-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 May  1 12:09 wwn-0x5000039593401692-part5 -> ../../sda5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw,relatime,data=ordered)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=9ae6132a-dc32-4a17-8eca-46555b627003 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=71d4a1c4-0a6f-49c3-9fab-9cca2c9ce628 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   1.144489288 = 1.228886016    boot/vmlinuz-4.8.0-36-generic                  1
 392.140819550 = 421.057998848  boot/vmlinuz-4.8.0-36-generic.efi.signed       1
   1.144489288 = 1.228886016    vmlinuz                                        1
 402.138294220 = 431.792705536  boot/initrd.img-4.8.0-36-generic               2
 402.138294220 = 431.792705536  initrd.img                                     2

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  b1 00 aa 29 72 5f d1 61  d9 37 22 96 61 f4 21 62  |...)r_.a.7".a.!b|
00000010  67 79 86 68 ed e2 60 98  7e 52 f1 9c 26 09 5d 81  |gy.h..`.~R..&.].|
00000020  3c 75 94 61 b9 6d 98 a3  dc 7e 02 8d 8a 8c 15 86  |<u.a.m...~......|
00000030  90 b1 f8 19 93 5c 53 37  ea 66 c9 e4 19 aa b6 2f  |.....\S7.f...../|
00000040  19 5d 90 58 b9 2f 87 88  b9 dd e6 56 86 6e f1 37  |.].X./.....V.n.7|
00000050  67 eb e0 b5 5d ba fc c7  ed 2b 6c 85 83 d6 93 75  |g...]....+l....u|
00000060  8a 35 9b c4 6e 5d 8c 5d  88 cf 41 50 30 5f 36 bc  |.5..n].]..AP0_6.|
00000070  03 63 73 c5 fd a9 46 31  38 19 a8 fe 40 36 3d ee  |.cs...F18...@6=.|
00000080  52 23 2d 45 c8 52 1a 2d  28 4e b6 80 f9 ca f6 b7  |R#-E.R.-(N......|
00000090  8b 6c e8 ce 7b ed 3c 8f  06 71 32 48 97 f5 4a f7  |.l..{.<..q2H..J.|
000000a0  c4 63 a3 58 b0 c9 dd 14  ec 0d fe 3a 7f 65 0a 0d  |.c.X.......:.e..|
000000b0  96 35 12 cf 9f ab a6 9a  8d 33 85 50 98 d9 a1 5d  |.5.......3.P...]|
000000c0  ba a9 e2 7f 68 4e f0 c5  67 6a a2 79 bb fe 57 f2  |....hN..gj.y..W.|
000000d0  ef 63 4c 28 fd 09 6f 95  82 03 87 92 80 f5 5a d1  |.cL(..o.......Z.|
000000e0  4c 13 c5 3b d6 6e 81 e7  d9 0c 70 83 6a 22 4d d6  |L..;.n....p.j"M.|
000000f0  9a 55 30 66 3a ac 4a a4  49 71 58 1e 84 3f 97 c4  |.U0f:.J.IqX..?..|
00000100  71 4b e0 e2 fd 65 4a 77  a0 6d f0 e2 7d 30 03 b1  |qK...eJw.m..}0..|
00000110  a8 01 fa 43 80 9b 4a c8  24 ef 9a 0b ae bc 51 48  |...C..J.$.....QH|
00000120  c0 1a 71 3a 83 2f d5 ce  ab 6b 48 dd 52 c4 b2 27  |..q:./...kH.R..'|
00000130  7d 7f 1d 8e ce a3 98 18  a2 29 38 99 cf 90 11 45  |}........)8....E|
00000140  54 00 27 07 76 70 95 0c  53 5b 0a ef b8 df 6b 66  |T.'.vp..S[....kf|
00000150  53 ff 76 4b 5e 00 19 92  f0 4d 0c 03 9c 45 66 00  |S.vK^....M...Ef.|
00000160  05 3d bf 12 48 98 5b ea  d9 f1 17 e3 f0 b9 b4 35  |.=..H.[........5|
00000170  3b 02 b2 b9 83 95 b3 39  f8 27 0b 6f 24 3e 05 0f  |;......9.'.o$>..|
00000180  69 6c 54 d5 6b 87 85 b5  16 fa 57 1d fc c5 bc 94  |ilT.k.....W.....|
00000190  a9 d4 10 d5 ad 83 74 71  50 91 d3 2f 88 d7 9b fc  |......tqP../....|
000001a0  c4 32 01 1b 48 c1 e7 fd  c1 40 07 86 79 0a ac 2b  |.2..H....@..y..+|
000001b0  16 71 43 0b 8c fc 44 2d  a7 61 26 dc c4 b4 00 fe  |.qC...D-.a&.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 10 fd 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/31801/mounts) leaked on lvs invocation. Parent PID 6343: bash
File descriptor 63 (pipe:[69081]) leaked on lvs invocation. Parent PID 6343: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-05-01__12h09 ===================
boot-repair version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
boot-repair is executed in live-session (Ubuntu 16.04.2 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
Partition 2 does not start on physical sector boundary.

=================== os-prober:
/dev/sda1:Ubuntu 16.04.2 LTS (16.04):Ubuntu:linux

=================== blkid:
/dev/sda1: UUID="9ae6132a-dc32-4a17-8eca-46555b627003" TYPE="ext4" PARTUUID="5443a8be-01"
/dev/sdb1: LABEL="UUI" UUID="6AAD-E3F0" TYPE="vfat"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="71d4a1c4-0a6f-49c3-9fab-9cca2c9ce628" TYPE="swap" PARTUUID="5443a8be-05"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

0+1 records in
0+1 records out
Partition 2 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.

=================== /mnt/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Feb 15 20:36 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Jan 13 16:26 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12261 Jan 13 16:26 10_linux
-rwxr-xr-x 1 root root 11082 Jan 13 16:26 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Jan 13 16:26 30_os-prober
-rwxr-xr-x 1 root root  1418 Jan 13 16:26 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jan 13 16:26 40_custom
-rwxr-xr-x 1 root root   216 Jan 13 16:26 41_custom
-rw-r--r-- 1 root root   483 Jan 13 16:26 README




=================== /mnt/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== efibootmgr -v
BootCurrent: 0009
Timeout: 0 seconds
BootOrder: 0009,0001,000D,0007,000B,0008,000A,000C,0002
Boot0001* Windows Boot Manager    HD(1,GPT,83461937-a298-4945-9dd3-7200665e3870,0x800,0x100000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...!................
Boot0002* PCI LAN: EFI Network (IPv6)    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(54ee7524ee48,0)/IPv6([::]:<->[::]:,0,0)x.J.+*.N.....=8.
Boot0003* Lenovo Recovery System    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,0,0)/HD(3,GPT,39620cc1-a370-4fe2-ab64-cc055123d3f6,0x276800,0x1f4000)/File(EFIMicrosoftBootlrsBootMgr.efi)
Boot0004  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0005  Boot Menu    FvFile(86488440-41bb-42c7-93ac-450fbf7766bf)
Boot0006  Diagnostic Splash    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0007* USB FDD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0008* ATAPI CD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
Boot0009* USB HDD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot000A* USB CD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot000B* ATA HDD: TOSHIBA MQ01ABF050                          PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,0,0)..bYVD.A...O.*..
Boot000C* PCI LAN: EFI Network (IPv4)    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(54ee7524ee48,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)x.J.+*.N.....=8.
Boot000D* kali    HD(2,GPT,b1d96562-1477-4070-b6fc-cf484601c22f,0x1f4800,0x82000)/File(EFIkaligrubx64.efi)
Boot0019* Lenovo Recovery System    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,0,0)/HD(3,GPT,39620cc1-a370-4fe2-ab64-cc055123d3f6,0x276800,0x1f4000)/File(EFIMicrosoftBootlrsBootMgr.efi)

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    grub2,    signed grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type      File system     Flags
1      1049kB  492GB  492GB   primary   ext4
2      492GB   500GB  8491MB  extended
5      492GB   500GB  8491MB  logical   linux-swap(v1)


Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      4194kB  16.0GB  16.0GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA TOSHIBA MQ01ABF0:;
1:1049kB:492GB:492GB:ext4::;
2:492GB:500GB:8491MB:::;
5:492GB:500GB:8491MB:linux-swap(v1)::;

BYT;
/dev/sdb:16.0GB:scsi:512:512:msdos:Generic Flash Disk:;
1:4194kB:16.0GB:16.0GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sdb   disk           14.9G
sdb1  part vfat      14.9G UUI
loop0 loop squashfs   1.4G
sda   disk          465.8G
sda2  part              1K
sda5  part swap       7.9G
sda1  part ext4     457.9G

KNAME ROTA RO RM STATE   MOUNTPOINT
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
loop0    1  1  0         /rofs
sda      1  0  0 running
sda2     1  0  0
sda5     1  0  0         [SWAP]
sda1     1  0  0         /mnt


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4024564k,nr_inodes=1006141,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=808032k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=9877ef558c5b5fdb)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=10125)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=808032k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt type ext4 (rw,relatime,data=ordered)
udev on /mnt/dev type devtmpfs (rw,nosuid,relatime,size=4024564k,nr_inodes=1006141,mode=755)
proc on /mnt/proc type proc (rw,nosuid,nodev,noexec,relatime)
sysfs on /mnt/sys type sysfs (rw,nosuid,nodev,noexec,relatime)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb userio v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control
Partition 2 does not start on physical sector boundary.

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     790M  9.5M  780M   2% /run
/dev/sdb1      vfat       15G  1.5G   14G  10% /cdrom
/dev/loop0     squashfs  1.4G  1.4G     0 100% /rofs
aufs           aufs      3.9G   74M  3.8G   2% /
tmpfs          tmpfs     3.9G   11M  3.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G   72K  3.9G   1% /tmp
tmpfs          tmpfs     790M   80K  790M   1% /run/user/999
/dev/sda1      ext4      451G  3.9G  424G   1% /mnt

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x5443a8be

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048 960184319 960182272 457.9G 83 Linux
/dev/sda2       960186366 976771071  16584706   7.9G  5 Extended
/dev/sda5       960186368 976771071  16584704   7.9G 82 Linux swap / Solaris



Disk /dev/sdb: 14.9 GiB, 15980298240 bytes, 31211520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     8192 31198229 31190038 14.9G  c W95 FAT32 (LBA)




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to) and reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


=================== Advice in case of suggested repair
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?

=================== User settings
The settings chosen by the user will not act on the boot.


```

---

### Post by oldfred on 2017-05-01
> BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.

When you installed  you ignored error message and converted install/drive from UEFI/gpt to BIOS/MBR. 
That still should work, but then you have to always boot in BIOS/CSM/Legacy mode. 

How you boot flash drive is separate from default boot of internal drives.
Each time you boot external drive, UEFI will show two options, one UEFI and one other that is the BIOS boot.
And how you boot UEFI or BIOS is how it installs or repairs.

But your internal drive has three boot modes, UEFI with Secure Boot on, UEFI and BIOS/CSM/Legacy.

You need to always boot in the same boot mode for flash drive and internal drive. Always UEFI or always BIOS.

If new install there are some advantages to UEFI/gpt, but if you have saved data or reconfigured system probably not worth backing up data & reinstalling.

---

### Post by Bucky Ball on 2017-05-01
Deferring to oldfred. He knows much about these things.

PS: In [your post here]("https://ubuntuforums.org/showthread.php?t=2359990&p=13640077&viewfull=1#post13640077"), you only need to post the link Boot Repair gives to the output. If you want to post the lot here, use [code] tags instead of whatever tags you've used here (quote tags?). If you don't it takes up way too much space. :)

---

### Post by oldfred on 2017-05-01
Changed to code tags from quote tags.
Easy to add with Forum's advanced editor and # icon.

 How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)

---

### Post by 3tyson on 2017-05-06
i dont think thats the problem because i had just turned on legacy boot and use to have it turned of and it gave me the same error i think the problem is that im not allowed to write annything to sda2

---

### Post by oldfred on 2017-05-07
You cannot write to sda2 as it is not a partition.
With MBR(msdos) you can have up to 4 primary partitions. But if you want more you have to convert one primary to an extended partition which is really just a container for as many logical partitions as you want to make. All logicals must be inside the extended partition.

Your sda2 is the extended partition and currently only has one logical partition swap.

```
/dev/sda1               2,048   960,184,319   960,182,272  83 Linux
/dev/sda2         960,186,366   976,771,071    16,584,706   5 Extended
/dev/sda5         960,186,368   976,771,071    16,584,704  82 Linux swap / Solaris

```

---

### Post by 3tyson on 2017-05-07
so in order for it to work i need to add more logical partitions inside it ?

---

### Post by oldfred on 2017-05-07
Everything you actually need is in sda1.
Many prefer to have additional partitions for /home and/or /mnt/data but all that is optional and depends on how you plan backups & use of system.

You show libparted boot loader. Not sure how you even get that, but better to use grub.
You can use Boot-Repair if booted in BIOS mode to reinstall grub.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

A: make sure you are booting in BIOS boot mode.
B: you will not get grub menu as you only have one install. If you want grub menu hold shift key from BIOS screen until grub menu appears.
If still issues may be video related (what video card?) or you need other boot parameters for new or unusual system.

---

