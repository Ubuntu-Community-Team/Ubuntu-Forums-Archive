---
title: "problem with cairo installation on SUSE"
date: 2011-05-26
forum: Programming Talk
---

### Post by Blackbug on 2011-05-26
I am tryin to install cairo
but its displayin followin error
```
checking for POPPLER... no
configure: WARNING: PDF backend will not be tested since poppler >= 0.13.3 is not available

```
 
i have installed poppler 3 times but no use
 
even pkg-config shows its installed
 
```

pkg-config --libs poppler
-L/nethome/tmt507/k/karnatak/bin/lib -lpoppler

```
 
any idea?

---

### Post by gmargo on 2011-05-26
What is the version of the installed poppler package?  Perhaps it is too old.

---

