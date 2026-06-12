---
title: "an easy way to solve grub error 17"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by sharks on 2008-05-23
when the grub shows up listing the operating systems,press E.it will bring a screen with four options.select root(hd0,?).error 17 occurs when the root(hd0,?) does not match with the one in the menu.lst.
  Now edit the root(hd0,?) by pressing E and change it to root(hd0,x)
> x = output of find /boot/grub/stage1.
press enter and then B to boot.now u will logon.
  in terminal type > sudo gedit /boot/grub/menu.lst and replace root(hd0,?) with root(hd0,x).

Thats all . it'll work fine. I had this error and just solved it now.

> ## ## End Default Options ##

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

this is my new list.earlier i had (hd0,9)  in the place of (hd0,5).:)

---

### Post by meierfra. on 2008-05-23
One also needs to change

#groot (hd0,?)

to

#groot (hd0,x)

otherwise, all the changes will be undone after the next kernel update.


Also this will only work in  some of the case of  Grub error 17.  For more information on error 17 see

[Hermanzone Grub Error 19]("http://users.bigpond.net.au/hermanzone/p15.htm#17")

---

