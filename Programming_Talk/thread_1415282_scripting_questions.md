---
title: "scripting questions"
date: 2010-02-24
forum: Programming Talk
---

### Post by Joe Ker1086 on 2010-02-24
i know this isn't really a 'programming' question persay, but does anyone know of a good scripting tutorial. looking to get into building packages, building iso images for live cds, ect.... any advice is apriciated

---

### Post by Joe Ker1086 on 2010-02-24
bump

---

### Post by smmalmansoori on 2010-02-24
When you say building packages do you mean a ".deb" package? if so then here is a link, which is btw a sticky in the Programming Talk section: [[COLOR=RoyalBlue]_click here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=910717")

---

### Post by Joe Ker1086 on 2010-02-24
that is helpful but i was more or less looking for a more general tutorial.....lets say i want to build packages on ubuntu....i would by default be able to build packages for any debian derived linux....but what if i then want to build packages for arch linux... or for fedora..... would i follow the same procedures? or would they be much different?

---

### Post by smmalmansoori on 2010-02-24
For any distribution first check out what is the package system used, for example fedora uses rpm and yum as opposed to ubuntu's deb. Next you'd have to check out how that certain package is built, for example yum [_[COLOR=RoyalBlue]here[/COLOR]_]("http://www.charlescurley.com/yum/repository.html"), and rpm [[COLOR=RoyalBlue]_here_[/COLOR]]("http://fedoraproject.org/wiki/How_to_create_an_RPM_package").

---

### Post by Joe Ker1086 on 2010-02-24
what about tarballs? cant they be installed on any linux version?

---

### Post by smmalmansoori on 2010-02-24
tarballs contain the source code which can compile on any distribution, any CPU architecture, and any OS.

---

### Post by Joe Ker1086 on 2010-02-25
so how do you make tarballs?

---

### Post by Barrucadu on 2010-02-25
Have a look at the `tar` command.

---

### Post by benj1 on 2010-02-25
> **Barrucadu said:**
> Have a look at the `tar` command.

its alot more complicated than that, you need to look at autoconf and automake, which in my opinion are complete pains in the backside.

if youre wanting to package a python (and i think perl) script, they have their own packaging tools that are alot easier to use.

---

