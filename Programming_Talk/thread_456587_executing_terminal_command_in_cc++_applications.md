---
title: "executing terminal command in c/c++ applications"
date: 2007-05-27
forum: Programming Talk
---

### Post by u04f061 on 2007-05-27
can anybody tell me how to run terminal commands in C/C++ programs. Does Qt provides any facility to do this? please give me some resources links (tutorials etc) related to it.

---

### Post by yabbadabbadont on 2007-05-27
```
man 3 system
```
You will probably need to have the manpages-dev package installed for that to work.  Also read up on the "spawn" series of library functions.

---

### Post by u04f061 on 2007-05-27
> man 3 system

what is man 3 system?
I only kno how to open man(1) page by simply typing man app_name

plz tell me how to open man 3

---

### Post by yabbadabbadont on 2007-05-27
```
man man
``` will answer your question....  :D

Short answer, just type it into a terminal window, hit enter, read.  ;)

---

### Post by u04f061 on 2007-05-27
thanks done it.

---

### Post by seamless on 2007-05-28
> **u04f061 said:**
> can anybody tell me how to run terminal commands in C/C++ programs. Does Qt provides any facility to do this? please give me some resources links (tutorials etc) related to it.
Qt provides full support using [QProcess]("http://doc.trolltech.com/4.2/qprocess.html"). You will probably want to use the [startDetached]("http://doc.trolltech.com/4.2/qprocess.html#startDetached") function otherwise spawned command will be killed when your application exits.

---

### Post by u04f061 on 2007-05-28
> Qt provides full support using QProcess. You will probably want to use the startDetached function otherwise spawned command will be killed when your application exits.

thanks. that is what i was looking for.

---

