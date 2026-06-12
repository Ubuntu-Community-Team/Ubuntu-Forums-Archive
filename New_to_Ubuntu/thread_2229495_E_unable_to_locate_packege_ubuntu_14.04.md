---
title: "E: unable to locate packege ubuntu 14.04"
date: 2014-06-13
forum: New to Ubuntu
---

### Post by jahanzeb on 2014-06-13
I have installed ubuntu 14.04 in my dell inspiron n5010 and i faced problem of missing/disabbling network-manager. i faced this issue in 13.10 as well now i tried couple of reinstallations first i tried installing 14.04 amd64 than i tried 14.04 amd64+mac and now i again installed 14.04 amd64 now i am unable to get update and unable to install any application network-manager issue is still exists!


cat /etc/apt/sources.list

```

# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64+mac (20140417)]/ trusty main restricted
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-security main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-security main restricted
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-security universe
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-security universe
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-security multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
```

---

### Post by mörgæs on 2014-06-13
Hi, welcome to the fora.
Do you get access using a wired internet connection?

---

