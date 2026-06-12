---
title: "[SOLVED] GRUB won't work"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by P13808 on 2008-09-16
So I have GRUB, and then I get GRUB loaded after the BIOS does the self check.  I hit e to edit the line.  Then I go down to the quiet line and press e.  I change it to nosplash.  I hit enter.  It then syas all the lines, with nosplash at the bottom.

I hit b to boot.  The computer powers off.  Then it comes on and goes to GRUB.  I hit enter on the recently modified entry and It isn't changed.  

I restart and hit e on the choice this time.  I look.  My changes didn't stay.  Why?

---

### Post by ptn107 on 2008-09-16
To permanently apply those changes you must edit the /boot/grub/menu.lst file.

---

### Post by mikewhatever on 2008-09-16
It is supposed to work this way. The changes you make by pressing e are temporary. You need to edit the /boot/grub/menu.lst file to make it permanent.

---

### Post by P13808 on 2008-09-16
Okay.  That makes sense.

---

