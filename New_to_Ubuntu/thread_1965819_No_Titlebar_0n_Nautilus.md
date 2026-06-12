---
title: "No Titlebar 0n Nautilus"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Resiler on 2012-04-26
I have ubuntu 11.4, the titlebar on all windows has gone. I cannot drag windows around and have to use force quit to shut them down.
Grrrr.... Can anyone let me know how to get them back?

---

### Post by ptn107 on 2012-04-26
Make sure you have these installed:

compiz
compiz-core
compiz-gnome
compiz-plugins-default
compiz-plugins-main-default
compizconfig-backend-gconf
libcompizconfig0
metacity
metacity-common
libmetacity-private0

Restart and check.

---

### Post by Resiler on 2012-04-26
I have all these installed but still no titlebar, Any ideas?

---

### Post by ptn107 on 2012-04-26
Just to try something...

Go to System Settings -> User Accounts and add a new account.  Give it just a made up name and password.  Then go to the login screen and login as this user.  Do you still have a problem with the titlebars? (You can login as yourself and delete that temp account when you're done.)

---

