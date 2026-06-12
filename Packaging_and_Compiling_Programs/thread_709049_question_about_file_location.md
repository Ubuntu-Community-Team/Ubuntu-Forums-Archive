---
title: "question about file location"
date: 2008-02-27
forum: Packaging and Compiling Programs
---

### Post by thungmail on 2008-02-27
hi
When I use the command sudo apt-get install XXXX.I would like to know where my XXXX 's directory..Can some body explain for me pls

---

### Post by RJ Hythloday on 2008-02-27
I think it's downloading it from an online repository, unless you used  a live dvd than it might ask you to put the dvd in the drive.

---

### Post by thungmail on 2008-02-28
so after installing, what is the directory for an application

---

### Post by dholbach on 2008-02-28
/var/lib/dpkg/info/XXXX.list will tell you which files were installed by that package.

/var/lib/dpkg/info/gedit.list for example.

---

