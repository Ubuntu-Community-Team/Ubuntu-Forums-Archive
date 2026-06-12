---
title: "Repair apparmor (mysql issue)"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by stuartsiegler on 2008-06-02
While attempting to re-install mysql-server-5.0, i've backed myself into an apparmor issue, where apparmor cannot load <abstractions/mysql>:

/etc/init.d/apparmor reload
Reloading AppArmor profiles Error: #include <abstractions/mysql> not found at line 9 in /etc/apparmor.d/usr.sbin.mysqld.
 Profile /etc/apparmor.d/usr.sbin.mysqld failed to load

(this cascading problem started because I could not log into the msqladmin.  apt-get remove does not remove everything and the reinstall was failing).


Where do I start with this?

Thanks!

---

### Post by stuartsiegler on 2008-06-02
Nevermind.  I just app-get removed apparmor.

---

