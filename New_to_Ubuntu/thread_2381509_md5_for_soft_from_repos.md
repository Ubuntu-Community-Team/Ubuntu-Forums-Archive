---
title: "md5 for soft from repos"
date: 2018-01-01
forum: New to Ubuntu
---

### Post by fund_raiser on 2018-01-01
Hi,

Before installing a program from repositories we can check its MD5 hash by using *apt-cache show . *So how to use md5sum after installing a program from repos?

I know we can use md5sum to check iso files after downloading them, but what about checking installed software, do we actually do it for installed software?

thx

PS
BTW when I type *dpkg -l md5sum* it doesn't find anything. Why doesn't it?

---

### Post by vasa1 on 2018-01-01
I've heard of *debsums* which is available from the repos. It maybe useful.

---

### Post by TheFu on 2018-01-01
Try
$ dpkg -S md5

The name of the package doesn't match 'md5sum' according to the manpage.

You could create your own hash for every file on a system and store them offline for comparison later.  Not really difficult. It is a nice, simple, beginning script level exercise.

APT validates each package signature, automatically. No need to do it manually, unless you download a package from outside a repository.  This is why using a trusted repository/PPA is so very important.

---

### Post by oldos2er on 2018-01-02
> when I type *dpkg -l md5sum* it doesn't find anything. Why doesn't it?

Because there's no package named "md5sum." md5sum is part of the coreutils package which I believe is installed by default on all versions of Ubuntu.

---

