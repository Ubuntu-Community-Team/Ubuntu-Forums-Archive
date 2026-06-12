---
title: "installing libmono-2.0"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Hirashgeff on 2008-05-31
I want to install libmono-system2.0-cil in my system (8.04)

when i tried to install libmono-system2.0-cil.deb(debian File)
It's ask for libmono-security2.0-cil dependency to be installed
then i tried to install libmono-security2.0-cil it's asking for 
libmono-system2.0-cil to be installed 

so i can't install any one of above 

Help Me plz

---

### Post by shifty_powers on 2008-05-31
[http://packages.ubuntu.com/hardy/libmono-system2.0-cil](http://packages.ubuntu.com/hardy/libmono-system2.0-cil)

also, post the output of your sources file ;)

```
sudo gedit /etc/apt/sources.list
```

---

### Post by paulphillips on 2008-05-31
This is a known bug in debian:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=375871](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=375871)

Unfortunately, I don't know how to fix it.

---

