---
title: "[SOLVED] Screen resolution"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Willthebeeguy on 2008-11-05
HELP!  My wife goofed around with the screen resolution setting and set it so large I cannot change it because I can't access the "Apply" button on the Monitor Resolution settings window.

Can I change the resolution without this window?

THANKS!

---

### Post by bawilson2 on 2008-11-05
Might be a bit overkill but this should do it for you. 

[INDENT] sudo dpkg-reconfigure -phigh xserver-xorg[/INDENT]

---

### Post by bull205 on 2008-11-05
You can also hold down the alt button while clicking the mouse.  That should allow you to drag the window around anywhere you need to so that you can click the buttons you need to.

---

### Post by arochester on 2008-11-05
If your using 8.04 or 8.10 then don't boot into your normal kernel. Boot into Recovery. That has an option "Try to recover Xserver. Then continue with normal boot. This has often repaired resolution.

---

### Post by Willthebeeguy on 2008-11-05
Thanks!  The alt key was THE key!

---

### Post by jsf_pp on 2008-11-09
thanks for the info

---

### Post by CatKiller on 2008-11-09
Just as a quick note; Alt-A is _A_pply in that window. Starcraft sometime does this to me (leaves the monitor at 640x480). It's generally the case that Alt and the underlined letter will work as a keyboard shortcut.

---

### Post by Kellemora on 2008-11-09
Hi Cat

Nice old 16 track you have there!

TTUL
Gary

---

### Post by barney385 on 2008-11-09
> **arochester said:**
> If your using 8.04 or 8.10 then don't boot into your normal kernel. Boot into Recovery. That has an option "Try to recover Xserver. Then continue with normal boot. This has often repaired resolution.


Yep. This worked for me.

thanks

---

