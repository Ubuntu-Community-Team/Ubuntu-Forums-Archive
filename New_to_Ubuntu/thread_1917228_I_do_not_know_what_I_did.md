---
title: "I do not know what I did"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by mr best buy on 2012-01-29
I downloaded the 10.11(?) and burned  the ISO to a DVD.  Then I installed the DVD to my computer and rebooted the machine.  The machine booted form the DVD and I  said to install  the software after erasing the version of Ubunutu I had installed( A dual boot.  So after the install was done I no longer had dual boot.  I had a menu selection to recover Windows 7.  So I did and my Ubunutu disappeared. So I reinstalled  Ubunutu again and I have no dual boot.  Do I get a  different version of Ubunutu or what?

---

### Post by lechien73 on 2012-01-29
Hmmm...I'm not sure what could have happened to your disk structure, but it would help to see the partition details.

Please could you boot from the DVD (select the option to **Try Ubuntu**), then go to [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net). Follow the instructions there to download and run the script. Finally, please post contents of the RESULTS.txt file here between CODE tags (the **#** button on the toolbar).

Then we can see what has happened to your hard drive structure.

---

### Post by mr best buy on 2012-01-29
I booted from the DVD and selected the try area.
I got a desktop and downloaded the file to my desk top
then I extracted the file to my desktop.  Its name is  boot_info_script060

I went to terminal and typed in the command
sudo bash ~/Desktop/boot_info_script.sh....

Did not find the file

then I tried
sudo bash ~/desktop/boot_info_script.sh
Same thing
then I tried
sudo bash ~/Desktop/boot_info_script060.sh
same thing
then I tried
sudo bash ~/desktop/boot_info_script060.sh
same error.  
is it correct to put .sh at the end?

---

### Post by oldfred on 2012-01-29
Linux is case sensitive, so it is only Desktop not desktop.

If you did extract to Desktop the command should have worked. You can change to the Desktop and use tab as a complete the line. Tab completion looks for files with the same characters you have typed and adds as many more as it can. If name is unique it adds the entire line.
#change to Desktop
cd Desktop
# list files  & folders in Desktop
ls 
# run script
sudo bash boo  #then press tab 

Another way to run it, may also make minor fixes:

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

---

### Post by halitech on 2012-01-29
if the file name is boot_info_script060.sh, then that is what you need to run. Also, is the file in a new folder or directly on the desktop? Also, desktop is not the same as Desktop when you are dealing with file names in Linux

---

### Post by mr best buy on 2012-01-29
> **oldfred said:**
> Linux is case sensitive, so it is only Desktop not desktop.

If you did extract to Desktop the command should have worked. You can change to the Desktop and use tab as a complete the line. Tab completion looks for files with the same characters you have typed and adds as many more as it can. If name is unique it adds the entire line.
#change to Desktop
cd Desktop
# list files  & folders in Desktop
ls 
# run script
sudo bash boo  #then press tab 

Another way to run it, may also make minor fixes:

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

OK let me get this stright:
Boot from the install DVD
select "Try Ubunutu"
Go to website  and download the Boo information file
It will go to m download folder, so I copy it to the desktop
Once there I extract it.
then I pull up the terminal
Type in the command "CD Desktop"
Type in "ls"
((Is this correct?))
Type in "sudo bash boo"

((I am confused here---What will see after  this command-----))
((Also, what do I do next????)))

---

### Post by cryptotheslow on 2012-01-29
This:
[I]Type in the command "CD Desktop"
Type in "ls"
((Is this correct?))
Type in "sudo bash boo"

[/I]Should read:
Type in the command "cd Desktop"    <<  note cd is not capitalised
Type in the command "sudo bash boo"   **and then** press the Tab key which will autocomplete the rest of the filename,

Then hit return to execute it.

GL

---

### Post by lechien73 on 2012-01-30
The file inside boot_info_script060.zip is simply called boot_info_script.sh, so the command:

```
sudo bash ~/Desktop/boot_info_script.sh
```

Should have worked.

---

### Post by mr best buy on 2012-01-30
[SIZE="3"]THESE ARE THE RESULTS AND I DO NOT KNOW WHAT THEY MEAN....[/SIZE]   


 ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    for  on this drive.

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
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:        /bootmgr /boot/BCD /wubildr

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
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   777,309,593   777,102,746   7 NTFS / exFAT / HPFS
/dev/sda3       1,440,192,512 1,465,145,343    24,952,832   7 NTFS / exFAT / HPFS
/dev/sda4         777,310,206 1,440,192,511   662,882,306   5 Extended
/dev/sda5       1,427,632,128 1,440,192,511    12,560,384  82 Linux swap / Solaris
/dev/sda6         777,310,208 1,415,069,695   637,759,488  83 Linux
/dev/sda7       1,415,071,744 1,427,615,743    12,544,000  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs  
/dev/sda1        FCBA27CBBA2780EE                       ntfs       SYSTEM
/dev/sda2        1C262C43262C1FEE                       ntfs       HP
/dev/sda3        28BAC428BAC3F07C                       ntfs       FACTORY_IMAGE
/dev/sda5        fd7ce906-95cb-4bb7-a58c-0bc5c4329c4d   swap      
/dev/sda6        e691ee1d-21f1-4481-8122-2a74fa2f06f0   ext4      
/dev/sda7        8aea8ff3-8e38-4721-90a6-256ece5fa132   swap      

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set=root e691ee1d-21f1-4481-8122-2a74fa2f06f0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root e691ee1d-21f1-4481-8122-2a74fa2f06f0
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
menuentry 'Ubuntu, with Linux 3.0.0-15-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e691ee1d-21f1-4481-8122-2a74fa2f06f0
    linux    /boot/vmlinuz-3.0.0-15-generic-pae root=UUID=e691ee1d-21f1-4481-8122-2a74fa2f06f0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e691ee1d-21f1-4481-8122-2a74fa2f06f0
    echo    'Loading Linux 3.0.0-15-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-15-generic-pae root=UUID=e691ee1d-21f1-4481-8122-2a74fa2f06f0 ro recovery nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e691ee1d-21f1-4481-8122-2a74fa2f06f0
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e691ee1d-21f1-4481-8122-2a74fa2f06f0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e691ee1d-21f1-4481-8122-2a74fa2f06f0
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e691ee1d-21f1-4481-8122-2a74fa2f06f0 ro recovery nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
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
    search --no-floppy --fs-uuid --set=root e691ee1d-21f1-4481-8122-2a74fa2f06f0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root e691ee1d-21f1-4481-8122-2a74fa2f06f0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root FCBA27CBBA2780EE
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 28BAC428BAC3F07C
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=e691ee1d-21f1-4481-8122-2a74fa2f06f0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8aea8ff3-8e38-4721-90a6-256ece5fa132 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/initrd.img-3.0.0-15-generic-pae           2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-15-generic-pae              1
               =                initrd.img                                     1
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf sdg

=============================== StdErr Messages: ===============================

unlzma: Decoder error
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

### Post by oldfred on 2012-01-30
I do not see anything wrong with results.txt. You do have an extra swap in sda5 that is not used and a part of wubi in sda3 (/wubildr) which is the recovery partition. Not sure how that would be there.

I might just try reinstalling grub2's boot loader to the MBR. Did you download Boot-Repair? That is usually the easiest way to fix things.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda6 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt

#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You can copy & paste commands from here to terminal in liveCD to avoid typos.

---

### Post by Quackers on 2012-01-30
Are you seeing a grub menu at all at bootup? You should get a screen giving you the choice of which OS to boot.

---

### Post by mr best buy on 2012-01-30
This is what I see ( approximately)
Ubunutu 110.10
previous linex versions
memory test
windows installer
windows  recovery

---

### Post by Quackers on 2012-01-30
The last 2 entries should read
"Windows 7 (loader) (on /dev/sda1)"
and
"Windows Recovery Environment (loader) (on /dev/sda3)"

Is this what you are seeing or something else?

---

### Post by mr best buy on 2012-01-30
Ubunutu with linux 3.0.0-15 generic.pae
Ubunutu with linux 3.0.0-15 generic.pae recovery mode
previous linux version
memory test
windows 7 loader ( on /dev/sda1)
Windows recovery enviroment (loader)



This is more accurete of what I see

---

### Post by rgreener25 on 2012-01-30
> **mr best buy said:**
> I downloaded the 10.11(?)11.10 maybe

---

### Post by Quackers on 2012-01-30
Ok thanks. With that menu on the screen press the down arrow on your keyboard until the "windows 7 loader ( on /dev/sda1)" entry is highlighted. Then press the enter key.
What happens then, please?

---

### Post by mr best buy on 2012-01-30
Ubunutu with linus 3.0.0-15 generic.pae
Ubunutu with linus 3.0.0-15 generic.pae recovery
previous linus versions
windows 7 loader ( on /dev/ sda 1)
windows recovery enviroment (loader) on 1 dev sda 3

---

### Post by Quackers on 2012-01-30
See post #16 above and give results please.

---

### Post by mr best buy on 2012-01-30
yes that was it.  thank you

---

### Post by Quackers on 2012-01-30
I suspected as much.
The grub menu entry you were worried about is the normal grub menu entry for booting Windows. Your system is fine :-)

Please mark the thread as solved using the Thread Tools item near the top of this page as it may help others when searching.

Enjoy! :-)

---

