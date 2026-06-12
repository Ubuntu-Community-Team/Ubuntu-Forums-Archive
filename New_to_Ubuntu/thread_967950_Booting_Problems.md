---
title: "Booting Problems"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Warpster Buntu on 2008-11-02
I got Ibex working fine, and then rebooted because of some updates made. But now, everytime it tries to load, it gets hanged in the same spot.

This happened to me with Hardy Heron as well... any ideas what this could be? It gets hanged up in recovery mode as well.

---

### Post by taurus on 2008-11-02
Do you know what "spot" does it get hung up?

---

### Post by rhcm123 on 2008-11-02
If you want to, you could, in grub, when it says "press ESC to enter the menu" press esc, then select your kernel (the top one) then hit u or c or whatever it is to modify commands, and i belive you change 'quiet' to 'loud', which, instead of giving you the nice graphic boot, it gives you a text-based boot. This should help us see the problem easier.

---

### Post by Warpster Buntu on 2008-11-02
It is neither u or c that makes it load in text format...

Would running it in recovery mode show where?

---

### Post by taurus on 2008-11-02
Highlight the kernel that you want to boot and press e for editing.  Then, remove the last two options, quiet splash, at the end so you would see all the stuff running/starting on the screen.  Don't worry, you didn't actually modify anything in /boot/grub/menu.lst at this point, only for this session.

---

### Post by Warpster Buntu on 2008-11-02
Alright, it says [      0.776261]Kernel panic - not syncing VFS: Unable to mount roof fs on unknown-block(0,0)

---

