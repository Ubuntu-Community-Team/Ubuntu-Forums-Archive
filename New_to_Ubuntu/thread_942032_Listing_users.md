---
title: "Listing users"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-08
How do I get a list of all users on my system via terminal?

---

### Post by bodhi.zazen on 2008-10-08
use "who"

```
who
```

If you want a list of all users on the system 

```
cat /etc/passwd
```

If you want a list of all users who would log in 

```
ls /home
```

---

### Post by Konstabel on 2008-10-08
Why do I get so many other "users" on my system as well, and not only root and those I have added?
example:
> root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh

---

### Post by Squid Tamer on 2008-10-08
The who command tells you who's currently logged in, and terminals and other things count as logins. tty7 is usually the graphical interface, and others are terminals.

---

### Post by bodhi.zazen on 2008-10-08
> **Konstabel said:**
> Why do I get so many other "users" on my system as well, and not only root and those I have added?
example:

Those other "users" are system users, ie a mail server etc.

I can not find a good link that reviews all the default system users on Ubuntu at the moment.

---

