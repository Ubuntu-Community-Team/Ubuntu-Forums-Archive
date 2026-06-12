---
title: "synaptic package manager isnt working"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by skater-dude on 2008-10-14
today i connected the internet to install something on synaptic package manager and when i opened it, it came up with E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
so i disconnected from the internet and it didnt go away. i went on terminal and typed in dpkg --configure -a and it came up with
dpkg: requested operation requires superuser privelidge

what do i do?

---

### Post by nothingspecial on 2008-10-14
Type 
```

sudo dpkg --configure -a
```

---

### Post by gn2 on 2008-10-14
Use the code in Nothingspecial's post.

sudo stands for super-user do and gives the required permissions to make system changes.

More info [**here**]("http://en.wikipedia.org/wiki/Sudo").

---

