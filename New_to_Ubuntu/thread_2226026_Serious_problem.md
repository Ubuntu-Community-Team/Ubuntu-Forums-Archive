---
title: "Serious problem"
date: 2014-05-24
forum: New to Ubuntu
---

### Post by johnsyzemore on 2014-05-24
I keep getting this error for my Ubuntu 14.04 repeatedly

E:Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.

I am open to any suggestions on how to fix it

---

### Post by Bashing-om on 2014-05-24
johnsyzemore; Hi Welcome to the forum.

Hey, the medibuntu repository has not been in existence in some time. Are you running a current supported release ?

To address the current issue, "line 1 in source list /etc/apt/sources.list.d/medibuntu.list";

Remove that source - ubuntu Software Center - and all should be good,
else for additional assistance show us the output of:
```

ls -la /etc/apt/sources.list.d/

```
And will direct how to remove it manually.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by aysiu on 2014-05-24
Open a terminal

Paste in ```
sudo nano /etc/apt/sources.list.d/medibuntu.list
``` delete the first line (control-k deletes). Then save (control-x).

---

### Post by johnsyzemore on 2014-05-25
Thank you soo much. That fixed my problem aysiu

---

### Post by aysiu on 2014-05-25
Glad to hear it!

---

