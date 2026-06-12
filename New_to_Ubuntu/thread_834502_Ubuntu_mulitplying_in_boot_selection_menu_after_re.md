---
title: "Ubuntu mulitplying in boot selection menu after restart updates"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by kayzon on 2008-06-19
When Ubuntu has a system update and it requires a restart I will restart it and when the boot options to boot into ubuntu or windows comes up I will have another set of ubuntu to select. It's almost to 12 ubuntu selections that lead to the same thing, is there a way to edit the bootlog or whatever it's called to delete some of these out? they all lead to the same install.

Thank you for your time in advance

---

### Post by Nikitas350 on 2008-06-19
Probably the different entries are for the different kernels. If you want to delete them post here the menu.lst (run in terminal gedit /boot/grub/menu.lst) and I will tell you what changes should be made.

---

### Post by forestpixie on 2008-06-19
You can keep that many kernels if you want - but I would remove some of the older ones. You can search for linux-image in synaptic and do a complete removal that will also update your menu.lst.

---

### Post by Duck2006 on 2008-06-19
From the terminal type.

gksudo gedit /boot/grub/menu.lst

and place a # in frount of the line you don't want to show up on your grub menu. If you want to remove them from your system go to your Synaptic Package Manager and remove them from there.

---

### Post by Oldsoldier2003 on 2008-06-19
> **Nikitas350 said:**
> Probably the different entries are for the different kernels. If you want to delete them post here the menu.lst (run in terminal gedit /boot/grub/menu.lst) and I will tell you what changes should be made.

deleting them in menu list is only a partial solution. Its best to delete the oldest kernels using Synaptic Package Manager. Search for "linux-image" Then mark the older images for complete removal. This will remove each selected old kernel and its associated files. It will also update your grub menu automatically.

It is always a good idea to keep at least two working kernel version just in case something goes south with your current kernel.

---

### Post by Inxsible on 2008-06-19
I agree with forestpixie....12 kernels is a little too much.

I would probably keep the latest and 1 older version - just so that if the new kernel gives me problems i could log into the older one.

Go to synaptics to remove the older versions. It will automatically take care of updating the menu.lst file in the grub

---

### Post by Keith Hedger on 2008-06-19
```
gksudo gedit /boot/grub/menu.lst 
```
find an entry like```
 ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=4
```

and set how many kernels u want to see
and then do ```
 sudo update-grub
```

---

### Post by Darkade on 2008-06-19
> **Oldsoldier2003 said:**
> deleting them in menu list is only a partial solution. Its best to delete the oldest kernels using Synaptic Package Manager. Search for "linux-image"
Agree. editing grub menu just makes the previous kernels not to be displayed, but it does not uninstall them. You should uninstall them from synaptic. just keep the last two or three

---

### Post by kayzon on 2008-06-19
Thank you guys so much, removing the old images using synaptic package manager worked perfectly.

---

### Post by forestpixie on 2008-06-19
Great - can you mark the thread as solved please.

---

### Post by pieniaszek on 2008-06-27
I went into Synaptic Package Manager to reduce the number of versions, but it didn't work.

Here is my 'menu.lst'le		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=75d4b941-f7fc-4a73-b313-2774fa71923a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=75d4b941-f7fc-4a73-b313-2774fa71923a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=75d4b941-f7fc-4a73-b313-2774fa71923a ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet
Customizing your dual-boot setup
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=75d4b941-f7fc-4a73-b313-2774fa71923a ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=75d4b941-f7fc-4a73-b313-2774fa71923a ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=75d4b941-f7fc-4a73-b313-2774fa71923a ro single
initrd		/boot/initrd.img-2.6.24-17-generic
Customizing your dual-boot setup
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=75d4b941-f7fc-4a73-b313-2774fa71923a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generCustomizing your dual-boot setupic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=Customizing your dual-boot setup75d4b941-f7fc-4a73-b313-2774fa71923a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75d4b941-f7fc-4a73-b313-2774fa71923a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75d4b941-f7fc-4a73-b313-2774fa71923a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Duck2006 on 2008-06-27
> I went into Synaptic Package Manager to reduce the number of versions, but it didn't work.


Does it show that the kernels are uninstalled in your Synaptic Package Manager?
If so just edit your menu.lst and remove the lines from there.

---

