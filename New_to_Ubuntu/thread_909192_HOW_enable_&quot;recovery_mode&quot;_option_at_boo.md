---
title: "HOW: enable &quot;recovery mode&quot; option at boot?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by equanime on 2008-09-03
My ubuntu (hardy heron) boots from turning the computer "ON"/ or restart without giving me any options as to which boot mode I'd like to use.

How do I enable this option?

---

### Post by falcon61102 on 2008-09-03
When you restart, as soon as you see Stage 1.5 Loading, hit ESC and you should be able to go to the GRUB menu.  From there you can select the recovery mode.

If that doesn't work you can edit the menu.lst to give you more time at boot, but try that first.

---

### Post by Oldsoldier2003 on 2008-09-03
> **equanime said:**
> My ubuntu (hardy heron) boots from turning the computer "ON"/ or restart without giving me any options as to which boot mode I'd like to use.

How do I enable this option?

you will need to edit /boot/grub/menu.lst and change the timeout value to a nonzero value. 3 or 5 both seem to work well but if you want more time you can make it larger.

You must use sudo to edit the file:

```
sudo nano /boot/grub/menu.lst
``` or if you prefer the gui:

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by equanime on 2008-09-03
Thank you falcon61102,

I only had to press ESC a couple times for the boot menu to show!!!

---

### Post by falcon61102 on 2008-09-03
No problem.  If you go into your menu.lst like OldSoldier2003 suggests, then you can change the timing to give yourself a couple seconds or just try to stay quick in timing the ESC key.

---

