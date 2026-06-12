---
title: "New to ubuntu, trouble with TestDisk"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by sarevok89 on 2012-01-11
Hello all, and sorry if this isn't the right thread :S it's not really a "newbie" question

I was trying to dual-boot ubuntu 11.10 (win 7 64bit native) and in my sleep deprived state deleted an "odd looking" partition from my secondary hdd thinking it was a virus. Of course, it was just for some games i'd installed to that drive :redface: but somehow that caused my OS to be completely F###ed to the point that my comp doesn't think there is an OS at all.
I thought it would be no big deal recovering it with testdisk but it hasn't found anything. I did a full search which took several hours but nothing has appeared.
Nothing has been written to the HDD since I deleted the partition (to my knowledge. virus?).

Further info:
- win 7 is installed to an ssd, the partition I deleted was on a secondary hdd. I have 2 hdds and 1 ssd total.
- I keep getting a message in ubuntu "Hard Disk Problems Detected" which pops up about a hundred times in a row, and it says that my SSD is "being used outside design parameters" possibly just because it's an ssd? Or maybe the source of problems?
- Running ubuntu 11.10 from a micro-sd usb, as my optical drives won't appear in bios (partly why I thought I had a virus)
- All 3 internal storage devices are on sata3
- Might be unrelated, but I had to reinstall ubuntu to my sd card after the partition deletion because it randomly stopped working. I had tried booting other comps with it, but it just hung at ubuntu logo boot screen.

At the least, can anyone recommend a different program that might work?
Please help me save my baby!

Specs: i7 2600k @ OC'd, Asrock Extreme6 mobo, nVidia GeForce GTX 570, 4x4gb g.skillz ripjaw, OCZ agility 3 SSD, Seagate baracuda green 2tb, **Seagate baracuda 1tb (has the deleted partition).**

---

### Post by sarevok89 on 2012-01-11
Could any of the issues i've mentioned be the cause of a virus? I'm surprised i'm not getting any feedback at all... :(

---

### Post by oldfred on 2012-01-11
Are you in BIOS/MBR or UEFI/gpt mode? New systems now support UEFI but often are still set up for BIOS. Windows only works in UEFI with gpt. Grub2/Ubuntu works with gpt in BIOS or UEFI.

The new test version of boot script will also parse efi partitions. You need to run from liveCD or USB with Linux.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Standard venison with instructions:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by sarevok89 on 2012-01-11
```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:  Syslinux looks at sector 30502 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2             206,848 1,953,519,615 1,953,312,768   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   117,227,519   117,225,472   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 3,497,426,943 3,497,424,896   7 NTFS / exFAT / HPFS
/dev/sdc2       3,497,430,825 3,907,024,064   409,593,240   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          8,192     7,837,695     7,829,504   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        30A40F32A40EF9DC                       ntfs       Software
/dev/sdb1        62B40F5BB40F30D9                       ntfs       
/dev/sdc1        CA3E5AC13E5AA66B                       ntfs       Media
/dev/sdc2        4D05174D109717ED                       ntfs       Ubuntu
/dev/sdd1        1D17-2D35                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc2        /media/Ubuntu            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdd1/boot/grub/grub.cfg: ===========================

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

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)



```

---

### Post by sarevok89 on 2012-01-11
I made sure no drives were mounted or in any way in use, don't know why it's saying that "sdb1" is, it's my ssd.

---

### Post by sarevok89 on 2012-01-11
I should have noted earlier that when I deleted the partition, I was using ubuntu's disk utility.

---

### Post by sarevok89 on 2012-01-12
So I guess a fresh install is my only option then...

---

### Post by oldfred on 2012-01-12
The script and Linux will not mount NTFS partitions that need chkdsk to prevent further damage that chkdsk then might not be able to fix. That is the most common reason it does not get mounted.

I might try chkdsk on sdb1. Not sure if there are any issues with chkdsk on SSDs as opposed to standard hard drives.

---

