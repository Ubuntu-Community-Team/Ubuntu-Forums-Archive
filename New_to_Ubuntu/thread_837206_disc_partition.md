---
title: "disc partition"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by 1963 on 2008-06-22
Hi all, 
yesterday, I divided my hard disk in order to have two operating systems on one PC(vista for my sister:sad:, ubuntu for me.:)). Although there are two operating systems, when I start up the computer, five options appear on the screen which are ubuntu 8.04, ubuntu 8.04(recovery mode), again ubuntu 8.04, dell partition(3 mb), windows vista.
Question is this: What should I do in order to reduce their numbers and see only two options.

p.s: I searched the forum but I could not find any thread about this issue. If there was some and I did not realize it, I am sorry.

---

### Post by sayakb on 2008-06-22
Open a terminal and type in:
```
gksudo gedit /boot/grub/menu.lst
```
And comment out (put a # at the beginning) of the unneeded lines.
Though, it is recommended that you do not remove the recovery mode option, since it may be a lifesaver whenever you break your system.
You may upload your menu.lst as attachment and we can do it for you.

---

### Post by sharks on 2008-06-22
type in the terminal: sudo gedit /boot/grub/menu.lst and it will be like this at a place.

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=6616a161-48fd-4fe9-a826-307b080e9775 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=6616a161-48fd-4fe9-a826-307b080e9775 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6616a161-48fd-4fe9-a826-307b080e9775 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6616a161-48fd-4fe9-a826-307b080e9775 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

Then change the things that u dont want and save it. Dont Forget to backup the file.

---

