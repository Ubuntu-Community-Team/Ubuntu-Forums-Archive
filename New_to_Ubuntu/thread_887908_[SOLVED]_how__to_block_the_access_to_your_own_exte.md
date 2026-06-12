---
title: "[SOLVED] how  to block the access to your own external drive with Gparted"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by nyarlatotheph on 2008-08-12
Hi all, I am a newbie wanting to make a copy of his ubuntu system before messing it up beyond any recognition again. Browsing around I found many people recommending Gparted. I made a liveCD, I booted from CD, then copied on my external Maxtor 3200 as a proof of principle my ubuntu 1,5 G swap partition from my HD. Gparted notified everything was successfully copied. As a result, I have lost what I had on the Maxtor (well, I  made a copy before) but, even better, I cannot access my Maxtor again :confused:
It seems to me that the Maxtor is still there from the following lines:

```
marco@marco-laptop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3b85ee4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       12815    92697600    6  FAT16
/dev/sda3           12816       23897    89016165    5  Extended
/dev/sda4           23898       24322     3399680   12  Compaq diagnostics
/dev/sda5           12816       16462    29294496   83  Linux
/dev/sda6           16463       16705     1951866   82  Linux swap / Solaris
/dev/sda7           16706       23897    57769708+  83  Linux

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55b3757d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36483   293049666   82  Linux swap / Solaris

Disk /dev/sdc: 2034 MB, 2034236416 bytes
33 heads, 63 sectors/track, 1911 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1912     1986543    6  FAT16

```

and
```
marco@marco-laptop:~$ sudo blkid
/dev/sda1: UUID="040CF0B4E49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="3C94EF8494EF3F50" LABEL="ACER" TYPE="ntfs" 
/dev/sda4: UUID="F87056367055FC36" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="f576a6cc-423b-48ba-83e2-9bba0ef9448c" 
/dev/sda7: UUID="902f3ebf-2ebb-4a8d-914a-33348610f40a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="1a638688-eac1-413d-806f-b0323389db70" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: TYPE="swap" UUID="80b9060f-70f8-4338-ae96-c2763695c1d9" 
/dev/sdc1: SEC_TYPE="msdos" UUID="3CBF-9CB7" TYPE="vfat" 


```

where sdb1 is the Maxtor. Nevertheless I don't have access in Dual boot (neither linux nor Vista). 
Thanks for your help!

Acer/Hardy Heron/Core2Duo 2GHZ/NVIDIA8600/Maxtor3200

---

### Post by nicedude on 2008-08-12
For starters Gparted is a partition editor not a software backup program, I would recommend you google "remastersys" as it is a program that can backup your whole setup and make you an install CD or DVD with everything you have changed intact. It has 2 modes to make disks the first one strips your name and home folder stuff out , for when you are making a backup to hand out to people. The second mode lets you make a live booting disk with all your info intact so you can take your system with you. It is not in the repositories though so you will need to google it and then follow instructions to add it to your Ubuntu system sources so that it will then be available via Synaptic package manager like it was in the repositories. 

Second it looks to me like you formated your entire 300GB external drive as Linux SWAP file space, that could be why Vista doesn't like it :-) . You obviously have Linux installed so use Gparted to first delete this and then create a new NTFS or FAT32 partition on this drive ( some would say NTFS hands down but sometimes for simple storage of videos etc. I like Fat32 as it never causes any mount problems that require me editing Fstab file and NTFS does for me sometimes ). Also you can get "pysdm" from the repositories as it is a cool python script that will help you mount any disk you hook up without having to use the "mount" command which is CLI only no GUI.

Also this is one of the crazyier looking fdisk outputs I have seen, see my comments below and maybe tell me more if you know.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics  - 10GB roughly and should be the system recovery partition which in my opinion is a waste of space if you can handle your own recovery needs

/dev/sda2   *        1275       12815    92697600    6  FAT16 - 92GB of FAT16 ? I hope that is some weird fdisk bug as since this is almost certainly your Vista partition - But FAT16 thats like circa 1995, Vista should be using NTFS ( heck I don't think you even get a choice )

/dev/sda3           12816       23897    89016165    5  Extended - 89GB primary extended partition which houses the logical partitions sda5, sda6 & sda7 which are listed later on.
 
/dev/sda4           23898       24322     3399680   12  Compaq diagnostics - Only 3GB but here is more disk space compaq wasted so they wouldn't have to give you a recovery CD - man I don't like these types of partitions as it steals your disk space when a simple recovery CD would suffice.

The rest of these are just logical partitions contained in the primary extended partition above and look OK it looks like you have 2 versions of linux installed in these as well as a 2GB swap file space.

/dev/sda5           12816       16462    29294496   83  Linux
/dev/sda6           16463       16705     1951866   82  Linux swap / Solaris
/dev/sda7           16706       23897    57769708+  83  Linux



hope this helps you out

---

### Post by louieb on 2008-08-12
Looks like the Maxtor now has 1 300GB swap partition. Was that the last of the 3 partitions copied?
 Vista can't read it. And to Linux its a swap partition for it to use.  

When you use GParted to copy - it copies one partition to another. 
To use it again You will need to use GParted and format the partition with a file system. Either ext3 or NTFS. 

IF you want to use GParted to copy your Linux installation. You should make a partition on the external the same size and copy  your hard drives Linux partition to the partition on the external.

---

### Post by nyarlatotheph on 2008-08-12
Thanks nicedude, 

> **nicedude said:**
> ...I would recommend you google "remastersys" as it is a program that can backup your whole setup and make you an install CD or DVD with everything you have changed intact.

It sounds good, I'll check it out



> **nicedude said:**
> Second it looks to me like you formated your entire 300GB external drive as Linux SWAP file space, that could be why Vista doesn't like it :-)

Neither do I. #-o I thought the transfer of partition was 1,5 G to 1,5 G and  not 1:1 indipendently from the physical size...

> **nicedude said:**
>  You obviously have Linux installed so use Gparted to first delete this and then create a new NTFS or FAT32 partition on this drive ( some would say NTFS hands down but sometimes for simple storage of videos etc.  

I'll do that


> **nicedude said:**
> Also this is one of the crazyier looking fdisk outputs I have seen, see my comments below and maybe tell me more if you know.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics  - 10GB roughly and should be the system recovery partition which in my opinion is a waste of space if you can handle your own recovery needs 

Right, it should be the recovery partition stuff

> **nicedude said:**
> /dev/sda2   *        1275       12815    92697600    6  FAT16 - 92GB of FAT16 ? I hope that is some weird fdisk bug as since this is almost certainly your Vista partition - But FAT16 thats like circa 1995, Vista should be using NTFS ( heck I don't think you even get a choice )

That means I have to reformat the Maxtor as NTFS if I want to use it with Vista then...


> **nicedude said:**
> /dev/sda4           23898       24322     3399680   12  Compaq diagnostics - Only 3GB but here is more disk space compaq wasted so they wouldn't have to give you a recovery CD - man I don't like these types of partitions as it steals your disk space when a simple recovery CD would suffice 

totally agree

> **nicedude said:**
> The rest of these are just logical partitions contained in the primary extended partition above and look OK it looks like you have 2 versions of linux installed in these as well as a 2GB swap file space.

/dev/sda5           12816       16462    29294496   83  Linux
/dev/sda6           16463       16705     1951866   82  Linux swap / Solaris
/dev/sda7           16706       23897    57769708+  83  Linux


I actually did not know that. That means I could delete one? Because I am just using Hardy. Man, what a mess I did...

Thanks heaps mate!

---

### Post by nyarlatotheph on 2008-08-12
Thanks louieb!

> **louieb said:**
> Looks like the Maxtor now has 1 300GB swap partition. Was that the last of the 3 partitions copied?

correct

> **louieb said:**
> When you use GParted to copy - it copies one partition to another. 
To use it again You will need to use GParted and format the partition with a file system. Either ext3 or NTFS. 

IF you want to use GParted to copy your Linux installation. You should make a partition on the external the same size and copy  your hard drives Linux partition to the partition on the external.

It's not that I want to use GParted, I just would like to have a backup of my system without causing major damages. If you have a better suggestion to make an image of your linux partitions & to restore them when things go dramatically wrong, you are mostly welcome to tell it to me  :)
I know that a fresh reinstall could maybe be faster, but I am known to make things more complicated than they are.

---

### Post by nicedude on 2008-08-12
Quote:
Originally Posted by nicedude View Post
/dev/sda2 * 1275 12815 92697600 6 FAT16 - 92GB of FAT16 ? I hope that is some weird fdisk bug as since this is almost certainly your Vista partition - But FAT16 thats like circa 1995, Vista should be using NTFS ( heck I don't think you even get a choice )
That means I have to reformat the Maxtor as NTFS if I want to use it with Vista then...

Nope Vista will recognize either NTFS or FAT32 partitions for hard disks by default and with no further setup. It just forces you to use NTFS when you are installing it, as to what type of partition Vista itself will reside on.

FAT32
NTFS  These are standard Microsoft type partitions

SWAP
EXT2
EXT3  These are common Linux type partitions

So if you want to use the portable hard drive in Vista & Ubuntu then you have the choice of formatting it as NTFS or as FAT32 either should work just fine. FAT32 does have some limits on filesize but I think the limit is 4GB for a single file so keep that in mind if you work with huge files or keep DVD full backups on it.

Quote:
Originally Posted by nicedude View Post
The rest of these are just logical partitions contained in the primary extended partition above and look OK it looks like you have 2 versions of linux installed in these as well as a 2GB swap file space.

/dev/sda5 12816 16462 29294496 83 Linux
/dev/sda6 16463 16705 1951866 82 Linux swap / Solaris
/dev/sda7 16706 23897 57769708+ 83 Linux
I actually did not know that. That means I could delete one? Because I am just using Hardy. Man, what a mess I did...

Probably but I can't say which one by all that, when your PC boots up to the GRUB bootlist menu how many linux's are listed ? You could copy your grub bootlist menu file and either post it here or PM me a copy and I would look it over real quick and try to tell you more info, especially if you can say which one of the grub boot list menu items you are currently selecting at boot up to use your Ubuntu ? As then I could see which one you are not using and maybe tell you what partition it is on.

Because I am just using Hardy. Man, what a mess I did...

So what, your learning as am I. When you figure it all out you will have learned some stuff and knowledge is power :-)

Here's a command to copy your GRUB boolist menu file to your desktop so you can look at it without risking messing it up.

cp /boot/grub/menu.lst ~/Desktop/GrubMenuList.txt

---

### Post by louieb on 2008-08-12
> **nyarlatotheph said:**
> 
It's not that I want to use GParted, I just would like to have a backup of my system without causing major damages...
I use partimage. on the SystemRescueCD  [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522") 

Also you can get a [GParted-Clonezilla -- LiveCD]("http://gpartedclonz.tuxfamily.org/index.php")  it runs partimage too. But with an easier to use interface.

---

### Post by nyarlatotheph on 2008-08-13
Hi again,

> **nicedude said:**
> 
Here's a command to copy your GRUB boolist menu file to your desktop so you can look at it without risking messing it up.

cp /boot/grub/menu.lst ~/Desktop/GrubMenuList.txt

here you go:
```
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
# kopt=root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro quiet splash
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro single

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Windows Vista/Longhorn (loader)
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
#title		Microsoft Windows XP Embedded
#root		(hd0,3)
#savedefault
#makeactive
#chainloader	+1


```
I choose the first option
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic

Recovery versions don't load, I have tried.

Curiosity: what is the difference between the files menu.lst~ and menu.lst ?
Thanks nicedude!

---

### Post by nicedude on 2008-08-13
Here you go with a quick answer, all these 4 linux selections are using hd0,4  ( which means in grubspeak hd is hard disk -> 0 means first disk -> 4 means fifth partition - since in grub 0=1 1=2 2=3 etc unlike fdisk sda? numbers where 1=1 2=2 3=3 ) this is the partition that these kernels are loaded from. That translates to sda5 ( or sd for sata disk -> a  for first hard disk -> 5 for fifth partition ). All the Linux kernel choices on your grub boot menu are the same linux on sda5 so it looks to me like sda7 could go bye bye as its not being used by grub and therefore not being used by you.


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)      <--- sda5
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro quiet splash
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)       <--- sda5
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro single

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,4)        <--- sda5
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)     <--- sda5
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

---

### Post by louieb on 2008-08-13
> Recovery versions don't load, I have tried.```

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro quiet splash
[COLOR=Red]initrd        /boot/initrd.img-2.6.22-19-generic[/COLOR]
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro single
[COLOR=Red]initrd        /boot/initrd.img-2.6.22-19-generic[/COLOR]


```I'd be surprised if either of the 1st 2 options work. Did not see an **initrd **statment. 
Might want to look in /boot and see if [COLOR=Red]initrd.img-2.6.22-19-generic [COLOR=Black]is there. If it is then add that statment to your grub entries. [/COLOR]
[/COLOR]

---

### Post by robert shearer on 2008-08-13
Re;
"For starters Gparted is a partition editor not a software backup program, I would recommend you google "remastersys" as it is a program that can backup your whole setup and make you an install CD or DVD with everything you have changed intact."

from here  [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by Miljet on 2008-08-13
Before you go deleting sda7, you might want to make sure that you didn't install your home directory there. If you followed many examples, you could have installed the /home directory in a separate partition and that looks like what may have happened.

---

### Post by nyarlatotheph on 2008-08-14
> **Miljet said:**
> Before you go deleting sda7, you might want to make sure that you didn't install your home directory there. If you followed many examples, you could have installed the /home directory in a separate partition and that looks like what may have happened.
Thanks Miljet, I will have a good look before thrashing it  :)

---

### Post by nyarlatotheph on 2008-08-14
> **louieb said:**
> ```

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro quiet splash
[COLOR=Red]initrd        /boot/initrd.img-2.6.22-19-generic[/COLOR]
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=1a638688-eac1-413d-806f-b0323389db70 ro single
[COLOR=Red]initrd        /boot/initrd.img-2.6.22-19-generic[/COLOR]


```I'd be surprised if either of the 1st 2 options work. Did not see an **initrd **statment. 
Might want to look in /boot and see if [COLOR=Red]initrd.img-2.6.22-19-generic [COLOR=Black]is there. If it is then add that statment to your grub entries. [/COLOR]
[/COLOR]
I'll check in the /boot. I always choose the first option in the kernel list, thought it was the 2.6.24-19-generic. I'll check it again.

---

### Post by nyarlatotheph on 2008-08-15
Louieb, 
initrd.img-2.6.22-19-generic is in /boot, only not in the grub entries. I don't know how to put it in the entries, but I am happy that I can boot :) Nicedude, I reformat the disk with ntfs and now I can access it again. Thanks!

---

