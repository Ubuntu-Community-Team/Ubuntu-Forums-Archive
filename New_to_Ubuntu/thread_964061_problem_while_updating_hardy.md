---
title: "problem while updating hardy"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by calimerox on 2008-10-30
hi there, 
i got a problem, while i updated hardy, it suddenly wrote:

[I]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 1 in source list /etc/apt/sources.list.d/ematech.list (URI parse), E:The list of sources could not be read.'

[/I]

before i tried somehow to install a n ematech repository, dont know if theres some connection... 
my sources list says this:
[I]

# 
# deb cdrom:[Ubuntu-Studio 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main multiverse restricted universe

# deb cdrom:[Ubuntu-Studio 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
[/I]


anyone can help me? would be really nice, cause i dont have any clou what that means....! THX!:)

---

### Post by Pro-reason on 2008-10-30
Open a terminal and do this:
```

sudo mv /etc/apt/sources.list.d/ematech.list ~
sudo apt-get update
sudo apt-get *dist-*upgrade

```

If you just want to update some packages within Hardy rather than upgrading Hardy to Intrepid, get rid of &#8220;dist-&#8221;.

---

### Post by calimerox on 2008-10-31
this helped me out, thanks a lot! the red sign disappeared and everything works fine again! :)

---

