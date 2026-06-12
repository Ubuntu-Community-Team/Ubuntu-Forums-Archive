---
title: "need advice on my sources.list"
date: 2006-01-09
forum: Repositories &amp; Backports
---

### Post by generalleoff on 2006-01-09
My list.conf looks like this right now.

```
## Ubuntu Breezy CD-ROM (5.10)
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Ubuntu Breezy (5.10)
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse

## Mirrormax Breezy (5.10)
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main restricted universe multiverse

## Marillat Sarge
deb ftp://ftp.nerim.net/debian-marillat/ sarge main
deb-src ftp://ftp.nerim.net/debian-marillat/ sarge main

## Penguin Liberation Front
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## Freecontrib
deb http://packages.freecontrib.org/ubuntu/freecontrib/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/freecontrib/ breezy free non-free


```

I'm not having any problems with it but I would like some advice.

Like is Marillat pretty much obsolete right now and rendered useless by freecontrib and plf? I don't much like installing none Ubuntu specific packages and I only use it for movie and music related things. It's been there seance the first version of Ubuntu and if it is no longer needed I would love to kill it off.

Is there even a difference between freecontrib and plf and should I kill one off? I don't see a difference.

What exactly is extras-staging and backports-staging and is it safe?

Any other suggested cleanups or additions?

---

### Post by Leif on 2006-01-09
I'd say get rid of marillat. I don't know about freecontrib. The -staging repos are where packages get tested first, so if you're not looking to help test them, don't use these.

---

