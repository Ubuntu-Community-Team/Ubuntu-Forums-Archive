---
title: "Cant acces Repository"
date: 2006-01-05
forum: Repositories &amp; Backports
---

### Post by pallaire on 2006-01-05
Since this morning I am not able to acces my repo anymore.


apt-get update output : 
```
apt-get update
Err http://security.ubuntu.com breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://archive.ubuntu.com breezy Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://archive.ubuntu.com breezy-updates Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://archive.ubuntu.com breezy-backports Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```


sources.list :
```
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
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
## deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secundairy repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secundairy are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

```

---

### Post by hobbit1983 on 2006-01-05
It looks as if synaptic is having problems resolving DNS names (i.e [www.domain.com](www.domain.com) to an IP addressxxx.xxx.xxx.xxx)

Try using the network tools to see if you can ping an address.

May be a network problem.  You could try refreshing your DNS list.  although I'm not tooo sure how to do that.

if it is still happening after an hour or so and your interent connection is fine then perhapes ask again

---

### Post by pallaire on 2006-01-05
That's is, my DNS was wrong :) 

Fixed ! Thanks

---

