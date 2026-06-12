---
title: "error message &quot;The repository may no longer...&quot;"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by konos on 2008-08-21
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


   Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)

---

### Post by t0p on 2008-08-21
The problem is likely in your list of repos, in /etc/apt/sources.list

If you want to post that file here we can have a look at it.

---

### Post by konos on 2008-08-21
thenx for the replay, but i do not know how to post the file.. (i have found a folder "sources.list.d" a file "sources.list" a file "sources.list.save" a file sources.list-"
thenx again

---

### Post by konos on 2008-08-21
is this the correct file??


# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by t0p on 2008-08-21
That is the correct file. Nothing jumps out at me there though.

Errors like this happen when repos are temporarily offline or something.  Not necessarily something to worry about.  Unless it happens regularly.

---

