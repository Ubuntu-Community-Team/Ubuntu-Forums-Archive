---
title: "Kernal Panic - Not syncing: VFS: Unable to mount root fs on unknown block(0,0)"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by BlueprintIT on 2012-06-27
PLEASE, be aware that I am NOT by any means that experienced with the  command line so I may need a little hand-holding/explaining.  Sorry for  any trouble that may cause.


So I am using a Toshiba Satellite with a 500GB HDD using Ubuntu 10.04.  As it turns out, this morning I ok'd the update manager to run a few suggested updates and the update manager frozen then crashed half way through an update (which file, I do not know)

I was able to continue using Ubuntu and nothing was amiss.  I left a client site and shut down the laptop.  When I got back to the office, I received the error message in the title when trying to boot the laptop.

I tried following a few different solutions but have been unable to fix my installation.  I have MANY client and personal files I can not afford to lose. Most are backed up but I have a few client files I CAN NOT lose so reinstallation is not an option at all.

I grabbed an Ubuntu LiveDVD 11.10 and ran the bootinfoscript file.  Here are the results.  ANY help is appreciated.


FULL DISCLOSURE:  I did make a mistake and only give 50MB to the BOOT partition (sda1) when I first created this installation.  Yeah, newbie mistake.  In any case, since my installation is messed up, and I had a liveCD running, I figured I should at least fix this using gparted, resize my main storage partition, and give the BOOT partition a nice 5GB of space.  It's not like I'm hurting for room on this HDD since this isn't used to download files and the files I do have are documents or spreadsheets.   I hope this doesn't complicate fixing this issue.


>                                     Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98 ) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 765802485.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    10,338,303    10,338,241  83 Linux
/dev/sda2          10,338,304   488,378,367   478,040,064   5 Extended
/dev/sda5          10,340,352    20,103,167     9,762,816  83 Linux
/dev/sda6          20,105,216    39,634,943    19,529,728  83 Linux
/dev/sda7          39,636,992    49,399,807     9,762,816  83 Linux
/dev/sda8          49,401,856    59,164,671     9,762,816  83 Linux
/dev/sda9          59,166,720   478,611,455   419,444,736  83 Linux
/dev/sda10        478,613,504   488,376,319     9,762,816  82 Linux swap / Solaris
/dev/sda3         488,392,065   765,802,484   277,410,420  83 Linux
/dev/sda4         765,802,485   976,768,064   210,965,580   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        13200159-4a5a-453d-a3b8-3f6f75a14e6d   ext4       
/dev/sda10       f30697d0-8fa4-4e9f-bdee-404f4f2e7311   swap       
/dev/sda3        cc972e82-b5f2-4316-939a-21c478ae92b4   ext4       Storage
/dev/sda4        7FDC-5969                              vfat       Store2
/dev/sda5        fb0caab1-d7a0-480d-9384-8d0cc53ce2f6   ext4       
/dev/sda6        4eaef3ce-de4f-4e70-bab9-84b08c23e5ca   ext4       
/dev/sda7        847ecb1f-69d8-4165-9004-3ac4f61c2bb1   ext4       
/dev/sda8        1881734a-2572-4595-9136-8e9260c843ad   ext4       
/dev/sda9        30abbff2-d904-4f2f-9cdb-ded20a4103b2   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/13200159-4a5a-453d-a3b8-3f6f75a14e6d ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /mnt/drive               ext4       (rw)
/dev/sda1        /mnt                     ext4       (rw)
/dev/sda3        /media/Storage           ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda4        /media/Store2            vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks)
/dev/sda5        /media/fb0caab1-d7a0-480d-9384-8d0cc53ce2f6 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /media/4eaef3ce-de4f-4e70-bab9-84b08c23e5ca ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/847ecb1f-69d8-4165-9004-3ac4f61c2bb1 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda8        /media/1881734a-2572-4595-9136-8e9260c843ad ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda9        /media/30abbff2-d904-4f2f-9cdb-ded20a4103b2 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda1/grub/grub.cfg: ==============================

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
search --no-floppy --fs-uuid --set 4eaef3ce-de4f-4e70-bab9-84b08c23e5ca
if loadfont /share/grub/unicode.pf2 ; then
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 13200159-4a5a-453d-a3b8-3f6f75a14e6d
set locale_dir=($root)/grub/locale
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 13200159-4a5a-453d-a3b8-3f6f75a14e6d
    linux    /vmlinuz-2.6.32-41-generic root=/dev/sda5 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.32-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 13200159-4a5a-453d-a3b8-3f6f75a14e6d
    echo    'Loading Linux 2.6.32-41-generic ...'
    linux    /vmlinuz-2.6.32-41-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
}
menuentry 'Ubuntu, with Linux 2.6.32-40-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 13200159-4a5a-453d-a3b8-3f6f75a14e6d
    linux    /vmlinuz-2.6.32-40-generic root=UUID=fb0caab1-d7a0-480d-9384-8d0cc53ce2f6 ro   quiet splash
    initrd    /initrd.img-2.6.32-40-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 13200159-4a5a-453d-a3b8-3f6f75a14e6d
    echo    'Loading Linux 2.6.32-40-generic ...'
    linux    /vmlinuz-2.6.32-40-generic root=UUID=fb0caab1-d7a0-480d-9384-8d0cc53ce2f6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-40-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 13200159-4a5a-453d-a3b8-3f6f75a14e6d
    linux    /vmlinuz-2.6.32-33-generic root=UUID=fb0caab1-d7a0-480d-9384-8d0cc53ce2f6 ro   quiet splash
    initrd    /initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 13200159-4a5a-453d-a3b8-3f6f75a14e6d
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /vmlinuz-2.6.32-33-generic root=UUID=fb0caab1-d7a0-480d-9384-8d0cc53ce2f6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 13200159-4a5a-453d-a3b8-3f6f75a14e6d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 13200159-4a5a-453d-a3b8-3f6f75a14e6d
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.008904934 = 0.009561600    grub/core.img                                  1
   0.011275768 = 0.012107264    grub/grub.cfg                                  1
   0.045928478 = 0.049315328    initrd.img-2.6.32-33-generic                   2
   0.039093494 = 0.041976320    initrd.img-2.6.32-40-generic                   6
   0.029431820 = 0.031602176    vmlinuz-2.6.32-33-generic                      1
   0.035063267 = 0.037648896    vmlinuz-2.6.32-40-generic                      1
   0.047847271 = 0.051375616    vmlinuz-2.6.32-41-generic                      5

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=fb0caab1-d7a0-480d-9384-8d0cc53ce2f6 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=13200159-4a5a-453d-a3b8-3f6f75a14e6d /boot           ext4    defaults        0       2
# /home was on /dev/sda9 during installation
UUID=30abbff2-d904-4f2f-9cdb-ded20a4103b2 /home           ext4    defaults        0       2
# /tmp was on /dev/sda8 during installation
UUID=1881734a-2572-4595-9136-8e9260c843ad /tmp            ext4    defaults        0       2
# /usr was on /dev/sda6 during installation
UUID=4eaef3ce-de4f-4e70-bab9-84b08c23e5ca /usr            ext4    defaults        0       2
# /var was on /dev/sda7 during installation
UUID=847ecb1f-69d8-4165-9004-3ac4f61c2bb1 /var            ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=f30697d0-8fa4-4e9f-bdee-404f4f2e7311 none            swap    sw              0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  20 20 20 20 20 20 3c 70  72 6f 70 20 6f 6f 72 3a  |      <prop oor:|
00000010  6e 61 6d 65 3d 22 4e 61  6d 65 22 3e 0a 20 20 20  |name="Name">.   |
00000020  20 20 20 20 20 20 20 3c  76 61 6c 75 65 20 78 6d  |       <value xm|
00000030  6c 3a 6c 61 6e 67 3d 22  65 6e 2d 55 53 22 3e 35  |l:lang="en-US">5|
00000040  39 32 35 20 57 68 69 74  65 20 4c 61 73 65 72 20  |925 White Laser |
00000050  4c 61 62 65 6c 73 20 66  6f 72 20 5a 69 70 20 44  |Labels for Zip D|
00000060  69 73 6b 73 20 28 66 61  63 65 29 3c 2f 76 61 6c  |isks (face)</val|
00000070  75 65 3e 0a 20 20 20 20  20 20 20 20 3c 2f 70 72  |ue>.        </pr|
00000080  6f 70 3e 0a 20 20 20 20  20 20 20 20 3c 70 72 6f  |op>.        <pro|
00000090  70 20 6f 6f 72 3a 6e 61  6d 65 3d 22 4d 65 61 73  |p oor:name="Meas|
000000a0  75 72 65 22 3e 0a 20 20  20 20 20 20 20 20 20 20  |ure">.          |
000000b0  3c 76 61 6c 75 65 3e 53  3b 39 31 38 32 3b 38 34  |<value>S;9182;84|
000000c0  31 32 3b 35 39 35 36 3b  35 30 38 30 3b 33 32 32  |12;5956;5080;322|
000000d0  36 3b 31 36 36 39 3b 32  3b 33 3c 2f 76 61 6c 75  |6;1669;2;3</valu|
000000e0  65 3e 0a 20 20 20 20 20  20 20 20 3c 2f 70 72 6f  |e>.        </pro|
000000f0  70 3e 0a 20 20 20 20 20  20 3c 2f 6e 6f 64 65 3e  |p>.      </node>|
00000100  0a 20 20 20 20 20 20 3c  6e 6f 64 65 20 6f 6f 72  |.      <node oor|
00000110  3a 6e 61 6d 65 3d 22 4c  34 37 22 20 6f 6f 72 3a  |:name="L47" oor:|
00000120  6f 70 3d 22 72 65 70 6c  61 63 65 22 20 6f 6f 72  |op="replace" oor|
00000130  3a 66 69 6e 61 6c 69 7a  65 64 3d 22 74 72 75 65  |:finalized="true|
00000140  22 3e 0a 20 20 20 20 20  20 20 20 3c 70 72 6f 70  |">.        <prop|
00000150  20 6f 6f 72 3a 6e 61 6d  65 3d 22 4e 61 6d 65 22  | oor:name="Name"|
00000160  3e 0a 20 20 20 20 20 20  20 20 20 20 3c 76 61 6c  |>.          <val|
00000170  75 65 20 78 6d 6c 3a 6c  61 6e 67 3d 22 65 6e 2d  |ue xml:lang="en-|
00000180  55 53 22 3e 35 39 32 35  20 57 68 69 74 65 20 4c  |US">5925 White L|
00000190  61 73 65 72 20 4c 61 62  65 6c 73 20 66 6f 72 20  |aser Labels for |
000001a0  5a 69 70 20 44 69 73 6b  73 20 28 74 6f 70 20 73  |Zip Disks (top s|
000001b0  70 69 6e 65 29 3c 2f 76  61 6c 75 65 3e 0a 00 a7  |pine)</value>...|
000001c0  a5 83 83 fe ff ff 00 08  00 00 00 f8 94 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 00 00  95 00 00 08 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 




---

### Post by BlueprintIT on 2012-06-27
anyone?

---

### Post by BlueprintIT on 2012-06-27
Does anyone have an idea, or would be willing to assist me on this?  I have tried various suggestions on this forum, but nothing has worked so far.

---

### Post by BlueprintIT on 2012-06-28
This is vitally important. I don't mean to spam but I absolutely have to have this repaired today ( 6/28 ). 
 
If I would get a better response in another sub-section of the forum, I'd gladly move this thread. I just don't have much experiance so this seemed the best place to post.
 
I dont mean to sound demanding, but over 100 views and no one is able to help?  I'm losing faith in Ubuntu.  (Ubuntu/Linux isn't just about the software but the community as well..)
 
If I have to pull the drive, back up the data and reinstall, I'm not sure I would go back to ubuntu since it is very hard to find help if you have issues.

---

### Post by BlueprintIT on 2012-06-28
Mark this as solved.
 
I went to IRC Chat and was helped by two GREAT community members who I now owe my continued employement too. 
 
THANK YOU CharlesA and philinux!
 
Solution:
 
First I had to reboot my laptop.
 
Next, as Ubuntu is the only OS on this hard drive and my GRUB menu will not show up during boot, I had to press the "SHIFT" key just after the bios screen, when a blinking cursor in the upper-left corner appeared (same time you would press "F8" to get the boot options menu in a Windows installation).
 
I selected an older kernal and booted into it.
 
Then, I ran the following commands in the Terminal:
 
> sudo update-initramfs -u -k 2.6.32-41-generic
(if you have the same issue, use the version number that you are trying to repair)
 
> sudo update-grub2
 
The commands repaired my broken linux install and my JOB IS SAVED!
 
To other newbies that need immediate help, use the IRC chat. Go to #Ubuntu (the support room) and POLITELY ask if someone could help you and then state your problem.
 
It worked great for me. I found the forums are not the best place to try and get support in a timely manner.

---

### Post by CharlesA on 2012-06-28
Glad you were able to get it working. :)

Here's the full solution on askubuntu:
[http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0](http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0)

---

