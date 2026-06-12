---
title: "Remove grub menu"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by pteri498 on 2008-08-16
I would like to set up grub so that none of the program ever displays itself.

I set the timeout to zero, but it still shows the "GRUB Stage 1.5" notification.

I would like it so that anyone starting the computer up would have no notification whatsoever that GRUB exists. Can this be done?

Thanks.

---

### Post by lisati on 2008-08-16
I don't know about eliminating the grub messages completely, but in your menu.lst file there should be an entry which looks something like this:
```
#hiddenmenu
```

Uncommenting it (by removing the "#") will prevent the display of the menu choices. You will still have a chance to press "Esc": it might be a good idea to keep this just in case you run into trouble after an update and need to revert to an earlier configuration to get things working again.

---

### Post by DGortze380 on 2008-08-16
> **lisati said:**
> I don't know about eliminating the grub messages completely, but in your menu.lst file there should be an entry which looks something like this:
```
#hiddenmenu
```

Uncommenting it (by removing the "#") will prevent the display of the menu choices. You will still have a chance to press "Esc": it might be a good idea to keep this just in case you run into trouble after an update and need to revert to an earlier configuration to get things working again.

x2 , you're really going to want to leave some way to access grub in case you need to boot a different kernel or run a memtest.

---

### Post by dje on 2008-08-16
afaik you cannot get rid of those lines, as far as you can go is hide the menu as posted above and setting the timeout to zero. besides it would be a bad idea even if you could because at some point you will need to get to the grub menu. personally i have a hidden menu and a timeout of zero

dje

---

### Post by pteri498 on 2008-08-16
True, I just remember reading in the past that there might be a way to dual-boot an XP and Ubuntu system where, if a layman was unaware of Ubuntu's existence and XP was the default boot option, there would be almost no way to tell that there was anything else on the machine except XP.

Only the ones who knew of Ubuntu would know exactly when to hit escape.

---

