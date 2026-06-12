---
title: "external hard disk -boot partitioning !!!"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by amrosama77 on 2012-08-15
Hello All,

now I have my pc with win 7, for my work reasons I can't make any changes in boot or system to it,

so I have an external 1TB hard disk,

my 1st question is: can I make 100G partition and install bootable ubuntu 12 on it, how the system will boot from a specific partition in my external hard?

my 2nd question is: can I make 2 partitions each is 100G and install bootable ubutn 12 on 1 partition and install bootable debin on the other ?
as I want to test both of them, if this possible so how could I boot from ubntu partition or debin partion ...!!!...???

Thank you so much,

---

### Post by Mark Phelps on 2012-08-15
IF you have ONLY the external disk connected when you install Ubuntu, it will automatically install GRUB to that disk, thus rendering it bootable.

Whether or not it will then boot depends on your PC booting from external drives.  The typical boot entry for this in PC BIOS settings is USB-HDD.

---

### Post by oldfred on 2012-08-15
You have to use manual install to get the option on which drive's MBR to install the grub2 boot loader into. All the auto install options default to sda which will normally be your internal drive, if that is still connected.

You also do not need 100GB. I have multiple Ubuntu installs each in 25GB  with 5 to 8GB used. But I put all data in two 100GB data partitions. One data  partition is shared and is formated NTFS from when I still booted XP. And the other is ext3 (I would use ext4 now) for data. Then the shared NTFS I can see from all installs including Windows and the other from most LInux installs although some distributions may have UID & GID issues.

Installer has not changed much so these instructions and screenshots are pretty close to what you should see.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select which drive's MBR to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

[http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/](http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/)

On my system a full install of Ubuntu onto a USB flash drive is seen as a hard drive in the boot choices from BIOS, not any of the USB choices.

---

### Post by amrosama77 on 2012-08-15
Thank you oldfred,
for your great detailed answer,
 
so I think I need more than 25G as I will install softwares (may be some games) via software center (I asked in the other thread about how to detirmin the location of installed applications but no one answer me)
 
>>>>And the other is ext3 (I would use ext4 now) 
 
why I didn't just use NTFS for all partiotions ...?, so I keep all my hard disk with same file format system,
or it will be more faster for ubuntu to be ext4?
 
thank you,

---

### Post by oldfred on 2012-08-15
All Linux system partitions have to be LInux formats not Windows formats. But you can use just about anything for data. The Linux formats support ownership & permissions and with NTFS you then just get defaults that you can set when mounting the NTFS partition. The use of ownership & permissions is part of why Linux is more secure than Windows and allows better security in a multi-user environment. Linux will automatically run fsck periodically on its Linux partitions, but cannot on NTFS. Windows waits until it stops working then you have to run chkdsk, but only can do that from a Windows install or if major issues with Windows from a Windows repairCD/USB.

Applications have different parts all over the place normally. But some like java or python can be stand alone applications that can be just about anywhere. Not sure about most games or how they install or integrate into the system.

Explanation of file structure
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)
Some real old history:
[http://lists.busybox.net/pipermail/busybox/2010-December/074114.html](http://lists.busybox.net/pipermail/busybox/2010-December/074114.html)

---

### Post by amrosama77 on 2012-08-16
I go with the process upon your great links,

at the last step I got the error of can't install boot loader, so I choose to continue the installation without boot loader, I though to install let manually later

after installation finish I restart my pc and remove the external hard to be sure the my win7 is okay, :(
but it didn't work and I got this >>>
error: no such dervice f937b5b6-0acd-4754-9124-00f5d02755d3
grub rescure>

:(
I restared and attached the external hard and try to boot from it
and this what I got:

black screen with blinking cursor without ability to write !!!!!!!


PLEASE HEEEEEEEEEEEEELP

---

### Post by oldfred on 2012-08-16
It seems grub2 installed its boot loader to the MBR of the internal as well as the external.

You should reinstall the Windows boot loader to the internal. You can use Windows or from Linux install syslinux or lilo which work exactly like the Windows in the MBR (not full boot loaders, just MBR bit of code).

What video card? do you have? And during install did you tick install optional proprietary drivers. That would install video drivers.

If you hold shift key down from BIOS, do you then get a grub menu?

I have nVidia and have to use nomodeset on liveCD and first boot until I install the proprietary nVidia driver.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

From a Windows repair or full install CD/DVD
How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub

Or the LInux work alike boot loader: This fixes most boot issues, but I think you actually are booting and past boot issues and just have a video issue.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by amrosama77 on 2012-08-16
Thank you for helping me,
But I was very clear that I want the installation to be on my external 1T hard not internal !!!
 
>>>You should reinstall the Windows boot loader to the internal. You can use Windows or from Linux install syslinux or lilo which work exactly like the Windows in the MBR (not full boot loaders, just MBR bit of code).

how to do this ...?
 
I think my video card is ATI, no I didn't install the extra drivers during the installation
but I don't think my vedio card have problem with ubuntu as I have flash drive with ubutu on it,
 
I will try to use boot repaire and see :confused:

---

### Post by oldfred on 2012-08-16
When you used the manual install, at the partitioning screen did you say to install grub2's boot loader to the external drive. It is a combo box listing drives (and partitions which you should not use). That has always worked for me, except the time I zoomed thru the install and skipped that step.

Boot repair should work. If you want post the BootInfo report it creates.

The liveCD usually uses the lowest level default video drivers to work with most systems. But for whatever reason the install does not have the same configuration and added settings are often needed. I do not know ATI, so I am not sure what settings may be best.

Not sure how current some of these links are. If you cannot resolve video issue, it would be better to start another thread with ATI & model in the title so those with ATI can help.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

---

### Post by amrosama77 on 2012-08-16
from my understanding when I ask to install on hard disk which didn't have any system (my external) so by default it must be bootable (also as I mention before at the end of the installation there was an error regarding the booting where I choose to install without booting)
so why the win7 boot changed !!!

more details:
I partition 2 partitions 50GB (/) 5GB (linux swap )
is it must to make partition with (/boot) selection ?!!

I will check boot repair and let you know, thank you,

---

### Post by oldfred on 2012-08-16
If / (root) is only 50GB, you should not need another partition for /boot.

Post BootInfo from Boot-Repair.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

But you may also have the video issues.

---

### Post by amrosama77 on 2012-08-16
:guitar: thank you, now my windows is back, boot repair

here is the report >> [http://paste.ubuntu.com/1151809/](http://paste.ubuntu.com/1151809/)

after that I attached my external hard disk 
and run the boot repair again 
and here is the report
[http://paste.ubuntu.com/1151815/](http://paste.ubuntu.com/1151815/)

Note: when boot repair ask me if my external hard is external or not I said not (I thought this will let the program repair the boot for it)

I didn't restart yet, I hope my external will work 

wish me luck

---

### Post by amrosama77 on 2012-08-16
Now,
I have the following situation

when I remove my external hard and restart I see the error message and guru rescur prompet then no windows loading at all

when I connect my external I see the boot menu with option for ubuntu which works fine, and option for my windows which work fine too,

so how could I do what I want now ...?

when I open my lab without the external I just see/run my windows
and when I attache the external and open the lab I see/run my ubuntu
:confused:

note: now I am happy that both systems running but not happy as my windows depend on the external hard !!!

---

### Post by oldfred on 2012-08-16
You installed the grub boot loader to the external, but  you had the Windows boot loader in the sda. But then you also installed grub2's boot loader to the internal. The grub on the internal has to find the grub files in the Ubuntu partition on the external to give you the boot menu, so that is why external has to be connected.

You want the Windows like bootloader - syslinux in the MBR of the internal drive, And you want grub2' boot loader in the MBR of the external. Then you set BIOS to boot external first and internal second. Then if external is connected, you get grub menu to boot either Ubuntu or Windows. If you disconnect external, then BIOS will find the internal drive & boot from it.

I think if you had told Boot-Repair that external was removeable external then it would have correctly installed in the first place.

It also reports another issue, your sda is wrong, run fixparts to correct it:
> Error: Can't have a partition outside the disk!

First backup partition table.
sudo sfdisk -d /dev/sda > parts_sda.txt

Fixparts - Repair broken partition tables (not overlapping issues) 
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by YannBuntu on 2012-08-17
Hello

> **amrosama77 said:**
> Note: when boot repair ask me if my external hard is external or not I said not

Why ????
As your external disk is removable, just answer yes! Then please indicate the new URL that will appear.

---

### Post by amrosama77 on 2012-08-17
I did
and here is the report

[http://paste.ubuntu.com/1152445/](http://paste.ubuntu.com/1152445/)

I will restart and see what is the case now

Thank you,

---

### Post by YannBuntu on 2012-08-17
ok (Your Windows partition is 99% full, you may need to remove some useless files from it. If Windows fails booting, you may also need to run again the Recommended repair, after disconnecting the external drive.)

---

### Post by amrosama77 on 2012-08-17
Yes
:KS
Now when I open my lab without external attached my windows run without any ubuntu menu

and when I attache the external I see the ubuntu start up menu with ability to run ubuntu or win7

Thank you all for helping me out,

:D

---

### Post by YannBuntu on 2012-08-17
Great ! :popcorn:
For my information, please could you indicate your current [Boot-Info URL]("https://help.ubuntu.com/community/Boot-Info") (this won't change your boot).

---

### Post by oldfred on 2012-08-17
Glad booting is straighten out.

But you still show partition error and need to run fixparts.


Also Windows really likes 30% free space in NTFS partitons. At 10% free it just about stops working as it does not have the space to write/rewrite sectors that it needs. LInux hides 5% just to be on the safe side, but still needs some extra room.

---

### Post by amrosama77 on 2012-08-17
No problem for the windows partition I will free a lot of space

but what other error do I have :confused:

I thought every thing is okay now

---

### Post by oldfred on 2012-08-17
See part 2 of post #14. It shows your partition ending after the last sector on the drive. Many tools stop working when you have an error like that. 

Windows partition boot sector - PBR also has to have correct information in it as to start and size of partition similar to partition table. Boot script is also report an error there. Run fixparts first to correct partition size. Then you may need to run chkdsk, fixboot and then chkdsk again from Windows.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r

---

### Post by amrosama77 on 2012-08-18
I free a lot of space and re-run the boot repair and here is the report>>>>>>>>>>>>>>

   ```
Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       1250054143 sectors, but according to the info from 
                       fdisk, it has 1250067841 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,250,274,689 1,250,067,842   7 NTFS / exFAT / HPFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    97,656,831    97,654,784  83 Linux
/dev/sdb2          97,658,878   107,421,695     9,762,818   5 Extended
/dev/sdb5          97,658,880   107,421,695     9,762,816  82 Linux swap / Solaris
/dev/sdb3         107,421,696 1,953,523,711 1,846,102,016   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0050F14D50F14A44                       ntfs       System Reserved
/dev/sda2        309AFD059AFCC87C                       ntfs       
/dev/sdb1        f937b5b6-0ac0-4754-9124-00f5d02755d3   ext4       
/dev/sdb3        3F21E4071A753949                       ntfs       
/dev/sdb5        5463df7e-58f8-423d-b37b-3de5e0ed5265   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb3        /media/3F21E4071A753949  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root f937b5b6-0ac0-4754-9124-00f5d02755d3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root f937b5b6-0ac0-4754-9124-00f5d02755d3
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f937b5b6-0ac0-4754-9124-00f5d02755d3
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=f937b5b6-0ac0-4754-9124-00f5d02755d3 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f937b5b6-0ac0-4754-9124-00f5d02755d3
    echo    'Loading Linux 3.2.0-29-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=f937b5b6-0ac0-4754-9124-00f5d02755d3 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f937b5b6-0ac0-4754-9124-00f5d02755d3
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=f937b5b6-0ac0-4754-9124-00f5d02755d3 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f937b5b6-0ac0-4754-9124-00f5d02755d3
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=f937b5b6-0ac0-4754-9124-00f5d02755d3 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f937b5b6-0ac0-4754-9124-00f5d02755d3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f937b5b6-0ac0-4754-9124-00f5d02755d3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0050F14D50F14A44
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 309AFD059AFCC87C
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=f937b5b6-0ac0-4754-9124-00f5d02755d3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5463df7e-58f8-423d-b37b-3de5e0ed5265 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  38.201229095 = 41.018257408   boot/grub/core.img                             1
  34.127220154 = 36.643823616   boot/grub/grub.cfg                             1
  34.980270386 = 37.559779328   boot/initrd.img-3.2.0-23-generic-pae           2
  45.513008118 = 48.869220352   boot/initrd.img-3.2.0-29-generic-pae           2
   0.429477692 = 0.461148160    boot/vmlinuz-3.2.0-23-generic-pae              1
  34.806427002 = 37.373116416   boot/vmlinuz-3.2.0-29-generic-pae              1
  34.980270386 = 37.559779328   initrd.img                                     2
  34.980270386 = 37.559779328   initrd.img.old                                 2
   0.429477692 = 0.461148160    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  a6 c3 80 ba 3d 77 df 68  75 6a bd dd fa 03 71 08  |....=w.huj....q.|
00000010  bc 24 39 55 ad c4 8f d2  bd 17 06 8d 6f 3f 24 bf  |.$9U........o?$.|
00000020  0b 2f 49 65 f4 31 be 88  69 11 4f 7f a4 a0 64 06  |./Ie.1..i.O...d.|
00000030  01 a1 25 04 5f 22 a8 4f  cb 5b b8 15 26 9c 72 e4  |..%._".O.[..&.r.|
00000040  8a 42 d2 ec 7e c4 59 31  f6 82 c1 32 4e a1 9e da  |.B..~.Y1...2N...|
00000050  23 42 8c 4d 9d 2f b1 dc  8f de a6 82 b3 dd f4 aa  |#B.M./..........|
00000060  81 a7 c0 0b 79 5e 0c 57  01 04 8a ee 7a 39 46 8f  |....y^.W....z9F.|
00000070  1e f4 1a 04 0f 54 16 74  0b 84 31 c7 7f 5e 24 76  |.....T.t..1..^$v|
00000080  10 b3 d4 f3 11 63 38 6e  cc 54 4e a5 7c d8 85 02  |.....c8n.TN.|...|
00000090  93 70 7c 98 e2 1a 9f 63  48 a9 f0 01 b7 aa 40 a5  |.p|....cH.....@.|
000000a0  26 c8 ed 61 2b 72 a1 8e  ea ed 32 d6 28 21 fa e6  |&..a+r....2.(!..|
000000b0  d4 b6 d6 5b 06 a9 fe e3  13 9c f1 3f 15 61 47 7b  |...[.......?.aG{|
000000c0  05 39 d5 1b e2 49 99 aa  e3 7a e0 4b 15 d5 af 1a  |.9...I...z.K....|
000000d0  ad cc 64 92 36 8d d8 b5  6c 67 6a 6b 56 7d ac 76  |..d.6...lgjkV}.v|
000000e0  96 63 e2 c7 d7 e7 86 68  b9 42 6f 5d 0b 1a 00 f1  |.c.....h.Bo]....|
000000f0  5d db 33 bf 78 3d e9 b0  08 d3 73 77 53 90 2f f2  |].3.x=....swS./.|
00000100  8a 91 b2 6f 42 9c 39 10  91 5b 85 59 e8 08 70 8d  |...oB.9..[.Y..p.|
00000110  2b 99 5d 79 80 d2 5d 0d  5a 23 c2 7d c6 ca a2 22  |+.]y..].Z#.}..."|
00000120  1f 89 42 5b c8 fd a9 0f  3f cd 9d d8 22 ff 6b 7e  |..B[....?...".k~|
00000130  09 43 36 e8 73 9a 0f a5  e8 f0 18 c1 e1 f4 2a 5b  |.C6.s.........*[|
00000140  e9 a2 65 9c 67 02 e9 85  02 00 50 e6 12 7a 88 eb  |..e.g.....P..z..|
00000150  2a 3d 8d 9c 30 da 23 58  6d ad 74 17 60 77 46 bc  |*=..0.#Xm.t.`wF.|
00000160  44 6b 39 d5 92 cd a8 79  13 79 fc d6 e1 43 a2 a4  |Dk9....y.y...C..|
00000170  91 11 d8 bd a1 f6 b3 0f  ed 83 4c 53 18 60 2a f8  |..........LS.`*.|
00000180  bf e6 05 69 35 8f 91 05  98 f3 81 c4 b6 fc d5 91  |...i5...........|
00000190  02 8a c7 47 02 e7 3b 4e  25 0c 38 a3 b5 8d 9e 9d  |...G..;N%.8.....|
000001a0  5b 2b 0c d4 ca e3 c4 a0  84 5f 01 45 76 de da 7d  |[+......._.Ev..}|
000001b0  1a e1 cc 24 07 ae 0b 1e  6d 65 ba c4 4e c3 00 fe  |...$....me..N...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 94 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-08-18__05h31 ===================
boot-repair version : 3.18-0ppa47~precise
boot-sav version : 3.192-0ppa5~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-sav-nonfree version : 3.18-0ppa10~precise

The following packages were automatically installed and are no longer required:
language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
language-pack-zh-hans-base firefox-locale-zh-hans
language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 4 not upgraded.
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
boot-repair is executed in installed-session (Ubuntu 12.04.1 LTS, precise, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sdb1:The OS now in use - Ubuntu 12.04.1 LTS CurrentSession:linux
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain

=================== blkid:
/dev/sda1: LABEL="System Reserved" UUID="0050F14D50F14A44" TYPE="ntfs"
/dev/sda2: UUID="309AFD059AFCC87C" TYPE="ntfs"
/dev/sdb1: UUID="f937b5b6-0ac0-4754-9124-00f5d02755d3" TYPE="ext4"
/dev/sdb3: UUID="3F21E4071A753949" TYPE="ntfs"
/dev/sdb5: UUID="5463df7e-58f8-423d-b37b-3de5e0ed5265" TYPE="swap"


2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Aug 18 03:18 grub.d
total 56
-rwxr-xr-x 1 root root 6715 Apr 17 20:16 00_header
-rwxr-xr-x 1 root root 5522 Apr 17 19:53 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17 09:22 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17 20:16 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17 20:16 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17 20:16 40_custom
-rwxr-xr-x 1 root root   95 Apr 17 20:16 41_custom
-rw-r--r-- 1 root root  483 Apr 17 20:16 README




=================== dmesg | grep EFI :
This installed-session is not EFI-compatible.
[    1.525680] EFI Variables Facility v0.08 2004-May-17



=================== PARTITIONS & DISKS:
sdb1    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sdb3    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/3F21E4071A753949.

sdb    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    2048 sectors * 512 bytes
sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    2048 sectors * 512 bytes

=================== parted -l:


                                                                          
Error: Can't have a partition outside the disk!

Model: Toshiba External USB HDD (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  50.0GB  50.0GB  primary   ext4            boot
2      50.0GB  55.0GB  4999MB  extended
5      50.0GB  55.0GB  4999MB  logical   linux-swap(v1)
3      55.0GB  1000GB  945GB   primary   ntfs


=================== mount:
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/amr/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=amr)
/dev/sdb3 on /media/3F21E4071A753949 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb5 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fb1 fd full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdb2 sdb3 sdb5 sdc sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 v4l vga_arbiter video0 zero
ls /dev/mapper:  control
ls: cannot access : No such file or directory
ls /mnt/boot-sav/sda2: Windows Users Information Volume System swsetup Reminder.mdb $Recycle.Bin Recovery (x86) Files Program Files Program ProgramData PerfLogs pagefile.sys CD on CD on Not MSOCache Amr Mohamed Intel Drivers HP HP Shield Hotspot hiberfil.sys Settings and Documents CyberNetNews.com_Windows_7_64-bit_Repair_Disc.iso boot-sav bootmgr Boot Tera 1

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb1      ext4       47G  5.2G   39G  12% /
udev           devtmpfs  3.0G   12K  3.0G   1% /dev
tmpfs          tmpfs     1.2G  884K  1.2G   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.0G  548K  3.0G   1% /run/shm
/dev/sdb3      fuseblk   881G  463G  418G  53% /media/3F21E4071A753949
/dev/sda1      fuseblk   100M   25M   76M  25% /mnt/boot-sav/sda1
/dev/sda2      fuseblk   597G  187G  410G  32% /mnt/boot-sav/sda2

=================== fdisk -l:

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000341a6

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1250274689   625033921    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054f20

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    97656831    48827392   83  Linux
/dev/sdb2        97658878   107421695     4881409    5  Extended
/dev/sdb3       107421696  1953523711   923051008    7  HPFS/NTFS/exFAT
/dev/sdb5        97658880   107421695     4881408   82  Linux swap / Solaris


User choice: Is sdb (1000GB) a removable disk? yes
Partition outside the disk detected.

=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sdb1 into the MBR of sdb.
It will also fix access to other systems (other MBRs) for the situations when the removable media is disconnected.
Additional repair will be performed: unhide-bootmenu-10s


sdb is removable, so we reinstall GRUB of the removable media only in its disk MBR
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 2 boot on

                                                                          
Error: Can't have a partition outside the disk!
parted /dev/sda set 1 boot off

                                                                          
Error: Can't have a partition outside the disk!

Reinstall the GRUB of sdb1 into the MBR of sdb
grub-install (GRUB) 1.99-21ubuntu3.1
grub-install --recheck /dev/sdb: Installation finished. No error reported.
exit code of grub-install /dev/sdb:0

update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Unhide GRUB boot menu in sdb1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on the removable disk!
```

---

### Post by oldfred on 2012-08-18
You still have these two errors. 

```
sda2: __________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  [COLOR=Red]According to the info in the boot sector, sda2 has 
                       1250054143 sectors, but according to the info from 
                       fdisk, it has 1250067841 sectors.[/COLOR]
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

```
```
Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total [COLOR=Red]1250263728[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 [COLOR=Red]1,250,274,689[/COLOR] 1,250,067,842   7 NTFS / exFAT / HPFS

/dev/sda2 ends after the last sector of /dev/sda

```

1,250,274,689 > 1,250,263,728

---

### Post by amrosama77 on 2012-08-18
thank you for the spot but any advice to fix it...?
:D

---

### Post by oldfred on 2012-08-18
Post #14 use fixparts from a LInux liveCD.

Post #19 use a Windows repair CD to fix the PBR.

---

### Post by amrosama77 on 2012-08-18
replay on post #14

I re-run and told that my external is external hard and now I don't need to attache the external every time I turn on the lab, unless I need the ubuntu, in this case it didn't show the ubuntu start up men and open windows directly without any menues (and I am happy with this)

for the other post which is related to windows fix disk, actually I don't trust any fix related to windows as I try them many times in many cases and they never helped me out :)

so I am in very bad situation now :)

as I see my self in great case ,but let me know if I am dreaming or something
:lolflag:

---

### Post by amrosama77 on 2012-08-18
I also now able to hibernate my ubuntu then de-attache the external then open my win7,

then attache my external and restart and I on ubuntu after resuming from hibernating 

(this is like a dream for me man)

:guitar:

---

### Post by amrosama77 on 2012-08-22
Am I able to make 40G partition and install debain on it? :D

if yes ,how?

---

### Post by oldfred on 2012-08-22
Yes, on which drive? And did you do the fixes, or gparted may not show drives.

On your 1TB drive you have NTFS taking up all of the end of the drive. You will have to defrag from Windows and shrink it. Then move it right in gparted from a liveCD so it is unmounted. You may have to click on swap and right click swap off to unmount swap. If unallocated is then at the end of the extended partition move the extended right and create a new partition in that space. If you think you may want other partitions now would be a good time to shrink the NTFS even more than the 40GB and move it further right.

You need good backups as any power failure or interruption will corrupt partitions. Do each task, do not queue them in gparted.

---

### Post by amrosama77 on 2012-08-22
humm thank you so much, I will try to do it

---

