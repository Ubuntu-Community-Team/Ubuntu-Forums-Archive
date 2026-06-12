---
title: "Determine OS version"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Jim Lennington on 2008-10-23
How do I find out which version of Ubuntu I have installed?

---

### Post by drs305 on 2008-10-23
```

uname -r
lsb_release -a

```

Results:
```

user@hostname:~$ uname -r
**2.6.27-7-generic**
user@hostname:~$ lsb_release -a
[B]No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid[/B]

```

---

### Post by bsharp on 2008-10-23
System->Administration->System Monitor and click the System tab

---

