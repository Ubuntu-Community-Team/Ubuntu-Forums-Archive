---
title: "Screwed up changing hostname"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by Balthazar54 on 2012-09-08
I've changed the hostname a second time on a debian system, and this time, unlike the first, the new name works everywhere except when trying to ssh in from another system.

Using the old (second) name works. Thought I did it exactly the same, and rebooted.

Can someone tell me what file I need to edit?

---

### Post by anewguy on 2012-09-08
/etc/hosts?

---

### Post by Balthazar54 on 2012-09-08
> **anewguy said:**
> /etc/hosts?

Nope, that has the new name in it, darn it.

Hmm, wonder if the system I am trying to connect from, Ubuntu 12.04, has cached it somehow...

---

### Post by sandyd on 2012-09-08
```

sudo nano /etc/hostname
```
^^ should be in there

---

### Post by coldcritter64 on 2012-09-08
> **sandyd said:**
> ```

nano /etc/hostname
```^^ should be in there
+1, "sudo" will be needed to edit that file, if the new name isn't already there OP.

---

### Post by Balthazar54 on 2012-09-09
Oops, my bad. Tried connecting from a windows boot on my laptop and it worked fine. 

My ubuntu system must have cached the name/address somewhere.

---

