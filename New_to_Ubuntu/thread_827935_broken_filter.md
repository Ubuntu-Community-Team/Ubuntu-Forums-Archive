---
title: "broken filter"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by slayerkiller on 2008-06-13
Update manager says I have bronken a package and to use broken filter to do this, how do I do it and how do I fix a broken package?

---

### Post by _sphinx_ on 2008-06-13
A simple command would probably do this
```

sudo apt-get install -f

```

---

### Post by env2156 on 2008-08-07
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on sun-java6-jre (= 6-06-0ubuntu1); however:
  Package sun-java6-jre is not installed.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin


that is what i got

when i was trying to install it told me to locate with broken filter to fix it i dont know what that means

---

### Post by Crafty Kisses on 2008-08-07
> **env2156 said:**
> dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on sun-java6-jre (= 6-06-0ubuntu1); however:
  Package sun-java6-jre is not installed.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin


that is what i got

when i was trying to install it told me to locate with broken filter to fix it i dont know what that means
You're going to have to install those packages.

---

