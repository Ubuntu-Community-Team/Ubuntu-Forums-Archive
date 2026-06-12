---
title: "Breezy source list in Dapper?"
date: 2006-05-14
forum: Repositories &amp; Backports
---

### Post by pkbarber on 2006-05-14
My synaptic package manager quit on me yesterday. 
```
E: Malformed line 49 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

```

So I went and looked in the list
```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://security.ubuntu.com/ubuntu breezy-security multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse

## PLF repositories, contains litigious packages, see http://wiki.ubuntu-fr.org/doc/plf

## Freecontrib, funny packages by the Ubuntu PLF Team
deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ 

```

I tried to cut and paste the correct list from the forums to the file but its read only.
Why would I have all Breezy repostitories on a Dapper box? Thoughts?

---

### Post by aysiu on 2006-05-15
I don't know where you got that Breezy list from... did you use Automatix, maybe?

You can easily get a Dapper list back, though. Just paste these commands into the terminal: ```
wget -c http://www.psychocats.net/ubuntu/sources.list
sudo mv /etc/apt/sources.list /etc/apt/breezy.list
sudo mv sources.list /etc/apt/sources.list
```

---

### Post by pkbarber on 2006-05-15
I did not use automatrix but I did use another script along the same line...
However after some terminal work using vi and gedit i got the right list back in.  There were a TON of updates.  Thanks for your advice.
PK

---

