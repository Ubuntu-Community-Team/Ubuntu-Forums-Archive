---
title: "Using source files from a later ubuntu version to compile deb package ?"
date: 2012-02-15
forum: Packaging and Compiling Programs
---

### Post by interzoneuk on 2012-02-15
Hi.

Can someone help me understand the best/easiest of creating an updated deb package? - I am a package maintainer for AUR arch packages and I frequently build RPM's - I have just never understood the debian way... 

Hi.

I am struggling to find a quick and easy way to easily update debian packages.....

With Arch Linux it's generally just a case of simply change the version number in the PKGBUILD - that's it - usually takes about 5 seconds of fiddling.

With RPM's I usually get a SRPM from a higher version - i.e a Fedora 16 SRC.RPM on a Fedora 15 machine - usually all that is involves is editing the .spec file, taking out a few patches and the change in the 'BuildRequires' versions.

With Deb packages i have been using methods outlined

[https://help.ubuntu.com/community/UpdatingADeb](https://help.ubuntu.com/community/UpdatingADeb)

However this is far from easy/simple.... As you copy the debian folder from a previous version (rather than the opposite way round with RPM) you end up having to spend ages removing/editing patches to get it to compile correctly.

I guess my question is :-

Can you get the source files from a later version of ubuntu/debian and compile it on the present version.

i.e :-

Could I use the source files for Ubuntu 11.10 and use them to compile a deb on Ubuntu 10.04 ?

i.e :-

the equivalent of apt-get source php5 on Ubuntu 11.10 - but on Ubuntu 10.04 ?

This would make the compile easier (as the patches, etc are based on the later version)

Why can't they make a system as simple as Arch ? Why is debian package building so un-user friendly ?

Any help would be welcomed.

---

### Post by Bachstelze on 2012-02-15
> **interzoneuk said:**
> 
the equivalent of apt-get source php5 on Ubuntu 11.10 - but on Ubuntu 10.04 ?


```
pull-lp-source php5 oneiric
```

---

### Post by eyelessfade on 2012-02-24
[Prevu]("https://wiki.ubuntu.com/Prevu") is a great tool for automatic backporting of packages. It even creates local repo.

---

