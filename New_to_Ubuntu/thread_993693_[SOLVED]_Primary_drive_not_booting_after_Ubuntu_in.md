---
title: "[SOLVED] Primary drive not booting after Ubuntu install on secondary drive"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by pastacat on 2008-11-26
I installed Ubuntu on my secondary hard drive today. Both of my hard drives have Windows XP on them, and I did not disconnect my primary hard drive for the installation. I did not install Ubuntu on my primary hard drive.

While I can select Windows from Ubuntu's boot menu, only the copy of Windows on my secondary hard drive will boot. I checked, and everything is still there on my primary hard drive. However, I do not know how to boot from this primary drive (C drive).

After some research, it seems that I should have disconnected my C drive for the duration of the Ubuntu installation. Now that the damage has been done, is there anything that I can do to be able to boot my regular Windows installation from the boot menu? Thank you for your time.

---

### Post by nakama85 on 2008-11-26
You could try Going into your bios and changing the boot sequence of your hard drives.

Just a guess

---

### Post by nakama85 on 2008-11-26
> **nakama85 said:**
> You could try Going into your bios and changing the boot sequence of your hard drives.

Just a guess

If that does not work I will try to find some grub info to help you point Grub to another drive

---

### Post by nakama85 on 2008-11-26
What you will probalably need to do is to edit your grub menu list and add the location of the other OS install and name it.

```
 sudo gedit /boot/grub/menu.lst
```

This is an example of a standard entry.
> # examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro


For windows you really only need to have the title and the root

---

### Post by pastacat on 2008-11-26
Thank you very much- your solution worked.

My 100% Windows C drive turned out to be (hd0,0), and the rest was simply a copy of the Windows section of your example and a name change under "title".

---

### Post by nakama85 on 2008-11-26
> **pastacat said:**
> Thank you very much- your solution worked.

My 100% Windows C drive turned out to be (hd0,0), and the rest was simply a copy of the Windows section of your example and a name change under "title".

Great\\:D/ glad to help

---

