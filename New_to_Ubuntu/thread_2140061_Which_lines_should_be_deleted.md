---
title: "Which lines should be deleted?"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by TimEnid on 2013-04-28
I did an update and got
```
W: Failed to fetch http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

```


this is what i get when i sudo gedit /etc/apt/sources.list



```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu raring-security main restricted
deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
deb http://security.ubuntu.com/ubuntu raring-security universe
deb-src http://security.ubuntu.com/ubuntu raring-security universe
deb http://security.ubuntu.com/ubuntu raring-security multiverse
deb-src http://security.ubuntu.com/ubuntu raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main

```

Thanks

---

### Post by prodigy_ on 2013-04-28
There's also **/etc/apt/sources.list.d**.

---

### Post by coldcritter64 on 2013-04-28
> **TimEnid said:**
> I did an update and got
```
W: Failed to fetch http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

```


this is what i get when i sudo gedit /etc/apt/sources.list



```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu raring-security main restricted
deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
deb http://security.ubuntu.com/ubuntu raring-security universe
deb-src http://security.ubuntu.com/ubuntu raring-security universe
deb http://security.ubuntu.com/ubuntu raring-security multiverse
deb-src http://security.ubuntu.com/ubuntu raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main

```

Thanks
In Unity, open Dash search for "Software Sources" open it, goto the Other Software Tab and detick the ppa and close Software sources. Run your update. You can also add or remove entries here without manually editting system files. Cheers

---

### Post by TimEnid on 2013-04-28
> **prodigy_ said:**
> There's also **/etc/apt/sources.list.d**.
that one is empty

---

### Post by TimEnid on 2013-04-28
that worked. thanks.

---

