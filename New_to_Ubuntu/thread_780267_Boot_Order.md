---
title: "Boot Order"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by kevb8ll on 2008-05-03
As my family use my PC, I want XP to be the default OS.

How do I change the order?

I am using the 8.04

---

### Post by aheckler on 2008-05-03
You need to edit /boot/grub/menu.lst. See here: [http://makingtheswitch.wordpress.com/2007/04/29/changing-grub-boot-order-to-boot-windows-xp-before-ubuntu/](http://makingtheswitch.wordpress.com/2007/04/29/changing-grub-boot-order-to-boot-windows-xp-before-ubuntu/)

---

### Post by kirios on 2008-05-03
Press Alt and F2 keys, then type this into the dialog box that appears: 

```
kdesu kwrite /boot/grub/menu.lst
``` 

Post the contents of the menu.lst file here.

---

### Post by ChompTheMan on 2008-05-03
If you don't like messing with /boot/grub/menu.lst, you can install qgrubeditor.  It's as easy as highlighting the Windows entry and clicking on the up arrow.

---

### Post by alzie on 2008-05-03
There is also startupmanager in the repositories.  It will let you specify the default OS.

---

### Post by Sef on 2008-05-03
> Press Alt and F2 keys, then type this into the dialog box that appears:

Code:

kdesu kwrite /boot/grub/menu.lst



If you are using Ubuntu, the code would be

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by kevb8ll on 2008-05-06
Right - I'm close to banging my head against a wall here, (not at the advice given though!)

I found startup manager, and installed it using add remove programs.

Can I find it anywhere to run it? Can I heck.

I'm really sorry, but I'm new to this - I really want to get my head round things and would appreciate some help.

I am running kubuntu 8.04 with KDE4.0

Pleeeeease can someone help me. :(

---

### Post by kirios on 2008-05-07
I've never used startup manager. I would assume that it either places an entry in System > Administration or else requires you to start it from the command line. 

Editing the menu.lst file is easy enough that one doesn't need to look for an alternative method. To change the boot order, you just change the default value listed near the top of the file. It would be easier to explain if you could post the contents of menu.lst here. Just navigate to Places > Computer > Filesystem > boot > grub, double-click on the menu.lst file, then copy-and-paste the contents into your next post. 

> **kevb8ll said:**
> Pleeeeease can someone help me. :(

---

### Post by kevb8ll on 2008-05-07
Yep I had to start it from a konsole. This subject spilt onto another thread. Anyway I'm sorted now thanks.

---

