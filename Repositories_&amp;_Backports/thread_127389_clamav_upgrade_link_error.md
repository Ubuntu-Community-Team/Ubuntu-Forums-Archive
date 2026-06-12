---
title: "clamav upgrade link error?"
date: 2006-02-08
forum: Repositories &amp; Backports
---

### Post by stock99 on 2006-02-08
HI,
I try to follow the instructions provided by clamav wbsite on upgrading the antivirus ([http://www.clamav.net/binary.html#pagestart)](http://www.clamav.net/binary.html#pagestart)). 

But i got the following link after i include link required in source.lst


-------------------------
W: GPG error: [http://downloads.planetmirror.com](http://downloads.planetmirror.com) sarge/volatile Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7EF7FFF4276981F4
W: You may want to run apt-get update to correct these problems
-------------------------


Can anyone help me to fix it? Because of it i can't install/update clamav to latest version. The version of linux i use is ubuntu 5.10. This is however NOT a problem for my old debian (upgraded to sarge from woody).


btw bellow is my source.lst 

===========================





deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted

deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe

deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://downloads.planetmirror.com/pub/debian-volatile](http://downloads.planetmirror.com/pub/debian-volatile) sarge/volatile main
deb-src [http://downloads.planetmirror.com/pub/debian-volatile](http://downloads.planetmirror.com/pub/debian-volatile) sarge/volatile main

---

