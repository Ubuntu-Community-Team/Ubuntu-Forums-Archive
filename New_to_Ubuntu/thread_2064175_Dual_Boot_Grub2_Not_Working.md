---
title: "Dual Boot Grub2 Not Working"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by eyeofreason on 2012-09-28
[LEFT] I just bought an Asus K55N and I want to dual boot Ubuntu 12.04 x64 with the factory installed Windows 7.  I used the live-cd. It partitioned the hard drive for me, but when I restart it goes straight to Window7. When I look in the bios, it gives me the option to boot from dvd or Windows loader. I have been running Ubuntu for years now and have installed a dual boot on several machines. I have never seen the grub gui not appear.   If anyone has the time, I would greatly appreciate it. 
Thanks.
[/LEFT]

---

### Post by oldfred on 2012-09-28
Is this a new UEFI system?

Download this into liveCD or download as a repairCD and post the link it creates for BootInfo.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by eyeofreason on 2012-09-28
Thank you for helping me. It is a UEFI (new to me). 
Here is the info that you requested.

 ```
Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    657864704 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt7)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda6: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8:A __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       411,647       409,600 EFI System partition
/dev/sda2         411,648       673,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         673,792   391,383,039   390,709,248 Data partition (Windows/Linux)
/dev/sda4     391,383,040   657,863,679   266,480,640 Data partition (Windows/Linux)
/dev/sda5     924,344,320   976,773,119    52,428,800 Windows Recovery Environment (Windows)
/dev/sda6     657,864,704   657,866,751         2,048 BIOS Boot partition
/dev/sda7     657,866,752   917,092,351   259,225,600 Data partition (Windows/Linux)
/dev/sda8     917,094,150   924,344,319     7,250,170 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0472-5756                              vfat       SYSTEM
/dev/sda3        8AF24081F240738B                       ntfs       OS
/dev/sda4        98C03E40C03E24C2                       ntfs       DATA
/dev/sda5        AC7A43BA7A438056                       ntfs       Recovery
/dev/sda7        628e13a8-8dc2-4b86-b9ee-78329a1007a1   ext4       
/dev/sda8        d884ffb1-a61b-48f0-ae52-d8fa86b8e5e4   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt7)'
search --no-floppy --fs-uuid --set=root 628e13a8-8dc2-4b86-b9ee-78329a1007a1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt7)'
  search --no-floppy --fs-uuid --set=root 628e13a8-8dc2-4b86-b9ee-78329a1007a1
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 628e13a8-8dc2-4b86-b9ee-78329a1007a1
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=628e13a8-8dc2-4b86-b9ee-78329a1007a1 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 628e13a8-8dc2-4b86-b9ee-78329a1007a1
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=628e13a8-8dc2-4b86-b9ee-78329a1007a1 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 628e13a8-8dc2-4b86-b9ee-78329a1007a1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 628e13a8-8dc2-4b86-b9ee-78329a1007a1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 8AF24081F240738B
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda5)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt5)'
    search --no-floppy --fs-uuid --set=root AC7A43BA7A438056
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=628e13a8-8dc2-4b86-b9ee-78329a1007a1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=d884ffb1-a61b-48f0-ae52-d8fa86b8e5e4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-3.2.0-29-generic               1
            ?? = ??             boot/vmlinuz-3.2.0-29-generic                  1
            ?? = ??             initrd.img                                     1
            ?? = ??             vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 04 de 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 40 06 00 11 03 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 56 57 72 04 4e  4f 20 4e 41 4d 45 20 20  |..)VWr.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[6118]) leaked on lvscan invocation. Parent PID 10595: bash
File descriptor 8 (pipe:[6118]) leaked on lvscan invocation. Parent PID 10595: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-09-28__14h48 ===================
boot-repair version : 3.18-0ppa52~lucid
boot-sav version : 3.192-0ppa24~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version : 3.18-0ppa14~lucid
Please connect internet. Then close this window.
/usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu) lucid main
/usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) lucid main
W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/Release.gpg](http://cdn.debian.net/debian/dists/squeeze/Release.gpg)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2](http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2](http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/Release.gpg](http://security.debian.org/dists/squeeze/updates/Release.gpg)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2](http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2](http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg](http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2](http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2](http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.


0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 55 not upgraded.
WARNING: The following packages cannot be authenticated!
os-uninstaller
Err [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/) lucid/main os-uninstaller all 3.18-0ppa12~lucid
Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa12~lucid_all.deb](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa12~lucid_all.deb)  Could not resolve 'ppa.launchpad.net'
E: Some files failed to download

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 55 not upgraded.
WARNING: The following packages cannot be authenticated!
boot-repair
Err [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) lucid/main boot-repair all 3.18-0ppa52~lucid
Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.18-0ppa52~lucid_all.deb](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.18-0ppa52~lucid_all.deb)  Could not resolve 'ppa.launchpad.net'
E: Some files failed to download
File descriptor 7 (pipe:[6118]) leaked on lvs invocation. Parent PID 3918: /bin/sh
File descriptor 8 (pipe:[6118]) leaked on lvs invocation. Parent PID 3918: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 18.07.2012, squeeze, Debian, x86_64)
CPU op-mode(s):        64-bit

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda3:Windows 7 (loader):Windows:chain
/dev/sda5:Windows Recovery Environment (loader):Windows1:chain
/dev/sda7:Ubuntu 12.04.1 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/sda1: LABEL="SYSTEM" UUID="0472-5756" TYPE="vfat"
/dev/sda3: LABEL="OS" UUID="8AF24081F240738B" TYPE="ntfs"
/dev/sda4: LABEL="DATA" UUID="98C03E40C03E24C2" TYPE="ntfs"
/dev/sda5: LABEL="Recovery" UUID="AC7A43BA7A438056" TYPE="ntfs"
/dev/sda7: UUID="628e13a8-8dc2-4b86-b9ee-78329a1007a1" TYPE="ext4"
/dev/sda8: UUID="d884ffb1-a61b-48f0-ae52-d8fa86b8e5e4" TYPE="swap"
/dev/loop0: TYPE="squashfs"


1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/memtest.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi


=================== sda7/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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





=================== sda7/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug 23 16:56 grub.d
total 56
-rwxr-xr-x 1 root root 6715 May 17 07:21 00_header
-rwxr-xr-x 1 root root 5522 May 17 07:07 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17 07:21 10_linux
-rwxr-xr-x 1 root root 6335 May 17 07:21 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17 07:21 30_os-prober
-rwxr-xr-x 1 root root  214 May 17 07:21 40_custom
-rwxr-xr-x 1 root root   95 May 17 07:21 41_custom
-rw-r--r-- 1 root root  483 May 17 07:21 README




WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

ReadEFI: /dev/sda , N 128 , 0 ,  , PRStart 1024 , PRSize 128

=================== dmesg | grep EFI :
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.




=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda3.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    no-grldr,    boot/bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda5.
sda7    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda7.

sda    : GPT,    GPT,    BIOS_boot,    has-correctEFI,     not-usb,    2048 sectors * 512 bytes

=================== parted -l:

Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name                          Flags
1      1049kB  211MB  210MB   fat32           EFI system partition          boot
2      211MB   345MB  134MB                   Microsoft reserved partition  msftres
3      345MB   200GB  200GB   ntfs            Basic data partition
4      200GB   337GB  136GB   ntfs            Basic data partition
6      337GB   337GB  1049kB                                                bios_grub
7      337GB   470GB  133GB   ext4
8      470GB   473GB  3712MB  linux-swap(v1)
5      473GB   500GB  26.8GB  ntfs            Basic data partition          hidden, diag


                                                                            Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                            Error: /dev/sr0: unrecognised disk label


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dvd dvdrw fd full fuse hidraw0 hidraw1 hpet initctl input kmsg log MAKEDEV mcelog md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sg0 sg1 shm snapshot snd sndstat sr0 stderr stdin stdout urandom usb v4l vga_arbiter video0 xconsole zero
ls /dev/md:
ls /mnt/boot-sav/sda3: Windows Users Information Volume System $RECYCLE.BIN Recovery (x86) Files Program Files Program ProgramData PerfLogs pagefile.sys NST MSOCache K55.BIN hiberfil.sys eSupport Settings and Documents BOOTSECT.BAK boot-sav bootmgr Boot AsusVibeData ANG0

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.7G  8.6M  1.7G   1% /
tmpfs        tmpfs    1.7G     0  1.7G   0% /lib/init/rw
udev         tmpfs    1.7G  224K  1.7G   1% /dev
tmpfs        tmpfs    1.7G     0  1.7G   0% /dev/shm
/dev/sr0   iso9660    347M  347M     0 100% /live/image
tmpfs        tmpfs    1.7G  8.6M  1.7G   1% /live/cow
tmpfs        tmpfs    1.7G     0  1.7G   0% /live
tmpfs        tmpfs    1.7G  8.0K  1.7G   1% /tmp
/dev/sda1     vfat    196M   23M  174M  12% /mnt/boot-sav/sda1
/dev/sda3  fuseblk    187G   69G  118G  37% /mnt/boot-sav/sda3
/dev/sda4  fuseblk    128G   90M  127G   1% /mnt/boot-sav/sda4
/dev/sda5  fuseblk     25G   13G   13G  50% /mnt/boot-sav/sda5
/dev/sda7     ext4    122G  2.7G  113G   3% /mnt/boot-sav/sda7

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x527cd163

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.


sda1 EFI part (detected by BIS but not in fstab) in same disk
EFI detected. Please check the options.
sda1 EFI part (detected by BIS but not in fstab) in same disk
=================== Advice displayed in case of recommended repair
Warning: continuing without internet would leave your system unbootable. Please connect internet.
BIOS-Boot detected. You may want to retry after deactivating the [Separate /boot/efi partition:] option.
Do you want to continue?
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!

=================== Default settings
Recommended-Repair
This setting would purge (in order to fix packages) and reinstall the grub-efi of sda7, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    backup-and-rename-efi-files

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!
Please connect internet. Then close this window.
```

---

### Post by eyeofreason on 2012-09-28
[http://paste.ubuntu.com/1248202/](http://paste.ubuntu.com/1248202/)

---

### Post by oldfred on 2012-09-28
I thought Boot-Repair had the info on whether you have 32bit or 64bit version of Ubuntu. I may have missed it.

If you have 64 bit, just run the recommended repairs. You have to fully uninstall the BIOS/MBR version of grub2 or grub-pc and install the grub2 UEFI version or grub-efi. It also adds a fstab entry for the efi partition to fstab. 

You also are showing lucid entries. Did you get the old version somehow? You will have to delete any lucid entries in your sources if they are are still there.

cp /etc/apt/sources.list ~/sources.list.backup

To edit, suggest just adding # in front on any entry with lucid to convert to comment.
 sudo gedit  /etc/apt/sources.list

---

### Post by eyeofreason on 2012-09-28
Thank you very much. Hours of headache over!

---

### Post by eyeofreason on 2012-09-28
Windows boots fine from grub loader but Ubuntu hangs. It just shows a blank plumb colored screen .

---

### Post by oldfred on 2012-09-28
Probably video related, but possibly other boot parameters are required. What video card/chip does it have?

 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by eyeofreason on 2012-09-28
I was afraid that the video card might cause issues. It has a AMD processor with a Radeon HD 7640G GPU built on the chip.

---

### Post by oldfred on 2012-09-28
I do not know AMD, I have nVidia.

If nomodeset or one of these do not work start a new thread with your video issue in the title. Those that may know Radeon issues will not be looking at a thread with grub in the title.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Rykhan on 2012-10-09
I'm having these same problems with the same laptop after multiple installs. 

I'm not sure if it's a problem with the uefi or not,  but when I try to run boot repair and install grub-efi through the terminal its coming up with errors while trying to configure grub-efi-amd64.

After boot repair is finished I'm able to get into the grub loader and access Win7 but as eyeofreason stated, it just hangs on at the blank ubuntu plumb looking screen.

Also when I try to load into recovery it says loading initial ramdisk and freezes. 

Sorry if I have typos above,  I'm on my cellphone.

---

### Post by oldfred on 2012-10-09
@Rykhan
At grub menu have you tried any of the Boot Options. Press e and add nomodeset in place of splash quiet or add other settings and see it if boots.

---

### Post by YannBuntu on 2012-10-09
> **oldfred said:**
> I thought Boot-Repair had the info on whether you have 32bit or 64bit version of Ubuntu. I may have missed it.

It is in the "PARTITIONS & DISKS" paragraph of the Boot-Info.
Furthermore, Boot-Repair will check that the installed Ubuntu is 64bit before installing grub-efi.

---

### Post by eyeofreason on 2012-10-09
Thank you to everyone that helped me with this. I have resolved my problems but not really the issue. The machine came with Window 7 occupying the first 4 partitions.  After using boot repair, it mentioned that my Ubuntu partition might be to far from the beginning of the disc and therefor the uefi/bios might not recognize it.  

I dug around in the bios and confirmed that it was not recognizing the partition as bootable.  Asus refused to give me a Windows recovery disk. I managed to get one elsewhere, but used my serial on the bottom of my notebook. I installed windows in 2 partitions and then put my live cd in and everything from there installed just like clockwork.  

This is what worked for this simple man. I hope you guys can figure out a better way from the info that I've given, so that other people that buy this machine don't feel, as I did, like they are being forced to hand over their computer to M$. Let me know when you guys are satisfied and I will mark it solved. 

Thanks Again.

---

### Post by Rykhan on 2012-10-09
> @Rykhan
At grub menu have you tried any of the Boot Options. Press e and add  nomodeset in place of splash quiet or add other settings and see it if  boots. 	

I have tried this but to no prevail. Thank you for your help!

> **eyeofreason said:**
> Thank you to everyone that helped me with this. I have resolved my problems but not really the issue. The machine came with Window 7 occupying the first 4 partitions.  After using boot repair, it mentioned that my Ubuntu partition might be to far from the beginning of the disc and therefor the uefi/bios might not recognize it.  

I dug around in the bios and confirmed that it was not recognizing the partition as bootable.  Asus refused to give me a Windows recovery disk. I managed to get one elsewhere, but used my serial on the bottom of my notebook. I installed windows in 2 partitions and then put my live cd in and everything from there installed just like clockwork.  

This is what worked for this simple man. I hope you guys can figure out a better way from the info that I've given, so that other people that buy this machine don't feel, as I did, like they are being forced to hand over their computer to M$. Let me know when you guys are satisfied and I will mark it solved. 

Thanks Again.

I think this is the route in which i'm going to take as well. Wish there  was an easier way so i can preserve the factory installed Win7, but  nothing else seems to be working.

---

### Post by YannBuntu on 2012-10-09
> **eyeofreason said:**
> Let me know when you guys are satisfied and I will mark it solved.

Thanks for the feedback. Please could you simply indicate your new [Boot-Info URL]("https://help.ubuntu.com/community/Boot-Info") (click the "Create BootInfo", not the "Repair" button), so that we know your current situation?

---

### Post by NikTh on 2012-10-09
> **eyeofreason said:**
> Thank you to everyone that helped me with this. I have resolved my problems but not really the issue. **The machine came with Window 7 occupying the first 4 partitions.**  After using boot repair, it mentioned that my Ubuntu partition might be to far from the beginning of the disc and therefor the uefi/bios might not recognize it.  

Hi ,

[s]If you had said this at first place (first post) then the guide would be different and the solution closer. 

When a PC comes with already 4 primary partitions , then you must use a tool from within windows (like partition-master) and convert the C partition to Extended.
Then with same tool , shrink the partition and then create a logical partition for Ubuntu to be installed. 
In this way not needed to delete any of the partitions and Ubuntu installation is easy.

But now is late for the instructions. [/s]

Thanks

---

### Post by YannBuntu on 2012-10-10
**@NikTh:** your instructions would have been incorrect as the disk is GPT (see post[#3]("http://ubuntuforums.org/showpost.php?p=12266792&postcount=3")).

---

### Post by NikTh on 2012-10-10
> **YannBuntu said:**
> **@NikTh:** your instructions would have been incorrect as the disk is GPT (see post[#3]("http://ubuntuforums.org/showpost.php?p=12266792&postcount=3")).


Hmmm... the truth is that I never tested this in a GPT. And even more truth that I didn't see it in 3rd post . :P 
Thanks you mentioned this.

---

### Post by YannBuntu on 2012-10-10
**@NikTh:** FYI, there are no "extended" nor "logical" partitions on a GPT disk, and there is no "4 primary" limitation like on Ms-Dos disk. Installing GRUB2 on a GPT disk requires either a BIOS-Boot or an EFI partition, see: [https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29](https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29)

---

### Post by NikTh on 2012-10-10
> **YannBuntu said:**
> **@NikTh:** FYI, there are no "extended" nor "logical" partitions on a GPT disk, and there is no "4 primary" limitation like on Ms-Dos disk. Installing GRUB2 on a GPT disk requires either a BIOS-Boot or an EFI partition, see: [https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29](https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29)


Thanks again **@YannBuntu  **, its time to edit my post :)

---

### Post by Rykhan on 2012-10-10
Thanks all, I'm not sure what the original problem was but i completely reformatted the whole drive, and everything seems to work now.

I've been dealing with Ubuntu for years, and I've never run into a problem with installation until this whole UEFI thing.

---

