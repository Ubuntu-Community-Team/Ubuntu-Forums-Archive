---
title: "Where is my menu.lst?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by baracuda68 on 2008-06-04
Hi.
In my /boot/grub I have a menu.lst file that is empty, and has no permissions. 
I also have a menu.lst.080531223827 which has permissions.This menu is not the list that I see at boot time.

Where else would the file be at that my machine boots from?

I have hidden files shown.
I believe this happened when I installed grub-splashimages...:confused:

---

### Post by bumanie on 2008-06-04
> cat boot/grub/menu.lst will show what the system is using as a boot reference.

---

### Post by Joeb454 on 2008-06-04
If the menu.lst.<numbers> is what your menu.lst used to be, you could just restore that :)

---

### Post by housam on 2008-06-04
Type in the terminal the following code :
```
gksu gedit /boot/grub/menu.lst
```
this will allow you to edit the menu.lst file.

---

