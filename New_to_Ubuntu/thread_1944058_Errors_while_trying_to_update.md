---
title: "Errors while trying to update"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by Norman Thom on 2012-03-20
When I try to do an update via the terminal in ubuntu 11.10 I get 2 errors and no update
Error 1 Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/team-xbmc-ppa-oneiric.list 

Error 2 The list of sources could not be read.

Can anyone help me resolve this problem

I thought it was due to XBMC but even after I removed it I still get the errors

Thanks in advance

---

### Post by TeoBigusGeekus on 2012-03-20
Well, what's the 3rd line of /etc/apt/sources.list.d/team-xbmc-ppa-oneiric.list?

---

### Post by Norman Thom on 2012-03-20
I checked my Soources list and the following is a copy:

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-proposed restricted main multiverse universe
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
# deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps

Does this help any?

---

### Post by TeoBigusGeekus on 2012-03-20
Not your sources.list file, but the file I mentioned in my previous post.

---

### Post by Norman Thom on 2012-03-20
Inputting that line of code results in a permission denied stating that there is no such file in directory

---

### Post by TeoBigusGeekus on 2012-03-20
Try
```
gedit /etc/apt/sources.list.d/team-xbmc-ppa-oneiric.list
```

---

### Post by Norman Thom on 2012-03-20
Better:

output = deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) oneiric main
n

I notice the terminal 'n' - should I just delete it?

---

### Post by TeoBigusGeekus on 2012-03-20
> **Norman Thom said:**
> Better:

output = deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) oneiric main
n

I notice the terminal 'n' - should I just delete it?

Yeah.

---

### Post by Norman Thom on 2012-03-20
I deleted th 'n' in the sources list and closed it
I was asked to 'save as' and did I then got an error Could not save the file /etc/apt/sources.list.d/team-xbmc-ppa-oneiric.list. stating that I did not have permission to save the file

---

### Post by TeoBigusGeekus on 2012-03-20
Of course.
Open the file with
```
gksu gedit /etc/apt/sources.list.d/team-xbmc-ppa-oneiric.list
```

---

### Post by Norman Thom on 2012-03-20
Thank-you TeoBiggus Geekus:

That's what it to to save the modified file.  A subsequent update worked a charm.  I will now reinstall xbmc and see how it works

Thanks and addio

---

### Post by TeoBigusGeekus on 2012-03-20
You're welcome mate!

---

