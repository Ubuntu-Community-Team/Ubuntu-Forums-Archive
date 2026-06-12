---
title: "Grub Error 17, LVM, LUKs and Grub2 Goodness"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by cfuser on 2011-11-01
I sure hope I'm missing something obvious, but I keep getting error 17 when Grub goes to load the menus. Note, a cable for my primary HD got knocked loose, which I think is the cause of this whole mess...

My setup

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c5ec3
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   204796619   102398278+   7  HPFS/NTFS/exFAT
/dev/sda2       204797952   205285375      243712   83  Linux
/dev/sda3       205285376  1953523711   874119168   83  Linux
```

Where sda3 is an encrypted LVM and sda2 is where /boot is mounted (well, on a working system).  

I booted into a live cd and did

```
sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sda3 crypt1
```

Which worked fine. 

```
ubuntu@ubuntu:~$ sudo lvdisplay
* --- Logical volume ---
* LV Name*************** /dev/vg1/lvswap
* VG Name*************** vg1
* LV UUID*************** jzdGGO-Gc02-vGrB-6toM-ngFE-0sRq-cjyqGu
* LV Write Access******* read/write
* LV Status************* available
* # open**************** 0
* LV Size*************** 9.31 GiB
* Current LE************ 2384
* Segments************** 1
* Allocation************ inherit
* Read ahead sectors**** auto
* - currently set to**** 256
* Block device********** 253:1
* *
* --- Logical volume ---
* LV Name*************** /dev/vg1/lvroot
* VG Name*************** vg1
* LV UUID*************** vvWD6i-gH2U-Se1z-MZbH-3QqE-3948-J8Jf2r
* LV Write Access******* read/write
* LV Status************* available
* # open**************** 1
* LV Size*************** 46.56 GiB
* Current LE************ 11920
* Segments************** 1
* Allocation************ inherit
* Read ahead sectors**** auto
* - currently set to**** 256
* Block device********** 253:2
* *
* --- Logical volume ---
* LV Name*************** /dev/vg1/lvhome
* VG Name*************** vg1
* LV UUID*************** qkfGDC-sJe9-hQVL-Uq0e-70ri-WfHJ-ci1XFQ
* LV Write Access******* read/write
* LV Status************* available
* # open**************** 0
* LV Size*************** 777.75 GiB
* Current LE************ 199103
* Segments************** 1
* Allocation************ inherit
* Read ahead sectors**** auto
* - currently set to**** 256
* Block device********** 253:3
```


So far, so good.

I then ran the following

```
sudo mkdir /mnt/root /mnt/root/boot /mnt/root/home
sudo mount /dev/vg1/lvroot /mnt/root
sudo mount /dev/vg1/lvhome /mnt/root/home
sudo mount /dev/sda2 /mnt/root/boot
sudo for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/root$i; done
```

All the mount points look good.

And chrooted

```
ubuntu@ubuntu:~$ sudo chroot /mnt/root
root@ubuntu:/# 
```

I did steps 3, 4 and 5 from the OPs instructions, unmounted, restarted and...  bleh, 

```
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17
```

So, how can I further troubleshoot, what have I done wrong, etc., etc.?  Grub does run, it just can't seem to find anything.

TIA.

---

### Post by drs305 on 2011-11-01
> **cfuser said:**
> I sure hope I'm missing something obvious, but I keep getting error 17 when Grub goes to load the menus. Note, a cable for my primary HD got knocked loose, which I think is the cause of this whole mess...


cfuser,

I don't know much about encryption or lvm, but I can tell you that Grub 2 is not installing since you are getting Grub error numbers. Grub legacy reports errors with number codes but Grub 2 does not.

I would suggest you download and run the boot info script from a LiveCD and post the contents of RESULTS.txt in a new thread. Include the fact that you are using lvm and encryption in the thread title. That combined with the RESULTS .txt contents should help those knowledgeable with these matters to assist you.

You can download the script and review the instructions by going to the "BIS" link in my signature line.

---

### Post by cfuser on 2011-11-01
Referencing 

Update by oldfred
Posts consolidated into this thread.

[http://ubuntuforums.org/showpost.php?p=11416522&postcount=189](http://ubuntuforums.org/showpost.php?p=11416522&postcount=189)

Basically, I muffed up my bootloader.  I can manually mount the boot device as well as my encrypted LVM (/root, /home), but I can't get the fellow to boot.  Per the suggestion in the referenced thread, my bootinfoscript RESULTS.txt is below...do you see any issues?  Any ideas?  I don't think it has much to do w/ LVM or encrypted partitions, thinking it's more a boneheaded thing I'm doing or a Grub thing.  Is my BIOS trying to hit sdc vs. sda?




```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub Legacy (v0.94) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd.
 => ISOhybrid (Syslinux 4.04 and higher) is installed in the MBR of /dev/sde.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 204818178 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda3: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/grub.cfg

sdf1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 NTFS / exFAT / HPFS
/dev/sda2         204,797,952   205,285,375       487,424  83 Linux
/dev/sda3         205,285,376 1,953,523,711 1,748,238,336  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   490,223,474   490,223,412  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   234,452,609   234,452,547  83 Linux

/dev/sdc1 ends after the last sector of /dev/sdc

Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63   625,137,344   625,137,282  83 Linux


Drive: sde _____________________________________________________________________

Disk /dev/sde: 2003 MB, 2003795968 bytes
19 heads, 24 sectors/track, 8582 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             64     1,428,055     1,427,992  17 Hidden NTFS / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63 2,930,272,064 2,930,272,002  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        24B88F2BB88EFB16                       ntfs       
/dev/sda2        22653b46-c15c-481f-9123-77d7c1172c76   ext4       boot
/dev/sda3        5ec8e8dd-95c0-463c-b1d9-3cc94fc06c3b   crypto_LUKS 
/dev/sdb1        f8fcdb2a-195a-43d0-a556-89ae9283dfaa   ext3       VIDS
/dev/sdc1        4b5ab58b-d871-42f1-b695-e4165113af3f   reiserfs   
/dev/sdd1        ca74a34a-4dfa-46d9-9c5c-a1719111a818   ext3       MP3
/dev/sde1                                               iso9660    Ubuntu 11.10 amd64
/dev/sdf1        4df6ea25-45ab-4bfd-a164-24f50cdf5b98   ext3       data

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

============================= sda2/grub/grub.cfg: ==============================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 22653b46-c15c-481f-9123-77d7c1172c76
if loadfont /grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 22653b46-c15c-481f-9123-77d7c1172c76
  set locale_dir=($root)/grub/locale
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
if background_color 0,71,115; then
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
        set root='(hd0,msdos2)'
        search --no-floppy --fs-uuid --set=root 22653b46-c15c-481f-9123-77d7c1172c76
        linux   /vmlinuz-3.0.0-12-generic root=/dev/mapper/vg1-lvroot ro   quiet splash vt.handoff=7
        initrd  /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos2)'
        search --no-floppy --fs-uuid --set=root 22653b46-c15c-481f-9123-77d7c1172c76
        echo    'Loading Linux 3.0.0-12-generic ...'
        linux   /vmlinuz-3.0.0-12-generic root=/dev/mapper/vg1-lvroot ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd  /initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos2)'
        search --no-floppy --fs-uuid --set=root 22653b46-c15c-481f-9123-77d7c1172c76
        linux   /vmlinuz-2.6.38-11-generic root=/dev/mapper/vg1-lvroot ro   quiet splash vt.handoff=7
        initrd  /initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos2)'
        search --no-floppy --fs-uuid --set=root 22653b46-c15c-481f-9123-77d7c1172c76
        linux   /vmlinuz-2.6.32-27-generic root=/dev/mapper/vg1-lvroot ro   quie
t splash vt.handoff=7
        initrd  /initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos2)'
        search --no-floppy --fs-uuid --set=root 22653b46-c15c-481f-9123-77d7c1172c76
        echo    'Loading Linux 2.6.32-27-generic ...'
        linux   /vmlinuz-2.6.32-27-generic root=/dev/mapper/vg1-lvroot ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd  /initrd.img-2.6.32-27-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos2)'
        search --no-floppy --fs-uuid --set=root 22653b46-c15c-481f-9123-77d7c1172c76
        linux16 /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos2)'
        search --no-floppy --fs-uuid --set=root 22653b46-c15c-481f-9123-77d7c1172c76
        linux16 /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root 24B88F2BB88EFB16
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

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                grub/grub.cfg                                  2
               =                grub/stage2                                    1
               =                initrd.img-2.6.32-27-generic                   2
               =                initrd.img-2.6.38-11-generic                   3
               =                initrd.img-3.0.0-12-generic                    3
               =                vmlinuz-2.6.32-27-generic                      1
               =                vmlinuz-2.6.38-11-generic                      2
               =                vmlinuz-3.0.0-12-generic                       1

=========================== sde1/boot/grub/grub.cfg: ===========================

```

---

### Post by oldfred on 2011-11-02
As drs305 says error 17 is from grub legacy which is your sdc 120GB drive. Have you tried booting from sda, your 1TB drive? It may not be complete as script does not show partition. But that may be just script.

To get script to parse a LVM partition:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install mawk

---

### Post by cfuser on 2011-11-03
I kinda thought I was--but, alas, you are correct, sir.  I messed w/ my BIOS and there is again joy in Mudville.

Thanks.

---

### Post by oldfred on 2011-11-03
I am really glad that worked as your combination of LVM & LUKs was way beyond me.:)

---

