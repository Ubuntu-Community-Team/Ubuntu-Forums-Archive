---
title: "Can't boot into XP"
date: 2009-01-14
forum: Other OS Talk
---

### Post by Hyper Tails on 2009-01-14
Hi I have xp/vista/7 and ubuntu on my laptop and I reinstalled grub and since then I can't boot into xp

I'l load into and after 1 second the hardrive does nothing at all

Please Help!!

---

### Post by caljohnsmith on 2009-01-14
In order to get a clearer picture of your setup related to your Windows booting problem, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by Hyper Tails on 2009-01-14
here it is```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM /Boot

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb570b9c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2        81915904   118783999    18434048    7  HPFS/NTFS
/dev/sda3       118784610   312576704    96896047+   f  W95 Ext'd (LBA)
/dev/sda5       118784673   218500064    49857696    7  HPFS/NTFS
/dev/sda6       218773233   312576704    46901736   83  Linux

sfdisk -V /dev/sda:

Warning: partition 2 does not start at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 2073 MB, 2073559040 bytes
2 heads, 63 sectors/track, 32142 cylinders, total 4049920 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x024f188e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     4049919     2024944    6  FAT16

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9884AC6784AC4A18" TYPE="ntfs" 
/dev/sda2: UUID="76A042D7A0429E0D" TYPE="ntfs" 
/dev/sda5: UUID="7E349C54349C116F" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda6: UUID="9f3c25ee-7422-4855-9be6-ccf9b216a97a" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DISK_IMG" UUID="024F-188E" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/liam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=liam)
/dev/sdb1 on /media/DISK_IMG type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="" 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

================================== sda1/Boot: ==================================

total 860
drwxrwxrwx 1 root root   4096 2009-01-13 01:07 .
drwxrwxrwx 1 root root   8192 2009-01-14 17:55 ..
-rwxrwxrwx 1 root root  40960 2009-01-14 17:59 BCD
-rwxrwxrwx 2 root root  24576 2008-12-29 22:49 BCD.Backup.0001
-rwxrwxrwx 1 root root 262144 2009-01-14 17:56 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-12-29 21:09 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-12-29 21:09 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-13 01:07 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-13 01:07 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-13 01:07 da-DK
drwxrwxrwx 1 root root      0 2009-01-13 01:07 de-DE
drwxrwxrwx 1 root root      0 2009-01-13 01:07 el-GR
drwxrwxrwx 1 root root      0 2009-01-13 01:07 en-US
drwxrwxrwx 1 root root      0 2009-01-13 01:07 es-ES
drwxrwxrwx 1 root root      0 2009-01-13 01:07 fi-FI
drwxrwxrwx 1 root root      0 2009-01-13 01:07 Fonts
drwxrwxrwx 1 root root      0 2009-01-13 01:07 fr-FR
drwxrwxrwx 1 root root      0 2009-01-13 01:07 hu-HU
drwxrwxrwx 1 root root      0 2009-01-13 01:07 it-IT
drwxrwxrwx 1 root root      0 2009-01-13 01:07 ja-JP
drwxrwxrwx 1 root root      0 2009-01-13 01:07 ko-KR
-rwxrwxrwx 1 root root 473864 2008-12-13 03:31 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-13 01:07 nb-NO
drwxrwxrwx 1 root root      0 2009-01-13 01:07 nl-NL
drwxrwxrwx 1 root root      0 2009-01-13 01:07 pl-PL
drwxrwxrwx 1 root root      0 2009-01-13 01:07 pt-BR
drwxrwxrwx 1 root root      0 2009-01-13 01:07 pt-PT
drwxrwxrwx 1 root root      0 2009-01-13 01:07 ru-RU
drwxrwxrwx 1 root root      0 2009-01-13 01:07 sv-SE
drwxrwxrwx 1 root root      0 2009-01-13 01:07 tr-TR
drwxrwxrwx 1 root root      0 2009-01-13 01:07 zh-CN
drwxrwxrwx 1 root root      0 2009-01-13 01:07 zh-HK
drwxrwxrwx 1 root root      0 2009-01-13 01:07 zh-TW

=========================== sda6/boot/grub/menu.lst: ===========================

default 0
timeout 10

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9f3c25ee-7422-4855-9be6-ccf9b216a97a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f3c25ee-7422-4855-9be6-ccf9b216a97a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=9f3c25ee-7422-4855-9be6-ccf9b216a97a ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=9f3c25ee-7422-4855-9be6-ccf9b216a97a ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=9f3c25ee-7422-4855-9be6-ccf9b216a97a ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=9f3c25ee-7422-4855-9be6-ccf9b216a97a ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn/Windows XP (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9f3c25ee-7422-4855-9be6-ccf9b216a97a /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda6/boot: ==================================

total 25524
drwxr-xr-x  3 root root    4096 2009-01-01 16:17 .
drwxr-xr-x 21 root root    4096 2009-01-01 16:14 ..
-rw-r--r--  1 root root  504280 2008-12-19 14:24 abi-2.6.27-11-generic
-rw-r--r--  1 root root  503560 2008-11-04 17:23 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85310 2008-12-19 14:24 config-2.6.27-11-generic
-rw-r--r--  1 root root   85316 2008-11-04 17:23 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-01 20:35 grub
-rw-r--r--  1 root root 8666518 2009-01-01 16:17 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8664136 2009-01-01 16:15 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 17:41 memtest86+.bin
-rw-r--r--  1 root root 1354796 2008-12-19 14:24 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1352144 2008-11-04 17:23 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1131 2008-12-19 14:28 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1130 2008-11-04 17:27 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2345056 2008-12-19 14:24 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2339552 2008-11-04 17:23 vmlinuz-2.6.27-7-generic

=============================== sda6/boot/grub: ===============================

total 228
drwxr-xr-x 2 root root   4096 2009-01-01 20:35 .
drwxr-xr-x 3 root root   4096 2009-01-01 16:17 ..
-rw-r--r-- 1 root root    197 2009-01-01 12:00 default
-rw-r--r-- 1 root root     15 2009-01-01 12:00 device.map
-rw-r--r-- 1 root root   8108 2009-01-01 12:00 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-01 12:00 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-01 12:00 installed-version
-rw-r--r-- 1 root root   8712 2009-01-01 12:00 jfs_stage1_5
-rw-r--r-- 1 root root   3275 2009-01-01 20:35 menu.lst
-rw-r--r-- 1 root root   5107 2009-01-01 16:15 menu.lst~
-rw-r--r-- 1 root root   5107 2009-01-01 20:35 menu.lst_original
-rw-r--r-- 1 root root   7352 2009-01-01 12:00 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-01 12:00 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-01 12:00 stage1
-rw-r--r-- 1 root root 121460 2009-01-01 12:00 stage2
-rw-r--r-- 1 root root   9556 2009-01-01 12:00 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-14
Currently you have Windows XP on sda5, a logical partition, and all of XP's boot files are in your Vista sda1 partition. Also, it looks like XP's boot.ini file has an incomplete entry in it. It looks like you previously booted the Vista partition to get XP, because when you boot your Vista partition, do you previously get the Vista boot loader where it gives you a choice of Vista or XP? I would recommend moving your XP boot files to the XP partition so you can boot Vista and XP separate from each other with Grub. If that sounds good, how about doing the following:
```
sudo mkdir /mnt/sda1 /mnt/sda5
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
sudo mv /mnt/sda1/boot.ini /mnt/sda1/ntldr /mnt/sda1/NTDETECT.COM /mnt/sda5
gksudo gedit /mnt/sda5/boot.ini
```
And change your boot.ini file by deleting the line highlighted in red, and modify the last line by changing the partition number as shown in blue:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
[COLOR="Red"]multi(0)disk(0)rdisk(0)partition(3)\WINDOWS=""[/COLOR] 
multi(0)disk(0)rdisk(0)partition[COLOR="Blue"](3)[/COLOR]\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
```
Next open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change the Vista entry, and also add an XP entry as follows:
```
title Other operating systems:
root

title Windows Vista
root (hd0,0)
chainloader +1
savedefault
makeactive

title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
And finally reboot, choose XP from the Grub menu, and if all goes well you should be able to boot into XP; if not, let me know exactly what happens, and we can work from there.

---

### Post by Hyper Tails on 2009-01-15
thanks I got it working now!!
i'm back in xp now 

I really apperated it

---

### Post by caljohnsmith on 2009-01-15
Glad you can boot into XP OK now; cheers and enjoy all your OSes. :)

---

