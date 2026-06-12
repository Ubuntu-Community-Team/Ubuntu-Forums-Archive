---
title: "Edgy - Could not download all repository indexes"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by col_b on 2008-11-05
Hi,

I've just installed Edgy on an old laptop, 256 mg ram, 20gb hd.  I tried later incarnations of ubuntu, but the machine didn't like them, so I stuck with Edgy which I've used in the past.

I'm trying to install some more apps, but seem to be having great difficulty.  I've searched and searched on this, but haven't been able to figure out a solution.

So the scenario is:  I go to add/remove apps.  I get a window saying that the list of available apps is out of date, and it asks me to reload them.  When I go to reload them, I get the error 'Could not download all repository indexes.'  This is the list of errors:

===========================================================
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
===============================================================

I also have the error that programs cannot be installed on your computer type (i386).

I've tried modifying sources.list.  I've tried changing the Software sources server.  All to no avail.  My sources.list file is:

=============================================================
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe
=======================================================================

I can't figure out the solution at all.  How do I get it to download the repository indexes, and how do I get rid of the wrong computer type error?

Many thanks in advance for any help.  

Cheers,
Col

---

### Post by hyper_ch on 2008-11-05
edgy is out of support if I'm not mistaken - so the repos were moved (they are somewhere else now, don't ask me where).

Either change your repos accordingly or upgrade to a supported version.

---

### Post by col_b on 2008-11-05
Ahah, ok, so does anyone know where they've been moved to?

Cheers,
Colin

---

### Post by hyper_ch on 2008-11-05
I saw a post on the forum abuot that... but you should rather upgrade as there are no security fixes anymore released for it.

---

### Post by drs305 on 2008-11-05
Here is a link to the old repositories, edgy included:
[http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

The edgy repositories: [http://old-releases.ubuntu.com/ubuntu/dists/]("http://old-releases.ubuntu.com/ubuntu/dists/")


Here are some of the possible entries for sources.list. You can explore the directories to see what is available:
```

deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse

```

---

### Post by philinux on 2008-11-05
Old releases website.

[http://old-releases.ubuntu.com./releases/](http://old-releases.ubuntu.com./releases/)

---

