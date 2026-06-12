---
title: "[SOLVED] Problem with Unetbootin - Windows no longer boots..."
date: 2008-10-12
forum: New to Ubuntu
---

### Post by volneilo on 2008-10-12
Absolute newbie problem: installed Unetbootin in order to create a live USB with Puppy Linux. Carelessly I sent the installation to my Windows partition instead of the USB flash drive one... Now, every time I choose Windows in the GRUB menu, it loads Puppy. I've checked and confirmed that Windows installation is already there, but inaccessible. I've made many attempts to restore GRUB, including re-writing MBR, but it always points to Puppy instead of Windows... Could someone help me? Oh, and excuse me for the poor english... I'm from Brasil.
Thanks in advance!

---

### Post by drowner on 2008-10-12
I'm not sure if this is an Ubuntu problem... 

From what I understand about Unetbootin, it just installs an operating system like normal, only it doesn't need a CD....so, here it would have installed puppy linux to the drive you specified -  are you 100% sure you haven't written over your windows partition with puppy linux?

---

### Post by Patb on 2008-10-12
> **volneilo said:**
> I've checked and confirmed that Windows installation is already there, but inaccessible.Volneilo, how have you checked? If you mean you can see windows files on that partition, that is just because Puppy is so small that there are still lots of files from your old Windows installation on the same partition.  Ultimately, you may have to back up all your own files and reinstall Windows.  Boa sorte!

Cheers, Pat.

PS Edit: I presume the Grub menu does not give a "Puppy" option in addition to the "Windows" option you mention. Please let us know if I have it wrong.

---

### Post by volneilo on 2008-10-12
Yes, I agree it isn't a Ubuntu problem... but since I got no help with this problem, and I'm an Ubuntu user, I'm asking for help from my fellows here, where I belong...  I'm pretty shure Puppy didn't over writed Windows because I can still access my "C:" through Ubuntu, and everything is already there... But there is no way to make GRUB boot Windows again. I've deleted all Puppy files that I could find in Windows drive, but GRUB's entry named "WINDOWS" calls a Linux loader, that complains about not finding Linux kernel image (because, of course, it isn't there no more...).

---

### Post by volneilo on 2008-10-12
Pat, thank you for responding. Yes, I assumed my Windows wasn't destroyed because I saw many files in the drive, as you said. And no, the GRUB didn't shown a "PUPPY" entry; instead of it shown a "WINDOWS" entry that calls Puppy... Just to be absolutely shure, there might be a way to make GRUB point to Windows again, wouldn't it? In this case, I think that, if my Windows installation is really ruined, in this case the option would lead to an empty hole and I would know for shure.

---

### Post by RealG187 on 2008-10-12
> **Patb said:**
> Volneilo, how have you checked? If you mean you can see windows files on that partition, that is just because Puppy is so small that there are still lots of files from your old Windows installation on the same partition.  Ultimately, you may have to back up all your own files and reinstall Windows.  Boa sorte!

Cheers, Pat.

PS Edit: I presume the Grub menu does not give a "Puppy" option in addition to the "Windows" option you mention. Please let us know if I have it wrong.

You can have puppy and Linux on the same partition? So will it go on a fat/ntfs partition?

---

### Post by drowner on 2008-10-12
I'm not sure how Puppy installs.... whether it makes it's own partition or what.

tell us a bit about how your computer is set up, and could you post the output of the following commands?

```
sudo fdisk -l
``` (that's a little L)

and 

```
cat /boot/grub/menu.lst
```

---

### Post by volneilo on 2008-10-12
Hi, RealG187. You meant Puppy and Windows? Well, the installer put Puppy in my Windows partition, which is (was?) FAT32. And I could access Puppy a couple of times before deleting his files...

---

### Post by volneilo on 2008-10-12
Ok drowner, here it goes:

volnei@volnei-desktop:~$ sudo fdisk -l
[sudo] password for volnei: 

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f679b6b

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1        1912    15358108+   c  W95 FAT32 (LBA)
/dev/sda2            1913        3000     8739360    b  W95 FAT32
/dev/sda3            3001        4865    14980612+   5  Estendida
/dev/sda5            3001        3062      497983+  82  Linux swap / Solaris
/dev/sda6            3063        4865    14482566   83  Linux


and:

volnei@volnei-desktop:~$ cat /boot/grub/menu.lst
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
timeout		20

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$qwH8f$CxPl8emdOuzxVAYbQHc8D/
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
# kopt=root=UUID=1caedc79-5848-4986-aab2-28e298e68dc2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=splash locale=pt_BR quiet

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1caedc79-5848-4986-aab2-28e298e68dc2 ro splash locale=pt_BR quiet
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1caedc79-5848-4986-aab2-28e298e68dc2 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=1caedc79-5848-4986-aab2-28e298e68dc2 ro splash locale=pt_BR quiet
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=1caedc79-5848-4986-aab2-28e298e68dc2 ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

(sorry, I don't know how to put it in a window...)

---

### Post by volneilo on 2008-10-12
I have two FAT32 partitions, one of them with Windows system and another with data (documents and personal files). The other (extended) is Ubuntu, with a SWAP partition.

---

### Post by RealG187 on 2008-10-12
If it was installed on the windows partition and the windows installation is there, then it didn't format the partition, which means it would have to be in whatever filesystem was there before, and Windows only runs off FAT or NTFS, which version of windows is it? If it's 9x, then it has to be fat (fat32 for 98 but not 95). If it's 2000 and up, it's probably NTFS unless you specified specifically for it to be fat32 (dont know why one would want that).

---

### Post by Patb on 2008-10-13
Volneilo, if all your XP files are still there, you might try fixing the MBR (master boot record) using a Windows XP install CD or (possibly better) a Super Grub Disk. See [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm). Let us know how you go. 

(RealG187, fdisk shows the partition is FAT32. I'm assuming Windows is XP from the menu.lst entry.)

Cheers, Pat

---

### Post by volneilo on 2008-10-13
RealG187, my Windows partitions are FAT32, as you can see by the commands outputs I posted before. I choose FAT in my last reinstallation, can't remember what reason.
Funny, Puppy was installed INSIDE a FAT32 partition! How could it be?

---

### Post by volneilo on 2008-10-13
Pat, I already tried Super Grub Disk, in all options (as I mentioned in my first post), unfortunately without success. GRUB always lead me to boot Puppy, and this is my point. If I had a damaged Windows installation, I would know because the whole thing should hang upon the boot. But no, the entry named 'WINDOWS' in the GRUB always leads to an Isolinux, or Syslinux (can't remember) boot loader that calls Puppy.

It's Windows XP Professional SP3, sorry for not to mention that.

---

### Post by Patb on 2008-10-13
> **volneilo said:**
> Funny, Puppy was installed INSIDE a FAT32 partition! How could it be?
That is the way Unetbootin puts the operating system onto a USB stick. It uses "squashfs" compression on FAT32 format and boots from there. Your current boot labelled (wrongly) "Microsoft Windows XP Professional" leads the boot process to start Puppy from this compressed OS which is located in one of the files on your Windows partition. There is some hope however that your Windows files are not damaged. The question seems to be how to check and how to get the boot sequence changed. 

Cheers, Pat.

---

### Post by louieb on 2008-10-13
To fix the boot sector of your widows drive. 
With the Windows install CD boot to the recovery console. the command you want to run is ```
fixboot c:
```If you don't have an install CD just Google fixboot. Believe theres some other rescue CD out there that have that program to.
Good Luck

---

### Post by adrian15 on 2008-10-13
> **volneilo said:**
> Now, every time I choose Windows in the GRUB menu, it loads Puppy. I've checked and confirmed that Windows installation is already there, but inaccessible.

You just need to edit your C:\boot.ini from a live cd or a working linux and add the lines that boot Windows.

Something like this:

```

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" /fastdetect

```

should work for most of the situations.

You can still leave there the puppy linux entry if you want to.

adrian15

---

### Post by volneilo on 2008-10-13
Thanks, fellows, for your attention. 

louieb, I've already tried fixboot, without success.

adrian15, I've checked the file C:\boo.ini, it's the way you described above, but still don't work. I've tried including your excellent Super Grub Disk (all options I thought could be helpful), but got nothing. GRUB still points to Puppy.

The only option I had no courage to use is "fixmbr", because of all the alert messages I got. Could it be the way?

---

### Post by volneilo on 2008-10-13
I wish to thank again everyone who helped me in this trouble. Just fixed the problem running **fixboot** (louieb was right). I had done it before, but I think it didn't work because I miss the parameter "C:" after the command...

Cheers to all!!!

---

### Post by RealG187 on 2008-10-13
> **volneilo said:**
> Puppy was installed INSIDE a FAT32 partition! How could it be?

That's why I was confused. Maybe that's the problem...

---

### Post by Patb on 2008-10-13
> **RealG187 said:**
> That's why I was confused. Maybe that's the problem...
Realg, isn't that simply because the main parts of the Puppy OS are installed not exactly on the partition but within a compressed file on that partition? (See my post #15). Unetbootin did not install Puppy, it created a bootable "disk" on the FAT32 partition. 

Or have I missed something?

Cheers, Pat.

---

### Post by RealG187 on 2008-10-13
Did he redirect Unetbootin to his windows drive instead of USB? I thought he ran the installer.

If he used Unetbootin then it could be on fat32 because my flashdrive I made with Unetbootin is fat32.

---

### Post by Patb on 2008-10-14
> **RealG187 said:**
> Did he redirect Unetbootin to his windows drive instead of USB?
Yes, he did. See the OP.

Cheers, Pat

---

