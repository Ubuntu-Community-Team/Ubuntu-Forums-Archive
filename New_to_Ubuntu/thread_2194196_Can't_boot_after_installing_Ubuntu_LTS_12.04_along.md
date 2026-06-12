---
title: "Can't boot after installing Ubuntu LTS 12.04 alongside Windows 8."
date: 2013-12-17
forum: New to Ubuntu
---

### Post by sinagz23 on 2013-12-17
Hello, I'm new to Ubuntu. After installing the Ubuntu LTS from a LiveUSB, only the GRUB Minimal Bash-like is showing on start up. I've created separate partitions for Ubuntu as stated by a guide. I've googled the problem but it seems like it's a case-to-case basis since each of the users are posting the results of their bootinfoscript. I don't want to lose data although I've already backed up the important ones. So, I'm seeking your expert advice. Thank you very much in advance.

Here's my bootinfoscript result:

                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 745090 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       (,msdos5)/grub on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.3 LTS
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 32808 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2             720,894   168,491,007   167,770,114   5 Extended
/dev/sda5             720,896     1,206,271       485,376  83 Linux
/dev/sda6           1,208,320    30,502,911    29,294,592  83 Linux
/dev/sda7          30,504,960    62,484,479    31,979,520  82 Linux swap / Solaris
/dev/sda8          62,486,528   168,491,007   106,004,480  83 Linux
/dev/sda3         168,491,008   420,149,247   251,658,240   7 NTFS / exFAT / HPFS
/dev/sda4         420,149,248 1,465,145,343 1,044,996,096   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8094 MB, 8094842880 bytes
255 heads, 63 sectors/track, 984 cylinders, total 15810240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,810,239    15,810,177   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        18E27DD1E27DB41A                       ntfs       System Reserved
/dev/sda3        8A3EEA7D3EEA61A5                       ntfs       
/dev/sda4        46B015FDB015F3E1                       ntfs       
/dev/sda5        0f2824c6-90aa-4ddf-b37b-c7064baed5e5   ext4       
/dev/sda6        d540ed0b-62ee-487a-aebe-2ce2c79a1746   ext4       
/dev/sda7        fc15bbaa-edc7-4432-820c-934a001eece2   swap       
/dev/sda8        917d6878-96b2-414a-9fe5-a4d96dfe0cb5   ext4       
/dev/sdb1        D047-C37B                              vfat       UUI

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda5/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initrd.img-3.8.0-29-generic                    3
               =                vmlinuz-3.8.0-29-generic                       2
               =                vmlinuz-3.8.0-29-generic.efi.signed            1

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=d540ed0b-62ee-487a-aebe-2ce2c79a1746 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
#UUID=0f2824c6-90aa-4ddf-b37b-c7064baed5e5 /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=917d6878-96b2-414a-9fe5-a4d96dfe0cb5 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=fc15bbaa-edc7-4432-820c-934a001eece2 none            swap    sw              0       0
#UUID=0f2824c6-90aa-4ddf-b37b-c7064baed5e5    /boot    ext4    defaults    0    2
UUID=0f2824c6-90aa-4ddf-b37b-c7064baed5e5    /boot    ext4    defaults    0    2
--------------------------------------------------------------------------------

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

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
```

---

### Post by alankon on 2013-12-17
Hi,

Welcome to Ubuntu! I had a very similar problem to this when I first tried to dual-boot on a Win8 machine... and I found the problem was resolved simply by restoring the BIOS (UEFI) to the factory default setting, then disabling the "Fast Boot" option.

May sound too simple... but worth a try!?

---

### Post by sinagz23 on 2013-12-17
Hello alankon, thanks for taking time to respond. The fast boot option is already disabled when I installed Ubuntu. I just restored the Settings to default like you said but the Minimal bash like thingy is still loading on start - up.

---

### Post by oldfred on 2013-12-17
Is it grub that is not booting or since it does not look like grub found Windows yet, you may be into booting kernel as it will not show grub menu if only one system shown. Then it could be video issue or other boot parameters.

If you can get to terminal and login?
sudo update-grub

Can you hold shift key down from BIOS until a menu appears?  You can try recovery mode boot or second line.
Or from first line add nomodeset boot option.
Then use e for edit scroll to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by sinagz23 on 2013-12-17
Hi oldfred, thanks for replying. I'll try your suggestions. 
Here's what it looks like when I turn on the PC as of the moment: 

[IMG]http://members.iinet.net.au/~herman546/p15/fig2grub.gif[/IMG]

---

### Post by plurga on 2013-12-17
hi sinagz23 , 
according the error u are facing u could try with this tool "Boot Repair".

---

### Post by sinagz23 on 2013-12-17
I actually tried Boot Repair thrice already, but I'm surprised it worked this 4th time. Thank you very much alankon, oldfred, and plurga for guiding me to the solution. I really appreciate it. Because of you, I may now start my journey with Ubuntu. Cheers! :guitar:

[IMG]http://www.indusladies.com/forums/attachments/ilite-milestones/197183d1381183377t-welcoming-sister-bhargavi-knbg-into-thank-you-word-cloud-1024x791.jpg[/IMG]

---

