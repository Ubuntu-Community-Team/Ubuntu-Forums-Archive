---
title: "Problems booting into XP"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by HellKing on 2008-09-25
Dear Friends,
I had Vista, Ubuntu and XP on a triple boot and all was working fine till I decided to format Vista, I formatted it with GParted and created a empty drive.

Problem 1 : I cannout mount this empty drive even if I try with root priveledges, it just says permission denied. If I do a 'gksudo nautilus' and try to change file permission(of /dev/sda1 or /media/sda1), I am not able to do so...

Anyway this is not the major problem

I downloaded the QGRUBEditor and deleted Vista's name from the list. I changed the default boot to XP and moved it to the top of the list. Then I added a splash screen.

When I restarted, it sayd it could not access the splash screen, then when I tried to go into XP, it just got hung up on 'Starting Up' and nothing else happened.

What Can I do to solve these problems??

here's my menu.lst file :
[I]
default saved
fallback 1
timeout 5

title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd1,5)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=5d84ac94-4db5-48a9-80d8-f1abe4ba8e4c ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root (hd1,5)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=5d84ac94-4db5-48a9-80d8-f1abe4ba8e4c ro single
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd1,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=5d84ac94-4db5-48a9-80d8-f1abe4ba8e4c ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd1,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=5d84ac94-4db5-48a9-80d8-f1abe4ba8e4c ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd1,5)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd1,0)
chainloader +1
savedefault
makeactiv[/I]

---

### Post by angel2121 on 2008-09-25
same problem for me until I remapped the partitions to 25gb xp default, 80gb vista 80gb shared partition remainder to ubuntu, shared partition appeared  in both xp/vista as secondary (E: drive) and seemed to work fine in that order, splash screen however I have no clue :( sorry. 
I used gparted as well, you could use a virtual machine within ubuntu to run xp/vista programs but that doesn't help much with music files.

---

### Post by appropri8 on 2008-09-25
Yeah, i can hardly ever get the splash screen to work in grub either, so i just leave it(it looks a bit naff anyway).

Try restoring the original Menu.lst file.

Try deleting the partition that vista was on, then formating it.

---

### Post by tangibleorange on 2008-09-25
the very last line might be causing a problem. it currently says 'makeactiv' - it should read 'makeactive'. try changing that, save, then restart and try to boot windows.

---

### Post by caljohnsmith on 2008-09-25
I personally wouldn't mess with a Grub splash screen myself, but as far as booting Windows XP, you need to use Grub's mapping feature if your Windows is on another drive; it looks like this is true for you since your Windows entry uses (hd1,0). Try the following and see if it works:
```
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
If that doesn't work, then post the output of:
```
sudo fdisk -lu
```
And we can work from there. Otherwise, let us know how it goes.

---

### Post by HellKing on 2008-09-26
Thankx a lot mates!! Got XP working!
I just reloaded the backup and saw what was the difference, and yes, I need to use the mapping feature...

so now what about auto mounting that partition??

---

### Post by tangibleorange on 2008-09-26
to automount a partition, you need to add an entry to your /etc/fstab file. make a folder to mount the partition and then open it up for editing:

```

sudo mkdir /media/WindowsMount
gksu gedit /etc/fstab
```

then add this line:
```

/dev/sdb1 /media/WindowsMount ntfs 0 0
```

assuming /dev/sdb1 is your windows partition. then, reboot. your windows partition should be mounted

---

