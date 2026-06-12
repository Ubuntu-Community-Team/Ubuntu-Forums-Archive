---
title: "how to find running process"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by apartfromthedirt on 2008-06-23
Looking to understand how to find running process(s), shut down a shell to early, and now can't complete an install. Error messages:

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable


Any suggestions for fixing this??

---

### Post by Mikecore on 2008-06-24
> **apartfromthedirt said:**
> Looking to understand how to find running process(s), shut down a shell to early, and now can't complete an install. Error messages:

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable


Any suggestions for fixing this??

to find a process use this command

```

sudo ps aux

```

to learn more about this command try

```

man ps

```

should tell you everything you want to know

---

### Post by iaculallad on 2008-06-24
> **apartfromthedirt said:**
> Looking to understand how to find running process(s), shut down a shell to early, and now can't complete an install. Error messages:

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable


Any suggestions for fixing this??

Try to execute this command in the terminal to find out what process is using that file:

```
lsof /var/cache/debconf/config.dat
```

or try:

```
fuser -v /var/cache/debconf/config.dat
```

---

