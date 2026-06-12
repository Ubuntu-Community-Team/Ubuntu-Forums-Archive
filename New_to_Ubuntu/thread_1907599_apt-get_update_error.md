---
title: "apt-get update error?"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by rom3lol on 2012-01-11
I'm trying to update and or install a program and this is what I get:

```
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

It seems as if the PATH is missing* /usr/local/sbin, /usr/sbin and /sbin. *How to fix this?

---

### Post by adityamagadi on 2012-01-11
on ur terminal run the cmd sudo apt-get install -f

---

### Post by rom3lol on 2012-01-12
Thanks for the reply adityamagadi, but that didn't help. So I boot into my Ubuntu Live CD and copied "ldconfig" and "ldconfig.real" into my filesystem.

Mount your filesystem and Open terminal
```
sudo cd / && cd sbin && cp ldconfig ldconfig.real /media/"file system name here"
``` "cd" into your mounted filesystem and type the following
```
sudo mv ldconfig ldconfig.real sbin
```

---

