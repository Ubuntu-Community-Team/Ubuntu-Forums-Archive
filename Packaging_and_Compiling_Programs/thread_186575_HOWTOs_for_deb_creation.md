---
title: "HOWTOs for deb creation?"
date: 2006-06-02
forum: Packaging and Compiling Programs
---

### Post by ketsugi on 2006-06-02
What are some good tutorials for creating .deb files?

Here are some I've found and used, but none are really easy to follow...

[http://www.ubuntuforums.org/showthread.php?t=51003](http://www.ubuntuforums.org/showthread.php?t=51003)
[https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch](https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch)

---

### Post by jobezone on 2006-06-02
Ubuntu dapper has a guide for it in System->Help->System Documentation , called Packaging guide, or something.

---

### Post by simplyw00x on 2006-06-05
A simple one here:
[http://www.desktopos.com/modules/articles/article.php?id=39](http://www.desktopos.com/modules/articles/article.php?id=39)

---

### Post by loell on 2006-06-06
checkinstall would be the easiest and quickest but dirty way to create a deb package

---

### Post by ketsugi on 2006-06-07
Checkinstall doesn't help if I just want to create a deb package for a shell scripts or a bunch of shell scripts. I have no make file, just a bunch of files I want to put in certain directories, and a bunch of dependencies I want to make sure are installed before the scripts gets installed.

---

### Post by loell on 2006-06-07
wouldn't it be better to just archive it?

---

### Post by mlind on 2006-06-30
I made few howto's about the subject
[http://ubuntuforums.org/showthread.php?t=206382](http://ubuntuforums.org/showthread.php?t=206382)
[http://ubuntuforums.org/showthread.php?t=204523](http://ubuntuforums.org/showthread.php?t=204523)
[http://ubuntuforums.org/showthread.php?t=203382](http://ubuntuforums.org/showthread.php?t=203382)
[http://ubuntuforums.org/showthread.php?t=200762](http://ubuntuforums.org/showthread.php?t=200762)

---

### Post by Mr Egg on 2006-07-08
In the book "Ubuntu Hacks : Tips & Tools for Exploring, Using, and Tuning Linux (Hacks)" published by O'Reilly, there is an entire chapter on Ubuntu package development and management, take a look at it :).

---

