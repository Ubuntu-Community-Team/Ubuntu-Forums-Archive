---
title: "Help. Wubi installed ubuntu. Windows 7. NTLDR is missing"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by gk3 on 2012-08-15
i was running a ubuntu and windows 7 dual boot
My wubi installed ubuntu 12.04 failed to boot up so i made a live usb of the boot repair disk iso. I backed up my data in a different partition and selected recommended repair.

Now i am getting the msg 
"NTLDR is missing"
and i cant even boot into my windows7 and m stuck with using the live usb at the moment.

Help me before i pull my hair out.:confused:

---

### Post by barrykgerdes on 2012-08-15
That usually happems when the item in the menu refers to the wrong drive number.

Barry

---

### Post by bcbc on 2012-08-15
From what I've seen, Bootrepair posts your bootinfoscript results to pastebin. Can you post that link?

---

### Post by gk3 on 2012-08-16
[http://paste.ubuntu.com/1149298/](http://paste.ubuntu.com/1149298/)

heres my repair log of boot repair disk.
from the thing i have read it seems to me that the repair ive tried was for a ubuntu clean install and not a wubi install from inside windows which has screwed up the boot process. Please help as i have no intentions to go through a clean install. I can agree to get rid of the wubi installed ubuntu 12.04 as ive managed to extract all my data and back it up. 
ive read that ntldr isnt usually a problem associated with windows 7 boots and that its usually something like bootmgr is missing.
i am going to try a startup repair using the windows 7 installation CD but i doubt my cdrom works. If it doesn't i am stuck.

---

### Post by bcbc on 2012-08-16
There are a few puzzling bits. 
Why it's complaining about /ntldr which (as you say) isn't even needed for win7 and in any case is there. 
Why bootrepair resulted in an unbootable windows which was working fine beforehand?
Unconventional partitions - /dev/sda1 is extended and it starts at sector 16065?

But having said that there's nothing that jumps out. I would go with a win7 repair disk. Or the install DVD and see if that can fix it.

You could [ask the creator]("http://ubuntuforums.org/showthread.php?p=10871917#post10871917") of bootrepair what might have made Windows stop booting. That doesn't seem like a good outcome for the repair assuming that that is all that you did.

Generally when wubi stops booting it requires a chkdsk (from windows). In the past there have been issues with overwritten bootloaders, and sometimes an fsck on the root.disk will help, but usually the chkdsk is the first recommended fix. So maybe bootrepair can be changed to check first before replacing a good bootloader or making other unnecessary mods.

So... in short... I'm not sure what happened, but I'd recommend the win7 repair route.

---

### Post by gk3 on 2012-08-16
could it have something to do with the fact that i upgraded from windows xp to windows 7 and it used to show an 'earlier version of windows' on boot which was dead.
not really helping as my cdrom is refusing to work.
m stuck with using the live usb at the moment.
i would have to make a bootable win7 usb from another pc at a friends house which could take hours.

---

### Post by gk3 on 2012-08-16
i did a bit more reading up on the subject and it seems that bios is looking for ntldr whereas it should be looking for the bootmgr which means somehow my windows 7 pbr has been replaced by a winxp pbr. Is it anyway i can undo this using the live boot repair disk usb as i can access the hard drive but dont have editors or programs except the terminal and text editors. 

as i mentioned earlier my cdrom doesnt seem to be working and i have only one 4gb usb through which i am using the boot repair disk.

---

### Post by gk3 on 2012-08-16
FIXED!
i renamed my bootmgr as ntldr and i got the bootmenu working. Can finally boot into my windows 7!
i will back up all my files and transfer all my data to a separate hard disk and do a fresh install of windows 7 and ubuntu!

Thanks for your help guys!!
:guitar:

---

### Post by YannBuntu on 2012-08-16
**@gk3:** good job! Please could you detail what you did exactly? did you rename the "bootmgr" file into "ntldr" ?
Also, if you have used Boot-Repair several times, please could you attach your log history (run Boot-Repair, click "Advanced options", click the "Backup partition tables..", save the ZIP file somewhere, then attach it to your reply).

**@bcbc:** I don't understand why Win7 would need ntldr, maybe because of the XP upgrade? B-R can't change any PBR. According to the log, what B-R did is:
1) mounting and opening root.disk to let the user backup files
2) a fsck of the root.disk,
3) put a syslinux generic MBR into sda,
4) put the boot flag on sda2 (which is the good place AFAIK).
This shouldn't have messed up the Windows boot. I hope that gk3's log will help understand.

---

### Post by bcbc on 2012-08-16
> **YannBuntu said:**
> **@gk3:** good job! Please could you detail what you did exactly? did you rename the "bootmgr" file into "ntldr" ?
Also, if you have used Boot-Repair several times, please could you attach your log history (run Boot-Repair, click "Advanced options", click the "Backup partition tables..", save the ZIP file somewhere, then attach it to your reply).

**@bcbc:** I don't understand why Win7 would need ntldr, maybe because of the XP upgrade? B-R can't change any PBR. According to the log, what B-R did is:
1) mounting and opening root.disk to let the user backup files
2) a fsck of the root.disk,
3) put a syslinux generic MBR into sda,
4) put the boot flag on sda2 (which is the good place AFAIK).
This shouldn't have messed up the Windows boot. I hope that gk3's log will help understand.

I did look at the log, and as I said there wasn't anything that jumped out that could explain the problem.

However, there are some concerns... you shouldn't have to manipulate the boot flag or replace the bootloader if they are working. While this shouldn't make a difference, it does assume that everyone is using a generic windows-style bootloader and that's not always the case (OEM specific). 

Maybe part of the interactive experience could be to ask the user if the computer is booting okay before including that in the recommended fix.

---

### Post by bcbc on 2012-08-16
> **gk3 said:**
> FIXED!
i renamed my bootmgr as ntldr and i got the bootmenu working. Can finally boot into my windows 7!
i will back up all my files and transfer all my data to a separate hard disk and do a fresh install of windows 7 and ubuntu!

Thanks for your help guys!!
:guitar:

Great!

---

### Post by YannBuntu on 2012-08-16
**@bcbc:** good idea -> [https://blueprints.launchpad.net/boot-repair/+spec/ask-if-windows-ok-when-wubi](https://blueprints.launchpad.net/boot-repair/+spec/ask-if-windows-ok-when-wubi)
The boot flag re-set on same location is a bug: [https://bugs.launchpad.net/boot-repair/+bug/1037733](https://bugs.launchpad.net/boot-repair/+bug/1037733)
Please could you point me to cases of OEM MBRs?

---

### Post by bcbc on 2012-08-16
> **YannBuntu said:**
> **@bcbc:** good idea -> [https://blueprints.launchpad.net/boot-repair/+spec/ask-if-windows-ok-when-wubi](https://blueprints.launchpad.net/boot-repair/+spec/ask-if-windows-ok-when-wubi)
The boot flag re-set on same location is a bug: [https://bugs.launchpad.net/boot-repair/+bug/1037733](https://bugs.launchpad.net/boot-repair/+bug/1037733)
Please could you point me to cases of OEM MBRs?

I looked for an old bootinfoscript from my dell, but couldn't find it. However, here's a link that explains what I am on about: [http://www.goodells.net/dellrestore/dellmbr.shtml](http://www.goodells.net/dellrestore/dellmbr.shtml). I don't think they're that common today - probably only on older computers (but not sure - maybe Asus still use them).

Thanks for adding the blueprint!

---

### Post by gk3 on 2012-08-16
Deleted post

---

### Post by gk3 on 2012-08-16
> Re: Help. Wubi installed ubuntu. Windows 7. NTLDR is missing
@gk3: good job! Please could you detail what you did exactly? did you rename the "bootmgr" file into "ntldr" ?
Also, if you have used Boot-Repair several times, please could you attach your log history (run Boot-Repair, click "Advanced options", click the "Backup partition tables..", save the ZIP file somewhere, then attach it to your reply).

yeap, while inside the live usb, i renamed the bootmgr file to ntldr  and the pc booted into the Choose OS bootmenu just fine after that.


My C drive contains the boot-sav folder, i can send you the different log files named 'RESULTS' in each repair folder if those files can help. (m just scared of running boot repair disk again sorry)


Also, now that i see  my pc is fairly messy with all the OSes ive attempted to install, this is what i have in mind:

I have 4 partitions of a 160gb HD
c -win7
d -ubuntu 
e -my data
f - my sisters data

each partition has around 40gb

i am planning to format the data on the d drive and shrink it down to 30gb using [http://www.majorgeeks.com/Partition_Wizard_Home_Edition_d6175.html](http://www.majorgeeks.com/Partition_Wizard_Home_Edition_d6175.html)
and will fresh install windows 7 on the new 30gb partition.

after that ill try different linux distros on the current c drive which i will shrink down to 20gb while inside the new windows 7.

ill distribute the remaining space to my  current data drives, e and g so that i can have more space for my data.

Can you spot any problem with the plan? 



P.S again, thankyou for all the time and effort you guys have spent to help me. Much Appreciated.
:KS

---

### Post by bcbc on 2012-08-16
Since you're starting from scratch, I'd skip using Wubi and do a normal dual boot. Wubi is not available for many other linux distros and support is not as good as for normal Ubuntu.

You will probably have to brush up on bootloaders if you do a normal install - most will use Grub2.

---

### Post by YannBuntu on 2012-08-16
> **gk3 said:**
> yeap, while inside the live usb, i renamed the bootmgr file to ntldr  and the pc booted into the Choose OS bootmenu just fine after that.

ok thanks. Before this, you deleted the old ntldr file, didn't you?



> **gk3 said:**
> My C drive contains the boot-sav folder, i can send you the different log files named 'RESULTS' in each repair folder if those files can help.

Yes please. Or just make a ZIP of the entire "boot-sav" folder.

> **gk3 said:**
> m just scared of running boot repair disk again

I understand. FYI, the "Backup partition table.." button doesn't change the system. Only the "Apply" and "Recommended repair" buttons do. 


[QUOTE=bcbc]Since you're starting from scratch, I'd skip using Wubi and do a normal dual boot. Wubi is not available for many other linux distros and support is not as good as for normal Ubuntu.[/QUOTE]

+1

---

### Post by gk3 on 2012-08-16
>  Since you're starting from scratch, I'd skip using Wubi and do a normal dual boot. Wubi is not available for many other linux distros and support is not as good as for normal Ubuntu.

You will probably have to brush up on bootloaders if you do a normal install - most will use Grub2. 


yup i didnt plan on using wubi anyways, i would use live usb first and if i like it enough i would install it manually.


> ok thanks. Before this, you deleted the old ntldr file, didn't you?
Yup.

ive attached the boot-sav folder.

---

### Post by YannBuntu on 2012-08-17
> **gk3 said:**
> ive attached the boot-sav folder.

Thanks. Your case is very interesting, so it would be nice if you could provide a little more information: _before you reinstall Ubuntu_, please could you do the following:
1) start Boot-Repair from a liveCD or liveUSB, click "Advanced options", click the "Backup partition tables.." button, save the **ZIP file** somewhere, then attach it to your reply.
2) come back to the main window, then click the "Create BootInfo summary" button. Indicate the **new URL** that will appear.

(This will just scan your system, it won't change your boot.)

---

### Post by gk3 on 2012-08-17
> **YannBuntu said:**
> Thanks. Your case is very interesting, so it would be nice if you could provide a little more information: _before you reinstall Ubuntu_, please could you do the following:
1) start Boot-Repair from a liveCD or liveUSB, click "Advanced options", click the "Backup partition tables.." button, save the **ZIP file** somewhere, then attach it to your reply.
2) come back to the main window, then click the "Create BootInfo summary" button. Indicate the **new URL** that will appear.

(This will just scan your system, it won't change your boot.)

Aah, i already did the fresh install :(

---

### Post by YannBuntu on 2012-08-17
ok, then please could you provide:
1) same as my last post
2) same as my last post
3) now in the GRUB menu, you should have two Windows entries (sda2 and sda3). Do both work?

---

### Post by oldfred on 2012-08-17
I think the original problem started with the deletion of the Windows boot partition or a change to partitions that moved it to the logical partition. Windows only boots from the one primary  partition with the boot flag. Then Boot-Repair fixed - added boot flag to  another install in a NTFS primary but its PBR - partition boot sector happened to have all the Windows 7 boot files (which is unusual unless OP copied them), but the NTFS boot sector was still XP. 

NTFS has at least two versions of NTFS partition boot sectors. I ran chkdsk on my XP install from a Windows 7 repairUSB and it did work better, but also wrote a Windows 7 PBR into my XP. It has more difference than just the boot file of bootmgr vs. ntldr which I could see with the comparison in testdisk of current & backup PBRs.

I think rather than renaming bootmgr to ntldr, it would have been  better to run fixboot from Windows to update PBR to the Windows 7 version of the PBR.

---

### Post by gk3 on 2012-08-17
ive done a lot of things since i renamed the bootmgr to ntldr.
Since i didnt have access to windows 7 installation disk nor could boot into the os my primary focus was to get into the system somehow and make it working. 

After getting back access, i made a win7 installation cd, ran a windows 7 startup repair which fixed the boot sequence and the bootmgr.

Then i proceeded to get rid of both my old win7 (it was getting bogged down) and the ubuntu which i couldnt fix. I played with the partitions a bit. 

I still want my pc in the best state possible and if you could think of anything which could help me overcome any lingering after effects of the events i would be happy to comply.

---

### Post by bcbc on 2012-08-17
@yannbuntu, I don't understand this RESULTS.txt. It shows the boot flag on /dev/sda3, but if you look lower down it shows a *parted* output that says it's on /dev/sda2.

This is the modified RESULT.txt put together with boot-repair and bootinfoscript I guess, but it's not clear why it would report this difference or what the timing is (is it chronological? if so the boot flag somehow changed between running bootinfoscript and the boot-repair running of parted and fdisk?)



```
                Boot Info Script 0.61-git      [15 June 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr /ntldr /NTDETECT.COM 
                       /wubildr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /wubildr 
                       /wubildr.mbr

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........X.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1326832 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

[COLOR="Red"]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1              16,065    81,915,434    81,899,370   f W95 Extended (LBA)
/dev/sda5              16,128    81,915,434    81,899,307   7 NTFS / exFAT / HPFS
/dev/sda2          81,915,435   163,830,869    81,915,435   7 NTFS / exFAT / HPFS
/dev/sda3    *    163,830,870   235,512,899    71,682,030   7 NTFS / exFAT / HPFS
/dev/sda4         235,512,900   312,576,704    77,063,805   7 NTFS / exFAT / HPFS
[/COLOR]

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,831,551     7,831,489   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       56f0b0d5-304d-45dd-85dd-f3f02674c4e7   ext3       
/dev/sda2        F4CC66DBCC66981E                       ntfs       Gautam
/dev/sda3        32946F2F946EF52F                       ntfs       Seven7
/dev/sda4        84787328787317DE                       ntfs       Docx
/dev/sda5        FC3E1D933E1D47D2                       ntfs       
/dev/sdb1        8094-B1F9                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /media/disk              squashfs   (ro,nosuid,nodev,uhelper=udisks)
/dev/loop1       /mnt/boot-sav/wubi1      ext3       (rw)
/dev/sda2        /media/Gautam            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/Seven7            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/Docx              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /live/image              vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)


======================== sda5/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root FC3E1D933E1D47D2
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root FC3E1D933E1D47D2
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root FC3E1D933E1D47D2
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux	/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=FC3E1D933E1D47D2 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root FC3E1D933E1D47D2
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	echo	'Loading Linux 3.2.0-27-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=FC3E1D933E1D47D2 loop=/ubuntu/disks/root.disk ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-27-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root FC3E1D933E1D47D2
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=FC3E1D933E1D47D2 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root FC3E1D933E1D47D2
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=FC3E1D933E1D47D2 loop=/ubuntu/disks/root.disk ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

============================= sda5/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk	none	swap	sw	0	0
--------------------------------------------------------------------------------

================= sda5/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   8.953720093 = 9.613983744    boot/grub/grub.cfg                             1
   2.634811401 = 2.829107200    boot/initrd.img-3.2.0-23-generic-pae          90
   9.502052307 = 10.202750976   boot/initrd.img-3.2.0-27-generic-pae          65
   0.960227966 = 1.031036928    boot/vmlinuz-3.2.0-23-generic-pae             21
   8.947534561 = 9.607342080    boot/vmlinuz-3.2.0-27-generic-pae             22
   8.947534561 = 9.607342080    vmlinuz                                       22
   0.960227966 = 1.031036928    vmlinuz.old                                   21

========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

========================== sda3/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit boot=live config   quiet

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label 32bits session
kernel /live/vmlinuz
append initrd=/live/initrd.img boot=live config   quiet

label ubnentry2
menu label 64bits session
kernel /live/vmlinuz2
append initrd=/live/initrd2.img boot=live config   quiet

label ubnentry3
menu label 32bits session (failsafe)
kernel /live/vmlinuz
append initrd=/live/initrd.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal

label ubnentry4
menu label 64bits session (failsafe)
kernel /live/vmlinuz2
append initrd=/live/initrd2.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal

label ubnentry5
menu label Memory test
kernel /live/memtest
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[135664]) leaked on lvscan invocation. Parent PID 27362: bash
File descriptor 8 (pipe:[135664]) leaked on lvscan invocation. Parent PID 27362: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-08-16__00h35 ===================
boot-repair version : 3.18-0ppa34~lucid
boot-sav version : 3.19-0ppa77~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version : 3.18-0ppa14~lucid
File descriptor 7 (pipe:[135664]) leaked on lvs invocation. Parent PID 12535: /bin/sh
File descriptor 8 (pipe:[135664]) leaked on lvs invocation. Parent PID 12535: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 02.07.2012 , squeeze , Debian , i686)
CPU op-mode(s):        32-bit

=================== os-prober:
/dev/sda2:Windows 7 (loader):Windows:chain
/dev/sda3:Windows 7 (loader):Windows1:chain

=================== blkid:
/dev/sda2: LABEL="Gautam" UUID="F4CC66DBCC66981E" TYPE="ntfs"
/dev/sda3: LABEL="Seven7" UUID="32946F2F946EF52F" TYPE="ntfs"
/dev/sda4: LABEL="Docx" UUID="84787328787317DE" TYPE="ntfs"
/dev/sda5: UUID="FC3E1D933E1D47D2" TYPE="ntfs"
/dev/sdb1: UUID="8094-B1F9" TYPE="vfat"
/dev/loop0: TYPE="squashfs"


1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

There is Wubi inside sda5

=================== PARTITIONS & DISKS:
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	ntldr,	no-winload,	no-recov-nor-hid,	bootmgr,	grldr,	Boot/BCD,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sda2.
sda3	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	grldr,	Boot/BCD,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sda3.
sda4	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sda4.
sda5	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sda5.

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes

[COLOR="red"]=================== parted -l:

Model: ATA ST3160212A (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
1      8225kB  41.9GB  41.9GB  extended               lba
5      8258kB  41.9GB  41.9GB  logical   ntfs
2      41.9GB  83.9GB  41.9GB  primary   ntfs         boot
3      83.9GB  121GB   36.7GB  primary   ntfs
4      121GB   160GB   39.5GB  primary   ntfs
[/COLOR]

Model: Corsair Flash Voyager (scsi)
Disk /dev/sdb: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  4010MB  4010MB  primary  fat32        boot, lba


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sdb1 on /live/image type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,allow_other,blksize=4096)
/dev/loop0 on /media/disk type squashfs (ro,nosuid,nodev,uhelper=udisks)


/sys/block/fd0:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  agpgart block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dri dvd fb0 fd fd0 full fuse hidraw0 hidraw1 hidraw2 hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 sda sda1 sda2 sda3 sda4 sda5 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sndstat sr0 stderr stdin stdout urandom v4l vga_arbiter video0 xconsole zero
/mnt/boot-sav/sda2:  Boot bootmgr BOOTSECT.BAK ChromeOS-Vanilla-2707.0.2012_08_04_1632-rd7a8aafa.img GK Docx grldr LIMBO [Install&Play].rar NTDETECT.COM ntldr $RECYCLE.BIN RECYCLER **** Sindhya user stuff Thumbs.db Users win7ldr Windows 7 installation files wubildr
/mnt/boot-sav/sda3:  Add_Show_Hide_File_Extensions_Option.reg Add_Show_Hide_Hidden_Files_Option.reg autoexec.bat Boot bootmgr boot-sav Config.Msi config.sys debug.log Documents and Settings DriveKey grldr Hardware.ini IORRT IO.SYS MSDOS.SYS NVIDIA pagefile.sys PerfLogs ProgramData Program Files Recovery $Recycle.Bin RECYCLER Samsung Show_File_Extension_On_Off.vbs Show_Hidden_Files_On_Off.vbs System Volume Information Thumbs.db Users Windows Windows.old wubildr wubildr.mbr
/mnt/boot-sav/sda5:  ChromeOS-Vanilla-2722.0.2012_08_07_1628-rd7a8aafa.img Config.Msi PFiles Plugins Program Files $RECYCLE.BIN System Volume Information ubuntu $WINDOWS.~BT

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    506M   43M  463M   9% /
tmpfs        tmpfs    506M     0  506M   0% /lib/init/rw
udev         tmpfs    501M  212K  500M   1% /dev
tmpfs        tmpfs    506M     0  506M   0% /dev/shm
/dev/sdb1     vfat    3.8G  363M  3.4G  10% /live/image
tmpfs        tmpfs    506M   43M  463M   9% /live/cow
tmpfs        tmpfs    506M     0  506M   0% /live
tmpfs        tmpfs    506M   20K  506M   1% /tmp
/dev/sda2  fuseblk     40G   11G   29G  27% /mnt/boot-sav/sda2
/dev/sda3  fuseblk     35G   27G  7.5G  79% /mnt/boot-sav/sda3
/dev/sda4  fuseblk     37G   33G  4.4G  89% /mnt/boot-sav/sda4
/dev/sda5  fuseblk     40G   13G   27G  33% /mnt/boot-sav/sda5
/dev/loop0
squashfs    320M  320M     0 100% /media/disk

[COLOR="red"]=================== fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8efb4639

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        5099    40949685    f  W95 Ext'd (LBA)
/dev/sda2   *        5100       10198    40957717+   7  HPFS/NTFS
/dev/sda3           10199       14660    35841015    7  HPFS/NTFS
/dev/sda4           14661       19457    38531902+   7  HPFS/NTFS
/dev/sda5               2        5099    40949653+   7  HPFS/NTFS
[/COLOR]
Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d4b23

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3915744+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
phys=(486, 254, 63) logical=(487, 125, 22)



=================== Recommended repair
recommendedrepair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda3.
Additional repair will be performed: unhide-bootmenu  repair-wubi


mount -o loop /mnt/boot-sav/sda5/ubuntu/disks/root.disk /mnt/boot-sav/wubi1
Warning: unknown mime-type for "/mnt/boot-sav/wubi1/home" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 3 boot on

                                                                          
Information: You may need to update /etc/fstab.


Boot successfully repaired.

You can now reboot your computer.

paste.debian ko, using paste.ubuntu

```

---

### Post by YannBuntu on 2012-08-17
@oldfred: i agree

@bcbc: this boot flag location incoherence (+ the fact that bootmgr has remained despite renaming) is why i asked more information.
FYI, the Boot-Info report provided by B-R is not in chronological order: indeed the BIS script is executed at the very end of the process, but I prefer to display its output at the start of the report.

@gk3: ok. I think we won't be able to understand fully what happened then. :( It was the 1st time for me to see a XP upgraded to Seven.

---

### Post by gk3 on 2012-08-20
This is my new hard drive configuration:

C: Windows 7 (30gb)
D: Secondary OS (20gb -Empty atm)
E and H: MY DATA (50 gb each)

After dividing the partitions as such using my last windows 7 I installed a fresh windows 7 and accidently deleted the old installation which obviously lead to the deletion of the original bcd and bootmgr being used to boot and rendered the pc bootless again. Installing the Fresh Windows again on the drive obviously fixed it but there is one anomaly i still dont get. 

Even though i completely formatted the drives which contained my previous OS installations the new boot menu still lists these four options 

Windows 7 (Currently being used)
Earlier version of Windows (DEAD)
Windows 7 (DEAD)
Ubuntu (DEAD)

The fresh installation of windows 7 would have installed the bcd and bootmgr in the partition i used to install the new windows , right?

Is it okay if i get rid of the other options using the boot menu editor of EASYBcd?

---

### Post by oldfred on 2012-08-20
Not necessarily. Windows can be installed muliple times, but it always installs its boot files to the partition with the boot flag. So when you installed did you have boot flag on that partition?

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by bcbc on 2012-08-20
It shouldn't be a problem.

Bootloader -> Boot sector -> Boot manager (bcd). 

Deleting non-working boot entries in the bcd will have no effect.

---

### Post by bcbc on 2012-08-20
@Yannbuntu,

So I'm confused. You said that boot-repair moved the bootflag to sda3 from sda2 and this stopped windows booting. Yet in your [bug report]("https://bugs.launchpad.net/boot-repair/+bug/1037733") you said that:
> The boot flag was initially on sda2.

Observed result: B-R set the boot flag again on sda2. (useless action)
Expected result: B-R should have done no action on the boot flag

And you marked the priority as low. I'd say it's a critical bug if it's stopping an OS booting. :confused:

---

### Post by YannBuntu on 2012-08-20
> **bcbc said:**
> You said that boot-repair moved the bootflag to sda3 from sda2 and this stopped windows booting.

I already uploaded a fix (boot-sav >= 3.192ppa9) in the [PPA]("https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages") for this critical bug. Now B-R should detect windows boot partition containing both ntldr and bootmgr, and leave the bootflag on it even when there is bootmgr in the windows system partition.

> **bcbc said:**
> Yet in your [bug report]("https://bugs.launchpad.net/boot-repair/+bug/1037733")

This is another bug.

---

### Post by gk3 on 2012-08-21
Okay thanks guys,

btw which Linux distros are worth trying on an old pc?

and how about the chromium OS?

---

### Post by YannBuntu on 2012-08-21
Light Ubuntu variants: Xubuntu and Lubuntu
Other: [http://en.wikipedia.org/wiki/Lightweight_Linux_distribution](http://en.wikipedia.org/wiki/Lightweight_Linux_distribution)

Better opening another thread.

---

