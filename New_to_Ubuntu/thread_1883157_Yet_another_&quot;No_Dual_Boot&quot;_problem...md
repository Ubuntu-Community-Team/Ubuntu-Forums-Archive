---
title: "Yet another &quot;No Dual Boot&quot; problem.."
date: 2011-11-18
forum: New to Ubuntu
---

### Post by malc_p on 2011-11-18
Sorry, all!
New ubuntu user so be gentle!
I have a PC running XP with three hard disks (500Gb, 500Gb, 120Gb), each has several partitions, and I had a 250Gb partition free on the second hard disk (and not allocated to XP as a known partition).
Downloaded the iso for Ubuntu 11.10, burnt it to a bootable CD and then booted up from the CD.
Selected the installer option to install alongside XP as an alternative bootable OS, selected the spare partition for the installation, the installation went fine but on restarting the PC, it goes straight to XP without showing me the dual-boot screen I'm expecting.
If I boot from the CD I get Ubuntu up and can access the hard disk no problem.
Help! I imagine it's because I installed to a different disk from the XP base disk, so is there something I need to do in XP?
Any more info you need from me, let me know!
Cheers
Malc

---

### Post by Espera on 2011-11-18
I've never dealt with multiple OS's over multiple HDD's but its sounds like it could be one of two things if my reasoning is correct.

1: From what i read unless ive read it wrong the HDD that ubuntu is on and the HDD that XP is on are different, have you tried changing your computer's boot order to boot off the linux hard drive first? if so then you should get grub and usually out the box recognises all os's. if you boot off that disk and only get ubuntu just run ubuntu grab a terminal and type: update-grub and i imagine that grub will then get all the os's and just use the ubuntu hdd to boot off in future.

2: this is unlikely as its never happened to me but you may not have installed grub.
if thats the case then I'm sure you could just launch a live session off your ubuntu disk grab a terminal and type: sudo apt-get install grub (i may be wrong) then that should solve a no grub issue.

Saying that i could just be completely wrong on both counts :P

---

### Post by duke.tim on 2011-11-18
When the hard drives are installed on a computer one of them is set to "master" the rest to "slave" (i'm simplifiying it a bit Primary/secondary master/slave) 

There are several options:

#0 install ubuntu on the master drive


#1 add an entry to the windows bootloader to chain to the ubuntu bl

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://ss64.com/nt/bootcfg.html](http://ss64.com/nt/bootcfg.html)



#2
Install Grub over the windows bootloader and configure it.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


___________________________________________________________________________________________________________
Just for kicks and giggles this kinda explains a bit about primary master/secondary slave
[http://www.computing.net/answers/hardware/dual-boot-two-drives-with-two-xp-/54270.html](http://www.computing.net/answers/hardware/dual-boot-two-drives-with-two-xp-/54270.html)

And a more technical explaination
[http://www.pcguide.com/ref/hdd/if/ide/confJumpering-c.html](http://www.pcguide.com/ref/hdd/if/ide/confJumpering-c.html)

---

### Post by oldfred on 2011-11-18
Both of above may be correct. But if newer SATA drives, there is no master/slave. You set boot drive in BIOS.

What drive did you install grub2's boot loader to, the default is usually sda.

To know what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

### Post by malc_p on 2011-11-19
OK I've run it...the results file is 417 lines, are you sure you want all this, or is there a section I can post up as necessary?
Cheers

---

### Post by rng on 2011-11-19
You can search other threads in this forum- many have posted output of boot_info_script.sh which clearly gives all partitions, booting and grub details.

---

### Post by BlinkinCat on 2011-11-19
> **malc_p said:**
> OK I've run it...the results file is 417 lines, are you sure you want all this, or is there a section I can post up as necessary?
Cheers

Note oldfred's comments regarding code tags.

---

### Post by malc_p on 2011-11-19
Yup it suggested sda for the boot drive; I have no idea how I would have told it to use the one where the machine boots from!
I have no experience of how to modify a bootloader file so here's the output from bootinfo and if anyone can point me in the direction as to what I have to do using EasyBCD or bootcfg I would appreciate it greatly. I haven't any partitions available on my main boot disk to put Ubuntu into which is why I plumped for the second of my 500Gb hard drives which I had 250Gb free on.
Many thanks all...

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Paragon is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb5
                       and looks at sector 826155848 of the same hard drive
                       for core.img, but core.img can not be found at this
                       location.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:   

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:   

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:   

sdc4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:   

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   532,474,424   532,474,362   7 NTFS / exFAT / HPFS
/dev/sda2         532,474,425   737,271,044   204,796,620   7 NTFS / exFAT / HPFS
/dev/sda3         737,271,045   976,768,064   239,497,020   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   204,812,684   204,812,622   7 NTFS / exFAT / HPFS
/dev/sdb2         204,812,685   460,824,524   256,011,840   7 NTFS / exFAT / HPFS
/dev/sdb3         460,824,574   976,771,071   515,946,498   5 Extended
/dev/sdb5         460,824,576   968,386,559   507,561,984  83 Linux
/dev/sdb6         968,388,608   976,771,071     8,382,464  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   286,712,054   286,711,992   7 NTFS / exFAT / HPFS
/dev/sdc2         286,712,055   327,677,804    40,965,750   7 NTFS / exFAT / HPFS
/dev/sdc3         327,677,805   368,643,554    40,965,750   7 NTFS / exFAT / HPFS
/dev/sdc4         368,643,555   490,223,474   121,579,920   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        0CF0B2CDF0B2BC70                       ntfs       Malcs Stuff
/dev/sda2        60ECC3ACECC37B34                       ntfs       Old Vid
/dev/sda3        441CDF6F1CDF5B0E                       ntfs       New S
/dev/sdb1        F4CC8E93CC8E4FB2                       ntfs       Main
/dev/sdb2        01C9A98498BBEE00                       ntfs       Video Edits
/dev/sdb5        978720c7-b271-4e38-884f-6faa2f2616ad   ext4
/dev/sdb6        239cc502-1807-42a7-89e9-ce1ef7f9a929   swap
/dev/sdc1        A268ED3568ED08BD                       ntfs       Old M
/dev/sdc2        5270DE0970DDF427                       ntfs       Kits Stuff
/dev/sdc3        30D41343D4130B2C                       ntfs       Fuji Cards
/dev/sdc4        96C478C1C478A4E1                       ntfs       Old S

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]^M
timeout=30^M
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS^M
[operating systems]^M
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer^M
--------------------------------------------------------------------------------

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 978720c7-b271-4e38-884f-6faa2f2616ad
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root 978720c7-b271-4e38-884f-6faa2f2616ad
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set=root 978720c7-b271-4e38-884f-6faa2f2616ad
        linux   /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=978720c7-b271-4e38-884f-6faa2f2616ad ro   quiet splash vt.handoff=7
        initrd  /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set=root 978720c7-b271-4e38-884f-6faa2f2616ad
        echo    'Loading Linux 3.0.0-12-generic-pae ...'
        linux   /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=978720c7-b271-4e38-884f-6faa2f2616ad ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.0.0-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set=root 978720c7-b271-4e38-884f-6faa2f2616ad
        linux   /boot/vmlinuz-3.0.0-12-generic root=UUID=978720c7-b271-4e38-884f-6faa2f2616ad ro   quiet splash vt.handoff=7
        initrd  /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set=root 978720c7-b271-4e38-884f-6faa2f2616ad
        echo    'Loading Linux 3.0.0-12-generic ...'
        linux   /boot/vmlinuz-3.0.0-12-generic root=UUID=978720c7-b271-4e38-884f-6faa2f2616ad ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set=root 978720c7-b271-4e38-884f-6faa2f2616ad
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set=root 978720c7-b271-4e38-884f-6faa2f2616ad
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set=root F4CC8E93CC8E4FB2
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=978720c7-b271-4e38-884f-6faa2f2616ad /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=239cc502-1807-42a7-89e9-ce1ef7f9a929 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-12-generic-pae           3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic-pae              1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================
```

---

### Post by oldfred on 2011-11-19
When you have multiple drives I prefer to have each system on a different drive and each boot loader in the MBR of that drive. Then each hard drive can boot without the other. But you have both XP & Ubuntu in sdb. EasyBCD only works with Vista or 7 not XP.

If you really want to keep the windows boot loader in sdb you can install grub to sdc and it will still boot the Ubuntu install in sdb. What is Paragon boot loader in sda, I am not familiar with it.

You have to use manual install or something else to get the choice on which drive to install grub2's boot loader to.

You can use liveCD, or down load one of several repair or boot tools.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sdb5 and want grub2's bootloader in drive sdc's MBR:
#Find linux partition, change sdb5 if not correct:
sudo fdisk -l
#confirm that linux is sdb5
[COLOR=Red]sudo mount /dev/sdb5 /mnt[/COLOR]
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
[COLOR=Red]sudo grub-install --boot-directory=/mnt/boot /dev/sdc[/COLOR]

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Then change BIOS to boot sdc.

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")


Or:

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This should let you boot Ubuntu and then you can reinstall grub from inside Ubuntu.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdc

You can choose to install grub to any drive.
If you want it to update where it reinstalls on grub updates.
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

