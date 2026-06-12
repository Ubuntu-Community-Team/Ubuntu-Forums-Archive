---
title: "Ubuntu wont boot from hdd"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by zapperlot on 2012-01-21
Hello, my name is Frank. I'm from Germany and English is not my first language, so.. believe me, I'm trying. Anyway, I cant get Ubuntu 11.10 up&running on my brand new lenovo b570.

0. Freedos was already installed. 
1. I downloaded the *.iso, made a bootable USB stick (my CD writer is broken) with 1 error: avira antivir prevented the autorun.inf to be executed (I don't know if this is important)
2. I plugged in the USB stick, booted from there, installed ubuntu with the option to overwrite freedos
3. Then it said to unplug the booting media and press enter.

Now I thought it would boot from the hdd, but it doesn't. Nothing happens, I get a blank screen for a couple of seconds, then the option to select a booting device (BIOS layout). 

I now booted Ubuntu from the stick. When I press the "Install Ubuntu 11.10" button, it says after two screens that Ubuntu is installed.

So, I don't know why it won't boot then. 

Thanks for help!

---

### Post by lechien73 on 2012-01-21
Hi and welcome to the forums,

It's possible that Grub was installed to the bootloader of the USB stick instead of the hard drive. This can happen during installation.

To check, please start Ubuntu from the USB stick - select to Try Ubuntu, rather than Install.

Then download the boot info script from here: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Follow the instructions, and then post the contents of the RESULTS.txt file here, between CODE tags (the **#** button on the toolbar).

---

### Post by Double.J on 2012-01-21
Hi there zapperlot! welcome to the forums!

The first thing to check I think is that your BIOS is set to boot from the internal HDD - it may still be looking for the external USB stick?

If that doesn't help, boot up off the live USB again and click on try instead of install (I'm afraid I don't know what those are in German).

press the windows key, then type "gparted" and hit enter - this should show you the partition table on the drive in an easy (ish) to understand way - check if anything seems obviously wrong?

If not, then open a terminal by pressing CTRL+ALT+T and copy/paste the following command
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```It will ask you to pres enter to add the repo.. do this.
once that finishes, install boot repair with the following command
```
sudo apt-get install -y boot-repair && boot-repair
```
The boot repair program should open - it'll scan our system first.

First of all try the recommended repair and see if this works.

if not, choose advanced -> grub location 

 Where it says place grub to, make sure it says /dev/sda or /dev/hda - no number at the end

try rebooting again.

If none of this works, reboot into a live environment one last time and paste the following into a terminal
```
sudo fdisk -l
```
copy the output and paste it here (highlight it in the reply and press the # button at the top :)

Really hope it helps!

---

### Post by zapperlot on 2012-02-22
Hello!

First of all my **sincere** apologies for net replying any sooner. But I get frustrated by errors and especially cryptic error messages REALLY FAST. It's what kept from learning how to program, how to use photoshop... 
Anyway, I made a Live CD today, reinstalled ubuntu for the 4th time, everything fine, laptop is connected to the internet, ubuntu downloaded some packages but still wont boot from hdd.
Here are the results.txt from the bootinfo script and a screenshot from gparted. Since I dont know if it is important or not that one partition doesnt seem to be formatted I'll stop here. If anyone still wants to help, I'd really appreciate it. Thank you!

PS: could anyone exlain to me where exactly these files are created? On the hdd or the system memory? 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sda1 has 0 
                       sectors.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________
[IMG]http://www.abload.de/image.php?img=screenshotat2012-02-2l3kpa.png[/IMG]
    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34        39,096        39,063 EFI System partition
/dev/sda2          39,097   960,171,909   960,132,813 Data partition (Windows/Linux)
/dev/sda3     960,171,910   976,773,118    16,601,209 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        AE6E-8C46                              vfat       
/dev/sda2        95c83aa0-2e6e-42bd-9484-b44b625b4a8c   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root 95c83aa0-2e6e-42bd-9484-b44b625b4a8c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root 95c83aa0-2e6e-42bd-9484-b44b625b4a8c
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
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 95c83aa0-2e6e-42bd-9484-b44b625b4a8c
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=95c83aa0-2e6e-42bd-9484-b44b625b4a8c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 95c83aa0-2e6e-42bd-9484-b44b625b4a8c
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=95c83aa0-2e6e-42bd-9484-b44b625b4a8c ro recovery nomodeset 
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
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 95c83aa0-2e6e-42bd-9484-b44b625b4a8c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 95c83aa0-2e6e-42bd-9484-b44b625b4a8c
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=95c83aa0-2e6e-42bd-9484-b44b625b4a8c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=AE6E-8C46  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
#UUID=73a688f2-0478-43ea-813e-0007f5ff58d4 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     3
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```
[[img]http://www.abload.de/thumb/screenshotat2012-02-2l3kpa.png[/img]](http://www.abload.de/image.php?img=screenshotat2012-02-2l3kpa.png)

---

### Post by oldfred on 2012-02-23
You have a gpt partitioned drive. And a efi partition as the first partition. The efi seems a bit small but may be ok.

Did you run from Boot-repair as it now uses the git version?

The new/test/git version of boot info script also parses efi partiitons. Please download this and run it.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by zapperlot on 2012-02-23
Hello!
I'm not quite sure I fully understood what you wrotes, sorry. I suppose there is some information missing in my bootinfo script?

Here is the file bootrepair created: [http://paste.ubuntu.com/854516/](http://paste.ubuntu.com/854516/)

---

### Post by oldfred on 2012-02-23
That is the git version of boot script and then it does not look like you have any efi files in your efi partition.

Did you create partitions in advance? Most seem to not get it to install in efi unless partitioned in advance. And some said it worked when they reinstalled to the existing partitions. (but then it was partitioned)

I also suggest you make a smaller / (root) partition of about 25GB and then use the rest of the drive for a new partition /home.

---

### Post by zapperlot on 2012-02-24
I didn't do anything regarding the partitions. As I wrote, freedos was already installed, I chose the option to delete it and moved on. The partitions now were set by default. 
Hm so I'll reinstall it and then what options should I choose regarding the partitions?
&#8364;: is there a way to see if there are files on /dev/sda1? When I had Ubuntu running from the Live CD, I had no rights to do so.

---

### Post by cortman on 2012-02-24
When you reinstall, format and delete all partitions (create a new partition table), and follow Oldfred's advice: One ext4 partition for / (root), one ext4 for /home, and one for swap (the swap partition should be the same size as your RAM).

---

