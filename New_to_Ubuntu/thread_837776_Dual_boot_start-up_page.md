---
title: "Dual boot start-up page"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by SalsaShark on 2008-06-22
I've got an issue with my choose operating system page at start-up, namely that it has 3 listings of the same ubuntu OS, as well as 3 ubuntu recovery mode listings.  They all load the same OS from the same partition (ie, I don't have separate partitions the same OS running), so it's really only a matter of convenience, but I'd like to get rid of it.

---

### Post by omi291 on 2008-06-22
It's probably due to the kernel updates. Here's a thread about the same issue:

[http://ubuntuforums.org/showthread.php?t=832151](http://ubuntuforums.org/showthread.php?t=832151)

---

### Post by iaculallad on 2008-06-22
> **SalsaShark said:**
> I've got an issue with my choose operating system page at start-up, namely that it has 3 listings of the same ubuntu OS, as well as 3 ubuntu recovery mode listings.  They all load the same OS from the same partition (ie, I don't have separate partitions the same OS running), so it's really only a matter of convenience, but I'd like to get rid of it.

You could get rid of your OLD kernels in your GRUB menu list by editing the file /boot/grub/menu.lst file.

```
gksu /boot/grub/menu.lst
```

Try to comment (by placing # before the line of word)/delete your OLD kernel boot options and Remove the kernel files using your Synaptics Package Manager. (Search for linux-image)

---

### Post by SalsaShark on 2008-06-22
Beautiful, thank you very much.

---

### Post by AndyCee on 2008-06-22
Depending on your level of confidence, after backing up grub you can:

1) edit grub and just remove the older kernel versions
sudo gedit /boot/grub/menu.lst

or

2) Download "start-up-manager" which mucks around with grub using a gui. While this is a friendlier option, if you have an unusual screen resolution it might kill your spash screen upon boot. 

to back up grub:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bckup

It has been suggested to keep an older kernel version in case a new one has a problem.

Whoops, just missed

---

