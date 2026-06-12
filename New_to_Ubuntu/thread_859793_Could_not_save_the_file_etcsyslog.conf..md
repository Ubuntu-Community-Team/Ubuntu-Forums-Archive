---
title: "Could not save the file /etc/syslog.conf."
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Bartee on 2008-07-14
I am trying to change the settings for cronlog in the syslog.conf file.

When I try to save it does not allow me.

I suspect this is because it is a root file.

How can I edit it and save it.  I am the only user on the box.

---

### Post by adobrakic on 2008-07-14
```
sudo gedit /etc/syslog.conf
```
 
in terminal

---

### Post by ChameleonDave on 2008-07-14
> **Bartee said:**
> I am trying to change the settings for cronlog in the syslog.conf file.

When I try to save it does not allow me.

I suspect this is because it is a root file.

How can I edit it and save it.  I am the only user on the box.
Just put "sudo" before the command (or gksudo for graphical apps).

For example, you could edit the file with "sudo nano" or "gksudo gedit".

---

### Post by weirdfox on 2008-07-14
Yes as stated above, you need to use "sudo" to gain the right to edit system files (that means almost all files except those in your home folder).

Or to get the graphical password prompt use Alt+F2 and run :
```

gksudo gedit /etc/syslog.conf

```

---

### Post by iaculallad on 2008-07-14
It will always be a good practice to use **gksudo/gksu/kdesu** for accessing graphical application that needs authentication to process tasks and to lock **sudo** for terminal-base application.

```
gksudo gedit /etc/syslog.conf
```

```
sudo nano /etc/syslog.conf
```

---

