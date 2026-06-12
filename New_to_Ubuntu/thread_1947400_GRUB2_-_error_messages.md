---
title: "GRUB2 - error messages"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by avnd on 2012-03-26
Hello!

My hard drive is partitioned as follows:

/dev/sda1 - GRUB (where I keep my GRUB files)
/dev/sda2 - WINDOWS 7
/dev/sda3 - DATA
/dev/sda4 - EXTENDED
/dev/sda5 - SWAP
/dev/sda6 - LUBUNTU
/dev/sda7 - ARCH
/dev/sda8 - SPARE

I've been having this partition structure for a long time now. I had the GRUB Legacy bootloader installed on the MBR with the stage 2 (or 1.5 or whatever) residing in the 'dedicated' GRUB partition. This way, the bootloader was totally independent and I was able to delete any Linux installation without affecting the others. 

Recently, after reading a post by a user called Herman, I learned that this was possible with GRUB 2 also. I did the following. 
1. I installed Ubuntu 11.10 on my 'SPARE'(/dev/sda8 ) partition.

2. I logged into the new Ubuntu installation.

3. I created a folder for mounting my GRUB partition.
sudo mkdir /media/GRUBpartition

4. I mounted my GRUB partition onto that mount point.
sudo mount /dev/sda1 -t ext4 /media/GRUBpartition

5. I installed GRUB2 following the command in Herman's post.
sudo grub-install --root-directory=/media/GRUBpartition /dev/sda

6. I relaxed permissions on the GRUB files for easier editing.
sudo chmod 777 -R /media/GRUBpartition

7. I generated the grub.cfg file.
sudo grub-mkconfig -o /media/GRUBpartition/boot/grub/grub.cfg


After doing the above steps, I rebooted. The computer booted fine with the menu list showing in white characters on a magenta background. I only tried booting into my Windows and the new Ubuntu 11.10 OS's and they both booted fine.

Now, I wanted to know if the GRUB files were totally independent of the new Ubuntu 11.10 installation. That was the whole point. I reformatted the Ubuntu 11.10 root partition (I had no separate partitions for home or boot). I rebooted.

This time I was greeted with error messages which flashed before the menu list showed up. But, this time the menu list was white characters on black background with larger fonts than before. I only tried booting into Windows and Windows booted fine.

The error messages which flashed before the GRUB menu showed up read the following:

```
error: no such device: 68d95051-60d3-4d3b-83da-2a2cfcbee14b
error: file not found
error: no suitable mode found
error: no video mode activated
```

My grub.cfg file is as follows

```
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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=68d95051-60d3-4d3b-83da-2a2cfcbee14b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=68d95051-60d3-4d3b-83da-2a2cfcbee14b ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 0D9CAB5E0372A8B0
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Arch (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root e05b18c4-e84b-4a50-8a3c-ba2f7028857d
	linux /boot/vmlinuz-linux root=/dev/sda7
	initrd /boot/initramfs-linux.img
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
```


What do I make of the above error messages? How can I correct them? Did I do something wrong while following Herman's method?

Thanks.

---

### Post by oldfred on 2012-03-26
Is it menu.lst that is coming up from grub legacy or grub.cfg from grub2?

May be best to post boot info script. 

The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```Or if you want a gui:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

I used to use a dedicated grub legacy partition, but with grub2 have not needed it as I just add entries to 40_custom and turn off the os-prober. But I do manually maintain grub.cfg in my USB to loopmount ISO directly and add entries to boot some of my installs on the hard drive as a backup way to boot.

Since you have a grub only partition it does not have the grub files in the other system partitions. So you may need to remove the references that refer to those standard locations.
e.g.
> if loadfont [COLOR=Red]/usr/share/[/COLOR]grub/unicode.pf2 ; thenBut it should have installed all the insmod files and should find a default video mode.

I normally just have the boot stanza without any of the other processing steps. It  either boots or not, but then does not do error handling or other features as well or at all.

This is part of my grub.cfg on my flash drive (just more of similar entries is missing):

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 11.10 Oneiric 64bit" {
    set isofile="/boot/iso/oneiric-desktop-amd64.iso"
    loopback loop (/dev/sdd,msdos1)/$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

menuentry "Ubuntu 11.04 Natty 64bit" {
    set isofile="/boot/iso/ubuntu-11.04-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/iso/ubuntu-10.10-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}


menuentry " " {
set root= 
}


# iso_filename=$isofile boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
menuentry "Parted Magic 6.1" {
    set isofile="/boot/iso/pmagic-6.1.iso"
    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw loglevel=0 max_loop=256
    initrd (loop)/pmagic/initramfs
}
```

---

### Post by avnd on 2012-03-27
Thanks for your reply, oldfred.

I'll will need some time to understand what you've posted. Meanwhile, I thought I could try generating the grub.cfg from a Live CD (from what I read, only installing GRUB from a Live CD is going to be messy) and then replace my present grub.cfg with the new one. Kindly do let me know if that is not possible or will present any hitches.

> I normally just have the boot stanza without any of the other processing steps. It either boots or not, but then does not do error handling or other features as well or at all.
So, what exactly is the advantage in having all the 'if...fi' lines I have in the beginning of my grub.cfg, mate? Yours looks so much neater. I'm no computer programmer. All those look like some foreign language to me.

> Since you have a grub only partition it does not have the grub files in the other system partitions. So you may need to remove the references that refer to those standard locations.
I'm just scared to delete lines that I don't completely understand, mate.

I'm also working on reading the GRUB2 manual so that I could write my own configuration file. 

Thanks.

P.S. I read that one is not supposed to change the grub.cfg file and that in order to change things in it, one has to edit the scripts that creat this file. From what I read, I see that some exist in the /etc folder of the linux installation that installed the GRUB. Now that I have a 'dedicated' GRUB partition, is there no way I can access those scripts?

---

### Post by coffeecat on 2012-03-27
@avnd, run the boot info script that oldfred described. This will give an complete overview of your system without which people cannot give informed advice. If you want to read about the boot info script, you can do so here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

But wget the git/testing version that oldfred mentions rather than the version in that link.

---

### Post by avnd on 2012-03-27
@coffeecat: Thanks for the link.

Here's the 'RESULTS' of bootinfoscript on my system.

```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 148372264 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Arch Linux ()
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  83 Linux
/dev/sda2    *        206,848    52,635,647    52,428,800   7 NTFS / exFAT / HPFS
/dev/sda3          52,635,648   136,521,727    83,886,080   7 NTFS / exFAT / HPFS
/dev/sda4         136,523,774   234,440,703    97,916,930   5 Extended
/dev/sda5         136,523,776   138,620,927     2,097,152  82 Linux swap / Solaris
/dev/sda6         138,622,976   180,566,015    41,943,040  83 Linux
/dev/sda7         180,568,064   201,539,583    20,971,520  83 Linux
/dev/sda8         201,541,632   234,440,703    32,899,072  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        70765486-1284-4c2f-aeaf-acf7d3a38e89   ext4       BOOT
/dev/sda2        0D9CAB5E0372A8B0                       ntfs       SEVEN
/dev/sda3        336C11E97D14234A                       ntfs       DATANTFS
/dev/sda5        61688e5f-26e5-4a8a-a7be-6a7c6f861b3f   swap       SWAP
/dev/sda6        74965cc2-9fb2-4a0f-9edf-9bde9472fb0a   ext4       
/dev/sda7        e05b18c4-e84b-4a50-8a3c-ba2f7028857d   ext4       ARCH_E16
/dev/sda8        dc8c4beb-e5f2-43eb-ac25-963617f93d5a   ext4       DATAEXT4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/DATANTFS          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=68d95051-60d3-4d3b-83da-2a2cfcbee14b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=68d95051-60d3-4d3b-83da-2a2cfcbee14b ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 0D9CAB5E0372A8B0
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Arch (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root e05b18c4-e84b-4a50-8a3c-ba2f7028857d
	linux /boot/vmlinuz-linux root=/dev/sda7
	initrd /boot/initramfs-linux.img
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

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.009088516 = 0.009758720    boot/grub/core.img                             1
   0.010945320 = 0.011752448    boot/grub/grub.cfg                             1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 0D9CAB5E0372A8B0
	chainloader +1
}
menuentry "Arch (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root e05b18c4-e84b-4a50-8a3c-ba2f7028857d
	linux /boot/vmlinuz-linux root=/dev/sda7
	initrd /boot/initramfs-linux.img
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=61688e5f-26e5-4a8a-a7be-6a7c6f861b3f none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda6/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  70.749435425 = 75.966627840   boot/grub/core.img                             1
  78.285739899 = 84.058673152   boot/grub/grub.cfg                             1
  67.332126617 = 72.297320448   boot/initrd.img-3.0.0-12-generic               2
  68.147602081 = 73.172930560   boot/initrd.img-3.0.0-16-generic               2
  74.343494415 = 79.825719296   boot/vmlinuz-3.0.0-12-generic                  1
  66.628391266 = 71.541690368   boot/vmlinuz-3.0.0-16-generic                  2
  68.147602081 = 73.172930560   initrd.img                                     2
  67.332126617 = 72.297320448   initrd.img.old                                 2
  66.628391266 = 71.541690368   vmlinuz                                        2
  74.343494415 = 79.825719296   vmlinuz.old                                    1

================= sda6: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

  78.288391113 = 84.061519872   boot/extlinux/chain.c32                        1
  74.234523773 = 79.708712960   boot/extlinux/extlinux.conf                    1

============== sda6: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux  [/boot/vmlinuz-linux]
root   (hd0,0)
kernel /vmlinuz-linux root=/dev/sda3 ro
initrd /initramfs-linux.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>	<dir>	<type>	<options>	<dump>	<pass>
tmpfs		/tmp	tmpfs	nodev,nosuid	0	0
/dev/sda5 swap swap defaults 0 0
/dev/sda7 / ext4 defaults 0 1
--------------------------------------------------------------------------------

======================= sda7/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: https://wiki.archlinux.org/index.php/Syslinux
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Set to 1 if you always want to display the boot: prompt 
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to http://syslinux.zytor.com/wiki/index.php/Doc/menu
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
	MENU LABEL Arch Linux
	LINUX ../vmlinuz-linux
	APPEND root=/dev/sda3 ro
	INITRD ../initramfs-linux.img

LABEL archfallback
	MENU LABEL Arch Linux Fallback
	LINUX ../vmlinuz-linux
	APPEND root=/dev/sda3 ro
	INITRD ../initramfs-linux-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  86.231025696 = 92.589858816   boot/grub/menu.lst                             1
  86.689651489 = 93.082304512   boot/initramfs-linux-fallback.img              1
  86.662609100 = 93.053267968   boot/initramfs-linux.img                       1
  86.658874512 = 93.049257984   boot/vmlinuz-linux                             1

================= sda7: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

  88.575721741 = 95.107457024   boot/syslinux/syslinux.cfg                     1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

```

Thanks.

---

### Post by oldfred on 2012-03-27
The advantage of a full grub install with a Ubuntu install is you get the other files that are used to auto update grub2's grub.cfg.

 GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts. And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

When you have your grub only partition you only have grub.cfg and change it to editable. You then are responsible for all the updates, but there are ways to minimize all those. But you cannot just use the copy of grub.cfg from an install as it still depends on the scripts and the rest of the system. You can only use the parts that are in /boot/grub or the insmod files and grub.cfg.

I prefer to use my main install as my grub2 in the MBR and just edit 40_custom. Once I learned the grub2 menus I turned off os-prober and primary use grub2 to update current kernel and have a 40_custom for everything else.
But I use a grub only install on all my flash drives and do have them set to boot just about anything on my system.

At the minimum you need to remove all the script as that will not function. You should reduce to just the boot stanza's for each system you want to boot. I am not familar with Arch but it looks like it uses old grub legacy (and may not be installed to correct locations). I would reinstall grub legacy but install it to sda7 or in old grub (hd0,6).

If you do not want to maintain boot stanzas with every system update you can with Ubuntu boot the partition. Ubuntu puts a link to the most current kernel in / (root), and you can directly boot using the link.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number. And change menu entry in the quotes to whatever best describes your partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by avnd on 2012-03-28
@oldfred: Thanks for your time, mate.

> When you have your grub only partition you only have grub.cfg and change it to editable. You then are responsible for all the updates, but there are ways to minimize all those. 

Can you post me some link where I can read up on how to minimize those?

> But you cannot just use the copy of grub.cfg from an install as it still depends on the scripts and the rest of the system. You can only use the parts that are in /boot/grub or the insmod files and grub.cfg.

> I prefer to use my main install as my grub2 in the MBR and just edit 40_custom. Once I learned the grub2 menus I turned off os-prober and primary use grub2 to update current kernel and have a 40_custom for everything else.

I understand that since I don't wish to have any OS at all to be related to GRUB, I don't have the option of using 40_custom. 

Pardon me if I sound stupid. Is it possible to copy these scripts to the 'dedicated GRUB partition' and run them from the GRUB shell to update the grub.cfg?

> I am not familar with Arch but it looks like it uses old grub legacy (and may not be installed to correct locations). I would reinstall grub legacy but install it to sda7 or in old grub (hd0,6).

When I had GRUB Legacy in the GRUB partition, I had it booting all the kernels directly without chainloading. So I did not bother installing a bootloader for my Arch Linux installation. It did come with GRUB Legacy,by default, though.

> If you do not want to maintain boot stanzas with every system update you can with Ubuntu boot the partition. Ubuntu puts a link to the most current kernel in / (root), and you can directly boot using the link.

I first saw this from Ranch hand

I did try it and it worked well. 

> This is part of my grub.cfg on my flash drive (just more of similar entries is missing):

I commented out my default grub.cfg generated by grub-mkconfig (I did not want to delete it for sake of convenience) and used the blueprint you have given in the above quote. Here's a copy of my new grub.cfg.

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
#Aif [ -s $prefix/grubenv ]; then
#A  set have_grubenv=true
#A  load_env
#Afi
#Aset default="0"
#Aif [ "${prev_saved_entry}" ]; then
#A  set saved_entry="${prev_saved_entry}"
#A  save_env saved_entry
#A  set prev_saved_entry=
#A  save_env prev_saved_entry
#A  set boot_once=true
#Afi

#Afunction savedefault {
#A  if [ -z "${boot_once}" ]; then
#A    saved_entry="${chosen}"
#A    save_env saved_entry
#A  fi
#A}

#Afunction recordfail {
#A  set recordfail=1
#A  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
#A}

#Afunction load_video {
#A  insmod vbe
#A  insmod vga
#A  insmod video_bochs
#A  insmod video_cirrus
#A}

#Ainsmod part_msdos
#Ainsmod ext2
#Aset root='(hd0,msdos8)'
#Asearch --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#Aif loadfont /usr/share/grub/unicode.pf2 ; then
#A  set gfxmode=auto
#A  load_video
#A  insmod gfxterm
#A  insmod part_msdos
#A  insmod ext2
#A  set root='(hd0,msdos8)'
#A  search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#A  set locale_dir=($root)/boot/grub/locale
#A  set lang=en_IN
#A  insmod gettext
#Afi
#Aterminal_output gfxterm
#Aif [ "${recordfail}" = 1 ]; then
#A  set timeout=-1
#Aelse
#A  set timeout=10
#Afi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
#Aset menu_color_normal=white/black
#Aset menu_color_highlight=black/light-gray
#Aif background_color 44,0,30; then
#A  clear
#Afi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
#Aif [ ${recordfail} != 1 ]; then
#A  if [ -e ${prefix}/gfxblacklist.txt ]; then
#A    if hwmatch ${prefix}/gfxblacklist.txt 3; then
#A      if [ ${match} = 0 ]; then
#A        set linux_gfx_mode=keep
#A      else
#A        set linux_gfx_mode=text
#A      fi
#A    else
#A      set linux_gfx_mode=text
#A    fi
#A  else
#A    set linux_gfx_mode=keep
#A  fi
#Aelse
#A  set linux_gfx_mode=text
#Afi
#Aexport linux_gfx_mode
#Aif [ "$linux_gfx_mode" != "text" ]; then load_video; fi
#Amenuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
#A	recordfail
#A	set gfxpayload=$linux_gfx_mode
#A	insmod gzio
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos8)'
#A	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#A	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=68d95051-60d3-4d3b-83da-2a2cfcbee14b ro   quiet splash vt.handoff=7
#A	initrd	/boot/initrd.img-3.0.0-12-generic
#A}
#Amenuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
#A	recordfail
#A	insmod gzio
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos8)'
#A	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#A	echo	'Loading Linux 3.0.0-12-generic ...'
#A	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=68d95051-60d3-4d3b-83da-2a2cfcbee14b ro recovery nomodeset 
#A	echo	'Loading initial ramdisk ...'
#A	initrd	/boot/initrd.img-3.0.0-12-generic
#A}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
#Amenuentry "Memory test (memtest86+)" {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos8)'
#A	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#A	linux16	/boot/memtest86+.bin
#A}
#Amenuentry "Memory test (memtest86+, serial console 115200)" {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos8)'
#A	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#A	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
#A}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
#Amenuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
#A	insmod part_msdos
#A	insmod ntfs
#A	set root='(hd0,msdos2)'
#A	search --no-floppy --fs-uuid --set=root 0D9CAB5E0372A8B0
#A	chainloader +1
#A}
#Amenuentry "Ubuntu, with Linux 3.0.0-16-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos6)'
#A	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
#A	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro quiet splash vt.handoff=7
#A	initrd /boot/initrd.img-3.0.0-16-generic
#A}
#Amenuentry "Ubuntu, with Linux 3.0.0-16-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos6)'
#A	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
#A	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset
#A	initrd /boot/initrd.img-3.0.0-16-generic
#A}
#Amenuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos6)'
#A	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
#A	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro quiet splash vt.handoff=7
#A	initrd /boot/initrd.img-3.0.0-12-generic
#A}
#Amenuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos6)'
#A	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
#A	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset
#A	initrd /boot/initrd.img-3.0.0-12-generic
#A}
#Amenuentry "Arch (on /dev/sda7)" --class gnu-linux --class gnu --class os {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos7)'
#A	search --no-floppy --fs-uuid --set=root e05b18c4-e84b-4a50-8a3c-ba2f7028857d
#A	linux /boot/vmlinuz-linux root=/dev/sda7
#A	initrd /boot/initramfs-linux.img
#A}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
#Aif [ -f  $prefix/custom.cfg ]; then
#A  source $prefix/custom.cfg;
#Afi
### END /etc/grub.d/41_custom ###

set default=0
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Lubuntu_Latest Kernel Boot" {
	set root=(hd0,6)
	linux /vmlinuz root=/dev/sda6 ro quiet splash
	initrd /initrd.img
}

menuentry "Lubuntu" --class gnu-linux --class gnu --class os {
      insmod part_msdos
      insmod ext2
      set root='(hd0,msdos6)'
      search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
      linux /boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472$
      initrd /boot/initrd.img-3.0.0-16-generic
}

menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
      insmod part_msdos
      insmod ntfs
      set root='(hd0,msdos2)'
      search --no-floppy --fs-uuid --set=root 0D9CAB5E0372A8B0
      chainloader +1
}
```

I added 2 entries for Lubuntu. One was a copy from the one created by grub-mkconfig. The other was the 'Ranch hand' one you had suggested. The 'Ranch hand' entry boots fine into Lubuntu. But I don't see the entry I had copied from the original 'grub-mkconfig generated' file. 

I would like some help on 2 issues.

1. Why do I not see the menu-entry "Lubuntu" in my menu choice?

2. I still have some error message right before the GRUB menu choice shows up. I'm having trouble pausing my screen during the message. After many tries, I captured part of the message with the 'pause' button. It read the following
```
error: $
error: syntax error
error: Incorrect command
error: syntax error
```

Can any one tell me why I get the above message and why?

The following is a copy of my bootinfoscript after correcting the grub.cfg file.

```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 148372264 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Arch Linux ()
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  83 Linux
/dev/sda2    *        206,848    52,635,647    52,428,800   7 NTFS / exFAT / HPFS
/dev/sda3          52,635,648   136,521,727    83,886,080   7 NTFS / exFAT / HPFS
/dev/sda4         136,523,774   234,440,703    97,916,930   5 Extended
/dev/sda5         136,523,776   138,620,927     2,097,152  82 Linux swap / Solaris
/dev/sda6         138,622,976   180,566,015    41,943,040  83 Linux
/dev/sda7         180,568,064   201,539,583    20,971,520  83 Linux
/dev/sda8         201,541,632   234,440,703    32,899,072  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        70765486-1284-4c2f-aeaf-acf7d3a38e89   ext4       BOOT
/dev/sda2        0D9CAB5E0372A8B0                       ntfs       SEVEN
/dev/sda3        336C11E97D14234A                       ntfs       DATANTFS
/dev/sda5        61688e5f-26e5-4a8a-a7be-6a7c6f861b3f   swap       SWAP
/dev/sda6        74965cc2-9fb2-4a0f-9edf-9bde9472fb0a   ext4       
/dev/sda7        e05b18c4-e84b-4a50-8a3c-ba2f7028857d   ext4       ARCH_E16
/dev/sda8        dc8c4beb-e5f2-43eb-ac25-963617f93d5a   ext4       DATAEXT4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
#Aif [ -s $prefix/grubenv ]; then
#A  set have_grubenv=true
#A  load_env
#Afi
#Aset default="0"
#Aif [ "${prev_saved_entry}" ]; then
#A  set saved_entry="${prev_saved_entry}"
#A  save_env saved_entry
#A  set prev_saved_entry=
#A  save_env prev_saved_entry
#A  set boot_once=true
#Afi

#Afunction savedefault {
#A  if [ -z "${boot_once}" ]; then
#A    saved_entry="${chosen}"
#A    save_env saved_entry
#A  fi
#A}

#Afunction recordfail {
#A  set recordfail=1
#A  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
#A}

#Afunction load_video {
#A  insmod vbe
#A  insmod vga
#A  insmod video_bochs
#A  insmod video_cirrus
#A}

#Ainsmod part_msdos
#Ainsmod ext2
#Aset root='(hd0,msdos8)'
#Asearch --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#Aif loadfont /usr/share/grub/unicode.pf2 ; then
#A  set gfxmode=auto
#A  load_video
#A  insmod gfxterm
#A  insmod part_msdos
#A  insmod ext2
#A  set root='(hd0,msdos8)'
#A  search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#A  set locale_dir=($root)/boot/grub/locale
#A  set lang=en_IN
#A  insmod gettext
#Afi
#Aterminal_output gfxterm
#Aif [ "${recordfail}" = 1 ]; then
#A  set timeout=-1
#Aelse
#A  set timeout=10
#Afi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
#Aset menu_color_normal=white/black
#Aset menu_color_highlight=black/light-gray
#Aif background_color 44,0,30; then
#A  clear
#Afi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
#Aif [ ${recordfail} != 1 ]; then
#A  if [ -e ${prefix}/gfxblacklist.txt ]; then
#A    if hwmatch ${prefix}/gfxblacklist.txt 3; then
#A      if [ ${match} = 0 ]; then
#A        set linux_gfx_mode=keep
#A      else
#A        set linux_gfx_mode=text
#A      fi
#A    else
#A      set linux_gfx_mode=text
#A    fi
#A  else
#A    set linux_gfx_mode=keep
#A  fi
#Aelse
#A  set linux_gfx_mode=text
#Afi
#Aexport linux_gfx_mode
#Aif [ "$linux_gfx_mode" != "text" ]; then load_video; fi
#Amenuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
#A	recordfail
#A	set gfxpayload=$linux_gfx_mode
#A	insmod gzio
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos8)'
#A	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#A	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=68d95051-60d3-4d3b-83da-2a2cfcbee14b ro   quiet splash vt.handoff=7
#A	initrd	/boot/initrd.img-3.0.0-12-generic
#A}
#Amenuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
#A	recordfail
#A	insmod gzio
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos8)'
#A	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#A	echo	'Loading Linux 3.0.0-12-generic ...'
#A	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=68d95051-60d3-4d3b-83da-2a2cfcbee14b ro recovery nomodeset 
#A	echo	'Loading initial ramdisk ...'
#A	initrd	/boot/initrd.img-3.0.0-12-generic
#A}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
#Amenuentry "Memory test (memtest86+)" {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos8)'
#A	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#A	linux16	/boot/memtest86+.bin
#A}
#Amenuentry "Memory test (memtest86+, serial console 115200)" {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos8)'
#A	search --no-floppy --fs-uuid --set=root 68d95051-60d3-4d3b-83da-2a2cfcbee14b
#A	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
#A}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
#Amenuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
#A	insmod part_msdos
#A	insmod ntfs
#A	set root='(hd0,msdos2)'
#A	search --no-floppy --fs-uuid --set=root 0D9CAB5E0372A8B0
#A	chainloader +1
#A}
#Amenuentry "Ubuntu, with Linux 3.0.0-16-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos6)'
#A	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
#A	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro quiet splash vt.handoff=7
#A	initrd /boot/initrd.img-3.0.0-16-generic
#A}
#Amenuentry "Ubuntu, with Linux 3.0.0-16-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos6)'
#A	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
#A	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset
#A	initrd /boot/initrd.img-3.0.0-16-generic
#A}
#Amenuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos6)'
#A	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
#A	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro quiet splash vt.handoff=7
#A	initrd /boot/initrd.img-3.0.0-12-generic
#A}
#Amenuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos6)'
#A	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
#A	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset
#A	initrd /boot/initrd.img-3.0.0-12-generic
#A}
#Amenuentry "Arch (on /dev/sda7)" --class gnu-linux --class gnu --class os {
#A	insmod part_msdos
#A	insmod ext2
#A	set root='(hd0,msdos7)'
#A	search --no-floppy --fs-uuid --set=root e05b18c4-e84b-4a50-8a3c-ba2f7028857d
#A	linux /boot/vmlinuz-linux root=/dev/sda7
#A	initrd /boot/initramfs-linux.img
#A}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
#Aif [ -f  $prefix/custom.cfg ]; then
#A  source $prefix/custom.cfg;
#Afi
### END /etc/grub.d/41_custom ###

set default=0
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Lubuntu_Latest Kernel Boot" {
	set root=(hd0,6)
	linux /vmlinuz root=/dev/sda6 ro quiet splash
	initrd /initrd.img
}

menuentry "Lubuntu" --class gnu-linux --class gnu --class os {
      insmod part_msdos
      insmod ext2
      set root='(hd0,msdos6)'
      search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
      linux /boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472$
      initrd /boot/initrd.img-3.0.0-16-generic
}

menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
      insmod part_msdos
      insmod ntfs
      set root='(hd0,msdos2)'
      search --no-floppy --fs-uuid --set=root 0D9CAB5E0372A8B0
      chainloader +1
}


--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.009088516 = 0.009758720    boot/grub/core.img                             1
   0.011727333 = 0.012592128    boot/grub/grub.cfg                             1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 74965cc2-9fb2-4a0f-9edf-9bde9472fb0a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 0D9CAB5E0372A8B0
	chainloader +1
}
menuentry "Arch (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root e05b18c4-e84b-4a50-8a3c-ba2f7028857d
	linux /boot/vmlinuz-linux root=/dev/sda7
	initrd /boot/initramfs-linux.img
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=74965cc2-9fb2-4a0f-9edf-9bde9472fb0a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=61688e5f-26e5-4a8a-a7be-6a7c6f861b3f none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda6/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  70.749435425 = 75.966627840   boot/grub/core.img                             1
  78.285739899 = 84.058673152   boot/grub/grub.cfg                             1
  67.332126617 = 72.297320448   boot/initrd.img-3.0.0-12-generic               2
  68.147602081 = 73.172930560   boot/initrd.img-3.0.0-16-generic               2
  74.343494415 = 79.825719296   boot/vmlinuz-3.0.0-12-generic                  1
  66.628391266 = 71.541690368   boot/vmlinuz-3.0.0-16-generic                  2
  68.147602081 = 73.172930560   initrd.img                                     2
  67.332126617 = 72.297320448   initrd.img.old                                 2
  66.628391266 = 71.541690368   vmlinuz                                        2
  74.343494415 = 79.825719296   vmlinuz.old                                    1

================= sda6: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

  78.288391113 = 84.061519872   boot/extlinux/chain.c32                        1
  74.234523773 = 79.708712960   boot/extlinux/extlinux.conf                    1

============== sda6: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux  [/boot/vmlinuz-linux]
root   (hd0,0)
kernel /vmlinuz-linux root=/dev/sda3 ro
initrd /initramfs-linux.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>	<dir>	<type>	<options>	<dump>	<pass>
tmpfs		/tmp	tmpfs	nodev,nosuid	0	0
/dev/sda5 swap swap defaults 0 0
/dev/sda7 / ext4 defaults 0 1
--------------------------------------------------------------------------------

======================= sda7/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: https://wiki.archlinux.org/index.php/Syslinux
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Set to 1 if you always want to display the boot: prompt 
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to http://syslinux.zytor.com/wiki/index.php/Doc/menu
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
	MENU LABEL Arch Linux
	LINUX ../vmlinuz-linux
	APPEND root=/dev/sda3 ro
	INITRD ../initramfs-linux.img

LABEL archfallback
	MENU LABEL Arch Linux Fallback
	LINUX ../vmlinuz-linux
	APPEND root=/dev/sda3 ro
	INITRD ../initramfs-linux-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  86.231025696 = 92.589858816   boot/grub/menu.lst                             1
  86.689651489 = 93.082304512   boot/initramfs-linux-fallback.img              1
  86.662609100 = 93.053267968   boot/initramfs-linux.img                       1
  86.658874512 = 93.049257984   boot/vmlinuz-linux                             1

================= sda7: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

  88.575721741 = 95.107457024   boot/syslinux/syslinux.cfg                     1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

```

Can anyone tell me if there is any simple way for me to capture the error message I get before the GRUB menu shows up?

Thanks.

---

### Post by oldfred on 2012-03-28
I do not know how to capture errors while booting. I think some do it in a virtual memory system and then can get them. I have used my camera to record the boot as sometimes it does go by quickly. You may be able to then extract an image from a video.

It looks like you have a $ at the end of the UUID in the stanza that is not working. New grub with 1.99 has become more sensitive to typos. I think even spaces at the end of a line can cause issues.

When I suggest minimizing changes, it is boot entries like Ranch Hand's version or chainloading. Then grub.cfg does not change. 

I might have just copied grub.cfg to grub.cfg.backup and deleted all the stuff you commented out.

---

### Post by avnd on 2012-04-03
> I might have just copied grub.cfg to grub.cfg.backup and deleted all the stuff you commented out.

That seems much simpler, thanks :)

For the past few days, I been googling to find ways to theme my GRUB 2, oldfred. But all the guides I come across, require me to use the scripts that are in folders inside the OS used to install GRUB.

In my situation, since I installed GRUB from a Live CD, I don't have those folders (that's exactly what I want). But I would like to have themes for my GRUB. 

I actually got a link to a nice guide called 'The Definitive Guide to Theming GRUB 2' by Towheed Mohammed. But instructions in the book involve changes to the scripts generating grub.cfg. Can someone please post me some links which describe how to do this with a 'dedicated' GRUB partition?

I would also like a little clarification on something else. Now, if GRUB ultimately reads stuff from grub.cfg, is it possible to just copy the files required for theming into the 'dedicated GRUB partition' and make changes to grub.cfg to use them?

Thanks.

P.S. Now, that the problem with which I started this thread has been solved (or rather, I have found an alternative) and the questions I have now are moving away from the thread title, do I post this question in a new thread?

The setup I have ultimately settled with now is to have a GRUB on the MBR pointing to the files in the 'dedicated' partition. From there, I guess I'm going to chainload to another GRUB installed on the individual partitions and set the wait time in those to zero (or something like that), so that the transition does not affect the  aesthetics. I guess now when I update GRUB from within the specific OS, only the GRUB at the partition gets updated. The main GRUB remains unaffected.

---

### Post by oldfred on 2012-04-03
I do not use theming. I just want it to boot quickly.
Is this the links you had on theming?
Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

Since it is sudo update-grub that builds a grub.cfg and it looks like most of the theme files are normally in /boot/grub you then should be able to copy what the script creates for theming into grub.cfg. 

Just the opposite of what I told you to undo from the grub.cfg, but just manually add every file and make sure the path & files it wants are really there.

---

### Post by avnd on 2012-04-03
> Is this the links you had on theming?

@oldfred: Yes. Those were the links, mate. 

> Since it is sudo update-grub that builds a grub.cfg and it looks like most of the theme files are normally in /boot/grub you then should be able to copy what the script creates for theming into grub.cfg. 

Since I can find no instructions on how to edit grub.cfg directly, I guess I'm going to install GRUB and Ubuntu on a virtual machine to find what is getting changed in the grub.cfg for the necessary changes in do in the directed files. 

If anyone can direct me to instructions which show how to effect those changes by editing grub.cfg directly, it'll be wonderful.

Thanks for your reply, Oldfred.

I will get back on how I did it or where I keep failing after I try it.

P.S. One big restriction I have is that I only have 100 MB allotted for the 'dedicated GRUB partition'. I don't know if it's too small to accommodate the theming files.

---

