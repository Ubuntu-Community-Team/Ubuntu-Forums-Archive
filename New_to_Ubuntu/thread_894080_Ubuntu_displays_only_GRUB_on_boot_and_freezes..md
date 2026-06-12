---
title: "Ubuntu displays only GRUB on boot and freezes."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Cord_ on 2008-08-18
I use a MacBook and duel boot OS X and Ubuntu. Everything was working fine until I booted into OS X to get a file to move over to Ubuntu via USB flash drive. Once I got the file, I rebooted to Ubuntu. The computer then stopped loading and displayed only the word GRUB with a blinking line ( _ ) beside it.

I tried to search for a fix for the last 30 mins but no luck. Anyone know what is wrong?

I think I'm using Ubuntu 8.04 32bit. The computer had been working fine for the past 3 days. I use Bootcamp to duel boot with a 60GB hard drive, 40GB for OS X and 20GB for Ubuntu.

---

### Post by neurostu on 2008-08-19
Can you boot the liveCD?

---

### Post by Cord_ on 2008-08-19
I can use the live CD and still boot into OS X

---

### Post by Cord_ on 2008-08-19
Fixed it! I found out how to restore the GRUB here...

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

What I did was...

1. Boot in livecd
2. open terminal
3. sudo grub
In the grub terminal
4. find /boot/grub/stage1
It returned (hd0,5)
5. root (hd0,5)
6. setup (hd0)
7. Restart

Note- in step 4, I got a return of (hd0,2) and (hd0,3) but I picked (hd0,3) for step 5 because I had no idea what I was doing and it was closer to (hd0,5). haha

This worked for me but If anyone has any idea why this issue happened in the first place, please do share.

---

### Post by caljohnsmith on 2008-08-19
Because you didn't know which partition to choose after "find /boot/grub/stage1" returned two different partitions, you may run into problems in the future if you don't know which OS is in your (hd0,3) partition (or sda4). For instance, your /boot/grub/menu.lst may not get updated with your latest kernel upgrades if Grub is using the menu.lst in the wrong OS.

If you want to prevent future confusion/problems, I would recommend booting up a Live CD and posting the output of:
```
sudo fdisk -lu
```
And also post the output of:
```
sudo mkdir /mnt/sda4
sudo mkdir /mnt/sda3
sudo mount /dev/sda4 /mnt/sda4
sudo mount /dev/sda3 /mnt/sda3
cat /mnt/sda4/boot/grub/menu.lst
cat /mnt/sda3/boot/grub/menu.lst
```
Then we can help you make sure everything is in order.

---

### Post by Cord_ on 2008-08-19
There's a lot of stuff that was displayed; I hope you don't mind. The results are as followed.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  EFI GPT
/dev/sda2   *      409640    73547815    36569088   af  Unknown
/dev/sda4        73547816   116175193    21313689   83  Linux

----------------------------------------------------------------

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda4
mkdir: cannot create directory `/mnt/sda4': File exists
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda3
mkdir: cannot create directory `/mnt/sda3': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt/sda4
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/sda3
mount: special device /dev/sda3 does not exist
ubuntu@ubuntu:~$ cat /mnt/sda4/boot/grub/menu.lst
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
# kopt=root=UUID=3d777953-e5dc-488c-94ca-36eac3f70149 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3d777953-e5dc-488c-94ca-36eac3f70149 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3d777953-e5dc-488c-94ca-36eac3f70149 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$ cat /mnt/sda3/boot/grub/menu.lst
cat: /mnt/sda3/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-08-19
That's good news, Cord_: it looks like using (hd0,3) was indeed the correct partition when setting up grub, so your guess was correct. :)

---

### Post by Cord_ on 2008-08-19
Great. Thanks for your help.

---

