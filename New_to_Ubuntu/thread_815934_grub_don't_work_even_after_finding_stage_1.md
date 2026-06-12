---
title: "grub don't work even after finding stage 1"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by defenestratos on 2008-06-02
> hugo@hugo-laptop:~$ sudo grub Password:
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
grub> root (hd0,0)
root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
hugo@hugo-laptop:~$


After I do this and reboot it still doesn't work and I need to use live cd and choose boot from first hard drive

How can I just get the normal grub menu?

---

### Post by bumanie on 2008-06-02
Boot the live cd and post output of > sudo fdisk -l (That's a lower case L).

---

### Post by Xiong Chiamiov on 2008-06-02
[SuperGrubDisk]("http://supergrubdisk.org") will save you a lot of time.

---

### Post by defenestratos on 2008-06-02
hugo@hugo-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       29070    14651248+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/hda2           29071      116280    43953840    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/hda3               1           1           0+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5           29071      108519    40041981   83  Linux
/dev/hda6          108519      112583     2048256   82  Linux swap / Solaris
/dev/hda7          113157      116280     1574338+  83  Linux
/dev/hda8          112583      113157      289138+   6  FAT16

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7649    61440561    c  W95 FAT32 (LBA)
/dev/sda2            7650       28899   170690625   83  Linux
/dev/sda3           29421       30401     7879882+  83  Linux
/dev/sda4           28900       29420     4184932+   6  FAT16

Partition table entries are not in disk order
hugo@hugo-laptop:~$
hugo@hugo-laptop:~$

---

### Post by sayakb on 2008-06-02
Since you can boot into Ubuntu, try reinstalling GRUB
```
sudo apt-get install --reinstall grub
```

---

### Post by meierfra. on 2008-06-03
Try switching the boot order in the bios to boot of you other hard drive.

If that did not help:

We need more information.

What happens during boot up?
Does the grub menu appear? (press "Esc" during boot up)
Do you get any error messages?

Post your menu.lst:

```
sudo  mkdir /ubuntu
sudo mount -t ext3 /dev/hda1  /ubuntu
gksudo gedit /ubuntu/boot/grub/menu.lst

```

---

### Post by defenestratos on 2008-06-03
> **meierfra. said:**
> Try switching the boot order in the bios to boot of you other hard drive.

If that did not help:

We need more information.

What happens during boot up?
Does the grub menu appear? (press "Esc" during boot up)
Do you get any error messages?

Post your menu.lst:

```
sudo  mkdir /ubuntu
sudo mount -t ext3 /dev/hda1  /ubuntu
gksudo gedit /boot/grub/menu.lst

```

I reinstalled grub no go. When I boot it says > non-bootable device in drive 
H or something. I canT be more specific because I have to go to work.I will find out exactly in a few hours. I remember boot sectors from dos. Have I corrupted that somehow?

 Here is Menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-51-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-51-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-51-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-51-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-51-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-51-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title Ubuntu
root (hd0,0)
configfile /wubi/boot/grub/menu.lst



title Ubuntu
root (hd0,6)
configfile /wubi/boot/grub/menu.lst



title Ubuntu
root (hd0,6)
configfile /wubi/boot/grub/menu.lst




---

### Post by meierfra. on 2008-06-03
It really looks like you just need to change  the boot order in the bios.

---

### Post by defenestratos on 2008-06-03
When I go to bios all I can choose is the order of devices, the order is CD, HD, Drive A (Non existent) and LAN.

Whereabouts do I choose which partition to boot?

---

### Post by meierfra. on 2008-06-03
Some bios don't let you change the boot order. 

So you need to install grub to /dev/hda

```
gedit device.map
```
This created an empty file. Type these two lines:
(hd0)  /dev/sda
(hd1) /dev/hda

(no blank lines, but press "enter" at the and of the last line. Actually I don't think this really matters, but better save than sorry) Save the file.  Then 

```
sudo grub --device-map=device.map
```

At the grub prompt

```
 find /boot/grub/menu.lst
```
This is just for double checking. it should return (hd1,0)
Next (still at the grub prompt):

```
root (hd1,0)
setup (hd0)
quit
```


You also need to edit menu.lst:
```
sudo  mkdir /ubuntu
sudo mount -t ext3 /dev/hda1  /ubuntu
cd /ubuntu/boot/grub
sudo cp menu.lst menu.lst.bu
gksudo gedit menu.lst

```

Change all "(hd0,0)" to "(hd1,0)"
(don't forget to change "#groot (hd0,0)" to "#groot (hd1,0)")

Save the file, reboot and hope for the best.

---

### Post by defenestratos on 2008-06-04
when i boot now i still need the live cd to get to the grub list but now when i select ubuntu i get a message saying i cant boot from that drive. Now i need to boot the live cd and from there i can|t access my file system to change my menu.lst back to how it was...

The message without the live cd on boot up is:

Invalid boot sector press h to retry

---

### Post by meierfra. on 2008-06-04
Some bios  refuse to boot a hard drive without a  "boot flag" So try this.
Boot from the LiveCD. Open a terminal and type

```
sudo fdisk -l
```

Check whether you 250GB drive still is /dev/sda (sometimes the Live CD sees it different when Ubuntu.

Then

```
sudo cfdisk /dev/sda  #  Use whatever fdisk told you for the 250 GB drive
```

Select the second partition. Press "enter"  to make it "bootable". Select the "write" tab and press enter again. Then "quit" and reboot. 

Hopefully this will solve you problem.

---

### Post by meierfra. on 2008-06-04
Just in case  that my previous post did not solve your problem: 
This should get you into ubuntu so that you can restore "menu.lst"

Boot from the LiveCD, select "boot from hard drive" and at the grub menu select "ubuntu". But do not press "enter", press "e" instead. Press "e" again.  Change "root (hd1,0)" to  "root (hd0,0)". Press "enter" and then "b" to boot.

This should boot you into ubuntu.

---

### Post by defenestratos on 2008-06-05
that gets me back to ubuntu. is there a difference betweem boot sector and boot device? can i resetup my boot sector?

---

### Post by meierfra. on 2008-06-05
Setting the boot flag did not help?


> Invalid boot sector press h to retry 

This sounds like a messages from your bios. But I'm not sure how to interpret it. Did you get any error messages during  "root (hd1,0)  setup (hd0)"?   You bios don't seem to recognize that "grub" is installed to the MBR of your 250 GB drive.  You might look in your bios and see whether there are any settings you can change. 

You could  also try to physically swap the position of your two hard drives.

---

