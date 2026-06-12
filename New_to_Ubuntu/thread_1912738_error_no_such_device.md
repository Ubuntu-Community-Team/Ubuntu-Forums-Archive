---
title: "error no such device"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by Imatech64 on 2012-01-21
Hello everyone

Since this morning I am unable to see the grub menu and the computer stops at 

error: no such device : xxxxxxxxx
grub rescue>

I went through many posts and I have the boot_info_script Result.txt file hereunder ...

If anyone could give a help, I would be very thankfull..

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   300,386,303   300,384,256  83 Linux
/dev/sdc2         300,388,350   312,576,704    12,188,355   5 Extended
/dev/sdc5         303,532,173   312,576,704     9,044,532  82 Linux swap / Solaris
/dev/sdc6         300,388,352   303,532,031     3,143,680  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        94A8764DA8762DBC                       ntfs       
/dev/sdb1        2018BD3718BD0CB2                       ntfs       
/dev/sdc1        5dfbee77-072c-40b6-9da1-346b09ccb0bb   ext4       
/dev/sdc5        7b6934df-40fa-4bf5-8733-a80899f64565   swap       
/dev/sdc6        7349ac86-f303-4c84-8078-b759e834d5a9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set=root 5dfbee77-072c-40b6-9da1-346b09ccb0bb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos1)'
  search --no-floppy --fs-uuid --set=root 5dfbee77-072c-40b6-9da1-346b09ccb0bb
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
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 5dfbee77-072c-40b6-9da1-346b09ccb0bb
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5dfbee77-072c-40b6-9da1-346b09ccb0bb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 5dfbee77-072c-40b6-9da1-346b09ccb0bb
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5dfbee77-072c-40b6-9da1-346b09ccb0bb ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 5dfbee77-072c-40b6-9da1-346b09ccb0bb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 5dfbee77-072c-40b6-9da1-346b09ccb0bb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 94A8764DA8762DBC
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

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=5dfbee77-072c-40b6-9da1-346b09ccb0bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=7349ac86-f303-4c84-8078-b759e834d5a9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by drs305 on 2012-01-21
I have to log off, but a couple of quick questions.

Is sdc the first drive in the BIOS boot order?

At the grub rescue prompt, if you type the following, do you get what I describe after the # symbol?  sdc1 should be (hd2,1). If you come up with nothing, try (hd1,1) or (hd0,1)

```
ls (hd2,1)/ # vmlinuz and initrd.img
ls (hd2,1)/boot # the kernel and initrd files
ls (hd2,1)/boot/grub # Lots of *.mod files and grub.cfg
```

Back later.

---

### Post by Imatech64 on 2012-01-21
Thanks for the reply, though being new , I do not even understand your question


In the meantime .....  yes sdc is the first drive in the BIOS boot order.

---

### Post by Imatech64 on 2012-01-21
On the grub rescue I type

ls (hd2,1) 

no such partition .... was the result

by typing
ls (hd1,1)  

unknown filesystem ... was the result

same for (hd0,1)

---

### Post by sudodus on 2012-01-21
When you see the following text (the grub rescue prompt)
```
grub rescue>
```
Please type the list file command
```
ls (hd2,1)/
``` and finish with the ***Enter*** key. Do you see```
vmlinuz and initrd.img
```
Then continue with the other commands suggested by drs305 to find out what is seen!

Good luck!

---

### Post by sudodus on 2012-01-21
I think you need to repair grub from a live CD or USB drive. Read
[[COLOR="Red"]_https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
[[COLOR="red"]_http://odzangba.wordpress.com/2011/05/14/455/_[/COLOR]]("http://odzangba.wordpress.com/2011/05/14/455/")
[[COLOR="red"]_https://help.ubuntu.com/community/Grub2_[/COLOR]]("https://help.ubuntu.com/community/Grub2")
You can browse the internet for 'repair grub' or 'update grub' to find several other help texts, that might suit better for your particular problem.

---

### Post by Imatech64 on 2012-01-21
First of all thank you

I did type 
ls (hd2,1)ang the result is

error no such partition where as with 1,1 and 0,1 the result was 
unknown filesystem

sorry for late reply but since running on ubuntu livecd to have access to the internet

---

### Post by sudodus on 2012-01-21
> **Imatech64 said:**
> First of all thank you

I did type 
ls (hd2,1)ang the result is

error no such partition where as with 1,1 and 0,1 the result was 
unknown filesystem

sorry for late reply but since running on ubuntu livecd to have access to the internet
This primitive ls command does not recognize ntfs, and it does not find the partition on the third drive, where you have linux. So that drive (/dev/sdc) may not be connected properly.

---

### Post by Imatech64 on 2012-01-21
Thanks again...

I tried the boot-repair without success. 
All HD are connected (checked)....what may be the cause would simply that the HD is dead!

Can I install ubuntu (11.10) on another hard drive and expect the grub menu to appear normally?

---

### Post by sudodus on 2012-01-21
No, it is way too early to give up on the third hard drive. Start a live session from a linux install CD or USB drive and see what devices you can see and mount with the following commands
```
sudo fdisk -lu
```
```
df
```

---

### Post by Imatech64 on 2012-01-21
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba7bba7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156296384    78148161    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2f6267bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392064   244196001    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa1e4a1e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   300386303   150192128   83  Linux
/dev/sdc2       300388350   312576704     6094177+   5  Extended
/dev/sdc5       303532173   312576704     4522266   82  Linux swap / Solaris
/dev/sdc6       300388352   303532031     1571840   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/cow                    772024     51544    720480   7% /
udev                    764632         4    764628   1% /dev
tmpfs                   308812       812    308000   1% /run
/dev/sr1                711980    711980         0 100% /cdrom
/dev/loop0              683136    683136         0 100% /rofs
tmpfs                   772024        16    772008   1% /tmp
none                      5120         4      5116   1% /run/lock
none                    772024       104    771920   1% /run/shm
ubuntu@ubuntu:~$

---

### Post by sudodus on 2012-01-21
***fdisk*** sees the partitions all-right. I forgot to ask you to mount the partitions before running df. In your file browser, please try to mount the partitions of /dev/sdc or use the following commands
```
mount /dev/sdc1 -t auto /mnt
```
and check with
```
df /dev/sdc1
```
unmount it with 
```
umount /dev/sdc1
```
and then mount the next one (substitute sdc[COLOR="Red"]1[/COLOR] with sdc[COLOR="red"]2[/COLOR])

---

### Post by Imatech64 on 2012-01-21
mount /dev/sdc1 -t auto /mnt[FONT=monospace]came with the respond

[/FONT]
[FONT=monospace]ubuntu@ubuntu:~$ mount /dev/sdc1 -t auto /mnt
mount: only root can do that





[/FONT]

---

### Post by VraiChevalier on 2012-01-21
I'm certainly no grub expert but something looks odd in the "Boot Info Summary" output by the "Boot Info Script".

Under "Drive/Partition Info" it shows /dev/sda1 and /dev/sdb1 as having the boot flag set but none of the partitions on /dev/sdc have the boot flag set.

The "Boot Info Summary" shows sda1 with:
Boot files:  /boot.ini /ntldr /NTDETECT.COM

nothing on sdb1 for Boot Files

and sdc1 shows this:
Boot files:  /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

Should perhaps sdc1 have the boot flag set?

---

### Post by Imatech64 on 2012-01-21
Thank you VraiChevalier..
I apolodgize not to understand your question

"Should perhaps sdc1 have the boot flag set? 	"

I have no idea how to set a boot flag.

---

### Post by sudodus on 2012-01-21
> **Imatech64 said:**
> mount /dev/sdc1 -t auto /mnt[FONT=monospace]came with the respond

[/FONT]
[FONT=monospace]ubuntu@ubuntu:~$ mount /dev/sdc1 -t auto /mnt
mount: only root can do that
[/FONT] Then you need 
```
sudo mount /dev/sdc1 -t auto /mnt
```
```
sudo df /dev/sdc1
```
and ```
sudo umount /dev/sdc1

```

---

### Post by sudodus on 2012-01-21
> **VraiChevalier said:**
> I'm certainly no grub expert but something looks odd in the "Boot Info Summary" output by the "Boot Info Script".

Under "Drive/Partition Info" it shows /dev/sda1 and /dev/sdb1 as having the boot flag set but none of the partitions on /dev/sdc have the boot flag set.

The "Boot Info Summary" shows sda1 with:
Boot files:  /boot.ini /ntldr /NTDETECT.COM

nothing on sdb1 for Boot Files

and sdc1 shows this:
Boot files:  /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

Should perhaps sdc1 have the boot flag set?
Glad you saw it :-)

*Imatech64*, from the live session again, run ***gparted*** and set the boot flag for /dev/sdc1.

---

### Post by Imatech64 on 2012-01-21
I think it worked for sdc1.

I tried for sdc2 but ...

Here is the outcome:


ubuntu@ubuntu:~$ sudo mount /dev/sdc1 -t auto /mnt
ubuntu@ubuntu:~$ sudo df /dev/sdc1
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1            147835352   3001668 137324080   3% /mnt
ubuntu@ubuntu:~$ sudo umount /dev/sdc1
ubuntu@ubuntu:~$ sudo mount /dev/sdc2 -t auto /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ 

Should I try rebooting?

---

### Post by sudodus on 2012-01-21
Sorry sdc2 is extended (only a container for logical partitions inside it, which are swap partitions). So it is enough that we know you can mount sdc1. I am pretty sure that it is good. But you may need add a boot flag.

If that does not work, I suggest that you dig deeper into the three links I supplied in post #6.

---

### Post by Imatech64 on 2012-01-21
Thank you so much Sudodus for the time spend and the precious advices.

I will try to boot and see .

If I understood from VraiChevalier, I can add a boot flag through gparted app.

---

### Post by Imatech64 on 2012-01-21
Well, sorry to inform that after reboot , I ended to grub rescue prompt.

---

### Post by Imatech64 on 2012-01-21
Thank you all for your help.

---

### Post by sudodus on 2012-01-21
- Did you manage to set the boot flag?

- Did you dig deeper into the three links I supplied in post #6: did you really try various tips in order to get a working grub system?

I think it is too early to give up and try to reinstall linux.

---

### Post by Imatech64 on 2012-01-21
Allow me to answer :

- yes I managed to set a boot flag on sdc with gparted

- Yes I spend a long time reading post#6 as well as many others with similar search

- tried the boot-repair after all that

And I know much much, thanks ti you all, but as result I am still at my post#1 with the grub rescue.

Tired for today , I will continue tomorrow , in case anybody got an idea.

---

### Post by sudodus on 2012-01-21
Sorry we could not help you today. But the good thing is that sometimes during sleep, the solution will come to you, either by yourself or from someone from another time zone ;-)

If not,

1. backup your data from the third drive /dev/sdc

2. repartition it using gparted in a live session from the CD or USB drive

- one primary partition for the Ubuntu file system (maybe you want to make a different size than before). But if it is OK to have ~ 150 GB for the system and ~ 6 GB for swap, you need only to clear the logical partitions inside the extended partition and make new ones.

- one extended partition of the rest of the drive with

. one swap area with size equal to the RAM or double RAM size.

. one data partition of the rest of the space (NTFS if you want data to read/write data after booting into either Windows or Ubuntu, otherwise ext3 file system)

3. Install Ubuntu from the installation CD or USB drive. ***Select the manual method for partitioning*** (don't let the installer do it, use what you did with gparted: /dev/sdc1 should be used as root file system, the symbol /

*. The installer finds the swap partition automatically.

---

### Post by drs305 on 2012-01-21
I'd also just like to confirm the "ls (hd2,1)/" command results at the Grub prompt. Did you include the "/" at the end of the command?  

"ls (hd2,1)" is not the same as "ls (hd2,1)/" as far as Grub is concerned.

---

