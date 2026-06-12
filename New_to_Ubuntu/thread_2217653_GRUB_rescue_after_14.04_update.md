---
title: "GRUB rescue after 14.04 update"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by Ronjet on 2014-04-18
Hello,

Today I've updated from 13.10 do 14.04 using software updater but after reboot I saw this message:

[COLOR=#333333]"error: symbol 'grub_term_highlight_color' not found.[/COLOR]
[COLOR=#333333]grub rescue>'
[/COLOR]
I found this site how to fix grub:

[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd-pendrive.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd-pendrive.html)

Now after reboot I got this message:

[COLOR=#000000]"GNU GRUB vesrion 2.02~beta2-9[/COLOR]

[COLOR=#000000]Minimal BASH-like line editing is supported. For the first word, TAB list possible command completions. Anywhere else TAB lists possible device or file completions.[/COLOR]

[COLOR=#000000]grub>"
[/COLOR]
Here's my terminal log from above mentioned instructions:

```
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]Disk /dev/sda: 500.1 GB, 500107862016 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Disk identifier: 0xf9a7b679[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/dev/sda1   *        2048     3074047     1536000    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/dev/sda2         3074048   845699071   421312512    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/dev/sda3       948099072   976771071    14336000    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/dev/sda4       845701118   948099071    51198977    5  Extended[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/dev/sda5       845701120   861323263     7811072   82  Linux swap / Solaris[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/dev/sda6       861325312   948099071    43386880   83  Linux[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]Partition table entries are not in disk order[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]Disk /dev/sdb: 4003 MB, 4003037184 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]255 heads, 63 sectors/track, 486 cylinders, total 7818432 sectors[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Disk identifier: 0x0005e838[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/dev/sdb1   *          63     7818431     3909184+   b  W95 FAT32[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo mount /dev/sd6 /mnt[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]mount: special device /dev/sd6 does not exist[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/boot.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]mount: mount point /mnt/boot. does not exist[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/boot[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$              sudo mount --bind /dev /mnt/dev[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo mount --bind /usr/ /mnt/usr[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo chroot /mnt[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]root@ubuntu:/# update-grub2[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/usr/sbin/grub-mkconfig: 250: /usr/sbin/grub-mkconfig: cannot create /boot/grub/grub.cfg.new: Directory nonexistent[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]root@ubuntu:/# update-grub[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/usr/sbin/grub-mkconfig: 250: /usr/sbin/grub-mkconfig: cannot create /boot/grub/grub.cfg.new: Directory nonexistent[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]root@ubuntu:/# grub-install /dev/sda[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Installing for i386-pc platform.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Installation finished. No error reported.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]root@ubuntu:/# sudo grub-install --recheck /dev/sda[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]sudo: unable to resolve host ubuntu[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Installing for i386-pc platform.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Installation finished. No error reported.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]root@ubuntu:/# exit[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo umount /mnt/dev[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo umount /mnt/proc[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo umount /mnt/sys[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo umount /mnt/boot[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo umount /mnt/usr[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo umount /mnt[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]umount: /mnt: device is busy.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        (In some cases useful info about processes that use[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]         the device is found by lsof(8) or fuser(1))[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$[/FONT][/COLOR]
```

How can I fix GRUB and run computer normally :(? Please help.

---

### Post by oldfred on 2014-04-18
Not seen that error, but did you change grub menu colors?
Similar to this?
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

And that says the entry is like this:
menu_color_highlight=text-color/bg-color

So where did you add your entry? That is probably why it is not correctly creating a new grub.cfg or it is not working. I had a typo in my 40_custom that worked with older versions of grub2 but then stopped working as it improved checking for errors.

---

### Post by Ronjet on 2014-04-18
> **oldfred said:**
> Not seen that error, but did you change grub menu colors?


No. I've used Boot Repair and now everything seems to be ok except one thing. Here's report:

[http://paste.ubuntu.com/7274494/](http://paste.ubuntu.com/7274494/)

Now I've got two Windows 8 entries in GRUB. Which should I remove safely? Sda1 or Sda2?

---

### Post by oldfred on 2014-04-18
Boot flag is on sda1, so I would keep that. Windows uses boot flag, grub does not.

Boot-Repair copies Windows boot files from its boot partition to main install as many users seem to not know sda1 is the Windows boot partition and just delete it. Then they have major issues. But then with the boot files also in sda2, grub will add another entry.

You also installed grub to sda3 which is a NTFS partition. That may cause major issues even though not a boot partition. Never install grub to a NTFS partition and extremely rarely to any partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by Ronjet on 2014-04-18
Ok, so to clarify. I need now for example go to this page: [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)   and follow this steps? Which is the easiest way to remove grub from NTFS partition?

---

### Post by oldfred on 2014-04-18
If backup is valid you want to restore the backup.

Otherwise you have to use testdisk to create its generic NTFS boot sector (BS) as with grub installed to the PBR, Windows will not even recognize the partition.
If you have to use testdisk to create a BS, it is more a XP type, and you should run chkdsk from your version of Windows which will update it. But with grub in the BS, you cannot even run chkdsk.

---

### Post by Ronjet on 2014-04-19
I'm a little confused, so sorry for my questions. What should I do now? I don't have backup of Ubuntu.
Do I need to run testdisk while I'm using Windows 8? 

Here's chkdsk results:

```
Microsoft Windows [Version 6.3.9600]
(c) 2013 Microsoft Corporation. Wszelkie prawa zastrze&#380;one.


C:\WINDOWS\system32>chkdsk
The type of the file system is NTFS.
Volume label is Windows8_OS.


WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.


Stage 1: Examining basic file system structure ...




  315392 file records processed.


File verification completed.




  4511 large file records processed.




  0 bad file records processed.


Stage 2: Examining file name linkage ...




  392334 index entries processed.


Index verification completed.




  0 unindexed files scanned.




  0 unindexed files recovered.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.




  38472 data files processed.
CHKDSK is verifying Usn Journal...




  36082168 USN bytes processed.


Usn Journal verification completed.


Windows has scanned the file system and found no problems.
No further action is required.


 421312511 KB total disk space.
 183637720 KB in 206470 files.
    118028 KB in 38473 indexes.
         0 KB in bad sectors.
    430771 KB in use by the system.
     65536 KB occupied by the log file.
 237125992 KB available on disk.


      4096 bytes in each allocation unit.
 105328127 total allocation units on disk.
  59281498 allocation units available on disk.


C:\WINDOWS\system32>
```

I have no idea how to fix thix problem :( Please help.

---

### Post by oldfred on 2014-04-19
Not the backup of Ubuntu but the backup of the PBR  partition boot record or BS boot sector.

Testdisk screen shows you grub in PBR and may say it is ok, but it is not, but you want to restore the backup BS if testdisk says it is ok. If not create new BS also on same screen in testdisk.

Please review post #4, either of those links gives you the entire process.

---

### Post by Ronjet on 2014-04-22
I've got question regarding these instructions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Which partition should I choose now? (After [COLOR=#000000]  Fifth   screen:  Select the Windows system partition  and choose "boot")
My screenshot: [/COLOR][IMG]http://i.imgur.com/1cl80fH.png[/IMG]

Is it a solution to my problem or only a small step and I should review/read other links :)?

Best regards,
Ron.

---

### Post by oldfred on 2014-04-22
Its not your boot partition and that is why Windows works, but all NTFS partitions need a NTFS boot sector. Or never have grub in the PBR of a NTFS partition.

BootInfo report shows grub installed to PBR or boot sector of  sda3 another NTFS partition, which testdisk is showing as your lenovo-recovery. So just run the commands on sda3.

>  [COLOR=#ff0000]sda3[/COLOR]: _____________________________

       File system:       [COLOR=#ff0000]ntfs[/COLOR]
    Boot sector type:  [COLOR=#ff0000]Grub2[/COLOR] (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 920361184 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for . No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        



If you look as sda1 or sda2 they show correct NTFS boot sectors in bootinfo report.

---

### Post by Ronjet on 2014-04-22
> **oldfred said:**
> Its not your boot partition and that is why Windows works, but all NTFS partitions need a NTFS boot sector. Or never have grub in the PBR of a NTFS partition.

BootInfo report shows grub installed to PBR or boot sector of  sda3 another NTFS partition, which testdisk is showing as your lenovo-recovery. So just run the commands on sda3.

If you look as sda1 or sda2 they show correct NTFS boot sectors in bootinfo report.

Ok, now I understand what's the problem :) Here's log from testdisk on Lenovo_Recovery NTFS:

```
TestDisk 6.14, Data Recovery Utility, July 2013Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 3 P HPFS - NTFS          59016 111 40 60801  47 46   28672000 [Lenovo_Recovery]


Boot sector
Status: OK


Backup boot sector
Status: OK


Sectors are identical.


A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
```

Sectors are identical? What should I do? There's no "Backup BS" option. It looks that Lenovo NTFS partition is ok (or I did something wrong).

Latest bootinfoscript log:

```
                  Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 920361184 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for . No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        


sda4: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda6: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 500.1 GB, 500107862016 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 60801, w sumie sektorów: 976773168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048     3,074,047     3,072,000   7 NTFS / exFAT / HPFS
/dev/sda2           3,074,048   845,699,071   842,625,024   7 NTFS / exFAT / HPFS
/dev/sda3         948,099,072   976,771,071    28,672,000   7 NTFS / exFAT / HPFS
/dev/sda4         845,701,118   948,099,071   102,397,954   5 Extended
/dev/sda5         845,701,120   861,323,263    15,622,144  82 Linux swap / Solaris
/dev/sda6         861,325,312   948,099,071    86,773,760  83 Linux




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        8E28FA0728F9EE59                       ntfs       SYSTEM_DRV
/dev/sda2        E68841048840D4A9                       ntfs       Windows8_OS
/dev/sda3        C038F84438F83ACC                       ntfs       Lenovo_Recovery
/dev/sda5        6c03aa34-1f9d-4b32-bfaf-615369fecaea   swap       
/dev/sda6        a3f26fd1-c445-4804-af68-06f3356424ea   ext4       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda6        /                        ext4       (rw,errors=remount-ro)




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
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a3f26fd1-c445-4804-af68-06f3356424ea
else
  search --no-floppy --fs-uuid --set=root a3f26fd1-c445-4804-af68-06f3356424ea
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


### BEGIN /etc/grub.d/10_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-8E28FA0728F9EE59' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8E28FA0728F9EE59
	else
	  search --no-floppy --fs-uuid --set=root 8E28FA0728F9EE59
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Windows 8 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-E68841048840D4A9' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  E68841048840D4A9
	else
	  search --no-floppy --fs-uuid --set=root E68841048840D4A9
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/10_os-prober ###


### BEGIN /etc/grub.d/20_linux ###
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a3f26fd1-c445-4804-af68-06f3356424ea' {
recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a3f26fd1-c445-4804-af68-06f3356424ea
	else
	  search --no-floppy --fs-uuid --set=root a3f26fd1-c445-4804-af68-06f3356424ea
	fi
	linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=a3f26fd1-c445-4804-af68-06f3356424ea ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a3f26fd1-c445-4804-af68-06f3356424ea' {
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-a3f26fd1-c445-4804-af68-06f3356424ea' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a3f26fd1-c445-4804-af68-06f3356424ea
		else
		  search --no-floppy --fs-uuid --set=root a3f26fd1-c445-4804-af68-06f3356424ea
		fi
		echo	'Loading Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=a3f26fd1-c445-4804-af68-06f3356424ea ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-a3f26fd1-c445-4804-af68-06f3356424ea' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a3f26fd1-c445-4804-af68-06f3356424ea
		else
		  search --no-floppy --fs-uuid --set=root a3f26fd1-c445-4804-af68-06f3356424ea
		fi
		echo	'Loading Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=a3f26fd1-c445-4804-af68-06f3356424ea ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-19-generic-advanced-a3f26fd1-c445-4804-af68-06f3356424ea' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a3f26fd1-c445-4804-af68-06f3356424ea
		else
		  search --no-floppy --fs-uuid --set=root a3f26fd1-c445-4804-af68-06f3356424ea
		fi
		echo	'Loading Linux 3.11.0-19-generic ...'
		linux	/boot/vmlinuz-3.11.0-19-generic root=UUID=a3f26fd1-c445-4804-af68-06f3356424ea ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-19-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-19-generic-recovery-a3f26fd1-c445-4804-af68-06f3356424ea' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a3f26fd1-c445-4804-af68-06f3356424ea
		else
		  search --no-floppy --fs-uuid --set=root a3f26fd1-c445-4804-af68-06f3356424ea
		fi
		echo	'Loading Linux 3.11.0-19-generic ...'
		linux	/boot/vmlinuz-3.11.0-19-generic root=UUID=a3f26fd1-c445-4804-af68-06f3356424ea ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-19-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-31-generic-advanced-a3f26fd1-c445-4804-af68-06f3356424ea' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a3f26fd1-c445-4804-af68-06f3356424ea
		else
		  search --no-floppy --fs-uuid --set=root a3f26fd1-c445-4804-af68-06f3356424ea
		fi
		echo	'Loading Linux 3.8.0-31-generic ...'
		linux	/boot/vmlinuz-3.8.0-31-generic root=UUID=a3f26fd1-c445-4804-af68-06f3356424ea ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-31-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-31-generic-recovery-a3f26fd1-c445-4804-af68-06f3356424ea' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a3f26fd1-c445-4804-af68-06f3356424ea
		else
		  search --no-floppy --fs-uuid --set=root a3f26fd1-c445-4804-af68-06f3356424ea
		fi
		echo	'Loading Linux 3.8.0-31-generic ...'
		linux	/boot/vmlinuz-3.8.0-31-generic root=UUID=a3f26fd1-c445-4804-af68-06f3356424ea ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-31-generic
	}
}


### END /etc/grub.d/20_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a3f26fd1-c445-4804-af68-06f3356424ea
	else
	  search --no-floppy --fs-uuid --set=root a3f26fd1-c445-4804-af68-06f3356424ea
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  a3f26fd1-c445-4804-af68-06f3356424ea
	else
	  search --no-floppy --fs-uuid --set=root a3f26fd1-c445-4804-af68-06f3356424ea
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


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


=============================== sda6/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=a3f26fd1-c445-4804-af68-06f3356424ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6c03aa34-1f9d-4b32-bfaf-615369fecaea none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sda6: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda4


00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 ee 00 00 fe  |...........`....|
000001d0  ff ff 05 fe ff ff b1 66  ee 00 51 11 2c 05 00 00  |.......f..Q.,...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-J2jz6m9k/Tmp_Log: Nie ma takiego pliku ani katalogu
```

---

### Post by oldfred on 2014-04-22
I would expect them to both be valid as grub in PBR is a valid choice, but they should not be identical. Did you install grub to PBR of sda3 more than once?

You can from testdisk use the command to create a new BS. Rebuild BS.
I believe it creates a standard XP type and then you may need to run chkdsk from your install of Windows. Often chkdsk will fix minor issues of a PBR, with with grub in PBR chkdsk will not even run as it does not even think it is a NTFS partition. But with the XP type PBR then you can run chkdsk.

The dump I show where they are different was because I ran a Windows 7 chkdsk on my XP. It converted PBR to Windows 7 type not XP and I wanted to see if they were different and they are.

---

### Post by Ronjet on 2014-04-22
> **oldfred said:**
> I would expect them to both be valid as grub in PBR is a valid choice, but they should not be identical. Did you install grub to PBR of sda3 more than once?

I have no idea. As I said I'm beginner user, so I only installed Ubuntu next to Windows 8 (it was 12.10, then upgraded to 13.10 and now to 14.10). During installation there were several messages regarding GRUB (to replace or save some grub files). Probably GRUB was installed automat


> **oldfred said:**
> You can from testdisk use the command to create a new BS. Rebuild BS.

Ok, but is it safe? :) I don't want to damage/lost my RECOVERY partition ;)
BTW thank you for your patience in answering my questions.

---

### Post by oldfred on 2014-04-22
As long as you have grub in NTFS PBR of your recovery partition it will be unusable.
So you just about have no choice.
Most have not had any issues.

But did you not make a recovery set of DVDs soon after purchase of system. Many do that and then just delete recovery partition as it is not worth much. It is just the vendor's replacement for actually providing the DVD's themselves. 

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by xterminalx on 2014-04-25
I did the upgrade last night. Same error. Normally I wouldn't even post, I'd just follow the instructions and go on with my life, but I was thinking about this on the way to work this morning...

"error: symbol 'grub_term_highlight_color' not found."

Now, I've been a steady Ubuntu enduser for a while now (9.something was my first install, I think), but I certainly wouldn't claim any knowledge of the internals. So this may be the dumbest question you have heard all day. BUT... looking at the error, and reading what little I have been able to find on its causes, this sounds like an inconvenient annoyance rather than a showstopper that should prevent a machine from booting altogether. Is this (in good old MS Windows fashion) a "tip of the iceberg" error that is actually pointing to something much more serious underneath the hood that the average joe would have no idea about? Is highlight color really ridiculously important? Is this a result of rampant perfectionism? Inquiring minds wanna know! (or at least wonder about it idly whilst 90% asleep and driving to work before the sun rises...)

---

### Post by oldfred on 2014-04-25
There is a bug. only 67 reports so far. Seems to be more upgrades related.
Error report may not be what issue really is. 

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)

Most find one of these work to fix it.
And a purge & reinstall of grub with Boot-Repair.

OR use Supergrub to boot or chroot into install and run this
sudo dpkg-reconfigure grub-pc.

---

