---
title: "messed up mysql installation, have to remove completely"
date: 2012-09-04
forum: Programming Talk
---

### Post by sid0972 on 2012-09-04
hi fellas
i installed mysql sometimes earlier, and then i installed XAMPP (similar to LAMP ) over it.
Now when i try to run XAMPP, it starts up fine, except for mysql, it says

XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

i already have uninstalled mysql using 

```
sudo apt-get remove mysql-server
```

how do i remove it completely?

---

### Post by mevun on 2012-09-04
You may have some lock/pid file left over in /var/run if that is where the mysql-server daemon puts it.  Sometimes those files are in weird places though (or can be changed).

---

### Post by Bachstelze on 2012-09-04
What you have uninstalled is a metapackage, not the actual server. You should have a package mysql-server-VERSION, which is the one you need to uninstall.

---

### Post by sid0972 on 2012-09-05
> **Bachstelze said:**
> What you have uninstalled is a metapackage, not the actual server. You should have a package mysql-server-VERSION, which is the one you need to uninstall.

how do i do that?

---

### Post by Bachstelze on 2012-09-05
The same way you uninstalled the package mysql-server?

---

### Post by sid0972 on 2012-09-06
did that, uninstalled mysql-server-5.5
actually i uninstalled everything,whole lamp and xampp
encountered this error now

/etc/init.d/apache2: 51: .: Can't open /etc/apache2/envvars

anyways, i installed peppermint OS, its working fine in there
i guess i'll just work there itself

---

