---
title: "Used netbook, need to remove previous user and change boot order"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by frh1 on 2011-11-18
I bought a Samsung N-145 Netbook with Windows 7 Starter that also had Umbantu installed as the default boot option.  I bought that particular netbook because it is compatibile with a Pixel Qi daylight readable screen.  I plan to use the netbook with a landscape industry specific software program running on Windows 7.

I would prefer to keep Umbantu on the netbook, and with time may grow to prefer it.  But in the meantime I have two problems:

First, right now Umbantu is the default boot option.  It would be a lot easier to use the netbook for the purpose I bought it for if the default boot option was Windows 7.  (If I can't do that I will have to remove Umbantu).

My second issue is, although the previous owner gave me her passwords, I know so little about Umbantu I don't have any idea how to completely replace her name, identity, etc., with mine so it can really be my computer.

Umbantu is so new (and strange) to me that I haven't been able to figure out what version is on the netbook.  I've been trying to read tutorials, but without a good starting place, it seems like the more I read, the more confused I get.  I can follow simple instructions, but right now I just don't know where to start.

(Forgive typing errors, I am typing this on a 7" android tablet while waiting in a hospital emergency room.)

---

### Post by cbanakis on 2011-11-18
I have not dual booted before...
But I believe the default session is selected in Windows.

Control Panel/System/Advanced System Settings/Startup and Recovery/

There you can choose the default os to boot, and even adjust the timer for the auto-select at the boot screen.

You probably need to change the control panel view "category view" to either of the other options. 

Hope this helps

---

### Post by Elfy on 2011-11-18
Hi and welcome to the forum

if you can go here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and follow those instructions it will give us a lot of information. 

While you are in the terminal you can also run this and it will tell us what version you are running 

```
lsb_release -r
```

We can deal with > how to completely replace her name, identity, etc.,  later - but let's deal with the issues one at a time so you don't get lost.

---

### Post by frh1 on 2011-11-18
Thank's for the quick responses.  I went into the control panel in Windows 7 this morning and could not find anything that might affect boot order.  My wife has COPD.  Being around sick grandkids caused her to get mild to moderate pnemonia that was not responding to antibiotics and steroids at home.  They decided to admit her to the hospital last night so they can knock out with IV antibiotics before it gets worse.   I'll be heading back to the hospital as soon as my son's Dr. appointment is finished.  The hospital has an unsecured network for patients.  She called me this morning to tell me she is already feeling better so they might decide to release her this afternoon.  If they don't release her by the time I get there, I could have the rest of the day to mess with the netbook.

---

### Post by grahammechanical on 2011-11-18
Hi and welcome to the forums

I am sorry to hear about your wife. Having had an operation myself a couple of years ago may I say? That when you are ill, you are ill. A person might be out of hospital and up and about but does not mean that they are well and back to their usual self.

May I also recommend something called Grub Customizer? You can read about here:

[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

You can use it to set the boot order of the operating systems that are on your computer. It is simple to use.

You will also be able to set yourself as a user on the system with administrator rights and when you can login with your own password you can then remove the user who was the previous owner.

The information that you have been asked to provide will help us tell you how to do that. Ubuntu is being developed all the time and menus change and utilities are redesigned. We do not want to send you looking for something that has changed.

Regards.

---

### Post by frh1 on 2011-11-21
I'm typing this in Firefox running under Umbantu, so it's working and I am getting into some things.

I've been able to get into the terminal and paste input such as "lsb_release -r, then it asks for Jennifer's password but won't accept imput from the keyboard.

I also downloaded Grub customizer, but haven't been able to make it run.  Here's an example of what I get when I try to do anything in the terminal:

Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-11-generic i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

60 packages can be updated.
35 updates are security updates.

New release 'oneiric' available.
Run 'do-release-upgrade' to upgrade to it.

jennifer@jennifer-N250P:~$  sudo bash ~/Desktop/boot_info_script.sh
[sudo] password for jennifer: 
Sorry, try again.
[sudo] password for jennifer: 
Sorry, try again.
[sudo] password for jennifer: 


I'm frustrated.  I'm not computer stupid, I never had a problem back in the 1980's with MS DOS.  But I'm just not getting Umbantu.  I definately need some hand holding.  HELP PLEASE!

---

### Post by snowpine on 2011-11-21
Simply type the regular user password for 'jennifer'. It will not show on the screen as you're typing. This is assuming jennifer is an admin account, if not, somebody who is an admin will have to [add her to the "admin" group]("https://help.ubuntu.com/community/RootSudo#Allowing_other_users_to_run_sudo"). 

I would recommend a fresh install of Ubuntu. I always do this when I acquire a used computer. I don't need/want a stranger's settings, customizations, and data. There are simple "how to download and install" instructions at ubuntu.com.

---

### Post by Zill on 2011-11-21
> **snowpine said:**
> ...I would recommend a fresh install of Ubuntu. I always do this when I acquire a used computer. I don't need/want a stranger's settings, customizations, and data. There are simple "how to download and install" instructions at ubuntu.com.
+1 - Excellent advice.

To the OP:  No-one here has ever heard of "Umbantu" - we all use "Ubuntu". ;-)

---

### Post by frh1 on 2011-11-21
Sorry about the misspelling.  RESULTS.TXT:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   184,756,223   184,549,376   7 NTFS / exFAT / HPFS
/dev/sda3         184,758,270   459,956,223   275,197,954   f W95 Extended (LBA)
/dev/sda5         184,758,272   322,747,046   137,988,775   7 NTFS / exFAT / HPFS
/dev/sda6         322,748,416   454,270,975   131,522,560  83 Linux
/dev/sda7         454,273,024   459,956,223     5,683,200  82 Linux swap / Solaris
/dev/sda4         459,956,224   488,392,703    28,436,480  27 Hidden NTFS (Recovery Environment)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        02DEC480DEC46E0B                       ntfs       SYSTEM
/dev/sda2        4A3C21303C211909                       ntfs       
/dev/sda4        5CF2F44EF2F42E40                       ntfs       SAMSUNG_REC
/dev/sda5        6890138790135B40                       ntfs       
/dev/sda6        03c38ec2-681b-4e09-9166-657a96821bec   ext4       
/dev/sda7        1870d82c-14c0-4d6b-a6b4-0c92a091a80c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=600)


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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 03c38ec2-681b-4e09-9166-657a96821bec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 03c38ec2-681b-4e09-9166-657a96821bec
set locale_dir=($root)/boot/grub/locale
set lang=
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 03c38ec2-681b-4e09-9166-657a96821bec
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=03c38ec2-681b-4e09-9166-657a96821bec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 03c38ec2-681b-4e09-9166-657a96821bec
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=03c38ec2-681b-4e09-9166-657a96821bec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 03c38ec2-681b-4e09-9166-657a96821bec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 03c38ec2-681b-4e09-9166-657a96821bec
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 02DEC480DEC46E0B
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 5CF2F44EF2F42E40
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
UUID=03c38ec2-681b-4e09-9166-657a96821bec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=1870d82c-14c0-4d6b-a6b4-0c92a091a80c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 190.034084320 = 204.047544320  boot/grub/core.img                             1
 186.103546143 = 199.827161088  boot/grub/grub.cfg                             1
 210.164257050 = 225.662152704  boot/initrd.img-2.6.38-11-generic              2
 209.086246490 = 224.504647680  boot/vmlinuz-2.6.38-11-generic                 1
 210.164257050 = 225.662152704  initrd.img                                     2
 209.086246490 = 224.504647680  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

