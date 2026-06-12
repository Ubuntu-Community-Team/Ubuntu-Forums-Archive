---
title: "when I tried to install GFX Grub, I faced problems with one command :("
date: 2008-04-24
forum: New to Ubuntu
---

### Post by legolas_w on 2008-04-24
Hi
Thank you for reading my post
I was trying to install GFX grub based on 
[http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/](http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/)
 and everything was going ok until i was trying to perform
```

sudo grub
find /boot/grub/stage1

```

It looks like that sudo grub does not works in my ubuntu installation :(

Can some one please let me know what should I do?

will I be able to restart my computer without facing boot problem?

here is the content of menu.lst that I have now:

```

## ## End Default Options ##
gfxmenu /boot/grub/message.ububrown

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=df9e01b9-f029-43a1-92a7-e0dde840c15b ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=df9e01b9-f029-43a1-92a7-e0dde840c15b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```


Can you please let me know how I should continue with other steps?

Thanks.

---

### Post by legolas_w on 2008-04-24
Any one?
Please let me know the solution, I wont be able to boot if I restart for any reason :-(

Thanks.

---

### Post by swoll1980 on 2008-04-24
do you have a menu.list file under /boot/grub?

---

### Post by poopboypat on 2008-12-14
I have the same exact problem.  Anyone have any Ideas?

---

### Post by 16@r on 2009-01-18
I think you will find your answer on this blog:
[http://technoemperor.blogspot.com/2008/10/installing-gfx-grub-in-ubuntu-grub.html](http://technoemperor.blogspot.com/2008/10/installing-gfx-grub-in-ubuntu-grub.html)
> Unfortunately doesn't work with Intrepid because Intrepid formats its ext3 partitions to use the newer 256 byte inode size file system standard, rather than previous versions of Ubuntu that used a 128 byte inode size.

---

