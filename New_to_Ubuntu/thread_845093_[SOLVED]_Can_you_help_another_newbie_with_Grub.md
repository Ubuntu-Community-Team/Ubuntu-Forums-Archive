---
title: "[SOLVED] Can you help another newbie with Grub?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by PicklePouch on 2008-06-30
Hi all, this is my first post here so I'd like to start by saying what a great forum this is, I've been searching it extensively over the past week trying to solve my own problem before asking for help but alas I just can't do it alone.

A pal of mine put me on to Ubuntu so I gave the 8.04 live cd a go, not installing at first just running from the disk, suffice to say I loved it so I 'tried' to install it alongside Win XP Pro 64, well XP was on a Sata Raid 0 and Ubuntu I installed on an old 80gig IDE. This caused me no end of problems with one booting but not the other and visa versa. 

After many hours of searching for solutions and finding I didn't understand any of them I decided to try to simplify things and split the Raid array back into 2 seperate drives installing XP on the first and Ubuntu on the second leaving the IDE empty ( good for storage and backup I guess). Anyhow I've had a little more success this way, I've set the drive containing Ubuntu to boot first in BIOS the grub loads and I can boot XP from the grub menu, however, selecting the Ubuntu 8.04 from the grub list gives me an error 17 cannot mount the selected partition.

After more and more Googling, searching and reading things I'm struggling to understand I beleive some settings in Grub are to blame, is this correct? And if so, how do I fix it?

Thanks for taking the time to read my cry for help and any assistance will be gratefully accepted.

---

### Post by unutbu on 2008-06-30
Hi PicklePouch, welcome to Ubuntu. We'll need a bit more information to help you. Please boot from the LiveCD. Open a terminal.
Then post the output of the command
```

sudo fdisk -l
```

---

### Post by PicklePouch on 2008-06-30
Hi Unutbu and thanks for the welcome. 

Sudo fdisk -l returns the following:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75bf75bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cd9b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29164   234259798+  83  Linux
/dev/sdb2           29165       30401     9936202+   5  Extended
/dev/sdb5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcba2cba2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           14335       14946     4915890    5  Extended

---

### Post by unutbu on 2008-06-30
Please post the output of 
```
sudo mkdir /Ubuntu
sudo mount /dev/sdb1 /Ubuntu
cat /Ubuntu/boot/grub/menu.lst
```

---

### Post by PicklePouch on 2008-06-30
Ok buddie the first two commands returned nothing but I'm assuming that they shouldn't. The 3rd returned a whole lot of text, here goes :

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
# kopt=root=UUID=524573e2-053e-4b44-9f86-d9b025fea501 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=524573e2-053e-4b44-9f86-d9b025fea501 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=524573e2-053e-4b44-9f86-d9b025fea501 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Professional x64 Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Again as a newbie I wasn't sure if you needed all the lines starting with a hash so sorry if you didn't.

---

### Post by unutbu on 2008-06-30
```
gksudo gedit /Ubuntu/boot/grub/menu.lst
```
Find and replace all occurrences of (hd2,0) with (hd0,0). There should be four places that need changing.
Save and exit. Reboot, and see if you can now boot both Ubuntu and Windows.

---

### Post by ChameleonDave on 2008-06-30
**Edit: sorry, this solution would apply if GRUB failed before it got to the OS choices list.  If it fails *after*, then you need to edit /boot/grub/menu.lst.**

If you make any changes -- physically or in the BIOS -- to the drives connected to the system and the partitions on them, then GRUB can be left trying to load its files from the wrong location.  This is because GRUB goes by rules like "load files from the fifth partition of what the BIOS tells me is the second drive attached to the machine".

You can get info about all the drives by running the "fdisk -l" command as root (normally by putting "sudo" in front of it).

You will no doubt have to reinstall GRUB, which is easy.  Just boot from a Linux live CD, go to a command-line terminal and run "grub" as root.  Grub will then take over the terminal and allow you to type in the following:

```
grub> find /boot/grub/stage1
 (hd1,6)

grub> root (hd1,6)

grub> setup (hd1)

grub> quit
```

The above is an example showing how it would work on my computer.  As you can see, the first command comes back with the information that the files GRUB needs are on hard drive 1, partition 6.  I then used that info to set the root partition as being hd1,6, and then told it to install itself to the master boot record of hard drive 1.  Then I quit.

You'll find that if you press Tab while typing "root (hd", GRUB will helpfully do some autocompletion for you, suggesting possible drives and suchlike.  In fact, the info it gives you as you do this can actually dispense with the need to use "find" or "fdisk".

---

### Post by PicklePouch on 2008-06-30
I've found 3 of the 4 instances under the End Default Options, 1 relating to Ubuntu 8.04 kernel, 1 for recovery mode and 1 for the memtest can't find the fourth.

---

### Post by philinux on 2008-06-30
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)


It's in this section

---

### Post by unutbu on 2008-06-30
The fourth is the one that says
```

#groot=(hd2,0)
```

In gedit, go to the menu bar and click Search>Replace
you can use that to find all (hd2,0) and replace them with (hd0,0).

---

### Post by ChameleonDave on 2008-06-30
> **PicklePouch said:**
> I've found 3 of the 4 instances under the End Default Options, 1 relating to Ubuntu 8.04 kernel, 1 for recovery mode and 1 for the memtest can't find the fourth.

Here's a fancy command-line way of doing it flawlessly:

```

sudo -i
cd /boot/grub
cp menu.lst menu.lst.backup
sed "s/(hd2,0)/hd(0,0)/g" menu.lst.backup > menu.lst
exit

```

---

### Post by PicklePouch on 2008-06-30
Thank you Unutbu, that has fixed it, both Os's are now booting from Grub. Was this an error on my part when installing or is this Grubs fault, it would be nice to know to help me understand rather than it being fixed and me being none the wiser. And thanks also Dave for your help.

By the way I'm installing the Ubuntu updates which has alerted me to a new menu.lst file, I decided to overwrite with the new one and edit this one the same. Was this a wise choice?

---

### Post by ChameleonDave on 2008-06-30
> **PicklePouch said:**
> 
By the way I'm installing the Ubuntu updates which has alerted me to a new menu.lst file, I decided to overwrite with the new one and edit this one the same. Was this a wise choice?

It doesn't matter too much whether you let it overwrite it, as long as you take a peek afterwards to make sure that GRUB will still be looking in the right places.

---

### Post by philinux on 2008-06-30
I always choose the package maintainers version.

---

### Post by ChameleonDave on 2008-06-30
Note that, if some weird thing happens to your menu.lst file or to your partitions, and therefore GRUB can't find the correct partition to boot from, you don't necessarily have to use a live CD to fix it.

GRUB itself contains an interface that allows you to specify all that stuff in real time.  On the boot screen, you'll notice that it allows you to press "e" to edit the entries.  With a little fiddling, you'll quickly see how to make GRUB boot from any partition you desire, even if menu.lst is completely wrong.  Once you've managed to boot, you can then correct menu.lst.

---

### Post by PicklePouch on 2008-06-30
Well that didn't go according to plan, after updating the menu.lst file during the Ubuntu updates and then opening it with gedit I find the file is blank, empty nothing there at all not a sausage. What happened more importantly what do I do now. After a week of trying I had it working for 5 mins then I screwed it.

---

### Post by ChameleonDave on 2008-06-30
> **PicklePouch said:**
> Well that didn't go according to plan, after updating the menu.lst file during the Ubuntu updates and then opening it with gedit I find the file is blank, empty nothing there at all not a sausage. What happened more importantly what do I do now. After a week of trying I had it working for 5 mins then I screwed it.

Are you absolutely sure?  It would also come up blank if you got the filename slightly wrong.

Type this into the terminal:

```
cat /boot/grub/menu.lst
```

Also, if something happens to your menu.lst file, there are almost certainly backups of it.  Just look in the directory:

```
ls /boot/grub/menu*
```

---

### Post by unutbu on 2008-06-30
Here is an explanation of the problem and the fix:

First clue: You were able to select and boot Windows from the GRUB menu, so I knew your menu.lst was getting read. 
Second clue: You were getting error 17 when trying to boot Ubuntu.
According to [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting), Error 17 means
> 
17 : Cannot mount selected partition

This is usually a very easy error to fix. It means that the line which says "root (hdx,y)" has the wrong numbers x and y. (hdx,y) is GRUB notation for the y-th partition on the x-th hard drive (with counting starting at 0). 

Notice your original /boot/grub/menu.lst contained a stanza like this: 
> 
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=524573e2-053e-4b44-9f86-d9b025fea501 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

For some reason, when Hardy installed itself, it thought your linux partition was on the third hard drive. However, when you booted up, the BIOS thought your linux partition was not the third hard drive. 

So clue #3: Your Windows boots, and it uses "root (hd1,0)", so the BIOS must think Windows is on your second hard drive. 

So... Linux is not on the third hard drive (according to the BIOS, since it won't boot with root set to (hd2,0)) and Linux is not on the second hard drive because Windows is successfully booting from there. Genius that I am, I deduced Linux must be on the first hard drive.

So the fix was simply to change all occurrences of (hd2,0) to (hd0,0).

---

### Post by PicklePouch on 2008-06-30
Thanks Dave.. that command worked and also showed me that I had the path of the gedit command wrong,  /ubuntu/boot/grub/menu.lst  instead of /boot/grub/menu/menu.lst. Would I just need the /ubuntu at the begining after booting from the Live CD? So all is well and Grub is booting correctly. Thanks again Unutbu and Dave.

Your last post Unutbu was the most definative and explanitory answer that I have been searching for for days, you put that in such a way that I understood even after using ubuntu for a small number of hours. I hope this post helps others with the same problem.

---

### Post by ChameleonDave on 2008-06-30
> **PicklePouch said:**
> Thanks Dave.. that command worked and also showed me that I had the path of the gedit command wrong,  /ubuntu/boot/grub/menu.lst  instead of /boot/grub/menu/menu.lst. Would I just need the /ubuntu at the begining after booting from the Live CD? So all is well and Grub is booting correctly. Thanks again Unutbu and Dave.

Yes, the file is normally located at */boot/grub/menu.lst*.

The slash at the beginning means "look start from the root partition that this Linux installation is on".  When you are running a live CD, the root partition is actually a RAM disk created just for that session, which vanishes when you shut down.  To access your partitions on your actual hard drives, you have to manually mount them with something like the "*sudo mount  /dev/sdb1  /Ubuntu*" that Unutbu showed you.  If you had put "*sudo mount  /dev/sdb1  /rude_bananas*" then you would have found the file at "*/rude_bananas/boot/grub/menu.lst*".  They only stay mounted like that until you shut down.

Here's a tip: when entering paths on the command line, press Tab for autocompletion.  That way, you can see if something exists before you press Enter.  For example, if you'd typed "sudo gedit /Ubu" and then hit Tab, the lack of autocompletion would have shown you that "/Ubuntu" did not exist.

---

