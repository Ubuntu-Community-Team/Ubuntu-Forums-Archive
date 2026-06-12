---
title: "mozilla-firefox-locale-en-gb problem"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by potayto9 on 2008-05-02
I can't install anything on my update manager (resently switched to hardy). when i do I get:
/var/cache/apt/archives/libldap-2.4-2_2.4.7-6ubuntu4.1_i386.deb: files list file for package `mozilla-firefox-locale-en-gb' is missing final newline
and i can't remove it either.

---

### Post by Oldsoldier2003 on 2008-05-02
> **potayto9 said:**
> I can't install anything on my update manager (resently switched to hardy). when i do I get:
/var/cache/apt/archives/libldap-2.4-2_2.4.7-6ubuntu4.1_i386.deb: files list file for package `mozilla-firefox-locale-en-gb' is missing final newline
and i can't remove it either.

try 
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by potayto9 on 2008-05-02
tried sudo apt-get clean
response:
Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)

---

### Post by potayto9 on 2008-05-05
Im still not able to install any updates because of this error.
Does anyone know how i can fix it?

---

