---
title: "Computer restarting in windows after dual boot install"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by lbarnes on 2008-11-02
hey guys, i've never had this problem before, but if i leave my computer in windows the computer will restart after awhile, and when i come back ubuntu is loaded up.  in the grub under other os it has "windows/vista (loader)" listed two times, which i've never seen the loader part before.  on my old comuter it was just windows xp professional, so i don't know what the (loader) business is.  the computer does not restart if i leave ubuntu on like i did last night.

thanks guys

---

### Post by lbarnes on 2008-11-02
sorry to bump this, but it's not even on page 1 anymore lol

---

### Post by bumanie on 2008-11-02
Firstly, it is discouraged to bump before 24 hours has past as there is a dedicated team that answers unanswered posts, if yours happened to go unanswered. 
Any way, can you post the output of > sudo fdisk -lu from ubuntu and > cat /boot/grub/menu.lst As you say, there is normally only one vista entry, I suspect your grub list has two entries for windows. Why windows shuts down of its own accord, I have no idea other than you may have gathered a nasty off the internet - may be give it a full scan with clamav from within ubuntu and see if it comes up with anything.

---

### Post by lbarnes on 2008-11-02
> Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1154639744   577319841    7  HPFS/NTFS
/dev/sda2      1438974180  1465144064    13084942+   7  HPFS/NTFS
/dev/sda3      1154639745  1438974179   142167217+   5  Extended
/dev/sda5      1154639808  1427343119   136351656   83  Linux
/dev/sda6      1427343183  1438974179     5815498+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdg: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ec89eab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1           16065  1465144064   732564000    f  W95 Ext'd (LBA)
/dev/sdg5           16128  1465144064   732563968+   7  HPFS/NTFS
lennon@lennon-desktop:~$ cat /boot/grub/menu.lst 
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
# kopt=root=UUID=9466303c-b53e-40ec-9065-0da94c7dc13c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9466303c-b53e-40ec-9065-0da94c7dc13c

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9466303c-b53e-40ec-9065-0da94c7dc13c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9466303c-b53e-40ec-9065-0da94c7dc13c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9466303c-b53e-40ec-9065-0da94c7dc13c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9466303c-b53e-40ec-9065-0da94c7dc13c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9466303c-b53e-40ec-9065-0da94c7dc13c
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


the computer is like 2 weeks old, i decided to wait until the new ubuntu was released to put it on.  windows worked great until ubuntu.  windows does still work great it just won't stay on!  i use windows to send movies and music to my ps3.  i noticed that would cause the computer to restart for some reason.  it never did that before ubuntu.  so i decided to load up windows and do nothing... it friggin' restarted lol!  ubuntu does NOT restart, ever, however.  wtf!

---

### Post by handydan918 on 2008-11-02
> **lbarnes said:**
> hey guys, i've never had this problem before, but if i leave my computer in windows the computer will restart after awhile, and when i come back ubuntu is loaded up.  in the grub under other os it has "windows/vista (loader)" listed two times, which i've never seen the loader part before.  on my old comuter it was just windows xp professional, so i don't know what the (loader) business is.  the computer does not restart if i leave ubuntu on like i did last night.

thanks guys

+1 on the virus issue. Very likely, windows has been rebooting all along, but why would you notice? If windows is running, you leave, it reboots, and windows is still running when you come back, nothing happened that you know about, right? Now you have Ubu as default O/S in the bootloader program, and when windows crashes (as it inevitably does) Ubuntu comes up instead. 
Your Windows machine may very well have been bot-netted. I would check it over very carefully with a good security program. AVG and Avast are two pretty good ones that are available free.

---

### Post by lbarnes on 2008-11-02
guys, it's not a virus lol!
i would've known if it restarted on its own, come on guys!
i constantly have some process going on with this thing.
it started as soon as i installed ubuntu.
it's really annoying because i like vista better for some things
and i've gotta restart to get it back into vista lol!

---

