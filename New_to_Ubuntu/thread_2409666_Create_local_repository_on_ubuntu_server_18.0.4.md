---
title: "Create local repository on ubuntu server 18.0.4"
date: 2019-01-05
forum: New to Ubuntu
---

### Post by omid5ive on 2019-01-05
hi
my server 18.0.4  has no internet connection and i can't get my package with apt-get from internet.
how can i create local repository that when i want to apt-get i can refer to this repository not internet

---

### Post by CatKiller on 2019-01-05
apt-mirror is the part that does most of the work. Then you'll need something to make that repository available: ftp or http are both common. Then you simply use the sources.list to point to your mirror rather than the Internet ones.

---

### Post by oldrocker99 on 2019-01-05
Are you using wifi, or Ethernet?

---

