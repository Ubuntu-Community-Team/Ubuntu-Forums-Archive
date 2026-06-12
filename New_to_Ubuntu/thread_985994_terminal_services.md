---
title: "terminal services"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Omegaomni on 2008-11-18
how can i turn on services using the terminal?
specifically the login screen.

---

### Post by beno1990 on 2008-11-18
```
sudo /etc/init.d/gdm start
```

Should start GDM if you have it installed.

/etc/init.d stores init scripts which you can use to start, stop or restart certain programs and services with.

---

### Post by superprash2003 on 2008-11-18
or type startx

---

