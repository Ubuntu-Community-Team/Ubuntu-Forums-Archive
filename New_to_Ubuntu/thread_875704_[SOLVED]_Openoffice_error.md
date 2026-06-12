---
title: "[SOLVED] Openoffice error"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-31
Hi.
I get this error while starting openoffice.org word processor 2.4:
```
The application cannot be started.
The user interface language cannot be determined.
```
Any suggestions?
Thanks.

---

### Post by dew5 on 2008-07-31
try this

cd ~
sudo chown --reference=. -R .openoffice.org2
sudo chmod -R 0755 .openoffice.org2

let me know how it goes..

dew5

---

### Post by cristo-father on 2008-07-31
I got this error.
[ATTACH]79587[/ATTACH]

---

### Post by fire5nake on 2008-09-08
> **dew5 said:**
> try this

cd ~
sudo chown --reference=. -R .openoffice.org2
sudo chmod -R 0755 .openoffice.org2

let me know how it goes..

dew5

Fixed it for me ... thanks :popcorn:

---

