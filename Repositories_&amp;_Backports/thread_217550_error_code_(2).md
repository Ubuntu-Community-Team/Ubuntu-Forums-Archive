---
title: "error code (2)?"
date: 2006-07-17
forum: Repositories &amp; Backports
---

### Post by Uncle Spellbinder on 2006-07-17
Checked for updates last night and again this morning. Each time I got this:
```
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.bz2: Sub-process bzip2 returned an error code (2)
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.bz2: Sub-process bzip2 returned an error code (2)
```

Here's my Sources.list:
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://www.beerorkid.com/automatix/apt dapper main

deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free
```

Ideas?

---

