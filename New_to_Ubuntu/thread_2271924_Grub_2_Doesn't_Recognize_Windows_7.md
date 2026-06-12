---
title: "Grub 2 Doesn't Recognize Windows 7"
date: 2015-04-02
forum: New to Ubuntu
---

### Post by Grace_Guo on 2015-04-02
I have Windows 7 on my HDD disk and I installed Ubuntu on my SDD disk. When I change the BIOS to boot from the HDD disk, Grub runs but only shows Ubuntu, not Windows 7. Both os-prober and update-grub did not work. I haven't figured out a way to boot into Windows yet.

Boot Info Script:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    16,775,167    16,773,120  84 OS/2 hidden C: drive
/dev/sda2    *     16,775,168    46,071,807    29,296,640  83 Linux
/dev/sda3          46,071,808    61,695,999    15,624,192  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sdb2             411,648   490,041,343   489,629,696   7 NTFS / exFAT / HPFS
/dev/sdb3         882,399,232   935,811,071    53,411,840   7 NTFS / exFAT / HPFS
/dev/sdb4         935,811,072   976,361,471    40,550,400  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        b82d7c17-19ab-48cf-b35c-99970ccf9295   ext4       
/dev/sda3        48dda2be-5905-4997-a91d-83cabe5ef708   swap       
/dev/sdb1        FA5E625C5E6211A5                       ntfs       SYSTEM_DRV
/dev/sdb2        5C18647E186458D2                       ntfs       Windows7_OS
/dev/sdb3        52CE6815CE67EFA1                       ntfs       LENOVO
/dev/sdb4        4AE213B0E2139EEF                       ntfs       LENOVO_PART

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sdb2        /media/happyeagle/Windows7_OS fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  b82d7c17-19ab-48cf-b35c-99970ccf9295
else
  search --no-floppy --fs-uuid --set=root b82d7c17-19ab-48cf-b35c-99970ccf9295
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-b82d7c17-19ab-48cf-b35c-99970ccf9295' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  b82d7c17-19ab-48cf-b35c-99970ccf9295
    else
      search --no-floppy --fs-uuid --set=root b82d7c17-19ab-48cf-b35c-99970ccf9295
    fi
    linux    /boot/vmlinuz-3.16.0-33-generic root=UUID=b82d7c17-19ab-48cf-b35c-99970ccf9295 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-33-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-b82d7c17-19ab-48cf-b35c-99970ccf9295' {
    menuentry 'Ubuntu, with Linux 3.16.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-33-generic-advanced-b82d7c17-19ab-48cf-b35c-99970ccf9295' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  b82d7c17-19ab-48cf-b35c-99970ccf9295
        else
          search --no-floppy --fs-uuid --set=root b82d7c17-19ab-48cf-b35c-99970ccf9295
        fi
        echo    'Loading Linux 3.16.0-33-generic ...'
        linux    /boot/vmlinuz-3.16.0-33-generic root=UUID=b82d7c17-19ab-48cf-b35c-99970ccf9295 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-33-generic-recovery-b82d7c17-19ab-48cf-b35c-99970ccf9295' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  b82d7c17-19ab-48cf-b35c-99970ccf9295
        else
          search --no-floppy --fs-uuid --set=root b82d7c17-19ab-48cf-b35c-99970ccf9295
        fi
        echo    'Loading Linux 3.16.0-33-generic ...'
        linux    /boot/vmlinuz-3.16.0-33-generic root=UUID=b82d7c17-19ab-48cf-b35c-99970ccf9295 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-advanced-b82d7c17-19ab-48cf-b35c-99970ccf9295' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  b82d7c17-19ab-48cf-b35c-99970ccf9295
        else
          search --no-floppy --fs-uuid --set=root b82d7c17-19ab-48cf-b35c-99970ccf9295
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=b82d7c17-19ab-48cf-b35c-99970ccf9295 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-recovery-b82d7c17-19ab-48cf-b35c-99970ccf9295' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  b82d7c17-19ab-48cf-b35c-99970ccf9295
        else
          search --no-floppy --fs-uuid --set=root b82d7c17-19ab-48cf-b35c-99970ccf9295
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=b82d7c17-19ab-48cf-b35c-99970ccf9295 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-advanced-b82d7c17-19ab-48cf-b35c-99970ccf9295' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  b82d7c17-19ab-48cf-b35c-99970ccf9295
        else
          search --no-floppy --fs-uuid --set=root b82d7c17-19ab-48cf-b35c-99970ccf9295
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /boot/vmlinuz-3.13.0-48-generic root=UUID=b82d7c17-19ab-48cf-b35c-99970ccf9295 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-recovery-b82d7c17-19ab-48cf-b35c-99970ccf9295' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  b82d7c17-19ab-48cf-b35c-99970ccf9295
        else
          search --no-floppy --fs-uuid --set=root b82d7c17-19ab-48cf-b35c-99970ccf9295
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /boot/vmlinuz-3.13.0-48-generic root=UUID=b82d7c17-19ab-48cf-b35c-99970ccf9295 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=b82d7c17-19ab-48cf-b35c-99970ccf9295 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=48dda2be-5905-4997-a91d-83cabe5ef708 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-R1ThspO7/Tmp_Log: No such file or directory


```

---

### Post by oldfred on 2015-04-02
If you install a Windows boot manager to sdb, your 500GB drive, does it boot?
Did you leave Windows 7 hibernated?

Otherwise I do not see why it should not work, os-prober primarily looks for bootmgr & BCD to know which NTFS partition is the bootable one, and you have both of those files in sdb1 & sdb2.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

If not we can add our own boot stanza to boot Windows like we did before os-prober worked for Windows 7 type installs.

---

### Post by Grace_Guo on 2015-04-03
I restored the Windows bootloader to sdb. When I booted it, it went to Repair, so I used these in the Command Prompt
```
bootrec.exe /fixboot
bootrec.exe /fixmbr
```
The fixboot command could not find the file but the fixmbr command worked. However, that would not let me boot.

I changed the boot flag through GParted from the System partition to the C: partition and when I booted that, it offered several options (Safe Mode, Normal, etc) that all did not work. Will I need to boot it through an installation disk while the boot flag is on the C: partition?

Also, I did not leave Windows hibernated.

---

### Post by oldfred on 2015-04-03
You show boot files in both sdb1 and sdb2, so either could have boot flag. Normally with Windows 7 or later it is on the 100MB boot partition.

Grub can only boot working Windows so you need to run Windows repairs.
You may need chkdsk on sdb1 and/or sdb2 and maybe other repairs.
If you run Windows autofix you have to run it 3 times as it does not fix everything on one pass.
And with chkdsk you have to run it until no errors as it does not fix everything on one pass.

---

### Post by Grace_Guo on 2015-04-03
I tried chkdsk, but it cannot open any volume except for X, which it states is write protected.
I ran autofix three times and they came up with these errors:
```

Startup Repair diagnosis and repair log
---------------------------
Number of repair attempts: 1
Session details
---------------------------
System Disk = \Device\Harddisk0
Windows directory =
AutoChk Run = 0
Number of root causes = 1

Test Performed:
---------------------------
Name: Check for updates
Result: Completed successfully. Error code = 0x0
Time taken = 0ms

Test Performed:
---------------------------
Name: System disk test
Result: Completed successfully. Error code = 0x0
Time taken = 16ms

Test Performed:
---------------------------
Name: Disk failure diagnosis
Result: Completed successfully. Error code = 0x0
Time taken = 46ms

Test Performed:
---------------------------
Name: Disk metadata test
Result: Completed successfully. Error code = 0x0
Time taken = 0ms

Root cause found:
---------------------------
System volume on disk is corrupt.

Repair action: File system repair (chkdsk)
Result: Failed. Error code = 0x1f
Time taken = 0ms

---------------------------
---------------------------
```

The metadata problem is probably because I removed dmraid before installing Ubuntu.

Thanks so much for you help so far!

---

### Post by oldfred on 2015-04-03
Do not know advanced Windows repairs. But you really need to get chkdsk to work or fix whatever issue is causing it not to work.
Did you change the drive order, or was Windows on sda?

       [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by Grace_Guo on 2015-04-04
chkdsk is not working because Windows thinks my file system is RAW, not NTFS. I am going to boot it from a system image.

Thanks again for all of your help!

---

### Post by oldfred on 2015-04-04
If it thinks it is RAW then the partition boot sector is damaged. If it was NTFS there is a backup that testdisk can restore. Or from a Windows repair you can use bootsect.exe to create a new boot sector.

Often required where users have accidentally installed grub to partition boot sector. NTFS has to have its own boot and configuration data in the boot sector.

 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

      
 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by Grace_Guo on 2015-04-06
Thanks for the additional resources!

---

### Post by Grace_Guo on 2015-04-25
UPDATE:
I started from scratch and wiped and reinstalled Windows on my HDD disk. Then I installed Ubuntu on my HDD disk and didn't manually edit anything (I just let the installation disc do all of the work). Now, I can successfully dual-boot both OSes. I think the error before may have been because I installed Ubuntu on my SSD disk which probably confused it. But now everything is working!
Thanks so much for all of your help!

---

