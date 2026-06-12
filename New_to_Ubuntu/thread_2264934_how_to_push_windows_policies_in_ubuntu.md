---
title: "how to push windows policies in ubuntu"
date: 2015-02-11
forum: New to Ubuntu
---

### Post by ramesh6 on 2015-02-11
hi

I have joined ubuntu system to windows domain but m not able to apply policies same as in windows.

pls help me

---

### Post by sandyd on 2015-02-11
> **ramesh6 said:**
> hi

I have joined ubuntu system to windows domain but m not able to apply policies same as in windows.

pls help me

Hi, Ubuntu does not support GP due to the fact that GP is based on Windows Objects. You can do server-side policies that depend on LDAP as those are enforced on the server though.

There are also a number of commercial solutions such as [Centrify DirectControl ]("http://www.centrify.com/products/server-suite/") that will convert most things set in GP to something that will work in Linux.

---

