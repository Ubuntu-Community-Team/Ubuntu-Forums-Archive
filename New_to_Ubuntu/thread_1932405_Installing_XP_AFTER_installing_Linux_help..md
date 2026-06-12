---
title: "Installing XP AFTER installing Linux help."
date: 2012-02-27
forum: New to Ubuntu
---

### Post by hayloiuy on 2012-02-27
Hi guys, i am new here.

As stated above I need help installing XP after installing Ubuntu 11.04.

I have done my homework(at least I think). Apparently Windows is such a self-centered person that it does not recognize the existence of other OS when it is installed. Therefore, some modification in Linux bootloader is required.

Problem is I have no idea whatsoever on how to modify a bootloader. Also when I tried to install XP, it does not recognize the partition I made.

This site offered some help:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2)

but it is based on Ubuntu 9.04. Ubuntu 11.04 does not have /boot/grub/menu.lst but it has /boot/grub/grub.conf and their content are different.

Can someone modify the file such that it will recognize both XP and Linux(I have Backtrack 5 on the hard drive as well)?



TL;DR:
Teach me how to install XP on Ubuntu 11.04.

Thank you in advance.

---

### Post by audiomick on 2012-02-27
I'm not sure about the partition. Did you format it to NTFS? If it is formatted to one of the Linux file system, I expect the XP installer wont see it.

As far as re-installing the Gub boot loader, here are a couple of links.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

Installing XP will definitely overwrite Grub, but it is not that hard to put it back once you have XP re-installed.

---

### Post by hayloiuy on 2012-02-28
Ok so, I installed XP.

I fixed the Grub thing with this tutorial.
[http://community.linuxmint.com/tutorial/view/245](http://community.linuxmint.com/tutorial/view/245)

New problem:
I always boot to ubuntu when I start the machine.
I have Backtrack 5 and Windows XP as well but the GRUB won't list them down and just enter Ubuntu.

I think the original GRUB file which contain pointer to other OS is overwritten when I followed the tutorial.

Help please.:(

---

### Post by oldfred on 2012-02-28
Have your tried.

```
sudo update-grub
```

Or if that does not work run the boot info script from this, which is good to have as it can also repair things:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by hayloiuy on 2012-02-28
I tried the update- grub. It list XP and Ubuntu now but no Bactrack 5. What is wrong?

---

### Post by audiomick on 2012-02-28
I would suggest looking at the link to "boot repair"  in oldfred's signature. There is reference there to the boot info script. The information that this provides would likely be useful at this point.

---

### Post by hayloiuy on 2012-02-28
Ok, I tried the boot-repair thing but it just says "Scanning systems. This may take several minutes." As of writing it has been 20 minutes since the scan.

So in the mean time, I tried the boot info script thing.

This is the result. I dunno which part is significant so I just post all of them. Sorry.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   566,706,175   566,704,128  83 Linux
/dev/sda2    *    566,708,940   772,067,834   205,358,895   7 NTFS / exFAT / HPFS
/dev/sda3         772,079,614   976,771,071   204,691,458   5 Extended
Extended partition linking to another extended partition.
/dev/sda5         772,079,616   960,380,927   188,301,312  83 Linux
/dev/sda6         960,382,976   968,445,951     8,062,976  82 Linux swap / Solaris
/dev/sda4         968,458,240   976,771,071     8,312,832  82 Linux swap / Solaris

/dev/sda3 overlaps with /dev/sda4

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 8e569131-159a-45c8-a3bd-e217f9c4b2b2   swap       
/dev/sda1        32402436-a1de-4e60-a42b-697e05c3147d   ext4       
/dev/sda2        D654323054321429                       ntfs       
/dev/sda6        a92cb711-4513-4450-97d8-8c79ed21ff01   swap       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /mnt/boot-sav/sda2       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 32402436-a1de-4e60-a42b-697e05c3147d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 32402436-a1de-4e60-a42b-697e05c3147d
  set locale_dir=($root)/boot/grub/locale
  set lang=en_SG
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32402436-a1de-4e60-a42b-697e05c3147d
	linux	/boot/vmlinuz-3.0.0-16-generic-pae root=UUID=32402436-a1de-4e60-a42b-697e05c3147d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32402436-a1de-4e60-a42b-697e05c3147d
	echo	'Loading Linux 3.0.0-16-generic-pae ...'
	linux	/boot/vmlinuz-3.0.0-16-generic-pae root=UUID=32402436-a1de-4e60-a42b-697e05c3147d ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32402436-a1de-4e60-a42b-697e05c3147d
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=32402436-a1de-4e60-a42b-697e05c3147d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32402436-a1de-4e60-a42b-697e05c3147d
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=32402436-a1de-4e60-a42b-697e05c3147d ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32402436-a1de-4e60-a42b-697e05c3147d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32402436-a1de-4e60-a42b-697e05c3147d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root D654323054321429
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=32402436-a1de-4e60-a42b-697e05c3147d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=24c6a022-dcc4-4d07-8937-15af2a4ac9dd none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   3.112365723 = 3.341877248    boot/grub/core.img                             1
   2.920906067 = 3.136299008    boot/grub/grub.cfg                             2
   1.797851562 = 1.930428416    boot/initrd.img-3.0.0-12-generic               3
   4.586914062 = 4.925161472    boot/initrd.img-3.0.0-16-generic-pae           4
   2.377151489 = 2.552446976    boot/vmlinuz-3.0.0-12-generic                  1
   1.028877258 = 1.104748544    boot/vmlinuz-3.0.0-16-generic-pae              1
   1.797851562 = 1.930428416    initrd.img                                     3
   1.797851562 = 1.930428416    initrd.img.old                                 3
   2.377151489 = 2.552446976    vmlinuz                                        1

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
mdadm: No arrays found in config file or automatically

```

Thanks.

---

### Post by fractalman on 2012-02-28
If you can sacrifice enough ram you could always put xp on a virtual box inside natty

---

### Post by hayloiuy on 2012-02-28
By the way can someone explain why there is more than threeOSes when I see the see the Grub list?

There should only be Ubuntu, XP and Backtrack. Why the nonsense like swap, and other Linuxes recovery mode that I don't remember installing be in the list?

Also, why are there so many partitions(sda4,5,6....) when I only created partitions for THREE OSes?

Thank you and sorry for being ignorant.

---

### Post by audiomick on 2012-02-28
Ok. I would suggest waiting for more informed advice. I'm not very experienced with this. Maybe oldfred will come back.

However, I don't like the looks of a couple of things. In the first section, sda5 and sda4 come up as "unknown file type", although they are respectively labelled as "Linux" (file system) and "swap" further down.

In the second section, headed Drive/ partition info, there is this
```
Extended partition linking to another extended partition.  /dev/sda3 overlaps with /dev/sda4 
``` I don't recalll having seen "extended linked with another extended" before, but it strikes me as odd.

I have seen "sdaY overlaps sdaX" before, and I think that is always a problem.

I'm guessing at this point that the grub update didn't find Backtrack 5 because something has been corrupted on the drive.

When you boot into Ubuntu, can you see and mount the partition (in Nautilus) that Backtrack is on? If things are in order, I believe you should be able to.

---

### Post by audiomick on 2012-02-28
> **hayloiuy said:**
> By the way can someone explain why there is more than threeOSes when I see the see the Grub list?
Actually, there are only two: windows and Ubuntu. What looks like more Ubuntu installs is just old kernels. 

> 
Why the nonsense like swap, and other Linuxes recovery mode that I don't remember installing be in the list?

There are no Linux "recovery" installs in that sense. Is I mentioned above, there are older kernels there. That is useful sometime when a kernel upgrade breaks you system. You can often boot into the older kernel and have the system still work.

As swap partition is always created automatically when you install Linux. You seem to have to, one of which isn't quite healthy. You can, at least with the Ubuntu installer, tell it to use only an existing swap partition without creating a new one. I would say you have two there because there are two Linux installs on there, or at least there are supposed to be.

> Also, why are there so many partitions(sda4,5,6....) when I only created partitions for THREE OSes?

Your partitions:

/dev/sda1               2,048   566,706,175   566,704,128  83 Linux /dev/sda2    *    566,708,940   772,067,834   205,358,895   7 NTFS / exFAT / HPFS /dev/sda3         772,079,614   976,771,071   204,691,458   5 Extended Extended partition linking to another extended partition. /dev/sda5         772,079,616   960,380,927   188,301,312  83 Linux /dev/sda6         960,382,976   968,445,951     8,062,976  82 Linux swap / Solaris /dev/sda4         968,458,240   976,771,071     8,312,832  82 Linux swap / Solaris  /dev/sda3 overlaps with /dev/sda4Sda 1 is Ubuntu
Sda 2 is XP

Sda3 is an extended partition. It doesn't count as a partition in it's own right. It is kind of like a container for logical partitions.

Sda5 is probably where Backtrack got  installed to, I think.
Sda 6 is a swap, maybe the one that got put in for Backtrack

Sda 4 is a swap, possibly the one that the Ubuntu installer made.

This all makes sense. There is nothing there that can't be accounted for. The only thing is, I fear that it is a bit messed up.

As I said, I don't feel qualified to help you try and fix it. You are better off waiting for someone with more of an idea about it than me.

---

### Post by oldfred on 2012-02-28
You do have two swaps, but that by itself is not a problem. But the issue is that sda4 has to be a primary partition as all partitions from sda1 thru sda4 are primary. But primary sda4 is inside the extended partition which can only have logical partitions inside it.  That then makes for issues reading partitions table.

If you do not need sda4 I would try to delete it. If gparted will not let you delete it, then try fixparts.

Backup partition table first, just in case.

First backup partiton table, use your drive for sda, sdb etc.
sudo sfdisk -d /dev/sda > parts_sda.txt

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I am hopeful that is all the issues. But if the other partitions still show issues then we may have to try e2fsck on those partitions.

---

### Post by hayloiuy on 2012-02-29
> **oldfred said:**
> You do have two swaps, but that by itself is not a problem. But the issue is that sda4 has to be a primary partition as all partitions from sda1 thru sda4 are primary. But primary sda4 is inside the extended partition which can only have logical partitions inside it.  That then makes for issues reading partitions table.

If you do not need sda4 I would try to delete it. If gparted will not let you delete it, then try fixparts.

Backup partition table first, just in case.

First backup partiton table, use your drive for sda, sdb etc.
sudo sfdisk -d /dev/sda > parts_sda.txt

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I am hopeful that is all the issues. But if the other partitions still show issues then we may have to try e2fsck on those partitions.

Do people in "Absolute Beginner Talk " speaks this way? Because I have no idea what you are talking about. I will try to read the links though.

---

### Post by ixtok on 2012-02-29
The advise to install ubuntu after windows is well documented, now can see why.

I hate work arounds and if it were me, I would run a live cd and back up all my files, I would run gparted and wipe the hard drive, with formating with ntfs.

I would install windows using the whole hard drive, I would see if windows works.

I would install ubuntu using the install beside option.

Granted it takes a while to install two operating systems, but you can read a book or watch tv while it is going on. You have probably wasted more time than reinstalling would have taken and you wouldn't have a headache. You will have two new clean systems

---

### Post by hayloiuy on 2012-02-29
I tried the boot-repair. It gives the same result as update-grub.

Boot-repair gave me this link that contain the grub info.

[http://paste.ubuntu.com/861571/](http://paste.ubuntu.com/861571/)

Also Gparted shows my whole disk is unallocated. All 500GB of it.
Attempts to create a new partition table will erase ALL data. 
FixParts does not help much as it expects you to know what you are doing which I don't.

What is going on here? I just want Backtrack 5 to be listed in the Grub.:cry:

---

### Post by hayloiuy on 2012-02-29
> **ixtok said:**
> The advise to install ubuntu after windows is well documented, now can see why.

I hate work arounds and if it were me, I would run a live cd and back up all my files, I would run gparted and wipe the hard drive, with formating with ntfs.

I would install windows using the whole hard drive, I would see if windows works.

I would install ubuntu using the install beside option.

Granted it takes a while to install two operating systems, but you can read a book or watch tv while it is going on. You have probably wasted more time than reinstalling would have taken and you wouldn't have a headache. You will have two new clean systems

That is one of the solution, but to me it sounds like running away from the problem. It makes you less understand how linux works. Isn't the point of linux is to teach GUI users how computers REALLY work?

---

### Post by hayloiuy on 2012-02-29
By the way, in FixParts what does the option 'w' do.

```

MBR command (? for help): w

Final checks complete. About to write MBR data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

```

Is this dangerous?

---

### Post by Mark Phelps on 2012-02-29
> **hayloiuy said:**
> By the way, in FixParts what does the option 'w' do.Is this dangerous?

Don't use Fixparts -- see the tutorial I linked below for you for more info:

[http://www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixparts/")

As to your question about Linux, I would say no -- the purpose of Linux is to provide a free alternative to MS Windows and Mac OSX. If you want to dig down inside of it to see how it works, that's entirely up to you.  Unlike with these other OSs, source code is actually available for your perusal.

---

### Post by hayloiuy on 2012-02-29
> **Mark Phelps said:**
> Don't use Fixparts -- see the tutorial I linked below for you for more info:

[http://www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixparts/")

As to your question about Linux, I would say no -- the purpose of Linux is to provide a free alternative to MS Windows and Mac OSX. If you want to dig down inside of it to see how it works, that's entirely up to you.  Unlike with these other OSs, source code is actually available for your perusal.

No.... There is nothing in about 'w' option in there....

Any other tool to fix partition table?

Thanks.

---

### Post by oldfred on 2012-02-29
If the partition table is ok, after the changes Fixparts suggests, then you have to do the w to write the corrections. Only do that if you have made the backup of your current partition table with sfdisk as posted and saved to another device. Did you go thru the tutorial on the fixparts site?

All the other ways to fix the type of errors in a partition table are not for new users. Lots of command line.

---

### Post by hayloiuy on 2012-03-02
> **oldfred said:**
> If the partition table is ok, after the changes Fixparts suggests, then you have to do the w to write the corrections. Only do that if you have made the backup of your current partition table with sfdisk as posted and saved to another device. Did you go thru the tutorial on the fixparts site?

All the other ways to fix the type of errors in a partition table are not for new users. Lots of command line.

Show me the way , Master.....

---

### Post by oldfred on 2012-03-02
Have you run fixparts following the instructions on the fixparts site? That should fix partition table.

If not post this which you ran as the backup of your partition table before:

sudo sfdisk -d /dev/sda

---

