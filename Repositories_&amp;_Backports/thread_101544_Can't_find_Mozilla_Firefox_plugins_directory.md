---
title: "Can't find Mozilla Firefox plugins directory"
date: 2005-12-10
forum: Repositories &amp; Backports
---

### Post by sp_ubuntulinux on 2005-12-10
I've installed jdk 1.5.0_05 in my /opt/ directory and i tried to set the jre path for Firefox. I can't seem to find the Mozilla Firefox plugins directory. Could someone please help me? I've set my jdk path using /etc/bash.bashrc. :D :D :D :D

---

### Post by amohanty on 2005-12-10
```
/usr/lib/mozilla/plugins/
/usr/lib/mozilla-firefox/plugins
```

Also if you install (I think it is) gcj, you should be able to set sun-jdk as your default jvm. Basically you should be able to get to a point so that you can do this;


```
aseem@kandinsky:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
aseem@kandinsky:~$
```

I had to do this to get eclipse to work properly.

HTH

---

