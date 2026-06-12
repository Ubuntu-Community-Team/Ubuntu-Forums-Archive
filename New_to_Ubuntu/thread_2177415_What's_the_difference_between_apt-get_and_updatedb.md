---
title: "What's the difference between apt-get and updatedb commands in terminal"
date: 2013-09-28
forum: New to Ubuntu
---

### Post by adam20 on 2013-09-28
Not quite sure what the difference is between the 2

---

### Post by Jonathan Precise on 2013-09-28
```
apt-get
``` installs/upgrades **_packages_**.

```
updatedb
``` updates the slocate database.

---

### Post by Elfy on 2013-09-28
apt-get is the package handler - used to install packages

the updatedb command updates the database used by locate

They are completely different things :)

---

### Post by Elfy on 2013-09-28
> **Jonathan Precise said:**
> ...

```
updatedb
``` just updates a list of the programs that can be run by **_program-name_** instead of /path/to/**_program-name_**.

No - it does more than that :)

locate will find more than just program names. 

Check out updatedb.conf

```
cat /etc/updatedb.conf
```

You'll see there it keeps much more in the database, in my case I mount all my multimedia in /mnt mountpoints - I can use locate on those files too.

---

### Post by vasa1 on 2013-09-28
> **Jonathan Precise said:**
> ...
```
updatedb
``` updates the **s**locate database.
Jon, on my Lubuntu 13.04, `man` say that /var/lib/mlocate/**m**locate.db is the database.
BTW, very nice apt-get tutorial :)

---

