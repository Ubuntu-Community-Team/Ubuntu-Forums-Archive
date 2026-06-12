---
title: "screwed up installation"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by nerdinator on 2012-06-04
I installed Ubuntu over  Windows 7 on my new XPS laptop.

Initially, there were the following partitions on Windows:
1. sda1 - Dell Utility
2. sda2 - Windows recovery drive
3. sda3- C drive (Windows OS)
There was also a D drive that was already there in the new laptop.(not sure which kind of partition it was).

So I opened Disk Management on Windows and freed some 180GB from sda3 (Windows:OS partition) and left it there.

Then I booted from my USB with Ubuntu and selected "Something Else" during the install.
The partitioning menu showed up  and I selected "free space" and added the following new partitions to it.
1. **swap**    type:swap    4 GB 
2. **home**   type:ext4     mount at :/home 60GB
3. **root      **type:ext4     mount at :/ 60 GB

I decided to make an extra partition here for some storage purposes and I clicked on the partition corresponding to the D** drive on my Windows** ,deleted it and it became free space. 
***I created a new ext4 partition(100GB) from this of type :ext4 **and another one with **remaining space(this one for the** D drive **in Windows) type:**FAT32**.
One problem I encountered is that I had a choice of mount point(**for both the above**) between /dos and /windows.  I wasn't sure of which to choose. 
I didn't specify any and clicked on Continue. It gave me an error that said that I had to choose a mount point or else it may not be possible to mount it later(inaccurately reproduced,sorry). I clicked on continue and finished the installation.

I restart and open home and I see on the left side,under Devices,the following:
1.OS(corresponding to C drive) ,;**  I unmount it a hundred times and won't go away.**
2.a 100 GB one,that had a lost and found folder. I open that folder and it **says I don't have the rights to open it**. It doesn't ask me for a password or anything. Just doesn't let me open it. 
3.one corresponding to my D drive on Windows.

I rush back to Windows,only to find that my D drive can't be opened. I doesn't show that bar below it which shows how much data is filled. It just doesn't open and it gives an error.

I format the D drive (as **NTFS**) on Windows and then it gets alright.

**Another main problem:
I rush back to Ubuntu and open Disk Utility:
It gives the following warnings:
**The partition is misaligned by 512 bytes ,repartitioning is suggested.** - (for _***the Dell Utility partition***_  this **partition** was there even when I got my new laptop).
**The partition is misaligned by 1024 bytes ,repartitioning is suggested.** - for the Extended Partition containing all my Ubuntu logical partitions+ my D drive partition + the other ext4 partition.

Please help me.
Thank You

---

### Post by wilee-nilee on 2012-06-04
Download this link with a live ubuntu cd, extract it to your desktop and run the command.

Copy and paste all the text from the results.txt to a reply, highlight  all the text while the reply is still open and click on the # in the  reply panel.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by nerdinator on 2012-06-04
I'm sorry,I don't understand what you mean by download with a live Ubuntu cd. Please explain.

---

### Post by nerdinator on 2012-06-04
See screenshots

---

### Post by oldos2er on 2012-06-04
> **nerdinator said:**
> I'm sorry,I don't understand what you mean by download with a live Ubuntu cd. Please explain.

Boot from your Ubuntu LiveCD, open Firefox, then the URL wilee-nilee gave you. The bootinfo script should give us a clear picture of what's going on with your harddisks.

I hope you have backups of any sensitive data!

---

### Post by nerdinator on 2012-06-05
It's a new laptop. Nothing to backup. Hope atleast Windows won't have to get removed.

Here it is:

 ```
                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

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
    Boot files:        /Windows/System32/winload.exe

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
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 31088 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    27,865,087    27,783,168   7 NTFS / exFAT / HPFS
/dev/sda3          27,865,088   343,269,375   315,404,288   7 NTFS / exFAT / HPFS
/dev/sda4         343,271,422 1,953,523,711 1,610,252,290   5 Extended
/dev/sda5         343,271,424   351,268,863     7,997,440  82 Linux swap / Solaris
/dev/sda6         351,270,912   471,269,375   119,998,464  83 Linux
/dev/sda7         471,271,424   591,269,887   119,998,464  83 Linux
/dev/sda8         591,271,936   791,269,375   199,997,440  83 Linux
/dev/sda9         791,271,424 1,953,523,711 1,162,252,288   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192     7,843,839     7,835,648   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5450-4444                              vfat       DellUtility
/dev/sda2        4248184648183ADD                       ntfs       RECOVERY
/dev/sda3        20081BCC081B9FB8                       ntfs       OS
/dev/sda5        878843ca-d423-46ec-9003-ad5c4a1e3508   swap       
/dev/sda6        7493f7eb-c399-4732-86b8-fd2d324156fe   ext4       
/dev/sda7        3dd7fdfc-803e-4caf-829a-d20c5a9e4c84   ext4       
/dev/sda8        465b3045-2a63-4e8e-a177-8c8c5d4f93b3   ext4       New Volume
/dev/sda9        A2C6F784C6F756CF                       ntfs       Data
/dev/sdb1        543A-C99F                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root 7493f7eb-c399-4732-86b8-fd2d324156fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 7493f7eb-c399-4732-86b8-fd2d324156fe
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7493f7eb-c399-4732-86b8-fd2d324156fe
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=7493f7eb-c399-4732-86b8-fd2d324156fe ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7493f7eb-c399-4732-86b8-fd2d324156fe
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=7493f7eb-c399-4732-86b8-fd2d324156fe ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7493f7eb-c399-4732-86b8-fd2d324156fe
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=7493f7eb-c399-4732-86b8-fd2d324156fe ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7493f7eb-c399-4732-86b8-fd2d324156fe
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=7493f7eb-c399-4732-86b8-fd2d324156fe ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
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
    search --no-floppy --fs-uuid --set=root 7493f7eb-c399-4732-86b8-fd2d324156fe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7493f7eb-c399-4732-86b8-fd2d324156fe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 4248184648183ADD
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
UUID=7493f7eb-c399-4732-86b8-fd2d324156fe /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=3dd7fdfc-803e-4caf-829a-d20c5a9e4c84 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=878843ca-d423-46ec-9003-ad5c4a1e3508 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               1
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

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

=============================== StdErr Messages: ===============================

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
/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

### Post by wilee-nilee on 2012-06-05
Thanks for posting the script. 

**So if you could explain now, what happens when you power on now.** You should be getting a grub boot menu, it is missing the windows stanza as of now, but that should show if you run this command in the ubuntu install, in the terminal.
```
sudo update-grub
```your first post is hard to understand at least for me in a couple of ways, I know you were trying to explain stuff though. ;)

Partitions for us are letters and numbers, like sda1, sda2...etc, not D or C.

From what I can tell the script looks good as far as mount points, but it is a complex script to read.

You want to aware to that windows will not open the ubuntu ext type partitions, but ubuntu can open the windows NTFS type, or a fat as well.

---

### Post by nerdinator on 2012-06-05
Um I'm sorry,I don't understand again.
I get the GRUB boot menu and that is working fine. I can choose my OS properly. It is showing a Windows 7 option as well.
So what is that Windows stanza it is missing?

Should I type ```
sudo update-grub
``` again by booting via a USB drive?

> your first post is hard to understand at least for me in a couple of ways, I know you were trying to explain stuff though. 
What part is unclear. I'll try to explain better. :) 
> Partitions for us are letters and numbers, like sda1, sda2...etc, not D or C.
Yes,but I was drawing a correspondence. They refer to the same physical location right? 

> 
You want to aware to that windows will not open the ubuntu ext type partitions, but ubuntu can open the windows NTFS type, or a fat as well.

Yes. I am trying to open any ext partition on windows. I only tried opening the FAT32 partition(corresponding to D drive) on Windows. It didn't open. So I had to reformat it as NTFS and then it opened. The story behind it is in my first post. Should I explain this part better?

---

### Post by nerdinator on 2012-06-05
Basically,I wanted the following partitions:
1. sda1 Dell Utility which was already there.
2. sda2 Windows recovery which was already there.
3. sda3 Windows OS partition,which was already there.

4. /home partition, a separate one ,a logical partition. (**corresponding to 61 GB ext4 the image**)
5. /swap partition  ,a logical partition. (**corresponding to swap 4.1GB in the image**)
6. / root partition, for Ubuntu OS a logical partition
7. an extra ext4 partition for storage ,a logical partition. (**corresponding to New Volume 102GB in the image**)
8. a FAT32 / NTFS partition for storage under both OSes (corresponding to D drive on Windows) ,a logical partition
*(**Corresponding to Data(595 GB) in the image I posted**)*

**Note**: I wanted an NTFS partition for **number 8** but during installation Ubuntu didn't provide me with an option of that.

So I had to settle with FAT32. This FAT32 partition(D drive) didn't open on windows .So I had to reformat it as NTFS. Then it worked.


this arrangement can be seen on the images I posted.

---

### Post by wilee-nilee on 2012-06-05
You can make a ntfs on the live Ubuntu cd with gparted the partitioner before the install if you want. Windows will see this even if in the extended as you see now. Gparted has to be installed on a installed Ubuntu. Linux also will not adjust a partition on a running OS, you have to use a live cd to do this.

Not sure why the fat was not seen, but honestly fat is a bad choice on a HD, unless there is some specific use for it, read the web for differences on ntfs and fat partitions please.

The reason we only reference partitions as sda1, or sdb2....etc, is that is a exacting description, and Linux does not use letters. When you start referencing both descriptions it gets really confusing. We don't know which is which as far as the letters go, so we have to rely on a user to be exact, and if they are not
a OS can get bricked, personally it is the Joe Friday approach just the facts, not the narrative as to why and how you got to where you're at. 

This gets really hard when the user is new and mixes all these variables together the partition letters, and with the misunderstanding of when, where and how to build partitions and with what tools.

My brain is about the size of a walnut, but does well in-spite of this, lol. ;) Some users can read a post that is rather confusing to the majority of the helpers here and understand it, but they are far and few between, and it just cuts down on the efficiency of getting you helped and the quality of this help.

You are doing good though, it just takes time to recognize the differentials in how the open source community does things, and adapting to this. 

Keep the threads simple and isolated to single problems, sometimes there are more than one problem just reason the best way to link these together. You can always start another thread, you will not get a infraction for doing this. 

As far as I can tell you are all set with a running set up at this point.

---

### Post by nerdinator on 2012-06-06
Hi. 
My problem now is just that there is a misalignmemt. My laptop is new,so I just don't want to settle it with a quick fix. I was thinking of a linux reinstall with repartition of the whole extended partition. 2 issues. There is misalignment in dell utilty partition,sda1. Can't get fixed that way. And I don't know what went wrong the 1st time. Please suggest safe ,corrective steps.

---

