---
title: "Synaptic verification failed"
date: 2006-07-26
forum: Repositories &amp; Backports
---

### Post by dhawk312 on 2006-07-26
Can anyone please help me?  Synaptic keeps giving me the following return no matter what package I try to install:
E: /var/cache/apt/archives/ABC.deb: Verification on package /var/cache/apt/archives/ABC.deb failed!

None of my repos are returning any errors and this is all that comes back. If I use apt-get I get the following return no matter what package I try to install:
dpkg: error processing /var/cache/apt/archives/ABC.deb (--unpack):
 Verification on package /var/cache/apt/archives/ABC.deb failed!
Errors were encountered while processing:
 /var/cache/apt/archives/ABC.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have been using Dapper since flight 1 and this is my first problem that I've encountered.

---

### Post by jordilin on 2006-07-26
Give us your sources.list, just in case to see if there's some mistake. I would try doing
```
apt-get update
```
and then trying to install some package.

---

### Post by dhawk312 on 2006-07-26
after doing apt-get and rebooting i still get the same outputs from apt-get and synaptic. that being said heres my enitre sources list (ive been using this exact sources list for about a month and today is the first time this has happened):

####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse



deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe restricted main

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse




# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse




# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse





##############################
### Automatix Repositories ###
##############################

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

## created by automatixrepo2
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main
# deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./
deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) dapper-seveas all
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
# deb [http://ubuntu.geole.de/](http://ubuntu.geole.de/) dapper universe multiverse
deb [http://gauvain.tuxfamily.org/repos](http://gauvain.tuxfamily.org/repos) dapper contrib
deb-src [http://gauvain.tuxfamily.org/repos](http://gauvain.tuxfamily.org/repos) dapper contrib
deb [http://apt.alittletooquiet.net/staging](http://apt.alittletooquiet.net/staging) dapper main
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

