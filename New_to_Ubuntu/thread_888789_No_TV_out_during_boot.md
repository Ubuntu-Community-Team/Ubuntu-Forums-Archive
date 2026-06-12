---
title: "No TV out during boot"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by bodah197 on 2008-08-13
I am using a LA-FX20-H GeForce FX 5200 128MB AGP card.
I do not get any TV out during boot up.  I used to get the motherboard's boot screen, and the boot messages, now I get nothing.  Not until everything boots does the TV out work.

I tried searching, but the closest thing I could find was the opposite where people needed to edit their xorg.conf file for the TV.  I have already done this.  The issue is before xorg loads.

Any suggestions?

---

### Post by bodah197 on 2008-08-15
Anybody have an idea?

---

### Post by cariboo on 2008-08-15
I think usplash is blocking output to your television during boot, If everything works properly once everything is loaded, it seems to be working correctly. If you want to see all the output during boot up, you could change the quiet splash opton in /boot/grub/menu.lst to nosplash.

Jim

---

