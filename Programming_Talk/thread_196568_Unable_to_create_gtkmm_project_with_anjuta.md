---
title: "Unable to create gtkmm project with anjuta"
date: 2006-06-14
forum: Programming Talk
---

### Post by bhubanmm on 2006-06-14
Hello,

I am trying to develop a gtkmm application in C++ on FC4 with Anjuta 1.2. I have installed gtkmm-2.4 with Yum. But, when I try to create a new gtkmm application, it gives me an error saying:
> gtkmm-2.0 not found
It tells me to set the PKG_CONFIG_PATH to gtkmm-2.0.pc while I already have gtkmm-2.4.pc.
```
slocate gtkmm-2.4
```
shows me the directory that gtkmm-2.4.pc is present. I even tried setting the PKG_CONFIG_PATH variable, but it gave me the same error and I am not able to create a simple project with gtkmm. I am new to LINUX. Please help me.

Thanks in advance.

---

### Post by dungh on 2006-06-21
I did this:
1)edit the project configure.in file by replacing 
PKG_CHECK_MODULES(PACKAGE, [gtkmm-2.0]) with PKG_CHECK_MODULES(PACKAGE, [gtkmm-2.4])
2)save the file.
3)choose Build/Auto generate from within Anjuta.

Looks like it's working for me.

---

