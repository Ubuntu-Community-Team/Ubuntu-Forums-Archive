---
title: "Pbuilder --create fails"
date: 2009-09-09
forum: Packaging and Compiling Programs
---

### Post by korin43 on 2009-09-09
I have pbuilder installed but running pbuilder --create does this:

```
brendan@brendan-desktop:~$ sudo pbuilder --create
W: /home/brendan/.pbuilderrc does not exist
Distribution is jaunty.
Building the build environment
 -> running debootstrap
/usr/sbin/debootstrap
I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
W: Failure trying to run: chroot /var/cache/pbuilder/build/23651/. mount -t proc proc /proc
pbuilder: debootstrap failed
 -> Aborting with an error
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//23651 and its subdirectories
```

I've never had this problem before but I recently reinstall Ubuntu.

---

