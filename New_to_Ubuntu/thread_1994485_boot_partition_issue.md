---
title: "boot partition issue"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by jagdefalke on 2012-06-02
I've got this Aspire One d270, with the windows 7 starter on one half and 10.04 on the other half working just fine for awhile... until the other day I was running the win7 side and a "critical update" crashed it..   twice.    My husband (whose more comfortable with windows) got it restored and replaced with a premium win7, but now it only boots directly into that OS now.   The partitions seem to still be in place and healthy, so since i already had 12.04 on a thumb drive to play with, I booted with it to check out Drive Utility and it says that the Ext. that 10.04 is on is misaligned by 1024 kb and needs to be repartitioned.   "Repartitioning" is new to me, I don't want to dive into that and screw something up.     If all else fails, I'd only lose a few settings and browser bookmarks if I have to re install, in which case I may just install 12.04.  But if fixing this is simple I'd rather just repair what I have.
Any ideas?

---

### Post by NikTh on 2012-06-02
> **jagdefalke said:**
> , I don't want to dive into that and screw something up.     If all else fails, I'd only lose a few settings and browser bookmarks if I have to re install, in which case I may just install 12.04.  But if fixing this is simple I'd rather just repair what I have.
Any ideas?

Hi , 
you will not screw anything. Here it is an automated tool for restoring grub bootloader and after you will be able to boot in your favorite OS again. 
Boot from a LiveCD of Ubuntu (i hope you have one , if not you can download and create one even from windows) after boot click "Try Ubuntu" and then open a terminal , copy-paste this command 

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```Take a look at this documentation for more info about this Excellent (IMO) program 
[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

I think after that , you can mark this thread as solved.. (thread tools) :D
Of course IF boot-repair fix your problem.

---

### Post by jagdefalke on 2012-06-02
Thankyou, I'll try that!   Does it matter that it's 10.04 that's on the HD and 12.04 liveCD on a thumb drive that I have to use?   I somehow lost my 10.04 liveCD and would have to re download and make another one.... :(

---

### Post by jtarin on 2012-06-02
> **jagdefalke said:**
> Thankyou, I'll try that!   Does it matter that it's 10.04 that's on the HD and 12.04 liveCD on a thumb drive that I have to use?   I somehow lost my 10.04 liveCD and would have to re download and make another one.... :(
No it doesn't.....you only need the ability to download and run "Boot-Repair".

---

### Post by NikTh on 2012-06-02
> **jagdefalke said:**
>    Does it matter that it's 10.04 that's on the HD and 12.04 liveCD on a thumb drive that I have to use?

No , i don't think it matters. 
Try it.. and you will figure it out for sure.;)

---

### Post by jagdefalke on 2012-06-02
Ok, so I tried and it says I have to run it in a 64bit session and then aborted the operation.   Does that mean I have to use a CD?   I'm trying to download the CD on my desktop right now but for some reason it's downloading extra slow..  around 25kb/sec.


... it's just a little netbook, I thought it was a 32 bit...??

---

### Post by jagdefalke on 2012-06-02
I went ahead and ran the BootInfo summary:

```
                Boot Info Script 0.61-git      [12 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:  Syslinux looks at sector 1026702 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 80.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,265,024    27,469,823       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          27,469,824   335,386,623   307,916,800   7 NTFS / exFAT / HPFS
/dev/sda4         335,388,670   625,139,711   289,751,042   f W95 Extended (LBA)
/dev/sda5         335,388,672   560,668,671   225,280,000  83 Linux
/dev/sda6         560,670,720   611,870,719    51,200,000  83 Linux
/dev/sda7         611,872,768   625,139,711    13,266,944  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             80    15,663,103    15,663,024   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        E4F8C06FF8C04212                       ntfs       PQSERVICE
/dev/sda2        125CC1BA5CC198BD                       ntfs       SYSTEM RESERVED
/dev/sda3        CE9AC4779AC45E19                       ntfs       Acer
/dev/sda5        59dca341-da32-4147-96f7-cfcb95b60bcf   ext4       
/dev/sda6        324fc8a2-5ac7-4838-92bd-5a123e590f8a   ext4       
/dev/sda7        84e85a0b-cbdb-4fe1-8b88-7346a58a22e4   swap       
/dev/sdb1        496F-1FCF                              vfat       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 324fc8a2-5ac7-4838-92bd-5a123e590f8a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 324fc8a2-5ac7-4838-92bd-5a123e590f8a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-41-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 324fc8a2-5ac7-4838-92bd-5a123e590f8a
    linux    /boot/vmlinuz-2.6.32-41-generic root=UUID=324fc8a2-5ac7-4838-92bd-5a123e590f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 324fc8a2-5ac7-4838-92bd-5a123e590f8a
    echo    'Loading Linux 2.6.32-41-generic ...'
    linux    /boot/vmlinuz-2.6.32-41-generic root=UUID=324fc8a2-5ac7-4838-92bd-5a123e590f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-40-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 324fc8a2-5ac7-4838-92bd-5a123e590f8a
    linux    /boot/vmlinuz-2.6.32-40-generic root=UUID=324fc8a2-5ac7-4838-92bd-5a123e590f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-40-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 324fc8a2-5ac7-4838-92bd-5a123e590f8a
    echo    'Loading Linux 2.6.32-40-generic ...'
    linux    /boot/vmlinuz-2.6.32-40-generic root=UUID=324fc8a2-5ac7-4838-92bd-5a123e590f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-40-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 324fc8a2-5ac7-4838-92bd-5a123e590f8a
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=324fc8a2-5ac7-4838-92bd-5a123e590f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 324fc8a2-5ac7-4838-92bd-5a123e590f8a
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=324fc8a2-5ac7-4838-92bd-5a123e590f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 324fc8a2-5ac7-4838-92bd-5a123e590f8a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 324fc8a2-5ac7-4838-92bd-5a123e590f8a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set E4F8C06FF8C04212
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 125CC1BA5CC198BD
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=324fc8a2-5ac7-4838-92bd-5a123e590f8a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=59dca341-da32-4147-96f7-cfcb95b60bcf /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=84e85a0b-cbdb-4fe1-8b88-7346a58a22e4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 277.568344116 = 298.036740096  boot/grub/core.img                             1
 269.808078766 = 289.704218624  boot/grub/grub.cfg                             1
 277.738796234 = 298.219761664  boot/initrd.img-2.6.32-28-generic              1
 277.878864288 = 298.370158592  boot/initrd.img-2.6.32-40-generic              1
 277.931133270 = 298.426281984  boot/initrd.img-2.6.32-41-generic              1
 277.729969025 = 298.210283520  boot/vmlinuz-2.6.32-28-generic                 1
 277.752796173 = 298.234793984  boot/vmlinuz-2.6.32-40-generic                 1
 277.869609833 = 298.360221696  boot/vmlinuz-2.6.32-41-generic                 1
 277.931133270 = 298.426281984  initrd.img                                     1
 277.878864288 = 298.370158592  initrd.img.old                                 1
 277.869609833 = 298.360221696  vmlinuz                                        1
 277.752796173 = 298.234793984  vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
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

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-06-03__02h08 ===================
boot-repair version : 3.18-0ppa25~precise
boot-sav version : 3.18-0ppa99~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-repair is executed in live-session (Ubuntu 12.04 LTS , precise , Ubuntu , i686)

=================== OSPROBER:
/dev/sda1:Windows Recovery Environment (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda6:Ubuntu 10.04.4 LTS (10.04):Ubuntu:linux

=================== BLKID:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="PQSERVICE" UUID="E4F8C06FF8C04212" TYPE="ntfs"
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="125CC1BA5CC198BD" TYPE="ntfs"
/dev/sda3: LABEL="Acer" UUID="CE9AC4779AC45E19" TYPE="ntfs"
/dev/sda5: UUID="59dca341-da32-4147-96f7-cfcb95b60bcf" TYPE="ext4"
/dev/sda6: UUID="324fc8a2-5ac7-4838-92bd-5a123e590f8a" TYPE="ext4"
/dev/sda7: UUID="84e85a0b-cbdb-4fe1-8b88-7346a58a22e4" TYPE="swap"
/dev/sdb1: LABEL="New Volume" UUID="496F-1FCF" TYPE="vfat"


1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /mnt/boot-sav/sda6/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    BOOTMGR,    no-grldr,    BOOT/BCD,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda2.
sda3    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda3.
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    /mnt/boot-sav/sda6.

sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     2048 sectors * 512 bytes

=================== PARTED:

Model: ATA WDC WD3200BPVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  14.0GB  14.0GB  primary   ntfs            diag
2      14.0GB  14.1GB  105MB   primary   ntfs            boot
3      14.1GB  172GB   158GB   primary   ntfs
4      172GB   320GB   148GB   extended                  lba
5      172GB   287GB   115GB   logical   ext4
6      287GB   313GB   26.2GB  logical   ext4
7      313GB   320GB   6793MB  logical   linux-swap(v1)


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdb: 8020MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      41.0kB  8020MB  8019MB  primary  fat32        boot, lba


=================== MOUNT:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk ecryptfs fd full fuse hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sdb sdb1 sdc sg0 sg1 sg2 shm snapshot snd stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 v4l vga_arbiter video0 zero
/dev/mapper:  control
/mnt/boot-sav/sda3:  2012 AFA membership list_rough.xls 297276_2290081364394_1019779014_2525516_475732116_n.jpg Ancient Food Technology (Technology and Change in History)(gnv64).pdf autoexec.bat Backup book bookmarks-2012-04-10.json BOOTSECT.BAK brewing Complete Idiots Guide to Herbal Remedies.pdf config.sys Documents and Settings female diety-simek.pdf Ferments food Food Drying with an Attitude A Fun and Fabulous Guide to Creating Snacks, Meals, and Crafts.pdf Food Prep and Recipes Getting Started with Ubuntu 10.04.pdf hiberfil.sys Intel M2U00028.MPG mainregsAMENDED2012.pdf matronae.pdf my_pix Odroerir-Issue-1.pdf OEM pagefile.sys Paleo Eating For Modern People (gnv64).pdf PerfLogs plants and gardening ProgramData Program Files Recipes for the 21st Century Hunter Gatherer (gnv64).pdf Recovery $Recycle.Bin Survival and austere medicine System Volume Information The_Luck_In_the_Head(AWSmith1962).pdf The Paleo Solution - Robb Wolf.pdf Think_Again.pdf Ubuntu Unleashed.pdf Users Windows

=================== DF:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  495M  109M  387M  22% /
udev           devtmpfs   488M   12K  488M   1% /dev
tmpfs          tmpfs      198M  844K  198M   1% /run
/dev/sdb1      vfat       7.5G  703M  6.8G  10% /cdrom
/dev/loop0     squashfs   673M  673M     0 100% /rofs
tmpfs          tmpfs      495M   12K  495M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      495M   80K  495M   1% /run/shm
/dev/sda1      fuseblk     13G  8.9G  4.2G  68% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    100M   25M   76M  25% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    147G   36G  112G  25% /mnt/boot-sav/sda3
/dev/sda5      ext4       108G  2.5G  100G   3% /mnt/boot-sav/sda5
/dev/sda6      ext4        25G  3.6G   20G  16% /mnt/boot-sav/sda6

=================== FDISK:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd4d2a733

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Hidden NTFS WinRE
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27469824   335386623   153958400    7  HPFS/NTFS/exFAT
/dev/sda4       335388670   625139711   144875521    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       335388672   560668671   112640000   83  Linux
/dev/sda6       560670720   611870719    25600000   83  Linux
/dev/sda7       611872768   625139711     6633472   82  Linux swap / Solaris

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002048b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          80    15663103     7831512    c  W95 FAT32 (LBA)


/usr/share/boot-sav/gui-init.sh: line 59: kill: (17522) - No such process
=================== Repair blockers
64bits detected. Please use this software in a 64bits session. This will enable this feature.

=================== Default settings
recommendedrepair
This setting would reinstall the grub2 of sda6 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu   fix-windows-boot

=================== Settings chosen by the user
bootinfo
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!
pastebinit  packages needed
User refused to install pastebinit
```

I'm not sure what it all means, but I'm pretty confident that everything I have is 32bit.

---

### Post by jagdefalke on 2012-06-03
Still no luck.   I thought maybe it had something to do with the 12.04 usb start up so I made a 10.04 usb and tried again and the boot-repair is still telling me that it's detecting a 64bit.  I tried downloading the "secured 64bit CD" and it wouldn't download.   I really don't remember installing 10.04 in 64bit but i do have a fairly flakey memory at times.
Disk utilites is still giving me the "misaligned by 1024 bytes" and I can't seem to find anything on the forum and fits my situation.   I can access all my documents and downloads and such with this usb startup and I'm getting tempted to just back it all up and reformat the partitions, but I'm not sure that'll work.

---

### Post by jagdefalke on 2012-06-03
If I upgrade to the next distribution.. ie. 10.10, could that fix it??

---

### Post by Shadius on 2012-06-03
You could use GParted to resize your partition so that it corrects the misaligned partition. Boot-Repair installs the GRUB to the MBR of the hard disk drive so that you're able to boot into Ubuntu. As I understand, you were unable to boot into Ubuntu after installing Windows 7? Correct me if I'm wrong. That's because the bootloader of Windows 7 replaced GRUB, I believe. Here's a link that might help. 

[Partitioning]("http://askubuntu.com/questions/103855/partition-is-misaligned-by-3072-bytes-pavilion-dv7-6199us")

Hope it helps.

---

### Post by jagdefalke on 2012-06-03
Ok. I understand what that link is saying, but disk utility is telling me that the problem in the ext (sda4) and GParted will only let me make changes to sda6.  Would making changes to sda6 fix the problem?   
Also, I found in a bug report on the boot-repair software that lib64 files will cause the other 64 vs 32 issue, but I really don't know what to do about that.   (i really just need to take some linux/ubuntu classes or something..haha!!)

---

### Post by wilee-nilee on 2012-06-03
> **jagdefalke said:**
> Still no luck.   I thought maybe it had something to do with the 12.04 usb start up so I made a 10.04 usb and tried again and the boot-repair is still telling me that it's detecting a 64bit.  I tried downloading the "secured 64bit CD" and it wouldn't download.   I really don't remember installing 10.04 in 64bit but i do have a fairly flakey memory at times.
Disk utilites is still giving me the "misaligned by 1024 bytes" and I can't seem to find anything on the forum and fits my situation.   I can access all my documents and downloads and such with this usb startup and I'm getting tempted to just back it all up and reformat the partitions, but I'm not sure that'll work.

The alignment is not an issue, just finish the download of the boot-repair cd it will run 32 or 64 bit, and use it, with the recommended repair.

Check your internet speed on the web, and use this link it runs fast.
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by jagdefalke on 2012-06-03
I'm on 100mb alltel wireless.  I'll try that and see what happens.  Wish me luck!

---

### Post by jagdefalke on 2012-06-03
Still having issues downloading the CD.   It was downloading at around 25k/sec last night so I went to bed.  This morning all that was there was an empty icon so apparently it failed again.   I've tried this both on my desktop and on the netbook.
How do I fix grub the old fashioned way??

---

### Post by Shadius on 2012-06-03
> **jagdefalke said:**
> Still having issues downloading the CD.   It was downloading at around 25k/sec last night so I went to bed.  This morning all that was there was an empty icon so apparently it failed again.   I've tried this both on my desktop and on the netbook.
How do I fix grub the old fashioned way??

We'll reinstall it. 

Run the following code:
```
sudo fdisk -l
```

Post back the output.

---

### Post by wilee-nilee on 2012-06-03
You can chroot to the install, meaning with these commands you get to the root of the install to put grub back in the mbr, run these commands from a live ubuntu cd booted. You can copy and paste these to a terminal in the live cd environment.

```
sudo mount /dev/sda6 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
grub-install /dev/sda
``````
grub-install --recheck /dev/sda
``````
update-grub
``````
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```

---

### Post by jagdefalke on 2012-06-03
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd4d2a733

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1698    13631488   27  Unknown
/dev/sda2   *        1698        1710      102400    7  HPFS/NTFS
/dev/sda3            1710       20877   153958400    7  HPFS/NTFS
/dev/sda4           20877       38914   144875521    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5           20877       34901   112640000   83  Linux
/dev/sda6           34901       38088    25600000   83  Linux
/dev/sda7           38088       38914     6633472   82  Linux swap / Solaris

Disk /dev/sdb: 4043 MB, 4043309056 bytes
125 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00003fc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3944719    c  W95 FAT32 (LBA)

Disk /dev/sdc: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders
Units = cylinders of 320 * 512 = 163840 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002048b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       48948     7831512    c  W95 FAT32 (LBA)

```

---

### Post by Shadius on 2012-06-03
Follow wilee-nilee's post. Everything you need to do is there. Good luck!

---

### Post by jagdefalke on 2012-06-03
It worked!!!!!    Yay!!!   Thanx guys!  ... big hug... :)

---

### Post by Shadius on 2012-06-03
> **jagdefalke said:**
> It worked!!!!!    Yay!!!   Thanx guys!  ... big hug... :)

You're welcome and congratulations. Any other problems?

---

### Post by YannBuntu on 2012-06-04
Thanks wilee-nilee for helping jagdefalke!

**@jagdefalke:** your Ubuntu 10.04 was detected as a 64bits OS by Boot-Repair, which is why it asked you to use Boot-Repair from a 64bits session:

> **jagdefalke said:**
> ```
sda6    : (snip)    grub2,    grub-pc,    update-grub,    **64**
```

Please could you help me confirm if your 10.04 is indeed 32 or 64bits, by booting on your 10.04, then open a terminal (shortcut: CTRL+ALT+T), and indicate the output of the following 6 commands:
```
lscpu
uname -m
grep "model name" /proc/cpuinfo
cat /proc/cpuinfo | grep "flags" | head -n1 | grep "lm" | wc -l
ls /
ls /usr
```

---

### Post by jagdefalke on 2012-06-10
Sure.  It's 10.10 now because I got a hair up my butt to start stepping up to 12.04, but I'm starting to wonder if it wouldn't just be easier to reinstall for it instead.   

```
heathenhawker@heathenhawker-laptop:~$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit
CPU(s):                4
Thread(s) per core:    2
Core(s) per socket:    2
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 54
Stepping:              1
CPU MHz:               600.000
L1d cache:             24K
L1i cache:             32K
L2 cache:              512K
heathenhawker@heathenhawker-laptop:~$ uname -m
i686
heathenhawker@heathenhawker-laptop:~$ cat /proc/cpuinfo | grep "flags" | head -n1 | grep "lm" | wc -l
1
heathenhawker@heathenhawker-laptop:~$ ls /
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old
heathenhawker@heathenhawker-laptop:~$ ls /usr
bin  games  include  lib  lib64  local  sbin  share  src
heathenhawker@heathenhawker-laptop:~$ 

```I just finally now checked in on this thread because I was using the Win 7 partition on the internet today and it screwed up the grub, again!   So I had to reinstall it, again!   I'm not happy.  :p

---

### Post by YannBuntu on 2012-06-11
Thanks!
Your OS is 32bits indeed. Please could you update Boot-Repair, click "Create BootInfo" and indicate the new URL? 
(it should correctly detect the OS as 32bits now)

---

