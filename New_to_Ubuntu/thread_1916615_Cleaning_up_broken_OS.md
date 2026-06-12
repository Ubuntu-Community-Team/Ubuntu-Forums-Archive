---
title: "Cleaning up broken OS"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by gerryl on 2012-01-28
Please be patient with the newbie :(

I broke my 11.10 - I apparently overachieved in deleting what I thought were old, obsolete files in /boot.  The system would not reboot.

I had a CD with 10.04, so I installed that in a new partition which enabled me to recover my user files.  I then updated the 10.04 to 11.10, but I still have the old, broken 11.10 in its partition.  How do I clean up/get rid of this broken OS without risking losing my user files (which ARE backed up!!)?

Here is the Gparted analysis of my system.

---

### Post by sanderd17 on 2012-01-28
If you are able to remove an entire partition, you can boot a live CD, delete that partition with gparted and enlarge another partition (the one in which you could use more space). (you should probably delete /dev/sda6, and enlarge /dev/sda7)

Do know, when you touch partitions, there's always a chance of corrupting the entire hard disk. So be sure your backup is on another hard disk.

---

### Post by WasMeHere on 2012-01-28
> **sanderd17 said:**
> If you are able to remove an entire partition, you can boot a live CD, delete that partition with gparted and enlarge another partition (the one in which you could use more space). (you should probably delete /dev/sda6, and enlarge /dev/sda7)

Do know, when you touch partitions, there's always a chance of corrupting the entire hard disk. So be sure your backup is on another hard disk.
+1

You wrote that you already have backup up your data files. Then do what sanderd17 suggests, delete the old partition and after that expand your new one into that space (unless you don't need it and want to use the space as an own partition for experimental systems).

Good luck
Olle

---

### Post by grahammechanical on 2012-01-28
Now you can either install 10.04 into the old 11.10 partition and upgrade the 10.04 to 11.10 and transfer your data across. Or download a 11.10 ISO and use that to re-install 11.10 in its old partition and then transfer your data across.

At that point you can remove/delete the partition you created or keep it as a partition to test new releases or other distributions. It will only need about 15-20GB of space.

I had to do what you are doing a few years ago. I now like to see if I can set up a new release of Ubuntu the way I like it before upgrading. I do all my modifications on my testing partition before trying them out on my working partition.

It is one thing to break a test installation but something else to break the working install.

Regards.

---

### Post by coffeecat on 2012-01-28
Just to add - a side issue, but important:

> **gerryl said:**
> I broke my 11.10 - I apparently overachieved in deleting what I thought were old, obsolete files in /boot.  The system would not reboot.

My guess is that you accidentally deleted a current kernel file. Once you have your new system up and running and if you find yourself in the position of needing to clean out old kernels, it's not a good idea to delete them directly from /boot. There are other kernel files in /lib/modules and /usr/src. Use a package manager to clean out old kernels. That way the grub menu is automatically updated for you. When you need to do this, and if you need help, start a new thread and someone will help you with this.

---

### Post by ajgreeny on 2012-01-28
Don't forget that to upgrade from 10.04 to 11.10 is going to be possible only in 3 separate update steps, and will take a very long time and will give the system many opportunities to mess things up for you.

If I were you I would just do a clean installation of 11.10;  much quicker and less prone to disaster.

---

### Post by gerryl on 2012-01-29
I wish I had received Coffecat's reply sooner.  I took the advice to delete sda6 - which broke the system again - it would not reboot.  I was able to recover relatively easily, but it took another install, so my partitions are even more confused than before.

Coffeecat suggested I could clean them up using the package manager.  I need some guidance in doing this, hopefully without breaking the system again.

---

### Post by BC59 on 2012-01-29
There are many ways to delete the old kernels.
You can install Synaptic through Ubuntu Software Center and from there, search for kernels and delete the old ones (....just be careful)
Another way -simpler is to install Ubuntu-Tweak and from there clean the computer:
sudo add-apt-repository ppa:tualatrix/next
sudo apt-get update
sudo apt-get install ubuntu-tweak

---

### Post by coffeecat on 2012-01-29
> **gerryl said:**
> Coffeecat suggested I could clean them up using the package manager.  I need some guidance in doing this, hopefully without breaking the system again.

I think you are misunderstanding what I am saying. There seem to be two issues that are troubling you: cleaning up old kernels and tidying up your partition layout. You should use a package manager to delete old kernels, but this is not going to help with tidying up a partition layout.

What exactly is it that you are trying to achieve at the moment? What do you have installed and does it boot OK? I would suggest forgetting about deleting old kernels - at least for now. They don't take up that much room.

---

### Post by gerryl on 2012-01-29
Thank you for your patience with the newbie.

Yes - you are exactly correct - I am addressing two issues.  I am running successfully with 11.10, but I also have, I think, an old broken copy of 11.10, and a copy of 10.04.  I believe these are in separate partions, which seems to detract from my availabe space.  So yes, I do want to get rid of these old kernal copies, and yes, I also want to tidy up my partition layouts.  But, if as you suggest, I should forget about old kernals, I would be happy to just address the partition issue.

---

### Post by coffeecat on 2012-01-29
> **gerryl said:**
> Thank you for your patience with the newbie.

No problem! I remember what it was like. :)

Looking at your earlier Gparted screenshot, you have only two ext4 partitions. sda6 being the root partition of your working installation - presumably 11.10 - and sda8 would, I guess, be a broken system. You have three swap partitions, only one of which - sda7 - is in use. The other two swap partitions you can almost certainly get rid of. The last important thing to consider is that you have 42.47 GiB unallocated space between your root partition and your in-use swap partition. You also have a small 196MB primary ext3 partition labelled "os_part". It's not immediately obvious what that might be. 

It looks as though you have about 165 GiB space in your extended partition once you get rid of all the (probably) unneeded partitions - that is, everything except sda6 and sda7. Not forgetting that 42.47GiB is stuck between those two partitions at the moment.

Have a think about how you would like to use that space, and then let us know. Also, it might be useful to run the boot info script. It may provide useful information that is not obvious at the moment. Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

With the output of the boot info script and with your feedback on how you would like to use the spare space, we should be able to help you achieve what you need.

---

### Post by gerryl on 2012-01-29
OK - attached is the (abridged) boot info results file.

I guess what I would ultimately like is to have all space not specifically allocated to kernal, swap, or other necessary functions, consolidated into one large working space for user files.

---

### Post by coffeecat on 2012-01-29
> **gerryl said:**
> OK - attached is the (abridged) boot info results file.


No, don't post an abridged version. You've left out some important parts, the grub.cfg files for sda6 and sda8 and your /etc/fstab files. Without these we could make some errors in advice, particularly as there is an important complication. As far as I can make out, your working system is 11.10 on sda6, but grub is using the menu from your broken 10.04 on sda8. If you remove sda8, you will make your system unbootable until you reinstall grub. I say "as far as I can make out" because I am having to make some assumptions based on incomplete evidence.

Post the complete RESULTS.txt and post it between [noparse]```
 and 
```[/noparse] tags as I describe before. Posting an uploaded txt file is inconvenient for those trying to help.

I'm logging off soon. I'll check the thread in the morning, but I'm sure you'll get good advice in the meantime.

---

### Post by gerryl on 2012-01-29
OOPS - sorry (thank you again for your patience).

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 8 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Recovery: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda3 and looks at sector 4432097 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #3 
                       for /grub/menu.lst.
    Operating System:  
    Boot files:        /grub/menu.lst

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

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,455     4,321,484     4,209,030   b W95 FAT32
/dev/sda3    *      4,321,485     4,723,109       401,625  83 Linux
/dev/sda4           4,723,171   488,280,063   483,556,893   f W95 Extended (LBA)
/dev/sda5           4,723,173     9,896,039     5,172,867  82 Linux swap / Solaris
/dev/sda6         266,627,072   390,115,243   123,488,172  83 Linux
/dev/sda7         479,182,848   488,280,063     9,097,216  82 Linux swap / Solaris
/dev/sda8           9,897,984   256,098,303   246,200,320  83 Linux
/dev/sda9         256,100,352   266,614,783    10,514,432  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-0703                              vfat       DellUtility
/dev/sda2        4671-EEA0                              vfat       OS
/dev/sda3        484b4ddf-ec54-4455-80b4-c42e22d19c2b   ext3       os_part
/dev/sda5        5d7036f7-d70c-4c72-be63-aee0921581ef   swap       
/dev/sda6        af3305a8-e7c1-4d91-a748-c2ab1ff6fca3   ext4       
/dev/sda7        75b12d19-2d48-4fc5-b564-65d0945acaaa   swap       
/dev/sda8        092669dd-e988-4e6b-8fae-fc99afebd729   ext4       
/dev/sda9        fc3f23aa-5d4e-4f3d-88ee-4853ee49ffcd   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/OS                vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda3        /media/os_part           ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda8        /media/092669dd-e988-4e6b-8fae-fc99afebd729 ext4       (rw,nosuid,nodev,uhelper=udisks)


=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.gz                                      1
            ?? = ??             vmlinuz                                        1

============================= sda3/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=03d43c17-93f0-4381-961d-8d6badcef19b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.10, kernel 3.0.0-12-generic
root		(hd0,2)
kernel		/vmlinuz-3.0.0-12-generic root=UUID=03d43c17-93f0-4381-961d-8d6badcef19b ro quiet splash 
initrd		/initrd.img-3.0.0-12-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-3.0.0-12-generic root=UUID=03d43c17-93f0-4381-961d-8d6badcef19b ro  single
initrd		/initrd.img-3.0.0-12-generic

title		Ubuntu 11.10, kernel 2.6.38-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.38-11-generic root=UUID=03d43c17-93f0-4381-961d-8d6badcef19b ro quiet splash 
initrd		/initrd.img-2.6.38-11-generic
quiet

title		Ubuntu 11.10, kernel 2.6.38-11-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.38-11-generic root=UUID=03d43c17-93f0-4381-961d-8d6badcef19b ro  single
initrd		/initrd.img-2.6.38-11-generic

title		Ubuntu 11.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz

--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.114358425 = 2.270275072    grub/menu.lst                                  2
   2.113492489 = 2.269345280    grub/stage2                                    2
   2.125810146 = 2.282571264    initrd.img-3.0.0-14-generic                   60
   2.149247646 = 2.307737088    initrd.img-3.0.0-15-generic                   56
   2.072435856 = 2.225261056    vmlinuz-3.0.0-12-generic                      20
   2.109537601 = 2.265098752    vmlinuz-3.0.0-14-generic                      20
   2.199748516 = 2.361961984    vmlinuz-3.0.0-15-generic                      19

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root af3305a8-e7c1-4d91-a748-c2ab1ff6fca3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root af3305a8-e7c1-4d91-a748-c2ab1ff6fca3
  set locale_dir=($root)/boot/grub/locale
  set lang=
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
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root af3305a8-e7c1-4d91-a748-c2ab1ff6fca3
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=af3305a8-e7c1-4d91-a748-c2ab1ff6fca3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root af3305a8-e7c1-4d91-a748-c2ab1ff6fca3
	echo	'Loading Linux 3.0.0-15-generic ...'
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=af3305a8-e7c1-4d91-a748-c2ab1ff6fca3 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root af3305a8-e7c1-4d91-a748-c2ab1ff6fca3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root af3305a8-e7c1-4d91-a748-c2ab1ff6fca3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 07d7-0703
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 11.10, kernel 3.0.0-12-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 484b4ddf-ec54-4455-80b4-c42e22d19c2b
	linux /vmlinuz-3.0.0-12-generic root=UUID=03d43c17-93f0-4381-961d-8d6badcef19b ro quiet splash
	initrd /initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 484b4ddf-ec54-4455-80b4-c42e22d19c2b
	linux /vmlinuz-3.0.0-12-generic root=UUID=03d43c17-93f0-4381-961d-8d6badcef19b ro single
	initrd /initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu 11.10, memtest86+ (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 484b4ddf-ec54-4455-80b4-c42e22d19c2b
	linux /memtest86+.bin 
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
# / was on /dev/sda7 during installation
UUID=af3305a8-e7c1-4d91-a748-c2ab1ff6fca3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=75b12d19-2d48-4fc5-b564-65d0945acaaa none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 164.472999573 = 176.601538560  boot/grub/core.img                             1
 165.056640625 = 177.228218368  boot/grub/grub.cfg                             1
 129.180446625 = 138.706448384  boot/initrd.img-3.0.0-15-generic               3
 137.423267365 = 147.557109760  boot/vmlinuz-3.0.0-15-generic                  1
 129.180446625 = 138.706448384  initrd.img                                     3
 137.423267365 = 147.557109760  vmlinuz                                        1

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 092669dd-e988-4e6b-8fae-fc99afebd729
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 092669dd-e988-4e6b-8fae-fc99afebd729
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 092669dd-e988-4e6b-8fae-fc99afebd729
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=092669dd-e988-4e6b-8fae-fc99afebd729 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 092669dd-e988-4e6b-8fae-fc99afebd729
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=092669dd-e988-4e6b-8fae-fc99afebd729 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 092669dd-e988-4e6b-8fae-fc99afebd729
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 092669dd-e988-4e6b-8fae-fc99afebd729
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d7-0703
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set af3305a8-e7c1-4d91-a748-c2ab1ff6fca3
	linux /boot/vmlinuz-3.0.0-15-generic root=UUID=af3305a8-e7c1-4d91-a748-c2ab1ff6fca3 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-15-generic
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set af3305a8-e7c1-4d91-a748-c2ab1ff6fca3
	linux /boot/vmlinuz-3.0.0-15-generic root=UUID=af3305a8-e7c1-4d91-a748-c2ab1ff6fca3 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-15-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=092669dd-e988-4e6b-8fae-fc99afebd729 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=fc3f23aa-5d4e-4f3d-88ee-4853ee49ffcd none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  56.959953308 = 61.160284160   boot/grub/core.img                             1
  51.191253662 = 54.966190080   boot/grub/grub.cfg                             1
  57.039642334 = 61.245849600   boot/initrd.img-2.6.32-21-generic              1
  56.982944489 = 61.184970752   boot/vmlinuz-2.6.32-21-generic                 1
  57.039642334 = 61.245849600   initrd.img                                     1
  56.982944489 = 61.184970752   vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

```

---

### Post by coffeecat on 2012-01-30
OK. I've had a chance to look at the complete RESULTS.txt. I suggest we take this as a 3-stage process: namely, re-install grub to the mbr, remove the unwanted partitions and then create new partitions. Two things to keep in mind. As mentioned yesterday, at the moment grub in the mbr is pointing to Lucid's grub on sda8 and you are using the Lucid grub menu. That is why you need to re-install grub to the mbr before removing the Lucid [noparse](sda8)[/noparse] partition. Also, you have what looks like an unused boot partition on sda3 for a now non-existent installation, probably 11.10, but using legacy grub. At some point you will need to remove or reformat that partition otherwise you will get spurious entries in your grub menu.

To action!

1 - Backup all your important files. You will be manipulating partitions. Something could go wrong.

2 - Did I say backup all your important files?

3 - Re-install grub to the mbr. You need an 11.10 live CD or live USB. Don't use another version. There are minor inconsistencies between the point releases of grub2 used in the last few Ubuntu releases. Boot up the live CD/USB and choose "try Ubuntu" to get to the desktop. First, open Gparted and double-check that the partition layout looks like the screenshot that you posted in post #7. It should do, but it won't do any harm to check. If all is at it should be, close Gparted and open a terminal. Now:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Now reboot, removing the CD/USB. You should now see the grub menu from your 11.10 system. Boot into 11.10. Is everything OK so far? If not, post back.

4 - I suggest you now do something about sda3. It's only about 200MiB so it's not worth trying to recover that space, but the residual legacy grub files are causing spurious entries in your grub2 menu. Open Gparted in 11.10 (I assume you have Gparted already installed) and reformat it with Partition -> Format to. I suggest you reformat it FAT32. You could use it to store things on. Small things! :)

5 - Close Gparted and run this from the terminal:

```
sudo update-grub
```

That will regenerate the grub menu without the unwanted sda3 menu entries.

Try rebooting after this step to make sure everything is OK. If it is, move on to the next step.

6 - Boot up the live CD/USB again and open Gparted. Double-check that your partition layout is still like your earlier screenshot (with the exception of sda3). Now right-click on each of the swap partitions in turn and choose "swapoff". Mark sda5, sda8, and sda9 for deletion. Don't mark sda6 and sda7 for deletion - these are your 11.10 partitions. Double-check that sda6 and sda7 are showing as 58.88GiB and 4.34Gib respectively. Double-check that I have told you to mark the correct partitions for deletion - it's your system and I could make a mistake! If you are confident everything is marked as it should be, click on the green tick apply button and let Gparted do its work.

7 - I suggest you take a screenshot of the Gparted window now that yuou have deleted the unwanted partitions and save it in case there is any problem booting into your permanent installation.

8 - Try rebooting into the hard drive 11.10. Does it work? It's just possible that grub might fail because your sda6 and sda7 partitions will probably now have different numbers. Don't worry if this happens. You can easily reinstall grub. Just post back with details if you get a problem at this stage. If all is well, take a screenshot of a Gparted window (or use the one from the live CD) and post this so that we can see where you are now.

That's it for now. Tell us how you got on and post some thoughts about how you would like to use the spare space. The simplest option is to create two ext4 partitions for data storage - or perhaps you would like to reserve some space for dual-booting another distro.

---

### Post by gerryl on 2012-01-30
WOW - sounds heavy, but I'll give it a try.

First question - live bootable CD.  There seem to be several utilities for doing backups, but I'm not sure which one will give me a bootable version.  I know I can create a bootable CD by downloading from the Ubuntu web site, but this is a very slow process.  Any recommendations for creating a bootable CD from my system?

---

### Post by coffeecat on 2012-01-30
Sorry - coffeecat smites forehead and wonders what he did with his brain today! :( 

:wink:

You can boot into Ubuntu 11.10, of course, from the current 10.04 grub menu. You can reinstall grub from that. No need for a live CD at all. Here goes:

Boot into Ubuntu 11.10, open a terminal and:

```
sudo grub-install /dev/sda
```

Now do this for good measure:

```
sudo update-grub
```

That's it! Now reboot to make sure the 11.10 grub menu is working OK and then go from #4 in my previous post.

**EDIT**: just to add - you will need a live CD for deleting partitions. The 10.04 should be OK for that.

---

### Post by gerryl on 2012-01-30
OK - it looks like we were pretty much successful!!!

One anomoly - I was not able to delete sda5 - the error message was:
 "Please unmount any logical partitions having a number higher than 5."

and I was reluctant to do that without knowing the consequences.

Ultimately, if possible, I think I would like to just combine the unallocated partitions with sda6 to form one big partition for user files.  Does this make sense or do you have another recommendation?  I do not anticipate wanting to have dual-boot capabilities.

So it looks like we were successful in getting rid of some spurious partitions.  But it appears that I still have an old 10.04 version hanging around.  The Grub User Guide Section 7 gives what seems to be simple instructions that even I could follow for removing old kernals.  Your comments on doing this???

Also, I have learned my lesson and would like to create a bootable backup CD.  What utility do you recommend for this or should I just download it from the Ubuntu web site?

---

### Post by coffeecat on 2012-01-30
> **gerryl said:**
> 
One anomoly - I was not able to delete sda5 - the error message was:
 "Please unmount any logical partitions having a number higher than 5."

and I was reluctant to do that without knowing the consequences.

That was because you were using Gparted from your permanent 11.10 installation. You must have missed my edit to my previous post. You have to use Gparted from the live CD if you wish to delete partitions numbered lower than any mounted ones. sda6 was still mounted because it's your root partition. If you use a live CD, it won't be mounted. Do you have a live CD/USB of any version of Ubuntu?

> **gerryl said:**
> Ultimately, if possible, I think I would like to just combine the unallocated partitions with sda6 to form one big partition for user files.  Does this make sense or do you have another recommendation?  I do not anticipate wanting to have dual-boot capabilities.

That's entirely possible but definitely needs Gparted from a live CD. And it will take a long time - perhaps a couple of hours or more - because you have to grow sda6 backwards by over 100GiB.

> **gerryl said:**
> So it looks like we were successful in getting rid of some spurious partitions.  But it appears that I still have an old 10.04 version hanging around.

10.04 is gone! All you have now is 11.10 on sda6, its swap partition on sda7 and the unwanted swap partition on sda5.

> **gerryl said:**
> 
  The Grub User Guide Section 7 gives what seems to be simple instructions that even I could follow for removing old kernals.  Your comments on doing this???

Link? I'll comment when I've seen it.

Let us know what live CD you have if any, and then we can see about getting rid of sda5 and enlarging sda6 to fill all that space.

---

### Post by gerryl on 2012-01-30
I have a live CD of 10.04.

---

### Post by coffeecat on 2012-01-30
That will be fine.

I need to log off in a moment, and I want to make sure I get the instructions for enlarging sda6 correct for you, so I'll do that in the morning. It's not at all difficult - I just want to get the details right. In the meantime make sure you have adequate backups because enlarging a partition is a little more risky than simply deleting unwanted ones. I've done it successfully a few times myself, but the risk is there.

You also might want to delete that sda5 partition with the 10.04 CD Gparted just to get some practice! :) Don't forget to right-click -> "swapoff" both the swap partitions before you do so. You don't want to delete sda7, but you won't be able to delete sda5 until you swapoff both.

I'll check the thread in the morning.

---

### Post by coffeecat on 2012-01-31
Just as a pre-amble, a couple more cautionary comments, and sorry about the uncertainty.

When you come to delete sda5, your sda6 and sda7 partitions will probably be renumbered to sda5 and sda6 respectively. This won't affect the code in grub.cfg and /etc/fstab because both use UUIDs to identify partitions. However, it *might* affect grub in the mbr which now points to sda6. I'm hoping it won't because I believe that UUIDs are used. The worst that could happen is that you would have a boot failure with a grub error and you would have to re-install grub to the mbr, for which you would need a live CD. Which brings us to the next point. The reason I mentioned earlier that you need to use the 11.10 CD, and not the 10.04 CD to re-install grub to the mbr, is that 10.04 uses version 1.97/8 of grub2 and 11.10 uses 1.99. If you used a 10.04 CD you would end up with 1.98 code in the mbr and 1.99 code in /boot/grub, and there *may* be incompatibilities between the two. I have certainly experienced problems using the &#8220;wrong&#8221; version of grub to re-install to the mbr. Again, a worst case scenario is that you would have to obtain a 11.10 CD to repair grub. I appreciate that you said that downloading the 11.10 ISO would be slow for you and, of course, you would need another machine if you got a boot failure.

I know I've mentioned this before, but I'll stress it again. Resizing a partition usually works just fine, but Gparted does have to rebuild the filesystem which takes quite some time. If you were to experience a power failure, for example, during that time, the damage to the filesystem would probably be irreparable. Backup first!

To business. Boot up your Ubuntu live CD and open Gparted. Right-click on both the swap partitions and choose &#8220;swapoff&#8221;. Mark the sda5 swap partition for deletion (if you have not already deleted it) and click on apply. Let that complete. Now highlight your 58.88GiB ext4 partition (which may now be numbered sda5). Now, Partition menu &#8594; Resize/Move. Simply adjust the figures in the three fields, or move the end sliders in the blue box at the top of the Resize window, so that the partition uses all the available space. That's about 125GiB to the left and 42GiB to the right. If there is 1MiB in either space-preceding or space-following that you can't get rid of, don't worry about it. Click on the Resize/Move button, and then click on Apply. And now wait. You'll almost certainly have enough time for a meal.

You asked earlier about backups. If you mean making a clone or image of your system, most people recommend clonezilla. I don't use it myself &#8211; I have other slightly more eccentric ways of backing up my systems which I am used to &#8211; but I see that it is highly regarded.

If anything above is unclear, please do post back, and good luck.

---

### Post by gerryl on 2012-01-31
Thank you again for all your time and effort.

Before I start this step I want to make sure that if something goes wrong, it will not be TOO difficult to recover.  Specifically I want to make sure I understand what you mean by a live CD.  Will I get this live CD if I download 11.10 from the Ubuntu.com web site and write it to disk?  Will clonezilla do that from my system?  Clonezilla is not on the Ubuntu software center.

BTW - the reason I earlier thought I still have a copy of 10.04 is that when I reboot I get a selection screen asking me to select between booting from 3.0.0-15 and 2.6.32-21.  If i try the latter I get an error, and the Package Manager does not show a 2.6.32-21.  Don't know why it shows up on the boot window.  Perhaps after everything is cleaned up it will go away ;-)

---

### Post by coffeecat on 2012-01-31
A live CD is obtained by downloading the ISO from the Ubuntu site and burning that as an image to a CD. Alternatively you can use the ISO to create a bootable USB pendrive. But surely you would have done this before? You have/had several Ubuntu installations.

[Clonezilla]("http://clonezilla.org/"). Clonezilla is a standalone utility which you burn to CD/USB in the same way as with an Ubuntu ISO.

If you are seeing entries for 10.04 in your grub menu and you have deleted your 10.04 partition, then you have not run "sudo update-grub" as I suggested. "update-grub" *should* completely regenerate the grub menu with only those kernels which exist.

---

### Post by gerryl on 2012-02-02
OK - the re-partitioning process worked well and I think I am now done!  Spurious kernels and partitions seem to have been cleaned out (see Gparted image).  The process went smoothly and only took about a half hour.

Thank you for your patience and expertise in guiding me through this process.  It turned into a real learning experience for me.  Of course, the most important thing I learned is "Don't mess with the Operation System - especially if, like me, you don't know what you are doing!!!"

I waited a day to repost just to make sure there were no surprises ready to spring up on me.  I found only two minor anomolies:

1. I had to reinstall fotoxx - my preferred photo processing tool.  The install seemed to go OK, and fotoxx is available from the dash Applications->Graphics->fotoxx.  But if I select a jpg file, fotoxx is not available as an "Open with" option, including "Show Other Applications".  Where/why is it hiding?

2. On selecting Shut Down, I get the purple Ubuntu screen, but all the shutdown messages appear in a tiny font.  Not a big deal because I seldom read them, but just in case there is an important message, I would like to be able to read it (similar problem with startup messages).  I read a little about editing the grub preferences, but am reluctant to mess with it (see second paragraph above:(  ).   Is is a screen size mismatch?  I use a Dell 20" monitor with 1680x1050 resolution.

---

### Post by coffeecat on 2012-02-02
I'm glad the resizing of the partition went well.

Your reference to spurious kernels being cleaned out suggests that you *may* still be confused about the relationship between kernels and partitions. The kernels that were in the partitions that have been deleted have gone - they were the kernels of the operating systems that were in the deleted kernels - but you may still have more than one kernel installed in your remaining in-use system. If you want to tidy them up, then you need to use the package manager as I mentioned before. In which case you would be better starting a new thread with a relevant title if you need help with this. But, tbh, unwanted kernels don't take up that much space. I usualy don't bother about them.

With regard to your other two questions, I have no experience of fotoxx and I have no immediate explanation for why it is not appearing in the list of other applications. I'm slightly surprised that you are seeing text messages on bootup and shutdown - this is not the default behaviour, so perhaps you have changed grub configurations at some point.

You may want to start new threads for these issues too. Good luck!

---

### Post by gerryl on 2012-02-02
Thank you yet again for your help.

By text messages, I mean that the system displays messages that processes are shutting down, network connections are being disconnected, etc.  I have been getting these messages since day 1, so I assumed they were normal.  But in the past they were with a legible font size.  Now the font is tiny.

FWIW - I found that someone else did open a thread about the fotoxx problem about one week ago.  No replies yet.

---

