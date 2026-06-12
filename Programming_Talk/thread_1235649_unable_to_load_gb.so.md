---
title: "unable to load gb.so"
date: 2009-08-09
forum: Programming Talk
---

### Post by kipelovets on 2009-08-09
hi

i have installed php5 and php5-gd into my ubuntu 8.10, and now i get this message in error_log:

PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: undefined symbol: gdImageCreateFromGif in Unknown on line 0

how can i fix that?

---

### Post by PaulFr on 2009-08-11
This is probably an incompatibility with libgd.so on your system. Can you check if libgd2-xpm or libgd2-noxpm is installed on your system ? (command is **aptitude search libgd2**, but you already know this). If it is not installed, I would suggest you install libgd2-xpm and then try again.

---

### Post by kipelovets on 2009-08-11
> **PaulFr said:**
> This is probably an incompatibility with libgd.so on your system. Can you check if libgd2-xpm or libgd2-noxpm is installed on your system ? (command is **aptitude search libgd2**, but you already know this). If it is not installed, I would suggest you install libgd2-xpm and then try again.

libgd2-xpm is installed on my system

---

### Post by PaulFr on 2009-08-12
libgd.so removed support for GIF images because of patent issues, then added back support for them in version 2.0.28.

Is **php5-gd** package installed ? If not, please install it, and then restart the Apache browser (or you could restart the system).

---

### Post by kipelovets on 2009-08-12
php5-gd is installed, still the problem exists

---

### Post by PaulFr on 2009-08-13
What is the output of ```
$ **cd /usr/lib/php5/20060613+lfs; ldd gd.so | grep libgd**
```
Maybe you need to try the instructions in the _last comment_ at the bottom of **_[http://www.phpfreaks.com/forums/index.php?topic=226019.0](http://www.phpfreaks.com/forums/index.php?topic=226019.0)_**.

---

### Post by kipelovets on 2009-08-13
> **PaulFr said:**
> What is the output of ```
$ **cd /usr/lib/php5/20060613+lfs; ldd gd.so | grep libgd**
```Maybe you need to try the instructions in the _last comment_ at the bottom of **_[http://www.phpfreaks.com/forums/index.php?topic=226019.0](http://www.phpfreaks.com/forums/index.php?topic=226019.0)_**.


```

phantom@phantom-laptop:~$ cd /usr/lib/php5/20060613+lfs
phantom@phantom-laptop:/usr/lib/php5/20060613+lfs$ ldd gd.so | grep libgd
    libgd.so.2 => /usr/lib/libgd.so.2 (0xb7f2c000)

```

---

