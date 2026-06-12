---
title: "[SOLVED] how do i get root rights?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by sven_wien on 2008-11-11
hi all i need root rights for usr share games openttd data, how do i get those?

thanks

---

### Post by __Frank__ on 2008-11-11
Hi Sven,

To run a command as superuser: sudo <command>
To change to root: sudo su

Hope this helps.

Regards,
Frank

---

### Post by mapes12 on 2008-11-11
In Terminal

```
sudo
```

or

```
sudo su
```

to become permanent root for the session

or

```
gksu nautilus
```

For a GUI file browser with root privileges

All to be used with great care.

---

### Post by taurus on 2008-11-11
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

