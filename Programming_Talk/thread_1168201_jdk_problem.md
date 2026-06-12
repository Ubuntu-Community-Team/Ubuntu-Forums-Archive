---
title: "jdk problem"
date: 2009-05-23
forum: Programming Talk
---

### Post by bubuzzz on 2009-05-23
Hi all,

from [http://ubuntuforums.org/showthread.php?t=1168048](http://ubuntuforums.org/showthread.php?t=1168048), i find out a very funny thing with ubuntu 9.04. I installed jdk 1.6 from synaptic, but when compiling the code in the above thread, i got the error and when checking jdk version, i got 1.5. Please see screenshot for more details. Is this a bug in ubuntu 9.04 or something ?

---

### Post by cl333r on 2009-05-23
When one has several JDKs installed one has to the option to choose the default one:
```

sudo update-alternatives --config java

```

---

### Post by bubuzzz on 2009-05-23
yup, i know. But why does ubuntu 9.04 also install gcj on my system? This doesn't happen in ubuntu 8.04

---

### Post by cl333r on 2009-05-24
- When people install from DVD OpenJDK is installed along which could also install some form of gcj, though I don'thave gcj installed, got 9.04.
- Never installed Java from synaptic, always from the command line.

---

### Post by jespdj on 2009-05-25
Some packages, such as ubuntu-restricted-extras, might still (incorrectly) depend on the gcj Java. So if you install such a package, you also get gcj installed.

---

### Post by bubuzzz on 2009-05-25
as i mentioned in the previous reply, i used to use ubuntu 8.04 with ubuntu-retricted-extra and jdk but had no problem with it. This is the first time i saw gcj appear in my computer. Maybe cl333r is right, the problem comes from installing throught synaptic, or this ubuntu version (dell-ubuntu9.04 from dell wiki)

---

### Post by jespdj on 2009-05-25
I don't know if ubuntu-restricted-extras does this or not, but there are packages like that which might have (wrong) dependencies like that. And because it didn't happen in 8.04, doesn't mean it doesn't happen in 8.10 or 9.04.

---

