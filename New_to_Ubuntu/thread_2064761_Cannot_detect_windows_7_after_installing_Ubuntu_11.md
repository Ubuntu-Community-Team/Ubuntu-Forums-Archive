---
title: "Cannot detect windows 7 after installing Ubuntu 11.10 64-bit"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by aeroditya on 2012-09-30
I have been breaking my head trying to install Ubuntu on my new 64-bit machine. I have already installed Windows 64-bit. Now that I succeeded in installing Ubuntu 11.10 64-bit, my machine doesn't give me any boot menu and directly takes me to Ubuntu. After exploring many threads here, I downloaded and ran the BootInfoScript utility. The Results.txt file is pasted below :
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
d    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048    81,922,047    81,920,000 Data partition (Windows/Linux)
/dev/sda2      81,922,048    82,126,847       204,800 EFI System partition
/dev/sda3      82,126,848    82,388,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4      82,388,992   287,188,991   204,800,000 Data partition (Windows/Linux)
/dev/sda5     287,188,992   711,124,991   423,936,000 Data partition (Windows/Linux)
/dev/sda6     711,124,992   933,763,071   222,638,080 Data partition (Windows/Linux)
/dev/sda7     933,763,072   974,778,697    41,015,626 Data partition (Windows/Linux)
/dev/sda8     974,778,698   976,772,838     1,994,141 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        24122A93122A6A4E                       ntfs       
/dev/sda2        DE28-5EA9                              vfat       
/dev/sda4        14C82ACBC82AAAC6                       ntfs       Work
/dev/sda5        125472DB5472C151                       ntfs       Big Volume
/dev/sda6        3064CDA664CD6EE2                       ntfs       Other Volume
/dev/sda7        8dfecd7c-6be5-47f4-b70c-0e11796e751d   ext4       
/dev/sda8        095cb8c9-79b8-441e-be08-8a703e6d9766   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw)
/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sr0         /media/Ubuntu 12.04 LTS amd64 iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt7)'
search --no-floppy --fs-uuid --set=root 8dfecd7c-6be5-47f4-b70c-0e11796e751d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt7)'
  search --no-floppy --fs-uuid --set=root 8dfecd7c-6be5-47f4-b70c-0e11796e751d
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
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 8dfecd7c-6be5-47f4-b70c-0e11796e751d
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8dfecd7c-6be5-47f4-b70c-0e11796e751d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 8dfecd7c-6be5-47f4-b70c-0e11796e751d
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8dfecd7c-6be5-47f4-b70c-0e11796e751d ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 8dfecd7c-6be5-47f4-b70c-0e11796e751d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 8dfecd7c-6be5-47f4-b70c-0e11796e751d
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=8dfecd7c-6be5-47f4-b70c-0e11796e751d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=DE28-5EA9  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda8 during installation
UUID=095cb8c9-79b8-441e-be08-8a703e6d9766 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```I also downloaded and ran the Boot Repair utility, but it gives the following error : 
                               [INDENT]*GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.  *
 *Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.*


[/INDENT]I am attaching a screenshot of my GParted, to get a view of my disk system :


[ATTACH]224884[/ATTACH]


sda1 = Windows 7 C:/
sda4,5,6 = Windows 7 partitions (All my data)
sda7,8 = Ubuntu installation and swap area


[LEFT]How do I proceed to solve my problem, so that I can continue to use Windows 7 and Ubuntu in dual-booted harmony ? If I have to make a new BIOS-boot partition, how do I go about it? If that is not required, what is the easy fix?
[/LEFT]

---

### Post by fooman on 2012-09-30
no expert here,  but have you tried running update-grub in a terminal to see if it picks up your windows partitions and adds them to the boot menu?  

open a terminal and run the following:

```
sudo update-grub
```again,  post the output back here if it doesn't work.

---

### Post by Bashing-om on 2012-09-30
aeroditya; Hi ! welcome to the forum.

I am not up-to-date on UEFI ...below links will assist you ..At some point will have to get myself up to speed !...

On Topic: Partitions; older msdos partitioning could only have 4 primary partitions per disk. In any case ubuntu will have to match the windows scheme (GPT ?) in the installation process.
[http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise](http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise)
[http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI](http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI)

These links will answer your current questions..by all means post back with additional questions.[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by houseworkshy on 2012-09-30
This may be useful
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2012-09-30
If booting in UEFI mode you do not need a bios_grub partition. That is for gpt partitioned drives using BIOS to boot. 
Windows only installs to gpt partitioned drives if in UEFI mode.

To run repairs from Ubuntu you have to use 64bit versions and boot from UEFI menu to efi mode not BIOS, legacy, AHCI or whatever your system calls it. Repairs, installs etc will be in the same mode you boot.

If you boot 64bit version, then Boot_repair will work and repair efi boots.

You install is a bit unusual as the efi partition is supposed to be first. But I have seen one or two that were not. I think the FAT32 driver built into the UEFI system cannot read beyond a certain point, so it just is easier to tell everyone that the efi fAT32 partition must be first.

---

### Post by aeroditya on 2012-10-01
> **fooman said:**
> no expert here,  but have you tried running update-grub in a terminal to see if it picks up your windows partitions and adds them to the boot menu?  

open a terminal and run the following:

```
sudo update-grub
```again,  post the output back here if it doesn't work.
Fooman,

The output to *sudo update-grub  *is

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by NikTh on 2012-10-01
Try one more time .. with these commands 

```
sudo grub-install /dev/sda
sudo mount /dev/sda1 /mnt 
sudo update-grub
```give the results of the 3rd ,back here.

Thanks

---

### Post by aeroditya on 2012-10-01
> **oldfred said:**
> If booting in UEFI mode you do not need a bios_grub partition. That is for gpt partitioned drives using BIOS to boot. 
Windows only installs to gpt partitioned drives if in UEFI mode.

To run repairs from Ubuntu you have to use 64bit versions and boot from UEFI menu to efi mode not BIOS, legacy, AHCI or whatever your system calls it. Repairs, installs etc will be in the same mode you boot.

If you boot 64bit version, then Boot_repair will work and repair efi boots.

You install is a bit unusual as the efi partition is supposed to be first. But I have seen one or two that were not. I think the FAT32 driver built into the UEFI system cannot read beyond a certain point, so it just is easier to tell everyone that the efi fAT32 partition must be first.
I am currently running Ubuntu 11.10 64-bit (I am kinda stuck inside it). Shouldn't it automatically download the 64-bit Boot-Repair?
Can you tell me how to get the correct version of Boot-Repair, so that I can proceed to repair....?

Thanks

---

### Post by aeroditya on 2012-10-01
> **NikTh said:**
> Try one more time .. with these commands 

```
sudo grub-install /dev/sda
sudo mount /dev/sda1 /mnt 
sudo update-grub
```give the results of the 3rd ,back here.

Thanks
Here you go NikTh (no errors were reported)

[I]Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-26-generic
Found initrd image: /boot/initrd.img-3.0.0-26-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done
[/I]

---

### Post by oldfred on 2012-10-01
If you have UEFI, then you need 12.04. They have been making a lot of fixes to grub and how it installs. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Just be sure not to download default 32bit.
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by YannBuntu on 2012-10-01
Hello

> **aeroditya said:**
> I also downloaded and ran the Boot Repair utility, but it gives the following error : 
                               [INDENT]*GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.  *
 *Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.*

Please could you run Boot-Repair --> "Create a BootInfo summary" , and tell us the URL that will appear?
(this will provide a BootInfo more complete than the one you gave in your post#1)

---

### Post by Gini1195 on 2012-10-01
> **aeroditya said:**
> I have been breaking my head trying to install Ubuntu on my new 64-bit machine. I have already installed Windows 64-bit. Now that I succeeded in installing Ubuntu 11.10 64-bit, my machine doesn't give me any boot menu and directly takes me to Ubuntu. After exploring many threads here, I downloaded and ran the BootInfoScript utility. The Results.txt file is pasted below :
[CODE]                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1:  
[LEFT]How do I proceed to solve my problem, so that I can continue to use Windows 7 and Ubuntu in dual-booted harmony ? If I have to make a new BIOS-boot partition, how do I go about it? If that is not required, what is the easy fix?
[/LEFT]


 Okay, as a real Ubuntu newbie I probably should just read and not respond, but please take a look at this link,   http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/   specifically the second page, about half way through the tut, where the text reads:   &quot;After installation has completed successfully, reboot the computer. It should reboot into Windows. This is expected. At this point, Windows does not know that it is now sharing the computer with another operating system. The next step is to tell it, and modify its boot menu to reflect that fact.&quot;   Continue reading about Easy BCD and how it is used to place the needed entry in the MBR. I know you are installing Ubuntu 11.10 and not version 12.04, but this aspect may be the same.  Hope this helps!

---

### Post by oldfred on 2012-10-01
If you are using UEFI, you do not install to the MBR.

I think older copies of EasyBCD did not work with UEFI either. They are working on fixing that as I understand, but if you have UEFI be careful with older instructions for any BIOS based system.

---

### Post by Gini1195 on 2012-10-01
Sorry, I misread your post and see that you boot directly into Ubuntu, not Windows! Easy BCD may still help, but different directions would obviously be needed.

---

### Post by aeroditya on 2012-10-02
> **YannBuntu said:**
> Hello



Please could you run Boot-Repair --> "Create a BootInfo summary" , and tell us the URL that will appear?
(this will provide a BootInfo more complete than the one you gave in your post#1)


Here you go Yaanbuntu....
[http://paste.ubuntu.com/1255341/](http://paste.ubuntu.com/1255341/)

Thanks

---

### Post by YannBuntu on 2012-10-02
ok.
Please run Boot-Repair --> Advanced options --> GRUB location tab --> tick the "Separate /boot/efi" option --> Apply. 
Tell us the new URL that will appear.
Then reboot and indicate what you observe.

---

### Post by aeroditya on 2012-10-15
Thanks for the help and patience guys! I was able to run the boot repair, using help documentation from the Boot-Repair utility site. I am currently able to access my Windows 7, by manually choosing to boot from my HDD everytime! :p

Ofcourse, I want to be able to still use Ubuntu, but when I boot into Ubuntu (which still happens automatically if I don't hit F12 and manually change boot device), it goes to the infamous **grub rescue** command prompt! I don't know where to go from here, how to recover my Ubuntu.

Will EasyBCD from Windows do the trick? Will I ever get a decent Boot menu with Windows 7 and Ubuntu options?

Thanks,

---

### Post by newb85 on 2012-10-15
So, if you don't hit F12, what is your machine using as the boot device?

---

### Post by YannBuntu on 2012-10-15
> **aeroditya said:**
> Thanks for the help and patience guys! I was able to run the boot repair

Please indicate the resulting URL each time you use Boot-Repair.

> **aeroditya said:**
> I am currently able to access my Windows 7, by manually choosing to boot from my HDD everytime!

Which entry to you choose, in which menu? please could you show us a picture?

> **aeroditya said:**
> Will EasyBCD from Windows do the trick?

Probably not, as EasyBCD / BCDedit are not reported to be UEFI compliant.

---

