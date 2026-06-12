---
title: "cant get in touch with http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release."
date: 2006-06-14
forum: Repositories &amp; Backports
---

### Post by melb steven on 2006-06-14
Hi all,

I get this

[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not connect to archive.ubuntu.com:80 (85.133.25.7), connection timed out

In the synaptic 

"Could not download all repository indexes" warning box.

Yet I can go to [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg) in firefox. I can ping 85.133.25.7

root@humanoid4:~# ping 85.133.25.7
PING 85.133.25.7 (85.133.25.7) 56(84) bytes of data.
64 bytes from 85.133.25.7: icmp_seq=1 ttl=43 time=313 ms
64 bytes from 85.133.25.7: icmp_seq=2 ttl=43 time=312 ms
64 bytes from 85.133.25.7: icmp_seq=3 ttl=43 time=313 ms
64 bytes from 85.133.25.7: icmp_seq=4 ttl=43 time=313 ms
64 bytes from 85.133.25.7: icmp_seq=5 ttl=43 time=313 ms

Any ideas?

I was trying to get lippng-dev to compile mplayer with the gui. I have hand edited the rep list but I restored it to

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by melb steven on 2006-06-14
Hmm,

It looks like I need a key??

Is this the solution?

gpg --keyserver subkeys.pgp.net --recv-keys ??????????
gpg --export --armor ??????? | sudo apt-key add -

If so how do I find the number I need?

---

