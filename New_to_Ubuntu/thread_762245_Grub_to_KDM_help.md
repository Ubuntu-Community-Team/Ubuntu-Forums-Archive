---
title: "Grub to KDM help"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by garrowolf on 2008-04-21
I want to be able to pass arguments from the Grub to KDM so that I can have all my different desktop types listed in my grub and only have one place to make a selection instead of two.

---

### Post by Rocket2DMn on 2008-04-21
As far as I know, this is not possible without just doing separate linux installs and having each of them default to a different desktop environment.
I think GRUB can only do boot options for the kernel and a few other options.  However, you don't need to reboot in order to get to a different desktop environment, you just need to log out, then choose the new session you want to use, then log back in.

---

### Post by garrowolf on 2008-04-22
so you can't start a script from Grub?

---

### Post by Rocket2DMn on 2008-04-22
To my knowledge, no.  You can set scripts to run at boot time, but that is a little different than what you want.  Let me seek some advice on this.

---

### Post by SOULRiDER on 2008-04-22
AFAIK, you can't do that. It would be interesting to see if someone cna come up with a solution though.

---

### Post by vkbidve on 2011-08-05
No, you can't do so. Grub can pass arguments (options - bootargs) to linux KERNEL but not to the desktop environment. To do so, as Rocket2DMn suggested, you just need to log-off and log back in in desired desktop environment. Alternatively, you can set KDE as your default DE and each time you will get KDM login screen.

---

