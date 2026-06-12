---
title: "how can i tell if i'm running linux x86 or linux x86_4"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by sonaural on 2008-07-04
i'm trying to install an ati driver form the website and they asked me this.  i have no idea where to check the system specs

thanks

---

### Post by YaroMan86 on 2008-07-04
Open a turminal and type the following:

```
uname -a
```

It should return something like this:

```
Linux irma 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux
```

---

### Post by drs305 on 2008-07-04
```
uname -m
```

x86_64 is the 64-bit response.

---

### Post by jerome1232 on 2008-07-04
Applications - Accessories - Terminal
type
```
uname -m
```

---

