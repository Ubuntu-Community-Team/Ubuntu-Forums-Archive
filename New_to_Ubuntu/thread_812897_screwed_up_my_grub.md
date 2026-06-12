---
title: "screwed up my grub"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by xiaozhu on 2008-05-30
i was trying to make vista as the first option but i screwed it now!

i remembered i change something like (hd 0,0) to a different number.

is there anyway i can recover the original menu.lst file>?

---

### Post by Duck2006 on 2008-05-30
Some info on grub that may be of help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

---

### Post by tim.n9puz on 2008-05-30
Which editor did you use to make the changes? Some create backups by default, others you have to specifically request one be made. I usually use the editor called nano and it requires a -B parameter to cause a backup to be created.

In the /boot/grub directory you have the menu.lst file. If a backup file exists it is likely named menu.lst~. If so, you should make a copy of the current menu.lst and then rename the backup to menu.lst.

For future reference it's a good idea to always make a copy of configuration files before you tinker with them. I try to remember to do it no matter how sure I am of the change I'm about to make.

Tim

---

### Post by xiaozhu on 2008-05-30
yes i found the file after booting in the liveCD

i tried to revert it back but i can't

it says i dun have permission to do so, can anyone help me?

---

### Post by lolwhites on 2008-06-07
Having the same problem. I screwed up my GRUB, I can see the backup when I boot with the live CD, but cannot rename it. Surely there must be an easz waz of doing this.

---

### Post by drs305 on 2008-06-07
Read my entry on grub displays and boot options. It won't help you restore your old grub but will help you preserve your next one:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

Go to System > Administration > StartUp-Manager> Boot Options. You can set the default operating system from there (if you haven't messed up grub too much). ;-)

You can do a search to see if perhaps there is a backup copy of menu.lst in the directory:
```
find /boot/grub -iname menu*
``` 
You'd be looking for something like menu~.lst, menu.lst.bak, ~menu.lst, etc

---

### Post by lolwhites on 2008-06-07
I managed to get the backup working (by booting into XP, deleting *menu.lst* and renaming *menu.lst-backup* as *menu.lst*). So it's now working but I have an old grub which doesn't boot the latest kernel.

How can I update the grub to do that? I've got QTGRUBEditor, but am loath to touch it after last time. I've noticed that the entries which let me boot into a kernel that works have a UUID in the entry. Do I need to know that too?

---

### Post by drs305 on 2008-06-07
> **lolwhites said:**
> How can I update the grub to do that? I've got QTGRUBEditor, but am loath to touch it after last time. I've noticed that the entries which let me boot into a kernel that works have a UUID in the entry. Do I need to know that too?

If the latest kernel isn't shown as installed in synaptic, install it. If it is already displayed, try reinstalling it. That might refresh the grub menu.

If that doesn't work, post your menu.lst and maybe we can patch it together:
```
cat /boot/grub/menu.lst
```

---

### Post by louieb on 2008-06-07
> **lolwhites said:**
> ...I have an old grub which doesn't boot the latest kernel..... UUID in the entry. Do I need to know that too?

look in /boot to see what the latest kernel and initrd files are. (they will have the biggest # at the end. 

Just cut and paste one of your other entries.  The only thing  that is different is the kernel file name, initrd file name, and title.  

And yes you need the UUID but that should remain the same.

---

### Post by lolwhites on 2008-06-08
I tried reinstalling the latest kernel but although I had to restart, the GRUB menu remains the same. Its relevant contents are:
> title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1
savedefault
makeactive

The most recent kernel in /boot is 2.6.24-19

I've tried adding a new entry with QTGRUB Editor, but when I reboot, the new option doesn't work.

EDIT: Opened menu.lst with sudo gedit, copied the first entry and re-pasted it at the top of the list then changed the kernel number to the most recent one. It seems to work fine now, but was that the right thing to do?

---

### Post by wdaniels on 2008-06-08
Run:

```
sudo update-grub
```

This should automatically add the right menu entries based on a special template in the comments at the start of the menu.lst.

If that does not work then probably something has removed (or mangled) those magic comments in the menu.lst (perhaps this GUI GRUB editor that you mentioned - I'm not familiar with it) and you will need to fix that otherwise you'll have the same problem with each kernel update.

So, if update-grub doesn't fix it, post the *entire* menu.lst file so we can sort it out.

---

### Post by lolwhites on 2008-06-08
I don't think *sudo update-grub* changed anything. The menu.lst file is:
> default 0
timeout 10

title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1
savedefault
makeactive
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
# kopt=root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro

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
# howmany=2

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


---

### Post by drs305 on 2008-06-08
> **lolwhites said:**
> I don't think *sudo update-grub* changed anything. The menu.lst file is:

First, save your current menu.lst (the standard combined with your entries):
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak1

```

Then make this your menu.lst:
```

hiddenmenu
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
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout	10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
##### hiddenmenu

# Pretty colours
color cyan/blue white/blue		##### #color cyan/blue white/blue

#A splash image for the menu
#splashimage=(hd1,0)/boot/grub/splashimages/gunhole.xpm.gz

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
# kopt=root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet

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
# howmany=10

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1
savedefault
makeactive

### END DEBIAN AUTOMAGIC KERNELS LIST


```

Then use StartUp-Manger to safely make changes. ;-)
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by wdaniels on 2008-06-08
For the automagic stuff to work (which is what automatically maintains the kernel list with each update), the Linux entries should be within the automagic markers:

```
### BEGIN AUTOMAGIC KERNELS LIST
...default options....
...kernel menu list...
### END DEBIAN AUTOMAGIC KERNELS LIST
```

Since they did something recently to try and make it keep the manual edits within this section, it makes things a bit more complicated than it used to be, so probably the easiest way to fix all this now is probably to do:

```
ucfr --purge grub /var/run/grub/menu.lst
```

Then replace your menu.lst with the following, which has your Windows entry added manually at the top and then a blank automagic section:

```
default 0
timeout 10

title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1
savedefault
makeactive

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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c9f43096-8638-436d-b478-195629c17dbe ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##



### END DEBIAN AUTOMAGIC KERNELS LIST
```

Now you run:

```
sudo update-grub
```

And select to use the package maintainer's version when prompted. This should regenerate the kernel list within the automagic section using the kernels found under /boot.

You should not manually edit the stuff within the automagic section - if you want to change the options used in generating these entries, do it by modifying the default options in the comments at the top of that section.

---

### Post by wdaniels on 2008-06-08
Oops, I got sidetracked wondering why [update-grub stopped regenerating missing kernel lines]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/229656") and so I missed the reply from drs305 :D

---

