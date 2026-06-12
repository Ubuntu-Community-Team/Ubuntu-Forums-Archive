---
title: "While patching...server crashed"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by comcom on 2008-05-17
Like the Title said...the server crashed when it was updating Ubuntu.

Now when i login, i have a empty desktop and don't know how i can recover this all.

In advance...

Comcom

---

### Post by jaakan on 2008-05-17
try this
reboot the server don't login to the GUI/X
hit Crtl+Alt+F1

login in on the command line
sudo -i ( it will ask you for your password again )
aptitude update
dpkg --configure -a
aptitude update
aptitude upgrade
reboot

Jaakan

[edit]
thanks Joeb for catching that

---

### Post by Joeb454 on 2008-05-17
Preferably replace sudo -s with ```
sudo -i
```

---

