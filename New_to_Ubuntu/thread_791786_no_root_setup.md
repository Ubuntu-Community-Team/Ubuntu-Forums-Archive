---
title: "no root setup?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by DMinard on 2008-05-12
during the install of ubuntu i was never asked to create a root account/password. is this common practice for ubuntu or did i miss something during the install process? this really make installation of things quite impossible in general.

---

### Post by Monicker on 2008-05-12
Ubuntu is different from other distros in that respect.  The root account exists, but users are encouraged to use sudo to perform administrative tasks.

Take a look here:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by dje on 2008-05-12
A quick search on google would have found you an answer like [this]("https://help.ubuntu.com/community/RootSudo")

dje

EDIT: Monicker beat me to it!

---

### Post by inportb on 2008-05-12
Don't worry, it's Ubuntu. You don't have a root password by default, so you can't actually login to root (and potentially do bad stuff to yourself). Instead, you use sudo.

If you actually do need to login as root, use set a root password by "sudo passwd"

EDIT: we're a friendly community, eh? =D

---

### Post by DMinard on 2008-05-12
thanx a bunch fellas...much appreciated

---

