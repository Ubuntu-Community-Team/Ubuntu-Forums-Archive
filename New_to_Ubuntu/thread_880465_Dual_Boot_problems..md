---
title: "Dual Boot problems."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Warpster Buntu on 2008-08-05
I've been using Ubuntu for a couple weeks now, and everything has been working fine. However, I have reason to switch to Windows. When I installed Ubuntu, I did so as a dual boot to Windows, and at the restart it always asked me whether or not to boot either one.

However, now it goes straight to Ubuntu, and when I try looking around, I still can't find Windows. Is it buried somewhere in the laptop, or has some ill-fate overtaken the laptop?

Will I be forced to reinstall Windows?:confused:

---

### Post by cdtech on 2008-08-05
Can we see your "/boot/grub/menu.lst" file. It may just need tweaked a bit to find the correct drive.....

---

### Post by jualin on 2008-08-05
Using the terminal post the output of > cat /boot/grub/menu.lst

---

### Post by jualin on 2008-08-05
If it needs tweaking you can install a program called "startupmanager" which edits the "menu.lst" file for you using the Graphic User Interface. You can install it via Synaptic or via terminal > sudo apt-get install startupmanager Hope this works

---

### Post by Warpster Buntu on 2008-08-05
Well, I typed it into the terminal and it replied that there was no such file or directory...

Did I type something wrong?

---

### Post by jualin on 2008-08-05
Probably you thought that the "lst" part was "1st". The command has an **l** (lower case **L**) not a **1** (one)

---

### Post by kansasnoob on 2008-08-05
> **jualin said:**
> If it needs tweaking you can install a program called "startupmanager" which edits the "menu.lst" file for you using the Graphic User Interface. You can install it via Synaptic or via terminal  Hope this works

+1

Then you find it by going to System > Administration > Startup-Manager and see this:

[ATTACH]80256[/ATTACH]

Note: I clicked the "toggle" to the right of "default operating system" to expand the operating system menu.

If Windows is in the list be sure and (tick) Show Bootloader Menu and Show Boot Splash.

---

### Post by Warpster Buntu on 2008-08-05
Alright. I did the start up manager, and all it shows is Ubuntu.

Did XP just mysteriously disappear?

---

### Post by Warpster Buntu on 2008-08-05
Bump

---

### Post by cdtech on 2008-08-05
Within Ubuntu can you see the windows partition under places? Or do you have it mounted?

If not do "fdisk -l" to list the partitions and see if we can even mount it.

Still need to see the "sudo gedit /boot/grub/menu.lst" copy and paste.

---

### Post by Warpster Buntu on 2008-08-05
# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
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
timeout		5

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
# kopt=root=UUID=7270d166-0e77-414e-8b03-3a0937c59335 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7270d166-0e77-414e-8b03-3a0937c59335 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7270d166-0e77-414e-8b03-3a0937c59335 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Is that it?

---

### Post by cdtech on 2008-08-05
Thats it, we just need to add an entry for windows. Can you post the output of "fdisk -l" so we know which partition to boot to.

---

### Post by Warpster Buntu on 2008-08-05
How would I type that in the terminal?

---

### Post by kansasnoob on 2008-08-05
> **cdtech said:**
> Thats it, we just need to add an entry for windows. Can you post the output of "fdisk -l" so we know which partition to boot to.

Agreed, we either need the output from:

```
sudo fdisk -l
```

Or a screenshot from Gparted (aka: partition editor) which may need to be installed by:

```
sudo apt-get install gparted
```

Then it'll be found in System > Administration > Partition Editor, and you'll get a graphic like this:

[ATTACH]80261[/ATTACH]

---

### Post by kansasnoob on 2008-08-05
> **Warpster Buntu said:**
> How would I type that in the terminal?

You can just "cut-n-paste" my commands.

And ignore that "thumbnail" in my last post .......... I goofed!

---

### Post by Warpster Buntu on 2008-08-05
Here is the pic:

[ATTACH]80262[/ATTACH]

---

### Post by kansasnoob on 2008-08-05
Do you have more than one hard drive?

If so you'll have to click the "toggle" in the upper right hand corner to see them all.

---

### Post by Warpster Buntu on 2008-08-05
By the looks of this, no.

*Sigh*

---

### Post by kansasnoob on 2008-08-05
> **Warpster Buntu said:**
> By the looks of this, no.

*Sigh*

Then you have no windows on the machine!

Partitions don't just disappear without some physical action by someone.

Do you have the Windows installation disc(s), and if so is it Vista or XP?

---

### Post by Warpster Buntu on 2008-08-05
I probably have the XP disc.

I know that that I didn't delete it, because it was still there when I finished booting Ubuntu and it appeared for quite a while.

Well, I guess I'm just going to have to reinstall.

---

### Post by kansasnoob on 2008-08-05
> **Warpster Buntu said:**
> I probably have the XP disc.

I know that that I didn't delete it, because it was still there when I finished booting Ubuntu and it appeared for quite a while.

Well, I guess I'm just going to have to reinstall.

Does anyone else use your computer?

I guess it doesn't really matter, but I can guarantee you that no partition just disappears without some physical action.

But since you're going to reinstall, and assuming you want to dual boot, I'd use Gparted from the Ubuntu Live CD (you can't do it from the mounted Ubuntu OS) I'd resize Ubuntu (partition /dev/sda1) and then follow this tutorial to reinstall Windows:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Just DO NOT try to "sandwich" windows between sda1 and your swap which is sda5 (contained in extended partiton sda2) or you'll end up with problems.

---

### Post by jualin on 2008-08-06
I agree with everyone else on this post. Windows doesn't seem to be installed on your machine. But like kansasnoob said "no partition just disappears without some physical action". Something that calls my attention is that your hard drive shows that it has only 27.95 GB so maybe there is another hard drive inside of your machine or something wrong with the hard drive that made the rest disappear. Just a shot in the dark.

---

