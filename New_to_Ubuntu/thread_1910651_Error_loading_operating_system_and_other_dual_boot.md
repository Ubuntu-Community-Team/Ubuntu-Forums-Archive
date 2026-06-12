---
title: "Error loading operating system and other dual boot woes"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by oktorockto on 2012-01-17
Hi all,

well, firstly thanks to everyone in the Linux community for the collective effort over the years which has led to the point it is at now. I'm a fairly well experienced Windows user but have been sticking with XP over the years as I was bitten first by the lack of device support for Windows XP64 and then the horrors of Vista. I'm still running XP on my business computers as I do a lot of work in acoustics and audio but I am going to slowly change over to Ubuntu as I can and will probably leave a small windows XP partition for the few things I will have to keep it for. Anyway, I am more than impressed with Ubuntu - on to my problems.

I have a system which originally had two drives - XP on an 80gb Maxtor IDE drive with a Samsung 500gb SATA drive for file storage. I started off by using the Ubunbtu download to install alongside windows but it seemed pretty slow (My windows XP install was a few years old, had gotten very slow and also had some spy-ware problems I could not fix)

So I then decided to try installing Ubuntu on a spare Western Digital 500gb IDE drive I had. After doing this I realized I would have been better using the SATA drive with the extra transfer speed this should give it.

So I have ended up with the windows XP partition still on the 80gb Maxtor drive (dev/sdb), the Ubuntu operating system on the 500gb Samsung drive (dev/sdc) with the 500gb WD drive as a spare (sda)

I had it all working nicely apart from nbot being able to get a bootloader to work - this didn't matter as I only need the XP partition to be there until I transfer all of the files i need over from it and I can choose the boot device by pressing F11 after BIOS loads.

I have messed around a bit with permissions and trying to get drives to automount at startup and be shared between user accounts and now realize I should have done a bit more reading before jumping headfirst in a blind sort of way. I don't care too much about the sharing and stuff at the moment as the major problem I have now is that when I try and boot Ubuntu I get the message "Error loading operating system" after BIOS. Occasionally I have got Ubuntu to boot but only about one in every ten tries. I can't get windows to boot now either!

I have booted off the CD and downloaded and installed boot info script and the results are pasted below. I am using v11.10. I hope someone can help me recover teh operating systems. I have a feeling that I have Grub installed on all of my hard drives or something like that.

Thanks in advance to anyone who can help.

Okto

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for .
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   160,055,594   160,055,532   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   972,580,863   972,578,816  83 Linux
/dev/sdc2         972,582,910   976,771,071     4,188,162   5 Extended
/dev/sdc5         972,582,912   976,771,071     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3C68A9C468A97CF0                       ntfs       Western500
/dev/sdb1        28844B0B844ADAC8                       ntfs       Home system
/dev/sdc1        96388fff-70be-4515-afd5-30ddf136f547   ext4       
/dev/sdc5        5222e70e-7290-4360-bbd7-c75600f4fdb1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set=root 96388fff-70be-4515-afd5-30ddf136f547
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos1)'
  search --no-floppy --fs-uuid --set=root 96388fff-70be-4515-afd5-30ddf136f547
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 96388fff-70be-4515-afd5-30ddf136f547
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=96388fff-70be-4515-afd5-30ddf136f547 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 96388fff-70be-4515-afd5-30ddf136f547
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=96388fff-70be-4515-afd5-30ddf136f547 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 96388fff-70be-4515-afd5-30ddf136f547
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=96388fff-70be-4515-afd5-30ddf136f547 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 96388fff-70be-4515-afd5-30ddf136f547
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=96388fff-70be-4515-afd5-30ddf136f547 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 96388fff-70be-4515-afd5-30ddf136f547
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 96388fff-70be-4515-afd5-30ddf136f547
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 28844B0B844ADAC8
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

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=96388fff-70be-4515-afd5-30ddf136f547  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=5222e70e-7290-4360-bbd7-c75600f4fdb1  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/New 500  ntfs  nls=iso8859-1,ro,users,umask=000,user  0  0  
/dev/sdb1                                  /media/sdb1     ntfs  defaults                  0  0  
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               4
               =                boot/initrd.img-3.0.0-14-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                initrd.img.old                                 4
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  65 5b 14 25 65 2c 62 39  69 1f 22 e7 43 c6 a4 56  |e[.%e,b9i.".C..V|
00000010  58 65 03 4b 4d 4e 61 eb  ae ec da c8 5c 49 cf df  |Xe.KMNa.....\I..|
00000020  69 11 b9 07 67 c9 1c 9d  ab f2 37 cc 91 92 a1 98  |i...g.....7.....|
00000030  91 0e f3 96 39 34 95 87  3b 5e c1 54 bd 12 c4 cf  |....94..;^.T....|
00000040  7f 78 65 ee f5 9c 43 8d  b5 52 5b ab cc 93 9d cb  |.xe...C..R[.....|
00000050  0b 97 2a 4b 9d b7 79 41  15 9a 8c e5 42 d9 3d fb  |..*K..yA....B.=.|
00000060  29 ad 22 72 7d 42 3b c5  37 31 34 93 63 91 a3 ac  |)."r}B;.714.c...|
00000070  2d 3c 96 de 27 77 37 35  43 ff ac dc 2a 3f 5f b2  |-<..'w75C...*?_.|
00000080  2e 3a a0 7c 95 32 b0 31  c2 f3 a5 d5 7a 6d ae 18  |.:.|.2.1....zm..|
00000090  8e 4b ef 11 8b 95 de 5c  2d 21 97 91 8c a6 ad 6f  |.K.....\-!.....o|
000000a0  9a 90 9b 75 45 4c 58 f6  1a 7d 53 65 59 d9 bd b8  |...uELX..}SeY...|
000000b0  14 aa 65 a5 70 43 3e de  86 9f e5 85 bf ba ac 06  |..e.pC>.........|
000000c0  de 4c 36 26 ef 1f a4 33  79 b6 3e 57 53 14 5a bf  |.L6&...3y.>WS.Z.|
000000d0  ad fa 67 b2 2f 38 34 9d  86 0f 26 7b 35 50 9c 9c  |..g./84...&{5P..|
000000e0  e3 73 91 4f 9e 58 2d 06  1b 71 3e 2b d7 5e 76 02  |.s.O.X-..q>+.^v.|
000000f0  d1 7c b8 8a ad e2 e3 47  87 96 ac 16 27 be 37 b2  |.|.....G....'.7.|
00000100  25 c2 57 ed 1f 96 9f da  49 9d d0 ed 5e 40 6e 96  |%.W.....I...^@n.|
00000110  ac 5a b0 4c fc e6 2f 75  dd 1f da ea bb 07 9b 84  |.Z.L../u........|
00000120  25 1b 4d 57 1e b2 c6 13  3d 19 77 da 11 a0 64 4c  |%.MW....=.w...dL|
00000130  5b 6e 42 7a 08 58 bc e7  4b 68 a1 b9 03 86 42 78  |[nBz.X..Kh....Bx|
00000140  c1 0d 97 93 10 ba c9 b1  c7 85 15 60 f0 ed e0 e3  |...........`....|
00000150  c3 e6 81 2d c3 ec e4 5a  01 0f 3b 7d 82 ee 80 a6  |...-...Z..;}....|
00000160  a5 e4 81 1d 30 c4 ec d4  7b 7c 18 62 67 72 f0 56  |....0...{|.bgr.V|
00000170  d7 0c a0 ca aa 8e 8a c6  86 8e 4a 00 cd 0d d9 23  |..........J....#|
00000180  cb 0c 6a 7d 4f 0c 0c f4  89 d9 21 21 0d ff 4f 9a  |..j}O.....!!..O.|
00000190  bc e9 85 e0 9c 25 c5 b3  26 46 57 50 62 17 62 18  |.....%..&FWPb.b.|
000001a0  64 da 71 38 2e 48 13 84  4b fd 9a d6 f0 41 82 3b  |d.q8.H..K....A.;|
000001b0  a6 1f 29 db 76 7d ab 23  18 24 c7 fc 5c b8 00 fe  |..).v}.#.$..\...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 3f 00 00 00  |............?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
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

### Post by cbanakis on 2012-01-17
I have only been using linux for a year or 2, so I am still pretty new to all of this.

I have had a problem with booting that might be related.  (long shot though)

For some reason, if you have multiple hard drives in one system, Ubuntu likes to install the boot loaded on the lowest numerical device, regardless of what drive Ubuntu itself is installed on.

Example

Sata0 1TB 7200rpm
Sata1 300GB 1000RPM
Sata2 160GB SSD

So you have windows installed on your 10000rpm drive.  (Sata1)
You use the TB drive for storage. (Sata0)
And you just installed Ubuntu on your brand new SSD. (Sata2)

When you tell your Bios to boot to your 10000rpm drive, windows boots.
But if you try to boot to your SSD where you installed Ubuntu, nothing happens.

That is because your TB drive is SATA0, and that is where your boot loader was installed.
So if you tell your BIOS to boot to the TB drive, you would actually be booting off the SSD.

Not sure why it is the way it is, but I'm glad I eventually figured it out.


On a side note...

You said you work with acoustics, and audio.

Just wanted to share, that I have Adobe Audition 3.0 running on my Ubuntu through wine.

Your millage may vary, but I just installed in as if I were using windows.

No difficulties, or issues of any kind, and from what I can tell, it works perfectly.

Not sure if thats the type of software you use though.

---

### Post by oktorockto on 2012-01-17
Thanks for replying. I think it might be a problem like the one you describe - just need some help in figuring it out.

I use samplitude for recording/editing audio - it is very good. I havent tried it under Wine yet. The main problem comes with getting decent drivers for multi channel audio interfaces. I also use software such as EASE and other acoustics industry software such as INSUL and Bruel and Kjaer applications - these might run under Wine but havent had a chance yet. When I can confidently run Linux on my home system I'll start a dual boot machine at work and gradually try to change over to it. I have already been using firefox/thunderbird for years and other open software such as Lyx so hopefully this can all be reality.

---

### Post by saneearth on 2012-01-17
Wow, looks like some kind of mess I would have made or have made in the past. :) Honestly, I can't tell you how to fix this. My mind got bent by looking at what you did, though I have done similar things. Instead of "fixing" a lot of times it is just best now that you have done some exploring to decide what configuration you are sure you want and to start all over. If you don't want Windows to figure into the equation, but want to just preserve the data, I would pull the drive out completely. I would then reinstall Ubuntu. You could just format your root partition and preserver your home partition and data if you would like during install. After the install is complete, I would then shut down and connect the Windows drive. The drive should mount or will mount if you click on it after Ubuntu starts and you can then pull what data you need or just use it for storage. It does appear grub is installed twice. Typically, it is best to have windows installed first on sda, and then install Ubuntu and grub should install by default on sda also. If you don't want windows however, pull the drive out so that the windows install will not even be entered in grub. Hope I haven't confused you more, but starting again may be your best bet. IMHO

---

### Post by oktorockto on 2012-01-17
Agreed - a real mess. I just changed the boot order to the Windows drive and it went through and loaded the Ubuntu partition. My next step is I'm going to disconnect the drives other than the Ubuntu drive and try to use boot repair on just that and see what happens.....

---

### Post by oktorockto on 2012-01-17
Ok - sort of solved. I'm back to the position of being able to access each partition seperately. Back to the boot loader later. Thanks for help.

---

### Post by cbanakis on 2012-01-17
The method I used as a permanent solution, was to open up my box, and re-arrange the cables to make sure the drive I wanted to run Ubuntu on was plugged into sata0.

Then I re-installed everything, and all has been well ever since.


You can also avoid the problem all together by selecting advanced during Ubuntu setup.
(there you can specify which drive to install the bootloader on)

But advanced looked a little too advanced for me, so I re-arranged my cables instead.  :)

---

### Post by oktorockto on 2012-01-18
cbanakis - I like your practical style - I might give that a go later.

---

### Post by cbanakis on 2012-01-20
> **oktorockto said:**
> cbanakis - I like your practical style - I might give that a go later.

Yeah, thats what I did.

I changed the boot settings in BIOS to get it to work, then next time I re-installed everything (A few months later), I re-arranged the wires to do it right.

---

