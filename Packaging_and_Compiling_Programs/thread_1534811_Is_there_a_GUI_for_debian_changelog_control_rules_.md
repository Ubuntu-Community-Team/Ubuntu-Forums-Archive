---
title: "Is there a GUI for debian changelog control rules etcetera and ppa?"
date: 2010-07-20
forum: Packaging and Compiling Programs
---

### Post by _sluimers_ on 2010-07-20
Right now, before I upload my source packages for the PPA builders to compile, I have those edit those debian files manually and I really hate that.

Isn't there a GUI for this?
Or at least a shell script that automatically bumps up the versions and delivers them to all chosen series.

I don't know about you guys, but 9/10 uploads still fail to me, due to minor stupid errors.

---

### Post by lisati on 2010-07-20
Thread closed, duplicate of [http://ubuntuforums.org/showthread.php?t=1534810](http://ubuntuforums.org/showthread.php?t=1534810)

---

### Post by km0r3 on 2010-07-21
> **_sluimers_ said:**
> Right now, before I upload my source packages for the PPA builders to compile, I have those edit those debian files manually and I really hate that.

Isn't there a GUI for this?
Or at least a shell script that automatically bumps up the versions and delivers them to all chosen series.

I don't know about you guys, but 9/10 uploads still fail to me, due to minor stupid errors.

What about [Deb-O-Matic]("https://launchpad.net/debomatic")? The description is promising, though I have never tried it:

> Automatic build machine for Debian source packages based on pbuilder.

Deb-o-Matic is an easy to use build machine for Debian source packages based on pbuilder, written in Python.

It provides a simple tool to automate build of source packages with limited user interaction and a simple configuration. It has some useful features such as automatic update of pbuilder, automatic scan and selection of source packages to build and modules support.

It is meant to help developers to build their packages without worrying too much of compilation, since it will run in background and no user feedback is required during the whole process.

Please, tell if it's that what you've searched for.

---

### Post by _sluimers_ on 2010-07-22
Thanks, I wish I knew how to use this. Simply copying their example debomatic.conf from /etc/debomatic to my helloWorld.cpp example and running 
```
sudo debomatic -c debomatic.conf
```
doesn't seem to do anything.

[EDIT]I can see in the logfile:

```
Another instance is running. Aborting.
```

---

### Post by km0r3 on 2010-07-22
Unfortunately, I have no idea, mate...

A good place for your question would be Launchpad or the project's mailing list.

---

