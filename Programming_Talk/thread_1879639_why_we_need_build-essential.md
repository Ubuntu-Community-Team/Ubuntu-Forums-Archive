---
title: "why we need build-essential"
date: 2011-11-12
forum: Programming Talk
---

### Post by lalitpratap on 2011-11-12
Can anyone explain me what is the significance of **build-essential** package in any **Linux** system?  Why do we really need it?

---

### Post by Bachstelze on 2011-11-12
For starters, build-essential is only a Debian thing, it does not exist on all Linux systems. And no, you do not *really* need it, it is just a convenient way to install a basic C/C++ development environment.

---

### Post by MadCow108 on 2011-11-12
it is the package that is installed on every debian build daemon (or unconditionally gets installed when starting a build).
So packages do not need to explicitly build depend on tools that are required to build pretty much everything, like libc, make or dpkg tools.

as mentioned you do not need to install it. Especially regular developers usually do not need dpkg-dev it pulls in which provides packaging tools.
It is still recommended to beginners as it is a simple way to install the basic environment to get started with c programming

---

### Post by 3Miro on 2011-11-12
It is not installed by default, therefore you don't really need it. Every distro that I have seen has a build-essential or some equivalent to it. The purpose of such package is to allow users that want to do development to easily get the most basic tolls like gcc and gnu-make. Without such package one would need to keep a list "I need to install gcc and make and some libs ... ", build essentials is a shortcut.

---

