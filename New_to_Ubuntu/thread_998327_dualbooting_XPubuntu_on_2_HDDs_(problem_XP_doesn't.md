---
title: "dualbooting XP/ubuntu on 2 HDDs (problem: XP doesn't boot)"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by causticburning on 2008-11-30
Hi, I'm wanting to dual-boot Windows XP and Ubuntu on 2 separate HDDs, and I've somehow mucked it up and windows won't boot.  Ubuntu boots fine, but when windows is selected, the result is just a flashing cursor.  So far I've only used Super Grub Disk to boot linux, then edited my menu.lst to what it is now, then tried SGD again to get windows working because it failed to boot. 

Possibly I might have destroyed the boot sector of my windows partition (does it even work that way?) so that it loads the correct partition but the partition has no idea how to boot once it's there.  (Which is purely speculation, please enlighten me :P)

Here's what I have so far (results of fdisk -l) and my menu.lst:

```
laren@Matilda:~$ sudo fdisk -l
[sudo] password for laren: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf620b8c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       17994   125001765   83  Linux
/dev/sda3           17995       18518     4209030   82  Linux swap / Solaris
/dev/sda4           18519       19457     7542517+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7fe044b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS




laren@Matilda:~$ sudo gedit /boot/grub/menu.lst

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
color cyan/blue white/blue

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
# kopt=root=UUID=f2e35d32-cf2b-4c58-9357-720612c8993e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=f2e35d32-cf2b-4c58-9357-720612c8993e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=f2e35d32-cf2b-4c58-9357-720612c8993e ro single
initrd		/boot/initrd.img-2.6.24-19-rt

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f2e35d32-cf2b-4c58-9357-720612c8993e ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f2e35d32-cf2b-4c58-9357-720612c8993e ro single
#initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP (loader)
rootnoverify		(hd1,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by causticburning on 2008-11-30
Hrm, I don't get a 
NTLDR is missing
Press CTRL+ALT+DEL to restart 
message so I think my boot sector is fine...  I have no idea what's happening :(

---

### Post by causticburning on 2008-11-30
OK I must have done something else wrong, because now I'm getting a grub error 17 :O

---

### Post by caljohnsmith on 2008-11-30
I see at least part of your problem; when you boot Windows from any drive other than the drive that is first in the BIOS boot order, you have to use Grub's "mapping" technique to fool Windows into thinking it is being booted from the first boot drive. So how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then change your Windows entry to:
```
title		Windows XP (loader)
rootnoverify		(hd1,0)
map    (hd0) (hd1)
map    (hd1) (hd0)
chainloader	+1
```
Try that, and let me know exactly what happens when you boot Windows from your Grub menu. We can work from there if you want. :)

---

### Post by causticburning on 2008-11-30
changing the entry gave me a Grub Error 18

---

### Post by caljohnsmith on 2008-11-30
So you get the Grub menu OK on start up, but when you try and boot XP from the menu you get a Grub error 18? Are you booting the Ubuntu drive on start up? How about posting: 
```
sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
sudo xxd  -l  2 -p /dev/sdb
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
And we can work from there.

---

### Post by causticburning on 2008-11-30
```

laren@Matilda:~$ sudo xxd  -l  2 -p /dev/sda
[sudo] password for laren: 
eb48
laren@Matilda:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
00ff
laren@Matilda:~$ sudo xxd  -l  2 -p /dev/sdb
eb48
laren@Matilda:~$ sudo xxd -s 1049 -l 2 -p /dev/sdb
0081

```

---

### Post by causticburning on 2008-12-01
I think I have destroyed something badly... I tried booting from my windows XP cd, but the installer doesn't recognise the partition as a valid windows installation, and I can't seem to mount it in ubuntu.  (PANICKING)

---

### Post by sarum on 2008-12-01
I think it was on this forum some time ago now that I saw a diagram of how to wire up two HDs in the same case with an 'on-off-on' switch. Pretty basic stuff, but I thought it might be useful for me when the non-Linux grandchildren come to play. I'm not confident enough to try it; but I think it just involved the red wires going to each HD.
Sorry to butt-in if you're looking for a more sensible solution..........sarum

---

### Post by causticburning on 2008-12-01
Thanks for the innovative solution, but I'm using a lappy :O

---

### Post by Quarkrad on 2008-12-01
Have a look at this site:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

contains all sorts of dual boot scenarios - may help.  I found the help on fixing grub/boot/mbr issues did the trick for me.

---

### Post by caljohnsmith on 2008-12-01
How about posting the output of the following:
```
sudo mount /dev/sdb1 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
If that first command does not work, then instead try:
```
sudo mount -t ntfs-3g -o force /dev/sdb1 /mnt
```
And if that works, continue with the remaining to commands. When you boot your Windows CD, can you go to the "recovery console" by pressing "r" at the first main menu? If so, then try:
```
fixmbr
fixboot
chkdsk /r
```
And run the chkdsk as many times as necessary until it reports no errors. Also, have you ever been able to boot Windows before, or is it a fresh install?

---

### Post by causticburning on 2008-12-01
Thanks, but I followed some advice on the internet and managed to actually mangle my partition, necessitating a format (apparently?) 

I gave up and reformatted when I realised I had 98% of my data backed up anyway.  Thanks for the help though.

---

### Post by TJCIB on 2008-12-01
Just a recommendation...

Put Windows on the Master Hard Disk and Ubuntu on your Slave or secondary one.  It makes life easier.  Linux is more flexible than Windows.

Hope it works.  Sorry you have to sit through the annoying windows install again...

---

### Post by causticburning on 2008-12-01
> **TJCIB said:**
> Just a recommendation...

Put Windows on the Master Hard Disk and Ubuntu on your Slave or secondary one.  It makes life easier.  Linux is more flexible than Windows.

Hope it works.  Sorry you have to sit through the annoying windows install again...
So, after reformatting and losing my data I reloaded grub and have the same problem, so rather than trying every option I'll ask here rather than trying every option under the sun.

---

### Post by roshanjose on 2008-12-01
hey i have done the same and i have no problem...

i have 2 HDD's

160GB - ubuntu

80GB - XP

now i use BIOS to priotize which disk to boot 1st.....suppose i give it to 160GB 1st then i get ubuntu....suppose if i give it to 80GB then i get XP...

so there exists no confusion.....

u try it the same way....

---

### Post by causticburning on 2008-12-01
So what is the first thing I should do? - I can access my windows drive but cannot boot into it.

---

### Post by roshanjose on 2008-12-01
wat do u mean by access your windows...but can't boot into it??

---

### Post by handydan918 on 2008-12-01
> **causticburning said:**
> So what is the first thing I should do? - I can access my windows drive but cannot boot into it.


Go back and ignore everything that everyone said EXCEPT caljohnsmith. He knows the way. Follow him.

---

### Post by causticburning on 2008-12-02
I can access my NTFS partition from linux but it cannot boot anymore :(

---

### Post by causticburning on 2008-12-02
So what do I actually do?  I just want to be able to boot both windows and ubuntu, sorry if I'm spamming..

---

### Post by caljohnsmith on 2008-12-02
Since you reinstalled, how about posting the new output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48".

Are you able to boot your Ubuntu drive at all and get a Grub menu on start up? What happens on start up right now?

[QUOTE=handydan918]Go back and ignore everything that everyone said EXCEPT caljohnsmith. He knows the way. Follow him.[/QUOTE]
Thanks for the vote of confidence; I just try to help out like everyone else. :)

---

### Post by causticburning on 2008-12-02
fdisk
```

laren@Matilda:~$ sudo fdisk -lu
[sudo] password for laren: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf620b8c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    39070079    19535008+  83  Linux
/dev/sda2        39070080   289073609   125001765   83  Linux
/dev/sda3       289073610   297491669     4209030   82  Linux swap / Solaris
/dev/sda4   *   297491670   312576704     7542517+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7fe044b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312576704   156288321    7  HPFS/NTFS


```
xxd
```

laren@Matilda:~$ sudo xxd  -l  2 -p /dev/sda
eb48
laren@Matilda:~$ sudo xxd  -l  2 -p /dev/sdb
fa33
laren@Matilda:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
00ff

```

Currently I can only boot ubuntu from my grub menu but not my windows partition. I can access my windows partition through ubuntu (it automatically mounts it).  If I try to boot the second drive from the grub menu I just get a flashing cursor and nothing happens.

---

### Post by caljohnsmith on 2008-12-02
So is Windows on sda4 or sdb1? Please post the output of the following:
```
sudo mkdir /mnt/sda4 /mnt/sdb1
sudo mount /dev/sda4 /mnt/sda4
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda4 /mnt/sdb1
cat /mnt/sda4/boot.ini /mnt/sdb1/boot.ini
```
Note "-l" is a lowercase L, not a one.

---

### Post by thiebaude on 2008-12-02
Here's the best to dual boot: Install windows first then get your windows updates,after that install ubuntu and when you get get to the partioning part select how much HD space you want to allocate to ubuntu, then you should be all set, real simple, then grub,  upon startup should give you a choice of operating systems.

---

### Post by causticburning on 2008-12-02
My windows partition is on sdb1 (the whole drive)

```

laren@Matilda:~$ sudo mkdir /mnt/sda4 /mnt/sdb1
[sudo] password for laren: 
laren@Matilda:~$ sudo mount /dev/sda4 /mnt/sda4
laren@Matilda:~$ sudo mount /dev/sdb1 /mnt/sdb1
laren@Matilda:~$ ls -l /mnt/sda4 /mnt/sdb1
/mnt/sda4:
total 17883
-rwxrwxrwx 1 root root        0 2008-08-12 07:50 AUTOEXEC.BAT
-rwxrwxrwx 1 root root      340 2005-09-12 01:18 AUTOMODE
-rwxrwxrwx 1 root root       14 2008-08-07 17:49 BLOCK.RIN
drwxrwxrwx 1 root root     4096 2007-11-15 03:50 boot
-rwxrwxrwx 1 root root      321 2008-12-02 11:58 boot.ini
-rwxrwxrwx 1 root root   438328 2006-10-04 09:02 bootmgr
-rwxrwxrwx 1 root root        0 2008-08-12 07:50 CONFIG.SYS
-rwxrwxrwx 1 root root      117 2006-11-04 05:43 Desktop.ini
-rwxrwxrwx 1 root root     8134 2002-09-11 02:14 Folder.htt
drwxrwxrwx 1 root root        0 2007-11-15 03:50 HP
-rwxrwxrwx 1 root root        0 2008-08-12 07:50 IO.SYS
drwxrwxrwx 1 root root        0 2008-08-12 08:29 logdir
-rwxrwxrwx 1 root root 17345622 2008-10-02 23:31 log_fs.log
-rwxrwxrwx 1 root root      700 2007-11-15 03:03 MASTER.LOG
-rwxrwxrwx 1 root root        0 2008-08-12 07:50 MSDOS.SYS
-rwxrwxrwx 1 root root    47564 2006-10-01 12:00 NTDETECT.COM
-rwxrwxrwx 1 root root   250032 2006-10-01 12:00 ntldr
drwxrwxrwx 1 root root     4096 2007-11-15 03:50 preload
-rwxrwxrwx 1 root root   181648 2004-11-23 01:28 protect.ed
drwxrwxrwx 1 root root        0 2007-11-15 03:50 RECOVERY
drwxrwxrwx 1 root root        0 2008-08-07 17:51 $RECYCLE.BIN
drwxrwxrwx 1 root root     4096 2008-12-02 23:39 RECYCLER
drwxrwxrwx 1 root root     4096 2007-11-15 03:50 SOURCES
drwxrwxrwx 1 root root        0 2008-12-02 22:58 swsetup
drwxrwxrwx 1 root root     4096 2007-11-15 03:50 System Volume Information
drwxrwxrwx 1 root root     4096 2007-11-15 03:50 Tools
-rwxrwxrwx 1 root root        0 2007-11-15 03:03 USER
drwxrwxrwx 1 root root        0 2007-11-15 03:50 WINDOWS

/mnt/sdb1:
total 5239288
drwxrwxrwx 1 root root       4096 2008-12-02 12:26 Documents and Settings
drwxrwxrwx 1 root root          0 2008-12-02 12:06 EXP_INST
-rwxrwxrwx 1 root root 3219574784 2008-12-02 23:39 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-12-02 22:57 Intel
-rwxrwxrwx 1 root root 2145386496 2008-12-02 23:39 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-12-02 23:40 Program Files
drwxrwxrwx 1 root root          0 2008-12-02 23:19 RECYCLER
drwxrwxrwx 1 root root          0 2008-12-02 12:05 System Volume Information
drwxrwxrwx 1 root root      53248 2008-12-02 23:41 WINDOWS
laren@Matilda:~$ cat /mnt/sda4/boot.ini /mnt/sdb1/boot.ini
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
cat: /mnt/sdb1/boot.ini: No such file or directory

```

---

### Post by caljohnsmith on 2008-12-02
How did you install Windows? Right now it looks like you have Vista installed on sda4 and XP installed on sdb1, and also XP's boot files are in Vista's sda4 partition. Are you just trying to get XP to boot, or are you also trying to boot Vista?

---

### Post by causticburning on 2008-12-02
I believe that the vista partition is the 'rescue' partion that came with the laptop.  i'm not particularly fussed about nuking it.  The only partions i want to load are the XP partition and the Ubuntu partition.

---

### Post by caljohnsmith on 2008-12-02
OK, that makes sense then. While you have sda4 and sdb1 mounted from the directions in post #24, next do:
```
gksudo gedit /mnt/sda4/boot.ini
```
And replace it with:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```
Save that, and then do the following, and please post the output of all commands:
```
sudo apt-get install tofrodos
sudo unix2dos /mnt/sda4/boot.ini
cat -A /mnt/sda4/boot.ini
sudo mv /mnt/sda4/boot.ini /mnt/sda4/ntldr /mnt/sda4/NTDETECT.COM /mnt/sdb1

```
Next do:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your existing Windows entry with:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, choose Windows XP from the Grub menu, and let me know exactly what happens. :)

---

### Post by causticburning on 2008-12-02
```

laren@Matilda:~$ sudo apt-get install tofrodos
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  tofrodos
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 17.4kB of archives.
After this operation, 73.7kB of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com hardy/main tofrodos 1.7.6-2 [17.4kB]
Fetched 17.4kB in 6s (2575B/s)  
Selecting previously deselected package tofrodos.
(Reading database ... 170057 files and directories currently installed.)
Unpacking tofrodos (from .../tofrodos_1.7.6-2_amd64.deb) ...
Setting up tofrodos (1.7.6-2) ...
laren@Matilda:~$ sudo unix2dos /mnt/sda4/boot.ini
laren@Matilda:~$ cat -A /mnt/sda4/boot.ini
[boot loader]^M$
timeout=30^M$
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS^M$
[operating systems]^M$
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect^M$
laren@Matilda:~$ sudo mv /mnt/sda4/boot.ini /mnt/sda4/ntldr /mnt/sda4/NTDETECT.COM /mnt/sdb1

```

gonna reboot now.. wish me luck

---

### Post by causticburning on 2008-12-02
Sweet, XP booted up!  What happened?

---

### Post by caljohnsmith on 2008-12-02
> **causticburning said:**
> Sweet, XP booted up!  What happened?
Well, when you install Windows to a slave drive (and it looks like sdb could be configured that way), Windows insists on putting its boot files on the master drive in some primary NTFS/FAT partition; that's why your XP boot files ended up in sda4. So we just moved the boot files to sdb1, corrected boot.ini to use the correct drive, and then all is well in Windows Land again. :)

---

### Post by amheuwr on 2008-12-20
I seem to have a similar problem to that of causticburning in that I have two hard drives. One 160gb Primary Master with 8.10 loaded and a 80gb Primary Slave loaded with WindowsXP Home Edition. Ubuntu loads perfectly but the option to load windows from the Grub menu leaves me sitting at a press Ctrl+Alt+Del to restart your system prompt. On doing that I go back to the Grub menu and select Ubuntu which boots up correctly. 
I have seen the comment made about the boot.ini file not being on the correct location and that seemed to be causticburning's problem. Mine differs here in that I do not have another operating system other than the two mentioned above, but I do have a USB MyBook hdd. I have run all the commands that caljohnsmith recommended and have added the output below in the hope that someone can kindly point me in the right direction.
```
amheuwr@amheuwr-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   314118944   157059441   83  Linux
/dev/sda2       314118945   320159384     3020220    5  Extended
/dev/sda5       314119008   320159384     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x478f478e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   625121279   312560608+   c  W95 FAT32 (LBA)
amheuwr@amheuwr-desktop:~$
```

```
amheuwr@amheuwr-desktop:~$ sudo xxd  -l  2 -p /dev/sda
eb48
amheuwr@amheuwr-desktop:~$ sudo xxd  -l  2 -p /dev/sdb
33c0
amheuwr@amheuwr-desktop:~$ sudo xxd  -l  2 -p /dev/sdc
33c0


amheuwr@amheuwr-desktop:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
00ff
amheuwr@amheuwr-desktop:~$ sudo xxd -s 1049 -l 2 -p /dev/sdb
0000
sudo xxd -s 1049 -l 2 -p /dev/sdc
0000
```

```
amheuwr@amheuwr-desktop:~$ sudo mkdir /mnt/sdc1 /mnt/sdb1
mkdir: cannot create directory `/mnt/sdb1': File exists
amheuwr@amheuwr-desktop:~$ sudo mount /dev/sdc1 /mnt/sdc1
amheuwr@amheuwr-desktop:~$ sudo mount /dev/sdb1 /mnt/sdb1
fuse: mount failed: Device or resource busy
amheuwr@amheuwr-desktop:~$ ls -l /mnt/sdc1 /mnt/sdb1
/mnt/sdb1:
total 1573161
-rwxrwxrwx 1 root root          0 2008-12-20 00:11 AUTOEXEC.BAT
-rwxrwxrwx 1 root root        194 2008-12-20 00:05 boot.ini
-rwxrwxrwx 1 root root          0 2008-12-20 00:11 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-12-20 00:18 Documents and Settings
-rwxrwxrwx 1 root root          0 2008-12-20 00:11 IO.SYS
-rwxrwxrwx 1 root root          0 2008-12-20 00:11 MSDOS.SYS
-rwxrwxrwx 1 root root      45124 2001-08-18 13:00 NTDETECT.COM
-rwxrwxrwx 1 root root     222368 2001-08-18 13:00 ntldr
-rwxrwxrwx 1 root root 1610612736 2008-12-20 00:14 pagefile.sys
drwxrwxrwx 1 root root       4096 2008-12-20 00:19 Program Files
drwxrwxrwx 1 root root          0 2008-12-20 12:31 sda4
drwxrwxrwx 1 root root          0 2008-12-20 12:31 sdb1
drwxrwxrwx 1 root root          0 2008-12-20 00:14 System Volume Information
drwxrwxrwx 1 root root      20480 2008-12-20 00:21 WINDOWS

/mnt/sdc1:
total 5143712
drwx------ 20 amheuwr root      32768 2008-09-28 19:32 amheuwr
drwx------  2 amheuwr root      32768 2008-09-28 19:32 autorun
drwx------  5 amheuwr root      32768 2008-12-03 20:20 Finances
-rwx------  1 amheuwr root 1004190628 2008-02-04 19:47 Linguaphone.tar.gz
drwx------  3 amheuwr root      32768 2007-01-03 17:02 Music backup
drwx------ 12 amheuwr root      32768 2008-09-28 14:51 Photos
-rwx------  1 amheuwr root 4262654900 2008-09-28 20:01 Photos.tar.gz

drwx------  3 amheuwr root      32768 2008-12-19 17:14 sbackup01
drwx------  5 amheuwr root      32768 2008-04-04 16:28 Shared Documents
drwx------  9 amheuwr root      32768 2006-07-20 10:50 WD_Windows_Tools
drwx------  4 amheuwr root      32768 2008-09-28 17:42 Windows Document Folders
amheuwr@amheuwr-desktop:~$ cat /mnt/sdc1/boot.ini /mnt/sdb1/boot.ini
cat: /mnt/sdc1/boot.ini: No such file or directory
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
amheuwr@amheuwr-desktop:~$ 
```

I hope that someone can assist in  solving this rather annoying problem :-k

---

### Post by caljohnsmith on 2008-12-20
Amheuwr, you mentioned you have a USB MyBook HDD? Is that the drive that Windows is on? If so, that could be the issue, because from what I've read, it takes quite a bit of hacking to get Windows to boot from a USB drive. In order to get a better picture of your setup, please also do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your Windows booting problem might be.

---

### Post by amheuwr on 2008-12-20
XP is installed on the 80gb drive. The external hdd is for back ups and other files. I have run the script and looked at the results and although I do not have the best understanding of sripts and their results I understand enough to see that there might be a problem with the External drive in that it says windows is installed in the MBR of that drive as well as sdb1. This script and the result will be an excellent learning tool for me as I try and get to grips with the varying problems that arise from time to time.
Bit impolite of me. Forgot to say thank you for such a quick reply.

---

### Post by caljohnsmith on 2008-12-20
OK, I suspect the problem is with your XP partition's boot sector. How about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. We can work from there.

---

### Post by amheuwr on 2008-12-20
> **caljohnsmith said:**
>  if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. We can work from there.
Unfortunately the sectors showed as identical and i did not get an option to write, although there is a strange entry about a valid boot NTFS sector must be present. Looks like that is where the problem is but how do I create one of those, if indeed that is the problem?

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 80 GB / 74 GiB - CHS 9729 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  9727 254 63  156280257

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

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 80 GB / 74 GiB - CHS 9729 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  9727 254 63  156280257

filesystem size           156280257
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               9767516
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.







[  Dump  ]  [  List  ]  [  Quit  ]

                           List directories and files

```
I had a quick look at all the other commands  available with testdisk but there was nothing obvious to my untrained eye that I could do. ?

---

### Post by caljohnsmith on 2008-12-20
Do you have your Windows XP Install CD? If so, please boot that, go to the "recovery console" and run:
```
fixboot
chkdsk /r
```
And run the chkdsk as many times as it takes until it reports no errors. If you don't have your Windows XP Install CD handy, you can download a Windows XP Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). After doing the above commands, again try to boot XP and let me know exactly what happens.

---

### Post by amheuwr on 2008-12-20
This step has got me stumped a little. I have booted my system with the Ubuntu hdd removed  and it boots into XP just fine. (that was yesterday, many times) When I add the linux hdd back I get the same problem with failing to boot to XP. When I try and run the windows recovery disk using chkdsk it reports that there are errors, but I am not sure whether it is looking at the Linux disk or the Windows one? Sorry to appear a bit dull but I think I have reached the limit of my abilities which don't amount to much it would appear.:?

---

### Post by caljohnsmith on 2008-12-20
> **amheuwr said:**
> This step has got me stumped a little. I have booted my system with the Ubuntu hdd removed  and it boots into XP just fine. (that was yesterday, many times) When I add the linux hdd back I get the same problem with failing to boot to XP. When I try and run the windows recovery disk using chkdsk it reports that there are errors, but I am not sure whether it is looking at the Linux disk or the Windows one? Sorry to appear a bit dull but I think I have reached the limit of my abilities which don't amount to much it would appear.:?
OK, I didn't realize you could boot XP just fine with the Ubuntu HDD unplugged. You are certainly not being dull, I just need to get a better handle on your situation I think. :) How about rebooting, and on start up when you get the Grub menu, press "c" to get the command line, and then do:
```
grub> geometry (hd1)
grub> geometry (hd2)
```
Both (hd1) and (hd2) should show only one partition, but let me know which drive shows the partition as being "type 0x7"; most likely it will be (hd1), but I just want to make sure.

---

### Post by amheuwr on 2008-12-20
> **caljohnsmith said:**
> 
Both (hd1) and (hd2) should show only one partition, but let me know which drive shows the partition as being "type 0x7"; most likely it will be (hd1), but I just want to make sure.
 
this is a copy of the text returned for hd0 (Linux drive) and hd1 XP.
hd0
"drive 0x81: C/H/S = 1024/255/63, the number of sectors = 320173056, LBA partition num = 0 filesystem type is ext2fs, partition type 0x83,
partition num = 4 filesystem type is unknown, partition type 0x82"

hd1
"drive 0x81: C/H/S = 1024/255/63, the number of sectors = 66055248, LBA partition num:0 filesystem type unknown, partition type 0x7"

I really appreciate your help here. My wife is the one that wants to boot into XP, I would prefer to just use Linux and learn a bit more each day.

---

### Post by caljohnsmith on 2008-12-20
OK, so Windows is indeed on (hd1), so your Grub menu entry for Windows should be OK. While the Ubuntu drive is still connected, how about going into your BIOS and change the boot order so that you boot the Windows drive first, and make sure the Windows drive still boots that way. Or if your BIOS has one of those quick boot menus on start up that you can get by pressing F10/F12 or a key like that, you can choose which drive to boot from. Please let me know the results.

---

### Post by amheuwr on 2008-12-21
> **caljohnsmith said:**
>  Please let me know the results.
Well, after many hours of what I would call messing around I have come to the conclusion that this second hard drive is totally knackered. Yes, it had been booting fine, but just won't have it any more. My big problem is that I have rebooted my main disk so many times that it too has now fallen over and can't seem to start it. Writing this from my childrens computer. Ah well, another good excuse to go out and find a new French Tutor, one with a couple of large hard drives. 
Must admit that I have quite enjoyed using XP again after a couple of years on Linux. Everything just seems to work as designed and there is'nt much thinking needed to do what I acually want to do and that is work on my photos and listen to music. Saying that, I have noticed a massive difference in speed, with the bloated XP being dreadfully slow. Looks like it won't be just my wife who will be using the XP on a dual boot machine. Sorry that I seem to have gone off thread here. Thanks again caljohnsmith, for your time, you don't get much of that from M$ users.

---

### Post by caljohnsmith on 2008-12-21
I was beginning to have my suspicions that something was going on with your Windows drive, so from what you say, it sounds like that was unfortunately true. Anyway, cheers and good luck with it. :)

---

