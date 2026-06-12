---
title: "Booting Problems"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Warpster Buntu on 2008-11-02
I got Ibex working fine, and then rebooted because of some updates made. But now, everytime it tries to load, it gets hanged in the same spot.

This happened to me with Hardy Heron as well... any ideas what this could be? It gets hanged up in recovery mode as well.

---

### Post by gorgon on 2008-11-02
if you are using GRUB bootloader, press 'e' before it boots ubuntu, then choose the line which says 'kernel' at the beginning and press 'e' again. add '-verbose' at the end of that line, press enter and then 'b'.

this will show at what point it gets stuck - tell us what the text says when it stops in the boot process.

grgn

---

