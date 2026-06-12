---
title: "[SOLVED] Messed up my boot sequence somehow..."
date: 2008-11-23
forum: New to Ubuntu
---

### Post by trooperchix on 2008-11-23
No clue what happened, I was trying to get a couple of games running under intrepid, I restarted the computer and all of a sudden I'm only offered the boot sequence for another bad partition on my system running hardy.  I need it to start from the intrepid version.  Any ideas how to fix this?  I'm online now running the Intrepid LiveCD version...  <sigh>

---

### Post by ibuclaw on 2008-11-23
Mount the partition with Intrepid installed on and locate your **boot/grub/menu.lst** file and post it's contents in a pastebin:

[http://paste.ubuntu.com]("http://paste.ubuntu.com")

[http://codepad.org]("http://codepad.org")

Regards
Iain

---

### Post by trooperchix on 2008-11-23
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
# kopt=root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04 (8.04) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 
savedefault
boot

---

### Post by ibuclaw on 2008-11-23
If what you have given is correct, then it appears that the Intrepid boot lines have gone byebye.

Just a case of putting them back in.

type in
```
sudo fdisk -l
```
to get the list of partitions on your hard drive and locate the one with Intrepid installed on and make a note of it.

Next, open the boot menu.lst file for editing (use sudo to grant permissions).

And add this immediately after:
```
#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

```

```

title       Ubuntu Intrepid, kernel 2.6.27-7-generic
root        **(hd0,0)**
kernel      /boot/vmlinuz-2.6.27-7-generic root=**/dev/sda1** ro quiet splash
initrd      /boot/initrd.img-2.6.27-7-generic
quiet

```

Except replace "hd0,0" with the location of your Intrepid installation, as found by fdisk -l.
The naming convention is straightforward enough.

ie:
/dev/sda1 = (hd0,0)
/dev/sda2 = (hd0,1)
/dev/sda3 = (hd0,2)
etc...
/dev/sdb1 = (hd1,0)

You should get the general idea of how that works.

The same is with "/dev/sda1", except you insert it as it is shown from the fdisk -l output.

Now save the file and reboot.

If you don't see the new entry, then you've probably made a mistake and printed the wrong boot menu.lst file ;)

Regards
Iain

---

### Post by trooperchix on 2008-11-23
Here's the results of sudo fdisk -l  :

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         369     2963961   83  Linux
/dev/sda2             370       19457   153324360    5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris
/dev/sda6   *         370       17954   141251449+  83  Linux
/dev/sda7           17955       18704     6024343+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb623b623

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux


I don't understand the rest of the instructions.  I think the one with the star, 

/dev/sda6   *         370       17954   141251449+  83  Linux

is the Intrepid part.  Again, remember, I am running now under the LiveCD...

---

### Post by caljohnsmith on 2008-11-23
How about first doing the following from a terminal (Applications > Accessories > Terminal) to make sure the file systems of your linux partitions are OK:
```
sudo fsck -y /dev/sda6
sudo fsck -y /dev/sda1
```
Next please post the output of the following:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
That will make it clear which of your partitions control Grub in the MBR.

---

### Post by trooperchix on 2008-11-23
Here are the results, again, I'm running right now through the Intrepid LiveCD:

ubuntu@ubuntu:~$ sudo fsck -y /dev/sda6
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda6 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda6: recovering journal
/dev/sda6: clean, 179892/8830976 files, 26593519/35312862 blocks
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1 has gone 202 days without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 9026/188416 files (0.1% non-contiguous), 135719/740990 blocks
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff05

ubuntu@ubuntu:~$ 

Somehow I don't think this is what you wanted, that these results are skewed because I'm in the LiveCD environment.  Just a guess..

---

### Post by caljohnsmith on 2008-11-23
Did you notice the warning it gave you:
[QUOTE=trooperchix]```
/dev/sda6 is mounted.

WARNING!!! Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.
```[/QUOTE]
I didn't know you had sda6 mounted, and unfortunately you should never do an fsck on a mounted file system (that's what the warning is for). That might be a big problem now. How about first unmounting sda6:
```
sudo umount /dev/sda6
```
And if that doesn't work, close all your file browsers and other terminal tabs/windows, and try again. After you are *sure* sda6 is unmounted with the above command, try the fsck again:
```
sudo fsck -y /dev/sda6

```
And hopefully it will be able to undo any damage to your sda6 partition. Please post the results, and if it says it is successful, post the output of:
```
sudo mount /dev/sda6 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by trooperchix on 2008-11-23
> **caljohnsmith said:**
> Did you notice the warning it gave you:

I didn't know you had sda6 mounted, and unfortunately you should never do an fsck on a mounted file system (that's what the warning is for). That might be a big problem now. How about first unmounting sda6:
```
sudo umount /dev/sda6
```
And if that doesn't work, close all your file browsers and other terminal tabs/windows, and try again. After you are *sure* sda6 is unmounted with the above command, try the fsck again:
```
sudo fsck -y /dev/sda6

```
And hopefully it will be able to undo any damage to your sda6 partition.

The results are as follows:

```
 ubuntu@ubuntu:~$ sudo umount /dev/sda6
umount: /dev/sda6: not mounted
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda6
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda6: clean, 179892/8830976 files, 26593519/35312862 blocks
ubuntu@ubuntu:~$ 

```

---

### Post by trooperchix on 2008-11-23
```
 ubuntu@ubuntu:~$ sudo umount /dev/sda6
umount: /dev/sda6: not mounted
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda6
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda6: clean, 179892/8830976 files, 26593519/35312862 blocks
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
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
# kopt=root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04 (8.04) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 
savedefault
boot

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
# kopt=root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04 (8.04) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 
savedefault
boot

ubuntu@ubuntu:~$ 


```

---

### Post by caljohnsmith on 2008-11-23
OK, thankfully it looks like sda6 is OK. From those previous "dd" commands you ran, they show that your sda6 partition is controlling Grub in the MBR (Master Boot Record), so that means the menu.lst in sda6 is the one that gets loaded on start up. Do you know for sure whether sda6 is your Intrepid partition? How about doing the following while sda6 is still mounted on /mnt:
```
sudo chroot /mnt /bin/bash
lsb_release -a
exit
```
And the lsb_release command should tell you whether that partition is Intrepid or Hardy. 

I have to run now and won't be back until tomorrow morning sometime, so if your problem is still unresolved, we can pick up then if you want. Otherwise best of luck and hope you get it resolved. :)

---

### Post by trooperchix on 2008-11-23
Here's the output of that:

```
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# 
root@ubuntu:/# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
root@ubuntu:/# EXIT
bash: EXIT: command not found
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 

```

---

### Post by unutbu on 2008-11-23
I noticed from your fdisk output that you have 2 drives: a 160GB (sda) and a 80GB (sdb) drive. Do you have a Linux OS installed on the 80GB drive? Could it be that your BIOS is set to boot from this other drive?

As far as I can see, everything about your setup on sda is fine. When you boot up, do you see a GRUB menu with 4 entries:

Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, memtest86+
Ubuntu 8.04 (8.04) (on /dev/sda1)

Or do you see something else?

---

### Post by trooperchix on 2008-11-23
> **unutbu said:**
> I noticed from your fdisk output that you have 2 drives: a 160GB (sda) and a 80GB (sdb) drive. Do you have a Linux OS installed on the 80GB drive? Could it be that your BIOS is set to boot from this other drive? I have two large hd partitions?  If it is what I think it may be, is my old hardy partition that literally disappeared on me.  Hmm.  I need to look at that because if I could save the pictures off that partition...  >  

As far as I can see, everything about your setup on sda is fine. When you boot up, do you see a GRUB menu with 4 entries:

Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, memtest86+
Ubuntu 8.04 (8.04) (on /dev/sda1)

Or do you see something else?

I see exactly that.  None of the options work, though I will say I haven't tried the memtest86+ option.  I should have an option for intrepid, shouldn't I?

---

### Post by trooperchix on 2008-11-23
*bump*

---

### Post by unutbu on 2008-11-23
Indeed. The boot options in your menu.lst are for Hardy. The Intrepid kernels are version 2.6.25 or 2.6.27. Let's try to find out where they are.

Boot from the LiveCD.
```
sudo mount /dev/sda6 /mnt
ls -l /mnt/boot/
ls -l /mnt/boot/grub
```

Please post the output of the above commands.

Also, could you describe in more detail what happens when you select 

Ubuntu 8.04, kernel 2.6.24-16-generic

from the GRUB boot menu? Do you get a GRUB error message?

---

### Post by trooperchix on 2008-11-23
OH, I figured out where the 80Gb HD came from...  it was one I was going to use as a backup, but for one reason or another, can't get it to play well with others.  Another issue for another time.  I disconnected it and now the output states...

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2             370       19457   153324360    5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris
/dev/sda6   *         370       17954   141251449+  83  Linux
/dev/sda7           17955       18704     6024343+  82  Linux swap / Solaris

Partition table entries are not in disk order 

So nevermind about the 80, it doesn't have anything on it for now...

---

### Post by trooperchix on 2008-11-23
> **unutbu said:**
> Indeed. The boot options in your menu.lst are for Hardy. The Intrepid kernels are version 2.6.25 or 2.6.27. Let's try to find out where they are.

Boot from the LiveCD.
```
sudo mount /dev/sda6 /mnt
ls -l /mnt/boot/
ls -l /mnt/boot/grub
```

Please post the output of the above commands.

Also, could you describe in more detail what happens when you select 

Ubuntu 8.04, kernel 2.6.24-16-generic

from the GRUB boot menu? Do you get a GRUB error message?


Here are the results:

> ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
mount: /dev/sda6 already mounted or /mnt busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt
ubuntu@ubuntu:~$ ls -l /mnt/boot/
total 29812
-rw-r--r-- 1 root root  422838 2008-10-22 03:12 abi-2.6.24-21-generic
-rw-r--r-- 1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r-- 1 root root   80062 2008-10-22 03:12 config-2.6.24-21-generic
-rw-r--r-- 1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
drwxr-xr-x 3 root root    4096 2008-11-23 21:25 grub
-rw-r--r-- 1 root root 7492967 2008-11-07 14:23 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7492947 2008-10-30 15:44 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root 8107347 2008-11-12 01:58 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r-- 1 root root  905617 2008-10-22 03:12 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root 1920760 2008-10-22 03:12 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
ubuntu@ubuntu:~$ ls -l /mnt/boot/grub
total 216
-rw-r--r-- 1 root root    197 2008-05-06 02:23 default
-rw-r--r-- 1 root root     15 2008-05-06 02:23 device.map
-rw-r--r-- 1 root root   8056 2008-05-06 02:23 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-05-06 02:23 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-05-06 02:24 installed-version
-rw-r--r-- 1 root root   8608 2008-05-06 02:23 jfs_stage1_5
-rw-r--r-- 1 root root   4628 2008-11-23 21:26 menu.lst
-rw-r--r-- 1 root root   5004 2008-11-23 21:25 menu.lst~
-rw-r--r-- 1 root root   4628 2008-05-07 03:01 menu.lst.backup
-rw-r--r-- 1 root root   7324 2008-05-06 02:23 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-05-06 02:23 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-05-07 03:01 splashimages
-rw-r--r-- 1 root root    512 2008-05-06 02:23 stage1
-rw-r--r-- 1 root root 108356 2008-05-06 02:24 stage2
-rw-r--r-- 1 root root   9276 2008-05-06 02:23 xfs_stage1_5
ubuntu@ubuntu:~$ 



Let me reboot and write down the error.  B back in a tinker's fart...

---

### Post by unutbu on 2008-11-23
Please post the output of 
```

sudo mount /dev/sda6 /mnt
cat /mnt/boot/grub/menu.lst~
cat /mnt/boot/grub/menu.lst.backup
```

---

### Post by trooperchix on 2008-11-23
> **unutbu said:**
> Please post the output of 
```

sudo mount /dev/sda6 /mnt
cat /mnt/boot/grub/menu.lst~
cat /mnt/boot/grub/menu.lst.backup
```

Here you go:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst~
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
timeout		1

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
password topsecret

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
# kopt=root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro

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
# defoptions=quiet splash vga=792

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04 (8.04) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 
savedefault
boot

ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst.backup
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
# kopt=root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ead810d0-dc3f-41f2-b5bf-3188b9c7dee2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04 (8.04) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 
savedefault
boot

ubuntu@ubuntu:~$ 
```

---

### Post by unutbu on 2008-11-23
Okay, I think we got lucky. Try:

```
sudo cp /mnt/boot/grub/menu.lst~ /mnt/boot/grub/menu.lst
```

Then reboot. See if you can boot

Ubuntu 8.10, kernel 2.6.27-7-generic

---

### Post by trooperchix on 2008-11-24
> **unutbu said:**
> Also, could you describe in more detail what happens when you select 

Ubuntu 8.04, kernel 2.6.24-16-generic

from the GRUB boot menu? Do you get a GRUB error message?

I pick that option (Ubuntu 8.04, kernel 2.6.24-16-generic) and hit Enter:

```
 Error 15: file not found

Press any key to continue... 
```

When I hit a key, I go right back to that main menu from which I picked the above option from.

---

### Post by trooperchix on 2008-11-24
> **unutbu said:**
> Okay, I think we got lucky. Try:

```
sudo cp /mnt/boot/grub/menu.lst~ /mnt/boot/grub/menu.lst
```

Then reboot. See if you can boot

Ubuntu 8.10, kernel 2.6.27-7-generic

You are a God amongst Geeks!!  Love you man, this worked!!

---

