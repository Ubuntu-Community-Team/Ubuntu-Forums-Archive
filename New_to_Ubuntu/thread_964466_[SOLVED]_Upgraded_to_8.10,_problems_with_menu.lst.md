---
title: "[SOLVED] Upgraded to 8.10, problems with menu.lst"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Eto_Demerzel on 2008-10-30
I just upgraded to Ubuntu 8.10 from 8.04 LTS by net. Just before the final restart, I got a message asking what to do with the menu.lst file. I chose Keep current. On restart, I didn't get 8.10 as an option in my OS menu, only 8.04.

My menu.lst file is:

> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=344347ab-37e0-4b42-9362-d11a047da5fe ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=344347ab-37e0-4b42-9362-d11a047da5fe ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=344347ab-37e0-4b42-9362-d11a047da5fe ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=344347ab-37e0-4b42-9362-d11a047da5fe ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows XP Home Edition
root		(hd0,1)
makeactive
chainloader	+1

How do I boot into Ibex? 

Thanks.

---

### Post by sayems on 2008-10-30
How did you upgraded Ubuntu 8.10?

---

### Post by ad_267 on 2008-10-30
You should be able to remove all the 8.04s and add one entry for 8.10. For the memtest you can just change 8.04.1 to 8.10.

```

title       Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=344347ab-37e0-4b42-9362-d11a047da5fe ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title       Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=344347ab-37e0-4b42-9362-d11a047da5fe ro single
initrd /boot/initrd.img-2.6.27-7-generic

```

---

### Post by kansasnoob on 2008-10-30
Post the output of:

```
 sudo fdisk -l
```

And also:

```
uname -a 
```

---

### Post by Eto_Demerzel on 2008-10-30
Thanks you guys, I figured it out myself. 

I changed the it to 2.6.27-7 in the menu.lst file and restarted.

Then lsb_release -a gave me:
> 
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

Yay! I'm on Interpid Ibex!

---

### Post by kansasnoob on 2008-10-30
Maybe just:

```
sudo update-grub
```

But I'd rather see what I'm dealing with first!

---

