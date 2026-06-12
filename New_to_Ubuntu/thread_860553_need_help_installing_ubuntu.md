---
title: "need help installing ubuntu"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by edwin2105z on 2008-07-15
need help installing ubuntu. selected the lang. but after that it gives me this message:

BusyBox v1.1.3 (Debian 1:1.1.3-ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

can someone tell me what to put on there so i can continue the install.

---

### Post by benfindlay on 2008-07-15
Hmmm, never seen that before, try downloading the alternate cd and doing a text based install.

I've noticed that the live cd seems to give more problems than the alternate cd generally so tend to always go straight for the alternate cd myself.

Hope this helps!

---

### Post by cait on 2008-07-15
Mine did that at first - I couldn't run from the cd or install. It was some sort of hardware compatibility issue. After you choose the language, edit the boot options by hitting F6. Add ```
all_generic_ide
``` to the end of this. See if that fixes it. It got mine to work.

---

### Post by louieb on 2008-07-15
Busybox is the Debian lightweight shell. The install CD will display that when things go wrong.  
1st thing do you have a least 384MB memory?  If not post the type of computer, amount of memory, and processor.

2nd. choose the option **check media for defects **it just takes a few twisted bits to turn the CD into a coaster. I burn iso files at 2x rarely have a problem.

Thats the 2 most common reasons for the busybox shell to be displayed. Lack of memory and or a bad CD burn.

---

