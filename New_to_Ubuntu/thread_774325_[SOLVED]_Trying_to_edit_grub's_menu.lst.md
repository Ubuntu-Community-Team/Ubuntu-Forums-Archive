---
title: "[SOLVED] Trying to edit grub's menu.lst"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by vale1286 on 2008-04-29
Hi to all, i'm a new ubuntu user, version 7.10

I was trying to edit grub's menu.lst but ubuntu says that i have not the rights to edit the file. Now, i'm the only user/administrator for my pc, how could i access that file?

And also, before i try it, do you think that this file is gonna work?

```
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Linux     --> Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0c896e8f-d308-4d4f-b232-638341c8c93f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0c896e8f-d308-4d4f-b232-638341c8c93f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
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

```


Edit: it says that only the root member can edit that file. What should I do?

---

### Post by eriqjaffe on 2008-04-29
For security reasons that should be pretty obvious, you need to be root to edit menu.lst

In a terminal:

```
sudo gedit /boot/grub/menu.lst
```

...or whatever editor you prefer instead of gedit.

edit:  Before you monkey around with that file, you should make sure you have a backup of it.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

That way, if you break it, you can recover relatively painlessly, as a messed up menu.lst file can make it a bit difficult to boot.  ;)

---

### Post by Perpetual on 2008-04-29
Open a terminal and

```
sudo gedit /boot/grub/menu.lst
```

Then when prompted, enter your users password.

I would suggest you make a copy of your menu.lst prior to messing around with it.  Just in case...

Edit: too slow :)

Edit 2: I see now you weren't inquiring about sources.list at all!  My mistake - corrected.

---

### Post by Ek0nomik on 2008-04-29
> **Perpetual said:**
> 
I would suggest you make a copy of your sources.list prior to messing around with it.

He wanted to edit menu.lst, not sources.  :)

Backup copy can be done by doing:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

---

### Post by forestpixie on 2008-04-29
We can't tell whether it will work without knowing you're partition setup - also why do you have a win install amongst the linux installs.

You can use fdisk -l to find out partition information

```
sudo fdisk -l
```

---

### Post by Yudraciell on 2008-04-29
im not sure if this might help too

sudo chmod 755 /boot/grub/menu.lst

the "chmod" changed the permission list for the file or folder

---

### Post by forrestcupp on 2008-04-29
> **Yudraciell said:**
> im not sure if this might help too

sudo chmod 755 /boot/grub/menu.lst

the "chmod" changed the permission list for the file or folder

No.  Don't do that.  This file requires super user privileges because if you screw it up, you're screwed.  It's best to keep the permissions how they are with system files like this.

---

### Post by vale1286 on 2008-04-29
Thank you all, it works perfectly now. :)

---

### Post by Yudraciell on 2008-06-25
> **vale1286 said:**
> Thank you all, it works perfectly now. :)

Can you do the admins a favor and mark this thread as solved :guitar:

---

### Post by mcduck on 2008-06-25
One thing you shoud really change is where you put the Windows entry. It's now inside the "automagick kernel list" area, which is rewritten during kernel updates..

This means that when the next kernel update happens your Windows entry will disappear completely.

Move it above the "automagick" area and everything will be fine.

---

