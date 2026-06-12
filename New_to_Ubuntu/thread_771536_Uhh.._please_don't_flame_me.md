---
title: "Uhh.. please don't flame me"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by JacobZlogar on 2008-04-27
I'm trying to install compiz-fusion but everytime i go into the terminal i get this 
jacob@jacob-desktop:~$ sudo aptitude install compizconfig-settings-manager
[sudo] password for jacob: 
E: Malformed line 62 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 62 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
E: Malformed line 62 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

Any help would be appreciated

---

### Post by scragar on 2008-04-27
paste back the results of:
```
cat /etc/apt/sources.lst | head -n 67 | tail
```
in the forums [code] tags if you don't mind.

---

### Post by zaussome on 2008-04-27
z

---

