---
title: "Errors reinstalling 14.04, dual boot with XP"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by andrea b on 2014-05-01
An XP refugee and noob, I've just installed Trusty on 3 older Thinkpads (sole OS on an T60, and dual boot on two X60s). I did my research best I could, and have really enjoyed the process.  Solving all the little problems that have come up - learning a lot. My data is well backed up, so I have the luxury of making mistakes ... and I'm  makin' em.  

One of the X60s showed serious boot problems (excruciatingly long boot time) and persistent slowness / freezes.  If I were more knowledgeable, I'd probably have known how to do diagnostics, etc... but I didn't have the time or patience to learn this right now.  So I reinstalled Trusty from the disc, making no changes in partitions. 

I imagined that the NTFS partition would remain unchanged,  that a reinstall "into" the original ubuntu partition would preserve my documents and most of my installed software, while reverting all settings to default. 

What I found (and this may not be news to non-noobs) was that the initial install was not overwritten; rather, all extant files were given a separate 28 GB partition.  And *another* partition was created for the new install.  So I now have two 'Computer' directories (bin, boot...var).  This was not clear to me in the diagram presenting the partitions via the install disc.

(a) is there any disadvantage to using GParted to delete the partitions containing the original install? There is nothing there that I need, and I'd prefer to have a 55 contiguous GB for Trusty.  Clearly, I'd have to read up on partitions...  (b) is the version of GParted available from the Software Center sufficient? (I have downloaded the ISO, but don't have a cd burner at the moment). 

Thanks!

---

### Post by oldfred on 2014-05-02
You usually cannot use a gparted on your working system as you have partitions mounted. I do install it but only work on another drive.
You need to use a Live installer. It was on what ever installer you used if Ubuntu, not sure about all flavors.

But if you still have your live installer that will work.
You also may have to click on swap and right click swap off. Installer in live mode likes to mount swap if found to speed things up a bit. And swap is often in the extended partition which in effect mounts the entire extended partition.

I generally do not like moving partitions left. It is slow as all data must be copied. And any interruption will totally corrupt data.

Be glad you do not have a new UEFI system. Reinstall on those just shows Ubuntu and users think they are overwriting just Ubuntu when the entire drive is overwritten. Not sure if Ubuntu installer, or user, but may be related to Windows 8 always in hibernation mode, so installer does not see it correctly.

Make sure you delete correct partition. Both installs probably used same swap.

Grub probably also includes old install. Second install should be the one in grub, so you do not have to update grub in MBR first. But it does not hurt to boot into install you want to keep and run this:
       
From inside your working install to have its grub boot loader in MBR of sda.
sudo grub-install /dev/sda

After deleting older install. Boot back into working install and run this to remove old installs grub entry.
sudo update-grub

---

### Post by andrea b on 2014-05-02
Thanks so much, oldfred!  

Does it make sense to delete all entries in old install (usr....var) before proceeding?  I'd do it via GUI.

I'm not sure that the live cd gave the option of deleting a partition ... but I'll have a look.  I had installed GParted via Software Center, and ... GParted made it look suspiciously easy to do...

(Fortunately, as I said ... I can afford to mess up.  Everything is backed up.) 

I'm going to read up on partitions ...but does deleting the Install #1 'partition wall' adjacent to new install automatically create the larger partition I'd wanted? Or are there no 'walls?'  I guess I'm saying: how do I conceptualize a 'partition'?  (I shouldn't be asking you to do my homework...)  

Yeah, I'm kind of clueless. Thanks so much for your help.

---

### Post by oldfred on 2014-05-02
I think the only auto partitioning change is the older auto install side by side. But any auto change has always scared me, so I use gparted in advance for all my installs and then use Something Else to choose partition mount and format. And I have managed to screw that up, by making several partitions, small for root and large for data and then forgetting which is which and installing to the large partition. :)
Deleting a partition does not auto adjust other partitions. You have to manually move them around. And if one is primary and the other logical you may also have to resize the extended partition first. It become the old slide puzzle game. With gparted also do not queue events, but process each change, so you know that it completes before starting anther.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by andrea b on 2014-05-02
So far in the Linuxsphere, I've never made a mistake so big I couldn't recover from it ... but I think I've now blown it. 

Using the Mini-Tool (Partition Wizard) on the installer cd, I went ahead and deleted what I ... am certain was the correct partition (before seeing oldfred's reply ... though I'm such an idiot, I don't think it would have helped me).  But - clearly, I didn't do enough homework, and Grub Rescue is my reward.  Can't boot.  Now the 28GB apportioned to the original install is 'unallocated' (and, according to the ubuntu installer, 'unusable')  

The only good thing is that - my data's all backed up. 

I began to resize the partition on the 23GB allocated to the second install - I'd want to merge it with the 28GB of unallocated space - but I know I don't know what I'm doing.  How to rescue myself?

Thanks for your patience...!

---

### Post by andrea b on 2014-05-02
small update - repaired MBR so I could boot into XP, made a series of other mistakes using the Partition Wizard Mini-Tool (I wish my install CD had come with GParted ...not that great software can stop me from making a mess) again unable to boot into either XP or Ubuntu.  Back to the installer disc.  

Extended NTFS partition to cover the unallocated space...booted with installer disc, and installed Boot Repair to boot back into Trusty. 

Whew!  I hate learning the hard way, but it seems to be the only way I learn.  

Now I'm unable to boot into XP (and also would want to shrink the XP partition with GParted, once I have it). 

My question now: how to boot into XP without messing up boot into Ubuntu?

---

### Post by oldfred on 2014-05-02
Any resize of a Windows NTFS partition required a chkdsk before it will boot again. You only can run chkdsk from a Windows repair CD or the XP installer.
Best to use Windows tools on Windows but only Linux tools with Linux.

Gparted is on the Ubuntu installer. Not sure about other flavors you easy to install if booted in live mode as it is in repository. Also you can download a gparted liveCD or Parted Magic liveCD.

Post link from Boot-Repair's BootInfo report. 
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by andrea b on 2014-05-03
Thanks so much, oldfred.   The current status is: (not knowing I had to use chkdsk) I used Gparted to resize XP and Ubuntu partitions to where I want them; I can now boot into Ubuntu fine, but still can't boot into XP (no surprise).  I did run bootinfo, and have a RESULTS.txt - is it ok to post this super-long thing?  (I'm in the process of burning Boot-Repair iso to disc and running this.)

Thanks for your ... patience.  (!)

---

### Post by mastablasta on 2014-05-03
> **andrea b said:**
>   I did run bootinfo, and have a RESULTS.txt - is it ok to post this super-long thing?  (I'm in the process of burning Boot-Repair iso to disc and running this.)


yes it is allowed just wrap it in code tags (the # icon)


by the way - you are needlesly complicating a very simple install.

---

### Post by andrea b on 2014-05-03
I only overcomplicate things the first time.  And - I really appreciate your help.  Here is the RESULTS.txt.  

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /NTLDR /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               6,144   112,859,135   112,852,992   7 NTFS / exFAT / HPFS
/dev/sda2    *    112,859,136   220,780,543   107,921,408  83 Linux
/dev/sda3         220,782,529   224,954,367     4,171,839   f W95 Extended (LBA)
/dev/sda5         220,782,592   224,954,367     4,171,776  82 Linux swap / Solaris
/dev/sda4         224,955,360   234,435,599     9,480,240   2 XENIX root


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01CF66B029E22F00                       ntfs       Preload
/dev/sda2        840d7d90-0601-49a8-b8ae-d120c83544e9   ext4       
/dev/sda4        70EF-93F2                              vfat       SERVICEV001
/dev/sda5        d04845a7-2b56-4a7f-bf85-21b2a10a5620   swap       
/dev/sr0                                                iso9660    CDROM

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/andrea/CDROM      iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
else
  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-840d7d90-0601-49a8-b8ae-d120c83544e9' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
	else
	  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
	fi
	linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=840d7d90-0601-49a8-b8ae-d120c83544e9 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-840d7d90-0601-49a8-b8ae-d120c83544e9' {
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-840d7d90-0601-49a8-b8ae-d120c83544e9' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
		else
		  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
		fi
		echo	'Loading Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=840d7d90-0601-49a8-b8ae-d120c83544e9 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-840d7d90-0601-49a8-b8ae-d120c83544e9' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
		else
		  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
		fi
		echo	'Loading Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=840d7d90-0601-49a8-b8ae-d120c83544e9 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
	else
	  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
	else
	  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-01CF66B029E22F00' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  01CF66B029E22F00
	else
	  search --no-floppy --fs-uuid --set=root 01CF66B029E22F00
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Windows NT/2000/XP (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-70EF-93F2' {
	insmod part_msdos
	insmod fat
	set root='hd0,msdos4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  70EF-93F2
	else
	  search --no-floppy --fs-uuid --set=root 70EF-93F2
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
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
# / was on /dev/sda7 during installation
UUID=840d7d90-0601-49a8-b8ae-d120c83544e9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d04845a7-2b56-4a7f-bf85-21b2a10a5620 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================================ sda4/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=C:\
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\ = "PC-DOS"
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-OdkCPVzW/Tmp_Log: No such file or directory

```

Thanks so much.

---

### Post by Bashing-om on 2014-05-03
andrea b; Hi !

You are coming along nicely, As your 1st responders are presently off-line, permit me to jump into this and offer my guidance.

ubunt's grub has picked up both the Windows install as well as what ever 'xenix' is that is installed to the partition (a slice on the hard disk platter) sda4.
Nomenclature:
sd = (s)serial (d)evice;
sda = the 1st (a) device recognized by the operating system
sdb = 2nd device recognized 
sdc = 3rd device
Now partitons (slices):
sda1= 1st partition on that 1st hard drive ( or other device recognized as 1st)
sda5 = 5th partition on that 1st hard drive
sdc2 = 2nd partition on 3rd hard drive

1) I need to know what is 'xenix' ; is that a viable operating system also installed to this hard disk on sda4 ?
2) The only fault I see with your boot-repair output is the version of grub that is installed onto you system. And It "might" just be find good and dandy, maybe not.
> 
Grub2 (v1.99) is installed in the MBR of /dev/sda

Where as my 13.10 version - and 14.04 I expect is an even later version - :
```

sysop@1310mini:~$ grub-install --version
grub-install (GRUB) 2.00-19ubuntu2.1
sysop@1310mini:~$

```
Let's look at what version of grub is actually installed.
Post back your output of terminal command:
```

grub-install --version

```

With the above discrepancy in mind,What version is your liveDVD(USB) that you are using to (RE-)install grub ? It needs to be the same same version as of that of the installed system.
3. When you now boot your computer, do you now get to the grub boot menu, and do you see in that boot selection menu , ubuntu, Windows and XENIX; What results when you select 'ubuntu' ?
Formerly noted:
> 
I can now boot into Ubuntu fine, but still can't boot into XP 



----------------
Off topic: I am impressed with your desire to learn. As you are aware there is a steep learning curve adjusting to any new operating system. It does take time and patience - we are here to help ! -. Up front, learning this operating system - where there are no secrets - will take a life time - and will still not know it all. We do get to a place where we are comfortable with it, and can explore the horizon of our skills and knowledge. 
---------------

-> Let's get you
[INDENT][INDENT][INDENT]booting ubuntu
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-05-03
I think the Xenix entry in partition table is a typo. 

The top probe of partition says vfat and os-prober thinks it is an XP or Windows 2000 install on a fat32 type partition.

Was your working copy of Windows in sda1 or sda4?

You may be able to just change partition table type to fat32 with Disks or Disk utility. You want to change type, but not format it. Type should be then FAT32 or 0x0b or whatever it shows.

Boot-Repair and Linux can only make minor repairs to Windows. Your boot.ini in sda1 looks correct. It shows the correct XP boot files. It shows no issues with PBR or partition boot sector, so it may just need chkdsk from your XP installer. Or sometimes doing the full refresh of the Windows repairs works even when things seem ok.

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
       FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

    
Cannot post fixing XP without also posting this warning:
 **Windows XP EOL will be April, 2014**.
[http://www.microsoft.com/en-us/windows/endofsupport.aspx](http://www.microsoft.com/en-us/windows/endofsupport.aspx)
Better to move to Linux. 
[https://wiki.ubuntu.com/StartUbuntu](https://wiki.ubuntu.com/StartUbuntu)
Older XP probably need Lubuntu, newer systems may run Xubuntu, or Ubuntu with gnome=-panel, but probably not Unity gui.

---

### Post by andrea b on 2014-05-03
Solved - and apologies for overcomplicating.   (As noted - I only do that when I know nothing!)

sudo update-grub  
resolved the issue, and my partitions are now resized. 

Thanks so much for all your help.

---

### Post by andrea b on 2014-05-03
Beginning Off-topic: Bashing-om - thanks so much for your encouragement...!  as oldfred noted correctly...I have a tendency to overcomplicate things (but only the first time!)  
-----------------------
Xenix is likely the ThinkPad's Rescue and Recovery preload.  Does no apparent harm - though I'm afraid that if I were to need / use it, it might mess with ubuntu install. 

Updating grub per oldfred's original reply to me (sudo update-grub) resolved the current boot issue.  

Many thanks for your help!

---

### Post by andrea b on 2014-05-03
Wait - I spoke too soon about resolving the issue!...don't close this thread quite yet!  Still can't boot into XP.

1) The output of
grub-install --version:

grub-install (GRUB) 2.02~beta2-9

2) On boot: when I select 'Ubuntu', I'm able to boot into Ubuntu with no problem.

The GRUB menu - if this is what you meant: 
Ubuntu
Advanced Options for Ubuntu
Memory test  (memtest86+)
Memory test (another type, couldn't catch it)
Microsoft XP Professional (on /dev/sda1)
Windows NT/2000/XP (on /dev/sda4)


3) I'm having trouble finding my XP disc to run chkdsk (and I'm assuming that running chkdsk won't mess with my Ubuntu install....)  Once I find it, I imagine chkdsk will check only the Windows partition?

I do have PC Doctor on disc, which has solved XP issues in the past.  Again - concerned that it respect the partition.

(as noted, working copy of Windows was sda1.  sda4 is ThinkVantage Rescue and Recovery.) 

4) Changing the partition type ... makes me a bit nervous.  But worth a try.

Thanks!

---

### Post by Bashing-om on 2014-05-03
andrea b; Hey,

Run Window's check disk, as we know now this is not so "Windows NT/2000/XP (on /dev/sda4)", get Windows booting, and if need be we can always (re-)install ubuntu's grub from the liveDVD.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by andrea b on 2014-05-03
How to run Window's check disk, then? I managed to find an old XP cd (SP2) ... ThinkPads don't come with reinstall disks (they have that Rescue and Recovery partition instead, but I can't seem to run diagnostics from it). I do have PC Doctor (DOS version) on a bootable disk. 

Just afraid it won't respect Ubuntu's partition.

---

### Post by andrea b on 2014-05-03
Update: Recovery Console could not find a hard drive installed on computer (!)

I imagine this provides a clue to what's going on...?

---

### Post by oldfred on 2014-05-03
Sorry, should have noticed before.
You have boot flag on sda2, grub2 does not use boot flag, but boot flag is essential for Windows.
The partition with the boot flag is the partition Windows knows to boot from if its boot loader is in the MBR, the partition it knows to repair  (or run chkdsk on) and if installing the partition to install boot files into.

So use gparted and move boot flag from sda2 to sda1. Only one boot flag per hard drive.

Then Windows repair tools will see the sda1 NTFS partitions.

---

### Post by andrea b on 2014-05-04
Ok ... ticked the boot flag for sda1 in Gparted.  Rebooted.  Recovery console still does not recognize a hard drive installed...so I was unable to run chkdsk on Windows partition.  I'm able to reboot into Ubuntu only.  

Any suggestions?

---

### Post by oldfred on 2014-05-04
Rerun BootInfo report and post new link, just to confirm that NTFS still looks ok.
It had all the correct info based on what we can see from Linux before.

---

### Post by andrea b on 2014-05-05
Here are the results of Bootinfo:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /NTLDR /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          6,144   112,859,135   112,852,992   7 NTFS / exFAT / HPFS
/dev/sda2         112,859,136   220,780,543   107,921,408  83 Linux
/dev/sda3         220,782,529   224,954,367     4,171,839   f W95 Extended (LBA)
/dev/sda5         220,782,592   224,954,367     4,171,776  82 Linux swap / Solaris
/dev/sda4         224,955,360   234,435,599     9,480,240   2 XENIX root


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01CF66B029E22F00                       ntfs       Preload
/dev/sda2        840d7d90-0601-49a8-b8ae-d120c83544e9   ext4       
/dev/sda4        70EF-93F2                              vfat       SERVICEV001
/dev/sda5        d04845a7-2b56-4a7f-bf85-21b2a10a5620   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
else
  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-840d7d90-0601-49a8-b8ae-d120c83544e9' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
	else
	  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
	fi
	linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=840d7d90-0601-49a8-b8ae-d120c83544e9 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-840d7d90-0601-49a8-b8ae-d120c83544e9' {
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-840d7d90-0601-49a8-b8ae-d120c83544e9' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
		else
		  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
		fi
		echo	'Loading Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=840d7d90-0601-49a8-b8ae-d120c83544e9 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-840d7d90-0601-49a8-b8ae-d120c83544e9' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
		else
		  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
		fi
		echo	'Loading Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=840d7d90-0601-49a8-b8ae-d120c83544e9 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
	else
	  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  840d7d90-0601-49a8-b8ae-d120c83544e9
	else
	  search --no-floppy --fs-uuid --set=root 840d7d90-0601-49a8-b8ae-d120c83544e9
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-01CF66B029E22F00' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  01CF66B029E22F00
	else
	  search --no-floppy --fs-uuid --set=root 01CF66B029E22F00
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Windows NT/2000/XP (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-70EF-93F2' {
	insmod part_msdos
	insmod fat
	set root='hd0,msdos4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  70EF-93F2
	else
	  search --no-floppy --fs-uuid --set=root 70EF-93F2
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
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
# / was on /dev/sda7 during installation
UUID=840d7d90-0601-49a8-b8ae-d120c83544e9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d04845a7-2b56-4a7f-bf85-21b2a10a5620 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================================ sda4/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=C:\
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\ = "PC-DOS"
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-WOvgqTnX/Tmp_Log: No such file or directory

```

Thanks in advance for all your attentiveness to this ... I really did spill the beans on this one.

---

### Post by oldfred on 2014-05-05
Your XP looks ok. And os-prober finds it and adds a menu entry so it also thought it was ok.

Sometimes you just have to go thru the full repairs again as it is not obvious what the issue is Windows.

       To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

   Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

   FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

   If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

### Post by andrea b on 2014-05-05
> **oldfred said:**
> 
   If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.

or:

Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

The hard drive is still not recognized as installed by the XP disc, so I'm left with options 2 and 3.  

Yes, I can boot into Ubuntu without problem.  I can mount the Windows partition without problem.

I'm going to pass Option 2 (copy from CD - in part because this is XP SP1 - don't know whether SP1 vs SP3 is relevant here) and go to Option 3.

Finding and copying ntdetect.com and ntldr is no problem ... how to copy them to 'root of C:\ ?  Do I just ... drag 'em into the root/ folder? Or do so from the command line as root? 

I don't know the architecture / hierarchy.

Once I know this, I'll deploy.

Thanks!

---

### Post by oldfred on 2014-05-05
I do think it needs to be the correct version. But I do not know how to tell.

It is at the top level.

I labeled my old XP WinXP. I have not used it for a couple of years, but it was up to date then.

```
 fred@fred-Precise:/media/WinXP$ ls -l
total 2096669
drwx------ 1 fred fred       4096 May  7  2011 Apps
-rw------- 1 fred fred        211 Jul 12  2011 boot.ini
drwx------ 1 fred fred       4096 Dec 18  2006 Documents and Settings
drwx------ 1 fred fred      77824 Aug 23  2011 Download
drwx------ 1 fred fred       4096 May 28  2007 ERDNT
drwx------ 1 fred fred       4096 Oct  9  2009 Hardware
-rw------- 1 fred fred      70294 Dec 19  2006 INF.log
-rw------- 1 fred fred      59235 Aug 10  2009 logfile
-rw------- 1 fred fred        950 Nov  9  2007 net_save.dna
-rw------- 1 fred fred      47564 Dec 23  2006 NTDETECT.COM
-rw------- 1 fred fred     250048 Jul 28  2008 ntldr
drwx------ 1 fred fred      16384 Jun 20  2012 Program Files
drwx------ 1 fred fred     233472 Nov 22  2011 WINDOWS


```
Edited out a bunch of 0 size files & folders and a few that I had added.

---

### Post by andrea b on 2014-05-06
> **oldfred said:**
> I do think it needs to be the correct version. But I do not know how to tell.

It is at the top level.

I labeled my old XP WinXP. I have not used it for a couple of years, but it was up to date then.

```
 fred@fred-Precise:/media/WinXP$ ls -l
total 2096669
drwx------ 1 fred fred       4096 May  7  2011 Apps
-rw------- 1 fred fred        211 Jul 12  2011 boot.ini
drwx------ 1 fred fred       4096 Dec 18  2006 Documents and Settings
drwx------ 1 fred fred      77824 Aug 23  2011 Download
drwx------ 1 fred fred       4096 May 28  2007 ERDNT
drwx------ 1 fred fred       4096 Oct  9  2009 Hardware
-rw------- 1 fred fred      70294 Dec 19  2006 INF.log
-rw------- 1 fred fred      59235 Aug 10  2009 logfile
-rw------- 1 fred fred        950 Nov  9  2007 net_save.dna
-rw------- 1 fred fred      47564 Dec 23  2006 NTDETECT.COM
-rw------- 1 fred fred     250048 Jul 28  2008 ntldr
drwx------ 1 fred fred      16384 Jun 20  2012 Program Files
drwx------ 1 fred fred     233472 Nov 22  2011 WINDOWS


```
Edited out a bunch of 0 size files & folders and a few that I had added.

oldfred - I don't understand this reply ... was this meant for me?  

What I was hoping for was clarification on how to execute the maneuver you recommended - copying ntdetect.com and ntldr to root of C:\ . Which I figure is the root/ folder. 

Do I need to use the command line?  Do I drag and drop the copies? 

Thanks!

---

### Post by oldfred on 2014-05-06
I thought you did not know where.

You can just copy & paste, or use command line.
Since NTFS there should not be permission or ownership issues.

I think this is the actual command line from Windows where the cddrive is f: or g: or whatever it is seen as. 
Long time since using Windows. :)

COPY [CDDRIVE]:\I386\NTLDR  C:\

---

### Post by andrea b on 2014-05-06
> **oldfred said:**
> I thought you did not know where.

You can just copy & paste, or use command line.
Since NTFS there should not be permission or ownership issues.

I think this is the actual command line from Windows where the cddrive is f: or g: or whatever it is seen as. 
Long time since using Windows. :)

COPY [CDDRIVE]:\I386\NTLDR  C:\

I may be a little dense, but - I just want to make sure I understand.  

I'm not using my optical drive,  I'm using the Windows system folders in the mounted Windows partion.  I have the ntdetect and ntldr files copied to my desktop, waiting - can I / am I supposed to drag and drop them to the root/ folder (on the Ubuntu side)?  

Or, if using th e command line, how would I do it? 

(The command COPY [CDDRIVE]:\I386\NTLDR  C:\  is a WINDOWS command, or am I incorrect in this ... ?) 

ONCE the files are in place, then I would be able run chkdsk from the XP disc, which hopefully will recognize the partition? 

Thanks!

---

### Post by oldfred on 2014-05-06
That command is a Windows command from its repair console when booted from CD.

You copy or drag to the top of the NTFS XP partition overwriting the current copies that are there. It looks like current copies are ok, but sometimes replacing then fixes something. 

Still better to use Windows to fix Windows issues.

---

### Post by andrea b on 2014-05-06
> **oldfred said:**
> That command is a Windows command from its repair console when booted from CD.

You copy or drag to the top of the NTFS XP partition overwriting the current copies that are there. It looks like current copies are ok, but sometimes replacing then fixes something. 

Still better to use Windows to fix Windows issues.

Ok - I just want to make sure I understand.  

I'm to locate ntdetect and ntldr on the XP SP1 disc (not booting from it - searching it for the files) and replacing the ones in the Windows partition (Service Pack files ... i386).  Correct? 

'The top of the NTFS XP partition'  I take it means the folders in which the current (SP3) ntdetect and ntldr files reside ... correct? 

I'll try that once I'm home...just in case SP1 / SP3 makes a difference, I'll retain copies of the originals on my desktop.

---

### Post by oldfred on 2014-05-06
It may make a difference. 

Are dates different. And how do dates compare to mine posted above?

---

### Post by andrea b on 2014-05-06
Ok - I am worried about replacing my XP partition's SP3 ntldr and ntdetect with old SP1 versions ... I need to have some sense that this is ok.

Anyone out there know? 

Again - ThinkPads come without reinstall or recovery discs, they come with a recovery partition (Rescue and Recovery) that isn't behaving properly (is not allowing me to copy ntdetect and ntldr to external media - doesn't give me a proper drop down list.)  So what I'm using is an old Dell XP recovery disk (2002).

Can I assume that by keeping copies of these files, I can correct things if they go wrong by just ... puttin' 'em back?

Again - I am someone who knows nothing about computers.  I learn fast, but I know nothing. 

Thanks!

---

### Post by andrea b on 2014-05-06
Ok - I don't do well navigating by the command line ... never quite get where I'm trying to go.  But if I click Properties, both of my SP1 files are 9/3/02; my SP3 files from Preload (XP partition) are 8/4/04.  Is this the same result I'd get by navigating to open the file and using ls -l?

---

### Post by andrea b on 2014-05-06
> **oldfred said:**
> It may make a difference. 

Are dates different. And how do dates compare to mine posted above?

Ok - I don't do well navigating by the command line ... never quite get where I'm trying to go.  But if I click Properties, both of my SP1 files are 9/3/02; my SP3 files from Preload (XP partition) are 8/4/04.  Is this the same result I'd get by navigating to open the file and using ls -l?

And - I really appreciate all the time you are taking with me.  Especially considering there must be a tidal wave of XP refugees.

---

### Post by Bashing-om on 2014-05-06
andrea b; Hello,

I continue to closely follow this thread. I wish I had the means to assist further, it is "frowned upon" to respond in any thread without making a contribution to the thread at large, thus I have been silent. I am - with no regret - now Window's illiterate and do not have the means to progress this thread.

Exercise continued patience for others to offer the required advise and means to re-install Windows' boot code.

[INDENT]if a wood chuck cud chuck wood
[/INDENT]

---

### Post by andrea b on 2014-05-06
UPDATE...

Ok, I was able to get into the Rescue and Recovery partition, copy NTDETECT and NTLDR (note upper case) to usb drive, and put them into i386 (removing the ntdetect and ntldr files that were there  - note lower case).  

I don't know if this is relevant, but I found what I imagine to be the 'original' NTDETECT and NTLDR (upper case) files *outside* the Windows folder on mounting / opening the partition, listed at the bottom of the directory along with boot.ini and other stuff.   Does this make sense / is this relevant to the problem?  I realize that how things look in the GUI may ... not be relevant.

And again - wow - thanks for hanging in there with me.

---

### Post by oldfred on 2014-05-06
Case does not matter in Windows, but does in Linux. So if caps or not should make any difference.

It depends on how you boot. If you boot your Windows the boot files are at c:\ or Windows root or top level. But if you boot with another Windows, CD, or Linux it will be the mount but the top level of that mount. If that makes any sense.

Just save copies. Not sure if all this will help or not.
If you can get into Windows recovery, you should run the full set of commands from post #23.

---

### Post by andrea b on 2014-05-07
> **oldfred said:**
> Case does not matter in Windows, but does in Linux. So if caps or not should make any difference.

It depends on how you boot. If you boot your Windows the boot files are at c:\ or Windows root or top level. But if you boot with another Windows, CD, or Linux it will be the mount but the top level of that mount. If that makes any sense.

Just save copies. Not sure if all this will help or not.
If you can get into Windows recovery, you should run the full set of commands from post #23.

Well - having transferred the files to i386 - no change.  XP disc still does not recognize my HD. 

So, Question 1: when you say 'the top level / top of the partition', what exactly do you mean?  I copied the two files into Windows\Service Pack Files\i386 in the partition (which I would assume is C:\...). I'm assuming I did this correctly? Is this 'the top'? 

Question 2: If I click 'repair MBR' in Partition wizard (or did so with GParted), would I likely be able to boot into XP, run the tests from there, and then reinstall Grub if needs be? 

Thanks so much ... sorry if I'm wearing out my welcome here.

---

### Post by oldfred on 2014-05-07
All the Linux tools install a Windows work alike boot loader to the MBR, I do not think that is your issue.
And if partition is NTFS, boot sector NTFS and you have boot flag, I do not know why Windows would not see the NTFS partition and attempt to repair it.

You can write a new BS Boot sector with testdisk. I think it writes a XP type to boot with ntldr, not a newer type that is Vista or later that boots with bootmgr.

More info here:
 If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by andrea b on 2014-05-08
> **oldfred said:**
> All the Linux tools install a Windows work alike boot loader to the MBR, I do not think that is your issue.
And if partition is NTFS, boot sector NTFS and you have boot flag, I do not know why Windows would not see the NTFS partition and attempt to repair it.

You can write a new BS Boot sector with testdisk. I think it writes a XP type to boot with ntldr, not a newer type that is Vista or later that boots with bootmgr.

More info here:
 If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Unfortunately, Testdisk didn't flag anything. I ran it a few times, first ignoring its warning about incorrect number of heads / cylinders (255 vs 240) and then changing the value to 240 (there was plenty of information about this 'fix geometry'  warning message in this and other forums ... ).  I didn't get alerted to fix the Boot Sector. 

Thanks so much for sharing your knowledge. I've learned a lot.  Like: I should have come to the forum with the original slow boot problem, and avoided all this!

---

### Post by oldfred on 2014-05-08
Note sure what to suggest.
Usually 255 is correct but I have seen 240 a few times.

I might just use the testdisk command to build a new BS.

---

### Post by andrea b on 2014-05-08
> **oldfred said:**
> Note sure what to suggest.
Usually 255 is correct but I have seen 240 a few times.

I might just use the testdisk command to build a new BS.

How would this affect my ability to boot into Ubuntu? (assuming I can figure out how to do it in the first place...)

If I'm unable to boot into Ubuntu, I figure I can reinstall GRUB via Livedisc?

---

### Post by Bashing-om on 2014-05-08
andrea b;

You are not abandoned. I just have nothing to add to the booting Windows issue.
As to booting ubuntu, We had planned on (re-)installing ubuntu's boot manager when the problem with Windows was resolved.

I do not anticipate getting ubuntu to a state of booting to be a big deal.

Windows ->
[INDENT][INDENT]meanwhile back at 
[INDENT][INDENT][INDENT]the ranch
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-05-08
I am just about out of ideas on Windows issues. 
You do not seem to be getting any error messages.
It looks like what we can see from Linux, boot files are all in the correct places.
So all we can suggest are the standard XP repairs which usually work.
Sometimes you do have to run chkdsk 3 times? Or until there are no errors.

---

### Post by andrea b on 2014-05-08
> **oldfred said:**
> I am just about out of ideas on Windows issues. 
You do not seem to be getting any error messages.
It looks like what we can see from Linux, boot files are all in the correct places.
So all we can suggest are the standard XP repairs which usually work.
Sometimes you do have to run chkdsk 3 times? Or until there are no errors.

All right, then - (by the way, did you mean chkdsk, or testdisk here?  Because running chkdsk has not been possible - HD not recognized as installed by XP Recovery Console.  I know it's getting to be ... a bit much!)

I'm running testdisk one last time, in hopes it will flag a bad boot sector, and give me the option of overwriting with back up (assuming I have a good backup)  

IF this doesn't come up, my understanding is that I would go to the 'Advanced menu / Filesystem utils, and get to a screen with 'Rebuild BS' as one of the options.  And then get to a couple of screens giving me the option to write a new boot sector from backup. 

Thanks so much for helping me, oldfred and Bashin'!

---

### Post by andrea b on 2014-05-08
Ok: running testdisk to rebuild boot sector: testdisk informed me that the *current* boot sector is 'OK' - but that the *backup* is 'bad' !!!???

I've tried to include a screenshot.

---

### Post by oldfred on 2014-05-09
Backup is just in case original gets damaged, but it should be good.
I still would have test disk create a new one, which would force the current one to be the backup.
Then see if you can run chkdsk on the NTFS partition. 
Do not understand why Windows will not recognize its own partition.

---

### Post by andrea b on 2014-05-09
> **oldfred said:**
> Backup is just in case original gets damaged, but it should be good.
I still would have test disk create a new one, which would force the current one to be the backup.
Then see if you can run chkdsk on the NTFS partition. 
Do not understand why Windows will not recognize its own partition.

Ok, just so I understand ... I am to go ahead and use the 'bad' backup to overwrite the current 'ok' boot sector, which will then make the current ('ok') boot sector the new backup? 

So: will this be **[Org. BS]**  or **[Rebuild BS**]?

I guess that, since I can't boot anyway, there's no harm in trying this.

---

### Post by oldfred on 2014-05-09
You want the Rebuild BS. I think the bad backup will just be copied to the orirginal and you have two bad ones. 
Rebuild creates a new one from scratch or how ever it does it.

---

### Post by andrea b on 2014-05-09
> **oldfred said:**
> You want the Rebuild BS. I think the bad backup will just be copied to the orirginal and you have two bad ones. 
Rebuild creates a new one from scratch or how ever it does it.

Ok - rebuilt the BS ... but  XP disc Recovery Console still wouldn't recognize installed HD, so still - no chkdsk possible ...

Googled further...Apparently, this was about the SATA controller (drivers not recognized by disc).  The fix for this:
Went into BIOS and temporarily changed SATA controller to Compatibiity mode from AHCI - and voila!  The console now recognized my HD.  (I'll change it back after diagnostics / etc.) 

Did not do FIXMBR, as I assume I still want GRUB in my MBR.  Per your recommendation, did FIXBOOT C: # and and BOOTCFG / rebuild# (got a bit worried / confused about load options ... used '2' for load, and pressed ENTER past options I didn't understand...

Having figured out the path to autochk.exe, I was finally able to run chkdsk, and ran it twice.  First time, it found and corrected one or several unspecified errors.  Second time, clean.  But ... *Still *can't boot into XP!

Booting back into Ubuntu, I got a system error message, and it was way slower to load.   

So ... and I think we're nearing the end of our little journey here you've gone above and beyond -  (1) any thoughts on boot that seems to hang a bit at every stage (including loading launcher)?  (2) Is there *harm* in seeing whether fixing MBR might allow XP to boot? (I realize I'm asking this again, but hope to understand the answer better  also looked at [similar threads]("http://ubuntuforums.org/showthread.php?t=1934589") on the forum). 

Nothing like learning on your own @&%!!! machine.

---

### Post by andrea b on 2014-05-10
> **mastablasta said:**
> yes it is allowed just wrap it in code tags (the # icon)


by the way - you are needlesly complicating a very simple install.

And you noted this before it got *really* complicated (!)  However.

'Needless' is the one needless word in your reply.  With 'very simple' as close runners-up.  Obviously, it's easy to 'overcomplicate' things if something goes wrong, you know your data is backed up, you read up on things in the forums, try to figure things out / learn on your own, and *know absolutely nothing about computers*.  Which is why I posted my problem in the 'Absolute Beginners Section' rather than 'Installation and Upgrades'.  (duh!)  

Anyway - I only 'needlessly' complicate things the first time.  Nothing like learning on your own @#&%!!! machine.

---

### Post by oldfred on 2014-05-10
How did system get changed to AHCI?

I changed my system to AHCI when I got a SSD several years ago and my XP quit working. Research said you just about have to reinstall XP to add newer drivers. Where newer copies of Windows have those drivers and just need to be turned on. So in my case I finally (as I had promised for a long while) turned off XP. Never felt better. :)

---

### Post by andrea b on 2014-05-10
> **oldfred said:**
> How did system get changed to AHCI?

I changed my system to AHCI when I got a SSD several years ago and my XP quit working. Research said you just about have to reinstall XP to add newer drivers. Where newer copies of Windows have those drivers and just need to be turned on. So in my case I finally (as I had promised for a long while) turned off XP. Never felt better. :)

AHCI seems to be the default on my ThinkPads.  I wish I could just completely get along without Windows :-s. 

So ... my (I hope final) questions remain, though.  (1) After using Recovery Console, booting is slow and hangs in Ubuntu (including little graphics card flashes, which I didn't have before, but have on my other 2 Ubuntu intstalls).

(2) as a last ditch senseless measure, could it hurt to repair MBR (either via the install discs Partition Mini-tool or Recovery Console FIXMBR)? And if so - which method would you recommend?

Once again ... thanks for hanging in with me.  If only I'd come to the forum after that initial slow boot problem, rather than reinstalling ...!

---

### Post by oldfred on 2014-05-10
If you can use Windows fixMBR installs the standard Windows boot loader.

But the boot loader in the MBR almost never matters, and there are several others that work. Boot-Repair adds syslinux, some use lilo which also is an old competitor to grub but will also boot Windows. They all just look for partitions and the one with the boot flag is the PBR or partition boot sector they jump to, so they can continue to boot. PBR says to use ntldr with XP.

Then from a Windows boot do you get error messages? Have you run the full gamut of XP repairs. Beyond that I am out of idea. There have been a few systems where users just could not fix system and had to reinstall after backing up data. But most were able to fix relatively easy with the standard Windows repair commands.

---

### Post by andrea b on 2014-05-10
> **oldfred said:**
> If you can use Windows fixMBR installs the standard Windows boot loader.

But the boot loader in the MBR almost never matters, and there are several others that work. Boot-Repair adds syslinux, some use lilo which also is an old competitor to grub but will also boot Windows. They all just look for partitions and the one with the boot flag is the PBR or partition boot sector they jump to, so they can continue to boot. PBR says to use ntldr with XP.

Then from a Windows boot do you get error messages? Have you run the full gamut of XP repairs. Beyond that I am out of idea. There have been a few systems where users just could not fix system and had to reinstall after backing up data. But most were able to fix relatively easy with the standard Windows repair commands.

I hear you.  On Windows boot, all I get is a blinking horizontal cursor in the upper left corner of the screen, and need to do a hard boot to exit.  In terms of the gamut you'd recommended, did all but FIXMBR... (fixboot, chkdsk twice...)

But can you recommend anything to get back to the fast boot I'd had for Ubuntu?  Slowed down after Recovery Console work.

---

### Post by oldfred on 2014-05-10
AHCI may be part of it? Someone before posted this:
 BIOS should be set for IDE compatibility mode - May make system slower so use with caution.


In Ubuntu look at log files.
I suggest first looking at dmesg, you may have log file viewer.
Do not post as it is very long. 
But if you have entries with outright errors, warnings, or just long times between entries those require further review. 

 gksudo gedit /var/log/dmesg

---

### Post by Bashing-om on 2014-05-10
andrea b; Hey,

Still hang'n in here with yall (oldfred).
As a thought, you have made changes to Windows boot code. Maybe just maybe a change has been made such that ubuntu's grub can now boot Windows (???).
Won't hurt to try and (RE-)install grub and see what results now - only as a suggested course of action, but I can not see how trying can hurt, and it might even work now. Though I too would be much more comfortable if you could boot Windows directly.

I hope I am not interfering in any others thought processes by suggesting we try at this time to boot from grub.
From the liveDVD of ubuntu -> booted to terminal:
Terminal commands:
```

sudo mount /dev/sda2 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
Reboot, reset bios to boot from the hard drive and boot into ubuntu..!

OK, from ubuntu, once more let's see if we can pick up Window's and chainload Windows onto ubuntu's boot manager.
Terminal code:
```

sudo update-grub

```

And let's see what happens.

[INDENT][INDENT][INDENT]maybe YES,
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andrea b on 2014-05-10
> **oldfred said:**
> AHCI may be part of it? Someone before posted this:
 BIOS should be set for IDE compatibility mode - May make system slower so use with caution.


In Ubuntu look at log files.
I suggest first looking at dmesg, you may have log file viewer.
Do not post as it is very long. 
But if you have entries with outright errors, warnings, or just long times between entries those require further review. 

 gksudo gedit /var/log/dmesg
well, the logfiles are a bit above my paygrade!  I see things that could raise an eyebrow - things the system was unable to load / do.  Not sure what to look for. 

The AHCI / IDE / Compatability mode post is is what I found that allowed me to run the XP Recovery Console; I've since set it back to AHCI.  Not even really knowing what all this really means.

---

### Post by oldfred on 2014-05-10
Only for a few times did I boot my XP once I had my SSD and had to use AHCI. I would go into BIOS change from AHCI and Windows would then boot. Then reverse procedure. But I was booting XP once a week or so and the updates, slow boot and time to switch just for one application became too much. The nearest Linux app to my Quicken that I had run since DOS days, all of a sudden was good enough.

---

### Post by andrea b on 2014-05-10
> **Bashing-om said:**
> andrea b; Hey,

Still hang'n in here with yall (oldfred).
As a thought, you have made changes to Windows boot code. Maybe just maybe a change has been made such that ubuntu's grub can now boot Windows (???).
Won't hurt to try and (RE-)install grub and see what results now - only as a suggested course of action, but I can not see how trying can hurt, and it might even work now. Though I too would be much more comfortable if you could boot Windows directly.

I hope I am not interfering in any others thought processes by suggesting we try at this time to boot from grub.
From the liveDVD of ubuntu -> booted to terminal:
Terminal commands:
```

sudo mount /dev/sda2 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
Reboot, reset bios to boot from the hard drive and boot into ubuntu..!

OK, from ubuntu, once more let's see if we can pick up Window's and chainload Windows onto ubuntu's boot manager.
Terminal code:
```

sudo update-grub

```

And let's see what happens.

[INDENT][INDENT][INDENT]maybe YES,
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

Ok, so now I can't boot from HD and into Ubuntu (except from live disc) ... my F12 option (which sets out boot options) isn't there...did reinstitute it via BIOS ... but it's not coming up. 

I get GRUB prompt ... what to do?  No valid os / devices found. 

How to 'undo' what I did via live disc?  Must undo! Or redo!

Worst case scenario - this becomes a uniboot linux machine.  That's not terrible.  Maybe I'll try ... Mint.

UPDATE: ran Boot Repair, and can now boot back into Ubuntu (though not XP).  Nerves now officially shot!

Bootinfo URL: [http://paste.ubuntu.com/7444436](http://paste.ubuntu.com/7444436), if anyone still has the patience...

and I feel I've already tried youse good folkses patience enough!

---

### Post by Bashing-om on 2014-05-10
andrea b; UnGood !

OK this :
> 
 my F12 option (which sets out boot options) isn't there

Is before any operating system is even thought about by the computer. IF bios is malfunctioning many times it is a matter of the CMOS battery voltage low. How old is this machine, and when was the last time the battery was changed ?

Is this a desktop box, (easy to get to the battery) ??
OR
A laptop ?? -> maybe not at all an easy thing to do. Will have to read the instructions.

As pulling/changing the battery will revert the bios to all default values.

If we do not have bios, nothing is going to go right !

[INDENT][INDENT][INDENT]a matter of fact
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-05-10
Often if battery, then clock also reverts to some default time not correct time. So then you know it is losing settings and battery needs replacing.

Sometimes after too many warm reboots systems just seem to get confused. A total cold reboot, remove battery if laptop and hold powerswitch to drain capacitors may reset it.

This does not look right as a standard boot.ini?

```
 [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\minint
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\minint="2" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


```

What is minint, and why a "" entry? Most XP only have the third entry. Did you run the XP commands to rebuild the boot.ini?

This is my typical boot.ini 

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

```

If you edit boot.ini with Linux editor be sure to save with Windows line endings not Linux line endings. nano usually works and gedit now has an option but you have to select it when you save.

---

### Post by andrea b on 2014-05-10
Hi, Bashin', 

Got it back up.  This is a 2007 Thinkpad X60.  

Unless my Bootinfo url (a post ago) is showing up something helpful, I think I'm going to just...give up on booting XP on this machine.  Enough!  (For now...anyway.  I don't give up easy!)

I still am curious about speeding up the *Ubuntu* boot time, which has slowed since using Recovery Console on XP.  This machine was the speediest boot of my 3 ubuntu machines until then. It flashes, goes black and pauses, seems the graphics card 'hiccups'?  

On the other hand ... bah!  On to other things! 

And many, many thanks for all the support!

---

### Post by oldfred on 2014-05-10
Just posted above you.

Turn AHCI back on, if not using XP.

---

### Post by andrea b on 2014-05-10
> **oldfred said:**
> Often if battery, then clock also reverts to some default time not correct time. So then you know it is losing settings and battery needs replacing.

Sometimes after too many warm reboots systems just seem to get confused. A total cold reboot, remove battery if laptop and hold powerswitch to drain capacitors may reset it.

This does not look right as a standard boot.ini?

```
 [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\minint
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\minint="2" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


```

What is minint, and why a "" entry? Most XP only have the third entry. Did you run the XP commands to rebuild the boot.ini?

This is my typical boot.ini 

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

```

If you edit boot.ini with Linux editor be sure to save with Windows line endings not Linux line endings. nano usually works and gedit now has an option but you have to select it when you save.

oldfred -

Editing boot.ini is way above my level of competence (as is most everything I've learned / done so far...!).  So your reply went over my head ... 

'MiniNT' is likely the bootable Rescue and Recovery partition...I think. This is what old ThinkPads have in lieu of recovery discs. The partition was supposed to help me ... recover, but has served no useful purpose thus far. Isn't working well.  Could this be what's causing my problems?

---

### Post by oldfred on 2014-05-11
If the MiniNT is missing or not working that could be the problem as it shows as default boot choice. But you should get boot menu showing all three entries. The "" may just be a spacer line between the two actual entries.

---

### Post by andrea b on 2014-05-11
Ok - here's what I'm (for lack of a better word) thinking.  This Ubuntu install was buggier than my others from the beginning (which is why I reinstalled in the first place) - and my other Thinkpads, all running well on 14.04 in single or dual boot,  do NOT have this Rescue and Recovery partition (on the T60, I overwrote it with a full install of Ubuntu).  

In addition to boot slowness (now resolved more or less), this machine now exhibits weird behaviors that all occur *together* at seemingly random times: cursor will only select text, *not allow typing*; in Chrome and Firefox, this machine will start using 'open in new window' as a default for everything, including opening individual emails in Gmail; the Shift and Caps Lock keys begin to do the opposite of what they're supposed to when pressed (I've seen other forum posts on this).  This is only happening on this one machine.   A reboot is what works when this happens. 

SO, FINAL QUESTION. Would uninstalling Ubuntu (deleting its partition) revert me (possibly) to bootable XP? I might also get rid of the Rescue and Recovery partition, which hasn't proven useful; although, I would see if I could use it to revert to XP.    I would *then* reinstall 14.04 more intelligently, using whatever wisdom you have to share about setting it up with Gparted.  (although the live disc without Gparted worked beautifully on my other dual boot machine,  BECAUSE there was no R&R partition there.)

---

### Post by oldfred on 2014-05-11
Uninstalling Ubuntu now will not help XP. They are independant. You may just have to reinstall Windows.
And if you really need Windows do not install Windows XP but buy Windows 7 (or even 8) so you have a system that is supported. With XP you will soon have so many virus and other issues that you will not find it usable.

---

### Post by andrea b on 2014-05-11
> **oldfred said:**
> Uninstalling Ubuntu now will not help XP. They are independant. You may just have to reinstall Windows.
And if you really need Windows do not install Windows XP but buy Windows 7 (or even 8) so you have a system that is supported. With XP you will soon have so many virus and other issues that you will not find it usable.

Got it. Though I would not be going *online* with XP!  Only using it for applications offline.   

I will open a separate thread for the weird cursor and window-opening behavior.

I think we're at the end of the road ... finally.  Thanks so much for your wisdom and patience. (!)

---

### Post by andrea b on 2014-05-17
Final update: my conclusion, based on things I've read elsewhere, is that a combination of significantly resizing the XP partition *and* the presence of that FAT32 recovery partition caused booting weirdness, whether by messing with Windows' filesystem and / or something else.  Ultimately: installed Windows 7 (full disc) and am now preparing to use GParted to prepare for a proper dual boot install with shared NTFS data partition.  Which means ... a new thread, probably.  No matter how much I read, I always manage to mess something up!

Lookin' forward to the day when I won't need Windows ... but unfortunately, it's still a ball and chain I can't get get away from. 

Thanks again for your amazing support.

---

### Post by oldfred on 2014-05-17
Be sure to shrink Windows 7 with its own disk managment tools, but do not create partitions with Windows. Use gparted. Immediately after resize, reboot Windows so it can run chkdsk and update its internal info to its new size.

Then use gparted to create partitions you want. And use Something Else in installer to choose which partition it / and its format like ext4.

I had old partitions with old installs, so I just had to select that partition. It auto finds swap if it already exists.

---

### Post by andrea b on 2014-05-21
Ok, final (triumphant) post - all's well that ends well.  Purchased an OEM Win7 disc, installed it.  (Before seeing oldfred's post).  Defragged and ran chkdsk to start (probably unnecessary after a fresh install, but what do I know?). Win7 Disk Management would not allow me to shrink shrink the partition to the size I'd had in mind (by around 23 GiB)  so I did end up using GParted, figuring I could use the Win7 disc's repair and recovery tools to fix the partition if it broke. But nothing broke.  Created shared ntfs data partition, and extended partition for root and swap. It all kind of went ... fine! and both Win 7 and Ubuntu boot fine.  

Now I'm just figuring out how to save stuff efficiently to the shared data partition. 

Thanks so much for all your help!!!

This was really a great experience - learned a lot.

---

### Post by oldfred on 2014-05-21
I have two data partitions. One NTFS and one Linux formatted. You have to mount it and if NTFS assign default ownership & permissions as part of the mount. You do that in fstab.

Then depending on what you want you can directly mount in /home, mount in /media, or mount in /mnt. If just some data you can use /home. Many use /media as that is the default mount of external devices, but it may show a second time in Nautilus left panel. If in /mnt you will not see it in /home, but then can link each folder in your data partition into /home if desired.

 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by Bashing-om on 2014-05-21
andrea b; Great !

See oldfred's last.

Pleased you are now up and running .
It just goes to show ->
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

