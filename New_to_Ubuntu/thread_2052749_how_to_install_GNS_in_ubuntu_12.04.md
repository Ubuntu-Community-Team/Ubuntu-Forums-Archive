---
title: "how to install GNS in ubuntu 12.04"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by nirajbu on 2012-09-03
how to install GNS in ubuntu 12.04.When i try to install from 
software center , it always display the error message of dependencies fail. Any one can please help.

---

### Post by Bashing-om on 2012-09-04
nirajbu;

   Try this from terminal to repair the broken packages:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

```

The use of sudo requires your password ..will get no echo to screen (security reasons).

[INDENT]hth <==BDQ

[/INDENT]

---

