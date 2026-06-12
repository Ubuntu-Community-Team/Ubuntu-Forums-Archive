---
title: "I think I hosed my partitions/Can't dual boot"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by LPShred on 2008-08-31
[IMG]http://www.personal.psu.edu/ssk5033/Pics/Screenshot--dev-sda - GParted.png[/IMG]

When I go to the grub boot menu, I wasn't able to to boot my Vista partition and I think I found out why.  It appears that my /home partition somehow got put inside the extended partition with my Vista install.

Is there any way to fix it so that my /home partition is outside the extended partition and so that Vista shows up in grub?

---

### Post by BDNiner on 2008-08-31
No, it seems like you have formatted and overwritten you vista partion. you will have to reinstall vista for scratch.

---

### Post by Rocket2DMn on 2008-08-31
You can't move a partition from inside a logical/extended one to outside (thus making it a physical partition).  What we can do, however, is make sure GRUB is setup correctly to load Vista.
Can you please post the output of these commands?
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
cat /boot/grub/menu.lst
```
Hopefully you haven't overwritten Vista already.

---

### Post by jemate18 on 2008-08-31
To verify if your Vista has been reformatted/erased

Boot your Ubuntu and then navigate to the files inside your /media/vista,

if there are still files, then it still exists, next thing to do is fix your GRUB as suggested in the previous post.

If there are no more files in it,, you have to reinstall vista.

________________________________
Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by LPShred on 2008-08-31
The output of the commands was:

```
steve@steve-laptop:~$ sudo fdisk -l
[sudo] password for steve: 

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         365     2931831   82  Linux swap / Solaris
/dev/sda2   *         366        1581     9767520   83  Linux
/dev/sda4            1582       13803    98173215    f  W95 Ext'd (LBA)
/dev/sda5            8067       13803    46082421    7  HPFS/NTFS
/dev/sda6            1582        8066    52090699+  83  Linux

Partition table entries are not in disk order
steve@steve-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=99cf3e9a-fbcc-4262-aaab-20ad9a148550 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=072e7d7b-f2c6-4220-a24d-1983b713ca32 /home           ext3    relatime        0       2
# /dev/sda1
UUID=df9b3a90-523f-4951-8b33-fd71e1d60e0d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
steve@steve-laptop:~$ sudo blkid
/dev/sda1: TYPE="swap" UUID="df9b3a90-523f-4951-8b33-fd71e1d60e0d" 
/dev/sda2: UUID="99cf3e9a-fbcc-4262-aaab-20ad9a148550" TYPE="ext3" 
/dev/sda5: UUID="130033C96B7E7CC9" LABEL="VISTA" TYPE="ntfs" 
/dev/sda6: UUID="072e7d7b-f2c6-4220-a24d-1983b713ca32" TYPE="ext3" 
steve@steve-laptop:~$ cat /boot/grub/menu.lst
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=99cf3e9a-fbcc-4262-aaab-20ad9a148550 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=99cf3e9a-fbcc-4262-aaab-20ad9a148550 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=99cf3e9a-fbcc-4262-aaab-20ad9a148550 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
steve@steve-laptop:~$ 

```

The vista files are still there, I think I just need to configure grub.

---

### Post by Rocket2DMn on 2008-08-31
Yeah there is no entry for Vista.  Assuming that Vista is still there (see post #4), we can try and add the correct entry for it.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
Then add the following to the end of the file
```
# divider
title Other operating systems:
root

# Vista entry
title Microsoft Windows Vista
root (hd0,4)
savedefault
makeactive
chainloader +1
```
The (hd0,4) is based on hard drive at slot 0, partition 4 (count starting at 0 - so sda5).
Save and close, then reboot and see if it will let you choose.

---

### Post by jemate18 on 2008-08-31
> **LPShred said:**
> The output of the commands was:

```
steve@steve-laptop:~$ sudo fdisk -l
[sudo] password for steve: 

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         365     2931831   82  Linux swap / Solaris
/dev/sda2   *         366        1581     9767520   83  Linux
/dev/sda4            1582       13803    98173215    f  W95 Ext'd (LBA)
/dev/sda5            8067       13803    46082421    7  HPFS/NTFS
/dev/sda6            1582        8066    52090699+  83  Linux

Partition table entries are not in disk order
steve@steve-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=99cf3e9a-fbcc-4262-aaab-20ad9a148550 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=072e7d7b-f2c6-4220-a24d-1983b713ca32 /home           ext3    relatime        0       2
# /dev/sda1
UUID=df9b3a90-523f-4951-8b33-fd71e1d60e0d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
steve@steve-laptop:~$ sudo blkid
/dev/sda1: TYPE="swap" UUID="df9b3a90-523f-4951-8b33-fd71e1d60e0d" 
/dev/sda2: UUID="99cf3e9a-fbcc-4262-aaab-20ad9a148550" TYPE="ext3" 
/dev/sda5: UUID="130033C96B7E7CC9" LABEL="VISTA" TYPE="ntfs" 
/dev/sda6: UUID="072e7d7b-f2c6-4220-a24d-1983b713ca32" TYPE="ext3" 
steve@steve-laptop:~$ cat /boot/grub/menu.lst
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=99cf3e9a-fbcc-4262-aaab-20ad9a148550 ro

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

[COLOR="Red"]title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=99cf3e9a-fbcc-4262-aaab-20ad9a148550 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=99cf3e9a-fbcc-4262-aaab-20ad9a148550 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
[/COLOR]

[COLOR="Green"]#Put you ENTRY Here for VISTA[/COLOR]


### END DEBIAN AUTOMAGIC KERNELS LIST
steve@steve-laptop:~$ 

```

The vista files are still there, I think I just need to configure grub.

Your windows VISTA wasn't included in your GRUB thats why you cant boot to it when you have GRUB.

You have to edit your GRUB and include an ENTRY for your VISTA

____________________
Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are
able to do what you intend to do and DONT FORGET to THANK the people
who HELPED YOU by clicking the "thanks" button on the lower right
"medal icon" for their help and useful post

jemate18

---

### Post by jemate18 on 2008-08-31
Check this for instructions

> [http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)

---

### Post by LPShred on 2008-08-31
I added that code.  The entry showed up in the boot loader, but I got a Error 12: invalid command
...Press any key to continue

or something like that

This will fix it as soon as we figure out the code for that partition.

---

### Post by jemate18 on 2008-08-31
> **LPShred said:**
> I added that code.  The entry showed up in the boot loader, but I got a Error 12: invalid command
...Press any key to continue

or something like that

This will fix it as soon as we figure out the code for that partition.

Make sure to change the...

title         "Windows Vista"
[COLOR="Green"]root         (hd0,0)[/COLOR]
chainloader      +1

to the proper value corresponding to your partition.

___________________________________-
Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are
able to do what you intend to do and DONT FORGET to THANK the people
who HELPED YOU by clicking the "thanks" button on the lower right
"medal icon" for their help and useful post

jemate18

---

### Post by Rocket2DMn on 2008-08-31
It's a little weird b/c you have Vista inside an extended partition, so I'm not quite sure how to handle that...

---

### Post by solaceinsilence9 on 2008-08-31
> **Rocket2DMn said:**
> It's a little weird b/c you have Vista inside an extended partition, so I'm not quite sure how to handle that...

Im pretty sure that your Windows Partition needs to be FIRST, before your Ubuntu Partition. This is how I have my HD set up:

/dev/sda1 Dell Utility Partition (FAT32)
/dev/sda2 Vista Parition (NFTS)
/dev/sda3 Extended
   &nbsp;/dev/sda5 Ubuntu!!! (ext3)
    /dev/sda6 Linux Swap
    /dev/sda7 Other Stuff (ext3)

---

### Post by solaceinsilence9 on 2008-08-31
> **Rocket2DMn said:**
> It's a little weird b/c you have Vista inside an extended partition, so I'm not quite sure how to handle that...

Im pretty sure that your Windows Partition needs to be FIRST, before your Ubuntu Partition. This is how I have my HD set up:

/dev/sda1 Dell Utility Partition (FAT32)
/dev/sda2 Vista Parition (NFTS)
/dev/sda3 Extended

    [INDENT][/INDENT]/dev/sda5 Ubuntu!!! (ext3)

    [INDENT][/INDENT]/dev/sda6 Linux Swap

    [INDENT][/INDENT]/dev/sda7 Other Stuff (ext3)

---

### Post by LPShred on 2008-08-31
And how do I fix that?

How do I get grub to boot a partition inside of a extended partition?

---

### Post by Rocket2DMn on 2008-08-31
solaceinsilence9, I deleted your duplicate post.  For future reference, you can edit previous posts by clicking the Edit button near the bottom right.

You *should* be able to use partitions inside an extended partition normally, but I'm not entirely sure.  Maybe you should try re-instaling grub using the Super Grub Disk to see if that can detect the correct settings for you - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by LPShred on 2008-08-31
I tried SGD and selected the windows partition to boot, but it didn't work.  It used the rootnoverify(hd0,4) command, but it never booted.

I'm going to play around a little more.

Will switching back to the Windows boot loader fix the problem?

---

### Post by Rocket2DMn on 2008-08-31
With the windows bootloader, you won't be able to access Ubuntu.  How did you do this setup anyway?  I've never dealt with a Vista dual boot setup with windows in an extended partition where Ubuntu is higher up in partition order.  Typically you are supposed to install windows first, then Ubuntu.
If you're setup is still relatively young, you may consider just redoing your whole setup - wipe it all, install Vista, then install Ubuntu again.
It may be a bit overkill, but it will definitely get the job done!

---

### Post by LPShred on 2008-08-31
Well, I started out with XP about 2 years ago.  I then installed Vista on another partition and had a XP-Vista dual boot.  Recently I, reformatted the XP partition in order to install Ubuntu.  I asked if this was going to be a problem before I did it, and no one said there would be one.

So would it work if  I reinstalled the Windows bootloader and then reinstalled grub?

---

### Post by Rocket2DMn on 2008-08-31
Ah, I see, that is a good explanation.  Unfortunately, reinstalling bootloaders isn't going to solve your problem.
It seems that your best bet would be to just start your dual boot over from scratch if that is feasible for you.  That would most likely require an external HD to do your backups on beforehand.  Otherwise, you are going to need more advanced Grub help than I can offer.

---

### Post by LPShred on 2008-08-31
I figured that it would come to that.  I wasn't really looking forward to reinstalling everything on Vista, but I guess that's the only way.

As for more advanced GRUB help, where should I go?

Is there any way to go back to Vista for the time being, until I backup and whatnot?

Thanks for working with me.

---

### Post by kansasnoob on 2008-08-31
> **Rocket2DMn said:**
> Yeah there is no entry for Vista.  Assuming that Vista is still there (see post #4), we can try and add the correct entry for it.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
Then add the following to the end of the file
```
# divider
title Other operating systems:
root

# Vista entry
title Microsoft Windows Vista
root (hd0,4)
savedefault
makeactive
chainloader +1
```
The (hd0,4) is based on hard drive at slot 0, partition 4 (count starting at 0 - so sda5).
Save and close, then reboot and see if it will let you choose.

This looks exactly right!

Did you try this? Just to recap:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

creates a backup of your menu list.

```
gksudo gedit /boot/grub/menu.lst
```

Opens an editable text file of your menu list. At the very end of the menu list you add the lines:

> # divider
title Other operating systems:
root

# Vista entry
title Microsoft Windows Vista
root (hd0,4)
savedefault
makeactive
chainloader +1

Then be sure you click on SAVE, then click on FILE > QUIT.

Note: Just use copy-n-paste, it looks to me like Rocket2DMan has it right.

---

### Post by Rocket2DMn on 2008-08-31
If you need to get back into Vista, you can try reinstalling their bootloader - [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
You won't be able to access Ubuntu again until you reinstall grub (you can use SGD for this since you have it already).
You can make your backups from within Ubuntu since you should have the Vista partition mounted, but do whatever works best for you.  Don't hurry to do the reinstallation of everything until you are sure you have everything backed up and you have time to handle it all.

---

### Post by rplantz on 2008-08-31
First, a caveat. I'm a Windows newbie, so I may not have done things the best way.

I recently bought an Acer laptop with Vista installed. Instead of supplying an install disk, there is a hidden partition from which I can redo the Vista install. Unfortunately, when I installed Ubuntu, it wrote over the Vista boot loader. I then screwed up my partitioning and could not get back into Vista. One of the problems with not having an install disk is that apparently there is no way to redo Vista from the hidden disk partition without having a working Vista boot loader.

With a little searching, I found a utility that repaired my Vista boot loader. So I managed to get Vista working again.

Then I followed this howto, [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu). It uses EasyBCD to tell the Vista boot loader about Ubuntu. It all works very nicely for me.

Off the topic a bit here, I've used lots of operating systems in my 40 years of programming. I've written specialized device drivers, designed gui's, etc. As I said above, I'm a newbie at Windows. After using it for a few months now, I'm totally baffled that anyone would ever choose to use such an OS, let alone buy it. Then again, the people I vote for seldom win the election.

---

### Post by Rocket2DMn on 2008-08-31
Come to think of it, the SGD may actually be able to install the Vista bootloader for you.  I used the disc a few months ago, and I think it may just have the option - certainly worth checking out if you don't have a Vista cd (though you said you installed it yourself).

---

### Post by solaceinsilence9 on 2008-09-01
> **Rocket2DMn said:**
> solaceinsilence9, I deleted your duplicate post.  For future reference, you can edit previous posts by clicking the Edit button near the bottom right.

You *should* be able to use partitions inside an extended partition normally, but I'm not entirely sure.  Maybe you should try re-instaling grub using the Super Grub Disk to see if that can detect the correct settings for you - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Yaaa I apologize for that, I did edit my post but I must have browsed back in my history.

---

### Post by solaceinsilence9 on 2008-09-01
> **rplantz said:**
> First, a caveat. I'm a Windows newbie, so I may not have done things the best way.

I recently bought an Acer laptop with Vista installed. Instead of supplying an install disk, there is a hidden partition from which I can redo the Vista install. Unfortunately, when I installed Ubuntu, it wrote over the Vista boot loader. I then screwed up my partitioning and could not get back into Vista. One of the problems with not having an install disk is that apparently there is no way to redo Vista from the hidden disk partition without having a working Vista boot loader.

With a little searching, I found a utility that repaired my Vista boot loader. So I managed to get Vista working again.

Then I followed this howto, [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu). It uses EasyBCD to tell the Vista boot loader about Ubuntu. It all works very nicely for me.

Off the topic a bit here, I've used lots of operating systems in my 40 years of programming. I've written specialized device drivers, designed gui's, etc. As I said above, I'm a newbie at Windows. After using it for a few months now, I'm totally baffled that anyone would ever choose to use such an OS, let alone buy it. Then again, the people I vote for seldom win the election.

The thing is, Windows is marketed for its ease of use and they have the money to pay for heavy advertising, so that is why its popular. For the computer illiterate, or the casual interested computer user Windows works well. I lost faith in Windows after 98SE... Vista is HORRIBLE...

---

### Post by caljohnsmith on 2008-09-01
LPShred, I don't think you have to give up on your Vista partition just yet. I know for sure that Windows XP can be booted from a logical partition, so I'm almost certain you can get your Vista booting from a logical partition too. First, try the following in your menu.lst, and let me know what errors you get (if any) on start up when you try it:
```
title Windows Vista
root (hd0,4)
chainloader +1
```
It may not look much different than what you might have all ready tried, but the critical point in the above entry is that it omits the Grub "makeactive" function, because Grub can not make a logical partition active (i.e. set its boot flag on). That's the first important step in getting Windows to boot from a logical partition.

---

