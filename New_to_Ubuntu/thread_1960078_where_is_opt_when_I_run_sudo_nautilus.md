---
title: "where is /opt/ when I run sudo nautilus?"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by hanzj on 2012-04-16
Hello,

where is /opt/ folder when I run "sudo nautilus"? I can't find it.
Please help.

---

### Post by oldos2er on 2012-04-16
Is /opt on a mounted partition?

You wouldn't necessarily need to use 'sudo' just to run 'cd /opt'

---

### Post by sixonqjz on 2012-04-28
To run nautilus, just press alt F2

---

### Post by haqking on 2012-04-28
> **hanzj said:**
> Hello,

where is /opt/ folder when I run "sudo nautilus"? I can't find it.
Please help.

first of all nautilus should be run with gksudo and not sudo, gksudo for graphical apps.

Aslo elevated privelege should not be needed to see that /opt directory which is by default in /

---

### Post by hanzj on 2012-04-28
I didn't want to just view /opt/. I wanted to add files.

---

### Post by haqking on 2012-04-28
> **hanzj said:**
> I didn't want to just view /opt/. I wanted to add files.

ok so from terminal

```
gksudo nautilus
```

or press alt+f2 and type same thing

and then /opt is under root / so just browse in root.

However be careful, if you dont know how to browse to a folder using root privelege it may not be a good idea ;)

Peace

---

