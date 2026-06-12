---
title: "Change GRUBB menu order?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by fedex1993 on 2008-05-21
okay i ahve been having issues with grubb where it auto chooses ubuntu which sometimes i dont want to get on is there anyway i can change the menu order and what not?

---

### Post by laffinet on 2008-05-21
I think what you want to do is change the default boot option. You do this by editing /boot/grub/menu.lst (that's a lowercase "L", not a "1").

In there you'll find a section that says

```
# By default, boot the first entry.
default 0
```

Change that to whatever entry you'd like to be the default.

---

### Post by djsroknrol on 2008-05-21
Remember when you are counting, "0" is the first line item option...it goes "0,1,2..."

Best of luck...

---

### Post by drs305 on 2008-05-21
If you have startup-manager installed, you change the default operating system, how many kernels are shown, and how long the menu is displayed by going System, Administration, Startup-Manager.

You can install it with:
```
sudo aptitude startupmanager
```

---

### Post by CloudFX on 2008-05-21
This is the best guide for editing GRUB:[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by radj2 on 2008-05-24
Thanks for info on start up manager, I triple boot on my machine and needed an easy way to change the booting os without keeping an eye on the boot loader

---

