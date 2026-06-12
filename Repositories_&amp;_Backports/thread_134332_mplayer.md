---
title: "mplayer"
date: 2006-02-21
forum: Repositories &amp; Backports
---

### Post by andyjoe1 on 2006-02-21
iam having problems getting mplayer to download it keeps telling me that there is a missing link

---

### Post by Sweet on 2006-03-02
[QUOTE=andyjoe1]iam having problems getting mplayer to download it keeps telling me that there is a missing link[/QUOTE]


Im getting the same problem trying to install mozilla-mplayer, mplayer has disappeared, I think some of the repos are down?!

```
mozilla-mplayer:
 Depends: mplayer (>=1.0-pre5) but it is not installable or
 	mplayer-custom (>=1.0-pre5) but it is not installable or
 	mplayer-386 (>=1.0-pre5) but it is not installable or
 	mplayer-586 (>=1.0-pre5) but it is not installable or
 	mplayer-686 (>=1.0-pre5) but it is not installable or
 	mplayer-k6 (>=1.0-pre5) but it is not installable or
 	mplayer-k7 (>=1.0-pre5) but it is not installable or
 	mplayer-powerpc (>=1.0-pre5) but it is not installable or
 	mplayer-g4 (>=1.0-pre5) but it is not installable or
 	mplayer-amd64 (>=1.0-pre5) but it is not installable or
 	mplayer-nogui (>=1.0-pre5) but it is not installable

```

Heres my sources.list, any ideas?

Thanks in advance :) 

```
## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu breezy universe
deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

#Java
deb http://ubuntu.tower-net.de/ubuntu/ breezy java

##############################
## ubuntuforums added sources:
##############################

#deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

#deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
#deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## breezy-extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

## plf primary repo - DOWN????????????
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
##deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
##deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secundairy repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secundairy are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

```

---

### Post by Aewheros on 2006-03-02
You are lacking multiverse, you only have the backport one.

Add:
```
deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse
```
Or uncomment a multiverse (without "-backport" or "-security") you already have.

---

### Post by Sweet on 2006-03-02
Ah, you legend, don't know how i missed that.

Thanks a lot :D

---

