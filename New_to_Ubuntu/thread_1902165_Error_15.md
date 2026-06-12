---
title: "Error 15"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by aoikonom on 2011-12-30
I have a netbook that normally dual boots ubuntu and Windows XP.  Something happened and now during boot "Error 15" is display and boot stops.  The netbook is not mine and I don't know what caused this situation.  Also I don't have much experience with linux.

I boot with a live ubuntu CD and find the following : 

/etc/fstab has

[FONT=Courier New]#<file system> <mount point> <type>  <options>  <dump>  <pass>
proc  /proc   proc   defaults   0      0
# / was on /dev/sda7 during installation
UUID=62a80b49-39fe-4a5f-8d3f-989faibc441e     /       ext3  errors=remount-ro   0   1
/dev/sda6   /media/cdrom0   udf,iso9600   user,noauto, exec,utf8   0   0[/FONT]

I wonder if instead of UUID([FONT=Courier New]62a80b49-39fe-4a5f-8d3f-989faibc441e)[/FONT] there should be /dev/sda7.  This is the partition that Ubuntu normally boots.

/boot has not a subfolder grub.  It has some other files like
[FONT=Courier New]abi-...generic
config...generic
initrd.img...generic
memtest...bin
system.map...generic
vmcoreinfo...generic
vmlinuz...generic[/FONT]

Any ideas on how to fix dual boot as it was?

---

### Post by coffeecat on 2011-12-30
> **aoikonom said:**
> I have a netbook that normally dual boots ubuntu and Windows XP.  Something happened and now during boot "Error 15" is display and boot stops.

Error 15 is an error from legacy grub, which has not been used in Ubuntu for some time. Which version of Ubuntu do you have installed on that netbook? If you are not sure, and since you seem to be able to find your way around with the live CD, have a look at the contents of the /etc/lsb-release file in your sda7 Ubuntu from the live CD. That will tell you.

> **aoikonom said:**
> 
I wonder if instead of UUID([FONT=Courier New]62a80b49-39fe-4a5f-8d3f-989faibc441e)[/FONT] there should be /dev/sda7.  This is the partition that Ubuntu normally boots.

Not necessarily. So long as that quoted UUID is the UUID for sda7, it is better to have a UUID in /etc/fstab.

> **aoikonom said:**
> /boot has not a subfolder grub.

If that is so, then that may be the cause of your problem. The directory /boot/grub contains legacy grub's stage 2 and menu.lst configuration file, without which grub will not work. Do you know what the "something happened" was? The other files you have listed are kernel-associated ones.

Let's have a closer look at your system. Boot up the live Ubuntu CD, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

One last thing. What version of Ubuntu are you running on the live CD?

---

### Post by aoikonom on 2011-12-30
Thanks for the reply.

The version of Ubuntu on the netbook is 9.04 jaunty.

I don't know what happened.  What they told me, they were trying to fix wireless network in WindowsXP.

On the live CD I have Ubuntu 11.10

Output of bootInfoScript is
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => FreeDOS (eXtended FDisk) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    25,167,871    25,165,824  12 Compaq diagnostics
/dev/sda2          25,167,872   207,620,095   182,452,224   7 NTFS / exFAT / HPFS
/dev/sda3         207,624,060   312,576,704   104,952,645   5 Extended
/dev/sda5         207,624,123   211,833,089     4,208,967  82 Linux swap / Solaris
/dev/sda6         211,833,153   222,355,664    10,522,512  1b Hidden W95 FAT32
/dev/sda7    *    222,355,728   312,576,704    90,220,977  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7904 MB, 7904165888 bytes
245 heads, 52 sectors/track, 1211 cylinders, total 15437824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               8,192    15,437,823    15,429,632   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FE647FB7647F70EF                       ntfs       PQSERVICE
/dev/sda2        CE40C52F40C51F59                       ntfs       ACER
/dev/sda5        2066000f-1c1c-46db-96ca-a22cb80a74b4   swap       
/dev/sda6        9B49-2AE4                              vfat       
/dev/sda7        62a80b49-39fe-4a5f-8d3f-989fa1bc441e   ext3       
/dev/sdb1        61B0-B95C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/62a80b49-39fe-4a5f-8d3f-989fa1bc441e ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/61B0-B95C         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

========================= sda6/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default /syslinux/vesamenu.c32
prompt 0
timeout 00
--------------------------------------------------------------------------------

================= sda6: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda6: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=62a80b49-39fe-4a5f-8d3f-989fa1bc441e /               ext3    errors=remount-ro 0       1
/dev/sda6       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/initrd.img-2.6.28-14-generic              3
               =                boot/vmlinuz-2.6.28-14-generic                 2
               =                initrd.img                                     3

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by coffeecat on 2011-12-30
A few points.

The /boot/grub folder is, indeed, missing from the sda7 partition. Fixing a wireless issue in Windows would not have caused this, so what did may remain a mystery. All a bit theoretical because the immediate problem is to get that machine booting again with half of grub missing.

9.04 Jaunty is now end-of-life and unsupported. Re-installing legacy grub in order to restore the /boot/grub folder and contents is theoretically possible, but would be challenging, involving chrooting from a live session and using the old-releases repository. But even if you managed to repair Jaunty's grub, you would still have an obsolete version of Ubuntu which you would not be able to upgrade to a supported one, because the upgrade path from 9.04 is 9.04 -> 9.10 -> 10.04, and 9.10 is also now unsupported.

There are a couple of options to consider:

1 - Use the live CD to rescue any data from sda7 and then do a fresh install of a supported version of Ubuntu, using sda7 as the root partition for the new install. If 11.10 is running OK from the live CD, then it would probably be fine when installed to the hard drive. If you do a fresh installation, you won't have to worry about grub. The installer will install 11.10's grub 2 and set up a dual-boot menu, somewhat as you had before.

2 - If the owner of the netbook needs thinking time, but also needs to boot into Windows in the meantime, this is easily achieved. If you don't have a Windows XP install disk to install the Windows bootloader, this can be done from the Ubuntu live CD.

If you need help with either of the above, post back and we can take it from there.

One oddity from the /etc/fstab in sda7:

```
/dev/sda6       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I'm not sure what's going on there. It looks as though the hidden FAT32 sda6 partition is being mounted as a cdrom. Since sda6 has syslinux in it, this looks to be interesting. Does the netbook owner know what that is about?

---

