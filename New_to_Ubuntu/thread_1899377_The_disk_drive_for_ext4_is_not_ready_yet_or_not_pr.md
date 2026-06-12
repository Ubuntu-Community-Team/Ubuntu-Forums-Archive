---
title: "The disk drive for ext4 is not ready yet or not present. Continue to wait; or press"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by dantakeoff on 2011-12-23
Hello...here my problem...
I have a dual-boot machine with windoze7 and Ubuntu 10.04, and for some reason when i was installing ubuntu I couldnt keep it simple and create just 2 partitions, 1 for W7 and 1 for Ubuntu, so now i have a partiton for the restoration of W7, a swap partition and an HP partition...all very confusing...
Anyway, I tried to fix a problem that occured after the installation, which was that about half the time, after the grub menu appeared, ubuntu wouldnt boot. I have no idea what I did to fix it, cause I just followed some instructions I found on google, and it must have worked, cause now it boots every time...
my problem is now this: i hit a splash screen that informs me "The disk drive for ext4 is not ready yet or not present. Continue to wait; or press s to skip mounting or M for manual recovery." I hit S and its all cool, but extremely annoying, and other people using my pc never know what to do...
I understand it is not a huge problem but it one that i would very much like to iron out...
Any suggestions?

---

### Post by oldfred on 2011-12-23
Are you mounting something in fstab besides / (root). Or is Ubuntu on another device?

May be just easier to document entire boot process, post results.txt:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk

---

### Post by dantakeoff on 2011-12-23
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   210,061,746   209,854,899   7 NTFS / exFAT / HPFS
/dev/sda3         600,952,832   625,139,711    24,186,880   7 NTFS / exFAT / HPFS
/dev/sda4         210,063,358   600,952,831   390,889,474   5 Extended
/dev/sda5         210,063,360   590,399,487   380,336,128  83 Linux
/dev/sda6         590,401,536   600,952,831    10,551,296  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        EAA0466DA0464075                       ntfs       SYSTEM
/dev/sda2        4A304D59304D4CDF                       ntfs       HP
/dev/sda3        F66A5C276A5BE2C3                       ntfs       FACTORY_IMAGE
/dev/sda5        612c5966-0520-467f-8231-184f7db5f100   ext4       
/dev/sda6        528d859b-ab58-4dce-a942-5ecdf029ccc4   swap       
/dev/sdb1        3A17-6D40                              vfat       BAMBOOZLE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw)
/dev/sdb1        /media/BAMBOOZLE         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set 612c5966-0520-467f-8231-184f7db5f100
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
search --no-floppy --fs-uuid --set 612c5966-0520-467f-8231-184f7db5f100
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
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 612c5966-0520-467f-8231-184f7db5f100
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=612c5966-0520-467f-8231-184f7db5f100 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 612c5966-0520-467f-8231-184f7db5f100
	echo	'Loading Linux 2.6.32-37-generic ...'
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=612c5966-0520-467f-8231-184f7db5f100 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 612c5966-0520-467f-8231-184f7db5f100
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=612c5966-0520-467f-8231-184f7db5f100 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 612c5966-0520-467f-8231-184f7db5f100
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=612c5966-0520-467f-8231-184f7db5f100 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 612c5966-0520-467f-8231-184f7db5f100
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 612c5966-0520-467f-8231-184f7db5f100
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set EAA0466DA0464075
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set F66A5C276A5BE2C3
	chainloader +1
}
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
LABEL=linux_root               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=528d859b-ab58-4dce-a942-5ecdf029ccc4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 138.374168396 = 148.578131968  boot/grub/core.img                             1
 232.519767761 = 249.666199552  boot/grub/grub.cfg                             2
 138.443065643 = 148.652109824  boot/initrd.img-2.6.32-33-generic              1
 138.485973358 = 148.698181632  boot/initrd.img-2.6.32-37-generic              1
 138.427234650 = 148.635111424  boot/vmlinuz-2.6.32-33-generic                 1
 138.433185577 = 148.641501184  boot/vmlinuz-2.6.32-37-generic                 1
 138.485973358 = 148.698181632  initrd.img                                     1
 138.443065643 = 148.652109824  initrd.img.old                                 1
 138.433185577 = 148.641501184  vmlinuz                                        1
 138.427234650 = 148.635111424  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 40 20 00  |.Z.MSWIN4.1..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  02 4c 38 3a b4 d1 01 00  00 00 00 00 02 00 00 00  |.L8:............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 40 6d 17 3a 4d  79 20 50 61 73 73 70 6f  |..)@m.:My Passpo|
00000050  72 74 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |rtFAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200



```

---

### Post by dantakeoff on 2011-12-23
Thanx for the quick reply...I dont know anything about fstab, im not even sure i followed your instructions properly, and I have no idea whats mounted and what isnt...Thanx for your patience...

---

### Post by oldfred on 2011-12-23
I am not sure how you boot at all. You can use devices, UUIDs & labels to mount partitions. Generally UUIDs are used as the almost never change unless you do something major to your system. Labels are not used much and maybe should be used more as then you have total control over when things change.

Except in your case you are mounting root with a label, but do not have it labeled. That is why I wonder how it boots at all?

```
# / was on /dev/sda5 during installation
[COLOR=Red]LABEL=linux_root[/COLOR]               ext4    errors=remount-ro 0       1

Device           UUID                                   TYPE       LABEL

/dev/sda1        EAA0466DA0464075                       ntfs       SYSTEM
/dev/sda2        4A304D59304D4CDF                       ntfs       HP
/dev/sda3        F66A5C276A5BE2C3                       ntfs       FACTORY_IMAGE
/dev/sda5        612c5966-0520-467f-8231-184f7db5f100   ext4       
/dev/sda6        528d859b-ab58-4dce-a942-5ecdf029ccc4   swap       
/dev/sdb1        3A17-6D40                              vfat       BAMBOOZLE

```You can either go back to UUID to mount it usin gthe UUID shown for sda5 and the style for swap or add a label to sda5 that is [COLOR=Red]linux_root.[COLOR=Black]
You can use gparted or disk utility to add a label.
[/COLOR] [/COLOR]

---

### Post by dantakeoff on 2011-12-23
You can either go back to UUID to mount it usin gthe UUID shown for sda5 and the style for swap or add a label to sda5 that is linux_root.
You can use gparted or disk utility to add a label.

How exactly do I add a label, and why would I even want to if the machine boots ok? Will that sort out the splash screen problem? If you have the time, I will do my best to follow your instructions... Im 8 hours in front of you though, so I have to sleep, but ill be here tommorow. Again thanks for your time...

---

### Post by oldfred on 2011-12-23
In system, administration, Disk Utility click on the partition and use edit labels to change label to linux_root.  It must be exactly the same as you have it in fstab, i.e. no caps w/ unscore all have to be the same.

---

### Post by dantakeoff on 2011-12-24
AAAAAARRRRGH! My pc locked up after I opened Disk Utility, clicked on my Linux partition and checked the "bootable" option after it wouldnt let me change the label...Now every time I boot into Linux, it drops to shell, saying "Gave up waiting for root device" HELP! Is there a script I can write down on a piece of paper or something I can do to get my lovely Ubuntu to boot?
Im sorry about all of this....
Edit: Bizzare...one in every 3 or 4 attempts, it boots! What!?

Edit: WHOOOOHOOO! Solved! I booted into Puppy Linux Lucid live cd, which has an incredibly intuitive Grub4 installation menu, all I had to do was open it and click OK three times, it picked up all my partitions and OS's and installed in about 2 seconds, I rebooted and hey presto, everything worked!

Thanks for the help anyway...

---

