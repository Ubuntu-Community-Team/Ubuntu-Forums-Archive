---
title: "Crashed Ubuntu"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by nebu on 2012-05-13
Hi,
I am using Ubuntu 12.04 and then I tried to get all fancy by trying to install evilwm.
And I deleted the .xinitrc file from my home directory.

Now when I put in the password in the login screen, it comes back right there. How do I fix this.

Cheers,
Nebu

---

### Post by Carborundum on 2012-05-13
> **nebu said:**
> I deleted the .xinitrc file from my home directory.

Why would you do that? :)

You can login via tty1 by pressing crtl+alt+f1. There, you need to either restore the .xinitrc you deleted, or create a new one containing this line:
```
exec evilwm
```To get back to a normal session, press ctrl+alt+f7.

Edit: on second thought, unless you have uninstalled Unity, you should be able to choose it from the login screen and login that way. Then you can restore/recreate your .xinitrc from a graphical session, if you would prefer that.

---

