---
title: "How to upgrade a set of packages?"
date: 2015-07-02
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-07-02
Hello guys 
Whenever you install Ubuntu you will probably have a lot of updates to install, so is there a way to update only packages related to certain category, for example: 
update multi-media related packages, and then internet related packages and so on.........
I hope my meaning is clear.
Thank you.

---

### Post by grahammechanical on 2015-07-02
1) Do not allow the installation of Ubuntu to install updates at the same time.
2) After installation load Ubuntu and run the Update Manager/Software Updater
3) Untick any packages that you do not want updated at that particular time.

We can do this at any time we run Software Updater.

Regards.

---

### Post by earruda on 2015-07-21
It is possible to update a set of packages, but, as far as I know, it is not possible to it as you like out-of-the-box.
You can follow @grahammechanical's tip on a GUI client, or by typing the name of each package in command line:

```

# apt-get install package1 package2 ...

```

---

