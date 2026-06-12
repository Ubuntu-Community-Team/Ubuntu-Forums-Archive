---
title: "Dual-boot woes"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by kathrync on 2012-10-18
I am having real trouble getting my dual boot system set-up.  I suspect the answer is probably out there somewhere already, but I am new to this and having trouble sorting through all the information.

The story so far is this:

I have a new desktop with Win 7 64 bit installed on an HDD it.

I put in a separate SSD, and installed Ubuntu 12.04 on that.

When I boot, the GRUB menu comes up with the following options:
Ubuntu
Advanced options for Ubuntu
Windows UEFI loader
Windows UEFI memory test
Windows 7 loader (on /dev/sda3)

Ubuntu boots ok

Selecting the Windows UEFI option gives me the error message:
"error: no such device: 9273-9636
error: file '/EFI/Microsoft/Boot/bootmgfw.efi.bkp' not found."

Selecting the Windows 7 loader option gives me:
"error: invalid EFI file path"

Worryingly, I can't boot from my Win 7 recovery or install disc to attempt to fix things from the Windows side.  I have tried forcing this from the BIOS (or UEFI or whatever it is now) to no avail...not even setting the CD-ROM drive to the top of the boot list works (and weirdly when I try it that, I find that it has moved itself back down the list when I go back in to try again).  I also tried selecting the system recovery option from the UEFI boot menu, but that took me back to the GRUB menu.

I am totally at a loss, and without being able to boot from my Win 7 discs I don't even know where to start fixing it (my first instinct is to attempt start-up repair in Windows but I can't get into it or boot from a CD to do that).

I have tried running boot-repair as well but that doesn't seem to have achieved anything.  The URL with the output  is here [http://paste.ubuntu.com/1287871/](http://paste.ubuntu.com/1287871/) if it is useful to anyone though.

I suspect my problem is either that I have installed GRUB in the Windows MBR, or that there is some UEFI/BIOS incompatibility going on but I don't know how to solve it.

Any help much appreciated...but please, treat me like an imbecile and walk me through every step...don't assume I know anything!  The point of installing Ubuntu was to learn about Linux, but I didn't quite expect to end up in the deep end like this!

Cheers

K

---

### Post by mitsi on 2012-10-18
hello , does your keyboard stop working as do the mouse buttons or not because if they stop  it might be a graphics card and / or driver problems ,also that is the problem i have not being able to re-install or fix from either ubuntu or win 7  side , most disappointing , my old laptop ( stand-alone on unbuntu ,no windows , is still working like new no problem ) found those answers on f1 online ,now i dont' know what to do next also don't rush into wiping out any thing just yet give it a little time so yeah look at your drivers hope that this helps a little ,knowing what  could be causing  problem is a start ,all the best , and good luck .  mitsi

---

### Post by AndyOpie150 on 2012-10-18
Try burning the Boot-Repair .iso to a CD and choose the first option. If that doesn't fix the problem go into the advanced section and choose to install a generic MBR to sda.

Check it out here: [http://ubuntuforums.org/showpost.php?p=12217150&postcount=2](http://ubuntuforums.org/showpost.php?p=12217150&postcount=2)

---

### Post by oldfred on 2012-10-19
You have Windows in the new UEFI boot mode with the drive partitioned with gpt partitioning.
You have Ubuntu on the SSD booting in the old BIOS mode with the drive partitioned in MBR(msdos) mode.

They do not work well when in different modes. Best to reinstall Ubuntu in UEFI mode using gpt partitioning.

Arch also recommends gpt partitioning on SSDs, but Windows only works with gpt when in UEFI mode. But you already are in UEFI mode so all drives should be gpt.

You have to use the 64bit version and boot the installer USB in UEFI mode or from UEFI choosing efi.

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by kathrync on 2012-10-19
Thanks oldfred, those links look very comprehensive.  I am away for the weekend so I won't get a chance to give this a go until Sunday or Monday evening, but I'll get back on here and let you know if I managed to sort it out (or possibly ask more stupid questions if not :) )

---

### Post by kathrync on 2012-10-23
Ok, so I've had a fiddle over the last couple of days and I think I'm getting there but I still can't make it work properly.

I managed to re-install Ubuntu in UEFI mode by following the very useful links that were posted.  See [http://paste.ubuntu.com/1301258/](http://paste.ubuntu.com/1301258/) for confirmation of that.

The situation at the moment is:

-If I remove the SSD with Ubuntu on it, Windows boots with no problems.

-If I put the SSD back in and boot with priority going to the HDD with Windows on it, it tries to boot Windows and gets as far as the splash screen which says "Starting Windows" and has the animated Windows logo on it.  From there, it goes to the GRUB menu rather than actually going into Windows.  The GRUB menu has an option for Windows but it doesn't work (I get the invalid EFI path error iirc).  I can boot Ubuntu ok from there though.

-If I put the SSD in and boot with priority going to the SSD, it goes directly to GRUB, but again no access to Windows.

I have tried running startup repair in Windows and boot-repair in Ubuntu but neither have fixed this problem.  I considered using a tool like EasyBCD to try and sort it out from within Windows, but as I can't boot Windows with the SSD containing Ubuntu in place this is proving difficult unless there's some trick I don't know.

While it's great to have both systems running again, rummaging around inside my box to remove the SSD every time I want to boot Windows is a little impractical....any tips for getting me the rest of the way there??

Thanks!

---

### Post by newb85 on 2012-10-23
Random thought from someone who doesn't really know what's going on:
Could it be that the drives are being identified differently when the SSD is in place, so Windows doesn't boot correctly because something is pointing to the wrong drive?

---

### Post by kathrync on 2012-10-23
> **newb85 said:**
> Random thought from someone who doesn't really know what's going on:
Could it be that the drives are being identified differently when the SSD is in place, so Windows doesn't boot correctly because something is pointing to the wrong drive?

That's where my line of thought is taking me as well.  I suspect that the Windows boot loader must somehow be pointing at GRUB.  Unfortunately, I have no idea how I can find out if this is the case, or how to fix it!

In any event, it is late here and I am off to bed, but I'll have a look at this tomorrow and see if there are any suggestions... :)

---

### Post by oldfred on 2012-10-23
It looks like sdb is still formatted as MBR? Only the listing for sda says gpt. And gpt drives do not have extended partitions.

So when you boot from sdb are your really booting grub in MBR mode, even though you show efi files in sdb1? There was some question if efi worked in MBR and no one knew. Maybe we just found out?

When in efi mode, grub2's os-prober does not create a valid chainload entry to the Windows efi. But Yann has updated Boot-Repair to fix that if grub-efi is installed not grub-pc for BIOS.

---

### Post by kathrync on 2012-10-24
> **oldfred said:**
> It looks like sdb is still formatted as MBR? Only the listing for sda says gpt. And gpt drives do not have extended partitions.

So when you boot from sdb are your really booting grub in MBR mode, even though you show efi files in sdb1? There was some question if efi worked in MBR and no one knew. Maybe we just found out?

When in efi mode, grub2's os-prober does not create a valid chainload entry to the Windows efi. But Yann has updated Boot-Repair to fix that if grub-efi is installed not grub-pc for BIOS.

Yeah, I was wondering about that after I logged off and went to bed last night.  Yesterday I was so pre-occupied with making sure the EFI files were present that I forgot to check how sdb was partitioned.

I re-partitioned sdb when I re-installed Ubuntu using the partitioning tool in the installer which you get to by selecting "do something else".  I didn't see any options for gpt partitioning there (at the time, I assumed that if you had booted in EFI mode, it would assume you wanted gpt partitions), so I'm guessing the next thing to try is to reformat sdb and pre-partion it using something like GParted before re-installing Ubuntu??  I just want to make sure that sounds like a sensible plan before I go for it!

I am not familiar with GParted...can I run it via my Live USB version of Ubuntu, or will I have to make a separate Live USB with just GParted on it??

K

---

### Post by oldfred on 2012-10-24
I think gparted just defaults to MBR(msdos).

You have click on device, create partition table, and open the advanced and in the combo box choose gpt.

You can also format with gdisk which is the gpt version of fdisk. Once installed you should add gdisk and anytime you see instructions on running fdisk, run gdisk (but commands a somewhat different).

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---

### Post by YannBuntu on 2012-10-24
Hello

> **kathrync said:**
> The URL with the output  is here [http://paste.ubuntu.com/1287871/](http://paste.ubuntu.com/1287871/) if it is useful to anyone though.

Your GRUB was booting Ubuntu correctly, you didn't have to change anything on the Ubuntu disk !

Please run Boot-Repair --> Advanced options --> Untick "Reinstall GRUB" --> tick "Restore efi backups" --> Apply
Indicate the new URL that will appear.
Then reboot, and setup your BIOS (UEFI firmware) to boot the "Windows" entry, and tell us if it boots Windows or not. (if not, your Windows efi file is broken, and you'll have to [use a Windows disk to fix it]("https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader")).

---

### Post by kathrync on 2012-10-26
Ok, so I have re-partitioned sdb (the SSD with Ubuntu on) and reinstalled it, but still no joy with getting the dual boot to work.

I tried your suggestion as well, Yannbuntu.  This was the output from that: [http://paste.ubuntu.com/1308322/](http://paste.ubuntu.com/1308322/)  

At the moment I am booting Ubuntu ok but I can't boot Windows from the GRUB menu, or directly from sda.

Edited to add:  Windows boots ok when sdb is removed from the box...

Any more help appreciated (and thanks for all the help already!)

K

---

### Post by YannBuntu on 2012-10-26
> **kathrync said:**
> At the moment I am booting Ubuntu ok

for information your BIOS is correctly setup to boot the HDD in UEFI mode.

> **kathrync said:**
> but I can't boot Windows from the GRUB menu

The default GRUB entry for Windows is invalid for UEFI. You can mark yourself "Affected" by this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

> **kathrync said:**
> or directly from sda.

what do you mean? how do you try to "boot directly from sda" ?

---

### Post by kathrync on 2012-10-26
> **YannBuntu said:**
> 
what do you mean? how do you try to "boot directly from sda" ?

My Ubuntu EFI partion is sdb1.  Booting from here loads GRUB (which has a Windows entry but it doesn't work...I'll have a look at the link to the bug in a minute)

My Windows EFI partition is sda1.  Booting from here loads Windows when sdb is not in the box, but returns an error when sdb is present.

By "booting directly from sda", I mean asking the computer to boot from sda using the "press escape to enter setup" boot menu rather than going into sdb/GRUB.

Sorry if that wasn't clear...my knowledge of the terminology isn't great!

---

### Post by YannBuntu on 2012-10-26
ok.
The "press escape to enter setup" boot menu is indeed your UEFI firmware (~BIOS).

When entering the BIOS to boot Windows, is there something you change or select in your BIOS?

Please could you show pictures of your BIOS ?  (especially the "boot order" screen)

---

### Post by oldfred on 2012-10-26
Yann,
  	kathrync still has the old grub Windows entry (incorrect one) and you have the updates that you add to put in a correct Windows entry.  Does not grub menu just need the correct entries or is the correct entry different when it is to a different drive?

---

### Post by kathrync on 2012-10-27
Yann and oldfred:

Thanks for all the help guys, I wouldn't have known where to start without it!

This morning, I put sdb back in the box, and Windows still boots.  I don't know what changed overnight, but at least I know that both the EFI partitions are functional now.

So, if I set boot order to sda first, it goes straight to Windows
If I set boot order to sdb first it goes to GRUB, where I can get to Ubuntu but the Windows entry in GRUB doesn't work.

Yann, I haven't permanently changed anything in my UEFI firmware.  There is a setup menu I can enter where I can change the default boot order,  but I have left that alone (it is currently set to sdb first as I use Ubuntu more than Windows).  There is also something that they are calling a boot menu, which allows me to set something else as the priority as a one-time event.  I am currently using this to get to Windows when I want to.

> **oldfred said:**
> Yann,
  	kathrync still has the old grub Windows entry (incorrect one) and you have the updates that you add to put in a correct Windows entry.  Does not grub menu just need the correct entries or is the correct entry different when it is to a different drive?

oldfred:  I think you are right with the above.  It looks like the Windows entry in my Grub menu is incorrect and I think that's the only thing that's still non-functional.  From the bug link that yann sent me yesterday it looks like boot-repair is solving this issue for most people, but it doesn't seem to be working for me.  I suspect this is because I am running the two OSs off separate drives and not on partitions within the same drive which is what everyone else seems to be doing.

If someone could walk me through adding the correct entry manually (yeah, sorry, I'm being a noob again), we could see if that works??

K

---

### Post by larrys4227 on 2012-10-27
I'll quickly step in here for a sec ....

If you need to manually change something in grub, maybe "Grub Customizer"  will help.  Its in the software center and has a nice gui.

Stepping back out again ... :popcorn:

---

### Post by oldfred on 2012-10-27
Have not paid close enough to details of the efi chain load entires Boot-Repair adds. The one's that grub2 automatically add are a known bug in the os-prober as it finds the Windows boot partition and just adds a standard MBR type boot entry.

Some of the standard entries have just a search for efi partition which you now have two of which can be an issue.

I have this in my notes. The UUID has to be the UUID of the efi partition with the Windows efi files. And the set root =  entry has to be the drive & partition or hd0 is first drive and gpt1 is first partition or sda1. 

Use this to find your partition & UUID:
sudo blkid -c /dev/null -o list

```
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='[COLOR=Red](hd0,gpt1[/COLOR])'
  search --fs-uuid --no-floppy --set=root [COLOR=Red]4f84-ee2e[/COLOR]
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```Not sure if you copy Windows efi files to Ubuntu efi, if then a standard efi boot would work as Windows BCD is supposed to tell it what partition has Windows and to boot from.

---

### Post by kathrync on 2012-10-27
Ok...

I opened /etc/grub.d/40_custom as sudo and edited it to countain the following:

```
# Windows 7 UEFI entry

menuentry "Windows 7 UEFI" {
	insmod part_gpt
	insmod fat
	insmod search_fs_uuid
	insmod chain
	set root='(hd0, gpt1)'
	search --fs-uuid --no-floppy --set=root B039-55F4
	chainloader (${root}/EFI/Microsoft/Boot/bootmgfw.efi)
}

```

I know the Windows EFI partition is sda1, and I looked up the UUID using blkid as you suggested.

I then ran update-grub2 and looked at /boot/grub/grub.cfg to confirm that my entry was there.

Now when I reboot, I have a Windows 7 UEFI entry in the GRUB menu.  However, it returns the following error:

error: invalid filename `'.

I suspect I have typed something wrong in my entry, but I can't see what it is.  Any suggestions...it sometimes helps for other people to look at these things!

K

---

### Post by kathrync on 2012-10-27
Oh, this is the output from blkid just in case it's of any use. 

```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  vfat    SYSTEM   (not mounted)  B039-55F4
/dev/sda3  ntfs    OS       (not mounted)  52B678EBB678D149
/dev/sda4  ntfs    HP_RECOVERY (not mounted) 9488FFEC88FFCAAE
/dev/sdb1  vfat             /boot/efi      F140-BFF2
/dev/sdb2  swap             <swap>         2b97bf91-71d8-4d36-b277-1dcb1f973cbe
/dev/sdb3  ext4             /              ae769c2e-f494-4729-a025-a86b0454b88e
/dev/sdb4  ext4             /home          fc87c3eb-a83b-4906-923e-e5c37441ae80
```

---

### Post by oldfred on 2012-10-27
Sorry, but the original setting of hd0 may be wrong. With BIOS/grub the drive you boot is always hd0, so then the next drive is hd1. So change the hd0 to hd1. But the search should have overriden the set root, as it is a backup to the set root, as removable devices often get renumbered and the search by UUID should then still  have worked.

When Boot-Repair adds entries it was adding an entry for 3 different Windows efi files and two of the three entries seemed to always work. What are the efi Windows files in your sda1 efi? Is the path correct also.

/efi/Microsoft/Boot

---

### Post by kathrync on 2012-10-27
Hi,

I tried changing hd0 to hd1 based on your last message (assuming that if I am booting sdb, the machine will take sdb to be hd0 and sda to be hd1) but I'm still getting the same error.

I am pretty sure the path is correct...it is the same as was given last time I ran boot-repair:

```
Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info October 25th 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99-2.00) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img, but core.img can not be found at 
    this location.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/HP/SystemDiags/CryptRSA.efi 
                       /EFI/HP/SystemDiags/CryptRSA32.efi 
                       /EFI/HP/SystemDiags/SystemDiags.efi 
                       /EFI/HP/SystemDiags/SystemDiags32.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi
```

From something I read on a different thread, bootmgfw is one of the ones that tends to work, but I will try the others and see what happens...

K

---

### Post by kathrync on 2012-10-28
Hi again,

I have now tried all the paths listed above, and tried each with root set to hd0 and hd1.

I am getting the "error: invalid filename `'." error with every combination.

My grub.cfg file looks a little odd to me...but I don't really know what I am looking at so it might be normal.  Firstly, it seems to be calling sdb hd1, even though it is thr drive that is booting first.  Secondly, it seems to be loading Ubuntu from gpt3, not gpt1 which is the EFI partion.  Does that mean I am still booting Ubuntu in BIOS mode??  I have put the cfg file below...sorry it's so long but I don't know what information is useful and what isn't!

```
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
set root='(hd1,gpt3)'
search --no-floppy --fs-uuid --set=root ae769c2e-f494-4729-a025-a86b0454b88e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd1,gpt3)'
  search --no-floppy --fs-uuid --set=root ae769c2e-f494-4729-a025-a86b0454b88e
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
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd1,gpt3)'
	search --no-floppy --fs-uuid --set=root ae769c2e-f494-4729-a025-a86b0454b88e
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=ae769c2e-f494-4729-a025-a86b0454b88e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd1,gpt3)'
	search --no-floppy --fs-uuid --set=root ae769c2e-f494-4729-a025-a86b0454b88e
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=ae769c2e-f494-4729-a025-a86b0454b88e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd1,gpt3)'
	search --no-floppy --fs-uuid --set=root ae769c2e-f494-4729-a025-a86b0454b88e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd1,gpt3)'
	search --no-floppy --fs-uuid --set=root ae769c2e-f494-4729-a025-a86b0454b88e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_gpt
	insmod ntfs
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set=root 52B678EBB678D149
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# Windows 7 UEFI entry

menuentry "Windows 7 UEFI" {
	insmod part_gpt
	insmod fat
	insmod search_fs_uuid
	insmod chain
	set root='(hd0, gpt1)'
	search --fs-uuid --no-floppy --set=root B039-55F4
	chainloader (${root}/EFI/Microsoft/Boot/bootmgfw.efi)
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###



```

---

### Post by oldfred on 2012-10-28
The grub in the MBR does not have a core.img to continue booting so that is not working.
It may be better to think of the efi partition as the same as the MBR. Normally you do not see MBR and would not have to edit or deal with efi partition. The MBR was just a first part of the boot loader.

Ubuntu's (and Windows) have most of the boot files in other locations although it is a bit more mixed as the efi partition does have more room than old MBR, so more boot loader code is in efi partition.

The actual grub menu & Ubuntu boot files are still in /boot which is normally still in your / (root) partition or a separate /boot if you happened to have one.  So that the grub menu refers to the install partition is correct.

Both set root with a specific location and the search are to find the correct location of the files you want to boot. Search is supposed to override the set to hd1,1 type entries since drive locations can change with plug in drives now a days.

But something is not correct if it cannot find location.

I believe this user used exactly the same entry you are and it worked.
UEFI dual boot two drives see post #14 
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by kathrync on 2012-10-28
Dual boot is go!

Thanks to everyone who helped out, especially oldfred and Yann :o)

Turns out I had closed a bracket in the wrong place when I wrote my GRUB entry for Windows UEFI.  I didn't notice until I was comparing it against the code from that other thread.  Still, no-one else noticed when I posted it earlier so I only feel slightly stupid!

Thanks again all 

Kathryn (feeling slightly less ignorant now than she did a week ago!)

---

### Post by oldfred on 2012-10-28
Glad you resolved it. And good to know entry works if configured correctly.

I have gone cross-eyed looking for that type of error many times. Good catch. :)

---

### Post by YannBuntu on 2012-10-28
> **kathrync said:**
> Dual boot is go!

Good job!
For information: [http://ubuntuforums.org/showthread.php?p=12323223#post12323223](http://ubuntuforums.org/showthread.php?p=12323223#post12323223)
It should work better for you next time :)

---

