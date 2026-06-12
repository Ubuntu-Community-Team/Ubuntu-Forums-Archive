---
title: "cant install iced tea"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-09-04
im getting this error message when i try to install java..
```
openjdk-6-jdk:
 Depends: openjdk-6-jre but it is not going to be installed
```

and then

```
openjdk-6-jre-headless:
 Depends: openjdk-6-jre-lib but it is not going to be installed
 Depends: tzdata-java but it is not going to be installed
```


i need assistance

---

### Post by Pro-reason on 2008-09-05
In Synaptic, go to “Preferences” and make sure that all the repositories are enabled.  Then hit “Reload” and try again.

Does the error persist?

---

### Post by Crafty Kisses on 2008-09-05
That looks like your missing dependices.

---

