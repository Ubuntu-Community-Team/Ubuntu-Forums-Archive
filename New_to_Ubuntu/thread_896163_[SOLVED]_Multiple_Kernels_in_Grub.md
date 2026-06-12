---
title: "[SOLVED] Multiple Kernels in Grub"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Anjruu on 2008-08-20
Hi! I'm running a dual-boot with Ubuntu 8.04 and Windows XP. When I boot, there are a bunch of different kernels I can choose from, but I always just pick the default, and I don't think I need the others. They don't take up too much space, so I could always just leave them, or modify my menu.lst file so that the other ones are not displayed, but I'd prefer a better solution. Can I go to my just go to my boot directory, manually remove the kernels that I don't need, and then edit my grub menu accordingly? The idea of manually deleting something from my boot directory sends small spasms of terror up and down my entire body.

Here's what (part of) my menu file looks like:
[I]
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.1, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=455a9a83-f4f7-4409-a199-b1416b6780a0 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 8.04.1, memtest86+
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
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1[/I]

---

### Post by iaculallad on 2008-08-20
Use the Synaptics Package Manager to safely delete those OLD kernels. Search for "linux-image" (w/o) quote and delete them permanently (Right-click on the kernel you want to delete and mark it as "Mark for complete Removal"). Do the same process with other remaining OLD kernels. When finished marking for removal, click on Apply and the process will automatically update your GRUB menu list.

---

### Post by yabbadabbadont on 2008-08-20
Edit: Too slow.

---

### Post by eriqjaffe on 2008-08-20
Or, for safety, just...

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```

...and then just comment out the irrelevant kernel lines by adding a # in front of the line.

---

### Post by mcduck on 2008-08-21
> **eriqjaffe said:**
> Or, for safety, just...

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```

...and then just comment out the irrelevant kernel lines by adding a # in front of the line.

This way you won't gain back the wasted disk space, and still loose the (possible) benefits of having old kernel versiosn available, as booting them without menu entry isn't that easy of a task.

If you really want that, the better solution would be to configure the setting about how many kernels should be displayed, the option is in the menu.lst files default options-section. This way you wouldn't have to do that again and again as new kernels get installed.

But I really recommend uninstalling the old kernels instead of just hiding them. Both ways are just as easy, and take about the same time, but uninstalling has more benefits. ;)

---

### Post by Anjruu on 2008-08-21
Thank you very much, that seems to have worked!

---

