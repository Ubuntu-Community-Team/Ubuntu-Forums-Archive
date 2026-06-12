---
title: "GRUB, menu.lst, number of kernel entries"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by yc2 on 2008-07-01
Hello :)

I don't understand some basics of boot/grub/menu.lst.

There is one line like this:
```
### BEGIN AUTOMAGIC KERNELS LIST
```

I think I understand that BEFORE this line I can specify, on uncommented lines (not beginning with # or ##) how GRUB works. I can for example set the time for how long the start-menu is showing (ten seconds in my case).

However, what I don't understand is what happens between these lines:
```
### BEGIN AUTOMAGIC KERNELS LIST
...
...

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I do not understand this line:
```
## DO NOT UNCOMMENT THEM, Just edit them to your needs
```

I have done the automatic kernel updates. I wish a few old kernels to be left as safety precaution. However in my case only the new, latest kernel seem to be accessible. At least that is the only thing I can see in GRUB.

I think the corresponding part in GRUB is this:
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```

So, please tell me, what should I do in order to save, for example the three latest kernels?

I thought that the most natural thing would be to uncomment one line and write:
```
howmany=3
```

But the instruction tells me not to uncomment lines? I think there is no idea to edit lines that start with # or ##.

How do I make my system save the three latest kernels and keep the corresponding entries in menu.lst?

Sorry for long question about small thing ;)


menu.lst
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
default saved

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
# kopt=root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Brynster on 2008-07-01
simply amend the number on the ```
# howmany=all
``` to ```
# howmany=3
```

then a little further down the menu.lst file you'll see alll the kernal variants you have available to use.

just delete the sections you don't want listed. 

eg 
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
default saved

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
# kopt=root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro

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
# howmany=3

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
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

this will update you grub screen. Alternative use synaptic to remove the kernel revision you don't want and that will also update grub i believe.

---

### Post by nick_h on 2008-07-01
There is a program called *update-grub* which maintains grub entries between the lines:

### BEGIN AUTOMAGIC KERNELS LIST
and
### END DEBIAN AUTOMAGIC KERNELS LIST

It will look at commented lines for its configuration, so as it says in the file don't uncomment them.

The *update-grub* program will be run when you install or remove kernels but you can also run it yourself with:
```
sudo update-grub
```

As Brynster said if you want 3 kernel versions you can specify:
```
# howmany=3
```

You can check what kernels you have installed through Synaptic or by a simple *ls* command:
```
ls -l /boot/vmlinuz*
```

---

### Post by yc2 on 2008-07-01
Thanks for clear advice. However, I still don't understand how my system works.

Following your suggested commands, I seem to have four kernels in my system:

```
$ ls -l /boot/vmlinuz*
-rw-r--r-- 1 root root 1904248 2008-04-10 18:51 /boot/vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 1921944 2008-05-01 19:59 /boot/vmlinuz-2.6.24-17-generic
-rw-r--r-- 1 root root 1921528 2008-05-29 04:39 /boot/vmlinuz-2.6.24-18-generic
-rw-r--r-- 1 root root 1920472 2008-06-18 20:11 /boot/vmlinuz-2.6.24-19-generic
$ 

```
But in my menu.lst I only have the OLDEST kernel as an entry!

Now I maybe remember, that for every kernel update I get a choice during the install (keep old version of ... )  I accept the recommended choice (which may be "keep old menu.lst". Sorry I don't remember exactly.


I now change as you have adviced me, into:

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=3
```

When I reboot I can still only see one old kernel.

I think you have helped me understand the problem to some extent, but now another problem arises:

I seem to be still running on the oldest kernel! (Maybe because I followed the kernel-installers advice: "keep old version?"). What should I do to get a full list of the four available kernels in menu.lst.

Thanks for the help I already got.

---

### Post by t.septekin on 2008-07-01
I believe your howmany=3 entry will apply to future updates and not to your present situation.
I would suggest that you first make a backup copy of your menu.lst.
Then change all entries that contain 2.6.24-16 to 2.6.24-19.
Restart: you should be using the latest kernel.

As you wish to see all four kernels in your menu, edit your menu.lst to include:
title
root
kernel
initrd
entries for the other three, by copying them from the first but changing only 2.6.24-xx part.
Best of luck.

---

### Post by plucky on 2008-07-01
> Now I maybe remember, that for every kernel update I get a choice during the install (keep old version of ... ) I accept the recommended choice (which may be "keep old menu.lst". Sorry I don't remember exactly.



That is why you only have one kernel.You should select "install the package maintainers version" so the new kernels will be put into menu.lst.

You are also probably still running the old kernel,as that is what is booting in menu.lst.You could edit your menu.lst to load the new kernel,or possibly reinstall the newer kernel images and see if that will update the menu.lst file.

I don't know if re-installation would work as I have never done it.

Good Luck

---

### Post by drs305 on 2008-07-01
I highly recommend you use StartUp-Manager rather than editing the grub menu.lst itself. It is almost error-proof and you can tweak a wide variety of options, including the number of kernels to display on boot.

To install:
```
sudo aptitude install startupmanager
```

To run:
System, Admin, StartUp-Manager
or:
gksudo startupmanger

I've posted info about SUM:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

There is also information about editing menu.lst  (if you must ;-) )

---

### Post by yc2 on 2008-07-01
Thanks for all advice.

I tried editing my menu.lst as attached below. I then started the newest (2.6.24-19) kernel. I can only say the result was not pretty. It went into text mode login and eventually into "low-resolution graphics mode". If you want more details on this please ask and I will tell you details.

I am now back on my old (backed up file of) menu.lst, system boots OK, but STILL RUNNING OLD KERNEL.

After your explanations I realize that I will have to put the newer kernels into play somehow, but HOW?

Uninstall and reinstall kernel via synaptic? But maybe risky since I have no experience?

Thanks a lot guys you are great!


```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by drs305 on 2008-07-01
Installing and uninstalling kernels via synaptic isn't difficult. If you have a current kernel and it works well, you should keep it as a backup in case the new kernel causes problems with your system. I'd advise keeping the current recovery mode option and one old kernel displayed in the grub menu. Speaking of which...

If you have StartUp-Manager installed, it has an option on the main tab to select which kernel you want to start. If you install new kernels via synaptic the StartUp-Manager will be updated, as will it if you remove kernels via synaptic. 

I told you it was easy!

---

### Post by nick_h on 2008-07-01
> After your explanations I realize that I will have to put the newer kernels into play somehow, but HOW?

Your listing of /boot shows 4 kernels installed.

To update grub simply run:
```
sudo update-grub
```

This will replace the code between "### BEGIN AUTOMAGIC KERNELS LIST" and "### END DEBIAN AUTOMAGIC KERNELS LIST" with new entries based on the kernels installed and the options in your menu.lst file.

Your Windows entry below "### END DEBIAN AUTOMAGIC KERNELS LIST" will be left unchanged.

---

### Post by t.septekin on 2008-07-01
Looks like I landed you in the you know what. Your edited menu.lst looks like mine, except that it has too many savedefault lines. Would you like to try again, but with only the 2.6.24-19 option and no savedefault to see if you can boot into the latest kernel (none of the older ones as choices)?

---

### Post by yc2 on 2008-07-01
Thanks again guys!

t.septekin
I made an erroneous conclusion when I said it didn't work adding kernel entries into menu.lst. I added kernel 17-19. I only tested kernel 19 that only could go into low resolution graphics mode. I now tested kernel 16-18 that all work well. Kernel 19 can still only go into low res. mode. "Cannot detect screen/graphics". So maybe the problem is kernel 19. it is not compatible with my computer, which is strange, I think (HP Pavillion laptop 6751.eo, nvidia 8600) Therefore I didn't try your latest suggestion (keeping only kernel 19 in the file).

menu.lst now looks like this:
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
default saved

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
# kopt=root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic; CAN ONLY RUN IN LOW RES. MODE
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

drs305
I installed the startup manager. As I understand it rewrites the menu.lst. I found the rightmost panel relevant (see enlosed picture). However, as I understood from menu.lst, it rewrites the "howmany"-parameter. Maybe I need to edit the file myself by adding the old kernels that I clumsily did not include at update time ("keep old verion of menu.lst").

nick_h
I am in the process of trying your suggestion. I will make a backup copy of menu.lst and then try the update-grub. I will come back with results.

Thanks all.

---

### Post by yc2 on 2008-07-01
I keep trying, aided by you guys ...

nick_h
I tried update-grub:
```

$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```
(I can see the traditional boot-splash starting any of the kernels, but update-grub says different.)

As I understand menu.lst is similar to the one I wrote by hand. New menu.lst after update-grub:

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
default saved

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
# kopt=root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic; CAN ONLY RUN IN LOW RES. MODE
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2d9151f6-6fde-4b90-96f0-fe5fa1ceb727 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
Kernel 16-18 works well, kernel 19 cannot detect my nvidia card!!!

I can only run kernel 18 and keep a good backup copy of menu.lst and wait for the next kernel update! Maybe nothing else to do? I think there is no particular incompatibility between kernel 19 and nvidia cards, my friends run them. However, I just can't make kernel 19 work.

---

### Post by t.septekin on 2008-07-01
After all, the objective of keeping some older kernels in your machine is that, if the latest one does not work for you, you revert to the older one. This seems to be your situation. Hope the next update will be be better for you!
Enjoy your ubuntu, old or new.

---

### Post by yc2 on 2008-07-01
> **t.septekin said:**
> ... Enjoy your ubuntu, old or new.

I will :)

I learnt a good deal from this thread, now I will "install the package maintainers version", use update-grub, set: howmany=all ...

Thanks all.

---

### Post by drs305 on 2008-07-01
> **yc2 said:**
> 
drs305
I installed the startup manager. As I understand it rewrites the menu.lst. I found the rightmost panel relevant (see enlosed picture). However, as I understood from menu.lst, it rewrites the "howmany"-parameter. **Maybe I need to edit the file myself by adding the old kernels that I clumsily did not include at update time** ("keep old verion of menu.lst").


yc2, 

The short answer is: **let SUM do it for you**. See 5 for more details.

1. Each time you close SUM, grub's menu.lst is rewritten to reflect SUM's settings and what kernels are actually installed on the computer.

2. StartUp-Manual can limit the number of kernels *displayed* but will not remove the actual kernels from your computer. 

3. If you set the SUM kernels to less than the number installed, the menu.lst will be shortened to the number you have asked to be displayed. SUM will edit menu.lst on closing to include the number of kernels you have set in 'Limit the number of kernels in the boot menu'.

If you set the SUM kernels to more than the number installed, the menu.lst will show all installed kernels.

4. Synaptic/apt removes/installs kernels. SUM only effects the grub menu and what is displayed on boot.

**5**. To add kernels that are not displaying properly because you manually edited grub:
Reduce the SUM displayed value to 1. This will rewrite the number of kernels to be displayed in grub to 1. Close SUM then open it again and change the display number to the number of kernels installed (or more). Close SUM again and all the kernels will again be entered in grub. If you now want to limit it to 2 or 3, you can do so.

6. I recommend always leaving the display value to at least 2 so you can revert to an older kernel. I also suggest having the recovery mode ticked in SUM.

I've written more here:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by nick_h on 2008-07-01
> I learnt a good deal from this thread, now I will "install the package maintainers version", use update-grub, set: howmany=all ...
The manual page for update-grub is worth a read if you want more information:
```
man update-grub
```

There is also a [grub manual](http://www.gnu.org/software/grub/manual/grub.html).

---

### Post by yc2 on 2008-07-02
I sometimes forget "man" as a source of information, thanks for reminding me about it.

I tried the startupmanager. My menu.lst was the one I listed above, produced by update-grub. I checked "limit number of kernels", set number of kernels to "1". When exiting the program the "performing postconfiguration tasks" continued "forever" until I stopped it after 6 minutes. I think menu.lst was unchanged, but I could not use update-grub afterwards:

```
$ sudo update-grub
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

```
After restart of the system and reissuing "update-grub" a good and interesting (as I see it) thing happened. update-grub started a ncurses-interface and gave me several alternatives one of which was "install the package maintainers version" which I quickly chose ;)

After that update-grub gave me an entirely new menu-lst with all four kernels. I run this menu.lst now. (I only added "savedefault" for a few more kernels).

A small hobby of mine is to try to keep my system "clean" and I guess that "2.6.24-19-generic" is not properly installed. **I would like to try to mark it for reinstallation in Synaptic. Do you think any problems may occur?**

Thanks everyone, this thread has taught me new things about my system :)

---

### Post by drs305 on 2008-07-02
> **yc2 said:**
> 
A small hobby of mine is to try to keep my system "clean" and I guess that "2.6.24-19-generic" is not properly installed. **I would like to try to mark it for reinstallation in Synaptic. Do you think any problems may occur?**

Thanks everyone, this thread has taught me new things about my system :)

You shouldnt have any problems reinstalling kernel 19. Once you have, you can check to see if it is the default by typing:
```
uname -r
```

If 19 isn't running you can change the default startup OS in StartUp-Manager. 
I think the problem you had getting the grub menu to update was because of all the manual editing. You should now be able to make the changes with StartUp-Manager - display times, number of kernels, etc.

---

### Post by yc2 on 2008-07-02
I'm not sure it was the manual editing that caused the problems. I think the basic problem was that I chose "keep old menu.lst" at kernel updates. Checking with
uname -r
always ran the kernel I had chosen at boot-time.

Anyway, many thanks for help here, I now hope the menu.lst-problems are history.

I tried synaptic reinstall 2.6.24-19-generic but the same graphics problem appears for this kernel.

It seems my system fits into this category:
[https://bugs.launchpad.net/ubuntu/+bug/242527](https://bugs.launchpad.net/ubuntu/+bug/242527)

the only way to get past it seems to be clean install and right now it is not worth it.

But I can fall back on kernels 16-18 and I have now set menu-lst-parameter "howmany=all" so hopefully *knock on wood* it will be OK.

Thanks all :)

---

### Post by yc2 on 2008-07-03
Regarding:
[https://bugs.launchpad.net/ubuntu/+bug/242527](https://bugs.launchpad.net/ubuntu/+bug/242527)

The updates that came today (July 3 - 08 ) seem to have fixed the problem between Nvidia-cards and kernel 2.6.24-19-generic, at least in my system.

---

