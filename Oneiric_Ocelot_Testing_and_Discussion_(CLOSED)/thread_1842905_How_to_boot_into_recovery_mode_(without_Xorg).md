---
title: "How to boot into recovery mode (without Xorg)"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by clivejo on 2011-09-12
I used to be able to select recovery mode in GRUB, then drop into a root session.  However, every time I "init 3" it drops me into a graphical log on screen.

How do I get a non-graphical session to update my Nvidia drivers?

---

### Post by effenberg0x0 on 2011-09-12
During the PC Boot, if you hold the shift key (to see grub2 options), you should have the recovery there.
Inside a X session, you can also use sudo service lightdm stop and that should take you back to console.

Regards,
Effenberg

---

### Post by clivejo on 2011-09-12
Thanks, got it sorted!

---

### Post by sisco311 on 2011-09-12
Cool! Don't forget to mark this as [SOLVED]. Thanks!

---

