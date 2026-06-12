---
title: "libc6 update weirdness"
date: 2005-03-23
forum: Repositories &amp; Backports
---

### Post by Technoviking on 2005-03-23
apt-get dist-upgrade wants to do the following.

root@pheonix:/home/dbasinge # apt-get dist-upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
Calculating Upgrade... Done
The following packages will be REMOVED:
  libc6-i686 ubuntu-base
The following packages will be upgraded:
  libc6 libc6-dev locales

Is removing ubuntu-base bad?

Mike

---

### Post by jdong on 2005-03-23
I just did it, and I'm not getting any trouble ;)

---

### Post by ubuntu_demon on 2005-03-23
[QUOTE=jdong]I just did it, and I'm not getting any trouble ;)[/QUOTE]
  For people who haven't already dist-upgraded today :

just do an upgrade instead of a dist-upgrade :

sudo apt-get upgrade gives :
.......
The following packages have been kept back::
libc6 libc6-dev libc6-i686 locales
.......

---

### Post by oracledarren on 2005-03-23
All the correct files are in the repo now  :)

---

