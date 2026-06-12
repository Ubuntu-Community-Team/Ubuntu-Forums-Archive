---
title: "Dual Boot Xubuntu 11.10 and Windows XP with SP3"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by ahmedmahdy on 2011-12-23
I've executed 2 scenarios to dual boot Xubuntu 11.10 and Windows XP SP3, but both scenarios ended by re-installing either Xubuntu or XP.

Scenario #1:

- System configuration:

1- Windows XP with SP3 installed on C:\ partition.
2- Xubuntu 11.10 installed on hd(0,2) with a separate SWAP partition and GRUB 2 installed over partition C:\

- Action

1- Xubuntu boots without any problems.
2- When choosing Windows XP Professional from the GRUB 2 boot menu, screen flicks for a moment then it loops back to GRUB 2 boot menu.

- Methods of resolve

I used Boot-Repair tool to repair the boot, but after choosing Windows XP from boot menu, I get a non-unicode sequence of characters in a single line and nothing occurs after that. 

Scenario #2:

- System configuration:

1- Xubuntu 11.10 installed on hd(0,2) with a separate SWAP partition and GRUB 2 installed on MBR.
2- Windows XP with SP3 installed on C:\ partition.

- Action

1- Windows XP bootloader overwrote GRUB 2.
2- Windows XP starts normally.

- Methods of resolve

I've installed EasyBCD 2.1.2 and I'm currently stuck with several options I'm afraid to go along with; and they are:

1- NeoGrub with configuration file "menu.lst" got it from: [http://neosmart.net/wiki/display/EBCD/NeoGrub]("http://neosmart.net/wiki/display/EBCD/NeoGrub")


```
# NeoSmart NeoGrub Bootloader Configuration File
#
# This NeoGrub menu.lst file should be located at \NST\menu.lst of the boot drive.
# Please see the EasyBCD Documentation for information on how to create/modify entries

#This is a comment. Comments are prefixed with a '#'

default 0		#Pick the task to be run if the user doesn't pick one within the time limit.
timeout 10		#Give the user 10 seconds to choose a task.

#We use the "title" keyword to indicate a new entry in the menu.

title 		Windows XP	#This is our first entry - it's number 0
find --set-root	/NTLDR  	#Search for NTLDR on all partitions. Once found, use that partition as root.
makeactive  			#Make this the active partition
chainloader /NTLDR		#Run NTLDR, the Windows XP bootloader
#If we're using a menu, we don't need to use the `boot` command - it's automatically implied.

#This is our second entry
title		Ubuntu Gutsy Gibbon    
root		(hd1,2)   	#Load Ubuntu from the 2nd harddrive's 3rd partition.
#Next Line: Translate (hd1,2) to Linux notation and set that as the root partition
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdbc
initrd		/boot/initrd.img-2.6.22-14-generic
#End Ubuntu entry

#That's it!

```

I can edit everything except the following 2 lines:

> kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdbc
initrd		/boot/initrd.img-2.6.22-14-generic

Because I'm not sure what parameters should be used exactly for Xubuntu 11.10 and note that NeoGRUB uses the core of GRUB and GRUB 2 which I'm not sure whether it will work or not.

2- Instead of using NeoGRUB, I've added entries of boot menu for Windows XP as for Windows with automated correct drive detection, however for Linux/BSD I got the following options:

> GRUB (Legacy)  >> Option to choose partition and to Use EasyBCD's copy of GRUB
GRUB 2         >> Automatically configured, no options
LILO/eLILO     >> Option to choose partition
FreeBSD/PC-BSD >> Option to choose partition
Wubi           >> Automatically configured, no options
SysLinux       >> Option to choose partition

I'm not sure which one would work correctly with Xubuntu and Windows XP.

So, I'd be glad if you provided me with a proper answer! :D

Thanks!

---

### Post by sikander3786 on 2011-12-23
Welcome to the forums. :)

The perfect scenario here would be to remove EasyBCD and simply re-install Grub. We would give you exact commands for that but you need to figure out the EasyBCD stuff on your own. I guess it would be easy to remove EasyBCD by going to the Add/Remove Programs in XP's control panel.

Once you've done that, test the Windows XP boot, hopefully it won't be affected. Even if it is, let us know as that can be easily repaired.

So in case XP boots just fine, you need to boot an Ubuntu/Xubuntu Live CD/USB and run and post the output of Bootinfoscript as per instructions here:

[http://www.bootinfoscript.sourceforge.net](http://www.bootinfoscript.sourceforge.net)

Please use [code] tags while posting the outputs by clicking the # icon in post menu and pasting your text in between the [code] tags.

---

### Post by ahmedmahdy on 2011-12-23
Thank you for the quick reply, I'm on my way to do this, if I didn't reply within an hour, so, I've lost boot :D

---

### Post by sikander3786 on 2011-12-23
> **ahmedmahdy said:**
> Thank you for the quick reply, I'm on my way to do this, if I didn't reply within an hour, so, I've lost boot :D
In that case, boot an Ubuntu Live CD/USB and stay connected to the forums at least. ;)

Good Luck!

---

### Post by ahmedmahdy on 2011-12-23
Here we go:

```
                        #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Liberation Serif'; font-variant: normal; text-indent: 0in; widows: 2; font-style: normal; font-weight: normal; text-decoration: none; color: rgb(0, 0, 0); text-align: left; font-size: 12pt; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Liberation Serif'; font-size: 12pt; text-align: left; }         [LEFT]                  Boot Info Script 0.60    from 17 May 2011[/LEFT]
            [LEFT]============================= Boot Info Summary: ===============================[/LEFT]
        [LEFT] => Windows is installed in the MBR of /dev/sda.[/LEFT]
    [LEFT] => Windows is installed in the MBR of /dev/sdb.[/LEFT]
    [LEFT] => Windows is installed in the MBR of /dev/sdc.[/LEFT]
        [LEFT]sda1: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:   No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  Windows XP[/LEFT]
    [LEFT]    Boot files:        /boot.ini /ntldr /NTDETECT.COM[/LEFT]
        [LEFT]sda2: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       Extended Partition[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
        [LEFT]sda5: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ext4[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
    [LEFT]    Operating System:  Ubuntu 11.10[/LEFT]
    [LEFT]    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/LEFT]
        [LEFT]sda6: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       swap[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
        [LEFT]sda7: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:   According to the info in the boot sector, sda7 starts [/LEFT]
    [LEFT]                       at sector 70. But according to the info from fdisk, [/LEFT]
    [LEFT]                       sda7 starts at sector 94381945.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files:        [/LEFT]
        [LEFT]sda8: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:   According to the info in the boot sector, sda8 starts [/LEFT]
    [LEFT]                       at sector 63.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files:        [/LEFT]
        [LEFT]sda3: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:   According to the info in the boot sector, sda3 starts [/LEFT]
    [LEFT]                       at sector 63. But according to the info from fdisk, [/LEFT]
    [LEFT]                       sda3 starts at sector 62926668.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files:        [/LEFT]
        [LEFT]sdb1: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:   No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files:        [/LEFT]
        [LEFT]sdc1: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows Vista/7[/LEFT]
    [LEFT]    Boot sector info:   No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files:        [/LEFT]
        [LEFT]============================ Drive/Partition Info: =============================[/LEFT]
        [LEFT]Drive: sda _____________________________________________________________________[/LEFT]
        [LEFT]Disk /dev/sda: 80.0 GB, 80000000000 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
        [LEFT]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/LEFT]
        [LEFT]/dev/sda1    *             63    41,945,714    41,945,652   7 NTFS / exFAT / HPFS[/LEFT]
    [LEFT]/dev/sda2          41,947,134   156,248,189   114,301,056   f W95 Extended (LBA)[/LEFT]
    [LEFT]Extended partition linking to another extended partition.[/LEFT]
    [LEFT]/dev/sda5          41,947,136    61,476,863    19,529,728  83 Linux[/LEFT]
    [LEFT]/dev/sda6          61,478,912    62,924,799     1,445,888  82 Linux swap / Solaris[/LEFT]
    [LEFT]/dev/sda7          94,381,945   125,837,144    31,455,200   7 NTFS / exFAT / HPFS[/LEFT]
    [LEFT]/dev/sda8         125,837,208   156,248,189    30,410,982   7 NTFS / exFAT / HPFS[/LEFT]
    [LEFT]/dev/sda3          62,926,668    94,381,874    31,455,207   7 NTFS / exFAT / HPFS[/LEFT]
        [LEFT]/dev/sda2 overlaps with /dev/sda3[/LEFT]
        [LEFT]Drive: sdb _____________________________________________________________________[/LEFT]
        [LEFT]Disk /dev/sdb: 499.4 GB, 499405291520 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 60715 cylinders, total 975400960 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
        [LEFT]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/LEFT]
        [LEFT]/dev/sdb1               2,048   975,400,959   975,398,912   7 NTFS / exFAT / HPFS[/LEFT]
            [LEFT]Drive: sdc _____________________________________________________________________[/LEFT]
        [LEFT]Disk /dev/sdc: 4051 MB, 4051697664 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 492 cylinders, total 7913472 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
        [LEFT]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/LEFT]
        [LEFT]/dev/sdc1    *             63     7,913,471     7,913,409   7 NTFS / exFAT / HPFS[/LEFT]
            [LEFT]"blkid" output: ________________________________________________________________[/LEFT]
        [LEFT]Device           UUID                                   TYPE       LABEL[/LEFT]
        [LEFT]/dev/loop0                                              squashfs   [/LEFT]
    [LEFT]/dev/sda1        ACACE865ACE82B90                       ntfs       WINDOWS[/LEFT]
    [LEFT]/dev/sda3        086C33076C32EED6                       ntfs       HD4[/LEFT]
    [LEFT]/dev/sda5        a9950f7a-15a2-4e08-9fb2-590ea49d2b79   ext4       [/LEFT]
    [LEFT]/dev/sda6        8a95da6a-7b4c-41fc-ba86-826cb7a1d4c4   swap       [/LEFT]
    [LEFT]/dev/sda7        FEEC1A12EC19C5B5                       ntfs       HD2[/LEFT]
    [LEFT]/dev/sda8        6E8022E38022B18F                       ntfs       HD3[/LEFT]
    [LEFT]/dev/sdb1        325220A852207331                       ntfs       My Passport[/LEFT]
    [LEFT]/dev/sdc1        A890399990396F46                       ntfs       [/LEFT]
    [LEFT]/dev/zram0       7b743868-9985-40db-9036-759753233288   swap       [/LEFT]
        [LEFT]================================ Mount points: =================================[/LEFT]
        [LEFT]Device           Mount_Point              Type       Options[/LEFT]
        [LEFT]/dev/loop0       /rofs                    squashfs   (ro,noatime)[/LEFT]
    [LEFT]/dev/sr0         /cdrom                   iso9660    (ro,noatime)[/LEFT]
            [LEFT]================================ sda1/boot.ini: ================================[/LEFT]
        --------------------------------------------------------------------------------
    [LEFT][boot loader][/LEFT]
    [LEFT]timeout=30[/LEFT]
    [LEFT]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS[/LEFT]
    [LEFT][operating systems][/LEFT]
    [LEFT]multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn[/LEFT]
    --------------------------------------------------------------------------------
        [LEFT]=========================== sda5/boot/grub/grub.cfg: ===========================[/LEFT]
        --------------------------------------------------------------------------------
    #
    [LEFT]# DO NOT EDIT THIS FILE[/LEFT]
    #
    [LEFT]# It is automatically generated by grub-mkconfig using templates[/LEFT]
    [LEFT]# from /etc/grub.d and settings from /etc/default/grub[/LEFT]
    #
        [LEFT]### BEGIN /etc/grub.d/00_header ###[/LEFT]
    [LEFT]if [ -s $prefix/grubenv ]; then[/LEFT]
    [LEFT]  set have_grubenv=true[/LEFT]
    [LEFT]  load_env[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]set default="0"[/LEFT]
    [LEFT]if [ "${prev_saved_entry}" ]; then[/LEFT]
    [LEFT]  set saved_entry="${prev_saved_entry}"[/LEFT]
    [LEFT]  save_env saved_entry[/LEFT]
    [LEFT]  set prev_saved_entry=[/LEFT]
    [LEFT]  save_env prev_saved_entry[/LEFT]
    [LEFT]  set boot_once=true[/LEFT]
    [LEFT]fi[/LEFT]
        [LEFT]function savedefault {[/LEFT]
    [LEFT]  if [ -z "${boot_once}" ]; then[/LEFT]
    [LEFT]    saved_entry="${chosen}"[/LEFT]
    [LEFT]    save_env saved_entry[/LEFT]
    [LEFT]  fi[/LEFT]
    }
        [LEFT]function recordfail {[/LEFT]
    [LEFT]  set recordfail=1[/LEFT]
    [LEFT]  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi[/LEFT]
    }
        [LEFT]function load_video {[/LEFT]
    [LEFT]  insmod vbe[/LEFT]
    [LEFT]  insmod vga[/LEFT]
    [LEFT]  insmod video_bochs[/LEFT]
    [LEFT]  insmod video_cirrus[/LEFT]
    }
        [LEFT]insmod part_msdos[/LEFT]
    [LEFT]insmod ext2[/LEFT]
    [LEFT]set root='(hd0,msdos8)'[/LEFT]
    [LEFT]search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]if loadfont /usr/share/grub/unicode.pf2 ; then[/LEFT]
    [LEFT]  set gfxmode=auto[/LEFT]
    [LEFT]  load_video[/LEFT]
    [LEFT]  insmod gfxterm[/LEFT]
    [LEFT]  insmod part_msdos[/LEFT]
    [LEFT]  insmod ext2[/LEFT]
    [LEFT]  set root='(hd0,msdos8)'[/LEFT]
    [LEFT]  search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]  set locale_dir=($root)/boot/grub/locale[/LEFT]
    [LEFT]  set lang=en_US[/LEFT]
    [LEFT]  insmod gettext[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]terminal_output gfxterm[/LEFT]
    [LEFT]if [ "${recordfail}" = 1 ]; then[/LEFT]
    [LEFT]  set timeout=-1[/LEFT]
    [LEFT]else[/LEFT]
    [LEFT]  set timeout=10[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/00_header ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/05_debian_theme ###[/LEFT]
    [LEFT]set menu_color_normal=white/black[/LEFT]
    [LEFT]set menu_color_highlight=black/light-gray[/LEFT]
    [LEFT]### END /etc/grub.d/05_debian_theme ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/10_linux ###[/LEFT]
    [LEFT]if [ ${recordfail} != 1 ]; then[/LEFT]
    [LEFT]  if [ -e ${prefix}/gfxblacklist.txt ]; then[/LEFT]
    [LEFT]    if hwmatch ${prefix}/gfxblacklist.txt 3; then[/LEFT]
    [LEFT]      if [ ${match} = 0 ]; then[/LEFT]
    [LEFT]        set linux_gfx_mode=keep[/LEFT]
    [LEFT]      else[/LEFT]
    [LEFT]        set linux_gfx_mode=text[/LEFT]
    [LEFT]      fi[/LEFT]
    [LEFT]    else[/LEFT]
    [LEFT]      set linux_gfx_mode=text[/LEFT]
    [LEFT]    fi[/LEFT]
    [LEFT]  else[/LEFT]
    [LEFT]    set linux_gfx_mode=keep[/LEFT]
    [LEFT]  fi[/LEFT]
    [LEFT]else[/LEFT]
    [LEFT]  set linux_gfx_mode=text[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]export linux_gfx_mode[/LEFT]
    [LEFT]if [ "$linux_gfx_mode" != "text" ]; then load_video; fi[/LEFT]
    [LEFT]menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]    recordfail[/LEFT]
    [LEFT]    set gfxpayload=$linux_gfx_mode[/LEFT]
    [LEFT]    insmod gzio[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root='(hd0,msdos8)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a9950f7a-15a2-4e08-9fb2-590ea49d2b79 ro   quiet splash vt.handoff=7[/LEFT]
    [LEFT]    initrd    /boot/initrd.img-3.0.0-12-generic[/LEFT]
    }
    [LEFT]menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]    recordfail[/LEFT]
    [LEFT]    insmod gzio[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root='(hd0,msdos8)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]    echo    'Loading Linux 3.0.0-12-generic ...'[/LEFT]
    [LEFT]    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a9950f7a-15a2-4e08-9fb2-590ea49d2b79 ro recovery nomodeset [/LEFT]
    [LEFT]    echo    'Loading initial ramdisk ...'[/LEFT]
    [LEFT]    initrd    /boot/initrd.img-3.0.0-12-generic[/LEFT]
    }
    [LEFT]### END /etc/grub.d/10_linux ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/20_linux_xen ###[/LEFT]
    [LEFT]### END /etc/grub.d/20_linux_xen ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/20_memtest86+ ###[/LEFT]
    [LEFT]menuentry "Memory test (memtest86+)" {[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root='(hd0,msdos8)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]    linux16    /boot/memtest86+.bin[/LEFT]
    }
    [LEFT]menuentry "Memory test (memtest86+, serial console 115200)" {[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root='(hd0,msdos8)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]    linux16    /boot/memtest86+.bin console=ttyS0,115200n8[/LEFT]
    }
    [LEFT]### END /etc/grub.d/20_memtest86+ ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/30_os-prober ###[/LEFT]
    [LEFT]menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ntfs[/LEFT]
    [LEFT]    set root='(hd0,msdos1)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set=root 267C91B77C91826B[/LEFT]
    [LEFT]    drivemap -s (hd0) ${root}[/LEFT]
    [LEFT]    chainloader +1[/LEFT]
    }
    [LEFT]### END /etc/grub.d/30_os-prober ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/40_custom ###[/LEFT]
    [LEFT]# This file provides an easy way to add custom menu entries.  Simply type the[/LEFT]
    [LEFT]# menu entries you want to add after this comment.  Be careful not to change[/LEFT]
    [LEFT]# the 'exec tail' line above.[/LEFT]
    [LEFT]### END /etc/grub.d/40_custom ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/41_custom ###[/LEFT]
    [LEFT]if [ -f  $prefix/custom.cfg ]; then[/LEFT]
    [LEFT]  source $prefix/custom.cfg;[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/41_custom ###[/LEFT]
    --------------------------------------------------------------------------------
        [LEFT]=============================== sda5/etc/fstab: ================================[/LEFT]
        --------------------------------------------------------------------------------
    [LEFT]# /etc/fstab: static file system information.[/LEFT]
    #
    [LEFT]# Use 'blkid' to print the universally unique identifier for a[/LEFT]
    [LEFT]# device; this may be used with UUID= as a more robust way to name devices[/LEFT]
    [LEFT]# that works even if disks are added and removed. See fstab(5).[/LEFT]
    #
    [LEFT]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/LEFT]
    [LEFT]proc            /proc           proc    nodev,noexec,nosuid 0       0[/LEFT]
    [LEFT]# / was on /dev/sda8 during installation[/LEFT]
    [LEFT]UUID=a9950f7a-15a2-4e08-9fb2-590ea49d2b79 /               ext4    errors=remount-ro 0       1[/LEFT]
    [LEFT]# swap was on /dev/sda9 during installation[/LEFT]
    [LEFT]UUID=8a95da6a-7b4c-41fc-ba86-826cb7a1d4c4 none            swap    sw              0       0[/LEFT]
    [LEFT]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/LEFT]
    --------------------------------------------------------------------------------
        [LEFT]=================== sda5: Location of files loaded by Grub: ====================[/LEFT]
        [LEFT]           GiB - GB             File                                 Fragment(s)[/LEFT]
        [LEFT]               =                boot/grub/core.img                             1[/LEFT]
    [LEFT]               =                boot/grub/grub.cfg                             1[/LEFT]
    [LEFT]               =                boot/initrd.img-3.0.0-12-generic               1[/LEFT]
    [LEFT]               =                boot/vmlinuz-3.0.0-12-generic                  1[/LEFT]
    [LEFT]               =                initrd.img                                     1[/LEFT]
    [LEFT]               =                vmlinuz                                        1[/LEFT]
        [LEFT]=============================== StdErr Messages: ===============================[/LEFT]
        [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
    [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
    [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
    [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
    [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
    [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
           
  
```

Please ignore "My Passport" partition, it's my external hard drive, if you would me populate another results without it, I'll paste it in the next reply post

---

### Post by ahmedmahdy on 2011-12-23
Full results for local hard disk without external hard disk:

Note: I got this notification in terminal during execution of the script:

> "gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.


```
                        #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Liberation Serif'; font-variant: normal; text-indent: 0in; widows: 2; font-style: normal; font-weight: normal; text-decoration: none; color: rgb(0, 0, 0); text-align: left; font-size: 12pt; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Liberation Serif'; font-size: 12pt; text-align: left; }         [LEFT]                  Boot Info Script 0.60    from 17 May 2011[/LEFT]
            [LEFT]============================= Boot Info Summary: ===============================[/LEFT]
        [LEFT] => Windows is installed in the MBR of /dev/sda.[/LEFT]
    [LEFT] => Windows is installed in the MBR of /dev/sdc.[/LEFT]
        [LEFT]sda1: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:   No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  Windows XP[/LEFT]
    [LEFT]    Boot files:        /boot.ini /ntldr /NTDETECT.COM[/LEFT]
        [LEFT]sda2: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       Extended Partition[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
        [LEFT]sda5: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ext4[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
    [LEFT]    Operating System:  Ubuntu 11.10[/LEFT]
    [LEFT]    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/LEFT]
        [LEFT]sda6: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       swap[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
        [LEFT]sda7: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:   According to the info in the boot sector, sda7 starts [/LEFT]
    [LEFT]                       at sector 70. But according to the info from fdisk, [/LEFT]
    [LEFT]                       sda7 starts at sector 94381945.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files:        [/LEFT]
        [LEFT]sda8: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:   According to the info in the boot sector, sda8 starts [/LEFT]
    [LEFT]                       at sector 63.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files:        [/LEFT]
        [LEFT]sda3: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:   According to the info in the boot sector, sda3 starts [/LEFT]
    [LEFT]                       at sector 63. But according to the info from fdisk, [/LEFT]
    [LEFT]                       sda3 starts at sector 62926668.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files:        [/LEFT]
        [LEFT]sdc1: __________________________________________________________________________[/LEFT]
        [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows Vista/7[/LEFT]
    [LEFT]    Boot sector info:   No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files:        [/LEFT]
        [LEFT]============================ Drive/Partition Info: =============================[/LEFT]
        [LEFT]Drive: sda _____________________________________________________________________[/LEFT]
        [LEFT]Disk /dev/sda: 80.0 GB, 80000000000 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
        [LEFT]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/LEFT]
        [LEFT]/dev/sda1    *             63    41,945,714    41,945,652   7 NTFS / exFAT / HPFS[/LEFT]
    [LEFT]/dev/sda2          41,947,134   156,248,189   114,301,056   f W95 Extended (LBA)[/LEFT]
    [LEFT]Extended partition linking to another extended partition.[/LEFT]
    [LEFT]/dev/sda5          41,947,136    61,476,863    19,529,728  83 Linux[/LEFT]
    [LEFT]/dev/sda6          61,478,912    62,924,799     1,445,888  82 Linux swap / Solaris[/LEFT]
    [LEFT]/dev/sda7          94,381,945   125,837,144    31,455,200   7 NTFS / exFAT / HPFS[/LEFT]
    [LEFT]/dev/sda8         125,837,208   156,248,189    30,410,982   7 NTFS / exFAT / HPFS[/LEFT]
    [LEFT]/dev/sda3          62,926,668    94,381,874    31,455,207   7 NTFS / exFAT / HPFS[/LEFT]
        [LEFT]/dev/sda2 overlaps with /dev/sda3[/LEFT]
        [LEFT]Drive: sdc _____________________________________________________________________[/LEFT]
        [LEFT]Disk /dev/sdc: 4051 MB, 4051697664 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 492 cylinders, total 7913472 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
        [LEFT]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/LEFT]
        [LEFT]/dev/sdc1    *             63     7,913,471     7,913,409   7 NTFS / exFAT / HPFS[/LEFT]
            [LEFT]"blkid" output: ________________________________________________________________[/LEFT]
        [LEFT]Device           UUID                                   TYPE       LABEL[/LEFT]
        [LEFT]/dev/loop0                                              squashfs   [/LEFT]
    [LEFT]/dev/sda1        ACACE865ACE82B90                       ntfs       WINDOWS[/LEFT]
    [LEFT]/dev/sda3        086C33076C32EED6                       ntfs       HD4[/LEFT]
    [LEFT]/dev/sda5        a9950f7a-15a2-4e08-9fb2-590ea49d2b79   ext4       [/LEFT]
    [LEFT]/dev/sda6        8a95da6a-7b4c-41fc-ba86-826cb7a1d4c4   swap       [/LEFT]
    [LEFT]/dev/sda7        FEEC1A12EC19C5B5                       ntfs       HD2[/LEFT]
    [LEFT]/dev/sda8        6E8022E38022B18F                       ntfs       HD3[/LEFT]
    [LEFT]/dev/sdc1        A890399990396F46                       ntfs       [/LEFT]
    [LEFT]/dev/zram0       7b743868-9985-40db-9036-759753233288   swap       [/LEFT]
        [LEFT]================================ Mount points: =================================[/LEFT]
        [LEFT]Device           Mount_Point              Type       Options[/LEFT]
        [LEFT]/dev/loop0       /rofs                    squashfs   (ro,noatime)[/LEFT]
    [LEFT]/dev/sr0         /cdrom                   iso9660    (ro,noatime)[/LEFT]
            [LEFT]================================ sda1/boot.ini: ================================[/LEFT]
        --------------------------------------------------------------------------------
    [LEFT][boot loader][/LEFT]
    [LEFT]timeout=30[/LEFT]
    [LEFT]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS[/LEFT]
    [LEFT][operating systems][/LEFT]
    [LEFT]multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn[/LEFT]
    --------------------------------------------------------------------------------
        [LEFT]=========================== sda5/boot/grub/grub.cfg: ===========================[/LEFT]
        --------------------------------------------------------------------------------
    #
    [LEFT]# DO NOT EDIT THIS FILE[/LEFT]
    #
    [LEFT]# It is automatically generated by grub-mkconfig using templates[/LEFT]
    [LEFT]# from /etc/grub.d and settings from /etc/default/grub[/LEFT]
    #
        [LEFT]### BEGIN /etc/grub.d/00_header ###[/LEFT]
    [LEFT]if [ -s $prefix/grubenv ]; then[/LEFT]
    [LEFT]  set have_grubenv=true[/LEFT]
    [LEFT]  load_env[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]set default="0"[/LEFT]
    [LEFT]if [ "${prev_saved_entry}" ]; then[/LEFT]
    [LEFT]  set saved_entry="${prev_saved_entry}"[/LEFT]
    [LEFT]  save_env saved_entry[/LEFT]
    [LEFT]  set prev_saved_entry=[/LEFT]
    [LEFT]  save_env prev_saved_entry[/LEFT]
    [LEFT]  set boot_once=true[/LEFT]
    [LEFT]fi[/LEFT]
        [LEFT]function savedefault {[/LEFT]
    [LEFT]  if [ -z "${boot_once}" ]; then[/LEFT]
    [LEFT]    saved_entry="${chosen}"[/LEFT]
    [LEFT]    save_env saved_entry[/LEFT]
    [LEFT]  fi[/LEFT]
    }
        [LEFT]function recordfail {[/LEFT]
    [LEFT]  set recordfail=1[/LEFT]
    [LEFT]  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi[/LEFT]
    }
        [LEFT]function load_video {[/LEFT]
    [LEFT]  insmod vbe[/LEFT]
    [LEFT]  insmod vga[/LEFT]
    [LEFT]  insmod video_bochs[/LEFT]
    [LEFT]  insmod video_cirrus[/LEFT]
    }
        [LEFT]insmod part_msdos[/LEFT]
    [LEFT]insmod ext2[/LEFT]
    [LEFT]set root='(hd0,msdos8)'[/LEFT]
    [LEFT]search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]if loadfont /usr/share/grub/unicode.pf2 ; then[/LEFT]
    [LEFT]  set gfxmode=auto[/LEFT]
    [LEFT]  load_video[/LEFT]
    [LEFT]  insmod gfxterm[/LEFT]
    [LEFT]  insmod part_msdos[/LEFT]
    [LEFT]  insmod ext2[/LEFT]
    [LEFT]  set root='(hd0,msdos8)'[/LEFT]
    [LEFT]  search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]  set locale_dir=($root)/boot/grub/locale[/LEFT]
    [LEFT]  set lang=en_US[/LEFT]
    [LEFT]  insmod gettext[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]terminal_output gfxterm[/LEFT]
    [LEFT]if [ "${recordfail}" = 1 ]; then[/LEFT]
    [LEFT]  set timeout=-1[/LEFT]
    [LEFT]else[/LEFT]
    [LEFT]  set timeout=10[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/00_header ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/05_debian_theme ###[/LEFT]
    [LEFT]set menu_color_normal=white/black[/LEFT]
    [LEFT]set menu_color_highlight=black/light-gray[/LEFT]
    [LEFT]### END /etc/grub.d/05_debian_theme ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/10_linux ###[/LEFT]
    [LEFT]if [ ${recordfail} != 1 ]; then[/LEFT]
    [LEFT]  if [ -e ${prefix}/gfxblacklist.txt ]; then[/LEFT]
    [LEFT]    if hwmatch ${prefix}/gfxblacklist.txt 3; then[/LEFT]
    [LEFT]      if [ ${match} = 0 ]; then[/LEFT]
    [LEFT]        set linux_gfx_mode=keep[/LEFT]
    [LEFT]      else[/LEFT]
    [LEFT]        set linux_gfx_mode=text[/LEFT]
    [LEFT]      fi[/LEFT]
    [LEFT]    else[/LEFT]
    [LEFT]      set linux_gfx_mode=text[/LEFT]
    [LEFT]    fi[/LEFT]
    [LEFT]  else[/LEFT]
    [LEFT]    set linux_gfx_mode=keep[/LEFT]
    [LEFT]  fi[/LEFT]
    [LEFT]else[/LEFT]
    [LEFT]  set linux_gfx_mode=text[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]export linux_gfx_mode[/LEFT]
    [LEFT]if [ "$linux_gfx_mode" != "text" ]; then load_video; fi[/LEFT]
    [LEFT]menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]	recordfail[/LEFT]
    [LEFT]	set gfxpayload=$linux_gfx_mode[/LEFT]
    [LEFT]	insmod gzio[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd0,msdos8)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=a9950f7a-15a2-4e08-9fb2-590ea49d2b79 ro   quiet splash vt.handoff=7[/LEFT]
    [LEFT]	initrd	/boot/initrd.img-3.0.0-12-generic[/LEFT]
    }
    [LEFT]menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]	recordfail[/LEFT]
    [LEFT]	insmod gzio[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd0,msdos8)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]	echo	'Loading Linux 3.0.0-12-generic ...'[/LEFT]
    [LEFT]	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=a9950f7a-15a2-4e08-9fb2-590ea49d2b79 ro recovery nomodeset [/LEFT]
    [LEFT]	echo	'Loading initial ramdisk ...'[/LEFT]
    [LEFT]	initrd	/boot/initrd.img-3.0.0-12-generic[/LEFT]
    }
    [LEFT]### END /etc/grub.d/10_linux ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/20_linux_xen ###[/LEFT]
    [LEFT]### END /etc/grub.d/20_linux_xen ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/20_memtest86+ ###[/LEFT]
    [LEFT]menuentry "Memory test (memtest86+)" {[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd0,msdos8)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]	linux16	/boot/memtest86+.bin[/LEFT]
    }
    [LEFT]menuentry "Memory test (memtest86+, serial console 115200)" {[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd0,msdos8)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set=root a9950f7a-15a2-4e08-9fb2-590ea49d2b79[/LEFT]
    [LEFT]	linux16	/boot/memtest86+.bin console=ttyS0,115200n8[/LEFT]
    }
    [LEFT]### END /etc/grub.d/20_memtest86+ ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/30_os-prober ###[/LEFT]
    [LEFT]menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ntfs[/LEFT]
    [LEFT]	set root='(hd0,msdos1)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set=root 267C91B77C91826B[/LEFT]
    [LEFT]	drivemap -s (hd0) ${root}[/LEFT]
    [LEFT]	chainloader +1[/LEFT]
    }
    [LEFT]### END /etc/grub.d/30_os-prober ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/40_custom ###[/LEFT]
    [LEFT]# This file provides an easy way to add custom menu entries.  Simply type the[/LEFT]
    [LEFT]# menu entries you want to add after this comment.  Be careful not to change[/LEFT]
    [LEFT]# the 'exec tail' line above.[/LEFT]
    [LEFT]### END /etc/grub.d/40_custom ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/41_custom ###[/LEFT]
    [LEFT]if [ -f  $prefix/custom.cfg ]; then[/LEFT]
    [LEFT]  source $prefix/custom.cfg;[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/41_custom ###[/LEFT]
    --------------------------------------------------------------------------------
        [LEFT]=============================== sda5/etc/fstab: ================================[/LEFT]
        --------------------------------------------------------------------------------
    [LEFT]# /etc/fstab: static file system information.[/LEFT]
    #
    [LEFT]# Use 'blkid' to print the universally unique identifier for a[/LEFT]
    [LEFT]# device; this may be used with UUID= as a more robust way to name devices[/LEFT]
    [LEFT]# that works even if disks are added and removed. See fstab(5).[/LEFT]
    #
    [LEFT]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/LEFT]
    [LEFT]proc            /proc           proc    nodev,noexec,nosuid 0       0[/LEFT]
    [LEFT]# / was on /dev/sda8 during installation[/LEFT]
    [LEFT]UUID=a9950f7a-15a2-4e08-9fb2-590ea49d2b79 /               ext4    errors=remount-ro 0       1[/LEFT]
    [LEFT]# swap was on /dev/sda9 during installation[/LEFT]
    [LEFT]UUID=8a95da6a-7b4c-41fc-ba86-826cb7a1d4c4 none            swap    sw              0       0[/LEFT]
    [LEFT]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/LEFT]
    --------------------------------------------------------------------------------
        [LEFT]=================== sda5: Location of files loaded by Grub: ====================[/LEFT]
        [LEFT]           GiB - GB             File                                 Fragment(s)[/LEFT]
        [LEFT]               =                boot/grub/core.img                             1[/LEFT]
    [LEFT]               =                boot/grub/grub.cfg                             1[/LEFT]
    [LEFT]               =                boot/initrd.img-3.0.0-12-generic               1[/LEFT]
    [LEFT]               =                boot/vmlinuz-3.0.0-12-generic                  1[/LEFT]
    [LEFT]               =                initrd.img                                     1[/LEFT]
    [LEFT]               =                vmlinuz                                        1[/LEFT]
        [LEFT]=============================== StdErr Messages: ===============================[/LEFT]
        [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
    [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
    [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
    [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
    [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
    [LEFT]awk: cmd. line:36: Math support is not compiled in[/LEFT]
           
  
```

Thanks!

---

### Post by sikander3786 on 2011-12-23
Thanks for the outputs.

Please confirm, you are able to boot Windows successfully, for now?

---

### Post by ahmedmahdy on 2011-12-23
Windows XP is booting well but I get a messages tells:
"Invalid boot.ini file .. Booting from C:\WINDOWS" then it boots

---

### Post by sikander3786 on 2011-12-23
Yeah fine. We might try to fix that error later.

So boot the Live CD/USB once again and get to a Terminal. Run these commands one by one:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Once completed, reboot and hopefully you'll be dual booting.

---

### Post by ahmedmahdy on 2011-12-23
> **sikander3786 said:**
> Yeah fine. We might try to fix that error later.

So boot the Live CD/USB once again and get to a Terminal. Run these commands one by one:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Once completed, reboot and hopefully you'll be dual booting.

Thanks! I'll reboot now but kindly check this message while executing the command:
```

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
```

---

### Post by ahmedmahdy on 2011-12-23
WOW! That really works! Thanks so much!

I just have 2 small issues for performance and maybe an error:

1- It takes 30-45 seconds after choosing desired OS to boot (time between clicking enter and to start boot process), Why does it take that long?

2- While choosing Windows, I get the following message:

```
error: no such device: 267C91B77C91826B
Press any key to continue...
```

I press any key then it works normally.

---

### Post by ahmedmahdy on 2011-12-23
I got another issue, the only mounted partition is the ext4 partition where I'm running my Xubuntu from! Cannot see Windows partitions nor my external hard drive!

---

