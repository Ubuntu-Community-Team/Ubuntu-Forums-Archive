---
title: "Major FGLRX problem."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Mazza558 on 2008-04-27
I installed the ATi drivers through the restricted driver manager, and they worked fine for one reboot - now they don't function correctly. 

- When hovering over menu options, there's no background thing to show you're selecting them.

- Some of the 2D elements don't update - for example, the gnome bar stays as it is before it's not loaded properly, even though it has.

My specs are in my sig. I'm running Hardy.

---

### Post by Mazza558 on 2008-04-27
Well, after regenerating a new Xorg, I get a blank white screen. Great.

What's going on? I haven't touched the xorg.conf before now...

---

### Post by Mazza558 on 2008-04-27
It seems the white screen's only when I use Compiz. I can rotate the (white) cube, but do nothing else.

---

### Post by ripdisk on 2008-04-27
I have found with experience that compiz is the cause of a lot of problems. When it comes right down to it, other than give you some pretty effects, it doesn't do anything but take up ram and break stuff. I prefer metacity. 

Anyway, try reinstalling the driver by un-checking the box in the restricted drivers panel, rebooting, and reselecting it. I had the white screen problem as well, and this fixed it for me.

---

### Post by Mazza558 on 2008-04-27
Okay, I think I fixed it. For me, it was the fault of Fusion-icon for some reason. When compiz was started from fusion-icon, it would have the bug mentioned above. However, if I just have a "compiz --replace" at startup, all is well.

---

### Post by ripdisk on 2008-04-27
I see. Oh well, tried :P

---

