---
title: "Syslog : Signal 15?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by django0909 on 2008-06-01
This line is in my syslog. Anyone know what it means?

```
Jun  1 00:44:48 dan-desktop exiting on signal 15
```

Thanks all..

---

### Post by quelx on 2008-06-01
signal 15 is a normal termination of an application, probably put in the syslog when you system was shutting down.

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_01.html)

and **man kill**

---

### Post by django0909 on 2008-06-01
Great, thanks :)

---

