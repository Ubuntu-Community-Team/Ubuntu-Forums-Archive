---
title: "ubuntu and xp boot matters"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by egebilmuh on 2008-10-15
firstly hi  forum guys, it is  my first  post .i m  ibrahim Y&#305;lmaz and i m student in ege university Computer Engineering dep. in izmir.I m  using  generally  windows xp , but i would try  ubuntu OS so as to  develop  my Object Oriented programing Course project(becoz i think  why i  dont  java project linux OS so i  have set up i m impartial  regarding Operating Sistem). later i set up Ubuntu ,i cant  open my Windows Xp, also  i dont delete  my Windows  im sure   that i
i m searching answer this  issue. plz help me  concerning  this issue
which  Strings ll i  write menu.lst ? :(
.> ibrahim@ibrahim-desktop:~$ sudo fdisk -l
[sudo] password for ibrahim:

Disk /dev/sda: 80.0 GB, 80026361856 bayt
255 heads, 63 sectors/track, 9729 cylinders
Units = silindir of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3cce3cc

   Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;  BlokSay&#305;s&#305; Kml Sistem
/dev/sda1               2        6374    51191122+   f  W95 Ext'd (LBA)
/dev/sda2   *        6375        7054     5462100   83  Linux
/dev/sda5               2        6374    51191091    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bayt
255 heads, 63 sectors/track, 9729 cylinders
Units = silindir of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd844d844

   Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;  BlokSay&#305;s&#305; Kml Sistem
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS
ibrahim@ibrahim-desktop:~$ 



                                                         Thanks A lot
                                                         Forum Guys

---

### Post by TheLions on 2008-10-15
if i understanded you right, you cannot boot into XP, but Ubuntu works fine???

put this in terminal:```
sudo fdisk -l
``` and copy output here

then this:```
 gedit /boot/grub/menu.lst 
``` and copy outpu here.

at end of that file you should have something like this:[HTML]title		Windows Vista
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1[/HTML]

where hd1 is HDDdrive and 0 is partition 0

in your case is should be root (hd0,1)

---

### Post by egebilmuh on 2008-10-15
```
sudo fdisk -l

Outputs===>


Disk /dev/sda: 80.0 GB, 80026361856 bayt
255 heads, 63 sectors/track, 9729 cylinders
Units = silindir of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3cce3cc

   Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;  BlokSay&#305;s&#305; Kml Sistem
/dev/sda1               2        6374    51191122+   f  W95 Ext'd (LBA)
/dev/sda2   *        6375        7054     5462100   83  Linux
/dev/sda5               2        6374    51191091    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bayt
255 heads, 63 sectors/track, 9729 cylinders
Units = silindir of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd844d844

   Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;  BlokSay&#305;s&#305; Kml Sistem
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS

```

```
gedit /boot/grub/menu.lst
 Outputs======>


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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=45279bf3-91ad-4e0e-9338-d31a30985392 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
default 1
//i write  it new  after  ur  post
timeout 5
title		Windows Vista
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=45279bf3-91ad-4e0e-9338-d31a30985392 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=45279bf3-91ad-4e0e-9338-d31a30985392 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST
```

firstly thanks  ur Attention bro,
i have 2  HDD(80GB - 80 GB) one  is  my  back up HDD(80  gb), another one is my OS  HDD s

---

### Post by TheLions on 2008-10-15
did you changed[HTML] root		(hd1,0) [/HTML] to [HTML]root	(hd0,1)
[/HTML]

and does it work???

---

### Post by Orange_and_Green on 2008-10-15
Hello,

I think you should remove the text you've added, which is this
```
default 1
//i write  it new  after  ur  post
timeout 5
title		Windows Vista
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```


and add this instead
```

title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Good luck :KS

---

### Post by caljohnsmith on 2008-10-15
> **egebilmuh said:**
> ```

Disk /dev/sda: 80.0 GB, 80026361856 bayt
255 heads, 63 sectors/track, 9729 cylinders
Units = silindir of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3cce3cc

   Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;  BlokSay&#305;s&#305; Kml Sistem
/dev/sda1               2        6374    51191122+   f  W95 Ext'd (LBA)
/dev/sda2   *        6375        7054     5462100   83  Linux
[COLOR="Blue"]/dev/sda5               2        6374    51191091    7  HPFS/NTFS[/COLOR]

Disk /dev/sdb: 80.0 GB, 80026361856 bayt
255 heads, 63 sectors/track, 9729 cylinders
Units = silindir of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd844d844

   Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;  BlokSay&#305;s&#305; Kml Sistem
[COLOR="Blue"]/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS[/COLOR]

```

So is your Windows on the same drive as Ubuntu, in partition sda5, or is Windows on sdb1 on your other drive?

TheLions: changing his Windows entry to (hd0,1) won't help because that is sda2, or his Ubuntu partition. :)

---

### Post by caljohnsmith on 2008-10-15
> **Orange_and_Green said:**
> 
and add this instead
```

title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Good luck :KS
His Windows could only be on sda5 (hd0,4) or sdb1 (hd1,0), so I don't think the above entry is going to help him. :)

---

### Post by Orange_and_Green on 2008-10-15
> **caljohnsmith said:**
> His Windows could only be on sda5 (hd0,4) or sdb1 (hd1,0), so I don't think the above entry is going to help him. :)

You're so right, that's an extended partition with sda5 as the logical unit. Sorry, and thanks!! ... I guess I need some rest...

---

