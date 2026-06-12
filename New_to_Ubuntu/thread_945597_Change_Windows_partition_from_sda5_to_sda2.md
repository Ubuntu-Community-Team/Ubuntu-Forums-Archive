---
title: "Change Windows partition from sda5 to sda2"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by bodzasfanta on 2008-10-12
I did install Intrepid Ibex a few days ago. Now my HDD is messed up... Ubuntu works perfectly but I can't boot to Windows.

sda5 - windows xp
sda2 - home files
sda3 - ext3 ubuntu
sda4 - swap

What I want is to change sda5 to sda2. I know, I can't do it with Gparted, I need to use fdisk. Can anyone help me?

---

### Post by SuperSonic4 on 2008-10-12
What if you edit your /boot/grub.list file (or similar) and change sda5 to sda2

---

### Post by Orange_and_Green on 2008-10-12
I'm sorry but I'm afraid I don't quite follow... You mean /dev/sda1 is an extended partition with a logical disk /dev/sda5 with windows? So basically, you would like /dev/sda1 to be a primary partition with windows on it instead? Is that what you are asking, or am I missing the point here somewhere?

---

### Post by bodzasfanta on 2008-10-12
Sorry, if you don't understand me... 

Yes, thats what I want.

---

### Post by WWSmith36 on 2008-10-12
It is strange to see windows on sda5, a logical partition.  Did you have other versions of windows on the machine before you installed ubuntu?  

Anyway, We may be able to help you boot windows.  Please post the output of

```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

Thank you

---

### Post by bodhi.zazen on 2008-10-12
Windows needt to be on a primary partition.

I agree that your partition numbers seem off.

You can use gparted to copy - paste (move) your windows patition

Or if it is on a primary partition already, let us know and I will show you how to re-write your partition table with fdisk.

---

### Post by bodzasfanta on 2008-10-12
I had Windows XP SP3 on the laptop. I've installed Ubuntu so many times but this was surprising to me also... 

```
bodzasfanta@bodzasfanta-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
15 heads, 63 sectors/track, 248086 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf407fbe7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             945    55294784    27646920    f  W95 Ext'd (LBA)
/dev/sda2        55295730   217457729    81081000    7  HPFS/NTFS
/dev/sda3       217457730   233611559     8076915   83  Linux
/dev/sda4       233611560   234441269      414855   82  Linux swap / Solaris
/dev/sda5   *        1008    55294784    27646888+   7  HPFS/NTFS

```

```
bodzasfanta@bodzasfanta-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=6eb9bf45-6e3c-47f0-9e1e-782fb53ae396 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6eb9bf45-6e3c-47f0-9e1e-782fb53ae396 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6eb9bf45-6e3c-47f0-9e1e-782fb53ae396 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional - magyar
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by bodzasfanta on 2008-10-12
Looks like this:

[IMG]http://img184.imageshack.us/img184/3262/kpernykpdevsdagpartedbm0.png[/IMG]

---

### Post by WWSmith36 on 2008-10-12
I would simple try and edit to your menu.lst file.  It looks like the root command is pointing to the wrong parition.  Currently is set to sda2

```
gksudo gedit /boot/grub/menu.lst
```

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional - magyar
root		(hd0,1)
savedefault
makeactive
chainloader	+1

I would change this to

title		Microsoft Windows XP Professional - magyar
rootnoverify	(hd0,4)
chainloader	+1

Hope this helps

---

### Post by bodhi.zazen on 2008-10-12
No, that will not work. Widows needs to be on a primary partition.

You can do this one of two ways.

First , resize sda2 and move sda5. Then delete sda1 and move sda5 to sda1 (graphically move the expended partition into an extended space).

IMO it is easier to use fdisk.

Boot a live CD

then :

```
sud fdisk /dev/sda
```

Now delete the sda5 and sda1 partitions and make a new primary partition the size of sda1.

See  [http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

dont worry, deleting a partition with fdisk does not delete data.

The commands in fdisk will be :

d # delete sda5
d # delete sda1

n # for new partition
p # for primary partition

1 # to make it sda1

Use all the space (go with the default).

Then write the partition table to disk

w

reboot to hard drive

You will need to change the grub stanza to boot windows to 

root (hd0,0)

---

### Post by handydan918 on 2008-10-12
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1            945    55294784    27646920    f  W95 Ext'd (LBA)
/dev/sda2        55295730   217457729    81081000    7  HPFS/NTFS
/dev/sda3       217457730   233611559     8076915   83  Linux
/dev/sda4       233611560   234441269      414855   82  Linux swap / Solaris
/dev/sda5   *        1008    55294784    27646888+   7  HPFS/NTFS

Interesting...sda1 seems to be a restore partition or something? sda2 and sda5 both seem to be windows partitions, so why is sda5 flagged as bootable? and isn't it interesting that sda1 and sda7 are so close to identical in terms of their location and size on the disk?

---

### Post by bodhi.zazen on 2008-10-12
> **handydan918 said:**
> Interesting...sda1 seems to be a restore partition or something? sda2 and sda5 both seem to be windows partitions, so why is sda5 flagged as bootable? and isn't it interesting that sda1 and sda7 are so close to identical in terms of their location and size on the disk?

It appears to me as if the  primary partition was somehow moved to an extended partition.

If you look at the blocks and you understand the partitioning scheme it makes more sense.

sda1 is an extended partition blocks             945    -> 55294784

sda5 is a logical partition within the extended partition blocks        1008    -> 55294784

Marked as bootable is almost irrelevant. You must have one partition marked as bootable for your bios and windows uses this flag as well.

---

### Post by meierfra. on 2008-10-12
```
 Windows needs to be on a primary partition.
```

Not necessarily.

More importantly, I suggest not to  follow bodhi.zazen's advice to use "fdisk" to turn sda5 into a primary partition. If you do that, the partition will probably  not  match up with the file system, and you will not be able access your Windows Partition.  It would be better to first use "testdisk" to examine  your partition table.

---

### Post by bodhi.zazen on 2008-10-12
> **meierfra. said:**
> ```
 Windows needs to be on a primary partition.
```This is plainly wrong.

More importantly, do  NOT follow bodhi.zazen's advice to use "fdisk" to turn sda5 into a primary partition. If you do that, the partition will not match up with the file system, and you will not be able access your Windows Partition in any way.

Would you kindly provide a link to back up your claims ?

---

### Post by handydan918 on 2008-10-12
> **bodhi.zazen said:**
> 
Marked as bootable is almost irrelevant. You must have one partition marked as bootable for your bios and windows uses this flag as well.
A remarkable statement, ""Almost irrelevant."
Sounds suspiciously like "Almost pregnant".

---

### Post by meierfra. on 2008-10-12
There is a small chance that WWSmith36 suggestion will work. So try that first. 


Did you delete any partition while installing Ubuntu?
Want kind of error messages to you get when  you try to boot XP?
Are you able to mount sda2 and sda5 in Ubuntu?

---

### Post by bodzasfanta on 2008-10-13
@bodhi.zazen
That won't help me because both sda2 and sda5 are full of. I mean, just a few gigs of free space are available. I think the only solution is to move out everything from sda5 to an external HDD and than reinstall Windows.

@meierfra.
I didn't delete any partitions. 

I can mount both sda2 and sda5 partitions. I can access to files too (edit, delete, read...).

I get the missing hal.dll error message when I try to boot Windows.

---

### Post by bodzasfanta on 2008-10-13
I tried WWSmith36's method so I changed
```
title Microsoft Windows XP Professional - magyar
root (hd0,1)
savedefault
makeactive
chainloader +1
```

to this

```
title Microsoft Windows XP Professional - magyar
rootnoverify (hd0,4)
chainloader +1
```

After reboot I get an error message, says "HDD reading problems" (Or something like that. It was in hungarian)

---

### Post by bodzasfanta on 2008-10-13
I've installed testdisk and adter the analyze I got this

```
Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 E extended LBA             0  15  1  3441 239 63   55293840

Bad relative sector.
Warning: Incorrect number of heads/cylinder 15 (NTFS) != 255 (HD)
 2 * HPFS - NTFS           3442   0  1 13536  29 63  162162000
 3 P Linux                13536  30  1 14541 164 63   16153830
 4 P Linux Swap           14541 165  1 14593  74 63     829710
Logical partition must not be bootable
Warning: Incorrect number of heads/cylinder 15 (NTFS) != 255 (HD)
 5 L HPFS - NTFS              0  16  1  3441 239 63   55293777

Bad relative sector.

```

---

### Post by meierfra. on 2008-10-13
> I can mount both sda2 and sda5 partitions. I can access to files too (edit, delete, read...).

I get the missing hal.dll error message when I try to boot Windows. 


The hal.dll error usually means that you have to edit "boot.ini"

Mount /dev/sda2 and open the file "boot.ini".

the file should look something like this:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows Xp Home Edition" /fastdetect

Look for the two appearances of  "partition(?)"  and change them to "partition(4)"  

Don't change anything else.

Hopefully that is enough to solve your problem. 

(use "root (hd0,1)" in menu.lst, just as it used to be)

---

