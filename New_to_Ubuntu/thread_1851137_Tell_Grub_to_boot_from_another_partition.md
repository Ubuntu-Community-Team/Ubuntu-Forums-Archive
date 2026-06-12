---
title: "Tell Grub to boot from another partition"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by mrtalkingbadger on 2011-09-27
Hez Guys,
i just installed BT and told it to install the bootloader to sda3 because i didn`t want it to mess with my grub preferences and i figured it should be pretty easy to find out how to boot from another partition.
now i`m apparently to stupid to do so.

does anybody how i tell grub to just boot from sda3 instead of just sda.
i already took a look into the wiki on linuxselfhelp but as i said am just to stupid to figure out what i do wrong.

thanks in advance

---

### Post by spiky001 on 2011-09-27
Dose the boot loader not show the different OS on pc Post output of ```
sudo fdisk -l
```

---

### Post by rewyllys on 2011-09-27
> **mrtalkingbadger said:**
> Hez Guys,
i just installed BT and told it to install the bootloader to sda3 because i didn`t want it to mess with my grub preferences and i figured it should be pretty easy to find out how to boot from another partition.
now i`m apparently to stupid to do so.

does anybody how i tell grub to just boot from sda3 instead of just sda.
i already took a look into the wiki on linuxselfhelp but as i said am just to stupid to figure out what i do wrong.

thanks in advance
I suggest that you use the Synaptic Package Manager to install Grub Customizer.  Then use GC to change GRUB as you wish.

---

### Post by ajgreeny on 2011-09-27
I think you can only chainload from grub on the MBR of a disk to another grub on a partition, so you may not be able to do exactly what you want.

I could tell you how to do that in legacy grub, but haven't got a clue in grub2, I'm afraid.  Have a google (or googlubuntu.com) search and see if that throws any further light on your question.

---

### Post by oldfred on 2011-09-27
Ubuntu does not need to chainload, but just finds other installs with the os-prober.

sudo update-grub.

I do have a few chain load entries, but I thought the new BT used grub2 which is not supposed to be in a PBR as it is less reliable. It will work initially but on updates, you will have to reinstall.

I have boot stanzas to chainload to other MBRs but use this to boot other Ubuntu installs. Ubuntu puts a link in / to the newest kernel that you boot from.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by mrtalkingbadger on 2011-09-27
> **spiky001 said:**
> Dose the boot loader not show the different OS on pc Post output of ```
sudo fdisk -l
```
outpt of fdisk -l:
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
 
and a list of my partitions that made me realize i can't flag sda3 as boot device without unflagging  sda1...

---

### Post by oldfred on 2011-09-27
Do you have a bios_grub partition and did BT then put its grub into that partition?

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by mrtalkingbadger on 2011-09-27
> **rewyllys said:**
> I suggest that you use the Synaptic Package Manager to install Grub Customizer.  Then use GC to change GRUB as you wish.
grub customizer recognizes everything as it should but does not apply any of my changes after saving.
i have to admit i didn't read the whole wiki on it.

heres is a screenshot of it. 
[http://i1113.photobucket.com/albums/k518/MrTalkingBadger/y%20u%20no%20work%20bt/Screenshot-GrubCustomizer.png]("http://i1113.photobucket.com/albums/k518/MrTalkingBadger/y%20u%20no%20work%20bt/Screenshot-GrubCustomizer.png")
it only displays the entrys under lupin and the windows7(on sda3) on boot.

---

### Post by mrtalkingbadger on 2011-09-27
> **oldfred said:**
> Do you have a bios_grub partition and did BT then put its grub into that partition?

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.


for some reason it doesn't display the results of os-prober like grub-customizer.
does this have to do with me having a wubi installation?
there you go:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 476377312 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 3 for /boot/grub.
    Operating System:  BackTrack 5 R1 - Code Name 
                       Revolution 64 bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   444,454,894   444,248,047   7 NTFS / exFAT / HPFS
/dev/sda3         465,940,480   488,396,799    22,456,320  83 Linux
/dev/sda4         444,456,958   465,940,479    21,483,522   5 Extended
/dev/sda5         444,456,960   463,892,479    19,435,520  83 Linux
/dev/sda6         463,894,528   465,940,479     2,045,952  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       86951138-a67d-4597-ae1e-09e390d275ce   ext4       
/dev/sda1        BC4CEC2E4CEBE15E                       ntfs       System-reserviert
/dev/sda2        BEBAEF5CBAEF0FA7                       ntfs       
/dev/sda3        26f64577-039c-4784-8b9c-9ade9e44f5e1   ext3       
/dev/sda5        ae96dc11-affc-4732-a4e9-4482700c4a83   ext4       
/dev/sda6        67ae594d-ef9e-4adf-9ef5-6b9e9d3d5e46   swap       Swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda2/Wubi/boot/grub/menu.lst: =========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=BEBAEF5CBAEF0FA7 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=BEBAEF5CBAEF0FA7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.04, kernel 2.6.38-11-generic
uuid        BEBAEF5CBAEF0FA7
kernel        /boot/vmlinuz-2.6.38-11-generic root=UUID=BEBAEF5CBAEF0FA7 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.38-11-generic

title        Ubuntu 11.04, kernel 2.6.38-11-generic (recovery mode)
uuid        BEBAEF5CBAEF0FA7
kernel        /boot/vmlinuz-2.6.38-11-generic root=UUID=BEBAEF5CBAEF0FA7 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.38-11-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        BEBAEF5CBAEF0FA7
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=BEBAEF5CBAEF0FA7 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        BEBAEF5CBAEF0FA7
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=BEBAEF5CBAEF0FA7 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, memtest86+
uuid        BEBAEF5CBAEF0FA7
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

======================== sda2/Wubi/boot/grub/grub.cfg: =========================

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

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root BEBAEF5CBAEF0FA7
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-11-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root BEBAEF5CBAEF0FA7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=BEBAEF5CBAEF0FA7 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-11-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root BEBAEF5CBAEF0FA7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=BEBAEF5CBAEF0FA7 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root BEBAEF5CBAEF0FA7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=BEBAEF5CBAEF0FA7 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root BEBAEF5CBAEF0FA7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=BEBAEF5CBAEF0FA7 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BC4CEC2E4CEBE15E
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

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  14.332031250 = 15.388901376   boot/grub/grub.cfg                             1
   2.631351471 = 2.825392128    boot/grub/menu.lst                             1
   3.652904510 = 3.922276352    boot/initrd.img-2.6.38-11-generic              2
   1.254463196 = 1.346969600    boot/initrd.img-2.6.38-8-generic               2
   6.957344055 = 7.470391296    boot/vmlinuz-2.6.38-11-generic                 1
  14.254215240 = 15.305347072   boot/vmlinuz-2.6.38-8-generic                  1
   3.652904510 = 3.922276352    initrd.img                                     2
   1.254463196 = 1.346969600    initrd.img.old                                 2
   6.957344055 = 7.470391296    vmlinuz                                        1
  14.254215240 = 15.305347072   vmlinuz.old                                    1

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 26f64577-039c-4784-8b9c-9ade9e44f5e1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 26f64577-039c-4784-8b9c-9ade9e44f5e1
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
menuentry 'Ubuntu, with Linux 2.6.39.4' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 26f64577-039c-4784-8b9c-9ade9e44f5e1
    linux    /boot/vmlinuz-2.6.39.4 root=UUID=26f64577-039c-4784-8b9c-9ade9e44f5e1 ro   text splash vga=791
    initrd    /boot/initrd.img-2.6.39.4
}
menuentry 'Ubuntu, with Linux 2.6.39.4 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 26f64577-039c-4784-8b9c-9ade9e44f5e1
    echo    'Loading Linux 2.6.39.4 ...'
    linux    /boot/vmlinuz-2.6.39.4 root=UUID=26f64577-039c-4784-8b9c-9ade9e44f5e1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.39.4
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 26f64577-039c-4784-8b9c-9ade9e44f5e1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 26f64577-039c-4784-8b9c-9ade9e44f5e1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set BC4CEC2E4CEBE15E
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=26f64577-039c-4784-8b9c-9ade9e44f5e1 /               ext3    errors=remount-ro 0       1
# /usr/local was on /dev/sda5 during installation
UUID=ae96dc11-affc-4732-a4e9-4482700c4a83 /usr/local      ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=67ae594d-ef9e-4adf-9ef5-6b9e9d3d5e46 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 227.154430389 = 243.905212416  boot/grub/core.img                             1
 227.060791016 = 243.804667904  boot/grub/grub.cfg                             1
 232.539741516 = 249.687646208  boot/initrdf.img-2.6.39.4                      6
 227.069652557 = 243.814182912  boot/initrd.img-2.6.39.4                       8
 232.557586670 = 249.706807296  boot/initrds.img-2.6.39.4                      7
 232.672355652 = 249.830039552  boot/vmlinuz-2.6.39.4                          3
 227.069652557 = 243.814182912  initrd.img                                     8
 232.672355652 = 249.830039552  vmlinuz                                        3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  01 1c 45 f7 c3 40 ae c5  96 38 98 50 44 4f 9c 21  |..E..@...8.PDO.!|
00000010  e1 f1 1f fc 23 c0 aa 08  83 4f 97 01 b5 40 56 0c  |....#....O...@V.|
00000020  61 20 f8 1f d0 62 97 c6  52 fa c4 1d 75 60 09 c2  |a ...b..R...u`..|
00000030  a7 e7 64 fa 38 92 8a 85  87 83 08 45 be fd 80 c5  |..d.8......E....|
00000040  4f 70 b8 f1 b2 a0 62 a1  58 30 db c5 3a 56 ed 06  |Op....b.X0..:V..|
00000050  1c 03 15 06 42 13 de 15  1c fb 00 c9 55 0c 7c ad  |....B.......U.|.|
00000060  a8 0c 05 4b 81 86 2b e2  a3 e8 86 92 ce 14 be 83  |...K..+.........|
00000070  0d c5 c2 13 de 97 a5 24  b6 95 1a 1e b0 11 06 18  |.......$........|
00000080  ac 04 41 c0 a5 79 83 74  4e 57 0f b9 e6 8d da 20  |..A..y.tNW..... |
00000090  12 86 87 23 40 46 44 5f  7a c0 4f e3 50 88 bf 7f  |...#@FD_z.O.P...|
000000a0  9f 54 05 c7 a5 93 5c 19  15 78 b8 d5 d3 63 b8 33  |.T....\..x...c.3|
000000b0  0c e7 c1 a0 0e 12 e0 1f  a0 ca 34 0d 80 6c 56 ad  |..........4..lV.|
000000c0  3a a1 f6 0f d5 dd 02 ff  3d 2b 48 f1 ca fc 25 5f  |:.......=+H...%_|
000000d0  7a 89 7f 98 5e 10 55 97  fd 54 6b 04 89 fc 53 80  |z...^.U..Tk...S.|
000000e0  a9 b1 03 a7 2f f8 23 78  d1 f1 a7 45 5e fa af 97  |..../.#x...E^...|
000000f0  c5 3b e5 2b 19 ce d8 46  3f ff 3f f4 2e 1e 00 74  |.;.+...F?.?....t|
00000100  40 d3 85 d7 ca e0 ef 66  13 57 07 c1 8f fa 93 08  |@......f.W......|
00000110  47 a2 25 23 f8 eb d9 b5  c3 dc b2 63 5d 3e 1b 01  |G.%#.......c]>..|
00000120  61 2a bc ca 67 aa 54 23  ab 9b bc 36 f8 74 43 56  |a*..g.T#...6.tCV|
00000130  c9 6e 9c 78 a8 03 81 e1  50 45 02 54 ad c0 64 09  |.n.x....PE.T..d.|
00000140  42 b7 af 85 47 44 4f 81  21 88 18 02 61 90 d8 f0  |B...GDO.!...a...|
00000150  2c 46 bf 82 a8 60 5c 78  de 0c 6b 34 8c 6f 06 21  |,F...`\x..k4.o.!|
00000160  a0 55 65 f4 77 fb d1 1f  ec 12 df b7 52 e1 18 90  |.Ue.w.......R...|
00000170  1f d6 de 18 1e b7 2a fc  19 06 04 5f cb 1b 50 04  |......*...._..P.|
00000180  be 7c 54 30 43 e2 c3 19  4d 65 0e 62 7a 32 0e 88  |.|T0C...Me.bz2..|
00000190  fb 85 fe f8 88 a7 db 27  31 38 e4 6a e7 07 c7 63  |.......'18.j...c|
000001a0  5f 02 43 18 ab 9b e0 53  7f 22 4f c5 25 87 d7 4c  |_.C....S."O.%..L|
000001b0  ca c4 8d 71 86 a4 1a 0c  84 08 33 e0 58 09 00 fe  |...q......3.X...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 28 01 00 fe  |............(...|
000001d0  ff ff 05 fe ff ff ce 91  28 01 34 3e 1f 00 00 00  |........(.4>....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```I got to somehow replace the sda2/Wubi/boot/grub/menu.lst with the updated one if i get it right.
problem is i can't even find the Wubi direction which should be located in /host/.
can't enter it using terminal either..."no such file or directory"
and where did grub customizer save its changes to?
wasn't there a command one could use to see which files a process accesses?

---

### Post by oldfred on 2011-09-27
It would have been nice to know Ubuntu was a wubi install. I do not think you can chain from it to anything else, but once in grub2 you can do a lot of different things.

Your wubi install has both grub & grub2? Did you install grub intentionally somewhere in wubi?

You can install BT's grub2 to the MBR to dual boot or use another third party boot loader which I know nothing about. EasyBCD. It is a windows boot loader that will boot the grub installed to the partition. But grub2 in a partition is not recommended, but will work for a while.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---

### Post by mrtalkingbadger on 2011-09-28
got it working now using in the commandprompt of grub (press c while grub manager asks you what to boot)  

menuentry "Back Track" { 
insmod part_msdos 
set root=(hd0,msdos3) 
search --no-floppy --fs-uuid --set=root <UUID of the partition>
linux /vmlinuz root=UUID=<UUID of the partition> ro quiet splash 
initrd /initrd.img
}  

still one problem remains. 
how do i make this change permanent? 
can i simply enter it in menu.lst?  
as i did it now the entry disappears every time i reboot. 

thanks for the help so far... wubi really didn't make this easier for me ](*,)

---

### Post by oldfred on 2011-09-28
IF that from your wubi grub command line? If so that would be good to know.

You can copy that into 40_custom from your Ubuntu command line and so a sudo update-grub to add it to your grub2 grub.cfg. You also seemed to have a menu.lst but that is from grub legacy and may confuse things even more.

gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by mrtalkingbadger on 2011-11-09
didn't work either. 
got no idea why...

got it working now with a fresh install
so something i have learned of this:
don't use wubi, if want to multiboot more than one distro and windows

---

