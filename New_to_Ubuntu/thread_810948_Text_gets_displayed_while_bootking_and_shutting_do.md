---
title: "Text gets displayed while bootking and shutting down"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by serid on 2008-05-28
Hi everyone,

This is an issue of a very little importance.
When I switch on my computer, I get a beautiful screen
displayed (grub-gfxboot). However, just after choosing 
the right kernel to load, some text gets displayed with
additional information about what is being loaded etc ...

Is there a way no to display it ? So after hitting the enter,
the Ubuntu screen shows up with the loading status bar ?

Also, the same happens when switching the computer off - a lot
of text gets displayed (which services are going down, etc ...)
and then the Ubuntu screen shows up with the status bar.
It would be nice to avoid that too ...


Cheers,

Adrian

---

### Post by Oldsoldier2003 on 2008-05-28
> **serid said:**
> Hi everyone,

This is an issue of a very little importance.
When I switch on my computer, I get a beautiful screen
displayed (grub-gfxboot). However, just after choosing 
the right kernel to load, some text gets displayed with
additional information about what is being loaded etc ...

Is there a way no to display it ? So after hitting the enter,
the Ubuntu screen shows up with the loading status bar ?

Also, the same happens when switching the computer off - a lot
of text gets displayed (which services are going down, etc ...)
and then the Ubuntu screen shows up with the status bar.
It would be nice to avoid that too ...


Cheers,

Adrian
example:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cd378e5e-24e4-4d76-a119-8aa6a678f6af ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
**quiet**
```

add quiet to suppress unnecessary messages. edit: opps soory, I neglected to mention this is your /boot/grub/menu.lst

---

### Post by leon.hh on 2008-05-28
Post the content of your /boot/grub/menu.lst and maybe I can help you

---

### Post by dwally89 on 2008-05-28
I have the same problem, and adding quiet doesn't seem to change anything.

---

### Post by Oldsoldier2003 on 2008-05-28
> **dwally89 said:**
> I have the same problem, and adding quiet doesn't seem to change anything.

make sure that nosplash is not in the menu entry as well. nosplash will suppress the splash screen.

---

### Post by dwally89 on 2008-05-28
Here is the contents of my menu.lst file:

```
default 0
timeout 0
hiddenmenu

title Ubuntu 8.04, kernel 2.6.24-17-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf
initrd /boot/initrd.img-2.6.24-17-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Dell Utility Partition
root (hd0,0)
chainloader +1
savedefault
makeactive

title Microsoft Windows XP Embedded
root (hd0,4)
chainloader +1
savedefault
makeactive
```

---

### Post by Oldsoldier2003 on 2008-05-28
hmm thats odd. IIRC you shouldn't be seeing a bunch of messages on boot. I removed the quiet parameter on purpose in order to display the messages...
edit: try this:

```
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf quiet splash
```

---

### Post by dwally89 on 2008-05-28
Any ideas how to hide the text?

---

### Post by Oldsoldier2003 on 2008-05-28
> **dwally89 said:**
> Any ideas how to hide the text?

add quiet splash to the end of the kernel line

---

### Post by inportb on 2008-05-28
quiet and splash are really not the issue, as i've been seeing these messages as well. they don't bother me, so i haven't been hunting them down.

but... it would be nice to know why it happens =D

---

### Post by Dazed_75 on 2008-05-28
Personally my preference is to keep seeing all those messages so if there is ever a problem starting up or shutting down, I have a real visual cue whether things are happening, failing, or are just stuck on some step.  Too bad you can't see this kind of info in windows when it has problems.

OTOH, some folks do not want to see it and linux gives you the choice and control.  While oldsolders fix might work, it lacks one step and is not a permanent fix.  The proper place to make the change is in a slightly different place in /boot/grub/menu.lst.  Before I show it to you I ask that you please make a copy of that file.  So in a terminal, do this:

  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

Once you have done that, and still in the terminal window, enter:

  gksudo gedit /boot/grub/menu.lst

then search for the stanza that looks something like:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash

edit the line "# defoptions=splash" to ad the word "quiet " (usually befor "splash").  Save the file and exit the editor which should return you to the terminal.  Now for the step that makes changes to menu.lst be effectual, enter:

  sudo update-grub

then the changes should take effect when grub runs on the next boot.

Hope this helps.

---

### Post by dwally89 on 2008-05-28
OK, I add quiet splash, did a reboot, and still got all the text.

Any other ideas?

---

### Post by dwally89 on 2008-05-28
> **Dazed_75 said:**
> Personally my preference is to keep seeing all those messages so if there is ever a problem starting up or shutting down, I have a real visual cue whether things are happening, failing, or are just stuck on some step.  Too bad you can't see this kind of info in windows when it has problems.

OTOH, some folks do not want to see it and linux gives you the choice and control.  While oldsolders fix might work, it lacks one step and is not a permanent fix.  The proper place to make the change is in a slightly different place in /boot/grub/menu.lst.  Before I show it to you I ask that you please make a copy of that file.  So in a terminal, do this:

  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

Once you have done that, and still in the terminal window, enter:

  gksudo gedit /boot/grub/menu.lst

then search for the stanza that looks something like:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash

edit the line "# defoptions=splash" to ad the word "quiet " (usually befor "splash").  Save the file and exit the editor which should return you to the terminal.  Now for the step that makes changes to menu.lst be effectual, enter:

  sudo update-grub

then the changes should take effect when grub runs on the next boot.

Hope this helps.

I dont have defoptions in my menu.lst file. What should I do?

---

### Post by leon.hh on 2008-05-28
Note: you posted this code:

```
title Ubuntu 8.04, kernel 2.6.24-17-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf
initrd /boot/initrd.img-2.6.24-17-generic
quiet
```

If this is correct, the options *ro quiet splash* at the end of root are missing. That would explain the problem, just edit the file and add these options.

Otherwise, if you change that line and the issue continues try to recompile your initram with the following code as root:

```
update-initramfs -u
update-grub
```

That should fix the startup problem but you probably will continue seeing text at shutdown, give it a try any way

---

### Post by dwally89 on 2008-05-28
> **leon.hh said:**
> Note: you posted this code:

```
title Ubuntu 8.04, kernel 2.6.24-17-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf
initrd /boot/initrd.img-2.6.24-17-generic
quiet
```

If this is correct, the options *ro quiet splash* at the end of root are missing. That would explain the problem, just edit the file and add these options.

Otherwise, if you change that line and the issue continues try to recompile your initram with the following code as root:

```
update-initramfs -u
update-grub
```

That should fix the startup problem but you probably will continue seeing text at shutdown, give it a try any way

Please could you give me an exact copy of the line I should copy and paste into my menu.lst file, as I don't want to mess it up by a mistake.

Thanks

---

### Post by Dazed_75 on 2008-05-28
Probably you could add it before your automagic kernals list section.  My worry is where you got a non standard menu.lst.  It certainly did not come from an ubuntu distribution.  So I would look for the standard one and consider using it and making whatever changes you wish.  Mine is customized, but I leave all the basics in place where possible.  Here it is for your reference.  Do note however, that not everyone will agree with the changes I chose.  I wanted you to see the normal file however, because you will see that it normally contained comments which would have helped you resolve this issue.

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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
# color cyan/blue white/blue

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
# kopt=root=UUID=9c750d7d-046e-48af-ac81-fddb660a8cf2 ro

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
# defoptions=splash

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
# howmany=4

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9c750d7d-046e-48af-ac81-fddb660a8cf2 ro splash
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9c750d7d-046e-48af-ac81-fddb660a8cf2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9c750d7d-046e-48af-ac81-fddb660a8cf2 ro splash
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9c750d7d-046e-48af-ac81-fddb660a8cf2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9c750d7d-046e-48af-ac81-fddb660a8cf2 ro splash
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9c750d7d-046e-48af-ac81-fddb660a8cf2 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=9c750d7d-046e-48af-ac81-fddb660a8cf2 ro splash
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault

title		Ubuntu 8.04, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=9c750d7d-046e-48af-ac81-fddb660a8cf2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by dwally89 on 2008-05-28
OK, I've updated my menu.lst file, and it now looks like this:

```
default 0
timeout 0
hiddenmenu

title Ubuntu 8.04, kernel 2.6.24-17-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf quiet splash
initrd /boot/initrd.img-2.6.24-17-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Dell Utility Partition
root (hd0,0)
chainloader +1
savedefault
makeactive

title Microsoft Windows XP Embedded
root (hd0,4)
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
# kopt=root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf ro

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
# defoptions=splash quiet

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf ro splash quiet
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

But I'm still getting text at shutdown and startup.

Anything else I could do?

---

### Post by Dazed_75 on 2008-05-28
If you look at your listing you should see that your menu entries occur BEFORE the sections with various options.  IOW, the options have no effect when the file is processed by grub because it see your menu entries BEFORE it sees the options.

Good luck fixing it as I have to go out now.  Hopefully this is enough to help you.

---

### Post by dwally89 on 2008-05-29
OK, I've had my menu.lst file regenerated.

It now looks like this:

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
timeout		0

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
# kopt=root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf ro

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a8dc08ef-300c-479c-b4e2-46bd3a8d07cf ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, memtest86+
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
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```

This is still showing text text when I boot and shut down.
How can I get rid of it?

Thanks

---

### Post by dwally89 on 2008-05-30
Anyone know what to do?

---

### Post by sisco311 on 2008-05-30
Please post the output from:
```
ls -al /usr/lib/usplash/usplash-artwork.so
ls -al /etc/alternatives/usplash-artwork.so
```

---

### Post by dwally89 on 2008-05-30
> **sisco311 said:**
> Please post the output from:
```
ls -al /usr/lib/usplash/usplash-artwork.so
ls -al /etc/alternatives/usplash-artwork.so
```


```
 ls -al /usr/lib/usplash/usplash-artwork.so
lrwxrwxrwx 1 root root 36 2008-05-29 15:27 /usr/lib/usplash/usplash-artwork.so -> /etc/alternatives/usplash-artwork.so

```

```
 ls -al /etc/alternatives/usplash-artwork.so
lrwxrwxrwx 1 root root 40 2008-05-29 15:27 /etc/alternatives/usplash-artwork.so -> /usr/lib/usplash/usplash-theme-ubuntu.so

```

---

### Post by sisco311 on 2008-05-30
Try to edit the /etc/usplash.conf file and set your screen resolution.
```
sudo gedit /etc/usplash.conf
```> xres=*1024*
yres=*768*
replace 1024 and 768 with your screen resolution.
```
sudo update-initramfs -u
```

---

### Post by dwally89 on 2008-05-30
It already had my resolution in that file (1280x800).

What to do next?

---

### Post by spiderbatdad on 2008-05-30
try this please:

```
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a8d ro **--quiet splash**
```With two dashes in front of quiet.

---

### Post by dwally89 on 2008-05-30
What do those two dashes do?

---

### Post by spiderbatdad on 2008-05-30
I'm sorry I do not know, but** it is the standard syntax for that option** in the kernel parameter.

---

### Post by dwally89 on 2008-05-30
OK I'll give it a go and see what happens.

---

### Post by spiderbatdad on 2008-05-30
you should also have this line...somewhere in the file:

```
# defoptions=quiet splash vga=792
```Just as show, with a hash at the beginning.

---

### Post by dwally89 on 2008-05-30
> **spiderbatdad said:**
> try this please:

```
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a8d ro **--quiet splash**
```With two dashes in front of quiet.

OK I tried that, but it just gave me some orange text below the progress meter at first, then even more white text against a black background than before.

---

### Post by dwally89 on 2008-05-30
> **spiderbatdad said:**
> you should also have this line...somewhere in the file:

```
# defoptions=quiet splash vga=792
```Just as show, with a hash at the beginning.

I have that line in my file, but I don't have the vga=792 bit.

What does that bit do?

Thanks

---

### Post by spiderbatdad on 2008-05-30
```
	640x480   800x600   1024x768   1280x1024   1600x1200
8bit	769	   771       773        775         777
15bit   784        787       790        793         796
16bit   785        788       791        794         797
24bit   786        789       792        795         798
```

---

### Post by dwally89 on 2008-05-30
Won't that just change the resolution of the display whilst booting?

---

### Post by spiderbatdad on 2008-05-30
I'm really not sure. If your native video drivers settings are determined during the boot, it is possible the kernel needs a hint. Sorry I can't be of much more help.
[http://blogs.techrepublic.com.com/geekend/?p=204](http://blogs.techrepublic.com.com/geekend/?p=204)

[http://womp.sourceforge.net/documentation/node11.html](http://womp.sourceforge.net/documentation/node11.html)

---

### Post by dwally89 on 2008-05-30
OK, Thanks for that, don't think that'll solve the problem.

Is there a log saved of all the text that appears at boot up?

---

### Post by spiderbatdad on 2008-05-30
```
dmesg > dmesg.txt
```will write a small text file in your home directory. It could be helpful as far a determining any hardware detection problems during the boot process. You can right click the file and select 'create an archive' and upload that archive here if you like, with the manage attachment tool below. But the fixes usually involve parameters to replace --quiet splash...that wouldn't resolve your original desire to have a non-verbose boot up.

---

### Post by dwally89 on 2008-05-30
OK, please find attached the specified file.

Thanks

---

### Post by spiderbatdad on 2008-05-30
looks pretty clean to me, I'm no expert. I have seen much worse.
You might want to try creating a profile of the process, which will speed it up a little...IDK if it will help with your original issue.

To create a profile: from the grub menu at startup. Press 'e' to edit the kernel parameters. Then use the arrow key to move to the line beginning with the word 'kernel.' Press 'e' again. Go to the end of the line. Add the word profile after --quiet splash. So it looks like 'ro --quiet splash profile.' Hit enter. Then press 'b' to boot. This boot will take a few seconds longer than usual while the profile is created.

---

### Post by dwally89 on 2008-05-30
> **spiderbatdad said:**
> looks pretty clean to me, I'm no expert. I have seen much worse.
You might want to try creating a profile of the process, which will speed it up a little...IDK if it will help with your original issue.

To create a profile: from the grub menu at startup. Press 'e' to edit the kernel parameters. Then use the arrow key to move to the line beginning with the word 'kernel.' Press 'e' again. Go to the end of the line. Add the word profile after --quiet splash. So it looks like 'ro --quiet splash profile.' Hit enter. Then press 'b' to boot. This boot will take a few seconds longer than usual while the profile is created.

OK, I did that, but what did that actually do?

Thanks

---

### Post by spiderbatdad on 2008-05-30
Should enable faster booting on subsequent boots...was hoping it might eliminate the verbose output you still have. Have you tried specifying any vga in the defoptions?

---

### Post by dwally89 on 2008-05-30
Would that profile have been effective from that boot up or do I need to do it again?

Thanks

---

### Post by spiderbatdad on 2008-05-30
the first time it creates the profile...so no, not from that boot up.

---

### Post by dwally89 on 2008-05-30
OK, I just restarted and no change.

Any other ideas?

Thanks

---

### Post by Gone fishing on 2008-05-30
Mmmm I've just developed this problem - it occurred after a kernel update.

If I boot to the old kernel its still a problem.

---

### Post by Gone fishing on 2008-05-30
Mmmm I've just developed this problem - it occurred after a kernel update.

If I boot to the old kernel its still a problem
.

---

### Post by dizee on 2008-05-30
I had a similar problem when I re-sized the swap partition. What was happening was the loading screen would appear for a few seconds at the start but once the OS started loading the text appeared.

Anyway long story short the answer was that the UUID code for the swap partition was wrong in the file /etc/fstab. Why this would affect graphical booting I don't know. But it did for me.

First find out the swap partition's UUID:
```
blkid
```
Make a note of the UUID given for the swap partition.

Check fstab to compare:
```
cat /etc/fstab
```

If the UUID for the swap partition entry is different, you'll need to edit fstab to fix it, replacing the UUID with the one you got with the blkid command.
```
sudo nano /etc/fstab
```

Then reboot and hopefully job done - nice Ubuntu loading bar restored. This might not be the same as your problem but hopefully it'll help some people. Worth a try anyway.

With thanks to analystscouch: [http://ubuntuforums.org/showpost.php?p=4714344&postcount=16](http://ubuntuforums.org/showpost.php?p=4714344&postcount=16)

---

### Post by dwally89 on 2008-05-31
> **dizee said:**
> I had a similar problem when I re-sized the swap partition. What was happening was the loading screen would appear for a few seconds at the start but once the OS started loading the text appeared.

Anyway long story short the answer was that the UUID code for the swap partition was wrong in the file /etc/fstab. Why this would affect graphical booting I don't know. But it did for me.

First find out the swap partition's UUID:
```
blkid
```
Make a note of the UUID given for the swap partition.

Check fstab to compare:
```
cat /etc/fstab
```

If the UUID for the swap partition entry is different, you'll need to edit fstab to fix it, replacing the UUID with the one you got with the blkid command.
```
sudo nano /etc/fstab
```

Then reboot and hopefully job done - nice Ubuntu loading bar restored. This might not be the same as your problem but hopefully it'll help some people. Worth a try anyway.

With thanks to analystscouch: [http://ubuntuforums.org/showpost.php?p=4714344&postcount=16](http://ubuntuforums.org/showpost.php?p=4714344&postcount=16)

I don't have a swap partition so that can't be the problem.

Anyone else got any ideas?

Thanks

---

### Post by Gone fishing on 2008-06-01
Thanks dwally89 I'm sure you've got the problem. I removed Mandriva from my system at the same time I updated and in retrospect thats probably what caused the problem. When I removed Mandriva I had to remake the swap partition and when I remade it I changed it and added it to fstab as:

/dev/sdb2 none           swap         sw                          0  0  

and I'm thats what caused the problem, anyway I've changed that to:

UUID=3727fb47-1ce8-426a-82fd-c5653870ec09  none           swap         sw                          0  0  

but I've still got the problem. :confused:

---

### Post by Gone fishing on 2008-06-01
OK fixed it:

It seems to be a bug when you change the swap file I found the fix here:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/206878](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/206878)

so thanks Mahesh Asolkar 

and the fix is:

> 1. Make sure you have the initramfs-tools update
2. sudo blkid
3. Check that swap line UUID from /etc/fstab matches swap UUID from step 2, if not change fstab.
4. Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step 2, if not change resume file.
5. sudo update-initramfs -u
6. Restart

---

### Post by dwally89 on 2008-06-01
OK, I decided to do a reinstall (leaving my home partition intact of course), and now there is now more text on booting :-)

I wonder what was causing the problem in the first place though...

---

### Post by OldTimeTech on 2008-06-01
dwally89...you should have a swap file...it is a needed part of unbuntu

---

### Post by dwally89 on 2008-06-01
> **OldTimeTech said:**
> dwally89...you should have a swap file...it is a needed part of unbuntu

I have 2GB of RAM.

---

### Post by OldTimeTech on 2008-06-01
Check this out....you are supposed to have a Swap no matter how much ram...I have 4gb and I have a 20 gb swap.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by dwally89 on 2008-06-01
When will you ever need 20GB of swap???

---

### Post by OldTimeTech on 2008-06-01
I won't, but I've got a large hard drive and so I decided to use that much...ya know gotta do something with all the room. ;)

---

### Post by dwally89 on 2008-06-01
Fine...

But still swap isn't needed with such a large amount of RAM.

---

### Post by philinux on 2008-06-01
If you have 2 gig mem you only need max 2 gig swap if you use suspend/hibernate etc.

The old rule was to have twice as much swap as ram. But that was for system with not much memory.

From the document on swap
> 

To begin with, let's say that computers have changed a lot since swap was first used :

    *

      At first, swap was needed to extend real memory capacity. You would use swap so that the available memory would be the addition of the ram space and the swap space.
    *

      Nowadays, ram are often big enough so that we could use the computer without any swap at all.

---

### Post by dwally89 on 2008-06-01
> **philinux said:**
> If you have 2 gig mem you only need max 2 gig swap if you use suspend/hibernate etc.

The old rule was to have twice as much swap as ram. But that was for system with not much memory.

Yeah, I heard about that, and since I never use suspend or hibernate I got rid of my swap partition, and my system runs fine :-)

---

### Post by OldTimeTech on 2008-06-01
Thank you philinux...I may have too much swap, but swap is still needed in Linux.

---

### Post by OldTimeTech on 2008-06-01
> **dwally89 said:**
> Yeah, I heard about that, and since I never use suspend or hibernate I got rid of my swap partition, and my system runs fine :-)

If you system ran fine you wouldn't be having all the text coming up at boot and shut down...maybe if you put a swap file in, it will go away!!!

---

### Post by philinux on 2008-06-01
> **OldTimeTech said:**
> Thank you philinux...I may have too much swap, but swap is still needed in Linux.

I've 2 gig ram and when I check system monitor swap has not been used once.

---

### Post by dwally89 on 2008-06-01
> **dwally89 said:**
> OK, I decided to do a reinstall (leaving my home partition intact of course), and now there is now more text on booting :-)

I wonder what was causing the problem in the first place though...

I have no text upon booting, and I have no swap, and my system runs fine, therefore no swap is needed.

---

### Post by OldTimeTech on 2008-06-01
Sorry...I wasn't paying enough attention to who asked for help.

Everyone is entitled to run their machine their way and if it works for you that is all that is important. :)

---

### Post by Barriehie on 2008-06-01
Try this; because I turned my boot/shutdown text ON so I could see what was happening.  Edit **/etc/default/rcS** and set **verbose=no**.  See **man rcS** for a description of the variable functions.

Barrie

---

### Post by dwally89 on 2008-06-01
> **dwally89 said:**
> OK, I decided to do a reinstall (leaving my home partition intact of course), and now there is now more text on booting :-)

I wonder what was causing the problem in the first place though....

---

### Post by the8thstar on 2008-06-01
Swap is not really necessary if you don't ever suspend or hibernate. With 2Gb of RAM, you're more than settled for the time being.

I ran a stress test for stability on my current config the other day with all the following apps running at the same time:

Compiz-Fusion Extra
Google-Earth 4.3
MS Word 2007 (Wine)
MS Excel 2007 (Wine)
MS Powerpoint 2007 (Wine)
OO Writer
OO Calc
OO Impress
Gimp

... and a few others, like baobab and gparted, just to ram the HDD a little bit more. I hardly reached 964Mb of RAM used, and NO swap. My system was rock solid and the CPU throttled at 25% on average. Who needs a Core Extreme, haha!

Actually, I have 4Gb of swap and I CAN'T hibernate anyway... it's a kernel issue though.

---

### Post by dwally89 on 2008-06-01
Was it hard to install Office 07 on Wine?

---

### Post by the8thstar on 2008-06-07
Sorry for the late post. I followed some tutorials on the forum. It was indeed difficult and I had several irritating failures before I found the tutorial that was right for my machine.

Four caveats I found:

1. You cannot update MS Office 2007 with SP1. It just won't install. I guess tweaking Wine could be an option but it's way beyond my competence

2. Double clicking a .doc file opens up Word 2007, but the document will not show on the display. You'll have to use the "Open" command instead. Other apps like Excel and Powerpoint don't have that problem.

3. The Ribbon is partially covered by the window... but there are workarounds that take care of that.

4. Full screen presentations in PowerPoint don't work. You need to install Powerpoint viewer or use OO.org Impress to display them correctly.

At this point in time, I have removed MS Office completely. There's no point in using it as OO takes care of things nicely enough. I still use it on my Vista partition of course.

---

