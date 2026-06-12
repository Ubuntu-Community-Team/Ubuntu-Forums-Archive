---
title: "[SOLVED] Stop Asking Me To Upgrade!"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by RussW210 on 2008-11-07
I just upgraded from 8.04 to 8.10 Ubuntu.  When I did so, it installed the newest KDE4 version of k9copy.  The ripping of a DVD to a single .iso didn't work on that so I uninstalled it and reinstalled the previous version I had (1.2.3).

However, Update Manager keeps asking me to upgrade k9copy to the newest version.  Is there any way to stop the update manager from asking me to upgrade this one package?  I don't want to keep unchecking it every time there are other updates and if I forget to uncheck I don't want to have to keep reinstalling the older version.

Thanks for the help.

---

### Post by drs305 on 2008-11-07
Open synaptic, highlight the package, select Package, Lock Version. I believe that will stop the upgrade messages.

---

### Post by cdtech on 2008-11-07
> aptitude hold pkgname: hold will cause a package to be ignored by future safe-upgrade or full-upgrade commands

This is from the man page........

---

### Post by RussW210 on 2008-11-07
Thank you both.  That did the trick!  Sorry, I should have looked through the man page.

---

### Post by cdtech on 2008-11-07
No prob. This is a "man" page. lol

---

