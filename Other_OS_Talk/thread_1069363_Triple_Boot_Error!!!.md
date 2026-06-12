---
title: "Triple Boot Error!!!"
date: 2009-02-13
forum: Other OS Talk
---

### Post by killjoy123987 on 2009-02-13
I am having a serious problem trying to triple boot. I just got a new computer with vista on it, and preceded to install ubuntu as normal, upon realizing that vista is horrible for most things and some things that even ubuntu cant do i decided to triple boot with XP. I installed Xp and restored GRUB as the main boot loader, but this is where things have seriously gotten wrong :(. It seems that my xp deleted my vista boot record in the MBR (I think). here is how my hard drive is set up:

Sda 01: Windows Vista 
Sda 02: Windows XP
Sda 03: /Home
sda 05: swap
sda 06: /

when i boot into sda01 it loads XP, when it should load vista, and when i load sda02 it gives me an error saying it cannot find some file (can't remember what its called started with an 'N') and told me to restart with ctrl-alt-del. I have tried numerous ways to get the vista boot back, including using the install discs to repair the boot process. Any help would be appreciated i couldn't find a smiler problem anywhere so this is my last hope :(, also xp and ubuntu work properly

P.S. This is my first post here and if this is not in the right section or should not be on this website just let me know

---

### Post by caljohnsmith on 2009-02-13
It definitely sounds like XP put its boot files in your sda1 Vista partition, and then also modified the boot sector to boot XP's "ntldr" rather than Vista's "bootmgr". Does your Vista Install CD have a command line available, or is your Vista CD OEM? It would help to get a clearer picture of your setup and confirm whether that is true or not, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your desktop, and then do the following as **root user**, but replace <username> with your username:
```
bash /home/[COLOR="Blue"]<username>[/COLOR]/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. That will help clarify your setup and hopefully what the solution to your problem might be.

---

### Post by killjoy123987 on 2009-02-14
I did what you said and here is what it generated:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6d506bf5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   244,155,869   244,155,807   7 HPFS/NTFS
/dev/sda2         244,155,870   289,073,609    44,917,740   7 HPFS/NTFS
/dev/sda3         289,073,610   432,437,669   143,364,060  83 Linux
/dev/sda4         432,437,670   488,392,064    55,954,395   5 Extended
/dev/sda5         483,636,888   488,392,064     4,755,177  82 Linux swap / Solaris
/dev/sda6         432,437,796   483,636,824    51,199,029  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7A9AC7CE9AC7855B" LABEL="COMPAQ" TYPE="ntfs" 
/dev/sda2: UUID="BA449E4A449E0971" TYPE="ntfs" 
/dev/sda3: UUID="0757811d-ad70-4aee-b60e-23031c582532" TYPE="ext3" 
/dev/sda5: UUID="605b4752-bb12-416c-8d95-40c6dbb1a6a8" TYPE="swap" 
/dev/sda6: UUID="f1260237-f8ef-4ee7-9736-711da2831601" TYPE="ext3" 

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
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jeremy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jeremy)

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows Vista Premium" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=f1260237-f8ef-4ee7-9736-711da2831601 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f1260237-f8ef-4ee7-9736-711da2831601

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        f1260237-f8ef-4ee7-9736-711da2831601
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f1260237-f8ef-4ee7-9736-711da2831601 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        f1260237-f8ef-4ee7-9736-711da2831601
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f1260237-f8ef-4ee7-9736-711da2831601 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        f1260237-f8ef-4ee7-9736-711da2831601
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=f1260237-f8ef-4ee7-9736-711da2831601 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        f1260237-f8ef-4ee7-9736-711da2831601
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=f1260237-f8ef-4ee7-9736-711da2831601 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        f1260237-f8ef-4ee7-9736-711da2831601
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn(Loader)
root            (hd0,0)
savedefault
makeactive
chainloader      +1




=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=f1260237-f8ef-4ee7-9736-711da2831601 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=0757811d-ad70-4aee-b60e-23031c582532 /home           ext3    relatime        0       2
# /dev/sda5
UUID=605b4752-bb12-416c-8d95-40c6dbb1a6a8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 224.4GB: boot/grub/menu.lst
 224.4GB: boot/grub/stage2
 224.3GB: boot/initrd.img-2.6.27-11-generic
 224.3GB: boot/initrd.img-2.6.27-7-generic
 224.4GB: boot/vmlinuz-2.6.27-11-generic
 224.4GB: boot/vmlinuz-2.6.27-7-generic
 224.3GB: initrd.img
 224.3GB: initrd.img.old
 224.4GB: vmlinuz
 224.4GB: vmlinuz.old

```i noticed that in the vista partition it said that its boot sector type was xp even though its OS is vista, im no expert but i guess this confirms what you said.

 As for the vista install CD i don't have one, my computer came with vista on it but i did make recovery discs before i did anything. I don't know if they can be used for the same thing, but i tried to repair my install using them and it generated an error about the boot sector and that it couldn't fix it automatically. I haven't checked about a command line but I don't think it has one , ill check though.

There is no command line option on the vista recovery CD

---

### Post by caljohnsmith on 2009-02-14
As I suspected, when you installed XP to sda2, XP put its boot files in your sda1 Vista partition and also modified the sda1 boot sector to boot "ntldr", which is a standard XP boot sector. To try and fix the boot sector first, how about making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows partition, choose "Boot", then choose "Backup BS"; if testdisk gives you a warning that the boot sectors are not identical, then choose "Write". Or if testdisk says the boot sectors are identical and doesn't give you an option to "Backup BS", let me know, and we can work from there.

---

### Post by killjoy123987 on 2009-02-14
this is the output i got from the testdisk:

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 15197 254 63  244155807 [COMPAQ]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.





[  Quit  ]  [  List  ]  [Rebuild BS]  [Repair MFT]  [  Dump  ]
                            Return to Advanced menu

```

it didnt give me an option to backup again this was from my vista partition i tried on the xp partition and it gave me the same result.
BTW thanks for your help :)

---

### Post by caljohnsmith on 2009-02-14
[QUOTE=killjoy123987]BTW thanks for your help.[/QUOTE]
You're welcome, hopefully we can get your setup working again. :) OK, while you are in Ubuntu, how about doing:
```
sudo dd if=/dev/sda2 of=~/Desktop/sda2_beginning.bin count=20
```
That will create a really small "sda2_beginning.bin" file on your desktop; please save that in case we need it. Next how about downloading a Windows Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"), boot that, go to the command line, and do:
```
bootrec /fixboot
```
And then try booting Vista from Grub again, and let me know what happens. If that doesn't allow you to boot Vista, please post the output of:
```
sudo xxd -s128 -l2 -p /dev/sda1
sudo xxd -s128 -l2 -p /dev/sda2
```
And we can work from there.

---

### Post by killjoy123987 on 2009-02-14
It Works!!!! thx alot everything works after that vista recovery CD. thx again for all your help :)

---

### Post by caljohnsmith on 2009-02-14
> **killjoy123987 said:**
> It Works!!!! thx alot everything works after that vista recovery CD. thx again for all your help :)
That's great news, glad to hear you can boot Vista again. I'm wondering though, can you boot XP right now? Does it show up in your Vista boot menu? I woudn't think so, unless you all ready added it. If you need a hand booting XP separate from Vista let me know. Otherwise cheers, and enjoy all your OSes. :)

---

### Post by pyrocloud on 2009-02-15
Sorry to bring up this post, but I also have/had this problem. 

The assessment that caljohnsmith made was correct. XP overwrote the MBR and replaced it with its NTLDR.

Running Vista's Bootrec.exe /fixboot and /fixMBR, then reinstalling grub takes care of the issue but leaves XP unable to boot. With Grub throwing an Error 12: Invalid Device Request when trying to call XP. All other boot options working fine.

I think this is because XP is looking for its NTLDR on the boot partition, which was erased during the Vista fix.

_Can someone clarify how to get XP boot info sync'ed?_

To aid here is boot info output. Thanks to any help in advance.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 92. But according to the info from fdisk, 
                       sda6 starts at sector 140208128.
    Operating System:  Windows XP
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f110b

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    14,338,091    14,336,044  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     14,346,045    77,272,649    62,926,605   7 HPFS/NTFS
/dev/sda3          77,273,064   108,740,807    31,467,744  af Unknown
/dev/sda4         108,740,811   312,581,447   203,840,637   5 Extended
/dev/sda5         108,740,812   140,208,035    31,467,224  83 Linux
/dev/sda6         140,208,128   171,673,599    31,465,472   7 HPFS/NTFS
/dev/sda7         171,675,784   224,114,795    52,439,012   7 HPFS/NTFS
/dev/sda8         224,114,800   310,458,623    86,343,824   7 HPFS/NTFS
/dev/sda9         310,458,628   312,581,447     2,122,820  82 Linux swap / Solaris

/dev/sda4 ends after the last cylinder of /dev/sda
/dev/sda9 ends after the last cylinder of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="RECOVERY" UUID="80E9-C15B" TYPE="vfat" 
/dev/sda2: UUID="7898FB3098FAEC0E" LABEL="VistaOS" TYPE="ntfs" 
/dev/sda3: TYPE="hfsplus" 
/dev/sda5: UUID="2a63db14-992c-48d8-9d58-9fa61e1b26b5" TYPE="ext3" 
/dev/sda6: UUID="E4E8CD18E8CCE9BE" LABEL="Win XP" TYPE="ntfs" 
/dev/sda7: UUID="1EEDADCE6619BBCD" LABEL="Documents" TYPE="ntfs" 
/dev/sda8: UUID="3E60376C6179DC96" LABEL="Store" TYPE="ntfs" 
/dev/sda9: TYPE="swap" UUID="27092d8e-c143-48a6-aa9a-3e059650580d" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

================================ sda2/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows Vista"
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda5/boot/grub/menu.lst: ===========================

default		0

timeout		5

#hiddenmenu

color cyan/blue white/blue

title		Kubuntu Linux
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2a63db14-992c-48d8-9d58-9fa61e1b26b5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Windows XP
root		(hd0,5)
savedefault
makeactive
chainloader	+1

title		Mac OS X
root		(hd0,2)
savedefault
makeactive
chainloader	+1
=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2a63db14-992c-48d8-9d58-9fa61e1b26b5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=27092d8e-c143-48a6-aa9a-3e059650580d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  63.7GB: boot/grub/menu.lst
  63.4GB: boot/grub/stage2
  63.5GB: boot/initrd.img-2.6.24-16-generic
  63.4GB: boot/initrd.img-2.6.24-16-generic.bak
  63.5GB: boot/initrd.img-2.6.24-23-generic
  63.5GB: boot/initrd.img-2.6.24-23-generic.bak
  63.4GB: boot/vmlinuz-2.6.24-16-generic
  63.5GB: boot/vmlinuz-2.6.24-23-generic
  63.5GB: initrd.img
  63.5GB: initrd.img.old
  63.5GB: vmlinuz
  63.4GB: vmlinuz.old

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e c0 8e d8 b0 48 e8  |.1............H.|
00000010  3d 01 66 8b 44 08 e8 54  01 66 31 c0 66 a3 00 e4  |=.f.D..T.f1.f...|
00000020  80 7c 04 af 75 03 e9 09  00 be a6 7d e8 10 01 e9  |.|..u......}....|
00000030  c2 00 b0 5d e8 18 01 b0  01 31 db 8e c3 bb 00 14  |...].....1......|
00000040  66 b9 02 00 00 00 e8 ae  00 73 03 e9 9b 00 a1 00  |f........s......|
00000050  14 3d 42 44 75 3f b0 7c  e8 f4 00 66 8b 1e 14 14  |.=BDu?.|...f....|
00000060  66 0f cb 66 c1 fb 09 66  31 c0 a1 7e 14 86 c4 52  |f..f...f1..~...R|
00000070  66 f7 e3 5a 66 31 db 8b  1e 1c 14 86 df 66 01 d8  |f..Zf1.......f..|
00000080  66 40 66 40 66 89 c1 b0  01 31 db 8e c3 bb 00 14  |f@f@f....1......|
00000090  e8 64 00 72 54 b0 7d e8  b5 00 a1 00 14 3d 48 2b  |.d.rT.}......=H+|
000000a0  74 05 3d 48 58 75 42 b0  2a e8 a3 00 66 a1 28 14  |t.=HXuB.*...f.(.|
000000b0  66 0f c8 66 c1 f8 09 66  8b 1e c0 15 66 0f cb 52  |f..f...f....f..R|
000000c0  66 f7 e3 5a 66 48 66 48  66 01 c1 b0 21 e8 7f 00  |f..ZfHfHf...!...|
000000d0  b0 7e bb 00 20 8e c3 bb  00 02 e8 1a 00 72 0a b0  |.~.. ........r..|
000000e0  59 e8 6b 00 ea 00 02 00  20 be bd 7d e8 50 00 b0  |Y.k..... ..}.P..|
000000f0  58 e8 5b 00 f4 eb fd 66  60 89 e5 1e 1e 66 03 0e  |X.[....f`....f..|
00000100  00 e4 66 03 4c 08 66 51  06 53 30 e4 50 50 b0 2d  |..f.L.fQ.S0.PP.-|
00000110  e8 3c 00 66 89 c8 e8 54  00 b0 3d e8 31 00 58 e8  |.<.f...T..=.1.X.|
00000120  4b 00 68 10 00 89 e6 b4  42 cd 13 73 0d e8 3d 00  |K.h.....B..s..=.|
00000130  b0 52 e8 1a 00 31 c0 cd  13 f9 89 ec 66 61 c3 bb  |.R...1......fa..|
00000140  01 00 fc ac 3c 00 74 06  b4 0e cd 10 eb f5 c3 66  |....<.t........f|
00000150  60 bb 01 00 b4 0e cd 10  66 61 c3 66 60 31 c9 88  |`.......fa.f`1..|
00000160  c1 b0 20 e3 05 e8 e7 ff  e2 f9 66 61 c3 66 60 b9  |.. .......fa.f`.|
00000170  04 00 66 0f c8 50 c0 c8  04 e8 17 00 58 e8 13 00  |..f..P......X...|
00000180  66 c1 c8 08 e2 ef b0 0a  e8 c4 ff b0 0d e8 bf ff  |f...............|
00000190  66 61 c3 24 0f 04 30 3c  39 76 02 04 07 e8 af ff  |fa.$..0<9v......|
000001a0  c3 b4 00 cd 16 c3 0a 0d  48 46 53 2b 20 70 61 72  |........HFS+ par|
000001b0  74 69 74 69 6f 6e 20 65  72 72 6f 72 00 0a 0d 45  |tition error...E|
000001c0  72 72 6f 72 20 6c 6f 61  64 69 6e 67 20 62 6f 6f  |rror loading boo|
000001d0  74 65 72 00 00 00 00 00  00 00 00 00 00 00 00 00  |ter.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

sed: can't read sda3/etc/issue: No such file or directory

```

---

### Post by caljohnsmith on 2009-02-15
Pyrocloud, your situation is a little different because you installed Windows XP to sda6, which is a logical partition. How about doing the following while you are in Ubuntu:
```
sudo mkdir /mnt/sda2 /mnt/sda6
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sda6 /mnt/sda6
sudo mv /mnt/sda2/boot.ini /mnt/sda2/ntldr /mnt/sda2/NTDETECT.COM /mnt/sda6
gksudo gedit /mnt/sda6/boot.ini
```
Then modify your boot.ini by deleting the Vista line highlighted in red, and modify the partition number to be "5" as shown highlighted in blue:
```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition[COLOR="Blue"](5)[/COLOR]\WINDOWS
[operating systems]
[COLOR="Red"]multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows Vista"[/COLOR]
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```
And since you are using gedit to modify your boot.ini file, it is good to ensure that the boot.ini file retains its Windows style line endings (carriage return + line feed), so how about doing:
```
sudo apt-get install tofrodos
sudo unix2dos /mnt/sda6/boot.ini

```
Next you will need to change your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And delete the "makeactive" line in your Windows XP entry, and also use "rootnoverify" so that it looks like:
```
title		Windows XP
rootnoverify		(hd0,5)
savedefault
chainloader	+1

```
And lastly, you will need to repair your Windows XP boot sector, because the file system parameters in the boot sector are not correct right now; that typically happens when you install Windows to a logical partition, because Microsoft does not expect that you will try to boot Windows directly from a logical partition. So how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the sda6 Windows XP partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. We can work from there if necessary.

---

### Post by Jack Shankle on 2009-02-15
I have a triple boot system that is working fine.
I went to this site for help: [url]www.neosmart.net/forums and went into the
subforum called: "freebcd". They solve a lot of peoples triple booting
problems there.
They solved mine.

---

### Post by pyrocloud on 2009-02-15
Thank you caljohnsmith. XP is now booting fine. Yeah, I forgot to change the boot.ini file back to what it was before I changed those lines. It was my attempt to get it working again. 

In the end it was testdisk rewriting the BootSector of the partition that fixed the problem.

I'm wondering why we need to set the XP boot options to rootnoverify. Is this just to get GRUB to ignore any boot sector issues?

Thanks again.

---

### Post by caljohnsmith on 2009-02-15
> **pyrocloud said:**
> Thank you caljohnsmith. XP is now booting fine. Yeah, I forgot to change the boot.ini file back to what it was before I changed those lines. It was my attempt to get it working again. 

In the end it was testdisk rewriting the BootSector of the partition that fixed the problem.

I'm wondering why we need to set the XP boot options to rootnoverify. Is this just to get GRUB to ignore any boot sector issues?

Thanks again.
I'm not sure of the exact technical difference between "root" and "rootnoverify", because the Grub manual claims that rootnoverify means the partition is not mounted; yet I've used rootnoverify with Linux partitions where they must be mounted in order to access there boot files. I just know from a practical standpoint that "rootnoverify" is less prone to Grub errors than just "root", and it always seems safe to use it with Windows partitions. I would probably have to look at the Grub source code if I really wanted to understand the difference, and I've never bothered. You could ask forum member meierfra, because he knows more about the technical details of things like that than I do. Anyway, cheers and glad XP boots now.

---

