---
title: "GRUB won't boot new kernel!"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by Shmook on 2011-10-29
So I've installed GRUB2 through Lubuntu 11.10, using Grub-Customizer, to the MBR. Everythings great, it's found all my OS's, no problem.

Now though, one OS (ArchBang) updated its kernel! I've gone back to Lubuntu, used the "update-grub" command, looked through grub-customizer, as well as ubuntu-tweak to delete the old kernels of AB, to no avail. I've been looking but haven't found a solution that works for me -- any ideas? please?

---

### Post by cogier on 2011-10-29
I had something similar when I installed Kubuntu 11.10 along side Ubuntu 10.04 LTS. All efforts in Ubuntu to sort GRUB out failed. 

I don't know but I suspect that ArchBang has created GRUB and you need to change it from inside ArchBang.

If you can't access ArchBang then you need to follow this [http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099").

This is quite a lot of work but it did do the trick for me.

---

### Post by Shmook on 2011-10-29
dyyaum! Why do they have to make such an enticing distro like archbang so difficult to have fun with! I can boot it -- it just runs the old 2.6....whatever kernel, after having just installed 3.0.4~~~

Anyway thanks for the reply, I'll check out that article.

---

### Post by oldfred on 2011-10-29
What boot loader does Archbang use. If grub legacy, just install its boot loader to the archbang root partition and add a chainload entry to 40_custom. If it uses grub2 you may have to run the grub updates in both systems so Ubuntu can find the new entries in Archbang's grub menu.

If you want to know what is where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by garvinrick4 on 2011-10-29
@shmook
Would be nice to see your boot_info_script as per oldfred just to see what arch did
anywhich way, thanks shmook.

---

### Post by Shmook on 2011-10-29
Sorry, I got involved in my other issue, Sabayon and how it treats my NTFS drive. ANYWAY:
```
             Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 11 Katya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda7 and looks at sector 289537332 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #7 
                       for /boot/grub/menu.lst.
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   153,597,464   153,597,402   7 NTFS / exFAT / HPFS
/dev/sda2         153,597,952   194,545,663    40,947,712  83 Linux
/dev/sda3         194,547,211   310,713,164   116,165,954   f W95 Extended (LBA)
/dev/sda5         194,547,213   258,019,964    63,472,752  83 Linux
/dev/sda6    *    258,020,028   288,736,244    30,716,217  83 Linux
/dev/sda7         288,736,308   310,713,164    21,976,857  83 Linux
/dev/sda4         310,713,165   312,576,704     1,863,540  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   586,072,063   586,070,016   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6E9852089851CF69                       ntfs       a1 xp
/dev/sda2        5c59838d-daed-405e-b6c7-1eff85362697   ext4       
/dev/sda4        e5d72faf-dc56-433d-8250-6e6c0e1330b3   swap       
/dev/sda5        1bba4f20-0f67-487d-a755-c5a92c6bfd0a   ext4       
/dev/sda6        99aa83b4-128f-4832-8607-1b9f2bfff089   ext4       
/dev/sda7        44091f86-80ce-4580-879e-34d564072977   ext4       
/dev/sdb1        2EB43EE1B43EAAEB                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,relatime,barrier=1,data=ordered)
/dev/sdb1        /media/2EB43EE1B43EAAEB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
--------------------------------------------------------------------------------

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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 5c59838d-daed-405e-b6c7-1eff85362697
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 5c59838d-daed-405e-b6c7-1eff85362697
set locale_dir=($root)/boot/grub/locale
set lang=en_AG
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 5c59838d-daed-405e-b6c7-1eff85362697
insmod jpeg
if background_image /boot/grub/vlcsnap-2010-12-28-04h29m08s212.jpg; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
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
menuentry "Linux Mint 11, 2.6.38-12-generic (/dev/sda2)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5c59838d-daed-405e-b6c7-1eff85362697
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=5c59838d-daed-405e-b6c7-1eff85362697 ro  vga=792  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry "Linux Mint 11, 2.6.38-12-generic (/dev/sda2) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5c59838d-daed-405e-b6c7-1eff85362697
	echo	'Loading Linux 2.6.38-12-generic ...'
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=5c59838d-daed-405e-b6c7-1eff85362697 ro single  vga=792
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-12-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/10_os-prober_proxy ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 6E9852089851CF69
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 99aa83b4-128f-4832-8607-1b9f2bfff089
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=99aa83b4-128f-4832-8607-1b9f2bfff089 ro vga=792 splash quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 99aa83b4-128f-4832-8607-1b9f2bfff089
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=99aa83b4-128f-4832-8607-1b9f2bfff089 ro recovery nomodeset vga=792 splash
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Sabayon GNU/Linux, with Linux x86-3.0.0-sabayon (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1bba4f20-0f67-487d-a755-c5a92c6bfd0a
	linux /boot/kernel-genkernel-x86-3.0.0-sabayon ro init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=us domdadm resume=swap:UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 real_resume=UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 root=UUID=1bba4f20-0f67-487d-a755-c5a92c6bfd0a docrypt
	initrd /boot/initramfs-genkernel-x86-3.0.0-sabayon
}
menuentry "Sabayon GNU/Linux, with Linux x86-3.0.0-sabayon (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1bba4f20-0f67-487d-a755-c5a92c6bfd0a
	linux /boot/kernel-genkernel-x86-3.0.0-sabayon ro single init_opts=single init=/linuxrc splash=verbose,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=us domdadm resume=swap:UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 real_resume=UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 root=UUID=1bba4f20-0f67-487d-a755-c5a92c6bfd0a docrypt
	initrd /boot/initramfs-genkernel-x86-3.0.0-sabayon
}
menuentry "ArchBang Linux (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 44091f86-80ce-4580-879e-34d564072977
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/44091f86-80ce-4580-879e-34d564072977 ro quiet resume=/dev/sda4
	initrd /boot/kernel26.img
}
menuentry "ArchBang Linux Fallback (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 44091f86-80ce-4580-879e-34d564072977
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/44091f86-80ce-4580-879e-34d564072977 ro
	initrd /boot/kernel26-fallback.img
}
### END /etc/grub.d/10_os-prober_proxy ###

### BEGIN /etc/grub.d/20_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/20_custom ###

### BEGIN /etc/grub.d/30_lupin ###
### END /etc/grub.d/30_lupin ###

### BEGIN /etc/grub.d/40_linux_xen ###
### END /etc/grub.d/40_linux_xen ###

### BEGIN /etc/grub.d/41_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5c59838d-daed-405e-b6c7-1eff85362697
	linux16	/boot/memtest86+.bin
}
### END /etc/grub.d/41_memtest86+_proxy ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=5c59838d-daed-405e-b6c7-1eff85362697 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 none            swap    sw              0       0
/dev/sda1	/media/c	ntfs	defaults	0	0
/dev/sdb1	/media/d	ntfs	defaults	0	0

--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  87.391899109 = 93.836337152   boot/grub/core.img                             1
  77.869930267 = 83.612200960   boot/grub/grub.cfg                             1
  76.295898438 = 81.922097152   boot/initrd.img-2.6.38-11-generic              3
  78.287448883 = 84.060508160   boot/initrd.img-2.6.38-12-generic              2
  73.998870850 = 79.455682560   boot/initrd.img-2.6.38-8-generic               3
  74.319644928 = 79.800111104   boot/vmlinuz-2.6.38-11-generic                 1
  76.096988678 = 81.708519424   boot/vmlinuz-2.6.38-12-generic                 1
  87.373512268 = 93.816594432   boot/vmlinuz-2.6.38-8-generic                  1
  78.287448883 = 84.060508160   initrd.img                                     2
  76.295898438 = 81.922097152   initrd.img.old                                 3
  76.096988678 = 81.708519424   vmlinuz                                        1
  74.319644928 = 79.800111104   vmlinuz.old                                    1

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_fonts ###
### END /etc/grub.d/00_fonts ###

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="${saved_entry}"
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 1bba4f20-0f67-487d-a755-c5a92c6bfd0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  # vga= is deprecated, grub2 handles this just fine
  # making grub2 res == linux fb res
  set gfxpayload=keep
  insmod gfxterm
fi
terminal_output gfxterm
if sleep --interruptible 0 ; then
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_distro_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 1bba4f20-0f67-487d-a755-c5a92c6bfd0a
insmod png
if background_image /boot/grub/default-splash.png ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_distro_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Sabayon GNU/Linux, with Linux x86-3.0.0-sabayon' --class sabayon --class gnu-linux --class gnu --class os {
	load_video
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1bba4f20-0f67-487d-a755-c5a92c6bfd0a
	echo	'Loading Linux x86-3.0.0-sabayon ...'
	linux	/boot/kernel-genkernel-x86-3.0.0-sabayon ro  init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=us domdadm resume=swap:UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 real_resume=UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 root=UUID=1bba4f20-0f67-487d-a755-c5a92c6bfd0a docrypt 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initramfs-genkernel-x86-3.0.0-sabayon
}
menuentry 'Sabayon GNU/Linux, with Linux x86-3.0.0-sabayon (recovery mode)' --class sabayon --class gnu-linux --class gnu --class os {
	load_video
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1bba4f20-0f67-487d-a755-c5a92c6bfd0a
	echo	'Loading Linux x86-3.0.0-sabayon ...'
	linux	/boot/kernel-genkernel-x86-3.0.0-sabayon ro single init_opts=single  init=/linuxrc splash=verbose,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=us domdadm resume=swap:UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 real_resume=UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 root=UUID=1bba4f20-0f67-487d-a755-c5a92c6bfd0a docrypt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initramfs-genkernel-x86-3.0.0-sabayon
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 6E9852089851CF69
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Linux Mint 11, 2.6.38-11-generic (/dev/sda2) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5c59838d-daed-405e-b6c7-1eff85362697
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=5c59838d-daed-405e-b6c7-1eff85362697 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Linux Mint 11, 2.6.38-11-generic (/dev/sda2) -- recovery mode (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5c59838d-daed-405e-b6c7-1eff85362697
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=5c59838d-daed-405e-b6c7-1eff85362697 ro single
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 99aa83b4-128f-4832-8607-1b9f2bfff089
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=99aa83b4-128f-4832-8607-1b9f2bfff089 ro vga=792 quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 99aa83b4-128f-4832-8607-1b9f2bfff089
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=99aa83b4-128f-4832-8607-1b9f2bfff089 ro recovery nomodeset vga=792
	initrd /boot/initrd.img-3.0.0-12-generic
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Thu Oct 20 13:48:59 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=1bba4f20-0f67-487d-a755-c5a92c6bfd0a /                       ext4    defaults        1 1
UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sdb1		/media/d		ntfs-3g	defaults	0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 112.994520664 = 121.326942720  boot/grub/core.img                             1
 112.994528294 = 121.326950912  boot/grub/grub.cfg                             1
  94.899893284 = 101.897984512  boot/grub/stage2                               1
  92.911413670 = 99.762870784   boot/initramfs-genkernel-x86-3.0.0-sabayon     1

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
search --no-floppy --fs-uuid --set=root 99aa83b4-128f-4832-8607-1b9f2bfff089
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 99aa83b4-128f-4832-8607-1b9f2bfff089
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
insmod part_msdos
insmod ntfs
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 2EB43EE1B43EAAEB
insmod png
if background_image /pix/Elbe.png; then
  set color_normal=light-gray/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 99aa83b4-128f-4832-8607-1b9f2bfff089
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=99aa83b4-128f-4832-8607-1b9f2bfff089 ro  vga=792 splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 99aa83b4-128f-4832-8607-1b9f2bfff089
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=99aa83b4-128f-4832-8607-1b9f2bfff089 ro recovery nomodeset  vga=792 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 6E9852089851CF69
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Linux Mint 11, 2.6.38-11-generic (/dev/sda2) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5c59838d-daed-405e-b6c7-1eff85362697
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=5c59838d-daed-405e-b6c7-1eff85362697 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Linux Mint 11, 2.6.38-11-generic (/dev/sda2) -- recovery mode (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5c59838d-daed-405e-b6c7-1eff85362697
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=5c59838d-daed-405e-b6c7-1eff85362697 ro single
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Sabayon GNU/Linux, with Linux x86-3.0.0-sabayon (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1bba4f20-0f67-487d-a755-c5a92c6bfd0a
	linux /boot/kernel-genkernel-x86-3.0.0-sabayon ro init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=us domdadm resume=swap:UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 real_resume=UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 root=UUID=1bba4f20-0f67-487d-a755-c5a92c6bfd0a docrypt
	initrd /boot/initramfs-genkernel-x86-3.0.0-sabayon
}
menuentry "Sabayon GNU/Linux, with Linux x86-3.0.0-sabayon (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1bba4f20-0f67-487d-a755-c5a92c6bfd0a
	linux /boot/kernel-genkernel-x86-3.0.0-sabayon ro single init_opts=single init=/linuxrc splash=verbose,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=us domdadm resume=swap:UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 real_resume=UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 root=UUID=1bba4f20-0f67-487d-a755-c5a92c6bfd0a docrypt
	initrd /boot/initramfs-genkernel-x86-3.0.0-sabayon
}
menuentry "ArchBang Linux (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 44091f86-80ce-4580-879e-34d564072977
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/44091f86-80ce-4580-879e-34d564072977 ro quiet resume=/dev/sda4
	initrd /boot/kernel26.img
}
menuentry "ArchBang Linux Fallback (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 44091f86-80ce-4580-879e-34d564072977
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/44091f86-80ce-4580-879e-34d564072977 ro
	initrd /boot/kernel26-fallback.img
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
UUID=99aa83b4-128f-4832-8607-1b9f2bfff089 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=ba6ef235-fa6e-4775-a327-d2a7c2310710 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1	/media/c	ntfs	defaults	0	0
/dev/sdb1	/media/d	ntfs	defaults	0	0

--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 135.469213486 = 145.458960384  boot/grub/core.img                             1
 123.904596329 = 133.041547264  boot/grub/grub.cfg                             1
 125.804029465 = 135.081048064  boot/initrd.img-3.0.0-12-generic               2
 131.194101334 = 140.868593664  boot/vmlinuz-3.0.0-12-generic                  1
 125.804029465 = 135.081048064  initrd.img                                     2
 131.194101334 = 140.868593664  vmlinuz                                        1

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
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

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

# (0) ArchBang Linux
title  ArchBang Linux
root   (hd0,6)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/44091f86-80ce-4580-879e-34d564072977 ro quiet resume=/dev/sda4   
initrd /boot/kernel26.img

# (1) ArchBang Linux fallback (useful if you change your hard disk/mainboard)
title  ArchBang Linux Fallback
root   (hd0,6)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/44091f86-80ce-4580-879e-34d564072977 ro
initrd /boot/kernel26-fallback.img

# (2) Optional entry for Windoze
#title Windoze
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0
UUID=44091f86-80ce-4580-879e-34d564072977 / ext4 defaults 0 1
UUID=e5d72faf-dc56-433d-8250-6e6c0e1330b3 swap swap defaults 0 0
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
PROMPT 0        # Change to 1 if you do not want to use a menu
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
	LINUX ../vmlinuz26
	APPEND root=/dev/sda3 ro
	INITRD ../kernel26.img

LABEL archfallback
	MENU LABEL Arch Linux Fallback
	LINUX ../vmlinuz26
	APPEND root=/dev/sda3 ro
	INITRD ../kernel26-fallback.img

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

 145.806550980 = 156.558592000  boot/grub/menu.lst                             1
 138.062253952 = 148.243216384  boot/grub/stage2                               1
 138.320867538 = 148.520900608  boot/kernel26-fallback.img                     1
 138.312677383 = 148.512106496  boot/kernel26.img                              1
 146.059282303 = 156.829960192  boot/vmlinuz26                                 1

================= sda7: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 145.828142166 = 156.581775360  boot/syslinux/syslinux.cfg                     1

=============================== StdErr Messages: ===============================

unlzma: (stdin): Compressed data is corrupt
  No volume groups found
mdadm: No arrays found in config file or automatically
```
I'm sure you didn't need that in its entirety, but there ya go. And yeah surprisingly ArchBang does use Legacy...

---

### Post by Shmook on 2011-10-29
^and also -- I usually just install GRUB to MBR but if I'm saving it to a partition does it matter if it's extended or primary? Based on what I've read it doesn't make a difference, though some folks seem to prefer having a "/boot" partition -- which lately doesn't seem like too bad an idea

---

### Post by amjjawad on 2011-10-29
> **Shmook said:**
> ^and also -- I usually just install GRUB to MBR but if I'm saving it to a partition does it matter if it's extended or primary? Based on what I've read it doesn't make a difference, though some folks seem to prefer having a "/boot" partition -- which lately doesn't seem like too bad an idea

I have already explained that to you on your other thread ;)

---

### Post by Shmook on 2011-10-29
@amjjawad...whoops #-o I forgot we'd covered that. And yeah these were similar cases, but different instances yknow.

@oldfred -- do I read you correctly -- I should ultimately use legacy instead of grub2? And I'm afraid to say I don't quite understand. I recall chainloading to boot Winders before using legacy...but chainloading a file? Sorry but if you could elaborate a bit please.

---

### Post by oldfred on 2011-10-29
Mint is the boot loader you have installed, so if you are updating grub in Ubuntu it never be seen. You need to update grub in  Mint or install Ubuntu's boot loader to the MBR.

I do not recommend a partition /boot for standard desktops. You have to have one for every install (cannot be shared) and it makes reinstall of grub more complicated.

You want grub2 as your boot loader. But with many installs it can get confusing which is booting and which is updating. I turn off os-prober and add manual entries. You chainload to any system that uses grub legacy as then you load its menu.lst and have the updated kernels. If using grub2 you put a boot stanza that boots the partition as Debian types put links to the most current kernel in / to boot from.

This was my old entry. I currently do not boot any legacy grub. 

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}
menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by amjjawad on 2011-10-29
> **Shmook said:**
> @amjjawad...whoops #-o I forgot we'd covered that. And yeah these were similar cases, but different instances yknow.

Concept is the same. Check your other thread ;)

> @oldfred -- do I read you correctly -- I should ultimately use legacy instead of grub2? And I'm afraid to say I don't quite understand. I recall chainloading to boot Winders before using legacy...but chainloading a file? Sorry but if you could elaborate a bit please.

I think oldfred meant that you need to edit your GRUB2 Configuration file. oldfred is much better than me in these stuff so you are with very capable hands :)

---

### Post by beew on 2011-10-29
> **oldfred said:**
> What boot loader does Archbang use. If grub legacy, just install its boot loader to the archbang root partition and add a chainload entry to 40_custom. If it uses grub2 you may have to run the grub updates in both systems so Ubuntu can find the new entries in Archbang's grub menu.


Doesn't matter whether it is grub legacy or grub2, installing to root partition should be fine. I multiboot several *buntus and they all use grub2. I don't have to update grub in all of them, only in the main Natty install which controls boot. 

@OP don't know about AB but some distros like Fedora actually has an option of not installing bootloader at all.

---

### Post by amjjawad on 2011-10-29
> **beew said:**
> i don't have to update grub in all of them, only in the main install which controls boot. 

+1

---

### Post by Shmook on 2011-10-29
You're right amjjawad -- after thinking about it for a minute it is pretty much identical -- both times AB had not been recognized for some reason. What confused me (and led me to think this was a separate problem) was that I got it to be recognized by Ubuntu by using GCust to install to the MBR, so it felt like the cause must be different. Silly me.

And oldfred -- first thanks very much -- and by Mint being my bootloader -- is that indicated by the boot flag - the one I never know what to do with while using gParted or installing Puppy? And also should I change that? If I were to install a different distro on sda2 for instance -- well I guess I'd just have to rewrite to the MBR...

And yes that's how I came to this situation -- wrote from Ubuntu, sda5, to the MBR using GrubCustomizer. So now -- using Mint -- I should remove the ArchBang entry from os-prober, and manually type in the hdd and partition as you showed. I'm guessing it'll look something like:

menuentry "ArchBang" {
set root=(hd0,6)  ---->if the drive/partition is: sda7
chainloader +1
}

my only other question -- well 2 questions:
1)Can I chainload all OS's this way or only ones that use legacy grub?
2)Where does AB's menu.lst come in? Do I use that in the 40_Custom entry somewhere? 

But I think I grasp this now and am very grateful to you both.

---

### Post by oldfred on 2011-10-29
You can only chainload an entry that has another boot loader in the PBR. You can use the other entry I posted.

---

### Post by amjjawad on 2011-10-30
> **Shmook said:**
> You're right amjjawad -- after thinking about it for a minute it is pretty much identical -- both times AB had not been recognized for some reason. What confused me (and led me to think this was a separate problem) was that I got it to be recognized by Ubuntu by using GCust to install to the MBR, so it felt like the cause must be different. Silly me.


Don't call yourself "silly", this is called Learning ;)

---

### Post by oldfred on 2011-10-30
If you chainload to a grub legacy install you will then see its menu as a second menu to some up. If you use the grub2 boot to a partition, you will not see a menu, and it will just boot the newest kernel.

I had just started to learn grub legacy and they came out with grub2 and grub2 does not like to be chain loaded. I hated it along with many posters. But with better documentation (see just about any post by drs305) and a better understanding of grub2 I now use it for everything. Like the fellow who only has a hammer so everything looks like a nail, I think everything now can be booted with grub2. I have grub2 installed on every drive and USB flash drive. I boot ISOs directly from flash or hard drive. I even downloaded a Windows7 repair CD copied to a flash drive and made it boot with grub2, so I could add a couple more repair ISOs on the same flash drive. But all of this took several years of learning & experimenting with grub2.

---

