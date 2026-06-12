---
title: "How can I see what version of Ubuntu I have?"
date: 2017-10-15
forum: New to Ubuntu
---

### Post by eliyahu22 on 2017-10-15
How can I see what version of Ubuntu I have?

---

### Post by &amp;KyT$0P# on 2017-10-15
Run these commands in a Terminal -
```
lsb_release -a
uname -a
```

---

### Post by deadflowr on 2017-10-15
The command 
```
lsb_release -a
```
will tell what release of Ubuntu.
the command
```
echo $DESKTOP_SESSION
```
should tell what flavor or desktop environment you have running.

Added, the command
```
cat /var/log/installer/media-info
```
will tell you which flavor of Ubuntu you originally installed.

Hope it helps

---

### Post by eliyahu22 on 2017-10-15
Thanks guys.

---

