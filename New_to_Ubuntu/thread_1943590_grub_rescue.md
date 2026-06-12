---
title: "grub rescue"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by jeboza on 2012-03-19
i tried to install ubuntu and got the following error error no such device: f51161c1-9230-4a9d-bc0c-cfc0b97769bc, grub rescue>

. I've tried all the resolutions I've found regarding this issue including boot repair all to no avail..`been running win 7 64bit on a HP Pavilllion quad core phenom ii for about a year now. running mac os as well. I've used ls to find the drives in the machine. tried to set the prefix etc.

right now my systems down. can't get back on to win 7 and ubuntu refuses to load except via the cd. i can see my drive but have no way of loading either os. 

any help would be greatly appreciated.

thanks

---

### Post by josephmills on 2012-03-19
Hello there and welcome to the forums. Could you please boot a live cd then open your terminal (ctrl+alt+t) then enter in ```
sudo fdisk -l
``` 
Then paste that here please.
Once again Welcome to Ubuntu Forums :p

---

### Post by jeboza on 2012-03-19
I'm on the live cd and i see my drives in the home folder. i do not get a terminal service by hitting the ctrl+alt+t and am unable to enter that command

tks

---

### Post by overdrank on 2012-03-19
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by jeboza on 2012-03-19
thx

---

### Post by jeboza on 2012-03-19
I'm on the live cd and i see my drives in the home folder. i do not get a terminal service by hitting the ctrl+alt+t and am unable to enter that command

tks

---

### Post by jeboza on 2012-03-19
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x855ed430

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1928189951   963991552    7  HPFS/NTFS/exFAT
/dev/sda3      1928189952  1953521663    12665856    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45df5ea9

  Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  2930274303  1465136128    7  HPFS/NTFS/exFAT

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008ea15

  Device Boot      Start         End      Blocks   Id  System
/dev/sdi1              63  1001665909   500832923+   c  W95 FAT32 (LBA)
/dev/sdi2      1001666558  1953523711   475928577    5  Extended
/dev/sdi5      1919973376  1953523711    16775168   82  Linux swap / Solaris
/dev/sdi6      1001666560  1886418943   442376192   83  Linux
/dev/sdi7      1886420992  1919961087    16770048   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdj: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03bf0065

  Device Boot      Start         End      Blocks   Id  System
/dev/sdj1   *          63    42502314    21251126   83  Linux
/dev/sdj2        42504190   625141759   291318785    5  Extended
/dev/sdj5        42504192   591587327   274541568   83  Linux
/dev/sdj6       591589376   625141759    16776192   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by jeboza on 2012-03-20
I have tried everything I can find on this issue including running Ubuntu grub rescue on the Ubuntu desktop. I really thought it was going to work. At this point, it might just be easier to reinstall windows 7 and get rid of Ubuntu, the programs on the computer are more important under windows than the data. It's backed up, though reloading those program would take several days plus reinstalling thr data.

The desktop version on cd works great, but it's obvious there's something wrong with the os loader. I've typed in more line commands than since DOS today. Thank God for up arrow.

Just wanting to see if anything had improved over the last couple of years. Had better success with Red Hat really had expected more from Ubuntu. I had a 320gb drive just for it.

Again thanks.

If you have any thoughts I'd really appreciate it.

---

### Post by varunendra on 2012-03-20
Use Boot-Repair again to create 'Boot-Info Summary', then post it (or its pastebin link) here. Although I don't know how well it works with GPTs, hopefully it 'should' give us a clear picture of your disks.

---

### Post by jeboza on 2012-03-20
> **varunendra said:**
> Use Boot-Repair again to create 'Boot-Info Summary', then post it (or its pastebin link) here. Although I don't know how well it works with GPTs, hopefully it 'should' give us a clear picture of your disks.

Ran boot-repair again, didn't fix anything and frankly I was unable to connect to the Internet in order to provide set report. I did enter all my network info and yet kept saying "unable to connect to the Internet". Internet is up. Idk of any other way of copying and posting that report? Any ideas?

I was looking around on the blogs and found another program called super-grub2-disk-hybridxxxxxx.iso that identifies OS's and was able to boot my win 7 partition. Though this program was suppose to find OS's it only found 2 instances 1 appears to be utunbu and the other is win7. Only win 7 works, ubuntu starts its attempt to load, but just restarts the system.

Obviously, this is less than ideal for me, is there anyway to repair the Ubuntu version with any other tool? Starting to enjoy this after 10 year away from when I last used UNIX and six years since Red Hat.


Any and all help would be greatly appreciated. Thx.

---

### Post by varunendra on 2012-03-20
> **jeboza said:**
> Idk of any other way of copying and posting that report? Any ideas?
If you were disconnected while 'creating' the boot-info-summary, it would have created it as a text file in 'root's home'. So just open nautilus as root by:
```
gksu nautilus
```, look if that Boot-Info_summary file is lying there. Just copy or move it to a pen drive or another location from where you can easily access it (set its permission as 'read/write' for all), then upload it from the system from which you are posting here.

---

### Post by jeboza on 2012-03-20
hers's the log file you requested. Thanks again.
```

Boot Info Script 0.60-git      [23 Feb 2012]


============================= Boot Info Summary: ===============================

=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
   the same hard drive for core.img. core.img is at this location and looks
   in partition 6 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdb.
=> Windows is installed in the MBR of /dev/sdc.
=> No boot loader is installed in the MBR of /dev/sdg.
=> Grub2 (v1.99) is installed in the MBR of /dev/sdi and looks at sector 1 of
   the same hard drive for core.img. core.img is at this location and looks
   for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

   File system:       ntfs
   Boot sector type:  Windows Vista/7: NTFS
   Boot sector info:  No errors found in the Boot Parameter Block.
   Operating System:
   Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

   File system:       ntfs
   Boot sector type:  Windows Vista/7: NTFS
   Boot sector info:  No errors found in the Boot Parameter Block.
   Operating System:  Windows 7
   Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

   File system:       ntfs
   Boot sector type:  Windows Vista/7: NTFS
   Boot sector info:  No errors found in the Boot Parameter Block.
   Operating System:
   Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

   File system:
   Boot sector type:  -
   Boot sector info:
   Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

   File system:       ntfs
   Boot sector type:  Windows Vista/7: NTFS
   Boot sector info:  No errors found in the Boot Parameter Block.
   Operating System:
   Boot files:

sdc1: __________________________________________________________________________

   File system:       ntfs
   Boot sector type:  Windows Vista/7: NTFS
   Boot sector info:  No errors found in the Boot Parameter Block.
   Operating System:
   Boot files:

sdg1: __________________________________________________________________________

   File system:       swap
   Boot sector type:  -
   Boot sector info:

sdi1: __________________________________________________________________________

   File system:       ext4
   Boot sector type:  -
   Boot sector info:
   Operating System:
   Boot files:

sdi2: __________________________________________________________________________

   File system:       Extended Partition
   Boot sector type:  Unknown
   Boot sector info:

sdi5: __________________________________________________________________________

   File system:       ext4
   Boot sector type:  -
   Boot sector info:
   Operating System:  Ubuntu 11.10
   Boot files:        /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab
                      /grub/core.img /boot/grub/core.img

sdi6: __________________________________________________________________________

   File system:       swap
   Boot sector type:  -
   Boot sector info:

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,928,189,951 1,927,983,104   7 NTFS / exFAT / HPFS
/dev/sda3       1,928,189,952 1,953,521,663    25,331,712   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2         264,192 3,907,028,991 3,906,764,800 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 2,930,274,303 2,930,272,256   7 NTFS / exFAT / HPFS


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *             26    15,724,799    15,724,774  82 Linux swap / Solaris


Drive: sdi _____________________________________________________________________

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdi1    *             63    42,502,314    42,502,252  83 Linux
/dev/sdi2          42,504,190   625,141,759   582,637,570   5 Extended
/dev/sdi5          42,504,192   591,587,327   549,083,136  83 Linux
/dev/sdi6         591,589,376   625,141,759    33,552,384  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        F01801E21801A924                       ntfs       SYSTEM
/dev/sda2        1474C5F974C5DD9C                       ntfs
/dev/sda3        1A887F6A887F4375                       ntfs       HP_RECOVERY
/dev/sdb2        6830474930471E06                       ntfs
/dev/sdc1        D24A04154A03F54F                       ntfs
/dev/sdg1        8ba0cf0a-1451-413b-b923-9479b9af44d9   swap
/dev/sdi1        e929268d-4c0c-43d1-ac54-78eac3440eb1   ext4
/dev/sdi5        45c9b484-4087-48ba-8964-1d3e489a6bf7   ext4
/dev/sdi6        28976a4a-260a-4a18-8a0b-45d1e38ce888   swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdi5        /media/45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /live/image              iso9660    (ro,noatime)


============================= sdi5/grub/grub.cfg: ==============================

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
true
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
   insmod part_msdos
   insmod ntfs
   set root='(hd0,msdos1)'
   search --no-floppy --fs-uuid --set=root F01801E21801A924
   chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
   insmod part_msdos
   insmod ntfs
   set root='(hd0,msdos3)'
   search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
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

=========================== sdi5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
if loadfont /usr/share/grub/unicode.pf2 ; then
 set gfxmode=auto
 load_video
 insmod gfxterm
 insmod part_msdos
 insmod ext2
 set root='(hd2,msdos5)'
 search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
 set locale_dir=($root)/boot/grub/locale
 set lang=en_US
 insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
 set timeout=10
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
   set root='(hd2,msdos5)'
   search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
   linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro   quiet splash vt.handoff=7
   initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
   recordfail
   insmod gzio
   insmod part_msdos
   insmod ext2
   set root='(hd2,msdos5)'
   search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
   echo    'Loading Linux 3.0.0-12-generic ...'
   linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro recovery nomodeset
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
   set root='(hd2,msdos5)'
   search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
   linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
   insmod part_msdos
   insmod ext2
   set root='(hd2,msdos5)'
   search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
   linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
   insmod part_msdos
   insmod ntfs
   set root='(hd0,msdos1)'
   search --no-floppy --fs-uuid --set=root F01801E21801A924
   chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
   insmod part_msdos
   insmod ntfs
   set root='(hd0,msdos3)'
   search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
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

=============================== sdi5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdj5 during installation
UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdj6 during installation
UUID=28976a4a-260a-4a18-8a0b-45d1e38ce888 none            swap    sw              0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdi5: Location of files loaded by Grub: ====================

          GiB - GB             File                                 Fragment(s)

           ?? = ??             boot/grub/core.img                             1
           ?? = ??             boot/grub/grub.cfg                             1
           ?? = ??             boot/initrd.img-3.0.0-12-generic               1
           ?? = ??             boot/vmlinuz-3.0.0-12-generic                  1
           ?? = ??             grub/core.img                                  1
           ?? = ??             grub/grub.cfg                                  1
           ?? = ??             initrd.img                                     1
           ?? = ??             vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdi2

00000000  21 fd 74 ce 63 58 17 af  4b d4 a9 f9 19 04 16 c7  |!.t.cX..K.......|
00000010  dc 5d 7c 99 e1 4a a1 09  2c e3 34 0a 46 70 4a 49  |.]|..J..,.4.FpJI|
00000020  92 45 12 c1 28 70 21 0c  14 ed ad 91 21 44 11 cc  |.E..(p!.....!D..|
00000030  e0 60 7d 0d 0d 0b f6 0b  41 55 65 56 c3 c0 93 4d  |.`}.....AUeV...M|
00000040  27 15 0e 64 6d 9f 72 7b  72 aa f6 d5 3f 0d 71 3e  |'..dm.r{r...?.q>|
00000050  68 52 b8 19 48 31 e2 03  72 23 6e 6a 4c a3 7f 88  |hR..H1..r#njL...|
00000060  0b 29 df 77 da 4d b7 88  17 3e d0 85 46 0b 73 b4  |.).w.M...>..F.s.|
00000070  00 8a fc 47 be c3 25 73  dd a7 35 84 f3 5c 86 c3  |...G..%s..5..\..|
00000080  2d f1 b4 b7 03 45 eb 60  82 b3 77 95 cf 52 66 64  |-....E.`..w..Rfd|
00000090  b5 13 54 51 62 4a 51 f0  e8 97 65 5f 5d 75 19 d3  |..TQbJQ...e_]u..|
000000a0  f4 d2 63 b0 8f e5 39 ac  c5 0b 45 a0 d2 f8 f7 d9  |..c...9...E.....|
000000b0  a9 3d a3 2c 5b e8 89 c8  73 d1 3c 4a b9 0a 5b 53  |.=.,[...s.<J..[S|
000000c0  f6 6e ab f7 6b a2 a4 fa  cc 0a 29 36 8c 2d 2a 1c  |.n..k.....)6.-*.|
000000d0  0b aa 38 ac b5 52 cd 2b  89 ae 00 b4 67 61 52 16  |..8..R.+....gaR.|
000000e0  14 ac 62 07 07 d0 d0 d0  bf 60 b4 50 4a 56 c0 2e  |..b......`.PJV..|
000000f0  32 d5 32 e1 bb 62 5e 37  91 4b b8 22 31 cb 0c 43  |2.2..b^7.K."1..C|
00000100  e0 3c b4 96 30 eb e7 af  56 c6 2c f3 fe c0 e2 46  |.<..0...V.,....F|
00000110  0b dd e9 79 63 46 3b fb  a5 ae b3 9d 4c 6d 30 4c  |...ycF;.....Lm0L|
00000120  cd 88 71 c9 81 ca 23 3b  35 b6 2e 7e ad 68 b8 e0  |..q...#;5..~.h..|
00000130  23 6b 62 9c 3b 8b 8e 58  23 dd 58 d5 79 f5 97 22  |#kb.;..X#.X.y.."|
00000140  d3 9f 89 58 f1 c2 92 f2  97 a2 3d d4 d3 f8 e0 e6  |...X......=.....|
00000150  8f d6 9c 8b bc 76 d9 cb  e5 1a bf 7e fd 63 4a 85  |.....v.....~.cJ.|
00000160  54 ba 80 09 df 62 8b 5e  e8 d3 11 55 11 70 21 0c  |T....b.^...U.p!.|
00000170  14 ed ae 0d 25 47 09 54  20 60 7d c5 d9 aa 1f 02  |....%G.T `}.....|
00000180  ee ac c0 87 61 e0 5b 32  ec bd 33 c1 98 47 74 fa  |....a.[2..3..Gt.|
00000190  bb 49 61 94 27 83 f1 0b  3c 0e 64 02 38 59 89 b5  |.Ia.'...<.d.8Y..|
000001a0  1b 71 06 61 3c ad 78 1c  9a c0 5b 3b 20 62 8c c3  |.q.a<.x...[; b..|
000001b0  5a 5e 98 a2 90 c7 d8 35  2f 4b 2d 4d fe 99 00 fe  |Z^.....5/K-M....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 58 ba 20 00 fe  |...........X. ..|
000001d0  ff ff 05 fe ff ff 02 58  ba 20 00 00 00 02 00 00  |.......X. ......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdh

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
File descriptor 7 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
File descriptor 8 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
 No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-03-20__11h56 ****************
boot-repair version : 3.16-0ppa10~lucid
boot-sav version : 3.17-0ppa18~lucid
/usr/share/boot-sav/gui-update.sh: line 31: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
internet: no-internet
internet: no-internet
File descriptor 7 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
File descriptor 8 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
No volume groups found
LIVESESSION is : yes (Debian GNU/Linux 6.0.3 (squeeze) , squeeze , Debian , x86_64  )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[2] (sdc) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[3] (sdb) = 34 sectors * 512 bytes = 17408 bytes.
BYTES_BEFORE_PART[4] (sdi) = 63 sectors * 512 bytes = 32256 bytes.

OSPROBER:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Windows Recovery Environment (loader):Windows1:chain

BLKID:
/dev/sda1: LABEL="SYSTEM" UUID="F01801E21801A924" TYPE="ntfs"
/dev/sda2: UUID="1474C5F974C5DD9C" TYPE="ntfs"
/dev/sda3: LABEL="HP_RECOVERY" UUID="1A887F6A887F4375" TYPE="ntfs"
/dev/sdc1: UUID="D24A04154A03F54F" TYPE="ntfs"
/dev/sdb2: UUID="6830474930471E06" TYPE="ntfs"
/dev/sdi1: UUID="e929268d-4c0c-43d1-ac54-78eac3440eb1" TYPE="ext4"
/dev/sdi5: UUID="45c9b484-4087-48ba-8964-1d3e489a6bf7" TYPE="ext4"
/dev/sdi6: UUID="28976a4a-260a-4a18-8a0b-45d1e38ce888" TYPE="swap"
/dev/sdg1: UUID="8ba0cf0a-1451-413b-b923-9479b9af44d9" TYPE="swap"
/dev/loop0: TYPE="squashfs"

1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 2 OS detected on sda disk.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

LIST_GPTPART[1] is  (sdb1 , sda)
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdc is MSDos
ReadEFI: /dev/sdb , N 128 , 0 ,  , PRStart 1024 , PRSize 128
part /dev/sdb2 is notBISEFI
TABLE_TYPE of sdb is EFI
TABLE_TYPE of sdi is MSDos
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, no-fstab.
sda2 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda2, no-os, no-gpt, notEFItable, no-fstab.
sda3 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda3, with-os, no-gpt, notEFItable, no-fstab.
sdc1 : sdc, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdc1, no-os, no-gpt, notEFItable, no-fstab.
sdb2 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb2, no-os, no-gpt, notBISEFI, no-fstab.
sdi1 : sdi, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdi1, no-os, no-gpt, notEFItable, no-fstab.
sdi5 : sdi, not-sepboot, grub-install, grub2 , update-grub, apt-get, 64, with boot, /mnt/boot-sav/sdi5, with-os, no-gpt, notEFItable, fstab-without-efi.

PARTED:

Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  106MB   105MB   primary  ntfs         boot
2      106MB   987GB   987GB   primary  ntfs
3      987GB   1000GB  13.0GB  primary  ntfs


Model: Hitachi HDS723020BLA642 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
2      135MB   2000GB  2000GB  ntfs         Basic data partition


Model: WDC WD15 EARS-00S8B1 (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1500GB  1500GB  primary  ntfs




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.


Error: /dev/sr0: unrecognised disk label

Model: WDC WD32 00AAJB-00TYA0 (scsi)
Disk /dev/sdi: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  21.8GB  21.8GB  primary   ext4            boot
2      21.8GB  320GB   298GB   extended
5      21.8GB  303GB   281GB   logical   ext4
6      303GB   320GB   17.2GB  logical   linux-swap(v1)


Model: Generic- MS/MS-Pro (scsi)
Disk /dev/sdg: 8064MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
1      13.3kB  8051MB  8051MB  primary  linux-swap(v1)  boot


MOUNT:
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
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdi1 on /mnt/boot-sav/sdi1 type ext4 (rw)
/dev/sdi5 on /mnt/boot-sav/sdi5 type ext4 (rw)


/sys/block/sda:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdg1 size slaves stat subsystem trace uevent
/sys/block/sdh:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdi:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdi1 sdi2 sdi5 sdi6 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  block bsg btrfs-control bus cdrom cdrom1 cdrom2 cdrw cdrw1 cdrw2 char console core cpu_dma_latency disk dvd dvd1 dvd2 dvdrw dvdrw1 dvdrw2 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hpet initctl input kmsg log MAKEDEV mcelog md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 scd1 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdc sdc1 sdd sde sdf sdg sdg1 sdh sdi sdi1 sdi2 sdi5 sdi6 sg0 sg1 sg10 sg2 sg3 sg4 sg5 sg6 sg7 sg8 sg9 shm snapshot snd sndstat sr0 sr1 stderr stdin stdout urandom usb v4l vga_arbiter video0 xconsole zero

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    7.9G  9.5M  7.9G   1% /
tmpfs        tmpfs    7.9G     0  7.9G   0% /lib/init/rw
udev         tmpfs    7.9G  316K  7.9G   1% /dev
tmpfs        tmpfs    7.9G     0  7.9G   0% /dev/shm
/dev/sr0   iso9660    339M  339M     0 100% /live/image
tmpfs        tmpfs    7.9G  9.5M  7.9G   1% /live/cow
tmpfs        tmpfs    7.9G     0  7.9G   0% /live
tmpfs        tmpfs    7.9G  8.0K  7.9G   1% /tmp
/dev/sda1  fuseblk    100M   37M   64M  37% /mnt/boot-sav/sda1
/dev/sda2  fuseblk    920G  344G  576G  38% /mnt/boot-sav/sda2
/dev/sda3  fuseblk     13G   11G  1.5G  88% /mnt/boot-sav/sda3
/dev/sdc1  fuseblk    1.4T  543G  855G  39% /mnt/boot-sav/sdc1
/dev/sdb2  fuseblk    1.9T  275G  1.6T  15% /mnt/boot-sav/sdb2
/dev/sdi1     ext4     20G  172M   19G   1% /mnt/boot-sav/sdi1
/dev/sdi5     ext4    258G  3.2G  242G   2% /mnt/boot-sav/sdi5

FDISK:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x855ed430

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848  1928189951   963991552    7  HPFS/NTFS
/dev/sda3      1928189952  1953521663    12665856    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45df5ea9

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  2930274303  1465136128    7  HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03bf0065

Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *          63    42502314    21251126   83  Linux
/dev/sdi2        42504190   625141759   291318785    5  Extended
/dev/sdi5        42504192   591587327   274541568   83  Linux
/dev/sdi6       591589376   625141759    16776192   82  Linux swap / Solaris

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000629a0

Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *          26    15724799     7862387   82  Linux swap / Solaris
Partition 1 has different physical/logical endings:
phys=(975, 255, 63) logical=(974, 255, 63)



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
bootinfo, nombraction, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION no (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 3)
internet: no-internet
internet: no-internet
```

---

### Post by varunendra on 2012-03-20
Please wrap the entire output code within [noparse]```
..
```[/noparse] tags (make it a habit for all terminal outputs). In its current form, it is very difficult to read and interpret.

To do so, just choose to 'Edit' your above post, then add [noparse]```
 in the beginning of the output, and add 
```[/noparse] at the end of it.

Another way (the usual one that is done during 'creation' of the post) is to go into 'Advanced' editing mode, then select (highlight) the output code part, then click on **#** at the top of the edit box to auto generate those tags around the selected text.

(next time, you can just click on #, then copy-paste the output in-between the generated tags).

Sorry for this no help post, but doing this will help us help you.

---

### Post by jeboza on 2012-03-20
Im not really clear on what you're asking for. i apologize i didn't see during the creation of the post . there were some options for disk correction.so can you give me an example of what you're asking? if i edit this file do you want it to say ```
 at the beginning of each line or just the entire report at the beginning and at the end. 

I'm sorry for the confusion. i can simply bypass utubu for now with the cd i created. long term i really see no point in trying to resolve something that clearly others are having a problem as well. i run mac os and win 7 and i've never experienced an issue that can so severely affect a pc. 

installation should be a snap. much like your live cd. truthfully, I'm interested in trying to resolve this problem and i appreciate the help, but its been 2 days and truthfully I'm no closer to a solution. i found no Advanced editing mode. What i have is simple editor under Ubuntu and no editor i could find under boot repair.

So if you can explain what, 'Please wrap the entire output code within [code]..
``` tags (make it a habit for all terminal outputs). In its current form, it is very difficult to read and interpret.' means?

best regards and appreciative of your help

---

### Post by jeboza on 2012-03-20
```

Boot Info Script 0.60-git [23 Feb 2012]


============================= Boot Info Summary: ===============================

=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
in partition 6 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdb.
=> Windows is installed in the MBR of /dev/sdc.
=> No boot loader is installed in the MBR of /dev/sdg.
=> Grub2 (v1.99) is installed in the MBR of /dev/sdi and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /Boot/BCD

sda2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files: /Windows/System32/winload.exe

sda3: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /boot/bcd

sdb1: __________________________________________________ ________________________

File system:
Boot sector type: -
Boot sector info:
Mounting failed: mount: unknown filesystem type ''

sdb2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:

sdc1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:

sdg1: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

sdi1: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files:

sdi2: __________________________________________________ ________________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sdi5: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 11.10
Boot files: /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab
/grub/core.img /boot/grub/core.img

sdi6: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

============================ Drive/Partition Info: =============================

Drive: sda __________________________________________________ ___________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 * 2,048 206,847 204,800 7 NTFS / exFAT / HPFS
/dev/sda2 206,848 1,928,189,951 1,927,983,104 7 NTFS / exFAT / HPFS
/dev/sda3 1,928,189,952 1,953,521,663 25,331,712 7 NTFS / exFAT / HPFS


Drive: sdb __________________________________________________ ___________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdb1 1 4,294,967,295 4,294,967,295 ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition Start Sector End Sector # of Sectors System
/dev/sdb1 34 262,177 262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2 264,192 3,907,028,991 3,906,764,800 Data partition (Windows/Linux)

Drive: sdc __________________________________________________ ___________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdc1 2,048 2,930,274,303 2,930,272,256 7 NTFS / exFAT / HPFS


Drive: sdg __________________________________________________ ___________________

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdg1 * 26 15,724,799 15,724,774 82 Linux swap / Solaris


Drive: sdi __________________________________________________ ___________________

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdi1 * 63 42,502,314 42,502,252 83 Linux
/dev/sdi2 42,504,190 625,141,759 582,637,570 5 Extended
/dev/sdi5 42,504,192 591,587,327 549,083,136 83 Linux
/dev/sdi6 591,589,376 625,141,759 33,552,384 82 Linux swap / Solaris


"blkid" output: __________________________________________________ ______________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 F01801E21801A924 ntfs SYSTEM
/dev/sda2 1474C5F974C5DD9C ntfs
/dev/sda3 1A887F6A887F4375 ntfs HP_RECOVERY
/dev/sdb2 6830474930471E06 ntfs
/dev/sdc1 D24A04154A03F54F ntfs
/dev/sdg1 8ba0cf0a-1451-413b-b923-9479b9af44d9 swap
/dev/sdi1 e929268d-4c0c-43d1-ac54-78eac3440eb1 ext4
/dev/sdi5 45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4
/dev/sdi6 28976a4a-260a-4a18-8a0b-45d1e38ce888 swap

================================ Mount points: =================================

Device Mount_Point Type Options

/dev/sda1 /media/SYSTEM fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)
/dev/sdi5 /media/45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0 /live/image iso9660 (ro,noatime)


============================= sdi5/grub/grub.cfg: ==============================

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
true
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root F01801E21801A924
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=========================== sdi5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
set timeout=10
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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
echo 'Loading Linux 3.0.0-12-generic ...'
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro recovery nomodeset
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root F01801E21801A924
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdi5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdj5 during installation
UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdj6 during installation
UUID=28976a4a-260a-4a18-8a0b-45d1e38ce888 none swap sw 0 0
/dev/scd1 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
--------------------------------------------------------------------------------

=================== sdi5: Location of files loaded by Grub: ====================

GiB - GB File Fragment(s)

?? = ?? boot/grub/core.img 1
?? = ?? boot/grub/grub.cfg 1
?? = ?? boot/initrd.img-3.0.0-12-generic 1
?? = ?? boot/vmlinuz-3.0.0-12-generic 1
?? = ?? grub/core.img 1
?? = ?? grub/grub.cfg 1
?? = ?? initrd.img 1
?? = ?? vmlinuz 1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdi2

00000000 21 fd 74 ce 63 58 17 af 4b d4 a9 f9 19 04 16 c7 |!.t.cX..K.......|
00000010 dc 5d 7c 99 e1 4a a1 09 2c e3 34 0a 46 70 4a 49 |.]|..J..,.4.FpJI|
00000020 92 45 12 c1 28 70 21 0c 14 ed ad 91 21 44 11 cc |.E..(p!.....!D..|
00000030 e0 60 7d 0d 0d 0b f6 0b 41 55 65 56 c3 c0 93 4d |.`}.....AUeV...M|
00000040 27 15 0e 64 6d 9f 72 7b 72 aa f6 d5 3f 0d 71 3e |'..dm.r{r...?.q>|
00000050 68 52 b8 19 48 31 e2 03 72 23 6e 6a 4c a3 7f 88 |hR..H1..r#njL...|
00000060 0b 29 df 77 da 4d b7 88 17 3e d0 85 46 0b 73 b4 |.).w.M...>..F.s.|
00000070 00 8a fc 47 be c3 25 73 dd a7 35 84 f3 5c 86 c3 |...G..%s..5..\..|
00000080 2d f1 b4 b7 03 45 eb 60 82 b3 77 95 cf 52 66 64 |-....E.`..w..Rfd|
00000090 b5 13 54 51 62 4a 51 f0 e8 97 65 5f 5d 75 19 d3 |..TQbJQ...e_]u..|
000000a0 f4 d2 63 b0 8f e5 39 ac c5 0b 45 a0 d2 f8 f7 d9 |..c...9...E.....|
000000b0 a9 3d a3 2c 5b e8 89 c8 73 d1 3c 4a b9 0a 5b 53 |.=.,[...s.<J..[S|
000000c0 f6 6e ab f7 6b a2 a4 fa cc 0a 29 36 8c 2d 2a 1c |.n..k.....)6.-*.|
000000d0 0b aa 38 ac b5 52 cd 2b 89 ae 00 b4 67 61 52 16 |..8..R.+....gaR.|
000000e0 14 ac 62 07 07 d0 d0 d0 bf 60 b4 50 4a 56 c0 2e |..b......`.PJV..|
000000f0 32 d5 32 e1 bb 62 5e 37 91 4b b8 22 31 cb 0c 43 |2.2..b^7.K."1..C|
00000100 e0 3c b4 96 30 eb e7 af 56 c6 2c f3 fe c0 e2 46 |.<..0...V.,....F|
00000110 0b dd e9 79 63 46 3b fb a5 ae b3 9d 4c 6d 30 4c |...ycF;.....Lm0L|
00000120 cd 88 71 c9 81 ca 23 3b 35 b6 2e 7e ad 68 b8 e0 |..q...#;5..~.h..|
00000130 23 6b 62 9c 3b 8b 8e 58 23 dd 58 d5 79 f5 97 22 |#kb.;..X#.X.y.."|
00000140 d3 9f 89 58 f1 c2 92 f2 97 a2 3d d4 d3 f8 e0 e6 |...X......=.....|
00000150 8f d6 9c 8b bc 76 d9 cb e5 1a bf 7e fd 63 4a 85 |.....v.....~.cJ.|
00000160 54 ba 80 09 df 62 8b 5e e8 d3 11 55 11 70 21 0c |T....b.^...U.p!.|
00000170 14 ed ae 0d 25 47 09 54 20 60 7d c5 d9 aa 1f 02 |....%G.T `}.....|
00000180 ee ac c0 87 61 e0 5b 32 ec bd 33 c1 98 47 74 fa |....a.[2..3..Gt.|
00000190 bb 49 61 94 27 83 f1 0b 3c 0e 64 02 38 59 89 b5 |.Ia.'...<.d.8Y..|
000001a0 1b 71 06 61 3c ad 78 1c 9a c0 5b 3b 20 62 8c c3 |.q.a<.x...[; b..|
000001b0 5a 5e 98 a2 90 c7 d8 35 2f 4b 2d 4d fe 99 00 fe |Z^.....5/K-M....|
000001c0 ff ff 83 fe ff ff 02 00 00 00 00 58 ba 20 00 fe |...........X. ..|
000001d0 ff ff 05 fe ff ff 02 58 ba 20 00 00 00 02 00 00 |.......X. ......|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdh

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
File descriptor 7 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
File descriptor 8 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-03-20__11h56 ****************
boot-repair version : 3.16-0ppa10~lucid
boot-sav version : 3.17-0ppa18~lucid
/usr/share/boot-sav/gui-update.sh: line 31: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
internet: no-internet
internet: no-internet
File descriptor 7 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
File descriptor 8 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
No volume groups found
LIVESESSION is : yes (Debian GNU/Linux 6.0.3 (squeeze) , squeeze , Debian , x86_64 )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[2] (sdc) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[3] (sdb) = 34 sectors * 512 bytes = 17408 bytes.
BYTES_BEFORE_PART[4] (sdi) = 63 sectors * 512 bytes = 32256 bytes.

OSPROBER:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Windows Recovery Environment (loader):Windows1:chain

BLKID:
/dev/sda1: LABEL="SYSTEM" UUID="F01801E21801A924" TYPE="ntfs"
/dev/sda2: UUID="1474C5F974C5DD9C" TYPE="ntfs"
/dev/sda3: LABEL="HP_RECOVERY" UUID="1A887F6A887F4375" TYPE="ntfs"
/dev/sdc1: UUID="D24A04154A03F54F" TYPE="ntfs"
/dev/sdb2: UUID="6830474930471E06" TYPE="ntfs"
/dev/sdi1: UUID="e929268d-4c0c-43d1-ac54-78eac3440eb1" TYPE="ext4"
/dev/sdi5: UUID="45c9b484-4087-48ba-8964-1d3e489a6bf7" TYPE="ext4"
/dev/sdi6: UUID="28976a4a-260a-4a18-8a0b-45d1e38ce888" TYPE="swap"
/dev/sdg1: UUID="8ba0cf0a-1451-413b-b923-9479b9af44d9" TYPE="swap"
/dev/loop0: TYPE="squashfs"

1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 2 OS detected on sda disk.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

LIST_GPTPART[1] is (sdb1 , sda)
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdc is MSDos
ReadEFI: /dev/sdb , N 128 , 0 , , PRStart 1024 , PRSize 128
part /dev/sdb2 is notBISEFI
TABLE_TYPE of sdb is EFI
TABLE_TYPE of sdi is MSDos
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, no-fstab.
sda2 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda2, no-os, no-gpt, notEFItable, no-fstab.
sda3 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda3, with-os, no-gpt, notEFItable, no-fstab.
sdc1 : sdc, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdc1, no-os, no-gpt, notEFItable, no-fstab.
sdb2 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb2, no-os, no-gpt, notBISEFI, no-fstab.
sdi1 : sdi, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdi1, no-os, no-gpt, notEFItable, no-fstab.
sdi5 : sdi, not-sepboot, grub-install, grub2 , update-grub, apt-get, 64, with boot, /mnt/boot-sav/sdi5, with-os, no-gpt, notEFItable, fstab-without-efi.

PARTED:

Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 106MB 105MB primary ntfs boot
2 106MB 987GB 987GB primary ntfs
3 987GB 1000GB 13.0GB primary ntfs


Model: Hitachi HDS723020BLA642 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number Start End Size File system Name Flags
1 17.4kB 134MB 134MB Microsoft reserved partition msftres
2 135MB 2000GB 2000GB ntfs Basic data partition


Model: WDC WD15 EARS-00S8B1 (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 1500GB 1500GB primary ntfs




Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0
has been opened read-only.


Error: /dev/sr0: unrecognised disk label

Model: WDC WD32 00AAJB-00TYA0 (scsi)
Disk /dev/sdi: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 21.8GB 21.8GB primary ext4 boot
2 21.8GB 320GB 298GB extended
5 21.8GB 303GB 281GB logical ext4
6 303GB 320GB 17.2GB logical linux-swap(v1)


Model: Generic- MS/MS-Pro (scsi)
Disk /dev/sdg: 8064MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 13.3kB 8051MB 8051MB primary linux-swap(v1) boot


MOUNT:
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
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdi1 on /mnt/boot-sav/sdi1 type ext4 (rw)
/dev/sdi5 on /mnt/boot-sav/sdi5 type ext4 (rw)


/sys/block/sda: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdg1 size slaves stat subsystem trace uevent
/sys/block/sdh: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdi: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdi1 sdi2 sdi5 sdi6 size slaves stat subsystem trace uevent
/sys/block/sr0: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev: block bsg btrfs-control bus cdrom cdrom1 cdrom2 cdrw cdrw1 cdrw2 char console core cpu_dma_latency disk dvd dvd1 dvd2 dvdrw dvdrw1 dvdrw2 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hpet initctl input kmsg log MAKEDEV mcelog md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 scd1 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdc sdc1 sdd sde sdf sdg sdg1 sdh sdi sdi1 sdi2 sdi5 sdi6 sg0 sg1 sg10 sg2 sg3 sg4 sg5 sg6 sg7 sg8 sg9 shm snapshot snd sndstat sr0 sr1 stderr stdin stdout urandom usb v4l vga_arbiter video0 xconsole zero

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


DF:

Filesystem Type Size Used Avail Use% Mounted on
aufs aufs 7.9G 9.5M 7.9G 1% /
tmpfs tmpfs 7.9G 0 7.9G 0% /lib/init/rw
udev tmpfs 7.9G 316K 7.9G 1% /dev
tmpfs tmpfs 7.9G 0 7.9G 0% /dev/shm
/dev/sr0 iso9660 339M 339M 0 100% /live/image
tmpfs tmpfs 7.9G 9.5M 7.9G 1% /live/cow
tmpfs tmpfs 7.9G 0 7.9G 0% /live
tmpfs tmpfs 7.9G 8.0K 7.9G 1% /tmp
/dev/sda1 fuseblk 100M 37M 64M 37% /mnt/boot-sav/sda1
/dev/sda2 fuseblk 920G 344G 576G 38% /mnt/boot-sav/sda2
/dev/sda3 fuseblk 13G 11G 1.5G 88% /mnt/boot-sav/sda3
/dev/sdc1 fuseblk 1.4T 543G 855G 39% /mnt/boot-sav/sdc1
/dev/sdb2 fuseblk 1.9T 275G 1.6T 15% /mnt/boot-sav/sdb2
/dev/sdi1 ext4 20G 172M 19G 1% /mnt/boot-sav/sdi1
/dev/sdi5 ext4 258G 3.2G 242G 2% /mnt/boot-sav/sdi5

FDISK:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x855ed430

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 206848 1928189951 963991552 7 HPFS/NTFS
/dev/sda3 1928189952 1953521663 12665856 7 HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45df5ea9

Device Boot Start End Blocks Id System
/dev/sdc1 2048 2930274303 1465136128 7 HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 1 4294967295 2147483647+ ee GPT

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03bf0065

Device Boot Start End Blocks Id System
/dev/sdi1 * 63 42502314 21251126 83 Linux
/dev/sdi2 42504190 625141759 291318785 5 Extended
/dev/sdi5 42504192 591587327 274541568 83 Linux
/dev/sdi6 591589376 625141759 16776192 82 Linux swap / Solaris

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000629a0

Device Boot Start End Blocks Id System
/dev/sdg1 * 26 15724799 7862387 82 Linux swap / Solaris
Partition 1 has different physical/logical endings:
phys=(975, 255, 63) logical=(974, 255, 63)



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
bootinfo, nombraction, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION no (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 3)
internet: no-internet
internet: no-internet

```

---

### Post by jeboza on 2012-03-20
```

Boot Info Script 0.60-git [23 Feb 2012]


============================= Boot Info Summary: ===============================

=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
in partition 6 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdb.
=> Windows is installed in the MBR of /dev/sdc.
=> No boot loader is installed in the MBR of /dev/sdg.
=> Grub2 (v1.99) is installed in the MBR of /dev/sdi and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /Boot/BCD

sda2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files: /Windows/System32/winload.exe

sda3: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /boot/bcd

sdb1: __________________________________________________ ________________________

File system:
Boot sector type: -
Boot sector info:
Mounting failed: mount: unknown filesystem type ''

sdb2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:

sdc1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:

sdg1: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

sdi1: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files:

sdi2: __________________________________________________ ________________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sdi5: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 11.10
Boot files: /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab
/grub/core.img /boot/grub/core.img

sdi6: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

============================ Drive/Partition Info: =============================

Drive: sda __________________________________________________ ___________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 * 2,048 206,847 204,800 7 NTFS / exFAT / HPFS
/dev/sda2 206,848 1,928,189,951 1,927,983,104 7 NTFS / exFAT / HPFS
/dev/sda3 1,928,189,952 1,953,521,663 25,331,712 7 NTFS / exFAT / HPFS


Drive: sdb __________________________________________________ ___________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdb1 1 4,294,967,295 4,294,967,295 ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition Start Sector End Sector # of Sectors System
/dev/sdb1 34 262,177 262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2 264,192 3,907,028,991 3,906,764,800 Data partition (Windows/Linux)

Drive: sdc __________________________________________________ ___________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdc1 2,048 2,930,274,303 2,930,272,256 7 NTFS / exFAT / HPFS


Drive: sdg __________________________________________________ ___________________

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdg1 * 26 15,724,799 15,724,774 82 Linux swap / Solaris


Drive: sdi __________________________________________________ ___________________

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdi1 * 63 42,502,314 42,502,252 83 Linux
/dev/sdi2 42,504,190 625,141,759 582,637,570 5 Extended
/dev/sdi5 42,504,192 591,587,327 549,083,136 83 Linux
/dev/sdi6 591,589,376 625,141,759 33,552,384 82 Linux swap / Solaris


"blkid" output: __________________________________________________ ______________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 F01801E21801A924 ntfs SYSTEM
/dev/sda2 1474C5F974C5DD9C ntfs
/dev/sda3 1A887F6A887F4375 ntfs HP_RECOVERY
/dev/sdb2 6830474930471E06 ntfs
/dev/sdc1 D24A04154A03F54F ntfs
/dev/sdg1 8ba0cf0a-1451-413b-b923-9479b9af44d9 swap
/dev/sdi1 e929268d-4c0c-43d1-ac54-78eac3440eb1 ext4
/dev/sdi5 45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4
/dev/sdi6 28976a4a-260a-4a18-8a0b-45d1e38ce888 swap

================================ Mount points: =================================

Device Mount_Point Type Options

/dev/sda1 /media/SYSTEM fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)
/dev/sdi5 /media/45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0 /live/image iso9660 (ro,noatime)


============================= sdi5/grub/grub.cfg: ==============================

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
true
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root F01801E21801A924
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=========================== sdi5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
set timeout=10
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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
echo 'Loading Linux 3.0.0-12-generic ...'
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro recovery nomodeset
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root F01801E21801A924
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdi5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdj5 during installation
UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdj6 during installation
UUID=28976a4a-260a-4a18-8a0b-45d1e38ce888 none swap sw 0 0
/dev/scd1 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
--------------------------------------------------------------------------------

=================== sdi5: Location of files loaded by Grub: ====================

GiB - GB File Fragment(s)

?? = ?? boot/grub/core.img 1
?? = ?? boot/grub/grub.cfg 1
?? = ?? boot/initrd.img-3.0.0-12-generic 1
?? = ?? boot/vmlinuz-3.0.0-12-generic 1
?? = ?? grub/core.img 1
?? = ?? grub/grub.cfg 1
?? = ?? initrd.img 1
?? = ?? vmlinuz 1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdi2

00000000 21 fd 74 ce 63 58 17 af 4b d4 a9 f9 19 04 16 c7 |!.t.cX..K.......|
00000010 dc 5d 7c 99 e1 4a a1 09 2c e3 34 0a 46 70 4a 49 |.]|..J..,.4.FpJI|
00000020 92 45 12 c1 28 70 21 0c 14 ed ad 91 21 44 11 cc |.E..(p!.....!D..|
00000030 e0 60 7d 0d 0d 0b f6 0b 41 55 65 56 c3 c0 93 4d |.`}.....AUeV...M|
00000040 27 15 0e 64 6d 9f 72 7b 72 aa f6 d5 3f 0d 71 3e |'..dm.r{r...?.q>|
00000050 68 52 b8 19 48 31 e2 03 72 23 6e 6a 4c a3 7f 88 |hR..H1..r#njL...|
00000060 0b 29 df 77 da 4d b7 88 17 3e d0 85 46 0b 73 b4 |.).w.M...>..F.s.|
00000070 00 8a fc 47 be c3 25 73 dd a7 35 84 f3 5c 86 c3 |...G..%s..5..\..|
00000080 2d f1 b4 b7 03 45 eb 60 82 b3 77 95 cf 52 66 64 |-....E.`..w..Rfd|
00000090 b5 13 54 51 62 4a 51 f0 e8 97 65 5f 5d 75 19 d3 |..TQbJQ...e_]u..|
000000a0 f4 d2 63 b0 8f e5 39 ac c5 0b 45 a0 d2 f8 f7 d9 |..c...9...E.....|
000000b0 a9 3d a3 2c 5b e8 89 c8 73 d1 3c 4a b9 0a 5b 53 |.=.,[...s.<J..[S|
000000c0 f6 6e ab f7 6b a2 a4 fa cc 0a 29 36 8c 2d 2a 1c |.n..k.....)6.-*.|
000000d0 0b aa 38 ac b5 52 cd 2b 89 ae 00 b4 67 61 52 16 |..8..R.+....gaR.|
000000e0 14 ac 62 07 07 d0 d0 d0 bf 60 b4 50 4a 56 c0 2e |..b......`.PJV..|
000000f0 32 d5 32 e1 bb 62 5e 37 91 4b b8 22 31 cb 0c 43 |2.2..b^7.K."1..C|
00000100 e0 3c b4 96 30 eb e7 af 56 c6 2c f3 fe c0 e2 46 |.<..0...V.,....F|
00000110 0b dd e9 79 63 46 3b fb a5 ae b3 9d 4c 6d 30 4c |...ycF;.....Lm0L|
00000120 cd 88 71 c9 81 ca 23 3b 35 b6 2e 7e ad 68 b8 e0 |..q...#;5..~.h..|
00000130 23 6b 62 9c 3b 8b 8e 58 23 dd 58 d5 79 f5 97 22 |#kb.;..X#.X.y.."|
00000140 d3 9f 89 58 f1 c2 92 f2 97 a2 3d d4 d3 f8 e0 e6 |...X......=.....|
00000150 8f d6 9c 8b bc 76 d9 cb e5 1a bf 7e fd 63 4a 85 |.....v.....~.cJ.|
00000160 54 ba 80 09 df 62 8b 5e e8 d3 11 55 11 70 21 0c |T....b.^...U.p!.|
00000170 14 ed ae 0d 25 47 09 54 20 60 7d c5 d9 aa 1f 02 |....%G.T `}.....|
00000180 ee ac c0 87 61 e0 5b 32 ec bd 33 c1 98 47 74 fa |....a.[2..3..Gt.|
00000190 bb 49 61 94 27 83 f1 0b 3c 0e 64 02 38 59 89 b5 |.Ia.'...<.d.8Y..|
000001a0 1b 71 06 61 3c ad 78 1c 9a c0 5b 3b 20 62 8c c3 |.q.a<.x...[; b..|
000001b0 5a 5e 98 a2 90 c7 d8 35 2f 4b 2d 4d fe 99 00 fe |Z^.....5/K-M....|
000001c0 ff ff 83 fe ff ff 02 00 00 00 00 58 ba 20 00 fe |...........X. ..|
000001d0 ff ff 05 fe ff ff 02 58 ba 20 00 00 00 02 00 00 |.......X. ......|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdh

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
File descriptor 7 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
File descriptor 8 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-03-20__11h56 ****************
boot-repair version : 3.16-0ppa10~lucid
boot-sav version : 3.17-0ppa18~lucid
/usr/share/boot-sav/gui-update.sh: line 31: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
internet: no-internet
internet: no-internet
File descriptor 7 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
File descriptor 8 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
No volume groups found
LIVESESSION is : yes (Debian GNU/Linux 6.0.3 (squeeze) , squeeze , Debian , x86_64 )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[2] (sdc) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[3] (sdb) = 34 sectors * 512 bytes = 17408 bytes.
BYTES_BEFORE_PART[4] (sdi) = 63 sectors * 512 bytes = 32256 bytes.

OSPROBER:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Windows Recovery Environment (loader):Windows1:chain

BLKID:
/dev/sda1: LABEL="SYSTEM" UUID="F01801E21801A924" TYPE="ntfs"
/dev/sda2: UUID="1474C5F974C5DD9C" TYPE="ntfs"
/dev/sda3: LABEL="HP_RECOVERY" UUID="1A887F6A887F4375" TYPE="ntfs"
/dev/sdc1: UUID="D24A04154A03F54F" TYPE="ntfs"
/dev/sdb2: UUID="6830474930471E06" TYPE="ntfs"
/dev/sdi1: UUID="e929268d-4c0c-43d1-ac54-78eac3440eb1" TYPE="ext4"
/dev/sdi5: UUID="45c9b484-4087-48ba-8964-1d3e489a6bf7" TYPE="ext4"
/dev/sdi6: UUID="28976a4a-260a-4a18-8a0b-45d1e38ce888" TYPE="swap"
/dev/sdg1: UUID="8ba0cf0a-1451-413b-b923-9479b9af44d9" TYPE="swap"
/dev/loop0: TYPE="squashfs"

1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 2 OS detected on sda disk.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

LIST_GPTPART[1] is (sdb1 , sda)
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdc is MSDos
ReadEFI: /dev/sdb , N 128 , 0 , , PRStart 1024 , PRSize 128
part /dev/sdb2 is notBISEFI
TABLE_TYPE of sdb is EFI
TABLE_TYPE of sdi is MSDos
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, no-fstab.
sda2 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda2, no-os, no-gpt, notEFItable, no-fstab.
sda3 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda3, with-os, no-gpt, notEFItable, no-fstab.
sdc1 : sdc, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdc1, no-os, no-gpt, notEFItable, no-fstab.
sdb2 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb2, no-os, no-gpt, notBISEFI, no-fstab.
sdi1 : sdi, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdi1, no-os, no-gpt, notEFItable, no-fstab.
sdi5 : sdi, not-sepboot, grub-install, grub2 , update-grub, apt-get, 64, with boot, /mnt/boot-sav/sdi5, with-os, no-gpt, notEFItable, fstab-without-efi.

PARTED:

Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 106MB 105MB primary ntfs boot
2 106MB 987GB 987GB primary ntfs
3 987GB 1000GB 13.0GB primary ntfs


Model: Hitachi HDS723020BLA642 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number Start End Size File system Name Flags
1 17.4kB 134MB 134MB Microsoft reserved partition msftres
2 135MB 2000GB 2000GB ntfs Basic data partition


Model: WDC WD15 EARS-00S8B1 (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 1500GB 1500GB primary ntfs




Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0
has been opened read-only.


Error: /dev/sr0: unrecognised disk label

Model: WDC WD32 00AAJB-00TYA0 (scsi)
Disk /dev/sdi: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 21.8GB 21.8GB primary ext4 boot
2 21.8GB 320GB 298GB extended
5 21.8GB 303GB 281GB logical ext4
6 303GB 320GB 17.2GB logical linux-swap(v1)


Model: Generic- MS/MS-Pro (scsi)
Disk /dev/sdg: 8064MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 13.3kB 8051MB 8051MB primary linux-swap(v1) boot


MOUNT:
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
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdi1 on /mnt/boot-sav/sdi1 type ext4 (rw)
/dev/sdi5 on /mnt/boot-sav/sdi5 type ext4 (rw)


/sys/block/sda: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdg1 size slaves stat subsystem trace uevent
/sys/block/sdh: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdi: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdi1 sdi2 sdi5 sdi6 size slaves stat subsystem trace uevent
/sys/block/sr0: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev: block bsg btrfs-control bus cdrom cdrom1 cdrom2 cdrw cdrw1 cdrw2 char console core cpu_dma_latency disk dvd dvd1 dvd2 dvdrw dvdrw1 dvdrw2 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hpet initctl input kmsg log MAKEDEV mcelog md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 scd1 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdc sdc1 sdd sde sdf sdg sdg1 sdh sdi sdi1 sdi2 sdi5 sdi6 sg0 sg1 sg10 sg2 sg3 sg4 sg5 sg6 sg7 sg8 sg9 shm snapshot snd sndstat sr0 sr1 stderr stdin stdout urandom usb v4l vga_arbiter video0 xconsole zero

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


DF:

Filesystem Type Size Used Avail Use% Mounted on
aufs aufs 7.9G 9.5M 7.9G 1% /
tmpfs tmpfs 7.9G 0 7.9G 0% /lib/init/rw
udev tmpfs 7.9G 316K 7.9G 1% /dev
tmpfs tmpfs 7.9G 0 7.9G 0% /dev/shm
/dev/sr0 iso9660 339M 339M 0 100% /live/image
tmpfs tmpfs 7.9G 9.5M 7.9G 1% /live/cow
tmpfs tmpfs 7.9G 0 7.9G 0% /live
tmpfs tmpfs 7.9G 8.0K 7.9G 1% /tmp
/dev/sda1 fuseblk 100M 37M 64M 37% /mnt/boot-sav/sda1
/dev/sda2 fuseblk 920G 344G 576G 38% /mnt/boot-sav/sda2
/dev/sda3 fuseblk 13G 11G 1.5G 88% /mnt/boot-sav/sda3
/dev/sdc1 fuseblk 1.4T 543G 855G 39% /mnt/boot-sav/sdc1
/dev/sdb2 fuseblk 1.9T 275G 1.6T 15% /mnt/boot-sav/sdb2
/dev/sdi1 ext4 20G 172M 19G 1% /mnt/boot-sav/sdi1
/dev/sdi5 ext4 258G 3.2G 242G 2% /mnt/boot-sav/sdi5

FDISK:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x855ed430

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 206848 1928189951 963991552 7 HPFS/NTFS
/dev/sda3 1928189952 1953521663 12665856 7 HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45df5ea9

Device Boot Start End Blocks Id System
/dev/sdc1 2048 2930274303 1465136128 7 HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 1 4294967295 2147483647+ ee GPT

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03bf0065

Device Boot Start End Blocks Id System
/dev/sdi1 * 63 42502314 21251126 83 Linux
/dev/sdi2 42504190 625141759 291318785 5 Extended
/dev/sdi5 42504192 591587327 274541568 83 Linux
/dev/sdi6 591589376 625141759 16776192 82 Linux swap / Solaris

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000629a0

Device Boot Start End Blocks Id System
/dev/sdg1 * 26 15724799 7862387 82 Linux swap / Solaris
Partition 1 has different physical/logical endings:
phys=(975, 255, 63) logical=(974, 255, 63)



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
bootinfo, nombraction, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION no (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 3)
internet: no-internet
internet: no-internet

```

---

### Post by jeboza on 2012-03-20
I'm so sorry if there is anyway to delete those mistakes up above, I think I got the hang of what you mean. i hope this works and again thanks so much for your patience with me.

```


Boot Info Script 0.60-git [23 Feb 2012]


============================= Boot Info Summary: ===============================

=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
in partition 6 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdb.
=> Windows is installed in the MBR of /dev/sdc.
=> No boot loader is installed in the MBR of /dev/sdg.
=> Grub2 (v1.99) is installed in the MBR of /dev/sdi and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /Boot/BCD

sda2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files: /Windows/System32/winload.exe

sda3: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /boot/bcd

sdb1: __________________________________________________ ________________________

File system:
Boot sector type: -
Boot sector info:
Mounting failed: mount: unknown filesystem type ''

sdb2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:

sdc1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:

sdg1: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

sdi1: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files:

sdi2: __________________________________________________ ________________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sdi5: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 11.10
Boot files: /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab
/grub/core.img /boot/grub/core.img

sdi6: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

============================ Drive/Partition Info: =============================

Drive: sda __________________________________________________ ___________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 * 2,048 206,847 204,800 7 NTFS / exFAT / HPFS
/dev/sda2 206,848 1,928,189,951 1,927,983,104 7 NTFS / exFAT / HPFS
/dev/sda3 1,928,189,952 1,953,521,663 25,331,712 7 NTFS / exFAT / HPFS


Drive: sdb __________________________________________________ ___________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdb1 1 4,294,967,295 4,294,967,295 ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition Start Sector End Sector # of Sectors System
/dev/sdb1 34 262,177 262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2 264,192 3,907,028,991 3,906,764,800 Data partition (Windows/Linux)

Drive: sdc __________________________________________________ ___________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdc1 2,048 2,930,274,303 2,930,272,256 7 NTFS / exFAT / HPFS


Drive: sdg __________________________________________________ ___________________

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdg1 * 26 15,724,799 15,724,774 82 Linux swap / Solaris


Drive: sdi __________________________________________________ ___________________

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdi1 * 63 42,502,314 42,502,252 83 Linux
/dev/sdi2 42,504,190 625,141,759 582,637,570 5 Extended
/dev/sdi5 42,504,192 591,587,327 549,083,136 83 Linux
/dev/sdi6 591,589,376 625,141,759 33,552,384 82 Linux swap / Solaris


"blkid" output: __________________________________________________ ______________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 F01801E21801A924 ntfs SYSTEM
/dev/sda2 1474C5F974C5DD9C ntfs
/dev/sda3 1A887F6A887F4375 ntfs HP_RECOVERY
/dev/sdb2 6830474930471E06 ntfs
/dev/sdc1 D24A04154A03F54F ntfs
/dev/sdg1 8ba0cf0a-1451-413b-b923-9479b9af44d9 swap
/dev/sdi1 e929268d-4c0c-43d1-ac54-78eac3440eb1 ext4
/dev/sdi5 45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4
/dev/sdi6 28976a4a-260a-4a18-8a0b-45d1e38ce888 swap

================================ Mount points: =================================

Device Mount_Point Type Options

/dev/sda1 /media/SYSTEM fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)
/dev/sdi5 /media/45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0 /live/image iso9660 (ro,noatime)


============================= sdi5/grub/grub.cfg: ==============================

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
true
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root F01801E21801A924
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=========================== sdi5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
set timeout=10
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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
echo 'Loading Linux 3.0.0-12-generic ...'
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro recovery nomodeset
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root F01801E21801A924
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdi5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdj5 during installation
UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdj6 during installation
UUID=28976a4a-260a-4a18-8a0b-45d1e38ce888 none swap sw 0 0
/dev/scd1 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
--------------------------------------------------------------------------------

=================== sdi5: Location of files loaded by Grub: ====================

GiB - GB File Fragment(s)

?? = ?? boot/grub/core.img 1
?? = ?? boot/grub/grub.cfg 1
?? = ?? boot/initrd.img-3.0.0-12-generic 1
?? = ?? boot/vmlinuz-3.0.0-12-generic 1
?? = ?? grub/core.img 1
?? = ?? grub/grub.cfg 1
?? = ?? initrd.img 1
?? = ?? vmlinuz 1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdi2

00000000 21 fd 74 ce 63 58 17 af 4b d4 a9 f9 19 04 16 c7 |!.t.cX..K.......|
00000010 dc 5d 7c 99 e1 4a a1 09 2c e3 34 0a 46 70 4a 49 |.]|..J..,.4.FpJI|
00000020 92 45 12 c1 28 70 21 0c 14 ed ad 91 21 44 11 cc |.E..(p!.....!D..|
00000030 e0 60 7d 0d 0d 0b f6 0b 41 55 65 56 c3 c0 93 4d |.`}.....AUeV...M|
00000040 27 15 0e 64 6d 9f 72 7b 72 aa f6 d5 3f 0d 71 3e |'..dm.r{r...?.q>|
00000050 68 52 b8 19 48 31 e2 03 72 23 6e 6a 4c a3 7f 88 |hR..H1..r#njL...|
00000060 0b 29 df 77 da 4d b7 88 17 3e d0 85 46 0b 73 b4 |.).w.M...>..F.s.|
00000070 00 8a fc 47 be c3 25 73 dd a7 35 84 f3 5c 86 c3 |...G..%s..5..\..|
00000080 2d f1 b4 b7 03 45 eb 60 82 b3 77 95 cf 52 66 64 |-....E.`..w..Rfd|
00000090 b5 13 54 51 62 4a 51 f0 e8 97 65 5f 5d 75 19 d3 |..TQbJQ...e_]u..|
000000a0 f4 d2 63 b0 8f e5 39 ac c5 0b 45 a0 d2 f8 f7 d9 |..c...9...E.....|
000000b0 a9 3d a3 2c 5b e8 89 c8 73 d1 3c 4a b9 0a 5b 53 |.=.,[...s.<J..[S|
000000c0 f6 6e ab f7 6b a2 a4 fa cc 0a 29 36 8c 2d 2a 1c |.n..k.....)6.-*.|
000000d0 0b aa 38 ac b5 52 cd 2b 89 ae 00 b4 67 61 52 16 |..8..R.+....gaR.|
000000e0 14 ac 62 07 07 d0 d0 d0 bf 60 b4 50 4a 56 c0 2e |..b......`.PJV..|
000000f0 32 d5 32 e1 bb 62 5e 37 91 4b b8 22 31 cb 0c 43 |2.2..b^7.K."1..C|
00000100 e0 3c b4 96 30 eb e7 af 56 c6 2c f3 fe c0 e2 46 |.<..0...V.,....F|
00000110 0b dd e9 79 63 46 3b fb a5 ae b3 9d 4c 6d 30 4c |...ycF;.....Lm0L|
00000120 cd 88 71 c9 81 ca 23 3b 35 b6 2e 7e ad 68 b8 e0 |..q...#;5..~.h..|
00000130 23 6b 62 9c 3b 8b 8e 58 23 dd 58 d5 79 f5 97 22 |#kb.;..X#.X.y.."|
00000140 d3 9f 89 58 f1 c2 92 f2 97 a2 3d d4 d3 f8 e0 e6 |...X......=.....|
00000150 8f d6 9c 8b bc 76 d9 cb e5 1a bf 7e fd 63 4a 85 |.....v.....~.cJ.|
00000160 54 ba 80 09 df 62 8b 5e e8 d3 11 55 11 70 21 0c |T....b.^...U.p!.|
00000170 14 ed ae 0d 25 47 09 54 20 60 7d c5 d9 aa 1f 02 |....%G.T `}.....|
00000180 ee ac c0 87 61 e0 5b 32 ec bd 33 c1 98 47 74 fa |....a.[2..3..Gt.|
00000190 bb 49 61 94 27 83 f1 0b 3c 0e 64 02 38 59 89 b5 |.Ia.'...<.d.8Y..|
000001a0 1b 71 06 61 3c ad 78 1c 9a c0 5b 3b 20 62 8c c3 |.q.a<.x...[; b..|
000001b0 5a 5e 98 a2 90 c7 d8 35 2f 4b 2d 4d fe 99 00 fe |Z^.....5/K-M....|
000001c0 ff ff 83 fe ff ff 02 00 00 00 00 58 ba 20 00 fe |...........X. ..|
000001d0 ff ff 05 fe ff ff 02 58 ba 20 00 00 00 02 00 00 |.......X. ......|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdh

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
File descriptor 7 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
File descriptor 8 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-03-20__11h56 ****************
boot-repair version : 3.16-0ppa10~lucid
boot-sav version : 3.17-0ppa18~lucid
/usr/share/boot-sav/gui-update.sh: line 31: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
internet: no-internet
internet: no-internet
File descriptor 7 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
File descriptor 8 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
No volume groups found
LIVESESSION is : yes (Debian GNU/Linux 6.0.3 (squeeze) , squeeze , Debian , x86_64 )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[2] (sdc) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[3] (sdb) = 34 sectors * 512 bytes = 17408 bytes.
BYTES_BEFORE_PART[4] (sdi) = 63 sectors * 512 bytes = 32256 bytes.

OSPROBER:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Windows Recovery Environment (loader):Windows1:chain

BLKID:
/dev/sda1: LABEL="SYSTEM" UUID="F01801E21801A924" TYPE="ntfs"
/dev/sda2: UUID="1474C5F974C5DD9C" TYPE="ntfs"
/dev/sda3: LABEL="HP_RECOVERY" UUID="1A887F6A887F4375" TYPE="ntfs"
/dev/sdc1: UUID="D24A04154A03F54F" TYPE="ntfs"
/dev/sdb2: UUID="6830474930471E06" TYPE="ntfs"
/dev/sdi1: UUID="e929268d-4c0c-43d1-ac54-78eac3440eb1" TYPE="ext4"
/dev/sdi5: UUID="45c9b484-4087-48ba-8964-1d3e489a6bf7" TYPE="ext4"
/dev/sdi6: UUID="28976a4a-260a-4a18-8a0b-45d1e38ce888" TYPE="swap"
/dev/sdg1: UUID="8ba0cf0a-1451-413b-b923-9479b9af44d9" TYPE="swap"
/dev/loop0: TYPE="squashfs"

1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 2 OS detected on sda disk.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

LIST_GPTPART[1] is (sdb1 , sda)
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdc is MSDos
ReadEFI: /dev/sdb , N 128 , 0 , , PRStart 1024 , PRSize 128
part /dev/sdb2 is notBISEFI
TABLE_TYPE of sdb is EFI
TABLE_TYPE of sdi is MSDos
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, no-fstab.
sda2 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda2, no-os, no-gpt, notEFItable, no-fstab.
sda3 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda3, with-os, no-gpt, notEFItable, no-fstab.
sdc1 : sdc, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdc1, no-os, no-gpt, notEFItable, no-fstab.
sdb2 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb2, no-os, no-gpt, notBISEFI, no-fstab.
sdi1 : sdi, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdi1, no-os, no-gpt, notEFItable, no-fstab.
sdi5 : sdi, not-sepboot, grub-install, grub2 , update-grub, apt-get, 64, with boot, /mnt/boot-sav/sdi5, with-os, no-gpt, notEFItable, fstab-without-efi.

PARTED:

Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 106MB 105MB primary ntfs boot
2 106MB 987GB 987GB primary ntfs
3 987GB 1000GB 13.0GB primary ntfs


Model: Hitachi HDS723020BLA642 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number Start End Size File system Name Flags
1 17.4kB 134MB 134MB Microsoft reserved partition msftres
2 135MB 2000GB 2000GB ntfs Basic data partition


Model: WDC WD15 EARS-00S8B1 (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 1500GB 1500GB primary ntfs




Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0
has been opened read-only.


Error: /dev/sr0: unrecognised disk label

Model: WDC WD32 00AAJB-00TYA0 (scsi)
Disk /dev/sdi: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 21.8GB 21.8GB primary ext4 boot
2 21.8GB 320GB 298GB extended
5 21.8GB 303GB 281GB logical ext4
6 303GB 320GB 17.2GB logical linux-swap(v1)


Model: Generic- MS/MS-Pro (scsi)
Disk /dev/sdg: 8064MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 13.3kB 8051MB 8051MB primary linux-swap(v1) boot


MOUNT:
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
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdi1 on /mnt/boot-sav/sdi1 type ext4 (rw)
/dev/sdi5 on /mnt/boot-sav/sdi5 type ext4 (rw)


/sys/block/sda: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdg1 size slaves stat subsystem trace uevent
/sys/block/sdh: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdi: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdi1 sdi2 sdi5 sdi6 size slaves stat subsystem trace uevent
/sys/block/sr0: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev: block bsg btrfs-control bus cdrom cdrom1 cdrom2 cdrw cdrw1 cdrw2 char console core cpu_dma_latency disk dvd dvd1 dvd2 dvdrw dvdrw1 dvdrw2 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hpet initctl input kmsg log MAKEDEV mcelog md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 scd1 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdc sdc1 sdd sde sdf sdg sdg1 sdh sdi sdi1 sdi2 sdi5 sdi6 sg0 sg1 sg10 sg2 sg3 sg4 sg5 sg6 sg7 sg8 sg9 shm snapshot snd sndstat sr0 sr1 stderr stdin stdout urandom usb v4l vga_arbiter video0 xconsole zero

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


DF:

Filesystem Type Size Used Avail Use% Mounted on
aufs aufs 7.9G 9.5M 7.9G 1% /
tmpfs tmpfs 7.9G 0 7.9G 0% /lib/init/rw
udev tmpfs 7.9G 316K 7.9G 1% /dev
tmpfs tmpfs 7.9G 0 7.9G 0% /dev/shm
/dev/sr0 iso9660 339M 339M 0 100% /live/image
tmpfs tmpfs 7.9G 9.5M 7.9G 1% /live/cow
tmpfs tmpfs 7.9G 0 7.9G 0% /live
tmpfs tmpfs 7.9G 8.0K 7.9G 1% /tmp
/dev/sda1 fuseblk 100M 37M 64M 37% /mnt/boot-sav/sda1
/dev/sda2 fuseblk 920G 344G 576G 38% /mnt/boot-sav/sda2
/dev/sda3 fuseblk 13G 11G 1.5G 88% /mnt/boot-sav/sda3
/dev/sdc1 fuseblk 1.4T 543G 855G 39% /mnt/boot-sav/sdc1
/dev/sdb2 fuseblk 1.9T 275G 1.6T 15% /mnt/boot-sav/sdb2
/dev/sdi1 ext4 20G 172M 19G 1% /mnt/boot-sav/sdi1
/dev/sdi5 ext4 258G 3.2G 242G 2% /mnt/boot-sav/sdi5

FDISK:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x855ed430

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 206848 1928189951 963991552 7 HPFS/NTFS
/dev/sda3 1928189952 1953521663 12665856 7 HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45df5ea9

Device Boot Start End Blocks Id System
/dev/sdc1 2048 2930274303 1465136128 7 HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 1 4294967295 2147483647+ ee GPT

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03bf0065

Device Boot Start End Blocks Id System
/dev/sdi1 * 63 42502314 21251126 83 Linux
/dev/sdi2 42504190 625141759 291318785 5 Extended
/dev/sdi5 42504192 591587327 274541568 83 Linux
/dev/sdi6 591589376 625141759 16776192 82 Linux swap / Solaris

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000629a0

Device Boot Start End Blocks Id System
/dev/sdg1 * 26 15724799 7862387 82 Linux swap / Solaris
Partition 1 has different physical/logical endings:
phys=(975, 255, 63) logical=(974, 255, 63)



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
bootinfo, nombraction, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION no (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 3)
internet: no-internet
internet: no-internet

```

---

### Post by jeboza on 2012-03-20
```
.Boot Info Script 0.60-git [23 Feb 2012]


============================= Boot Info Summary: ===============================

=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
in partition 6 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdb.
=> Windows is installed in the MBR of /dev/sdc.
=> No boot loader is installed in the MBR of /dev/sdg.
=> Grub2 (v1.99) is installed in the MBR of /dev/sdi and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /Boot/BCD

sda2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files: /Windows/System32/winload.exe

sda3: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /boot/bcd

sdb1: __________________________________________________ ________________________

File system:
Boot sector type: -
Boot sector info:
Mounting failed: mount: unknown filesystem type ''

sdb2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:

sdc1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:

sdg1: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

sdi1: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files:

sdi2: __________________________________________________ ________________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sdi5: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 11.10
Boot files: /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab
/grub/core.img /boot/grub/core.img

sdi6: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

============================ Drive/Partition Info: =============================

Drive: sda __________________________________________________ ___________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 * 2,048 206,847 204,800 7 NTFS / exFAT / HPFS
/dev/sda2 206,848 1,928,189,951 1,927,983,104 7 NTFS / exFAT / HPFS
/dev/sda3 1,928,189,952 1,953,521,663 25,331,712 7 NTFS / exFAT / HPFS


Drive: sdb __________________________________________________ ___________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdb1 1 4,294,967,295 4,294,967,295 ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition Start Sector End Sector # of Sectors System
/dev/sdb1 34 262,177 262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2 264,192 3,907,028,991 3,906,764,800 Data partition (Windows/Linux)

Drive: sdc __________________________________________________ ___________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdc1 2,048 2,930,274,303 2,930,272,256 7 NTFS / exFAT / HPFS


Drive: sdg __________________________________________________ ___________________

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdg1 * 26 15,724,799 15,724,774 82 Linux swap / Solaris


Drive: sdi __________________________________________________ ___________________

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdi1 * 63 42,502,314 42,502,252 83 Linux
/dev/sdi2 42,504,190 625,141,759 582,637,570 5 Extended
/dev/sdi5 42,504,192 591,587,327 549,083,136 83 Linux
/dev/sdi6 591,589,376 625,141,759 33,552,384 82 Linux swap / Solaris


"blkid" output: __________________________________________________ ______________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 F01801E21801A924 ntfs SYSTEM
/dev/sda2 1474C5F974C5DD9C ntfs
/dev/sda3 1A887F6A887F4375 ntfs HP_RECOVERY
/dev/sdb2 6830474930471E06 ntfs
/dev/sdc1 D24A04154A03F54F ntfs
/dev/sdg1 8ba0cf0a-1451-413b-b923-9479b9af44d9 swap
/dev/sdi1 e929268d-4c0c-43d1-ac54-78eac3440eb1 ext4
/dev/sdi5 45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4
/dev/sdi6 28976a4a-260a-4a18-8a0b-45d1e38ce888 swap

================================ Mount points: =================================

Device Mount_Point Type Options

/dev/sda1 /media/SYSTEM fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)
/dev/sdi5 /media/45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0 /live/image iso9660 (ro,noatime)


============================= sdi5/grub/grub.cfg: ==============================

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
true
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root F01801E21801A924
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=========================== sdi5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
set timeout=10
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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
echo 'Loading Linux 3.0.0-12-generic ...'
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro recovery nomodeset
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root F01801E21801A924
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdi5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdj5 during installation
UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdj6 during installation
UUID=28976a4a-260a-4a18-8a0b-45d1e38ce888 none swap sw 0 0
/dev/scd1 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
--------------------------------------------------------------------------------

=================== sdi5: Location of files loaded by Grub: ====================

GiB - GB File Fragment(s)

?? = ?? boot/grub/core.img 1
?? = ?? boot/grub/grub.cfg 1
?? = ?? boot/initrd.img-3.0.0-12-generic 1
?? = ?? boot/vmlinuz-3.0.0-12-generic 1
?? = ?? grub/core.img 1
?? = ?? grub/grub.cfg 1
?? = ?? initrd.img 1
?? = ?? vmlinuz 1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdi2

00000000 21 fd 74 ce 63 58 17 af 4b d4 a9 f9 19 04 16 c7 |!.t.cX..K.......|
00000010 dc 5d 7c 99 e1 4a a1 09 2c e3 34 0a 46 70 4a 49 |.]|..J..,.4.FpJI|
00000020 92 45 12 c1 28 70 21 0c 14 ed ad 91 21 44 11 cc |.E..(p!.....!D..|
00000030 e0 60 7d 0d 0d 0b f6 0b 41 55 65 56 c3 c0 93 4d |.`}.....AUeV...M|
00000040 27 15 0e 64 6d 9f 72 7b 72 aa f6 d5 3f 0d 71 3e |'..dm.r{r...?.q>|
00000050 68 52 b8 19 48 31 e2 03 72 23 6e 6a 4c a3 7f 88 |hR..H1..r#njL...|
00000060 0b 29 df 77 da 4d b7 88 17 3e d0 85 46 0b 73 b4 |.).w.M...>..F.s.|
00000070 00 8a fc 47 be c3 25 73 dd a7 35 84 f3 5c 86 c3 |...G..%s..5..\..|
00000080 2d f1 b4 b7 03 45 eb 60 82 b3 77 95 cf 52 66 64 |-....E.`..w..Rfd|
00000090 b5 13 54 51 62 4a 51 f0 e8 97 65 5f 5d 75 19 d3 |..TQbJQ...e_]u..|
000000a0 f4 d2 63 b0 8f e5 39 ac c5 0b 45 a0 d2 f8 f7 d9 |..c...9...E.....|
000000b0 a9 3d a3 2c 5b e8 89 c8 73 d1 3c 4a b9 0a 5b 53 |.=.,[...s.<J..[S|
000000c0 f6 6e ab f7 6b a2 a4 fa cc 0a 29 36 8c 2d 2a 1c |.n..k.....)6.-*.|
000000d0 0b aa 38 ac b5 52 cd 2b 89 ae 00 b4 67 61 52 16 |..8..R.+....gaR.|
000000e0 14 ac 62 07 07 d0 d0 d0 bf 60 b4 50 4a 56 c0 2e |..b......`.PJV..|
000000f0 32 d5 32 e1 bb 62 5e 37 91 4b b8 22 31 cb 0c 43 |2.2..b^7.K."1..C|
00000100 e0 3c b4 96 30 eb e7 af 56 c6 2c f3 fe c0 e2 46 |.<..0...V.,....F|
00000110 0b dd e9 79 63 46 3b fb a5 ae b3 9d 4c 6d 30 4c |...ycF;.....Lm0L|
00000120 cd 88 71 c9 81 ca 23 3b 35 b6 2e 7e ad 68 b8 e0 |..q...#;5..~.h..|
00000130 23 6b 62 9c 3b 8b 8e 58 23 dd 58 d5 79 f5 97 22 |#kb.;..X#.X.y.."|
00000140 d3 9f 89 58 f1 c2 92 f2 97 a2 3d d4 d3 f8 e0 e6 |...X......=.....|
00000150 8f d6 9c 8b bc 76 d9 cb e5 1a bf 7e fd 63 4a 85 |.....v.....~.cJ.|
00000160 54 ba 80 09 df 62 8b 5e e8 d3 11 55 11 70 21 0c |T....b.^...U.p!.|
00000170 14 ed ae 0d 25 47 09 54 20 60 7d c5 d9 aa 1f 02 |....%G.T `}.....|
00000180 ee ac c0 87 61 e0 5b 32 ec bd 33 c1 98 47 74 fa |....a.[2..3..Gt.|
00000190 bb 49 61 94 27 83 f1 0b 3c 0e 64 02 38 59 89 b5 |.Ia.'...<.d.8Y..|
000001a0 1b 71 06 61 3c ad 78 1c 9a c0 5b 3b 20 62 8c c3 |.q.a<.x...[; b..|
000001b0 5a 5e 98 a2 90 c7 d8 35 2f 4b 2d 4d fe 99 00 fe |Z^.....5/K-M....|
000001c0 ff ff 83 fe ff ff 02 00 00 00 00 58 ba 20 00 fe |...........X. ..|
000001d0 ff ff 05 fe ff ff 02 58 ba 20 00 00 00 02 00 00 |.......X. ......|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdh

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
File descriptor 7 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
File descriptor 8 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-03-20__11h56 ****************
boot-repair version : 3.16-0ppa10~lucid
boot-sav version : 3.17-0ppa18~lucid
/usr/share/boot-sav/gui-update.sh: line 31: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
internet: no-internet
internet: no-internet
File descriptor 7 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
File descriptor 8 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
No volume groups found
LIVESESSION is : yes (Debian GNU/Linux 6.0.3 (squeeze) , squeeze , Debian , x86_64 )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[2] (sdc) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[3] (sdb) = 34 sectors * 512 bytes = 17408 bytes.
BYTES_BEFORE_PART[4] (sdi) = 63 sectors * 512 bytes = 32256 bytes.

OSPROBER:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Windows Recovery Environment (loader):Windows1:chain

BLKID:
/dev/sda1: LABEL="SYSTEM" UUID="F01801E21801A924" TYPE="ntfs"
/dev/sda2: UUID="1474C5F974C5DD9C" TYPE="ntfs"
/dev/sda3: LABEL="HP_RECOVERY" UUID="1A887F6A887F4375" TYPE="ntfs"
/dev/sdc1: UUID="D24A04154A03F54F" TYPE="ntfs"
/dev/sdb2: UUID="6830474930471E06" TYPE="ntfs"
/dev/sdi1: UUID="e929268d-4c0c-43d1-ac54-78eac3440eb1" TYPE="ext4"
/dev/sdi5: UUID="45c9b484-4087-48ba-8964-1d3e489a6bf7" TYPE="ext4"
/dev/sdi6: UUID="28976a4a-260a-4a18-8a0b-45d1e38ce888" TYPE="swap"
/dev/sdg1: UUID="8ba0cf0a-1451-413b-b923-9479b9af44d9" TYPE="swap"
/dev/loop0: TYPE="squashfs"

1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 2 OS detected on sda disk.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

LIST_GPTPART[1] is (sdb1 , sda)
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdc is MSDos
ReadEFI: /dev/sdb , N 128 , 0 , , PRStart 1024 , PRSize 128
part /dev/sdb2 is notBISEFI
TABLE_TYPE of sdb is EFI
TABLE_TYPE of sdi is MSDos
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, no-fstab.
sda2 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda2, no-os, no-gpt, notEFItable, no-fstab.
sda3 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda3, with-os, no-gpt, notEFItable, no-fstab.
sdc1 : sdc, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdc1, no-os, no-gpt, notEFItable, no-fstab.
sdb2 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb2, no-os, no-gpt, notBISEFI, no-fstab.
sdi1 : sdi, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdi1, no-os, no-gpt, notEFItable, no-fstab.
sdi5 : sdi, not-sepboot, grub-install, grub2 , update-grub, apt-get, 64, with boot, /mnt/boot-sav/sdi5, with-os, no-gpt, notEFItable, fstab-without-efi.

PARTED:

Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 106MB 105MB primary ntfs boot
2 106MB 987GB 987GB primary ntfs
3 987GB 1000GB 13.0GB primary ntfs


Model: Hitachi HDS723020BLA642 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number Start End Size File system Name Flags
1 17.4kB 134MB 134MB Microsoft reserved partition msftres
2 135MB 2000GB 2000GB ntfs Basic data partition


Model: WDC WD15 EARS-00S8B1 (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 1500GB 1500GB primary ntfs




Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0
has been opened read-only.


Error: /dev/sr0: unrecognised disk label

Model: WDC WD32 00AAJB-00TYA0 (scsi)
Disk /dev/sdi: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 21.8GB 21.8GB primary ext4 boot
2 21.8GB 320GB 298GB extended
5 21.8GB 303GB 281GB logical ext4
6 303GB 320GB 17.2GB logical linux-swap(v1)


Model: Generic- MS/MS-Pro (scsi)
Disk /dev/sdg: 8064MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 13.3kB 8051MB 8051MB primary linux-swap(v1) boot


MOUNT:
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
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdi1 on /mnt/boot-sav/sdi1 type ext4 (rw)
/dev/sdi5 on /mnt/boot-sav/sdi5 type ext4 (rw)


/sys/block/sda: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdg1 size slaves stat subsystem trace uevent
/sys/block/sdh: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdi: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdi1 sdi2 sdi5 sdi6 size slaves stat subsystem trace uevent
/sys/block/sr0: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev: block bsg btrfs-control bus cdrom cdrom1 cdrom2 cdrw cdrw1 cdrw2 char console core cpu_dma_latency disk dvd dvd1 dvd2 dvdrw dvdrw1 dvdrw2 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hpet initctl input kmsg log MAKEDEV mcelog md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 scd1 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdc sdc1 sdd sde sdf sdg sdg1 sdh sdi sdi1 sdi2 sdi5 sdi6 sg0 sg1 sg10 sg2 sg3 sg4 sg5 sg6 sg7 sg8 sg9 shm snapshot snd sndstat sr0 sr1 stderr stdin stdout urandom usb v4l vga_arbiter video0 xconsole zero

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


DF:

Filesystem Type Size Used Avail Use% Mounted on
aufs aufs 7.9G 9.5M 7.9G 1% /
tmpfs tmpfs 7.9G 0 7.9G 0% /lib/init/rw
udev tmpfs 7.9G 316K 7.9G 1% /dev
tmpfs tmpfs 7.9G 0 7.9G 0% /dev/shm
/dev/sr0 iso9660 339M 339M 0 100% /live/image
tmpfs tmpfs 7.9G 9.5M 7.9G 1% /live/cow
tmpfs tmpfs 7.9G 0 7.9G 0% /live
tmpfs tmpfs 7.9G 8.0K 7.9G 1% /tmp
/dev/sda1 fuseblk 100M 37M 64M 37% /mnt/boot-sav/sda1
/dev/sda2 fuseblk 920G 344G 576G 38% /mnt/boot-sav/sda2
/dev/sda3 fuseblk 13G 11G 1.5G 88% /mnt/boot-sav/sda3
/dev/sdc1 fuseblk 1.4T 543G 855G 39% /mnt/boot-sav/sdc1
/dev/sdb2 fuseblk 1.9T 275G 1.6T 15% /mnt/boot-sav/sdb2
/dev/sdi1 ext4 20G 172M 19G 1% /mnt/boot-sav/sdi1
/dev/sdi5 ext4 258G 3.2G 242G 2% /mnt/boot-sav/sdi5

FDISK:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x855ed430

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 206848 1928189951 963991552 7 HPFS/NTFS
/dev/sda3 1928189952 1953521663 12665856 7 HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45df5ea9

Device Boot Start End Blocks Id System
/dev/sdc1 2048 2930274303 1465136128 7 HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 1 4294967295 2147483647+ ee GPT

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03bf0065

Device Boot Start End Blocks Id System
/dev/sdi1 * 63 42502314 21251126 83 Linux
/dev/sdi2 42504190 625141759 291318785 5 Extended
/dev/sdi5 42504192 591587327 274541568 83 Linux
/dev/sdi6 591589376 625141759 16776192 82 Linux swap / Solaris

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000629a0

Device Boot Start End Blocks Id System
/dev/sdg1 * 26 15724799 7862387 82 Linux swap / Solaris
Partition 1 has different physical/logical endings:
phys=(975, 255, 63) logical=(974, 255, 63)



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
bootinfo, nombraction, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION no (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 3)
internet: no-internet
internet: no-internet

```
    	      
 1 Minute Ago	   #16
jeboza
Spilled the Beans

 
Join Date: Mar 2012
Beans: 12
Re: grub rescue
I'm so sorry if there is anyway to delete those mistakes up above, I think I got the hang of what you mean. i hope this works and again thanks so much for your patience with me.

```


Boot Info Script 0.60-git [23 Feb 2012]


============================= Boot Info Summary: ===============================

=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
in partition 6 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdb.
=> Windows is installed in the MBR of /dev/sdc.
=> No boot loader is installed in the MBR of /dev/sdg.
=> Grub2 (v1.99) is installed in the MBR of /dev/sdi and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /Boot/BCD

sda2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files: /Windows/System32/winload.exe

sda3: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /boot/bcd

sdb1: __________________________________________________ ________________________

File system:
Boot sector type: -
Boot sector info:
Mounting failed: mount: unknown filesystem type ''

sdb2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:

sdc1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:

sdg1: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

sdi1: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files:

sdi2: __________________________________________________ ________________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sdi5: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 11.10
Boot files: /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab
/grub/core.img /boot/grub/core.img

sdi6: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

============================ Drive/Partition Info: =============================

Drive: sda __________________________________________________ ___________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 * 2,048 206,847 204,800 7 NTFS / exFAT / HPFS
/dev/sda2 206,848 1,928,189,951 1,927,983,104 7 NTFS / exFAT / HPFS
/dev/sda3 1,928,189,952 1,953,521,663 25,331,712 7 NTFS / exFAT / HPFS


Drive: sdb __________________________________________________ ___________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdb1 1 4,294,967,295 4,294,967,295 ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition Start Sector End Sector # of Sectors System
/dev/sdb1 34 262,177 262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2 264,192 3,907,028,991 3,906,764,800 Data partition (Windows/Linux)

Drive: sdc __________________________________________________ ___________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdc1 2,048 2,930,274,303 2,930,272,256 7 NTFS / exFAT / HPFS


Drive: sdg __________________________________________________ ___________________

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdg1 * 26 15,724,799 15,724,774 82 Linux swap / Solaris


Drive: sdi __________________________________________________ ___________________

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdi1 * 63 42,502,314 42,502,252 83 Linux
/dev/sdi2 42,504,190 625,141,759 582,637,570 5 Extended
/dev/sdi5 42,504,192 591,587,327 549,083,136 83 Linux
/dev/sdi6 591,589,376 625,141,759 33,552,384 82 Linux swap / Solaris


"blkid" output: __________________________________________________ ______________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 F01801E21801A924 ntfs SYSTEM
/dev/sda2 1474C5F974C5DD9C ntfs
/dev/sda3 1A887F6A887F4375 ntfs HP_RECOVERY
/dev/sdb2 6830474930471E06 ntfs
/dev/sdc1 D24A04154A03F54F ntfs
/dev/sdg1 8ba0cf0a-1451-413b-b923-9479b9af44d9 swap
/dev/sdi1 e929268d-4c0c-43d1-ac54-78eac3440eb1 ext4
/dev/sdi5 45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4
/dev/sdi6 28976a4a-260a-4a18-8a0b-45d1e38ce888 swap

================================ Mount points: =================================

Device Mount_Point Type Options

/dev/sda1 /media/SYSTEM fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)
/dev/sdi5 /media/45c9b484-4087-48ba-8964-1d3e489a6bf7 ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0 /live/image iso9660 (ro,noatime)


============================= sdi5/grub/grub.cfg: ==============================

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
true
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root F01801E21801A924
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=========================== sdi5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
set timeout=10
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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
echo 'Loading Linux 3.0.0-12-generic ...'
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 ro recovery nomodeset
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 45c9b484-4087-48ba-8964-1d3e489a6bf7
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root F01801E21801A924
chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 1A887F6A887F4375
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdi5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdj5 during installation
UUID=45c9b484-4087-48ba-8964-1d3e489a6bf7 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdj6 during installation
UUID=28976a4a-260a-4a18-8a0b-45d1e38ce888 none swap sw 0 0
/dev/scd1 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
--------------------------------------------------------------------------------

=================== sdi5: Location of files loaded by Grub: ====================

GiB - GB File Fragment(s)

?? = ?? boot/grub/core.img 1
?? = ?? boot/grub/grub.cfg 1
?? = ?? boot/initrd.img-3.0.0-12-generic 1
?? = ?? boot/vmlinuz-3.0.0-12-generic 1
?? = ?? grub/core.img 1
?? = ?? grub/grub.cfg 1
?? = ?? initrd.img 1
?? = ?? vmlinuz 1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdi2

00000000 21 fd 74 ce 63 58 17 af 4b d4 a9 f9 19 04 16 c7 |!.t.cX..K.......|
00000010 dc 5d 7c 99 e1 4a a1 09 2c e3 34 0a 46 70 4a 49 |.]|..J..,.4.FpJI|
00000020 92 45 12 c1 28 70 21 0c 14 ed ad 91 21 44 11 cc |.E..(p!.....!D..|
00000030 e0 60 7d 0d 0d 0b f6 0b 41 55 65 56 c3 c0 93 4d |.`}.....AUeV...M|
00000040 27 15 0e 64 6d 9f 72 7b 72 aa f6 d5 3f 0d 71 3e |'..dm.r{r...?.q>|
00000050 68 52 b8 19 48 31 e2 03 72 23 6e 6a 4c a3 7f 88 |hR..H1..r#njL...|
00000060 0b 29 df 77 da 4d b7 88 17 3e d0 85 46 0b 73 b4 |.).w.M...>..F.s.|
00000070 00 8a fc 47 be c3 25 73 dd a7 35 84 f3 5c 86 c3 |...G..%s..5..\..|
00000080 2d f1 b4 b7 03 45 eb 60 82 b3 77 95 cf 52 66 64 |-....E.`..w..Rfd|
00000090 b5 13 54 51 62 4a 51 f0 e8 97 65 5f 5d 75 19 d3 |..TQbJQ...e_]u..|
000000a0 f4 d2 63 b0 8f e5 39 ac c5 0b 45 a0 d2 f8 f7 d9 |..c...9...E.....|
000000b0 a9 3d a3 2c 5b e8 89 c8 73 d1 3c 4a b9 0a 5b 53 |.=.,[...s.<J..[S|
000000c0 f6 6e ab f7 6b a2 a4 fa cc 0a 29 36 8c 2d 2a 1c |.n..k.....)6.-*.|
000000d0 0b aa 38 ac b5 52 cd 2b 89 ae 00 b4 67 61 52 16 |..8..R.+....gaR.|
000000e0 14 ac 62 07 07 d0 d0 d0 bf 60 b4 50 4a 56 c0 2e |..b......`.PJV..|
000000f0 32 d5 32 e1 bb 62 5e 37 91 4b b8 22 31 cb 0c 43 |2.2..b^7.K."1..C|
00000100 e0 3c b4 96 30 eb e7 af 56 c6 2c f3 fe c0 e2 46 |.<..0...V.,....F|
00000110 0b dd e9 79 63 46 3b fb a5 ae b3 9d 4c 6d 30 4c |...ycF;.....Lm0L|
00000120 cd 88 71 c9 81 ca 23 3b 35 b6 2e 7e ad 68 b8 e0 |..q...#;5..~.h..|
00000130 23 6b 62 9c 3b 8b 8e 58 23 dd 58 d5 79 f5 97 22 |#kb.;..X#.X.y.."|
00000140 d3 9f 89 58 f1 c2 92 f2 97 a2 3d d4 d3 f8 e0 e6 |...X......=.....|
00000150 8f d6 9c 8b bc 76 d9 cb e5 1a bf 7e fd 63 4a 85 |.....v.....~.cJ.|
00000160 54 ba 80 09 df 62 8b 5e e8 d3 11 55 11 70 21 0c |T....b.^...U.p!.|
00000170 14 ed ae 0d 25 47 09 54 20 60 7d c5 d9 aa 1f 02 |....%G.T `}.....|
00000180 ee ac c0 87 61 e0 5b 32 ec bd 33 c1 98 47 74 fa |....a.[2..3..Gt.|
00000190 bb 49 61 94 27 83 f1 0b 3c 0e 64 02 38 59 89 b5 |.Ia.'...<.d.8Y..|
000001a0 1b 71 06 61 3c ad 78 1c 9a c0 5b 3b 20 62 8c c3 |.q.a<.x...[; b..|
000001b0 5a 5e 98 a2 90 c7 d8 35 2f 4b 2d 4d fe 99 00 fe |Z^.....5/K-M....|
000001c0 ff ff 83 fe ff ff 02 00 00 00 00 58 ba 20 00 fe |...........X. ..|
000001d0 ff ff 05 fe ff ff 02 58 ba 20 00 00 00 02 00 00 |.......X. ......|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdh

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
File descriptor 7 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
File descriptor 8 (pipe:[7373]) leaked on lvscan invocation. Parent PID 14297: bash
No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-03-20__11h56 ****************
boot-repair version : 3.16-0ppa10~lucid
boot-sav version : 3.17-0ppa18~lucid
/usr/share/boot-sav/gui-update.sh: line 31: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
internet: no-internet
internet: no-internet
File descriptor 7 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
File descriptor 8 (pipe:[7373]) leaked on lvs invocation. Parent PID 4100: /bin/sh
No volume groups found
LIVESESSION is : yes (Debian GNU/Linux 6.0.3 (squeeze) , squeeze , Debian , x86_64 )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[2] (sdc) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[3] (sdb) = 34 sectors * 512 bytes = 17408 bytes.
BYTES_BEFORE_PART[4] (sdi) = 63 sectors * 512 bytes = 32256 bytes.

OSPROBER:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Windows Recovery Environment (loader):Windows1:chain

BLKID:
/dev/sda1: LABEL="SYSTEM" UUID="F01801E21801A924" TYPE="ntfs"
/dev/sda2: UUID="1474C5F974C5DD9C" TYPE="ntfs"
/dev/sda3: LABEL="HP_RECOVERY" UUID="1A887F6A887F4375" TYPE="ntfs"
/dev/sdc1: UUID="D24A04154A03F54F" TYPE="ntfs"
/dev/sdb2: UUID="6830474930471E06" TYPE="ntfs"
/dev/sdi1: UUID="e929268d-4c0c-43d1-ac54-78eac3440eb1" TYPE="ext4"
/dev/sdi5: UUID="45c9b484-4087-48ba-8964-1d3e489a6bf7" TYPE="ext4"
/dev/sdi6: UUID="28976a4a-260a-4a18-8a0b-45d1e38ce888" TYPE="swap"
/dev/sdg1: UUID="8ba0cf0a-1451-413b-b923-9479b9af44d9" TYPE="swap"
/dev/loop0: TYPE="squashfs"

1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 2 OS detected on sda disk.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

LIST_GPTPART[1] is (sdb1 , sda)
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdc is MSDos
ReadEFI: /dev/sdb , N 128 , 0 , , PRStart 1024 , PRSize 128
part /dev/sdb2 is notBISEFI
TABLE_TYPE of sdb is EFI
TABLE_TYPE of sdi is MSDos
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, no-fstab.
sda2 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda2, no-os, no-gpt, notEFItable, no-fstab.
sda3 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda3, with-os, no-gpt, notEFItable, no-fstab.
sdc1 : sdc, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdc1, no-os, no-gpt, notEFItable, no-fstab.
sdb2 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb2, no-os, no-gpt, notBISEFI, no-fstab.
sdi1 : sdi, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdi1, no-os, no-gpt, notEFItable, no-fstab.
sdi5 : sdi, not-sepboot, grub-install, grub2 , update-grub, apt-get, 64, with boot, /mnt/boot-sav/sdi5, with-os, no-gpt, notEFItable, fstab-without-efi.

PARTED:

Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 106MB 105MB primary ntfs boot
2 106MB 987GB 987GB primary ntfs
3 987GB 1000GB 13.0GB primary ntfs


Model: Hitachi HDS723020BLA642 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number Start End Size File system Name Flags
1 17.4kB 134MB 134MB Microsoft reserved partition msftres
2 135MB 2000GB 2000GB ntfs Basic data partition


Model: WDC WD15 EARS-00S8B1 (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 1500GB 1500GB primary ntfs




Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0
has been opened read-only.


Error: /dev/sr0: unrecognised disk label

Model: WDC WD32 00AAJB-00TYA0 (scsi)
Disk /dev/sdi: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 21.8GB 21.8GB primary ext4 boot
2 21.8GB 320GB 298GB extended
5 21.8GB 303GB 281GB logical ext4
6 303GB 320GB 17.2GB logical linux-swap(v1)


Model: Generic- MS/MS-Pro (scsi)
Disk /dev/sdg: 8064MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 13.3kB 8051MB 8051MB primary linux-swap(v1) boot


MOUNT:
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
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdi1 on /mnt/boot-sav/sdi1 type ext4 (rw)
/dev/sdi5 on /mnt/boot-sav/sdi5 type ext4 (rw)


/sys/block/sda: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdg1 size slaves stat subsystem trace uevent
/sys/block/sdh: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdi: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdi1 sdi2 sdi5 sdi6 size slaves stat subsystem trace uevent
/sys/block/sr0: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1: alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev: block bsg btrfs-control bus cdrom cdrom1 cdrom2 cdrw cdrw1 cdrw2 char console core cpu_dma_latency disk dvd dvd1 dvd2 dvdrw dvdrw1 dvdrw2 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hpet initctl input kmsg log MAKEDEV mcelog md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 scd1 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdc sdc1 sdd sde sdf sdg sdg1 sdh sdi sdi1 sdi2 sdi5 sdi6 sg0 sg1 sg10 sg2 sg3 sg4 sg5 sg6 sg7 sg8 sg9 shm snapshot snd sndstat sr0 sr1 stderr stdin stdout urandom usb v4l vga_arbiter video0 xconsole zero

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


DF:

Filesystem Type Size Used Avail Use% Mounted on
aufs aufs 7.9G 9.5M 7.9G 1% /
tmpfs tmpfs 7.9G 0 7.9G 0% /lib/init/rw
udev tmpfs 7.9G 316K 7.9G 1% /dev
tmpfs tmpfs 7.9G 0 7.9G 0% /dev/shm
/dev/sr0 iso9660 339M 339M 0 100% /live/image
tmpfs tmpfs 7.9G 9.5M 7.9G 1% /live/cow
tmpfs tmpfs 7.9G 0 7.9G 0% /live
tmpfs tmpfs 7.9G 8.0K 7.9G 1% /tmp
/dev/sda1 fuseblk 100M 37M 64M 37% /mnt/boot-sav/sda1
/dev/sda2 fuseblk 920G 344G 576G 38% /mnt/boot-sav/sda2
/dev/sda3 fuseblk 13G 11G 1.5G 88% /mnt/boot-sav/sda3
/dev/sdc1 fuseblk 1.4T 543G 855G 39% /mnt/boot-sav/sdc1
/dev/sdb2 fuseblk 1.9T 275G 1.6T 15% /mnt/boot-sav/sdb2
/dev/sdi1 ext4 20G 172M 19G 1% /mnt/boot-sav/sdi1
/dev/sdi5 ext4 258G 3.2G 242G 2% /mnt/boot-sav/sdi5

FDISK:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x855ed430

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 206848 1928189951 963991552 7 HPFS/NTFS
/dev/sda3 1928189952 1953521663 12665856 7 HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45df5ea9

Device Boot Start End Blocks Id System
/dev/sdc1 2048 2930274303 1465136128 7 HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 1 4294967295 2147483647+ ee GPT

Disk /dev/sdi: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03bf0065

Device Boot Start End Blocks Id System
/dev/sdi1 * 63 42502314 21251126 83 Linux
/dev/sdi2 42504190 625141759 291318785 5 Extended
/dev/sdi5 42504192 591587327 274541568 83 Linux
/dev/sdi6 591589376 625141759 16776192 82 Linux swap / Solaris

Disk /dev/sdg: 8063 MB, 8063549440 bytes
256 heads, 63 sectors/track, 976 cylinders, total 15749120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000629a0

Device Boot Start End Blocks Id System
/dev/sdg1 * 26 15724799 7862387 82 Linux swap / Solaris
Partition 1 has different physical/logical endings:
phys=(975, 255, 63) logical=(974, 255, 63)



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
bootinfo, nombraction, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION no (10s), noflag (sda3)
PART_TO_REINSTALL_GRUB sdi5, PART_TO_REINSTALL_GRUB_PURGE sdi5, FORCE_GRUB all (sdi) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdi1) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 3)
internet: no-internet
internet: no-internet
```

---

### Post by varunendra on 2012-03-21
> **jeboza said:**
> Im not really clear on what you're asking for......
Oh no, you have 'Hugely' misunderstood :)

But now that *overdrank* has done it for you, you can probably understand what I meant. _It was your post here_ that you needed to edit to make it clear and readable. The advance editing mode is the button ("Go Advance") that appears at the bottom right corner of your post if you choose to edit it. Anyway, I think I would sometime create a whole thread or some wiki page with screenshots for stuff like this.

I think I should apologize for not being clear enough despite creating a full post for it.

Onto your problem now.

The error you posted in your first post > error no such device: f51161c1-9230-4a9d-bc0c-cfc0b97769bc, grub rescue> is appearing because you really don't have any partition with that address. So grub can't find the files to boot.

However, everything seems 'workable' on your 320GB disk. If you can bring up the boot-device selection menu of the BIOS, try selecting the 320GB disk to boot from (usually the menu is brought up pressing any of the F9 to F12 keys while the computer is starting. It should be mentioned somewhere in the first BIOS screen).

Please try that and post back the result.

---

### Post by jeboza on 2012-03-21
I changed the BIOS so that it would boot from the 320gb drive. initially appeared to do something. At the end i got just this message 'error: file not found. 
grub rescue>

Again thanks for the help. i now understand overdrank. thanks, i think we're closer. 

Any help would be greatly appreciated and i do see the Go Advanced.

---

### Post by varunendra on 2012-03-21
As an experiment, disconnect all other drives and boot the computer with only the 320GB one connected. If even that fails, we may have to reinstall grub using the same cd that you used to install Ubuntu on that drive.

---

### Post by jeboza on 2012-03-21
I reinstalled the Ubuntu OS onto the the 320gb hard drive. I made sure that the bios pointed to that drive and as far as i can determine I'm up and running. Windows 7 is booting great and Ubuntu looks awesome. 

Thanks for the excellent support. have a great day.

---

