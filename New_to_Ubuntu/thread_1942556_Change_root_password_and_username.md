---
title: "Change root password and username"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by Azatos on 2012-03-17
I accidentally had caps locks on when I was installing Ubuntu 11.10.


Any easy way to fix this?

---

### Post by jerome1232 on 2012-03-17
I assume you mean the first users password since by default in Ubuntu the root account is locked, has no password, and cannot be logged into.

See this for info about that [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To change your users pasword simply Click the gear icon in the top right, click system settings, click user accounts, click on password and change it.

Alternatively in a terminal

```
passwd
```

---

### Post by d4m1r on 2012-03-17
> **Azatos said:**
> I accidentally had caps locks on when I was installing Ubuntu 11.10.


If this is true, and the installer went ahead with this, they really should display a popup or confirmation message BEFORE the installer runs if the user doesn't realize they have caps lock enabled...

---

### Post by Azatos on 2012-03-20
Thanks worked fine.  It probably does warn you before hand I don't really remember I was slightly intoxicated during installation.

---

