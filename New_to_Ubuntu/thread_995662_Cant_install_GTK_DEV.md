---
title: "Cant install GTK DEV"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by rraj.be on 2008-11-28
Any help to install this please

```
raj@raj-desktop:~$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
                 Depends: libglib2.0-dev (>= 2.12.0) but it is not going to be installed
                 Depends: libgtk2.0-0 (= 2.12.9-3ubuntu2) but 2.12.9-3ubuntu4 is to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
E: Broken packages
raj@raj-desktop:~$
```

---

### Post by adult swim on 2008-11-28
do you have the universe and muliverse repositories enabled in synaptic package manager?

---

### Post by rraj.be on 2008-11-28
Yes .. 

all are enabled

---

### Post by adult swim on 2008-11-28
post your sources.list

---

### Post by rraj.be on 2008-11-28
[http://pastebin.com/me279719](http://pastebin.com/me279719)

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[APTonCD for ubuntu hardy - i386 (2008-08-27 21:47) DVD1]/ /

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner





deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe main multiverse restricted #Added by software-properties


deb http://www.remastersys.klikit-linux.com/repository/ remastersys/
deb http://update.eeepc.asus.com/p701/ p701 main
deb http://update.eeepc.asus.com/p701/en/ p701 main
```

---

### Post by adult swim on 2008-11-28
sorry for the delay!  make sure that under the updates tab you have the hardy recommended updates and you may need to enable the backports to get the newer versions of the dependencies.

---

