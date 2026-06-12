---
title: "[SOLVED] Dumbest question i guess"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-11-21
Hello, probably this is the most dumbest question in all the forum, i search in google but didnt find any command to do that

is there a command to know the version of linux i have?
like uname -r to know the kernel version?

Regards!

---

### Post by drs305 on 2008-11-21
I think what you want is:

```
lsb_release -a
```

Result:
```

[I]
64@hb1:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
[/I]

```

---

### Post by drakeman007 on 2008-11-21
> **drs305 said:**
> I think what you want is:

```
lsb_release -a
```

Result:
```

[I]
64@hb1:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
[/I]

```

Thats exactly what i wanted. thanksss!!!!:guitar:

---

### Post by steveneddy on 2008-11-21
can we mark this as solved please?

---

### Post by drakeman007 on 2008-11-21
> **steveneddy said:**
> can we mark this as solved please?

Done!
thanks!

---

