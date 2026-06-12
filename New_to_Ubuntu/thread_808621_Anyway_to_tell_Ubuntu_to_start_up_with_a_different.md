---
title: "Anyway to tell Ubuntu to start up with a different kernel"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by LinuxFox on 2008-05-26
I posted a topic a while ago about how Ubuntu 8.04 kept starting into BusyBox after an update.  Well I tried pressing ESC at the "Press ESC to enter menu... (countdown)"  I pressed the ESC key and found two versions of Ubuntu 8.04 with kernels versions and Windows XP.  I can't remember the exact version (I looked and it was 2.6.24.16 and 2.6.24.17), but I remember one kernel ended in 16, the other 17.  When I chose 16 it started up into Ubuntu. :)  When I started up into 17, it went to BusyBox.

I hope this helps anyone out if they have the same problem. :)  Now for my question, is there anyway I can tell my computer to boot into the 16 kernel and not the 17 one?  Or do I just keep pressing ESC everytime I want to use Ubuntu.

---

### Post by Sarah L on 2008-05-26
Edit the GRUB boot menu and put the kernels in the order that you prefer.
Alternatively, you can set the default choice to the number of your kernel.

```
sudo gedit /boot/grub/menu.lst
```

After you've put everything in the right order, you can set the timeout to 0 so you won't have to bother with the boot menu again.

---

### Post by spiderbatdad on 2008-05-26
```
gksu gedit /boot/grub/menu.lst
```

Find this section:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default		0**

```
Change defualt  0 to match the entry from the debian kernels you want to boot. They begin counting at 0....so, 0, 1, 2, etc.
From this section:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID= ro lapic pci=routeirq
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID= ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID= ro lapic pci=routeirq
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
savedefault
```

Above, I show 0, 1, and 2, in that order.

Also edit this line:```
## should update-grub add savedefault to the default options
## can be true or false
**# savedefault=true**

## ## End Default Options ##

```
To be sure savedefault=true

---

### Post by LinuxFox on 2008-05-26
Thanks a million Sarah and spiderbatdad.  I edited what needed to be edited, and now it's starting into Ubuntu using version 2.6.24.16.  Everything is working fine. :D

---

