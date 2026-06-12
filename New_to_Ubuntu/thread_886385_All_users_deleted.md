---
title: "All users deleted"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by jkarpago on 2008-08-11
Hi:

I installed proftpd yesterday and then I desinstalled with apt-get remove --purge and since then I have no users in gnome.

I restarted the computer and now I can no enter even to gdm because user GDM does not exist.

How can I fix this problem?
I cannot login as any users because there are no one.

---

### Post by meborc on 2008-08-11
if gdm does not exist then you must have removed something else then proftp :) ... try booting the recovery mode (second line in grub menu), then you are automatically root... install ubuntu-desktop package **apt-get install ubuntu-desktop**, this will install all packages needed for default ubuntu desktop (including gdm), then add new user and add him to sudoers group

[B]useradd NAME admin     EDIT: i might be wrong here... both useradd and adduser should work... but just to be on the safe side, use sisco's advice below!
passwd NAME[/B]

---

### Post by sisco311 on 2008-08-11
Boot the computer in Recovery Mode and add a new user
from the root shell:
```
adduser username
```
add the user to the admin group:
```
adduser username admin
```
and reboot:
```
reboot
```

---

### Post by sisco311 on 2008-08-11
> **meborc said:**
> if gdm does not exist then you must have removed something else then proftp :) ... try booting the recovery mode (second line in grub menu), then you are automatically root... install ubuntu-desktop package, this will install all packages needed for default ubuntu desktop (including gdm), then add new user and add him to sudoers group

[B]useradd NAME
passwd NAME[/B]

I think the network is not started in single user mode.
```
/etc/init.d/networking start
```should start it.

---

### Post by jkarpago on 2008-08-11
I have tried booting the recovery mode and I get this:

chown: 'root:utmp': invalid user 
chown: 'root:tty': invalid user
sulogin: cannot open password database! 
segmentation fault
init: rcS-sulogin main process (4160) terminated with status 139

I think this means that there is no user and I can`t do anything at all?

---

