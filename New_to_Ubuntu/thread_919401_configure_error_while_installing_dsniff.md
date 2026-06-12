---
title: "configure error while installing dsniff"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by resistantgnome on 2008-09-13
Hi

I tried installing dsniff-2.3 on Ubuntu 8.04. While executing *configure*, I got error regarding C compiler. I installed build-essential to solve it. Now, I am again getting *configure: error: Berkeley DB with 1.85 compatibility not found   *. Any idea how to solve this?

---

### Post by resistantgnome on 2008-09-14
Instead of command line I installed through synaptic. It works now.

---

### Post by mr.scotty on 2011-11-13
hi,
topic is quiet old, but I had the same problem right now. libdb-dev is missing.
```
apt-get install libdb-dev
```
this fixed it for me.
greetz

---

