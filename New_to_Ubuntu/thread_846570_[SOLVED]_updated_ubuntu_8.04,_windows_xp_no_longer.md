---
title: "[SOLVED] updated ubuntu 8.04, windows xp no longer in grub"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Anticitizen2 on 2008-07-01
Ok, I'm running a dual boot of windows xp and ubuntu 8.04.  Today I booted into ubuntu to check for any updates...there were many.  So I downloaded and installed them and restarted.  Upon reaching the grub menu I noticed that my windows xp installation was no longer there.  I loaded ubuntu and checked menu.lst, which was missing the windows entry, but had 2 entries for ubuntu and recovery mode.  I checked in the file system and the windows partition was still showing up.  

Any ideas on how to fix this?

---

### Post by Anticitizen2 on 2008-07-01
sorry, bumping to unbury

---

### Post by jingo811 on 2008-07-01
Post your results for the **"sudo fdisk -l"** command in terminal and make sure to wrap it in these html tags **[ code]** for easier reading:
```

linux@linux:~$ **sudo fdisk -l**


Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         765     6144831    b  W95 FAT32
/dev/hda2             766        4008    26049397+   f  W95 Ext'd (LBA)
/dev/hda5   *        2551        3279     5855661   83  Linux
/dev/hda6             766        2550    14337949+  83  Linux
/dev/hda7            3280        4008     5855661   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         131     1052226    b  W95 FAT32
/dev/hdb2             132         261     1044225   82  Linux swap / Solaris
/dev/hdb3             262        4998    38049952+  83  Linux
linux@linux:~$ 


```

---

### Post by Anticitizen2 on 2008-07-01
as requested:
[ code]
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb276b276

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       27320    14651280   83  Linux
/dev/sda3           27321       27928     4883760    b  W95 FAT32
/dev/sda4           27929       28052      996030    5  Extended
/dev/sda5           27929       28052      995998+  82  Linux swap / Solaris
[ code]

---

### Post by jingo811 on 2008-07-01
In the forum text gui toolbar there's a # character you can use to wrap stuff in proper html [/code] tags just so you know.  But that's not really important right now :)
[php]
```
/dev/sda1 * 1 25496 204796588+ 7 HPFS/NTFS
```
[/php]


Anyhow approximately how much GB does this partition have what's it used for?
```
/dev/sda1 * 1 25496 204796588+ 7 HPFS/NTFS
```

Approximately how much GB does this partition have what's it used for?
```
/dev/sda3 27321 27928 4883760 b W95 FAT32
```

Do you have 2 different Windows operating systems on your PC?

---

### Post by WRDN on 2008-07-01
Add to the bottom of your menu.lst file:

```
title Other Operating Systems
root

#Windows Entry (# denotes a comment, ignored by PC)
title Windows
root (hd0,0)
makeactive
chainloader + 1

```

To edit the file, you will need root priviledges to you need to use the command:

```
sudo gedit /boot/grub/menu.lst
```

Reboot and the entry for Windows should appear and work

---

### Post by jingo811 on 2008-07-01
> **WRDN said:**
> 
....
....

To edit the file, you will need root priviledges to you need to use the command:

```
sudo gedit /boot/grub/menu.lst
```

Reboot and the entry for Windows should appear and work

[COLOR="Red"]Before you do the above command backup your menu.lst file first in case you screw up![/COLOR]

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup_01_Original
```
Then do the mentioned command:
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Anticitizen2 on 2008-07-01
```
 /dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS 
```
this partition is my windows partition.  if has ~100gb of free space

```
 /dev/sda3           27321       27928     4883760    b  W95 FAT32

```
this is a partition I made for transferring files from windows to ubuntu before I learned that ubuntu could read ntfs.

thanks for the help

---

### Post by stchman on 2008-07-01
> **Anticitizen2 said:**
> Ok, I'm running a dual boot of windows xp and ubuntu 8.04.  Today I booted into ubuntu to check for any updates...there were many.  So I downloaded and installed them and restarted.  Upon reaching the grub menu I noticed that my windows xp installation was no longer there.  I loaded ubuntu and checked menu.lst, which was missing the windows entry, but had 2 entries for ubuntu and recovery mode.  I checked in the file system and the windows partition was still showing up.  

Any ideas on how to fix this?

I cannot say for sure but what you probably did was to manually edit the menu.lst and place XP first in the list.  When Ubuntu updates the kernel it replace the menu.lst with a new one wiping out what you did.

I do not recommend manually editing the menu.lst file.  Install StartUpManager to configure GRUB.

```
sudo apt-get install startupmanager
```

This will allow you to select the default OS to boot and give you other GRUB configurations in a nice GUI.

---

### Post by Anticitizen2 on 2008-07-01
thank you all for the replies.  I tried both suggestions, editing the menu.lst file and using the start up manager.  windows xp does not show up in the manager and after editing the menu.lst file the changes do not seem to stay (double-checked after editing to make sure that I saved).  Any other ideas or insights?

---

### Post by jingo811 on 2008-07-01
Let me see if I understood you right.
**1.** You edited menu.lst
**2.** Rebooted (no Windows entry)
**3.** Then you checked your menu.lst file to find that your added Windows specs is no longer there?

This time I think you should post your entire menu.lst file in the forums like this!
Oh this is my menu.lst so don't use it for your PC it won't work.  Also wrap your menu.lst in the [/php] html tags this time so we get some nice colorations, you'll find it in the forum toolbar next to the # < > icons :)
You don't have to include the md5-password part for the public eyes if you don't want to the rest we can see!!

[php]
# Which entry should boot by default?
default		0

# Countdown (seconds)
timeout		10

# Menu colors
color dark-gray/black white/red

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#######################################################################################



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
# kopt=root=/dev/hda8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-17-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-17-generic root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-17-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-17-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-17-generic root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.20-17-generic

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


#####################		{ Entry 0 }		###############################
#
# Partition:	/dev/hda5
title		Ubuntu Feisty
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0042284c-4547-41ef-9314-99824cfcf67c ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot

#####################		{ Entry 1 }		###############################
#
# Partition:	/dev/hda5
title		recovery mode
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0042284c-4547-41ef-9314-99824cfcf67c ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot

#####################		{ Entry 2 }		###############################
#
# Partition:	/dev/hda5
#title		memtest86+
#root		(hd0,4)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot





#######################################################################################
title		.....................................................................
root
#######################################################################################



#####################		{ Entry 3 }		###############################
#
# Partition:	/dev/hda6
title		Debian Etch
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.18-5-486 root=/dev/hda7 ro vga=791
initrd		/boot/initrd.img-2.6.18-5-486
savedefault
boot

#####################		{ Entry 4 }		###############################
#
# Partition:	/dev/hda6
title		single-user mode
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.18-5-486 root=/dev/hda7 ro single 
initrd		/boot/initrd.img-2.6.18-5-486
savedefault
boot

#####################		{ Entry 5 }		###############################
#
# Partition:	/dev/hda1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

#####################		{ Entry 5 }		###############################
#
# Partition:	/dev/hda8
title		openSUSE 10.3
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22.17-0.1-default root=/dev/disk/by-id/scsi-SATA_Maxtor_6E040L0_E118SYPN-part8 vga=0x31a resume=/dev/sdb2 splash=silent showopts
#kernel		/boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_Maxtor_6E040L0_E118SYPN-part8 vga=0x31a    resume=/dev/sdb2 splash=silent showopts
initrd		/boot/initrd-2.6.22.17-0.1-default
#initrd		/boot/initrd-2.6.22.5-31-default

[/php]

---

### Post by Anticitizen2 on 2008-07-01
> **jingo811 said:**
> Let me see if I understood you right.
**1.** You edited menu.lst
**2.** Rebooted (no Windows entry)
**3.** Then you checked your menu.lst file to find that your added Windows specs is no longer there?

yes, that is exactly what is happening.  I double checked to make sure I saved after making the changes.

---

### Post by jingo811 on 2008-07-01
Then I would do this.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup_02
```
```
gksudo gedit /boot/grub/menu.lst
```

[LIST]
[*]View > Highlight Mode > Scripts > **sh**
[/LIST]

[LIST]
[*]And add this to the very end of your menu.lst file nothing much is different from what someone else mentioned before except the savedefault line.  
Don't know what it does but my Windows specs has always looked like this by default in GRUB.
[*]Also comment out any old mention of any Windows entry you have maybe there's several Windows specs causing conflicts for GRUB.
[/LIST]

[PHP]#####################        { Entry 5 }        ###############################
#
# Partition:    /dev/hda1
title        Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1[/PHP]

---

