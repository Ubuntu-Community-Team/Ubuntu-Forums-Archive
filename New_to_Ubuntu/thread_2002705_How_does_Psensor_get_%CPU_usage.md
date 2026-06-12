---
title: "How does Psensor get %CPU usage?"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by vasa1 on 2012-06-13
Psensor can report temperature(s) and %CPU usage. Any idea how the %CPU usage is obtained by Psensor?

---

### Post by jeanfi on 2012-07-06
Hello,

> **vasa1 said:**
> Psensor can report temperature(s) and %CPU usage. Any idea how the %CPU usage is obtained by Psensor?

It is obtained by using libgtop ([http://developer.gnome.org/libgtop/stable/libgtop-lib.html](http://developer.gnome.org/libgtop/stable/libgtop-lib.html)). The code is here:
[http://wpitchoune.net/svnpub/psensor/trunk/src/lib/cpu.c](http://wpitchoune.net/svnpub/psensor/trunk/src/lib/cpu.c)

Basicaly, it is the % of time the cpu is running system and users processes.

---

### Post by vasa1 on 2012-07-06
Thanks, jeanfi :)

---

