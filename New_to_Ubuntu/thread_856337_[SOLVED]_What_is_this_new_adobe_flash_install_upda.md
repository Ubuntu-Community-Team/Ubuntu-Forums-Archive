---
title: "[SOLVED] What is this new adobe flash install update today?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by T2manner on 2008-07-11
I just updated my computer and the update today was some Adobe Flash Player Installer. 18Kbs.
but I thought I already had Flash player?

---

### Post by philinux on 2008-07-11
More than likely a bug fix.

---

### Post by shad0w_walker on 2008-07-11
It's exactly what it says on the tin. It's just an update. In all likelihood, a bugfix or security update.

---

### Post by DariusS on 2008-07-11
so long as you don't have any backports or other unsupported/bleeding edge repos, updates should be ok to install. they are usually just bug fixes and the like.

---

### Post by Foster Grant on 2008-07-11
Changelog as follows from Update Manager:

```
Version 10.0.1.218+10.0.0.525ubuntu1~hardy1: 

  * Automated backport upload; no source changes.


Version 10.0.1.218+10.0.0.525ubuntu1: 

  * New upstream beta.
  * debian/config:
    debian/postinst:  Update md5sums, filenames, and paths.
  * debian/control:  Demote versioned dependency for libflashsupport|
    libasound2-plugins to recommends.


Version 10.0.1.218ubuntu1: 

  * New upstream beta fixes many crashers (most significantly
    LP: #192888).
  * debian/config:
    debian/postinst:  Update md5sums, filenames, and paths.  Remove
    debugging bits (LP: #176226).
  * debian/control:  Readd versioned dependency for libflashsupport|
    libasound2-plugins to play nicely with either PulseAudio config
    while preserving OSSv4 users' ability to have audible "shiny"
    (LP: #206307, #186726, #183943, #151849).

```

---

### Post by philinux on 2008-07-11
> **DariusS said:**
> so long as you don't have any backports or other unsupported/bleeding edge repos, updates should be ok to install. they are usually just bug fixes and the like.

Please read this regarding backports.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

