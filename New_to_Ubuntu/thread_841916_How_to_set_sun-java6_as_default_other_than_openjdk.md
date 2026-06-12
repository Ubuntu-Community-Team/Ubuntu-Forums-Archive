---
title: "How to set sun-java6 as default other than openjdk?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Olnex on 2008-06-26
After installing ubuntu-restricted-extra, it pulls some openjdk packages, then I install sun-java-* but the default 'java' in command line is still openjdk, I tried to remove openjdk but it also removes other related packages.

---

### Post by lazyart on 2008-06-26
```
sudo update-alternatives --config java
```

---

### Post by starcannon on 2008-06-26
The way I deal with this annoyance is to uninstall open-jdk and then install sun-java-6.

Package manager takes care of removing and adding packages I need anyway /shrug, no problems yet.

---

