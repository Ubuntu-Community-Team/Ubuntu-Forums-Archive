---
title: "Tried to uninstall Ubuntu to use Vista, now I'm stuck with only a blinking underscore"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by Andross707 on 2008-11-25
I got tired of always being low on disk space when I used Vista, so I decided to try and un-install my Ubuntu Dual boot through Gparted using a liveCD (which I'm typing this message on now). I first deleted the ubuntu partition (I couldn't delete the swap partition) and then resized the Vista partition to take up the space where Ubuntu was. After this completed I rebooted and was greeted with an error message that said something about my boot being corrupted! I rebooted to linux using this liveCD and began to search the forums. To make a long story short I tried a few different options:

1) I tried to use the Vista Recovery CD that someone linked online (My laptop just came with a recovery partition and no I didn't backup regularly if at all) and tried to repair my Vista installation. It shows the partition where Vista is installed but when I try to repair it just briefly (I'd say less than 10 seconds) shows a console screen running 'bfsvc.exe' then says its fixed but may need to run again if the problem isn't fixed (wha?). So I reboot thinking its fixed but am stuck with only a blinking underscore in the upper left of my screen that just hangs there. I tried to run automatic repair again a few more times but nothing changed.

2) The second thing I tried was to use the Vista Recovery CD to access a command prompt to try 'bootrec.exe /fixboot' followed by 'bootrec.exe / fixmbr' and both of those said they completed successfully but I am still left hanging with a blinking underscore at boot.

3) I also tried to run 'chkdsk /r C:' on the drive and after about 30 minutes or so of hard disk activity it tells me that it found no errors but when I restart again, I am still stuck on a blinking underscore.

4) The most promising option I found was to use the testdisk application I download using a liveCD from the universe repository. I choose my only hard drive, and select Intel partition table type and then select analyse...
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 P HPFS - NTFS              0  32 33   847 225 18   13619200 [ServiceV002]

Bad sector count.
 2 * HPFS - NTFS            848   0  1 12062  29 63  180154800 [SW_Preload]

Bad relative sector.







*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

```

Then I do I quick search...

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12162 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0  32 33   847 225 18   13619200 [ServiceV002]
P HPFS - NTFS            847 225 19  9930  55 30  145907697
P Linux                 9932  65 54 12064   5 53   34246800










Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 6973 MB / 6650 MiB

```

(This seems promising as when I ask to list files on the NTFS partition that's not ServiceV002 I can see my C: drive so It would seem that my files are still intact...)

I am now going to write these results and then reboot and I will report back on what I find....

---

### Post by jimreynold2nd on 2008-11-25
Hmm, doing fixmbr then fixboot should correct the problem... try to see if you have any external harddrive/usb stick/CD drive plugged in, and make sure there is no memory card in the card reader... (in short, make sure your computer boots from the correct media, which is your main hard drive)

---

### Post by jimreynold2nd on 2008-11-25
I have a quick, dirty fix (not dirty to me, and useful if you ever wanna play with bootloaders): Try to install GrUB using one of the linux LiveCD (Ubuntu LiveCD's grub is crippled; Fedora's GrUB is good, openSuSE's GrUB is beautiful) and make GrUB to boot Windows, bypassing the part of fixing Windows' MBR.

---

### Post by caljohnsmith on 2008-11-25
Based on the results of testdisk, it sounds like your HDD's partition table might be corrupted. Also, if you want to go ahead and delete your swap partition first, just select the swap partition when you use gparted, right-click, and choose "swapoff". Then you should be able to delete it. 

After that, how about posting the output of:
```
sudo fdisk -l
```
And also run testdisk again to post the following output:
```
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", "Y" to search for Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results. We can work from there if you want. :)

---

### Post by Andross707 on 2008-11-25
Sudo fdisk -l gives me:

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8546bca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         848     6809600    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         848        9931    72953848+   7  HPFS/NTFS
/dev/sda3            9933       12065    17123400   83  Linux

```

And here's the first screen right after I chose analyse from the main menu:

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 P HPFS - NTFS              0  32 33   847 225 18   13619200 [ServiceV002]
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 2 * HPFS - NTFS            847 225 19  9930  55 30  145907697
No EXT2, JFS, Reiser, cramfs or XFS marker
 3 P Linux                 9932  65 54 12064   5 53   34246800
 3 P Linux                 9932  65 54 12064   5 53   34246800

```

and here are the results after a quick search:

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12162 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0  32 33   847 225 18   13619200 [ServiceV002]
P HPFS - NTFS            847 225 19  9930  55 30  145907697
P Linux                 9935 113 35 12067  53 34   34246800










Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 6973 MB / 6650 MiB

```

I just proceeded from there and didn't change anything, then I ran a deeper search which gave me:

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12162 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0  32 33   847 225 18   13619200 [ServiceV002]
D HPFS - NTFS            847 225 18  1695 163  3   13619200
D HPFS - NTFS            847 225 19  9930  55 30  145907697
D HPFS - NTFS            847 225 19 12161  39 38  181747712
D HPFS - NTFS            848   0  1 12062  29 63  180154800 [SW_Preload]
D Linux                 9935 113 35 12067  53 34   34246800
D Linux                 9936 216  9 12068 156  8   34246800
D Linux                 9938 128 47 12070  68 46   34246800
D Linux                 9941 176 28 12073 116 27   34246800
D Linux                 9946 169 16 12078 109 15   34246800
D Linux                 9947 239 21 12079 179 20   34246800
D Linux Swap           12062  31  1 12160 239 46    1587520

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 6973 MB / 6650 MiB

```

The SW_Preload partition I remember being the name of where Vista was originally, though I'm not sure what all those other NTFS partitions are. Also, I'm afraid to delete the Linux Partitions myself because I don't want to make any more problems for myself but if anyone has a way to safely delete them I'd be down for it...

---

### Post by Andross707 on 2008-11-26
Any ideas anyone?

---

### Post by Andross707 on 2008-11-27
I'm sorry to be a nudge but I really would like to be able to access my vista partition if at all possible by monday b/c exams are coming up and all my notes are on that partition...so i'd just like to know if I need to start retyping them or if there is a way to get them back or not. Thank you for anything!

---

### Post by adult swim on 2008-11-27
whenever you ran 
```
bootrec /fixboot
bootrec /fixmbr
```
did you change the drive to c: first?

---

### Post by caljohnsmith on 2008-11-27
If you want to access the files on your Vista partition, you could do the following from the Live CD and see if it works:
```
sudo mount /dev/sda2 /mnt
nautilus /mnt &
```
Also, with your Vista Recovery CD, you might also try doing:
```
bootrec /rebuildbcd
```
That will rebuild Vista's partition table information, which I think is probably necessary since you tried to resize the Vista partition. Anyway, give it a shot and let me know how it goes.

---

### Post by Andross707 on 2008-11-27
Ok,

Firstly I tried 
```
sudo mount /dev/sda2 /mnt
nautilus /mnt &
```
and I can indeed access my notes from class which is a relief as this was the main thing I was worried about...

but when I tried to run 'bootrec /rebuildbcd'  in the vista recovery disk console it tells me something like ```
sucessfully scanned Windows installations
Total Identified Windows installations: 0
The operation completed successfully
```
which I found odd considering on the menu right before it it asks me to select an operating system, the only choice I have labeled 'Windows Vista (TM) Business (recovered) on (C:) SW_Preload. By the way I ran 'bootrec /rebuildbcd' while in C:\ (e.g. I did 'cd C:\' first) I also tried fixboot and fixmbr both of which said they completed successfully but still no change in trying boot to Vista...

thanks in advance for anything...

---

### Post by Andross707 on 2008-11-29
bump

---

### Post by Andross707 on 2009-01-01
Anyone?

---

### Post by Andross707 on 2009-01-05
Anyone? Anything? I'm stuck here with a bricked laptop...

---

### Post by meierfra. on 2009-01-05
To get a better picture of your current setup:

Boot from you Ubunut LiveCD, open a terminal and run the command:

```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

This will download the script "boot_info_script.txt" to your Desktop, asks for your password, runs the script and creates the file "RESULTS.txt" on your Desktop.  Post the content of "RESULTS.txt",

---

### Post by Andross707 on 2009-01-06
Is it safe to give my password?

---

### Post by meierfra. on 2009-01-06
Good question.  Giving the password will  give the script permission to run as root. Unfortunately, even simple commands like "fdisk -l" need  to run as root.  The same script as been run  multiple times in the forums:

[http://www.google.com/search?q=site%3Aubuntuforums.org+boot_info_script.txt]("http://www.google.com/search?q=site%3Aubuntuforums.org+boot_info_script.txt")

You  can have a look at the script before you run it:

```

cd ~/Desktop

wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt'

gedit boot_info_script.txt


```

 
Then you can run the script anytime  via

```
sudo bash ~/Desktop/boot_info_script.txt 
```

The script just searches your computer for various information related to booting and writes it to  the file "RESULTS.txt".  I'm one of the  authors of the script and  you will download it from  my personal website hosted  by my internet provider. It's a fast and easy way to figure out how your computer is setup.  

But if your prefer, just post the output of

```
sudo fdisk -lu
cd /mnt
sudo mkdir sda{1,2}
sudo mount /dev/sda1 sda1
sudo mount /dev/sda2 sda2
ls -l sda{1,2}

```

This lists the content of the root folder of your  windows related partitions I need to know  where your boot files are located before any further investigation.

---

### Post by Andross707 on 2009-01-11
Sorry it took so long for me to get back with you meierfra... here are the results:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  Geometry: 240 Heads and 63 sectors per Track. No 
                       errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot /NST

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8546bca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    13621247     6809600    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    13623120   193777919    90077400    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 64.6 GB, 64692944896 bytes
255 heads, 63 sectors/track, 7865 cylinders, total 126353408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   121097969    60548953+  83  Linux
/dev/sdb2       121097970   126351224     2626627+   5  Extended
/dev/sdb5       121098033   126351224     2626596   82  Linux swap / Solaris

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="887AD8F07AD8DBCE" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="07B306F64674FFFF" LABEL="SW_Preload" TYPE="ntfs" 
/dev/sdb1: UUID="df935991-1326-4430-a6da-bd36ba4e18b3" TYPE="ext3" 
/dev/sdb5: UUID="ee3fd051-a579-4896-b251-e187a035f8bb" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cliff/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cliff)

================================== sda1/boot: ==================================

total 3620
drwxrwxrwx 1 root root       0 2006-12-07 21:20 .
drwxrwxrwx 1 root root    4096 2008-11-22 20:05 ..
-rwxrwxrwx 1 root root  262144 2008-11-25 01:06 bcd
-rwxrwxrwx 1 root root  262144 2008-11-25 01:06 bcd.LOG
-rwxrwxrwx 1 root root    1024 2006-12-07 21:18 bootfix.bin
-rwxrwxrwx 1 root root 3170304 2006-12-07 21:18 boot.sdi
-rwxrwxrwx 1 root root    2048 2006-12-07 21:18 etfsboot.com
drwxrwxrwx 1 root root       0 2006-12-07 21:19 fonts

============================== sda2/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD



find --set-root --ignore-floppies \wubi\boot\grub\menu.lst

configfile \wubi\boot\grub\menu.lst



# All your boot are belong to NeoSmart!
================================== sda2/Boot: ==================================

total 3892
drwxrwxrwx 1 root root    4096 2008-11-24 21:09 .
drwxrwxrwx 1 root root   12288 2008-11-24 21:09 ..
-rwxrwxrwx 1 root root   28672 2008-11-27 22:38 BCD
-rwxrwxrwx 2 root root   28672 2008-11-23 20:30 BCD.Backup.0001
-rwxrwxrwx 1 root root  262144 2008-11-27 22:38 BCD.LOG
-rwxrwxrwx 2 root root       0 2006-11-09 17:32 BCD.LOG1
-rwxrwxrwx 2 root root       0 2006-11-09 17:32 BCD.LOG2
-rwxrwxrwx 1 root root 3170304 2006-09-18 19:45 BOOT.SDI
-rwxrwxrwx 1 root root   65536 2006-11-09 17:32 bootstat.dat
drwxrwxrwx 1 root root       0 2008-11-24 21:09 cs-CZ
drwxrwxrwx 1 root root       0 2008-11-24 21:09 da-DK
drwxrwxrwx 1 root root       0 2008-11-24 21:09 de-DE
drwxrwxrwx 1 root root       0 2008-11-24 21:09 el-GR
drwxrwxrwx 1 root root       0 2008-11-24 21:09 en-US
drwxrwxrwx 1 root root       0 2008-11-24 21:09 es-ES
drwxrwxrwx 1 root root       0 2008-11-24 21:09 fi-FI
drwxrwxrwx 1 root root    4096 2008-11-24 21:09 Fonts
drwxrwxrwx 1 root root       0 2008-11-24 21:09 fr-FR
drwxrwxrwx 1 root root       0 2008-11-24 21:09 hu-HU
drwxrwxrwx 1 root root       0 2008-11-24 21:09 it-IT
drwxrwxrwx 1 root root       0 2008-11-24 21:09 ja-JP
drwxrwxrwx 1 root root       0 2008-11-24 21:09 ko-KR
-rwxrwxrwx 1 root root  406584 2008-01-18 22:44 memtest.exe
drwxrwxrwx 1 root root       0 2008-11-24 21:09 nb-NO
drwxrwxrwx 1 root root       0 2008-11-24 21:09 nl-NL
drwxrwxrwx 1 root root       0 2008-11-24 21:09 pl-PL
drwxrwxrwx 1 root root       0 2008-11-24 21:09 pt-BR
drwxrwxrwx 1 root root       0 2008-11-24 21:09 pt-PT
drwxrwxrwx 1 root root       0 2008-11-24 21:09 ru-RU
drwxrwxrwx 1 root root       0 2008-11-24 21:09 sv-SE
drwxrwxrwx 1 root root       0 2008-11-24 21:09 tr-TR
drwxrwxrwx 1 root root       0 2008-11-24 21:09 zh-CN
drwxrwxrwx 1 root root       0 2008-11-24 21:09 zh-HK
drwxrwxrwx 1 root root       0 2008-11-24 21:09 zh-TW

================================== sda2/NST: ==================================

total 21
drwxrwxrwx 1 root root     0 2007-06-22 20:40 .
drwxrwxrwx 1 root root 12288 2008-11-24 21:09 ..
-rwxrwxrwx 1 root root   407 2007-06-08 02:11 menu.lst
-rwxrwxrwx 1 root root  8192 2007-06-04 06:13 NeoGrub.mbr

=========================== sdb1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=df935991-1326-4430-a6da-bd36ba4e18b3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=df935991-1326-4430-a6da-bd36ba4e18b3

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		df935991-1326-4430-a6da-bd36ba4e18b3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=df935991-1326-4430-a6da-bd36ba4e18b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		df935991-1326-4430-a6da-bd36ba4e18b3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=df935991-1326-4430-a6da-bd36ba4e18b3 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		df935991-1326-4430-a6da-bd36ba4e18b3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=df935991-1326-4430-a6da-bd36ba4e18b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		df935991-1326-4430-a6da-bd36ba4e18b3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=df935991-1326-4430-a6da-bd36ba4e18b3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		df935991-1326-4430-a6da-bd36ba4e18b3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=df935991-1326-4430-a6da-bd36ba4e18b3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ee3fd051-a579-4896-b251-e187a035f8bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 23788
drwxr-xr-x  3 root root    4096 2008-12-28 00:23 .
drwxr-xr-x 20 root root    4096 2008-12-28 00:15 ..
-rw-r--r--  1 root root  507665 2008-11-04 15:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 17:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 15:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 17:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-28 00:15 grub
-rw-r--r--  1 root root 8194776 2008-12-28 00:14 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8195265 2008-12-28 00:23 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 15:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 17:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 15:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 17:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 15:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 17:46 vmlinuz-2.6.27-9-generic

=============================== sdb1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-28 00:15 .
drwxr-xr-x 3 root root   4096 2008-12-28 00:23 ..
-rw-r--r-- 1 root root    197 2008-12-27 14:12 default
-rw-r--r-- 1 root root     30 2008-12-27 14:12 device.map
-rw-r--r-- 1 root root   8108 2008-12-27 14:12 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-27 14:12 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-27 14:12 installed-version
-rw-r--r-- 1 root root   8712 2008-12-27 14:12 jfs_stage1_5
-rw-r--r-- 1 root root   5263 2008-12-28 00:15 menu.lst
-rw-r--r-- 1 root root   5179 2008-12-28 00:15 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-27 14:12 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-27 14:12 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-27 14:12 stage1
-rw-r--r-- 1 root root 121460 2008-12-27 14:12 stage2
-rw-r--r-- 1 root root   9556 2008-12-27 14:12 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by meierfra. on 2009-01-11
Both sda1 and sda2 contain the necessary boot files, so it not clear which of them  (if any) was fixed by bootrec. Try this:
edit menu.lst via

```
gksudo gedit /boot/grub/menu.lst 
```

and  change the Windows item to

title		Windows Vista/Longhorn (loader)
root		(hd1,0)
map             (hd0) (hd1)
map              (hd1) (hd0)
chainloader	+1

and

title		Windows Vista/Longhorn (loader)
root		(hd1,1)
map             (hd0) (hd1)
map            (hd1)  (hd0)
chainloader	+1


Also set the boot flag to sda1

```
sudo lilo -A1 /dev/sda
```


The boot from your Vista  drive.
Also boot from the Ubuntu drive and try both Vista entries in the Grub Menu.
Let us know exactly  what happened in each of your  attempts.

---

### Post by Andross707 on 2009-01-12
OK,

firstly, when I ran ```
sudo lilo -A1 /dev/sda
``` it gave me an error in the terminal: ```
Fatal: Cannon open '1'
```

I tried to restart without booting from my USB flash drive installation of Ubuntu and just see what happens and I was left with a blinking underscore

I then restarted with the USB flash drive in and it brought up the GRUB boot menu to which I tried the first Vista option (second from the bottom in the menu) and it took me to a recovery tool that comes pre-loaded onto the thinkpad I have. It has an option to just wipe everything and start anew with a fresh Windows install but I'd like to save that as last resort as there are some school related files I'd like to keep.

I restarted again and tried the very bottom Vista option on the boot menu and the computer responded immideately with: ```
Error 11: Unrecognized device string
Press any key...
```
and after I 'pressed any key...' it just took me back to the boot menu...

Thanks in advance for any further help...

---

### Post by meierfra. on 2009-01-14
Sorry for the delay.  I tried to answer yesterday, but  the ubuntuforums site  was down.

> ```
sudo lilo -A1 /dev/sda
```
Fatal: Cannon open '1'

My mistake, it needs to be

```
sudo lilo -A /dev/sda  1
```
(the "1" is the number one, not a lower case L).


> Error 11: Unrecognized device string
Press any key...


This sounds like a typo. Make sure there is a space between "root" and "(hd0,1)",   a space between "map" and "(hd0)" and a space between (hd0) and (hd1).  But there are  no spaces allowed  within (hd0,1).  To avoid typos just use copy and paste.

---

### Post by Andross707 on 2009-01-20
OK,

well I did everything you told me in the post before this one and now when I try to restart the computer without my USB flash drive in (which has Ubuntu on it) it just takes me to the 'Rescue and Recovery' bootup thing which came pre-installed on my laptop.

I then restarted and booted with the USB flashdrive which gave me a grub menu on boot. There were two Windows Vista/Longhorn options listed. I tried the very bottom option and took me to a screen that says 'Starting up' then just hangs at a blinking underscore below it (I waited for about 60 or so seconds, tried to press enter and nothing happened so I just pressed the power button which turned off the computer). The second to last option takes me to the rescue and recovery option...

---

### Post by Andross707 on 2009-02-16
bump

---

### Post by Andross707 on 2009-03-16
bump

---

### Post by meierfra. on 2009-03-16
Let's see whether there is still   a problem with your Windows  boot sectors

Download the newest stable version of testdisk:
   [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) 
to your desktop, and then do:

```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced"
Select  the first partition (sda1) and choose "boot"
"RebuildBS"
"Write"  

(If it does not give you an options to "Write", it means that the original and rebuild boot sector are identical)

Press  "q"  a few times to get back to the  screen where you can select the partitions. Select  the second partition and repeat the above steps.

---

### Post by sarang on 2009-03-16
See [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and try the Super Grub Disk. Read and understand every option properly while using it. It has good help. Do not hurry as a poor choice of actions could make things worse.

---

### Post by dkf747 on 2009-03-17
Save yourself the aggravation.  Since you can access the files using Live CD, back them up to an external hard drive or CD. Then reformat and/or reinstall Windows.  You have wasted months on this problem.

---

