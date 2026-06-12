---
title: "Graphical login fails for admin user... (Lubuntu)"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by Wutzl on 2013-06-24
Hi,

I just installed Lubuntu on my netbook. Now I can't use the graphical login anymore - after I enter my password, the screen flickers as if LXDE was starting, but then I get dropped back to the login screen without any error message.

Where would I go looking to find out what went wrong? There must be some place where errors that cause this are reported, right?

---

### Post by newb85 on 2013-06-24
Was this a fresh install, or did you add LXDE to Ubuntu or something? 

Did you by any chance do a password reset with an encrypted home directory?

---

### Post by MidnightGrey on 2013-06-24
Sounds like you may have a corrupt Xauthority file.
Can you log in as guest or any other user without any problems?

---

### Post by Wutzl on 2013-06-25
Thanks guys, noticed that the Xauthority file had the wrong ownership. I copied the home folder from an old install and must have messed up with the chown command somehow.
Thanks for your help!

---

