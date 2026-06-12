---
title: "Have I Broken Apt-Get?"
date: 2006-02-03
forum: Repositories &amp; Backports
---

### Post by mrgnash on 2006-02-03
Ever since I used the automatic sources list generator (source-o-matic), I have been encountering a lot of errors when using anything to do with apt-get. For instance, when I run apt-get install update, I get:

```
apt-get install update
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package update

```

So I tried apt-get update, but that doesn't seem to fix the problem, nor does apt-get -f install.

My current sources list is:

```
#standard 5.10
deb http://it.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu   breezy-security main restricted universe multiverse

#Extras 5.10
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main
deb http://ubuntu-backports.mirrormax.net/ breezy-extras restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-extras universe
deb http://ubuntu-backports.mirrormax.net/ breezy-extras multiverse

#dapper 6.04
deb http://it.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse 

#other applications

#wine
deb http://wine.sourceforge.net/apt/ binary/

#kde
deb http://kubuntu.org/packages/kde35 breezy main

#openoffice
deb http://people.ubuntu.com/~doko/OOo2 ./
deb http://apt.bxlug.be ooo/ # packages additionels pour openoffice

#PLF
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

#opera browser
deb http://deb.opera.com/opera/ etch non-free

#Amarok
deb http://kubuntu.org/packages/amarok-1.3.7 breezy main

#Doomsday games
deb http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse

```

Any ideas?

---

### Post by Adrian on 2006-02-03
You are using obsolete repositories. You can find working ones here:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by mushroom on 2006-02-03
Plus, you're trying to install a package that doesn't exist.

---

