---
title: "error: no such partition. grub rescue&gt;"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by kongluke on 2012-02-09
Hi,

When I turn on my computer, an eee dual-booting with windows and the ubuntu 11.10, it says "error: no such partition" and gives a "grub rescue>" prompt.

I had accidently chosen the wrong option from the grubs menu the last time I was booting up (windows in rescue mode?); when asked whether I wanted to reset to factory I pressed "exit," but then it started "Installing..." something, so I panicked and turned off the computer.

Here's the boot info script:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 30576 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 NTFS / exFAT / HPFS
/dev/sda2         209,717,248   241,174,527    31,457,280  1b Hidden W95 FAT32
/dev/sda3         241,176,574   488,353,791   247,177,218   5 Extended
/dev/sda5         486,277,120   488,353,791     2,076,672  82 Linux swap / Solaris
/dev/sda4         488,353,792   488,395,119        41,328  ef EFI (FAT-12/16/32)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16018046976 bytes
107 heads, 15 sectors/track, 19492 cylinders, total 31285248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,192    31,285,247    31,283,056   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        186EB4AD6EB48552                       ntfs       
/dev/sda2        86F4-D40A                              vfat       
/dev/sda5        0130dc66-56c6-4ada-b678-d438690949f6   swap       
/dev/sdb1        724A-F61A                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/186EB4AD6EB48552  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 80 0c  |........?.......|
00000020  f8 ff df 01 f2 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 0a d4 f4 86 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader on sda3

00000000  06 00 00 00 00 00 00 00  9e 68 3f 00 00 00 00 00  |.........h?.....|
00000010  63 a2 13 26 64 aa cb 01  1d 55 34 d7 fa b2 cc 01  |c..&d....U4.....|
00000020  1d 55 34 d7 fa b2 cc 01  1d 55 34 d7 fa b2 cc 01  |.U4......U4.....|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 10 00 00 00 00  63 a2 13 26 64 aa cb 01  |........c..&d...|
00000050  2b 0b 32 d7 fa b2 cc 01  2b 0b 32 d7 fa b2 cc 01  |+.2.....+.2.....|
00000060  2b 0b 32 d7 fa b2 cc 01  00 00 00 00 00 00 00 00  |+.2.............|
00000070  00 00 00 00 00 00 00 00  00 00 00 10 00 00 00 00  |................|
00000080  90 dd 01 18 00 00 00 00  77 dd 01 18 00 00 00 00  |........w.......|
00000090  00 00 00 00 00 00 00 00  28 00 00 00 00 00 00 00  |........(.......|
000000a0  01 00 00 00 40 00 00 00  00 00 00 00 00 00 00 00  |....@...........|
000000b0  1b 00 01 00 28 00 00 00  28 00 00 00 18 00 00 00  |....(...(.......|
000000c0  00 00 00 00 00 00 02 00  00 00 00 00 00 00 00 00  |................|
000000d0  c0 e0 77 a7 20 f3 d4 b9  9b dd 01 18 00 00 00 00  |..w. ...........|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  30 00 00 00 00 00 00 00  01 00 00 00 40 00 00 00  |0...........@...|
00000100  00 00 00 00 00 00 00 00  16 00 15 00 28 00 08 00  |............(...|
00000110  28 00 08 00 70 00 01 00  00 00 00 00 00 00 00 00  |(...p...........|
00000120  c8 00 00 00 00 00 00 00  db 40 00 00 00 00 00 00  |.........@......|
00000130  41 41 00 00 03 00 00 00  a7 dd 01 18 00 00 00 00  |AA..............|
00000140  9b dd 01 18 00 00 00 00  9b dd 01 18 00 00 00 00  |................|
00000150  88 00 00 00 00 00 00 00  01 00 00 00 40 00 00 00  |............@...|
00000160  00 00 00 00 00 00 00 00  0f 00 0e 00 28 00 00 00  |............(...|
00000170  28 00 60 00 58 08 01 00  00 00 40 00 00 00 08 00  |(.`.X.....@.....|
00000180  01 00 00 00 00 00 00 00  0e 8c 3f 00 00 00 00 00  |..........?.....|
00000190  93 7d 00 00 00 00 01 00  60 00 4e 00 00 00 00 00  |.}......`.N.....|
000001a0  79 7d 00 00 00 00 01 00  e7 ba 36 26 64 aa cb 01  |y}........6&d...|
000001b0  00 dc f5 dd 4e c6 c0 01  8f 1c 37 26 64 aa 00 fe  |....N.....7&d...|
000001c0  ff ff 82 fe ff ff 02 f0  9b 0e 00 b0 1f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```Any suggestions would be much appreciated!

---

### Post by Rubi1200 on 2012-02-10
We'll try and find someone to help you with this issue.

Thanks for being patient.

---

### Post by oldfred on 2012-02-10
It is not efi, and is standard MBR partitioning. A few vendors have  started naming the vendor utilities partition as "efi" but a true efi  has to be the first partition and will be gpt partitioning. It is just a  label.

With MBR partitioning you have the boot loader in the MBR. But with wubi the boot loader has to be Windows. (not sure if wubi would even work at all with efi??).

Since you have a separate swap partition did you start to install Ubuntu to partitions?

Do you have a Windows repairCD? If so you can run the Windows auto fixes 3 times or use Windows command line to run the BootRec.exe /fixMBR  command.

You can also install a Windows work alike boot loader from Ubuntu's liveCD if you do not have a Windows repairCD.

More info on Fixing Windows:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kongluke on 2012-02-10
Thank you for the reply.

I'm very new at all this, and don't know  what your first eight sentences mean.  The original installation went  wrong halfway through; following instructions on this thread plus lucky  guesswork got it to work (but/so I can't answer your first question):
[http://ubuntuforums.org/showthread.php?t=1889153](http://ubuntuforums.org/showthread.php?t=1889153)

I don't have a Windows repair CD.

>You can also install a Windows work alike boot loader from Ubuntu's
> liveCD if you do not have a Windows repairCD.

I think Ubuntu's liveCD is the flashdrive I'm use to install (and now run) Ubuntu, eh?  The only menu options I have in the "installer boot menu" is to run Ubuntu, install Ubuntu, test memory, boot from first hard disk, advanced options (empty), and help.

>How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
>[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Is  it the "How to restore the Windows Vista or 7 bootloader" section that  I'm after?  I should purchase and download the vista recovery, use a  universal USB installer to get it on a flashdrive, and then do the  bootrec.exe commands as instructed?  

Thanks for your help!

---

### Post by oldfred on 2012-02-10
If you have the newest versions, you may not have synaptic either, so you can run this also.
sudo apt-get install synaptic

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

then once you get Windows booting, boot into the repair/recovery mode and make your own Windows repairCD.


Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by kongluke on 2012-02-10
Thank you!

In the Synaptic Package Manager "Settings", the "Repositories" option is darkened and not selectable.

There might have been some problem when I installed it?  I'll paste in the terminal conversation below.  After the first failure, I found installed it from the "Ubuntu Software Centre".  Then repeating the command suggested that it was already installed.  I couldn't get into the Synaptic Package Manager from the launcher on the left side (the icon would just glow), or from the "dash home" search (nothing found), but entering "synaptic" in the terminal popped it open as a window... but no repositories.

```
ubuntu@ubuntu:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate
ubuntu@ubuntu:~$ !!
sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 366 not upgraded.
ubuntu@ubuntu:~$ synaptic

(synaptic:8054): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:8054): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:8054): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:8054): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


```Any suggestions now?

---

### Post by westie457 on 2012-02-10
To run Synaptic in the terminal you have be root, ie use sudo or gksudo synaptic. Then you will be able to change settings and install apps.

---

### Post by kongluke on 2012-02-10
Ach, thanks!  Works much better with sudo.

```
ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.

```That sounds encouraging!  How do I get windows booting?  When I turn the computer off and then on, it still goes to "error: no such partition".  Am I missing a step?

Thanks!

---

### Post by oldfred on 2012-02-10
If you updated sda and you get the same error, do you have BIOS booting from something else?

Or do you not have a boot flag on the NTFS partition? Grub does not need a boot flag, but Windows and Lilo do.

---

### Post by kongluke on 2012-02-11
I'm not sure where else bios might be booting from?
GParted shows a "boot" flag with dev/sdb1, which is ntfs, but there's a scary-sounding warning.  I'll attach pictures of GParted and the sdb1 information (the line 'file system support: ntfsprogs' is missing from the screenshot of the latter.
Thank you!

---

### Post by oldfred on 2012-02-11
Linux or gparted does not mount a NTFS partition that has errors to avoid creating more errors that chkdsk cannot fix.

You need to run chkdsk on your sda1 or sdb1. It seems that flash drive must now be sda as screenshots are showing drive as sdb?

You need a Windows repairCd or USB to run chkdsk. If Windows starts at all you may be able to use f8 as you start to boot to get to a repair console but with all the errors reported that may not be possible. Chkdsk has to be rerun until there are no errors as it does not fix everything on one pass.

If you look in Disk Utility and click on the drive, what does Smart Status say about drive. I do not understand details, but green is good.

---

### Post by kongluke on 2012-02-11
Okay, I've made a Windows Repair USB.  
startup repair "cannot repair this computer automatically"
"This version of system recovery options is not compatible with the version of windows you are trying to repair" (I'm not sure why; I made the USB from a Windows 7 machine, and my computer also has Windows 7)

I could open a command prompt and ran chkdsk c: /f.  It "made corrections to the file system."  I ran it again, and it "checked the file system and found no problems"

In DiskUtility, SmartStatus has a green light.

I'm gathering that recovery isn't going to be an easy option.  At this point I'd not be too sad if we could abandon all my data and turn the computer into a happy dual-boot, or windows-only, or ubuntu-only machine.  The Windows Repair USB had an option under "recovery-management" to restore the system from factory default.  Or is it possible to wipe everything clean and install ubuntu?  

All your help's much appreciated!

---

### Post by oldfred on 2012-02-11
I know there are different Windows repairCD for 32bit & 64bit, but chkdsk can run from any as I have used a Windows 7 repair USB to run chkdsk on my XP install.

If you have backed up all your data, you can just install Ubuntu to the entire drive. Or the Windows vendor recovery is usually just an image of the drive as purchased. Sometime it will not work if the Linux partitions are still on the drive, but it will erase entire drive and restore to as purchased. Again you need to backup your data first.

If partition can be mounted:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by kongluke on 2012-02-11
Great, Boot Repair did the trick!  The computer boots cleanly into windows.  I think I'm going to enjoy this for awhile, but I guess when I feel brave again I can try to install grub (and ubuntu) again, hey?

Many thanks for your help and for sticking with me.

---

### Post by ube17 on 2012-05-07
***
EDIT: See the new post here: [http://ubuntuforums.org/showthread.php?t=1975386]("http://ubuntuforums.org/showthread.php?t=1975386") and reply there.
Forum mod
***

i have same problem, i use windows xp home and ubuntu netbook remix
this is my bootinfoscript
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22  ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1912888 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys 
                       /syslinux/ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x233b233a

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    10,236,050    10,235,988  12 Compaq diagnostics
/dev/sda2     ?    10,236,051    94,124,834    83,888,784   7 NTFS / exFAT / HPFS
/dev/sda3          94,124,835    96,116,894     1,992,060  82 Linux swap / Solaris
/dev/sda4          96,117,019   312,578,594   216,461,576   f W95 Extended (LBA)
/dev/sda5         136,065,321   186,749,387    50,684,067   7 NTFS / exFAT / HPFS
/dev/sda6         186,749,451   312,578,594   125,829,144   7 NTFS / exFAT / HPFS
/dev/sda7          96,117,021   136,054,484    39,937,464  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4018 MB, 4018143232 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1714ece2

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,847,935     7,847,873   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        5430-7D5C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/sr0         /media/XP SP2            iso9660    (ro,nosuid,nodev,uhelper=hal,uid=999,utf8)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default /syslinux/menu.c32
prompt 0
timeout 300
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys
            ?? = ??             syslinux/ldlinux.sys
            ?? = ??             syslinux/menu.c32
            ?? = ??             syslinux/syslinux.cfg
            ?? = ??             syslinux/vesamenu.c32

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4


Unknown BootLoader on sda5


Unknown BootLoader on sda6


Unknown BootLoader on sda7



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```there is no such file or directory, open gparted, partition is unalocated
[IMG]http://cdn-u.kaskus.us/72/whky7ypm.png[/IMG]

but if i open with mini xp on hirens boot cd, my partition is normal
[IMG]http://cdn-u.kaskus.us/72/8lqw98hg.jpg[/IMG]

when i try this command ```
sudo mount /dev/sda7 /mnt
``` and not working
[IMG]http://cdn-u.kaskus.us/72/ajsxzbeu.png[/IMG]

and then, i use live usb ubuntu remix 9.04 and try this [How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 11.10)]("http://ubuntuforums.org/showthread.php?t=1014708") not working
i try [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") but packages are available on ubuntu 10.04 or later
and try [grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") is not available

thanks for your help :smile:

---

### Post by dangmc on 2012-06-25
I just did a fresh install of Ubuntu 12.04-x86_64 with a triple boot system:
/dev/sda=1tb. Western Digital sharing Windows 7 Professional x64 with Ubuntu
/dev/sdb=1tb. Western Digital with Slackware 13.37-x86_64. I repartitioned sda to allow 'root' to have a primary partition then logical for home and swap. I received the same error:no partition, etc. I found that pressing F8 at boot gave me the choice of drives; I switched from 'sdb' as the first boot drive to 'sda' and grub worked normally. I then changed the boot order in 'bios', now boots normally giving choice at boot screen. I should mention that Slackware was installed without a boot loader since it uses Lilo which I'm not familiar with. I'm assuming that I numbered my partitions incorrectly causing my problem. Even though everything is now working I would appreciate any advice as to how to avoid future problems. Thank you

---

