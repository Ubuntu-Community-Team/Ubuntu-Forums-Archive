---
title: "cloning windows hard drive with dd"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Logan Fife on 2012-06-05
Hi, I have searched here and google, but the results are a bit over my head.

I want to move my windows 7 installation to a hard drive with more space, and install ubuntu along side it in dual boot. its a laptop, so i can only fit one drive at a time, but i do have a usb portable hard drive with enough space to hold the windows 7 drive.

if i copy the windows hard drive onto the portable one, will i lose the other data on the portable? 

can i then swap the internal hdds for the bigger one and copy it back across?

I tried to read the dd man page, but i don't understand what any of it means:sad:

also, I found this:
[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)
but its copying it to an unformatted drive, and i have lots of videos and music on the portable i would rather not burn all over again. 
could i use gparted to create some unformatted space on the expansion and just follow this instructions?

 thanks very much, and sorry if i'm not being clear, I'm a bit confused!

---

### Post by mapes12 on 2012-06-05
I've read the link and I think if you create some space with Gparted on the drive that is = or > than your Win installation it will work.  

I've used dd before to clone drives and it worked perfectly. But I used an unformated drive with no other data on it as the target.

The big problem for you is trying this stuff on a drive where you have data you want to keep. Personally, I would back it up somewhere before starting all this.

Mark

---

### Post by wilee-nilee on 2012-06-05
I would use clonezilla, then you have a clone, and the original is not destroyed in the process, a text clone but fairly straight forward.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by C.S.Cameron on 2012-06-05
Dd will clone everything from one drive to another.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by Mark Phelps on 2012-06-05
IF you're simply migrating a Win7 install from one drive to another, you should really use Windows apps to do this.  One very good free one is Macrium Reflect.  Just download and install it in Win7, then image the Win7 install to the portable drive.  If you have a 100 or 200MB system partition, image that too.  This will take up less space than a clone because MR does compression on the image.

You will need to use the option to create and burn a Linux Boot CD for MR.

Then, you can boot from that CD and "restore" the image to another drive -- just make sure you have enough unallocated space on the new drive to hold both of the original Win7 partitions.

---

### Post by Paqman on 2012-06-05
> **wilee-nilee said:**
> I would use clonezilla

So would I. The problem with dd is that it copies everything, including the free space. That means it can be very, very slow on a modern drive with many GB of free space on it.

---

### Post by mapes12 on 2012-06-05
I know this is completely the wrong forum but I also need to migrate a Win 7 partition to another machine. It's on a Bootcamp partition on a Macbook. Size is 34GB.

I want it off the Mac to free up space then put it on a PC.

Tell me to go eleswhere if required :( but any pointers to do this would be very welcome.

Mark

---

### Post by wilee-nilee on 2012-06-05
> **mapes12 said:**
> I know this is completely the wrong forum but I also need to migrate a Win 7 partition to another machine. It's on a Bootcamp partition on a Macbook. Size is 34GB.

I want it off the Mac to free up space then put it on a PC.

Tell me to go eleswhere if required :( but any pointers to do this would be very welcome.

Mark

With your own issues always make your own thread, this just keeps the threads clean and focused on the OP's situation.

---

### Post by Logan Fife on 2012-06-05
Thanks for all the Replies!

I tried it with dd first, as i don't have quick access to blank cds, but do have several ubuntu live ones. 

heres what i did:
I took apart the external drive casing, and put the windows7 hdd in there, so now it works on usb!

then i deleted an unused partition to make space (using ubuntu disk utility)
i tried to use dd, but fdisk -l didn't list it.

so i went back into disk utility and turned the empty space into a ntfs partition.
fdisk now lists it as sda1, so i used dd to copy it across, which took ages.

finally, I updated grub. which picked up and recognised the windows installation, but when i select it from the boot menu, it says windows boot manager failed because something required is unavailable.

have I made a complete mess of this? oh, I also removed the "bootable" flag from the extended sda2 partition. heres the output of fstab blkid and fdisk. I don't know if these are of any help in diagnosing my stupidity?
sudo fdisk -l
```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00041904

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   294310799   147155368+   7  HPFS/NTFS/exFAT
/dev/sda2       294322174   976773119   341225473    5  Extended
/dev/sda5       489662464   734903852   122620694+  83  Linux
/dev/sda6       958879744   976773119     8946688   82  Linux swap / Solaris
/dev/sda7       294322176   489662463    97670144   83  Linux
/dev/sda8       734904320   958871551   111983616   83  Linux

Partition table entries are not in disk order

```cat /etc/fstab```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=2e92e572-7429-403e-9c55-3122ae06c58a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bdd8b039-a6d9-4a4e-9a1e-01a99fa65517 none            swap    sw              0       0

``` sudo blkid```

/dev/sda1: LABEL="windows" UUID="56DCCD26DCCD00EB" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu 10.04 LTS" UUID="799f22a5-3957-42d5-8946-18a60c991c4d" TYPE="ext4" 
/dev/sda6: UUID="bdd8b039-a6d9-4a4e-9a1e-01a99fa65517" TYPE="swap" 
/dev/sda7: LABEL="Xubuntu 12.04 LT" UUID="5cf4b598-35b7-4986-9b2f-7efad65212a6" TYPE="ext4" 
/dev/sda8: UUID="2e92e572-7429-403e-9c55-3122ae06c58a" TYPE="ext4" 

```and df -h```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda8       107G  5.9G   96G   6% /
udev            1.5G  8.0K  1.5G   1% /dev
tmpfs           595M  856K  595M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  340K  1.5G   1% /run/shm

```Thanks for taking your time to read this, Harry

---

### Post by wilee-nilee on 2012-06-05
Lets use the booscript to look at the set up. Download the link and extract it to the desktop using a ubuntu install or live cd. Run the command in the terminal. You will see a results.txt appear, copy and paste all of the text from it to a reply. While the reply is still open, highlight all the text and click on the # in the reply panel, this wraps the text in code tags.

Make sure the new hd is scanned with this script.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by Logan Fife on 2012-06-05
Thanks Wilee-Nilee, here is the output from the results.txt its a huge amount of data

what does bash do in the terminal?

```


                Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       234436481 sectors, but according to the info from 
                       fdisk, it has 294310736 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   294,310,799   294,310,737   7 NTFS / exFAT / HPFS
/dev/sda2         294,322,174   976,773,119   682,450,946   5 Extended
/dev/sda5         489,662,464   734,903,852   245,241,389  83 Linux
/dev/sda6         958,879,744   976,773,119    17,893,376  82 Linux swap / Solaris
/dev/sda7         294,322,176   489,662,463   195,340,288  83 Linux
/dev/sda8         734,904,320   958,871,551   223,967,232  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        56DCCD26DCCD00EB                       ntfs       windows
/dev/sda5        799f22a5-3957-42d5-8946-18a60c991c4d   ext4       Ubuntu 10.04 LTS
/dev/sda6        bdd8b039-a6d9-4a4e-9a1e-01a99fa65517   swap       
/dev/sda7        5cf4b598-35b7-4986-9b2f-7efad65212a6   ext4       Xubuntu 12.04 LT
/dev/sda8        2e92e572-7429-403e-9c55-3122ae06c58a   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 799f22a5-3957-42d5-8946-18a60c991c4d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 799f22a5-3957-42d5-8946-18a60c991c4d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-41-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 799f22a5-3957-42d5-8946-18a60c991c4d
    linux    /boot/vmlinuz-2.6.32-41-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 799f22a5-3957-42d5-8946-18a60c991c4d
    echo    'Loading Linux 2.6.32-41-generic ...'
    linux    /boot/vmlinuz-2.6.32-41-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 799f22a5-3957-42d5-8946-18a60c991c4d
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 799f22a5-3957-42d5-8946-18a60c991c4d
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 799f22a5-3957-42d5-8946-18a60c991c4d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 799f22a5-3957-42d5-8946-18a60c991c4d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=799f22a5-3957-42d5-8946-18a60c991c4d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bdd8b039-a6d9-4a4e-9a1e-01a99fa65517 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             2
               =                boot/initrd.img-2.6.32-24-generic              1
               =                boot/initrd.img-2.6.32-41-generic              1
               =                boot/vmlinuz-2.6.32-24-generic                 1
               =                boot/vmlinuz-2.6.32-41-generic                 1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=5cf4b598-35b7-4986-9b2f-7efad65212a6 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=5cf4b598-35b7-4986-9b2f-7efad65212a6 ro recovery nomodeset 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=5cf4b598-35b7-4986-9b2f-7efad65212a6 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=5cf4b598-35b7-4986-9b2f-7efad65212a6 ro recovery nomodeset 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-41-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 799f22a5-3957-42d5-8946-18a60c991c4d
    linux /boot/vmlinuz-2.6.32-41-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro quiet splash
    initrd /boot/initrd.img-2.6.32-41-generic
}
menuentry "Ubuntu, with Linux 2.6.32-41-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 799f22a5-3957-42d5-8946-18a60c991c4d
    linux /boot/vmlinuz-2.6.32-41-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro single
    initrd /boot/initrd.img-2.6.32-41-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 799f22a5-3957-42d5-8946-18a60c991c4d
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 799f22a5-3957-42d5-8946-18a60c991c4d
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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
UUID=5cf4b598-35b7-4986-9b2f-7efad65212a6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bdd8b039-a6d9-4a4e-9a1e-01a99fa65517 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=========================== sda8/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 2e92e572-7429-403e-9c55-3122ae06c58a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root 2e92e572-7429-403e-9c55-3122ae06c58a
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 2e92e572-7429-403e-9c55-3122ae06c58a
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=2e92e572-7429-403e-9c55-3122ae06c58a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 2e92e572-7429-403e-9c55-3122ae06c58a
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=2e92e572-7429-403e-9c55-3122ae06c58a ro recovery nomodeset 
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 2e92e572-7429-403e-9c55-3122ae06c58a
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=2e92e572-7429-403e-9c55-3122ae06c58a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 2e92e572-7429-403e-9c55-3122ae06c58a
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=2e92e572-7429-403e-9c55-3122ae06c58a ro recovery nomodeset 
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 2e92e572-7429-403e-9c55-3122ae06c58a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 2e92e572-7429-403e-9c55-3122ae06c58a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 56DCCD26DCCD00EB
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-41-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 799f22a5-3957-42d5-8946-18a60c991c4d
    linux /boot/vmlinuz-2.6.32-41-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro quiet splash
    initrd /boot/initrd.img-2.6.32-41-generic
}
menuentry "Ubuntu, with Linux 2.6.32-41-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 799f22a5-3957-42d5-8946-18a60c991c4d
    linux /boot/vmlinuz-2.6.32-41-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro single
    initrd /boot/initrd.img-2.6.32-41-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 799f22a5-3957-42d5-8946-18a60c991c4d
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 799f22a5-3957-42d5-8946-18a60c991c4d
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=799f22a5-3957-42d5-8946-18a60c991c4d ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
    linux /boot/vmlinuz-3.2.0-24-generic root=UUID=5cf4b598-35b7-4986-9b2f-7efad65212a6 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-24-generic
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
    linux /boot/vmlinuz-3.2.0-24-generic root=UUID=5cf4b598-35b7-4986-9b2f-7efad65212a6 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-24-generic
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=5cf4b598-35b7-4986-9b2f-7efad65212a6 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 5cf4b598-35b7-4986-9b2f-7efad65212a6
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=5cf4b598-35b7-4986-9b2f-7efad65212a6 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 56DCCD26DCCD00EB
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=2e92e572-7429-403e-9c55-3122ae06c58a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bdd8b039-a6d9-4a4e-9a1e-01a99fa65517 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 a8  a4 0b 2d 16 9e 0e 00 fe  |..........-.....|
000001d0  ff ff 05 fe ff ff 69 38  9c 27 99 27 11 01 00 00  |......i8.'.'....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
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

### Post by wilee-nilee on 2012-06-05
So you have 3 Ubuntu installs, hehe looks like my hard drive. It looks like the sda7 is the controlling boot, which ever one is at the top of the grub menu, if you have not modified grub is the controller. I could be wrong on which Ubuntu controllinging the boot so that is why I mention the first one has the control.

You have the bootflag on the sda1 as you should, Ubuntu does not use a bootflag windows does, in order to make that a partition active.

So in the controlling ubuntu run this command.
```
sudo update-grub
```This should rewrite grub and have windows booting if all is well there. Windows is showing the correct files, but if needed we can rebuild those files using  recovery or install disc for windows.

As far as I can tell the script looks good and all the OS should boot if they are all there.

---

### Post by Logan Fife on 2012-06-05
Thanks Wilee,

sudo update-grub moved windows 7 higher up the list, but i still get the error message.

```
Windows failed to start. A Recent hardware or software change might be the cause. 
To fix the problem:   
1. Insert your windows installation disc and restart your computer. 
2. Choose your langugae settings, and then click next 
3. Click "repair your computer." 

 **Status: 0xc000000e Info: The boot selection failed because a required device is inaccessible.** 
```yeah, sda7 is the most recent install, ubuntu 12.04. I've kept 10.04 on there because i'm not sure i like unity, and the third is Xubuntu, which is nice but unfamiliar! choices choices:smile:

---

### Post by wilee-nilee on 2012-06-05
The repair quite often has problems with grub in the mbr.

So I would boot the recovery or install disc and run this command first to reload the mbr with the windows bootloader.
```
bootrec.exe /fixmbr
```Then reboot the same disc to the repair, I have seen advice to run the repair three time so use your own intuition here.

If you are still having problems it may be due to the boot needing to be rebuilt as well and hard to say but maybe more repairs, maybe a chkdsk as well. So here are the commands for a full repair that has a chkdsk as part of this. There is a W7 forums link at the end for a reference on getting to the repair and terminal on the disc.

                                  [FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /fixmbr (#updates MBR master boot) [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]chkdsk /r [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /FixBoot (#updates PBR partition boot) [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /ScanOs [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /RebuildBcd [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html 
[/SIZE][/FONT]
[FONT=Verdana, sans-serif][SIZE=1]It may be that the PBR is part of the problem and a chkdsk is needed as well, I can't channel that info, lol.[/SIZE][/FONT]

[FONT=Verdana, sans-serif][SIZE=1]If you do not have a a recovery disc you can buy one on line.[/SIZE][/FONT]
[FONT=Verdana, sans-serif][SIZE=1]http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/

Here is a little information on these commands from Microsoft as well. 

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If the repair or the commands don't find the windows install you may have to run when using the terminal C: before the command, I think this is the correct configuration.

I suspect it is the PBR, so if me I would forgo the auto repair and go straight to the commands the whole set and recognize they may need to be pointed at the C partition, but that&#8217;s me. It may be that the repair finds no problems as well, but still does not boot.

If you get windows booting straight in you will just have to reload grub to the mbr as well.
[/SIZE][/FONT]

---

### Post by BigCityCat on 2012-06-06
> **Mark Phelps said:**
> IF you're simply migrating a Win7 install from one drive to another, you should really use Windows apps to do this.  One very good free one is Macrium Reflect.  Just download and install it in Win7, then image the Win7 install to the portable drive.  If you have a 100 or 200MB system partition, image that too.  This will take up less space than a clone because MR does compression on the image.

You will need to use the option to create and burn a Linux Boot CD for MR.

Then, you can boot from that CD and "restore" the image to another drive -- just make sure you have enough unallocated space on the new drive to hold both of the original Win7 partitions.

This is very good advice. Macrium is very good freeware.

---

### Post by wilee-nilee on 2012-06-06
This was a dd from the original not sure there is any going to a gui based cloner at this point.

---

### Post by Logan Fife on 2012-06-06
It Works!
fantastic, Thank you! 
does it matter that fdisk disagrees with the boot sector? I ran the boot info script since fixing windows and it still says this.

```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       234436481 sectors, but according to the info from 
                       fdisk, it has 294310736 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
```the boot sector is reporting the size of the old hard drive, while fdisk is reporting the size of the ntfs partition i created before using dd.

thanks again!

for those interested in what I did, I just put the old hard drive back in the machine and created a windows 7 recovery cd, then booted into that. it only gave me one option, "repair and restart" which fixed the error quickly, and left grub as it was to boot! ( bad pun intended)
the dd command i did to start this was from a live cd:
```
sudo dd if=/dev/sdc1 of=/dev/sda1
```where /dev/sdc1 was the original hdd in a portable usb case, and /dev/sda1 was the empty ntfs partition i created

perhaps I should have used a windows programme like Macrium Reflect, and probably will next time, but i tried dd first as it was the quickest "route to market" if it worked, and no real consequence if it failed. (given that i didn't wipe the original!), plus it was the only one that seemed to give me the option of keeping my current ubuntu installations.

---

### Post by oldfred on 2012-06-06
Windows does not normally boot if NTFS partition boot sector does not match the partition table. It has to have the correct size info in it. May have to do with old vs. new partition.

Fixboot should have updated that info and/or chkdsk. Sometimes you have to run chkdsk more than once.

---

### Post by wilee-nilee on 2012-06-06
> **Logan Fife said:**
> It Works!
fantastic, Thank you! 
does it matter that fdisk disagrees with the boot sector? I ran the boot info script since fixing windows and it still says this.

```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       234436481 sectors, but according to the info from 
                       fdisk, it has 294310736 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
```the boot sector is reporting the size of the old hard drive, while fdisk is reporting the size of the ntfs partition i created before using dd.

thanks again!

for those interested in what I did, I just put the old hard drive back in the machine and created a windows 7 recovery cd, then booted into that. it only gave me one option, "repair and restart" which fixed the error quickly, and left grub as it was to boot! ( bad pun intended)
the dd command i did to start this was from a live cd:
```
sudo dd if=/dev/sdc1 of=/dev/sda1
```where /dev/sdc1 was the original hdd in a portable usb case, and /dev/sda1 was the empty ntfs partition i created

perhaps I should have used a windows programme like Macrium Reflect, and probably will next time, but i tried dd first as it was the quickest "route to market" if it worked, and no real consequence if it failed. (given that i didn't wipe the original!), plus it was the only one that seemed to give me the option of keeping my current ubuntu installations.

Glad you're up and running, dd actually runs no faster then a imager/cloner, I would not touch dd with a ten foot pole personally. ;)

I use clonezilla, it has never failed for me in over a 100 or so clones, and it saves the mbr, it does not get much easier really.

---

### Post by HermanAB on 2012-06-07
Simple really, since duplicating a disk is a one liner.

Install second disk drive.
Boot off a CDROM.
Use dmesg, mount and df to ensure that you know which is which.  Getting the disk names the wrong way around will be very disappointing.

Copy drive using cat:
$ sudo cat /dev/sda > /dev/sdb

Or copy drive using Data Definition:
$ sudo dd if=/dev/sda of=/dev/sdb

then go and watch a ball game.

You can speed dd up a bit by defining a larger block size.  Read the man page.

Otherwise, if you are dysfunctional and really cannot type a one liner, use Clonezilla.

---

### Post by wilee-nilee on 2012-06-07
> **HermanAB said:**
> Simple really, since duplicating a disk is a one liner.

Install second disk drive.
Boot off a CDROM.
Use dmesg, mount and df to ensure that you know which is which.  Getting the disk names the wrong way around will be very disappointing.

Copy drive using cat:
$ sudo cat /dev/sda > /dev/sdb

Or copy drive using Data Definition:
$ sudo dd if=/dev/sda of=/dev/sdb

then go and watch a ball game.

You can speed dd up a bit by defining a larger block size.  Read the man page.

Otherwise, if you are dysfunctional and really cannot type a one liner, use Clonezilla.

Dysfunctional, hey, that’s the girlfriends line. ;)

---

### Post by Paqman on 2012-06-07
> **HermanAB said:**
> 
Otherwise, if you are dysfunctional and really cannot type a one liner, use Clonezilla.

I'm assuming this is a bit tongue-in-cheek, but there are certainly cases where using Clonezilla will be much better than dd, such as large disks with small amounts of data on them.

---

