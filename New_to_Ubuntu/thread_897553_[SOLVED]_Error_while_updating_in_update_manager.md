---
title: "[SOLVED] Error while updating in update manager"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by immy123 on 2008-08-22
I tried to update using the ubuntu manager in GUI, but it gave the following errors:

--------------------------------------------------------------------------
W: Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release.gpg](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release.gpg)  Could not resolve 'ubuntu-backports.mirrormax.net'

W: Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/i18n/Translation-en_US.bz2](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/i18n/Translation-en_US.bz2)  Could not resolve 'ubuntu-backports.mirrormax.net'

W: Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/i18n/Translation-en_US.bz2](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/i18n/Translation-en_US.bz2)  Could not resolve 'ubuntu-backports.mirrormax.net'

W: Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/i18n/Translation-en_US.bz2](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'ubuntu-backports.mirrormax.net'

W: Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/i18n/Translation-en_US.bz2](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'ubuntu-backports.mirrormax.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.
--------------------------------------------------------------------------


Anyway to fix this error? :confused:

Thanks in advance.

---

### Post by glennric on 2008-08-22
The server ubuntu-backports.mirrormax.net does not exist or is down.  Try disabling that source, and it should work.

---

### Post by Seisen on 2008-08-22
Post your source list

```
cat /etc/apt/sources.list
```

---

### Post by immy123 on 2008-08-23
I typed in the code in the terminal and the output was:

-------------------------------------------------------------------------------------
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
-------------------------------------------------------------------------------------

---

### Post by immy123 on 2008-08-23
How can I disable this? Sorry for asking, but I'm not that familiar with these stuff.

---

### Post by immy123 on 2008-08-23
I figured it out. Unchecked it in the software sources. Now, the update manager is working fine. Thanks a lot.

---

### Post by gjoellee on 2008-08-23
remove

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

(its on the bottom)

---

