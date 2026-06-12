---
title: "Boot loader question"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by Greywolft on 2011-11-02
I installed ubuntu to my external drive and now I need to change the boot loader.

I'm running in circles trying to sift through all the google info. I can't change the Bios to read from usb external drive, so that option is out. 

I'd rather not change anything in the windows boot.ini based on the sketchy info I can find online.

Can anyone point me to an article or tutorial explaining exactly what to put in the boot.ini?

I have 2 disks, with 5 partitions.

[[IMG]http://img207.imageshack.us/img207/3500/diskparions.png[/IMG]](http://imageshack.us/photo/my-images/207/diskparions.png/) Uploaded with [ImageShack.us](http://imageshack.us)

Disk 0 has 2 partitions, windows and recovery
Disk 1 has 3, 916.85gb ntfs storage, 9.33gb ext4 with Ubuntu, and 4.67Gb shared for memory

If any more info is needed, I'll gladly provide if it means I can stop chasing my tail and reading till my eyes cross.
T.

---

### Post by dolphin194 on 2011-11-02
Hello, Greywolft. I would highly recommend NOT using the Windows bootloader since it's...well...Windows. You can recover the GRUB bootloader by following this procedure:

> 

[LIST]
[*]Insert your Ubuntu CD, reboot your computer and boot into a live session. 
[*]Install and run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), select 'First Repair' and apply. 
[*]Reboot without the CD. GRUB menu will appear and will propose both Ubuntu and Windows.
[/LIST]


source:[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Greywolft on 2011-11-02
> **dolphin194 said:**
> Hello, Greywolft. I would highly recommend NOT using the Windows bootloader since it's...well...Windows. You can recover the GRUB bootloader by following this procedure:



source:[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Well that got me the one result I was trying to avoid, now neither OS boots.

I ran the Boot-repair and got the success message along with this URL [http://paste.ubuntu.com/726590](http://paste.ubuntu.com/726590) telling me to reboot the machine. When I do however I get 
Error: No such Device: 1f56a261-34f2-4360-856e-bfb9711c4b09
Grub rescue>
Which I'm assuming is the Label of the Partition housing Ubuntu

So have I made it to where the only way to get into an OS is through this Disk now? 

Sorry not meaning to sound snippy but this is damned frustrating. I LOVE the Internet except for this one fatal flaw, too much info and not enough wisdom on my part to know what is valid.

I'll try to find a list of grub rescue commands and see if that helps. I have a feeling the no such device error is because the external is not seen as a bootable device by the bios. So now instead of going to the windows boot.ini it's trying to get the grub off the external which can't be seen till after boot up.

---

### Post by dniMretsaM on 2011-11-02
> **Greywolft said:**
> I can't change the Bios to read from usb external drive, so that option is out.

If USB isn't an option in the boot sequence menu (I'm assuming it isn't), look for another menu in the BIOS named something like hard drive sequence. A lot of older computers
have USB in there instead of the boot sequence menu.

---

### Post by oldfred on 2011-11-02
You have installed grub2's boot loader to the internal drive that requires the external to boot.

You need to reinstall the Windows boot loader to the internal.
Are you sure you cannot boot from USB? Most computers in the last 4 or 5 years will boot USB devices. Otherwise check out plop.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by Greywolft on 2011-11-02
> **dniMretsaM said:**
> If USB isn't an option in the boot sequence menu (I'm assuming it isn't), look for another menu in the BIOS named something like hard drive sequence. A lot of older computers
have USB in there instead of the boot sequence menu.

My computer is an HP Pavillion Media Center PC M7650n, with a weird bios that I shy away from flashing.

When it boots It says Ata AHCI Bios Version 3.08
**This Version only supports Hard Drive and CD-rom**

When in the Bios my options are
Floppy Group
HDD Group (my external doesn't appear here)
CD-ROM Group
Network Boot Group
Disabled

So unless I'm missing something, I find no place to change it to USB external bootup.

---

### Post by dniMretsaM on 2011-11-02
> **Greywolft said:**
> My computer is an HP Pavillion Media Center PC M7650n, with a weird bios that I shy away from flashing.

When it boots It says Ata AHCI Bios Version 3.08
**This Version only supports Hard Drive and CD-rom**

When in the Bios my options are
Floppy Group
HDD Group (my external doesn't appear here)
CD-ROM Group
Network Boot Group
Disabled

So unless I'm missing something, I find no place to change it to USB external bootup.

That is a weird BIOS... What's under Disabled?

---

### Post by Greywolft on 2011-11-02
> **oldfred said:**
> You have installed grub2's boot loader to the internal drive that requires the external to boot.

You need to reinstall the Windows boot loader to the internal.
Are you sure you cannot boot from USB? Most computers in the last 4 or 5 years will boot USB devices. Otherwise check out plop.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Ok Now I'm stumped, put in the Recovery Cd for my PC and NOW it loads Grub with no problems and straight into my Ubuntu Os. Didn't even get to the prompt to enter the fixboot or fixmbr, could the disk have done that on it's own?
Now I just need to edit it so I can turn off auto select and I'm good to go, as long as I can still access my XP when needed. Which I'm hesitant to reboot since at least now im in the actual External drives OS and not the CD boot.

Thanks for being patient with me and helping me sort through this mess.
T.

---

### Post by oldfred on 2011-11-02
Did you plug external back in? Grub in both internal & external want to boot from external.

In first BIOS does it tell you keys to use for BIOS and one time boot? Mine is f12. I recently changed to AHCI and get same message, but if I press f12, I get a list of devices to boot. Under hard drives, my flash appears if it is bootable.

---

### Post by Greywolft on 2011-11-02
> **dniMretsaM said:**
> That is a weird BIOS... What's under Disabled?
Unlike most of the Bios' I've seen, where you use - or + to move in the list. Mine has

1st boot priority 
2nd boot priority
3rd boot priority
4th boot priority

And you choose one from the list for each, disabled is the option for a priority. Mine is set 

1st CDROM
2nd HDD
3rd Network Boot
4th Disabled

---

### Post by Greywolft on 2011-11-02
> **oldfred said:**
> Did you plug external back in? Grub in both internal & external want to boot from external.

In first BIOS does it tell you keys to use for BIOS and one time boot? Mine is f12. I recently changed to AHCI and get same message, but if I press f12, I get a list of devices to boot. Under hard drives, my flash appears if it is bootable.
[FONT="Georgia"][SIZE="3"][COLOR="Purple"][I]
Yeah the external's been plugged in the whole time.

Mine is set to AHCI as well, so here's what I got using F12. By the way, good call and thanks, never even knew I could do that.

It brought up
Intel Boot Agent GEU 1.2.4 Beta 4
Client Mac Address ********************
DHCP. (this one was obviously searching since it kept gaining..
Once done it gave this message.
PXE-E49 - No boot file name received.

Then it started windows normally.

So now I'm back to square one and can access my XP OS but grub or Ubuntu aren't available unless my XP repair disk is in the CD-Rom. Still not sure how or why that is but it's Ok for now. It's better than where I was 3 hours ago.

I am however taking a break so's to not get overwhelmed and frustrated, which is what caused me to throw in the towel last time I tried Ubuntu. Plus my poor computer's been rebooted so many time's I'm afraid it will end up with the PC equivalent of Narcolepsy :wink:

Once I've gotten level headed again, I will resume my efforts. Thanks again for bearing with me and taking time out of your day to help. It's VERY much appreciated. =D>

T[/I][/COLOR][/SIZE][/FONT]

---

### Post by Greywolft on 2011-11-03
*Ok, back to it and ready to tackle this once again.*

---

### Post by oldfred on 2011-11-03
Post boot script results.txt or pastebin link from boot repair run of boot script.

---

### Post by Greywolft on 2011-11-03
> **oldfred said:**
> Post boot script results.txt or pastebin link from boot repair run of boot script.
[FONT=Georgia][SIZE=3][COLOR=Purple][I]
I'm hoping this is what you asked for. No clue how to clean it up and make it a bit less chaotic though. 4 Files with that name.

C:\clean\log\2011-11-02__18h26boot-repair05
C:\clean\log\2011-11-02__18h37boot-repair32(this one is below, file name says 11-02 not sure why it says From May 2011 at the top of document)
D:\clean\log\2011-11-02__18h26boot-repair05
D:\clean\log\2011-11-02__18h37boot-repair32
(D:drive is my HP recovery partition)[/I][/COLOR][/SIZE][/FONT]

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   606,999,959   606,999,897   7 NTFS / exFAT / HPFS
/dev/sda2         606,999,960   625,137,344    18,137,385   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,922,783,231 1,922,783,169   7 NTFS / exFAT / HPFS
/dev/sdb2       1,922,783,232 1,932,572,671     9,789,440  82 Linux swap / Solaris
/dev/sdb3    *  1,932,572,672 1,952,149,503    19,576,832  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 3,907,024,895 3,907,022,848   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9A3CEA153CE9EBE7                       ntfs       HP_PAVILION
/dev/sda2        7902-759A                              vfat       HP_RECOVERY
/dev/sdb1        FA5023E85023A9F9                       ntfs       Tobs Media
/dev/sdb2        96a2c58f-b15f-4f43-9566-bbc98f06ae3a   swap       
/dev/sdb3        1f56a261-34f2-4360-856e-bfb9711c4b09   ext4       
/dev/sdc1        88C2D23DC2D22F66                       ntfs       Elements

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /fastdetect /usepmtimer /NoExecute=OptIn
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 1f56a261-34f2-4360-856e-bfb9711c4b09
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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 1f56a261-34f2-4360-856e-bfb9711c4b09
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 1f56a261-34f2-4360-856e-bfb9711c4b09
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=1f56a261-34f2-4360-856e-bfb9711c4b09 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 1f56a261-34f2-4360-856e-bfb9711c4b09
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=1f56a261-34f2-4360-856e-bfb9711c4b09 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 1f56a261-34f2-4360-856e-bfb9711c4b09
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 1f56a261-34f2-4360-856e-bfb9711c4b09
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9A3CEA153CE9EBE7
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7902-759a
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=1f56a261-34f2-4360-856e-bfb9711c4b09 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=96a2c58f-b15f-4f43-9566-bbc98f06ae3a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 927.787807465 = 996.204572672  boot/grub/core.img                             1
 927.652202606 = 996.058968064  boot/grub/grub.cfg                             1
 927.959499359 = 996.388925440  boot/initrd.img-2.6.32-33-generic              1
 927.950428009 = 996.379185152  boot/vmlinuz-2.6.32-33-generic                 1
 927.959499359 = 996.388925440  initrd.img                                     1
 927.950428009 = 996.379185152  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 98 15 2e 24  |........?......$|
00000020  e4 c0 14 01 0e 45 00 00  00 00 00 00 02 00 00 00  |.....E..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 9a 75 02 79 20  20 20 20 20 20 20 20 20  |..).u.y         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



ADDITIONAL INFORMATION :
**************** log of boot-repair 2011-11-02__18h26 ****************
boot-repair version : 3-0ppa15~lucid
clean-ubiquity-common version : 3-0ppa8~lucid
internet: connected
boot-repair-common version : 3.0-0ppa22~lucid
/usr/share/clean/cleancommon-gui.sh: line 142:  4836 Terminated              while true; do
done
Restore the original repositories in /etc/apt/sources.list
LIVESESSION is : yes
BYTES_BEFORE_PART[1] (sda) = 63 sectors * 512 bytes = 32256 bytes.
BYTES_BEFORE_PART[2] (sdb) = 63 sectors * 512 bytes = 32256 bytes.
BYTES_BEFORE_PART[3] (sdc) = 2048 sectors * 512 bytes = 1048576 bytes.
OSPROBER: /dev/sda1:Windows XP Media Center Edition:Windows:chain
/dev/sda2:Windows NT/2000/XP:Windows1:chain
/dev/sdb3:Ubuntu 10.04.3 LTS (10.04):Ubuntu:linux
BLKID: /dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="HP_PAVILION" UUID="9A3CEA153CE9EBE7" TYPE="ntfs"
/dev/sda2: LABEL="HP_RECOVERY" UUID="7902-759A" TYPE="vfat"
/dev/sdb1: LABEL="Tobs Media" UUID="FA5023E85023A9F9" TYPE="ntfs"
/dev/sdb2: UUID="96a2c58f-b15f-4f43-9566-bbc98f06ae3a" TYPE="swap"
/dev/sdb3: UUID="1f56a261-34f2-4360-856e-bfb9711c4b09" TYPE="ext4"
/dev/sdc1: LABEL="Elements" UUID="88C2D23DC2D22F66" TYPE="ntfs"
sda1 contains Windows XP Media Center (windows)
sda2 contains Windows (windows)
sdb3 contains Ubuntu 10.04.3 LTS (linux)
2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 2 OS detected on sda disk.
Total of 1 OS detected on sdb disk.
sda contains minimum one OS
sdb contains minimum one OS
FDISK
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   606999959   303499948+   7  HPFS/NTFS
/dev/sda2       606999960   625137344     9068692+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1e5b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1922783231   961391584+   7  HPFS/NTFS
/dev/sdb2      1922783232  1932572671     4894720   82  Linux swap / Solaris
/dev/sdb3   *  1932572672  1952149503     9788416   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020fc3

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907024895  1953511424    7  HPFS/NTFS

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   606999959   303499948+   7  HPFS/NTFS
/dev/sda2       606999960   625137344     9068692+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1e5b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1922783231   961391584+   7  HPFS/NTFS
/dev/sdb2      1922783232  1932572671     4894720   82  Linux swap / Solaris
/dev/sdb3   *  1932572672  1952149503     9788416   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020fc3

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907024895  1953511424    7  HPFS/NTFS
sda1 : sda, not-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda1, with-os, no-gpt, no-fstab.
sda2 : sda, not-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda2, with-os, no-gpt, no-fstab.
sdb1 : sdb, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sdb1, no-os, no-gpt, no-fstab.
sdb3 : sdb, not-sepboot, grub, aptget, 32, with boot, /mnt/clean/sdb3, with-os, no-gpt, fstab-without-efi.
sdc1 : sdc, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sdc1, no-os, no-gpt, no-fstab.
PARTED: Model: ATA Hitachi HDT72503 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
1      32.3kB  311GB  311GB   primary  ntfs         boot
2      311GB   320GB  9286MB  primary  fat32        lba


Model: WD My Book 1111 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
1      32.3kB  984GB   984GB   primary  ntfs
2      984GB   989GB   5012MB  primary  linux-swap(v1)
3      989GB   1000GB  10.0GB  primary  ext4            boot


Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  2000GB  2000GB  primary  ntfs



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label
MOUNT aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/clean/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/clean/sda2 type vfat (rw)
/dev/sdb1 on /mnt/clean/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb3 on /mnt/clean/sdb3 type ext4 (rw)
/dev/sdc1 on /mnt/clean/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/sys/block/sda:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  adsp audio block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dri dsp dvd dvdrw ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mem mixer net network_latency network_throughput null oldmem pktcdvd port ppp psaux ptmx pts radio0 random rfkill rtc rtc0 scd0 sda sda1 sda2 sdb sdb1 sdb2 sdb3 sdc sdc1 sequencer sequencer2 sg0 sg1 sg2 sg3 sg4 shm snapshot snd sndstat sr0 stderr stdin stdout urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 v4l vbi0 vga_arbiter video0 video24 video32 zero
/dev/mapper:  control
DF Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs   1007M  189M  818M  19% /
none      devtmpfs   1002M  320K 1001M   1% /dev
/dev/sr0   iso9660    688M  688M     0 100% /cdrom
/dev/loop0
squashfs    661M  661M     0 100% /rofs
none         tmpfs   1007M  216K 1006M   1% /dev/shm
tmpfs        tmpfs   1007M  1.2M 1005M   1% /tmp
none         tmpfs   1007M   92K 1006M   1% /var/run
none         tmpfs   1007M  4.0K 1007M   1% /var/lock
none         tmpfs   1007M     0 1007M   0% /lib/init/rw
/dev/sda1  fuseblk    290G  270G   20G  94% /mnt/clean/sda1
/dev/sda2     vfat    8.7G  8.1G  574M  94% /mnt/clean/sda2
/dev/sdb1  fuseblk    917G   60G  858G   7% /mnt/clean/sdb1
/dev/sdb3     ext4    9.2G  2.3G  6.6G  26% /mnt/clean/sdb3
/dev/sdc1  fuseblk    1.9T  350G  1.5T  19% /mnt/clean/sdc1
FDISK
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   606999959   303499948+   7  HPFS/NTFS
/dev/sda2       606999960   625137344     9068692+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1e5b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1922783231   961391584+   7  HPFS/NTFS
/dev/sdb2      1922783232  1932572671     4894720   82  Linux swap / Solaris
/dev/sdb3   *  1932572672  1952149503     9788416   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020fc3

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907024895  1953511424    7  HPFS/NTFS
Logs saved into /mnt/clean/sda1/clean/log/2011-11-02__18h26boot-repair05
Logs saved into /mnt/clean/sda2/clean/log/2011-11-02__18h26boot-repair05
Logs saved into /mnt/clean/sdb3/var/log/clean/log/2011-11-02__18h26boot-repair05
combobox_ostoboot_bydefault_fillin
Order Linux according to their /boot type 64
Order Linux according to their /boot type 32
combobox_efi_fillin sdb3
combobox_separateboot_fillin
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide sdb3
efi_show_hide 4 (no-gpt)
set_radiobutton_place_alldisks
separate_bootpart and efi show_hide sdb3
efi_show_hide 4 (no-gpt)
************************Before mainwindow appear
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 4 (sdb3)
FSCK_ACTION yes PASTEBIN_ACTION yes
REINSTALL_POSSIBLE yes MBR_ACTION reinstall UNHIDEBOOT_ACTION yes (10.s)
PART_TO_REINSTALL_GRUB 4 (sdb3) FORCE_GRUB all NOFORCE_DISK sdb REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sdb1) grub-pc ()
/usr/share/clean/bootrepair.sh: line 56:  5384 Terminated              while true; do
done
RETOURCOMBO_purge_grub : sdb3 (Ubuntu 10.04.3 LTS)
RETOURCOMBO_ostoboot_bydefault : sdb3 (Ubuntu 10.04.3 LTS)
separate_bootpart and efi show_hide sdb3
efi_show_hide 4 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : sdb
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sdb1
set_radiobutton_place_alldisks
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide sdb3
efi_show_hide 4 (no-gpt)
set_radiobutton_place_alldisks
separate_bootpart and efi show_hide sdb3
efi_show_hide 4 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : sdb
internet: connected
************************Before Repairing
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 4 (sdb3)
FSCK_ACTION yes PASTEBIN_ACTION yes
REINSTALL_POSSIBLE yes MBR_ACTION reinstall UNHIDEBOOT_ACTION yes (10.s)
PART_TO_REINSTALL_GRUB 4 (sdb3) FORCE_GRUB all NOFORCE_DISK sdb REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sdb1) grub-pc ()
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var
OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
65:00/01
Not automatically fixing this.
/dev/sda2: 17775 files, 2116217/2262741 clusters
OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb1 was processed successfully.
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb3: 138064/612000 files (0.1% non-contiguous), 617109/2447104 blocks
OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdc1 was processed successfully.
Freed space function
/dev/sda1            303499948 282903704  20596244  94% /mnt/clean/sda1
/dev/sda2              9050964   8464868    586096  94% /mnt/clean/sda2
/dev/sdb3              9634744   2314764   6830560  26% /mnt/clean/sdb3
Reinstall the GRUB of sdb3 into the MBR of sda
Unmount (force) all OS partitions except / and partition where we reinstall GRUB (sdb3)
dpkg_function
grub-install (GNU GRUB 1.98-1ubuntu12)
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /mnt/clean/sdb1: No such file or directory
ls: cannot access /mnt/clean/sdb1: No such file or directory
ls: cannot access /mnt/clean/sdb1: No such file or directory
ls: cannot access /mnt/clean/sdb1: No such file or directory
ls: cannot access /mnt/clean/sdc1: No such file or directory
ls: cannot access /mnt/clean/sdc1: No such file or directory
ls: cannot access /mnt/clean/sdc1: No such file or directory
ls: cannot access /mnt/clean/sdc1: No such file or directory
Found Windows XP Media Center Edition on /dev/sda1
Found Windows NT/2000/XP on /dev/sda2
done
Mount all the partitions for the logs
Reinstall the GRUB of sdb3 into the MBR of sdb
Unmount (force) all OS partitions except / and partition where we reinstall GRUB (sdb3)
dpkg_function
grub-install (GNU GRUB 1.98-1ubuntu12)
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /mnt/clean/sdb1: No such file or directory
ls: cannot access /mnt/clean/sdb1: No such file or directory
ls: cannot access /mnt/clean/sdb1: No such file or directory
ls: cannot access /mnt/clean/sdb1: No such file or directory
ls: cannot access /mnt/clean/sdc1: No such file or directory
ls: cannot access /mnt/clean/sdc1: No such file or directory
ls: cannot access /mnt/clean/sdc1: No such file or directory
ls: cannot access /mnt/clean/sdc1: No such file or directory
Found Windows XP Media Center Edition on /dev/sda1
Found Windows NT/2000/XP on /dev/sda2
done
Mount all the partitions for the logs
Unhide boot menu (10 seconds) if Wubi detected
Unhide GRUB boot menu in sdb3/boot/grub/grub.cfg
internet: connected
/usr/share/clean/bootrepair-actions.sh: line 88:  8591 Terminated              while true; do
done
dpkg-preconfigure: unable to re-open stdin:
```

---

### Post by oldfred on 2011-11-03
Please use code tags. You highlight like copying and click on the # in the edit bar at the top of your post to automatically add code tags. It makes it easier to read.

I do not see anything really wrong. Is this the latest run of boot info script? I see you are running it from the boot repair. The May date is the last version of the boot info script.

There have been some issues with grub2, large partitions or large drives. You may just have to have Ubuntu's / (root) nearer the front of a drive.

---

### Post by Greywolft on 2011-11-04
I'm closing this thread and starting a new one since I'm going to try a whole new approach to this mess.

Thanks to all for the help.

---

