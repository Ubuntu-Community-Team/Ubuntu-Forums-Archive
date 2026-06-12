---
title: "Installed but cannot get to start?"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by nessy777 on 2012-06-07
I bought a second hand Lenovo/IBM T60 without any operatig system to put Ubuntu on.
I tried it out using a bootable usb (I changed the boot options to ensure the usb started first) Everything seemed to go ok and I installed to the hard drive.
I then restarted (without the USB) but couldnt get Ubuntu to start. I thought I had to change the boot option back to HDD, tried but again no luck.
Not sure if I've picked the correct option but the list is as follows:

1 ATA HDD0: HTS (then a load of numbers)
2 ATA HDD2
3 ATA HDD1
4 USB FDD
5 ATAPI CDO DVD DRIVE
7 PCI LAN
8 USB CD

Cant work out what to do? I've since booted from the USB stick without any problems but cannot understand where I'm going wrong.

Thanks

---

### Post by nessy777 on 2012-06-07
Anyone help? Really do know where to start.

---

### Post by Gone fishing on 2012-06-07
My guess is that grub has been installed on the wrong hard drive you have 3 hard drives in the box have you tried to boot from each of them?

---

### Post by Shadius on 2012-06-07
Download and run this [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/"). That'll give us a better idea of what's going on. Post the results back here. Boot into your LiveUSB, download the script, run it in Terminal and post back the results.

---

### Post by nessy777 on 2012-06-07
> **Gone fishing said:**
> My guess is that grub has been installed on the wrong hard drive you have 3 hard drives in the box have you tried to boot from each of them?

I have tried to install from all but I only have 1 hard drive!


Now getting a message (without the USB stick); 

GNU GRUB

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible devise or file completions.

---

### Post by nessy777 on 2012-06-07
> **Shadius said:**
> Download and run this [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/"). That'll give us a better idea of what's going on. Post the results back here. Boot into your LiveUSB, download the script, run it in Terminal and post back the results.
Thanks for this but I really havnt got a clue what to do - I've downloaded, I know where the terminal is but unsure what I'm supposed to be pasting into the terminal.
I'm on the verge of giving up and installing Windows - I installed Ubuntu on my daughters laptop at the weekend and it was so easy, thought I did the same here but stuck. I think I'm well out of my depth.

---

### Post by Shadius on 2012-06-07
> **nessy777 said:**
> Thanks for this but I really havnt got a clue what to do - I've downloaded, I know where the terminal is but unsure what I'm supposed to be pasting into the terminal.
I'm on the verge of giving up and installing Windows - I installed Ubuntu on my daughters laptop at the weekend and it was so easy, thought I did the same here but stuck. I think I'm well out of my depth.

Some further instructions here:

[Boot Info Script Instructions]("http://bootinfoscript.sourceforge.net/")

---

### Post by wilee-nilee on 2012-06-07
The bootscript can be confusing, extract it to the desktop and run the command posted. Copy and paste all the text from the results.txt that is generated to a reply. While the reply is still open, highlight all the text and click on the # in the reply panel and submit reply.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by nessy777 on 2012-06-07
```
  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/mnt/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 7656 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   115,116,031   115,113,984  83 Linux
/dev/sda2         115,118,078   117,209,087     2,091,010   5 Extended
/dev/sda5         115,118,080   117,209,087     2,091,008  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *            129     3,907,007     3,906,879   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3   ext4       
/dev/sda5        2b3a1205-3fe2-4cc2-97bb-3dac0532c7f2   swap       
/dev/sdb1        AC90-76CC                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


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
search --no-floppy --fs-uuid --set=root c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3
    echo    'Loading Linux 3.2.0-24-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3
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
UUID=c75be6a3-69be-41c4-a4d9-8b8ef5b2bcb3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2b3a1205-3fe2-4cc2-97bb-3dac0532c7f2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           3
               =                boot/initrd.img-3.2.0-24-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-24-generic-pae              1
               =                initrd.img                                     2
               =                initrd.img.old                                 3
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
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

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
000001b0  30 30 30 30 30 30 30 30  30 30 30 30 30 30 00 fe  |00000000000000..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 1f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
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
/home/ryan/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

### Post by nessy777 on 2012-06-07
Not sure if I've done the above right, but thanks for the help!

---

### Post by nessy777 on 2012-06-07
Dont know if this helps, I've tried to install windows (to dual boot) but getting an error message stating that no hard disc drives were found. Is this because Ubuntu is already on there? and would I need to unistall first?

---

### Post by wilee-nilee on 2012-06-07
I see one HD,

If you are actually getting to the Ubuntu with the usb stick when you get there take it out and run theses two commands. Make sure it is the install not the loaded usb, people have confused these.

```
sudo grub-install /dev/sda
``````
sudo update-grub
```The script looks like it should boot with out the stick, but things can get mixed up.

---

### Post by nessy777 on 2012-06-08
> **wilee-nilee said:**
> I see two HD's make sure you are booting from the smallest one there is grub in both HD's mbr. 

The sda HD is the one you want, let us know how that goes.

If you are actually getting to the Ubuntu with the usb stick when you get there take it out and run theses two commands. Make sure it is the install not the loaded usb, people have confused these.

```
sudo grub-install /dev/sda
``````
sudo update-grub
```The script looks like it should boot with out the stick, but things can get mixed up.
Thanks

This is what I get:

ryan@ryan-ThinkPad-T60:~$ sudo grub-install /dev/sda
[sudo] password for ryan: 
Installation finished. No error reported.
ryan@ryan-ThinkPad-T60:~$ 

and

ryan@ryan-ThinkPad-T60:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
ryan@ryan-ThinkPad-T60:~$

---

### Post by wilee-nilee on 2012-06-08
> **nessy777 said:**
> Thanks

This is what I get:

ryan@ryan-ThinkPad-T60:~$ sudo grub-install /dev/sda
[sudo] password for ryan: 
Installation finished. No error reported.
ryan@ryan-ThinkPad-T60:~$ 

and

ryan@ryan-ThinkPad-T60:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
ryan@ryan-ThinkPad-T60:~$

Does the computer boot now to ubuntu without the stick?

Windows would need a ntfs  to install to, the sda is only 80 gigs, and windows is best as the first on the hd really.

---

### Post by nessy777 on 2012-06-08
Yes it does!!!.

What happened? why is it now working???

Many, many thanks :)

---

### Post by wilee-nilee on 2012-06-08
> **nessy777 said:**
> Yes it does!!!.

What happened? why is it now working???

Many, many thanks :)

The command.
```
sudo grub-install /dev/sda
```
Puts grub in the mbr, that is the start of the boot from the internal HD, sometimes things can get messed up even though grub shows to be in the mbr from the script.

---

### Post by nessy777 on 2012-06-08
> **wilee-nilee said:**
> The command.
```
sudo grub-install /dev/sda
```Puts grub in the mbr, that is the start of the boot from the internal HD, sometimes things can get messed up even though grub shows to be in the mbr from the script.

Thanks very much, really appreciate your help (any others too)

---

### Post by Shadius on 2012-06-08
Congratulations! Kindly mark the thread as solved.

---

