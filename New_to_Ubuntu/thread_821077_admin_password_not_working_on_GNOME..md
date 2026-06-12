---
title: "admin password not working on GNOME."
date: 2008-06-06
forum: New to Ubuntu
---

### Post by nightrider.36 on 2008-06-06
I upgrade from Feisty Fawn to Hardy Heron. Something strange happened to the hard drive so I ran FSCK manually. The system recovered but now the ROOT password does not work. 

The password does work when I "sudo".

SYSTEM -> ADMINISTRATION -> LOGIN WINDOW will not accept the root password.

%sudo gdmsetup does work

What's the difference? What's going on?

---

### Post by Joeb454 on 2008-06-06
By default - Ubuntu does not let you log in graphically as root. If you want a graphical nautilus window, run ```
gksudo nautilus
``` or if you want to become root temporarily in a terminal, run ```
sudo -i
```

---

