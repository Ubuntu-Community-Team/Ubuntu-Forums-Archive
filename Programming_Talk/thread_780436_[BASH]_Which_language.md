---
title: "[BASH] Which language?"
date: 2008-05-03
forum: Programming Talk
---

### Post by Martje_001 on 2008-05-03
Hello,
How do I find out in what locale gnome/kde is running (in a bash script)?

---

### Post by Martin Witte on 2008-05-03
I think this is a system wide setting, made in /etc/environment
```
martin@toshibap200:~$ echo $LANG
en_US.UTF-8

```

---

### Post by nvteighen on 2008-05-03
There's also the locale command...
```

ugi@UGI:~$ locale
LANG=es_AR.UTF-8
LC_CTYPE="es_AR.UTF-8"
LC_NUMERIC="es_AR.UTF-8"
LC_TIME="es_AR.UTF-8"
LC_COLLATE="es_AR.UTF-8"
LC_MONETARY="es_AR.UTF-8"
LC_MESSAGES="es_AR.UTF-8"
LC_PAPER="es_AR.UTF-8"
LC_NAME="es_AR.UTF-8"
LC_ADDRESS="es_AR.UTF-8"
LC_TELEPHONE="es_AR.UTF-8"
LC_MEASUREMENT="es_AR.UTF-8"
LC_IDENTIFICATION="es_AR.UTF-8"
LC_ALL=

```

---

### Post by Martje_001 on 2008-05-03
Thank you!

---

