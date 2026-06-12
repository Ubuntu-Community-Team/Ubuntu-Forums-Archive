---
title: "backportpackage set default gpg key"
date: 2012-03-12
forum: Packaging and Compiling Programs
---

### Post by eyelessfade on 2012-03-12
When I try to backport a package with
```
backportpackage -s oneiric -d lucid package -u ppa:myppa/ppa
```
It fails with: <username@computer>: secret key not available

How can I specify which gpg key to use. I've already tried with export GPGKEY

---

### Post by MadCow108 on 2012-03-12
put DEBSIGN_KEYID=keyid in ~/.devscripts

---

### Post by eyelessfade on 2012-03-13
> **MadCow108 said:**
> put DEBSIGN_KEYID=keyid in ~/.devscripts

Thanks that worked great.

---

