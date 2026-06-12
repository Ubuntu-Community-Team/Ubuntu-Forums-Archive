---
title: "Installing Wah!Cade?"
date: 2006-04-12
forum: Repositories &amp; Backports
---

### Post by tore- on 2006-04-12
Im trying to install wah!cade from [http://www.anti-particle.com/wahcade.shtml](http://www.anti-particle.com/wahcade.shtml)

Since this program isnt in the reps. i need to install all of the deps. by hand.

But I cant seem to find pygtk2, or elementtree?

My source.list:
```
deb-src http://no.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
deb-src http://no.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```


Im comming from BSD on server side so im not to familiar with how Ubuntu works.

It should be noted that i use XUbuntu with xfce4, nothing installed for what i know.

Thanks alot.

---

