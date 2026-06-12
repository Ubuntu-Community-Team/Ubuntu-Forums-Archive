---
title: "Installer busted :s"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Sc4Rzz on 2008-06-07
Hi,
I'm quite new to ubuntu, but everything worked fine until today, the installer AND updater doesn't work anymore.. whenever I try do install something or update my system, I get the following error: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Okay, so I tried it in the terminal:

sc4rzz@desktopsc4rzz:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
sc4rzz@desktopsc4rzz:~$ 

What am I doing wrong?

---

### Post by rampageoberon on 2008-06-07
you want to run dpkg with root privilages. So either open a root terminal or use sudo.

You can do this by doing
```
sudo dpkg --configure -a
```

Hope that helps

edit: If its a root terminal then you don't need to use sudo.

Root terminal will look like this:
sc4rzz@desktopsc4rzz:~#

---

### Post by Hozza on 2008-06-07
I had the same problem about a week ago.

so i used the sudo method -- and it worked 8)

---

