---
title: "Custom keyboard shortcut to mono project"
date: 2010-11-08
forum: Programming Talk
---

### Post by jambel on 2010-11-08
Hi,

I am trying to create a custom keyboard shortcut that executes a program that I wrote in mono, so I create a new custom shortcut and give the command:

```
mono /home/dev/myapp.exe 'argument'
``` I also tryied

```
/usr/bin/mono /home/dev/myapp.exe 'argument'
```

but shortcut refuse to obay even without argument, any ideas?

Thanks!

---

### Post by jambel on 2010-11-11
nothing? :(

---

### Post by jambel on 2010-11-11
OK I managed it.

Because it's a console application, it should be like...

```
gnome-terminal -x mono /home/john/dev/myapp/myapp.exe
```

---

