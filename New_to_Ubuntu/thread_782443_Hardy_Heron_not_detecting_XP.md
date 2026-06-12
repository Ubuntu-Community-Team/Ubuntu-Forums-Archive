---
title: "Hardy Heron not detecting XP"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Tb0ned on 2008-05-05
I decided to give Linux a shot and installed Hardy Heron, the only bad thing is that it is not detecting my XP install. While I'm liking Hardy Heron I got some important school type stuff on my windows partition. Is there anyway to make XP appear in Grub so I can actually boot windows. Out of my 500GB hard drive I have Hardy Heron on two partitions (Swap and Ext3) and then windows on another NTFS partition. How do I go about making everything play nice?

---

### Post by tamoneya on 2008-05-05
post the contents of /boot/grub/menu.lst as well as the result of```
sudo fdisk -l
```
This is a fairly simple and common problem.  We should get you up and running shortly.

---

### Post by Tb0ned on 2008-05-05
Here's the result of sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8db28db2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         522     4192933+  82  Linux swap / Solaris
/dev/sda2             523       60800   484183035    f  W95 Ext'd (LBA)
/dev/sda5             523        2480    15727603+  83  Linux
/dev/sda6            2481       60800   468455368+   7  HPFS/NTFS


/boot/grub/menu.lst

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
# kopt=root=UUID=38a92aa9-c3c7-4381-bcb5-d29cc622b722 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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



Also on a totally unrelated note do you do any drafting or solid modeling on that Quadro?

---

### Post by tamoneya on 2008-05-05
add this to the bottom of menu.lst
```
 title Windows XP
root (hd0,5)
makeactive
chainloader +1
```

---

### Post by Tb0ned on 2008-05-05
## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=38a92aa9-c3c7-4381-bcb5-d29cc622b722 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=38a92aa9-c3c7-4381-bcb5-d29cc622b722 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



Forgot this little bit

---

### Post by Tb0ned on 2008-05-05
The end of the file now looks like this:

## ## End Default Options ##

title 		Windows XP
root 		(hd0,5)
makeactive
chainloader +1

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=38a92aa9-c3c7-4381-bcb5-d29cc622b722 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=38a92aa9-c3c7-4381-bcb5-d29cc622b722 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Using this configuration I got this error:

Error 12: Invalid Device Requested

---

### Post by tamoneya on 2008-05-05
oops i thought that the NTFS partition was the OS partition but you have two windows partitions change (hd0,5) to (hd0,1)

---

### Post by Tb0ned on 2008-05-05
Huh, I do only have one windows ntfs partition which my OS is on. When I put in (hd0,1) I got: Error 12: Invalid Device Requested.

---

### Post by tamoneya on 2008-05-05
okay i was just having trouble figuring out which partition your OS is on.  You also have a FAT32 partition which was confusing me.  So it should definately be (hd0,5) but I am not sure why that is failing.  I have looked at my menu.lst on my laptop which is setup similarly and it is identical except that it also has the line "savedefault" like this ```
title Windows XP
root (hd0,5)
savedefault
makeactive
chainloader +1
``` One other difference is that I have the windows grub option after my ubuntu options.  This will affect the OS that loads by default and if you want ubuntu to load by default you should probably move it to the bottom.

None of this however seems to solve the error 12 problem.  Anyone else have any ideas about the error.  When you are in ubuntu (liveCD or installed) are you able to mount the NTFS partition:```
sudo mkdir /windows
sudo mount -t ntfs /dev/sda5 /windows
```

---

### Post by Tb0ned on 2008-05-05
paul@Tom-Servo:~$ sudo mkdir /windows
[sudo] password for paul: 
mkdir: cannot create directory `/windows': File exists
paul@Tom-Servo:~$ sudo mount -t ntfs /dev/sda5 /windows
NTFS signature is missing.
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
paul@Tom-Servo:~$ sudo mount -t ntfs /dev/sda2 /windows
NTFS signature is missing.



Apparently my windows partition is just not liking to be read...

---

### Post by Helios38 on 2008-05-05
all else fails, you can pop in th XP disk, reboot, press R at the greet screen, and do "fixmbr" once u get to the prompt

---

### Post by Michl on 2008-05-05
YOu need to put the windows information below the line
that says:

### END DEBIAN AUTOMAGIC KERNELS LIST


For example, in my case it looks like this:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by jimv on 2008-05-05
I don't think the problem is Grub.  Can you paste in the contents of the boot.ini file in Windows?

By the way, I noticed that you tried to mount /dev/sda5 for Windows.  Your XP partition is /dev/sda6 according to your fdisk -l output.

*Boot.ini should be on the root of your Windows drive.

---

### Post by Tb0ned on 2008-05-05
I do have the information below the line but somehow it's still not working.

Here's the content of my Boot.ini.backup
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by jimv on 2008-05-05
Try changing the 3 in the partition(3) to 6 in both places in the boot.ini file.  (not boot.ini.backup)

---

### Post by Tb0ned on 2008-05-05
Alright, horrible horrible newbie question. How do I get at boot.ini from inside Ubuntu?

---

### Post by jimv on 2008-05-05
Did you ever manage to get your XP partition mounted so you could see the files?

try this command if you haven't: sudo mount -t ntfs /dev/sda6 /windows

---

### Post by Tb0ned on 2008-05-05
I did get Ubuntu to read my XP partition. Not knowing where to find boot.ini I just did a search for it but only got boot.ini.backup. Maybe this is my problem...

---

### Post by jimv on 2008-05-05
Did you delete any partitions to get Ubuntu installed?  Some computers come with a small ntfs or fat partition as the first partition that has restore info and the Windows boot file on it.

Do you see either of these files on the XP partition:  NTLDR and NTDETECT.COM (should be right on the root of the drive)?  If not, you're gonna need your XP disk (if you have one) and you can find both of those files in the i386 folder on the disk.  Copy them right onto the root of your Windows drive.  Then make a copy of that boot.ini.backup file that you found and put it on the root of the Windows drive.  Remember to change the 3 to a 6 for the partition number in the boot.ini.

---

### Post by Tb0ned on 2008-05-05
To the first question when I first built the computer I initially put in three partitions (One for windows, one for swap, and one for Ubuntu) My windows partition ended up being the third so it's E:/. Throughout using windows through I accidentally formatted my swap partition into NTFS but that was taken care of during the Ubuntu install or at least I thought it would be.

To the second suggestion I put all those files, backed up boot.ini.backup, changed the name of one copy to boot.ini, and then made the changes. When I booted up I got the same error. Error 12: Invalid Device Requested

---

### Post by frodon on 2008-05-05
If your partition number entered in menu.lst is correct then i suggest you to reinstall GRUB in case the default install did not install it in the MBR.
You will find instructions for doing this here :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4)

An incorrect partition number for your windows partition in your menu.lst is known to generate such error so check it twice before reinstalling GRUB.

I'm not sure there's anything wrong on your windows partition.

---

### Post by jimv on 2008-05-05
The odd thing here is that when you did the fdisk -l, we have sda1,2,5,6...3 and 4 are missing.  SO what I'm wondering now is does Grub go by the hda number, or the order that the partition is on the drive.  So it's hda6 for Ubuntu, but maybe it's hd0,3 (fourth partition) for Grub.  Try changing that in the menu.list and then make the boot.ini point to partition(4)

---

### Post by frodon on 2008-05-05
No it's normal, it depends how you proceeded when you did your partitions. GRUB use the  partition number **[COLOR="Red"]-1[/COLOR]** to select the partition to boot therefore if your windows partition is sda6 then the corresponding grub entry will be (hd0,5) as suggested.

So follow Michl's example and put your windows entry at the end of the file like suggested and if it still doesn't work try to reinstall GRUB using the instructions in the link i gave you.

---

