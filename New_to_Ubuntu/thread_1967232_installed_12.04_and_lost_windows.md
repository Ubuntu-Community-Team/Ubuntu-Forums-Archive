---
title: "installed 12.04 and lost windows"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by cabz on 2012-04-27
I recently installed ubuntu 12.04 through wubi in windows , after the reboot I had no more windows. I didnt see anything in the program that asked me if i wanted to dual boot or just use 12.04 . is this normal? or did i just miss something.

---

### Post by carl4926 on 2012-04-27
You now have another thread about removing Vista, you didn't mention you used wubi there. Which is important.

To install ubuntu properly you should boot from the CD or create a bootable USB

---

### Post by cabz on 2012-04-27
> **carl4926 said:**
> You now have another thread about removing Vista, you didn't mention you used wubi there. Which is important.
 
To install ubuntu properly you should boot from the CD or create a bootable USB
 Sorry to confuse, there are two posts for two diffrent PC's my garage PC has lost windows and my work PC needs vista gone.

---

### Post by carl4926 on 2012-04-27
I can't help on wubi, I have never used it and never will. Sorry,

---

### Post by cryptotheslow on 2012-04-28
I have no experience of wubi, but my understanding is that it installs Ubuntu into a virtual disk (a file within the windows filesystem that can be mounted as a disk) and installs a bootloader that references both windows and ubuntu installs.

I think it would help if you could follow the instructions here:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

to download and run the boot info script and post back the resultant RESULTS.txt file

That will allow us to know what is installed where and where the various bootloaders have ended up.

In the meantime, don't do anything rash like attempting a reinstall - that will invariably make things worse.

---

### Post by bcbc on 2012-04-28
The very first boot of Ubuntu after installing Wubi does not prompt you. Thereafter, you get a choice. It should probably warn people of this, but that's what happens (on Vista and 7, but not on XP).

So don't worry, Windows is still there ;)

---

### Post by carl4926 on 2012-04-28
> **bcbc said:**
> The very first boot of Ubuntu after installing Wubi does not prompt you. Thereafter, you get a choice. It should probably warn people of this, but that's what happens (on Vista and 7, but not on XP).

So don't worry, Windows is still there ;)
Really... WOW
Top marks for that pointer

---

### Post by cabz on 2012-04-28
op.> **bcbc said:**
> The very first boot of Ubuntu after installing Wubi does not prompt you. Thereafter, you get a choice. It should probably warn people of this, but that's what happens (on Vista and 7, but not on XP).

So don't worry, Windows is still there ;)just turned the PC back on and no windows , I am not worried about it being gone since I have backups. just kinda wondering what happened:confused: and i dont know if this makes a diffrence but this pc was a win 7 laptop.

---

### Post by bcbc on 2012-04-28
> **cabz said:**
> just turned the PC back on and no windows , I am not worried about it being gone since I have backups. just kinda wondering what happened:confused:

Okay - now it's time for the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

Note that Wubi boots via the Windows boot manager - so it requires Windows to boot normally - and the files reside on the NTFS (sometimes FAT32) partition, along with other Windows files.

But let's see the result of that script...

---

### Post by 3rdalbum on 2012-04-28
As mentioned before, Wubi actually installs Ubuntu into a file on your Windows partition (or into a file on another hard disk). If it can boot Ubuntu, then your hard disk is still intact.

It should give you a menu allowing you to choose between Windows and Ubuntu. This is the actual Windows bootloader screen. If you're not getting this, I can't understand why - unless you still have the Ubuntu CD in your computer and it is trying to boot from the CD?

---

### Post by mobisallen on 2012-04-28
u can uninstall ubunto and reinstall it on some other partition.

---

### Post by cabz on 2012-05-01
[LEFT]I have tried ten  difrent ways to make the boot info script work but it will not just keeps saying that the directory does not exist. I opened the files on the desktop and tried linking to that and even hand type it in  instead of and with cutting and pasting and nothing! 
[/LEFT]

---

### Post by bcbc on 2012-05-01
> **cabz said:**
> [LEFT]I have tried ten  difrent ways to make the boot info script work but it will not just keeps saying that the directory does not exist. I opened the files on the desktop and tried linking to that and even hand type it in  instead of and with cutting and pasting and nothing! 
[/LEFT]

I downloaded the bootinfoscript-061.tar.gz file to my Downloads directory. I right clicked and told it to "Extract here". That created a directory: bootinfoscript-061

Within that the script was named "bootinfoscript" not "bootinfoscript.sh" as it says on the download page.

So to run it I do:
```
cd ~/Downloads/bootinfoscript-061
sudo bash bootinfoscript

```

Note the tilde "~" and the case-sensitive directory names. You can also use the TAB key for autocompletion (to make sure you're in the right place).


Another trick is to use locate to find something (this does take a fairly long time to update the database):
```
sudo updatedb
locate bootinfoscript
```

e.g. on mine it looks like this:
```
bcbc@ubuntu:~$ locate bootinfoscript
/home/bcbc/Downloads/bootinfoscript-061
/home/bcbc/Downloads/bootinfoscript-061.tar.gz
/home/bcbc/Downloads/bootinfoscript-061/CHANGELOG
/home/bcbc/Downloads/bootinfoscript-061/README
/home/bcbc/Downloads/bootinfoscript-061/bootinfoscript

```
The one I want to run is "/home/bcbc/Downloads/bootinfoscript-061/bootinfoscript"

---

### Post by cabz on 2012-05-01
thanks for the help, I am real new to this .Here is the result file info [ATTACH]217073[/ATTACH]

---

### Post by bcbc on 2012-05-01
This all looks normal. Is it possible you modified your Windows boot manager to boot Ubuntu?

When you boot it always boots straight to Ubuntu right?
Do you have a Windows repair CD handy?


```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

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
    Boot files:        /bootmgr /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,926,848   625,140,399   594,213,552   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       3aeb87a9-b001-4bc4-a3b1-cb306b3e4e9c   ext3       
/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        4E9A00D49A00BA8B                       ntfs       OS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext3       (rw)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda3/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 4E9A00D49A00BA8B
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 4E9A00D49A00BA8B
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 4E9A00D49A00BA8B
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=4E9A00D49A00BA8B loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 4E9A00D49A00BA8B
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=4E9A00D49A00BA8B loop=/ubuntu/disks/root.disk ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 4E9A00D49A00BA8B
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=4E9A00D49A00BA8B loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 4E9A00D49A00BA8B
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=4E9A00D49A00BA8B loop=/ubuntu/disks/root.disk ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk	none	swap	sw	0	0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic              63
               =                boot/initrd.img-3.2.0-24-generic              66
               =                boot/vmlinuz-3.2.0-23-generic                 20
               =                boot/vmlinuz-3.2.0-24-generic                 26
               =                initrd.img                                    66
               =                initrd.img.old                                63
               =                vmlinuz                                       26
               =                vmlinuz.old                                   20

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by cabz on 2012-05-01
yup boots straight into ubuntu, no asking which just ubuntu. i did have to f12 to get the cd to read at boot, but i have done that before and not had any issues. I am not horribly worried about getting windows back . i have access to all my windows files through ubuntu. i just wanna know where it went wrong for future knowledge.

---

### Post by bcbc on 2012-05-02
> **cabz said:**
> yup boots straight into ubuntu, no asking which just ubuntu. i did have to f12 to get the cd to read at boot, but i have done that before and not had any issues. I am not horribly worried about getting windows back . i have access to all my windows files through ubuntu. i just wanna know where it went wrong for future knowledge.

That's what's strange. This type of install you have can only be run from Windows, running wubi.exe. It downloaded a 500MB preinstalled image (tar.xz) file and expanded it onto the root.disk. This is clear because it has an ext3 filesystem as well as an '# UNCONFIGURED FSTAB FOR BASE SYSTEM'.

So there is no possible way to install this by booting a CD or even by running wubi.exe off the CD from windows.

In addition, the only way you can be booting Ubuntu is via the Windows boot manager, and grub4dos/grub2 (wubildr.mbr and wubildr). 

The only way I know this can happen is by manually setting the Windows Startup & recovery settings so that the "Time to display operating systems" is 0, as well as making Ubuntu the default boot OS.

What you will need to do to fix this is to boot a Windows repair CD and then go to a repair prompt and run:
```
bcdedit
```

Then post back the result (maybe with a camera) - or if the timeout is zero set it back with:
```
bcdedit /timeout 10
```

---

### Post by frankjeffries on 2012-05-02
> **bcbc said:**
> The very first boot of Ubuntu after installing Wubi does not prompt you. Thereafter, you get a choice. It should probably warn people of this, but that's what happens (on Vista and 7, but not on XP).

So don't worry, Windows is still there ;)This sounds real good but if Ubuntu does not boot then there is also nothing the next time it boots because it does not know its booted before

---

### Post by bcbc on 2012-05-03
> **frankjeffries said:**
> This sounds real good but if Ubuntu does not boot then there is also nothing the next time it boots because it does not know its booted before

That's not how it works. Since it's the Windows Boot Manager that is set to boot Ubuntu one-time only, it has no idea whether the boot is successful and doesn't care.

---

