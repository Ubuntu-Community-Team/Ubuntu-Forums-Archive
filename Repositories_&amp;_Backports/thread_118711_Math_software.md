---
title: "Math software"
date: 2006-01-17
forum: Repositories &amp; Backports
---

### Post by madskaddie on 2006-01-17
Hy, 
 today I tried to install some math software but I didn't made it to the end. I'm using breezy and there is always a missing package. The software I tried:

*tilp: The package seems corrupted and I tried to compile from source...but the libusb-dev package is missing [unavaible]. libgtk2.0-dev is also unavaible

*scilab and maxima there are also some unavaible packages...

I'm very sad with this. I was a Debian testing user and the missing of k3b for a long time took me  to change distro. Now...this...:( 

hope you considerer to solve this soon...

____
my sources.list:

 deb [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

---

### Post by André on 2006-01-17
Hi madskaddie,

may it be that you are missing some sources?? You do not have the "normal" sources included like main and restricted as far as i can tell. Maybe try:

```

deb http://pt.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

```

See if this works. Greetings
André

---

### Post by madskaddie on 2006-01-18
The problem should be that because I installed automatix and it solved. 

Thanks.

---

