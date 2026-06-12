---
title: "fedora-ubuntu dual boot"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Arendyl on 2011-10-15
I installed ubuntu 11.10, no problems. I then made a rather foolish mistake, and attempted to dual boot my computer with Fedora 15 as well. I chose to "shrink" the ubuntu partition to make room for fedora. Now, when I boot my computer, fedora loads, which is fine, but I cannot access Ubuntu. I would like to be able to have access to both, but restoring my old system would be just fine, even restoring the system and wiping the hard drive. Thanks for your help.

---

### Post by meatytaco on 2011-10-15
Maybe try installing ubuntu again over the old one? Might work things out. I haven't personally had this problem, but that's where I would start if I did.

---

### Post by Arendyl on 2011-10-15
I tried that, but my computer recognizes that ubuntu is installed. IT will only let me overwrite the ubuntu that is already there

---

### Post by howefield on 2011-10-15
You could reinstall grub 2, have a read here...

[https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Reinstalling_GRUB2)

For info, Fedora 16 will have grub 2, so will most likely play nicer with your Ubuntu installs.

---

### Post by coffeecat on 2011-10-15
+1 to what howefield said.

Alternatively, Fedora 15 and before use legacy grub. If you post the contents of the boot script output for your system...

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

... someone could help you edit the Fedora /boot/grub/menu.lst file so that Fedora's grub menu shows an Ubuntu entry.

---

### Post by bennachie on 2011-10-15
Boot from your Ubuntu LiveCD. Open a terminal window, then enter the following commands:

sudo fdisk -l

[that will give you a list of partitions - make sure you have identified which one is the "/" partition for Ubuntu]

sudo mkdir /media/sdax	

[where “sdax” identifies the "/" partition for Ubuntu - change it to whatever is appropriate]

sudo mount /dev/sdax /media/sdax
sudo grub-install –root-directory=/media/sdax /dev/sda
exit

[that's a double "-" sign in front of root-directory, and note that /dev/sda is correct, using /dev/sdax won't give you the result you want]

After rebooting Ubuntu, run:

sudo update-grub

You might like to note that the beta version of Fedora 16, which works pretty well, has switched to Grub2, so you could also solve your problem by reinstalling Fedora in that version.

---

### Post by garvinrick4 on 2011-10-15
Most likely Fedora made a /boot partition when you installed using grub-legacy.
Unless you specified not to install grub at all in "anaconda" Fedora's of installation
application. 
Run:
```
sudo parted -l
``` (Lower case L)

and see if a small /boot partition for fedora there also. If so have to install grub2 into
mbr with a live cd and then remove /boot and / for fedora install then boot into Ubuntu and update your grub so as not to have fedora or its /boot partition in your grub config file. Now you can reinstall and choose not to install grub at all in Anaconda during installation process of Fedora then go into ubuntu after install and update grub to add Fedora to its grub2 with no grub-legacy boot files anywhere at all, works a lot easier this way. Ubuntu is always in charge of boot process with its grub2 since Fedora does not have its own grub config file. ( I myself to not like mixing grub-legacy (grub) and grub2 (grub-pc)
# If no /boot partition for Fedora just have to remove reinstall Fedora in same partiition
and choose not to install grub at all. But most likely a /boot partition was made.

Fedora uses /boot partition to upgrade from version to version with so will now have to do a clean install if you want to go up to 16 when released.

### If you give coffeecat his boot_info_script it will tell you in better definition what Fedora has done with partition table and what exactly to remove.
I would say give him the boot script and let him give you full instructions with code to copy and paste. Enjoy your Ubuntu (if coffeecat finishes his session I will help you)

---

### Post by garvinrick4 on 2011-10-15
@Arendyl
I understand you are new to these forums and do not know if you are new to Ubuntu.
If you need assistance to run boot script or anything at all you just ask.

---

### Post by Arendyl on 2011-10-15
@coffeecat
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy0.97-71.fc15 is installed in the MBR of /dev/sda and looks at 
    sector 6151714 on boot drive #1 for the stage2 file.  A stage2 file is at 
    this location on /dev/sda.  Stage2 looks on partition #3 for 
    /grub/grub.conf..
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 4480624 of the same hard drive for 
                       core.img. core.img is at this location and looks for  
                       on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda4: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>........?.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 12180928 of /dev/sdb1 for 
                       its second stage. SYSLINUX is installed in the  
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 16.1 GB, 16139681792 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     6,123,519     6,121,472  83 Linux
/dev/sda2          29,446,142    31,520,767     2,074,626   5 Extended
/dev/sda5          29,446,144    31,520,767     2,074,624  82 Linux swap / Solaris
/dev/sda3           6,123,520     7,147,519     1,024,000  83 Linux
/dev/sda4           7,147,520    29,444,095    22,296,576  8e Linux LVM


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192    15,523,839    15,515,648   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       71d1926a-4f7d-42c9-b351-425dadf0af36   ext3       
/dev/sda1        1a6bdd81-3c24-46ee-8ad5-86577fdda022   ext4       
/dev/sda3        629b7a0e-4792-4ada-9dac-c9a52189dd78   ext4       
/dev/sda4        yNBVRE-L0zk-l69O-qjM0-XCeN-LIzk-Ds3WjL LVM2_member 
/dev/sdb1        3132-3263                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 1a6bdd81-3c24-46ee-8ad5-86577fdda022
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 1a6bdd81-3c24-46ee-8ad5-86577fdda022
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
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1a6bdd81-3c24-46ee-8ad5-86577fdda022
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=1a6bdd81-3c24-46ee-8ad5-86577fdda022 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1a6bdd81-3c24-46ee-8ad5-86577fdda022
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=1a6bdd81-3c24-46ee-8ad5-86577fdda022 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1a6bdd81-3c24-46ee-8ad5-86577fdda022
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1a6bdd81-3c24-46ee-8ad5-86577fdda022
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1a6bdd81-3c24-46ee-8ad5-86577fdda022 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     3
               =                vmlinuz                                        1

============================= sda3/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_arlithen-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.6-26.rc1.fc15.i686)
    root (hd0,2)
    kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_arlithen-lv_root rd_LVM_LV=vg_arlithen/lv_root rd_LVM_LV=vg_arlithen/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/grub.conf                                 1
               =                grub/menu.lst                                  1
               =                grub/stage2                                    1
               =                initramfs-2.6.38.6-26.rc1.fc15.i686.img        2
               =                vmlinuz-2.6.38.6-26.rc1.fc15.i686              1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  7f ab d3 a3 eb 4a e8 e8  85 ee 6a 86 9a a2 55 e6  |.....J....j...U.|
00000010  e7 e8 c6 ea c8 07 d4 a1  ff 00 1f f1 f6 26 83 e2  |.............&..|
00000020  1d 18 91 45 af 40 f6 44  85 a8 d7 cb 28 e0 5f 86  |...E.@.D....(._.|
00000030  fd 5c 93 fe 3e c4 96 c2  b1 d0 75 55 21 d8 aa f1  |.\..>.....uU!...|
00000040  e9 df 1e 8f a4 32 23 2a  9d 2c a4 0b de e6 f6 3e  |.....2#*.,.....>|
00000050  d2 ce 41 a8 af 48 e5 34  63 fb 3a 1b 76 3e 34 55  |..A..H.4c.:.v>4U|
00000060  65 b1 b1 14 d2 64 a9 88  da ff 00 9b 85 22 fe c1  |e....d......."..|
00000070  bb cd c7 85 6b 23 d7 82  9e 90 dc 3e 88 1a bd 6d  |....k#.....>...m|
00000080  41 f1 0a 7f e1 bb 23 09  13 c5 1c a9 15 1d 2c 65  |A.....#.......,e|
00000090  4f a5 81 55 d3 c0 1f 5f  a8 f7 cd 3f 73 d0 5c 6f  |O..U..._...?s.\o|
000000a0  d3 c8 a7 89 6f f0 9e a0  1e 61 21 af 58 fc cf f8  |....o....a!.X...|
000000b0  4f 56 7b b5 b2 a9 26 32  48 e0 94 04 75 8c b8 6b  |OV{...&2H...u..k|
000000c0  7a 5b e9 a7 4f f4 fe be  e0 bb 8b 76 13 77 f4 44  |z[..O......v.w.D|
000000d0  85 2b 9e 95 b0 d6 44 1e  38 5a ce 0f 3c 70 b7 27  |.+....D.8Z..<p.'|
000000e0  f2 3d bf 14 44 2d 6b d1  bd 83 14 26 be 7d 71 fb  |.=..D-k....&.}q.|
000000f0  2a 4a cc 8b 68 44 02 eb  a9 be 97 b0 b9 b7 1f 5f  |*J..hD........._|
00000100  62 4b 42 62 88 16 3d 1e  a3 32 9c f4 22 63 f0 f4  |bKBb..=..2.."c..|
00000110  62 28 dc 28 27 49 b8 bf  20 8e 2f 6f 6b e3 b8 90  |b(.('I.. ./ok...|
00000120  b6 3a 66 7b 87 a8 8f d3  a5 45 2e 32 94 c2 41 45  |.:f{.....E.2..AE|
00000130  d4 3f a7 d2 d6 fc fb 3b  b7 91 88 af 5b 49 18 0c  |.?.....;....[I..|
00000140  75 30 6d ea 39 a1 90 aa  2d ca f2 2c 01 3f 9e 3f  |u0m.9...-..,.?.?|
00000150  c7 d9 94 53 48 32 0f 4f  2c ac 09 fb 3a 49 c9 b4  |...SH2.O,...:I..|
00000160  a9 c3 bb 08 03 12 18 11  a5 ff 00 23 fa 8b 7b 7b  |...........#..{{|
00000170  eb 26 0d 8f 2e 91 fd 43  86 24 1c 74 86 cf 6c 48  |.&.....C.$.t..lH|
00000180  e4 8a 62 20 b2 15 bd 86  ae 2f fe b7 b5 91 6e 2c  |..b ...../....n,|
00000190  28 18 e7 ab ad f3 0c 67  1d 06 23 68 41 04 f1 84  |(......g..#hA...|
000001a0  a5 4b 7d 09 b3 ff 00 5f  af b4 b7 9b 8b 9f 3e 96  |.K}...._......>.|
000001b0  c7 75 21 a5 3a 32 9b 0f  6a d1 9a 25 6f 12 00 fe  |.u!.:2..j..%o...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 1f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by Arendyl on 2011-10-15
@bennachie
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 16.1 GB, 16139681792 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d4db4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     6123519     3060736   83  Linux
/dev/sda2        29446142    31520767     1037313    5  Extended
/dev/sda3         6123520     7147519      512000   83  Linux
/dev/sda4         7147520    29444095    11148288   8e  Linux LVM
/dev/sda5        29446144    31520767     1037312   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00043f1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192    15523839     7757824    b  W95 FAT32

---

### Post by Arendyl on 2011-10-15
@garvinrick4
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA A-DATA_SSD_16GB (scsi)
Disk /dev/sda: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  3135MB  3134MB  primary   ext4         boot
 3      3135MB  3660MB  524MB   primary   ext4
 4      3660MB  15.1GB  11.4GB  primary                lvm
 2      15.1GB  16.1GB  1062MB  extended
 5      15.1GB  16.1GB  1062MB  logical


Model: Generic- Multi-Card (scsi)
Disk /dev/sdb: 7948MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  7948MB  7944MB  primary  fat32        boot


ubuntu@ubuntu:~$

---

### Post by garvinrick4 on 2011-10-15
You have a very small drive but fast 16 gig. I would think you would
only want 1 operating system on this drive. How much RAM do you have installed?
You have a LVM partition with 11 gig Fedora and on sda3 looks to be a /boot partition of 528 meg for fedora. And 3 gig or so for Ubuntu on sda1. With the extended partition holding a 1 gig swap in sda5. 
We can delete all partitions except sda1 and then resize sda1 to take all but 1 gig at end and make new 1 gig for swap at end of drive being sda2. (gparted will make all sda#'s for you)
Put in your live Cd and or USB and open a app called gparted and give us a screenshot  (live cd is install Cd using Try Ubuntu)
if you can.
If not right click on all partitions to the right of sda1 in gparted and delete them.
right click on sda1 resize sda1 to take up all but 1 gig. Now right click on 1 gig left over and make new partition and make it swap. You must hit green apply arrow after each instance to make it happen. 
While in the Live CD (the same place you ran the boot script from.)
Now open a terminal and copy and paste this.
```
sudo mount /dev/sda1 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```Grub for Ubuntu is now reinstalled in mbr (master boot record) or your drive and will
boot off of the files in sda1 your Ubuntu install. 

Below is graphic for running gparted
to get rid of all and resize sda1 to take all of drive but 1 gig. ( you will now have a Ubuntu partition sda1 of 15 gig and a 1 gig swap to take up all of your 16 gig drive.

[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by Arendyl on 2011-10-15
here

---

### Post by garvinrick4 on 2011-10-15
Yes right click on all to the right of sda1 and delete, [COLOR=Red]do not delete sda1.[/COLOR]
Now right click on sda1 and resize to take up all but 1 gig of drive.
Remember after each instruction hit the green apply arrow so to execute command.
Now take the 1 gig leftover and make new partition and make it swap.
Then run the commands I gave you in previous post to put grub2 back in place.
Just copy and paste them into a terminal in your Live CD or USB.
Then reboot and done. Should now boot into Ubuntu.
If you want another Operating system get a USB drive to install it on and let Ubuntu
have the 16 gig ssd drive you have now. Will be around if any questions or troubles.

---

### Post by Arendyl on 2011-10-15
works perfectly, thanks a million.

---

### Post by garvinrick4 on 2011-10-15
> works perfectly, thanks a million.You are welcome, enjoy your Ubuntu Arendyl.
If you will go to top right under Thread Tools and mark as Solved so others with
same can benefit.

---

