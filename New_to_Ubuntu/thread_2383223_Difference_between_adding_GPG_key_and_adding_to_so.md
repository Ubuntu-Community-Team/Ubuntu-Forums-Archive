---
title: "Difference between adding GPG key and adding to sources.list"
date: 2018-01-22
forum: New to Ubuntu
---

### Post by rwalkerIII on 2018-01-22
Is there a difference between adding a GPG key (apt-key add) vs adding a site to sources.list?  That is, do the achieve the same thing or are two different things entirely?

---

### Post by deadflowr on 2018-01-22
Two different things, but one is required for the other to work.
The key is required to authenticate the packages from the sources.list entry.

---

