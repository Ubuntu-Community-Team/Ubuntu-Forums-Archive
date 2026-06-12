---
title: "package control file - how to automatically install depending packages"
date: 2013-04-24
forum: Packaging and Compiling Programs
---

### Post by tombert on 2013-04-24
I am creating packages using "dpkg --build" and the related control file:

```
Package: mypackageVersion: 1.0
Pre-Depends: apache2, php5, sed, awk, nodejs, imagemagick

```

The problem is:
```
dpkg: regarding .../mypackage.deb containing mypackage, pre-dependency problem:
 mypackage pre-depends on nodejs
  nodejs is not installed.
  ...

```

Is it possible the dependencies are getting installed automatically? I did not find any appropriate control option.

thx

---

### Post by schragge on 2013-04-24
Installing dependencies is done by apt-get/aptitude/synaptic etc., dpkg won't do it automatically. TBH, I have problem understanding what you are trying to achieve.

---

### Post by tombert on 2013-04-24
I think that answered the question. I thought that dpkg would do it.
thx

---

