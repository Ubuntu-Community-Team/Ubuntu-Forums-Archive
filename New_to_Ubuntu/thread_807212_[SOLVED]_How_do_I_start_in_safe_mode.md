---
title: "[SOLVED] How do I start in safe mode?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Acadia on 2008-05-25
My display is all messed up when I go in the regular way, and I cannot see anything, so I tried recovery mode - but there is no safe mode option.  Is there something I can type in the command line?

---

### Post by bwhite82 on 2008-05-25
To at least get a working X11 session, you can temporarily change the display driver to "vesa" in your xorg.conf. So from the command prompt:

> sudo nano /etc/X11/xorg.conf

Under section "Device", change the driver to "vesa". Then hit CTRL+X, , then press 'Y', then press enter. Then issue the command startx.

---

### Post by Acadia on 2008-05-25
> **Soldierboy said:**
> To at least get a working X11 session, you can temporarily change the display driver to "vesa" in your xorg.conf. So from the command prompt:



Under section "Device", change the driver to "vesa". Then hit CTRL+X, , then press 'Y', then press enter. Then issue the command startx.

You so massively rule.  Thank you so very very much.  Honestly - thank you.

---

### Post by bwhite82 on 2008-05-25
Glad you got it sorted out. Please mark the thread as "solved".

-Cheers

---

