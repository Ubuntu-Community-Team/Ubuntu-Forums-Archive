---
title: "Package Installation"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by deepraj2 on 2013-08-18
Installing Sundials packge in ubuntu..

sudo: ./configure: command not found

Why is this happening, every time I try to execute the configure file in the sundial directory?

---

### Post by GwL3eNC on 2013-08-18
Hmm,

i assume you have downloaded some tar.gz archiv containing some application
sources. Most times there is a readme inculded where you can find any information
about how to compilate and which requirements are needed.

You need

sudo apt-get install build-essential

installed. Then you need to be in the foder containing the config file and try
again. But these are all assumptions, it would be better to take a look at the
readme.

---

### Post by deepraj2 on 2013-08-19
[ATTACH=CONFIG]245477[/ATTACH]

This is what's happening !!

---

### Post by Cheesemill on 2013-08-19
Is your build directory on an NTFS drive by any chance?

Automatically mounted NTFS partitions are mounted with the noexec option, meaning that you can't execute scripts on them.

Try building Sundial from somewhere inside your home folder instead.

---

