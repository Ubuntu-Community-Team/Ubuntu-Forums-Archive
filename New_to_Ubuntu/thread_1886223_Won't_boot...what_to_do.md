---
title: "Won't boot...what to do?"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by franklin_m on 2011-11-24
Hello,

I'm in a bad spot. Updated my system last night, and now it won't boot from the screen that shows the various operating systems (-12, -12 generic, -11, etc.). Will boot to windows though.

Thinking back, there was an option at some point with the boot loader. I may have deleted the "pointer" to kernel -13 which, as I recall, was the update.

Is there a way to undo this mess easily?

If not, my first goal would be to keep from losing my files. Don't mine reloading etc.

If I reload Ubuntu from a stick, will the files I had in the linux file structure be over-written?

If yes to the last question, is there a way to retrieve them assuming they're still there?

This is relatively urgent, thanks so much.

[email]frankmellott@earthlink.net[/email]

---

### Post by drs305 on 2011-11-24
Have you tried booting -11? If you don't see them in the menu, look under the  "Previous" submenu.

---

### Post by ptrakk on 2011-11-24
are there any error messages?

---

### Post by franklin_m on 2011-11-24
Tried booting all previous versions shown on the screen...get "File not found"

Windows is the only one that will boot

---

### Post by Rubi1200 on 2011-11-24
Please post the results of the boot info script so we can get a better overview of what is happening.

Details in the link at the bottom of my post.

Thanks.

---

### Post by drs305 on 2011-11-24
We probably need to see the status of your system. If you can, boot an Ubuntu LiveCD and download/run the Boot Info Script. Post the contents of the RESULTS.txt file it generates.

Alternatively, you can try the Boot Repair app to fix things. The script is accessible from the "BIS" link in my signature line, as is "Boot Repair".

---

### Post by leeper69 on 2011-11-24
If you can boot to Ubuntu restricted mode or a previous kernel try typing sudo update-grub in the terminal for a previous kernel or at the prompt if you pick restricted mode. if none of the ubuntu listings in grub are showing up try running e2fsck from your install disk on your Ubuntu partitions.
If you choose to reload ubuntu you can choose to keep your old settings but as for your personal files?

---

### Post by franklin_m on 2011-11-24
I'm going to try the boot repair first, unless someone thinks it's better to try live USB first.

Any thoughts?
Thanks so much...
Frank

---

### Post by franklin_m on 2011-11-24
I couldn't get the iso of the Boot Repair to work, so I've made an ISO liveUSB and running ubuntu from that.

Next step is to do the BOOT INFO script

I'm a complete idiot when it comes to running from the terminal window, so exactly what would I type if I put the zip file contents on the desktop under my user, of the existing linux partition? (I can get to folder

linux/home/frank/documents for example

Sorry for asking such a stupid question, but I can't mess this up and lose some of these files (special ed stuff dealing w/ my kids).

Thanks

---

### Post by drs305 on 2011-11-24
Double-click the zip file and extract the script to your Desktop. If you have already extracted the file, move it to your Desktop. Then run it as:
```
sudo bash ~/Desktop/boot_info_script.sh
```

---

### Post by franklin_m on 2011-11-24
Results.txt:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Recovery: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 694960 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920   146,882,294   146,800,375   7 NTFS / exFAT / HPFS
/dev/sda3         292,109,895   312,576,704    20,466,810  db CP/M / CTOS / ...
/dev/sda4         146,882,295   292,109,894   145,227,600   5 Extended
/dev/sda5         146,882,358   287,916,929   141,034,572  83 Linux
/dev/sda6         287,916,993   292,109,894     4,192,902  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2030 MB, 2030043136 bytes
255 heads, 63 sectors/track, 246 cylinders, total 3964928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     3,951,989     3,951,927   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        B8B85C53B85C11EC                       ntfs       WinXP
/dev/sda3        9474-255C                              vfat       DELLRESTORE
/dev/sda5        7e8f25dd-34c4-425e-a1b3-4ee601242c45   ext3       Linux
/dev/sda6        89a64017-b88f-499f-bc8e-5b9ad32e1f2f   swap       
/dev/sdb1        508B-BA0C                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color white/black blink-light-green/black

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=7e8f25dd-34c4-425e-a1b3-4ee601242c45 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7e8f25dd-34c4-425e-a1b3-4ee601242c45

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
# defoptions=splash vga=788

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
# howmany=4

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.10, kernel 3.0.0-12-generic
uuid		7e8f25dd-34c4-425e-a1b3-4ee601242c45
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=7e8f25dd-34c4-425e-a1b3-4ee601242c45 ro splash vga=788 
initrd		/boot/initrd.img-3.0.0-12-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
uuid		7e8f25dd-34c4-425e-a1b3-4ee601242c45
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=7e8f25dd-34c4-425e-a1b3-4ee601242c45 ro  single
initrd		/boot/initrd.img-3.0.0-12-generic

title		Ubuntu 11.10, kernel 2.6.38-11-generic
uuid		7e8f25dd-34c4-425e-a1b3-4ee601242c45
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=7e8f25dd-34c4-425e-a1b3-4ee601242c45 ro splash vga=788 
initrd		/boot/initrd.img-2.6.38-11-generic
quiet

title		Ubuntu 11.10, kernel 2.6.38-11-generic (recovery mode)
uuid		7e8f25dd-34c4-425e-a1b3-4ee601242c45
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=7e8f25dd-34c4-425e-a1b3-4ee601242c45 ro  single
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.10, memtest86+
uuid		7e8f25dd-34c4-425e-a1b3-4ee601242c45
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,1)
savedefault
chainloader	+1

--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7e8f25dd-34c4-425e-a1b3-4ee601242c45 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=89a64017-b88f-499f-bc8e-5b9ad32e1f2f none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda5/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               2
               =                boot/initrd.img-3.0.0-13-generic               7
               =                boot/vmlinuz-3.0.0-13-generic                  5
               =                vmlinuz                                        5

================= sda5: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

               =                boot/extlinux/chain.c32                        2
               =                boot/extlinux/extlinux.conf                    1

============== sda5: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

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
            ?? = ??             syslinux/vesamenu.c32                          2

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by drs305 on 2011-11-24
Looking at the RESULTS.txt, there are only two things that jump out for me. The first is that you are still using Grub legacy. That is ok, but it isn't as versatile as Grub 2 (which I'll explain in a minute).

The other is that RESULTS.txt isn't able to pinpoint the location of your boot files. This sometimes happens even when there is nothing wrong, so it may or may not be an indicator of problems.

I don't see any obvious errors with your menu.lst file although my knowledge of Grub legacy is fading. There are two avenues I'd take in troubleshooting, barring the lack of anything truly definitive.

One possibility is that your Ubuntu partition may need an fsck check run on it (and perhaps that is why the script can't determine the location). From the LiveCD, you could mount your Ubuntu partition and run a check and then try rebooting:
```

sudo umount /dev/sda5 # Just to make sure it isn't mounted
sudo e2fsck -f -y -v /dev/sda5  # Perform the check
```

When you reboot, before attempting a full reboot, enter the BIOS and check the drive size. It should display approximately 160GB. If it shows 137GB or less, it's possible your boot files are positioned on the drive deeper than the BIOS and Grub can see. If this was Grub 2, we would be able to check if it could see the files on sda5, but Grub legacy doesn't provide this capability.

So try these things and let us know what happens.

---

### Post by franklin_m on 2011-11-24
I ran the two commands from the terminal.

After the first it told me sda5 not mounted, or words to that effect.

After the second, which seemed to execute very quickly, I rebooted and checked the bios. Showed 160gb. Of note, after running the second command, it showed a list of options for what I just asked it to do.

Tried rebooting and it still says "file not found"

---

### Post by franklin_m on 2011-11-24
FYI, I retyped the two commands again, because I just didn't think it seemed right that second executed so quickly.

After the first it said:
"umount: /dev/sda5: not mounted"

after the second, it said:
"e2fsck 1.41.14 (22-Dec-2010)"
"Pass 1: Checking inodes, blocks, and sizes"

And it's apparently still doing that now....

---

### Post by franklin_m on 2011-11-24
It's completed, gave a report. Nothing jumped out at me. Bios still shows 160gb. Tried booting again, still "file not found"

---

### Post by drs305 on 2011-11-24
I would recommend purging Grub and installing Grub 2. If there are problems with the partition, this won't fix things. If it's something related to the boot files, it should. And it will also leave you with Grub 2, which is much more versatile than Grub.

If you are interested in doing this, you would 'chroot' into your real installation via the LiveCD. You mount sda5, copy some system files, and then chroot. As root, you would purge Grub (grub) and install Grub 2 (grub-pc). Here is a link on how to accomplish this:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

Back to your original concern: this procedure will not affect any data files or most system files on your Ubuntu partition. It will remove/replace Grub bootloading files, but leave everything else intact.

To this point I've concentrated on the boot process. If you think it is something related to video or another problem after the kernel takes over, we can work on that instead.

---

### Post by franklin_m on 2011-11-24
Thanks. I'll try that. I'm up in Alaska working, on the north slope actually, and am about to head to dinner (Thanksgiving away from home...oh well). Hey, at least it's 25 below zero outside! Probably won't get to it for a couple hourse.

Anyway, not sure what time zone you're in, but I'm an hour behind Pacific, so might want to look for my update in the morning.

I really appreciate this. I'm confident that with your help we'll get it to work. I don't think it's video or anything. Like I said when I updated last night, some dialog box came up with the bootloader. I'm pretty sure it's confined to that. But I'll load grub2 and we'll see. Thanks.

Frank

---

### Post by drs305 on 2011-11-24
I've spent a lot of holidays away from family - Happy Thanksgiving. Fortunately for me those days are over.

I'll be logging off shortly but will check back in the morning. Enjoy your dinner.

---

### Post by drs305 on 2011-11-24
I've spent a lot of holidays away from family - fortunately for me those days are over.

I'll be logging off shortly but will check back in the morning. Enjoy your dinner. Happy Thanksgiving.

Added:

If you successfully install Grub 2 and it still won't boot, please rerun the boot info script and post the new RESULTS.txt

---

### Post by franklin_m on 2011-11-24
I can't thank you enough. It worked! I had to muck around to get the internet connection up (had to load Broadcom drivers) from liveCD, but was able to accomplish it.

As soon as I saw the grub find the -13 kernel, I know it would likely work. Two remaining questions:

How can I thank you?

How can I develop such knowledge?

Thanks,
Frank

---

### Post by drs305 on 2011-11-25
> **franklin_m said:**
> I can't thank you enough. It worked! I had to muck around to get the internet connection up (had to load Broadcom drivers) from liveCD, but was able to accomplish it.

How can I thank you?

How can I develop such knowledge?


The thanks came when I logged on and saw the 'SOLVED' tag. When you are able, help others on the forum.

The Ubuntu Forum members come from a vast spectrum of computer experience. Most of us learned Linux in our spare time. Fortunately experience and the Internet are great teachers. ;-)

The limited knowledge I've picked up is based on reading lots of questions on the forum, then reading more about the ones I'm interested in or curious about. It leaves very large gaps, but at least most of what I know applies to my computers (which often limits how I can help others).

I hear if you are doing night study in Alaska this time of year you'll become an expert in no time!

Happy Ubuntu-ing !

---

