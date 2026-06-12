---
title: "Where to find the source code of applications"
date: 2006-09-03
forum: Programming Talk
---

### Post by Timothy Butwinick on 2006-09-03
I am sorry if this is a stupid question, but where in the file system is the source of an installed application stored? Is this downloaded along with the intallation files, and if not, how and from where do I get it?

---

### Post by meng on 2006-09-03
Often it is not stored on the system. Go to the project's homepage to get the source.

---

### Post by christhemonkey on 2006-09-03
> **Timothy Butwinick said:**
> I am sorry if this is a stupid question, but where in the file system is the source of an installed application stored? Is this downloaded along with the intallation files, and if not, how and from where do I get it?

In most cases (all?) the source is not downloaded unless you specifically ask apt for it.
(you need deb-src entries for every deb entry in your sources.list)

Then you can just type:
```
sudo apt-get source PACKAGE_NAME 
```
(replacing PACKAGE_NAME with real package name obviously)

---

### Post by bukwirm on 2006-09-03
Source is usually stored /usr/src or /usr/local/src

---

### Post by H.E. Pennypacker on 2006-09-03
Many programmers will add the source files to the file you downloaded in the first place.  If not, you will need to go to the homepage, and download the source there.

---

