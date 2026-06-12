---
title: "problem with Automake (konqueror's fault)"
date: 2006-12-13
forum: Programming Talk
---

### Post by Absurd on 2006-12-13
I am having a problem using automake. First of all, it seems like konqueror does not allow files to have filenames in all capitals. So, when I do "touch NEWS README AUTHORS ChangeLog," I get news, readme, authors, and ChangeLog.

When I do "sudo automake -add-missing" I get

> automake: configure.ac: installing `./install-sh'; error while making link: Operation not permitted

automake: configure.ac: installing `./mkinstalldirs'; error while making link: Operation not permitted

automake: configure.ac: installing `./missing'; error while making link: Operation not permitted

automake: Makefile.am: installing `./INSTALL'; error while making link: Operation not permitted

automake: Makefile.am: installing `./COPYING'; error while making link: Operation not permitted


Adding a -v argument to automake only says that it is reading aclocal, etc but nothing about an error. 

Is it all konqueror's fault? And yes, that it what I get when I run automake as root.

Anyone know how I may fix this?

---

### Post by Absurd on 2006-12-14
ok, figured it out. It was the file system (FAT32). Just had to move my programming folder to my /home/username/ directory which is EXT3.

---

