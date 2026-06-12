---
title: "[SOLVED] Help with Grub error 25"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by DMzda on 2008-08-20
I have a system setup with an Ubuntu-Windows XP dual boot. After a windows update, I was prompted to restart my computer. I did so, but when it started, It came up with Grub error 25. Fortunately, I had access to the internet on another computer and used it to burn Super Grub Disk to CD. I tried restoring GRUB, but everything I tried failed with error 25. I tried using Windows--> Syslinux-->???. That worked, and it allowed me to boot into Windows normally without Grub.

Now I want to access Ubuntu, but I am afraid to reinstall GRUB incase it fails so that i cannot boot either OS. 

Any advice on how to do this will be appreciated.

(Lauchpad question [here]("https://answers.launchpad.net/ubuntu/+question/43185"))

---

### Post by caljohnsmith on 2008-08-20
From the Grub manual:
> Error 25 : Disk read error
This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 
So that is definitely not a good sign, as it could be an indication of a hardware problem. 
> **DMzda said:**
> I tried using Windows--> Syslinux-->???. That worked, and it allowed me to boot into Windows normally without Grub.

What is Windows--> Syslinux-->??? How exactly are you booting into Windows right now? 

If you can boot a Ubuntu Live CD, it would be helpful if you could post:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> quit
```

---

### Post by DMzda on 2008-08-20
> **caljohnsmith said:**
> 
What is Windows--> Syslinux-->??? How exactly are you booting into Windows right now? 


That is the menu option in super grub disk. I am not using Grub to boot into ubuntu. Im sorry, but that is all I know. I will boot onto the live CD now and run the code in the terminal.

Thanks.

---

### Post by DMzda on 2008-08-20
Here are the results of those commands:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065    74316689    37150312+   f  W95 Ext'd (LBA)
/dev/sda2   *    74316690   156232124    40957717+   7  HPFS/NTFS
/dev/sda5           16128    74316689    37150281    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa0aa80ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    82043954    41021946    7  HPFS/NTFS
/dev/sdb2       163863000   312576704    74356852+   7  HPFS/NTFS
/dev/sdb3        82043955   163862999    40909522+   5  Extended
/dev/sdb5        82044018    89851544     3903763+  82  Linux swap / Solaris
/dev/sdb6        89851608   163862999    37005696   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo grub

      [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,5)

grub> quit

ubuntu@ubuntu:~$ 
```

To clarify, Windows is on the 80 GB HDD, and Ubuntu is on the other HDD.

Thanks again.

---

### Post by caljohnsmith on 2008-08-20
Great, those commands clear up the ambiguity about what your setup is. Please boot your Live CD again, and from the terminal do:
```
sudo grub
grub> root (hd1,5)
grub> setup (hd1)
grub> setup (hd0)

```
That should enable to get the Grub menu on startup. We might have to tweak your Grub's /boot/grub/menu.lst if you have any problems booting into either Windows or Ubuntu, but since it worked before, I think we probably won't have to do anything else.

---

### Post by DMzda on 2008-08-21
I tried what you said, but after a reboot, it came back with error 25. Once again I had to use Super grub disk to boot into windows only, as the options for GNU/Linux all ended with error 25.
Any suggestions?

---

### Post by caljohnsmith on 2008-08-21
OK, please boot the Live CD, open a terminal and do:
```
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
sudo mount /dev/sdb6 /mnt
ls -l /mnt/boot/grub
cat /mnt/boot/grub/device.map
cat /mnt/boot/grub/menu.lst
sudo grub
grub> geometry (hd0)
grub> geometry (hd1)
grub> quit
```
Please post the output of all the commands above. Also, when you say you get the Grub error 25 on startup, do you get that before you see any Grub menu I assume?

---

### Post by DMzda on 2008-08-21
I will boot into the Live CD after a while, when I finish my current work.

EDIT: I get the Grub error before a menu shows up. It says something like "Grub initializing stage 1.5..." before the "GRUB Error 25" comes up.

---

### Post by DMzda on 2008-08-21
Here are the results of those commands:

```

ubuntu@ubuntu:~$ sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 8205                                   
0000002
2 bytes (2 B) copied, 0.000304341 s, 6.6 kB/s
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
2 bytes (2 B) copied, 4.342e-05 s, 46.1 kB/s
0000000 ff05                                   
0000002
ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt
ubuntu@ubuntu:~$ ls -l /mnt/boot/grub
total 204
-rw-r--r-- 1 root root    197 2008-08-18 22:22 default
-rw-r--r-- 1 root root     30 2008-08-18 22:22 device.map
-rw-r--r-- 1 root root   8056 2008-08-18 22:22 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-08-18 22:22 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-08-18 22:22 installed-version
-rw-r--r-- 1 root root   8608 2008-08-18 22:22 jfs_stage1_5
-rw-r--r-- 1 root root   4576 2008-08-18 20:27 menu.lst
-rw-r--r-- 1 root root   4576 2008-08-18 22:23 menu.lst~
-rw-r--r-- 1 root root   7324 2008-08-18 22:22 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-08-18 22:22 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-08-18 22:22 stage1
-rw-r--r-- 1 root root 108356 2008-08-18 22:22 stage2
-rw-r--r-- 1 root root   9276 2008-08-18 22:22 xfs_stage1_5
ubuntu@ubuntu:~$ cat /mnt/boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=7530edaf-852d-4bf6-9cee-e8ed526a263b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7530edaf-852d-4bf6-9cee-e8ed526a263b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7530edaf-852d-4bf6-9cee-e8ed526a263b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,5)
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
root		(hd1,1)
savedefault
makeactive
chainloader	+1

ubuntu@ubuntu:~$ sudo grub

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> geometry (hd0)  
drive 0x80: C/H/S = 9726/255/63, The number of sectors = 156250000, /dev/sda
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x81: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x82
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83

grub> quit

ubuntu@ubuntu:~$

```

Thanks.

---

### Post by caljohnsmith on 2008-08-21
Can you clarify which HDD is first in your BIOS boot order? Also, from your fdisk output, it seems that you might have two Windows XP installations, or at least you have one NTFS partition with its boot flag set on each HDD. But you have a total of four NTFS partitions--what are they all for? 

Also, your Grub's menu.lst appears to have incorrect (hd2,5) references for Ubuntu, because you don't have a 3rd HDD. From those "dd" commands I gave you it looks like sdb (your Ubuntu HDD) has Grub installed correctly in the MBR, but Grub is not installed to the MBR of sda, your Windows-only HDD. So probably on startup, your BIOS is trying to boot from sda.

From the Live CD, please do the following:
```
sudo grub
grub> root (hd1,5)
grub> setup (hd0)
grub> quit
```
Then reboot and see if you get your Grub menu.

---

### Post by DMzda on 2008-08-21
> **caljohnsmith said:**
> 
But you have a total of four NTFS partitions--what are they all for? 


Two are for windows programs, One is for documents, and the other is for multimedia files to be shared between the two OSes and across the network.

I will try those commands now.

---

### Post by DMzda on 2008-08-21
Having already tried that, I found that it doesn't work.

Thanks anyway.

---

### Post by DMzda on 2008-08-22
Any Help?

---

### Post by DMzda on 2008-08-25
Bump.

---

### Post by kansasnoob on 2008-08-25
Well, breaking this down one step at a time this:

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065    74316689    37150312+   f  W95 Ext'd (LBA)
/dev/sda2   *    74316690   156232124    40957717+   7  HPFS/NTFS
/dev/sda5           16128    74316689    37150281    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa0aa80ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    82043954    41021946    7  HPFS/NTFS
/dev/sdb2       163863000   312576704    74356852+   7  HPFS/NTFS
/dev/sdb3        82043955   163862999    40909522+   5  Extended
/dev/sdb5        82044018    89851544     3903763+  82  Linux swap / Solaris
/dev/sdb6        89851608   163862999    37005696   83  Linux

shows that you have one win OS on sda2, another win OS on sdb1 and Solaris on sbd6.

Am I right?

---

### Post by kansasnoob on 2008-08-25
From live Cd run this command:

```
find /boot/grub/stage1
```

---

### Post by DMzda on 2008-08-28
I have 1 Windows XP OS on the 80GB hard drive, and one Ubuntu OS on the 160 GB HDD.

---

### Post by DMzda on 2008-08-29
I don't know how, but I just tried using super grub disk again, and it worked. :) Grub boots fine.

However, I have a new problem now. Whilst trying to fix it, I reinstalleed ubuntu on the same partition without formatting it. It worked fine, although the windows had no close, minimize or maximize. Using Apt-on-cd, I backed up some of the packages I had installed. I tried to install them all at once by using:

```
sudo dpkg -i *
```

after I had used "cd" to open the directory. This caused major mayhem as lots of dependencies were missing. I couldn't use:

```
sudo apt-get install -f
```

to fix the dependencies as I needed ntlmaps to authorize the ISA proxy server that I must use.

I performed a command in dpkg which deselected all non-essential packages. It turned out to be a bad mistake as nothing would work. Eventually, using Ctrl+Alt+F2 (something like tty2 :confused:), I got ntlmaps to work. However, when it works, I cannot do anything else, only end it with Ctrl+C. With tty1, I tried to install a package from the internet while ntlmaps was running in tty2. This failed. Now I have a command line and windows :(.

It was a stupid thing to do :(

 Any help???

---

### Post by DMzda on 2008-08-29
Marked as solved...

Opened new thread for above question [HERE.]("http://ubuntuforums.org/showthread.php?p=5688738")

---

