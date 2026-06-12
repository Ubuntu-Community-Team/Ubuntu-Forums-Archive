---
title: "Not able to install apps from Software Center(Untrusted packages)"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by sivakumar-sakam on 2014-06-02
Not able to install apps from Software Center, getting **Requires installation of untrusted packages**(PFA snapshot)
This is the out put for command **sudo apt-get update **
```
Reading package lists... DoneW: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://archive.canonical.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: https://download.01.org trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
W: GPG error: http://archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 241FE6973B765FAE

```

---

### Post by stalkingwolf on 2014-06-02
try installing from synaptic package manager.  you may also have to update your repositories.

---

### Post by su:bhatta on 2014-06-02
Please give the output of :
```
cat /etc/apt/sources.list
```

---

### Post by sivakumar-sakam on 2014-06-02
Thanks for your replays..
I have update from 13.10 to 14.04
Out put of above command is
```
## deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1)]/ saucy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu trusty main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu trusty universe
deb-src http://archive.ubuntu.com/ubuntu trusty universe
deb http://archive.ubuntu.com/ubuntu trusty-updates universe
deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu trusty multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb http://archive.ubuntu.com/ubuntu trusty-security universe
deb-src http://archive.ubuntu.com/ubuntu trusty-security universe
deb http://archive.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu saucy partner
deb-src http://archive.canonical.com/ubuntu saucy partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://archive.canonical.com/ trusty partner
deb-src http://archive.canonical.com/ trusty partner
```

---

