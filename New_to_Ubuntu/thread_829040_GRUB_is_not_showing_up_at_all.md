---
title: "GRUB is not showing up at all"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by radiocognition on 2008-06-14
Hey everyone:

I have what appears to be a simple problem, but searching on the forums, I haven't found a solution.  I just recently wiped my hardisk and just installed a copy of Windows XP.  I found this cool program that allows me to read and write to ext3 drives from Windows, so I had planend to partition the drive like this:

------------------------------------------------------------------------------------------------------------------
| Windows |   \home (mounted in both Windows and Linux)  |  Ubuntu  |Swap| 
------------------------------------------------------------------------------------------------------------------

I was able to set everything up the way that I wanted to when I installed Ubuntu.  I had a custom partition table set up in the installer, and all the files copied successfully.  Apparently, GRUB was not properly setup; when I rebooted the computer, the windows bootloader took over.

My first approch was to follow the advice on this [thread]("http://ubuntuforums.org/showthread.php?t=224351"). From the GRUB terminal, I was getting the right output, but whenever I rebooted without the live cd, I was once again dumped into windows.

Next I noticed that the partition with windows was marked with the "boot" flag.  I changed the boot flag so that it matched up with my own root directory and rebooted.  The system couldnt find either operating system.

I think I am getting close, but am missing something really simple that any user should know.  If any of you know anything about how to fix this, drop me a message.

Thanks

---

### Post by dacorr on 2008-06-14
what does the /boot/grub/menu.lst look like?

and does it even start to load grub or just straight to windows splash screen?

Dac

---

### Post by ChameleonDave on 2008-06-14
Did you definitely type "setup (hd0)"?  Did you accidentally add a partition number too?

---

### Post by radiocognition on 2008-06-14
The grub/menu.lst configuration file appears to be normal . . . it includes entries for Ubuntu, safe-mode and for Windows, like it should.

However, when I boot the computer, the GRUB screen doesnt show up at all, it just goes straight to windows (uses the windows bootloader).  And yes, when I was troubleshooting the GRUB install, I made sure to exactly type the command >>setup (hd0).  I think this has to do more with my custom partition scheme, this is the first time that I have installed Ubuntu with my own custom partitions (GRUB is working without any difficulties when I install in one of the 'cookie cutter' partition maps).  Perhaps there is some option or step in the install process that I am missing out on.  I have allready tried a reinstall twice, so I think its something I am doing or leaving out in the installation process.

---

### Post by meierfra. on 2008-06-14
Try SuperGrub (see my signature) and follow these instruction:
[URL="http://www.supergrubdisk.org/wiki/Howto_Fix_Grub"]
http://www.supergrubdisk.org/wiki/Howto_Fix_Grub[/URL]

If that did not help:

Do you have more than one hard drive?
Did you get any error messages while trying to reinstall grub?
Any chance that your MBR is "write" protected (check your bios)?
Post your "menu.lst" and post the output of

```
sudo fdisk -l
```
(l is a lower case L)

---

### Post by radiocognition on 2008-06-14
I am pretty sure that the the MBR isn't protected.  I have been changing all kinds of things with this system's boot record before I just wiped it all out.  Yes there is more than one disk, but I have them unplugged so that I dont accidentally overwrite them.

As for Super Grub Disk, I just downloaded and tried that.  Nifty little utility, but it was unable to find my /grub/menu.lst on the partition I pointed it to.  I will be holding onto this CD for the future, but for right now, it was unable to help me with my problem

As for the output of fdisk and my menu.lst file, I have to go and liveboot real quick.

---

### Post by radiocognition on 2008-06-14
Here are the results from fdisk:
```
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         701     5630751    7  HPFS/NTFS
/dev/sda2            3844        4998     9277537+  83  Linux
/dev/sda3            1169        3843    21486937+  83  Linux
/dev/sda4             926        1168     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Now here are what each of the partitions are:
/sda1               Windows System
/sda2               Ubuntu System Root
/sda3               /home partition
/sda4               Swap Space

Now there does exist a file at /sda2/boot/grub/menu.lst, here are the contents:
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
# kopt=root=UUID=7aa64497-f548-40d5-9761-e1974e6a1c6e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7aa64497-f548-40d5-9761-e1974e6a1c6e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7aa64497-f548-40d5-9761-e1974e6a1c6e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by meierfra. on 2008-06-14
This is strange. According to fdisk you only have one hard drive. But  according to menu.lst Ubuntu  thinks it is on the second hard drive: (hd1,1)

(Grub starts counting at zero, so (hd1,1) means second partition on the second hard drive)

Did you have any hard drives (or flash drives) plugged in, while you installed Ubuntu?


Is your hard drive a USB drive?

---

### Post by meierfra. on 2008-06-14
Edit: Read my next post first.

Is where anything plugged  in  which could confuse Grub?  Is your cd-drive plugged in correctly? Try this


Boot from the live cd. Open a terminal and type

```
sudo grub
```

and at the grub prompt:

```
find /boot/grub/menu.lst
```

The output should be

(hd1,1) or (hd0,1) or "file not found". In the first two cases:

```
root (hd1,1)    (use the output from "find .."
setup   (hd1)     (use the first number from the output)
quit
```


Also open menu.lst via

```
gksudo gedit /mount_point_of_sda2/boot/grub/menu.lst
```


and change all "(hd1,1)" to "(hd0,1)"

(there is one "# groot=(hd1,1)" and three "root (hd1,1)" which you need to change. Just change the first number to "0". Don't change anything else)

Save the file and reboot.

---

### Post by meierfra. on 2008-06-14
If you actually do have the a second hard drive, then you might be able to solve your problem by simply changing the boot order in the bios. (try this before you do anything else)

---

### Post by Duck2006 on 2008-06-14
Do what "meierfra" posted, but was ubuntu the first drive or second?

---

