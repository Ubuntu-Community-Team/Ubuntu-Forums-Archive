---
title: "Disk Computer wont boot Win 8.1 or linux is Cant find Grub2 di"
date: 2015-04-30
forum: New to Ubuntu
---

### Post by lambertrj on 2015-04-30
[B]Hi from Calgary canada and thanks for reading!!!!!!
[/B]
I have been using linux for a few days along with win 8.1.

I restarted from windows and the computer booted into grub2 as normal however now no OS shows up  start and I cant boot into either os.

Using and booting the live linux usb boot-repair-disk did nothing to repair window or linux..I noted that the boot-repair advance options to located the GRUB  are blank could grub be broken?

My results from boot repair where.

[http://paste.ubuntu.com/10958098/](http://paste.ubuntu.com/10958098/)

I also ran bootinfoscrip with the following results. 





                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/MokManager.efi /efi/ubuntu/shimx64.efi

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07
    Boot sector info:  Syslinux looks at sector 32800 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,333,247     1,331,200 Windows Recovery Environment (Windows)
/dev/sda2       1,333,248     1,865,727       532,480 EFI System partition
/dev/sda3       1,865,728     2,127,871       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       2,127,872 1,361,205,247 1,359,077,376 Data partition (Windows/Linux)
/dev/sda5   1,361,205,248 1,423,288,319    62,083,072 Data partition (Windows/Linux)
/dev/sda6   1,423,290,368 1,465,137,151    41,846,784 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 32.3 GB, 32254197760 bytes
255 heads, 63 sectors/track, 3921 cylinders, total 62996480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    62,996,479    62,994,432   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C82ACE6F2ACE59D8                       ntfs       WINRE
/dev/sda2        E05E-DA7C                              vfat       
/dev/sda4        C26E4E896E4E7667                       ntfs       Windows
/dev/sda5        1CCC3E07CC3DDC28                       ntfs       
/dev/sda6        6E02CA9302CA5FA7                       ntfs       RECOVERY
/dev/sdb1        8A09-9327                              vfat       BOOT-REPAIR
/dev/zram0       fd95e28a-9291-4e72-b473-fba13f78a998   swap       
/dev/zram1       136d74fc-2e7b-4207-81b6-cfe36f774574   swap       
/dev/zram2       7812cc28-7656-448c-9e27-a3a1535bdc4c   swap       
/dev/zram3       101176a7-9e49-4ad6-8480-157b808e66c3   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 58 14 00  |........?....X..|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 7c da 5e e0 4e  4f 20 4e 41 4d 45 20 20  |..)|.^.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-qhYbLrGv/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-qhYbLrGv/Tmp_Log: No such file or directory
  No volume groups found



```


Im not sure what to do now. Thanks!!!

---

### Post by oldfred on 2015-04-30
You show no Linux partitions?
But you do show Ubuntu as an UEFI boot option.

And the efi partition now does not show any Windows efi boot files or folders? Sometimes script has not correctly shown them, are they really there?

Boot-Repair cannot fix Windows, you need your Windows repair flash drive to restore Windows efi boot files to efi partition.
And you need your Linux partition to be able to boot Ubuntu. Did it somehow from Windows get changed to NTFS?

       Windows 8 UEFI fixes
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html](http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html)

---

### Post by lambertrj on 2015-05-01
Ok, thanks so much for your help, While my window os was shuting down it was updating 1 update, I have no idea perhaps unfortunatly the partision was changed, would that mean it was formated if it was altered?

---

