---
title: "Update Manager issues"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by thechad90000 on 2012-05-01
I just recently upgraded from 11.10 to 12.04 and now I'm having issues with the update manager. In the top right hand side of the screen instead of it's regular icon there is a big red circle with a white line through it and when I try to find packaged to update I receive this pop up notification:

Could Not Initialize the package information

An unresolvable problem occurred while initializing the package information

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)'


Does anyone know how I can fix this. Any help would be great. Thank you.

---

### Post by plucky on 2012-05-01
> **thechad90000 said:**
> I just recently upgraded from 11.10 to 12.04 and now I'm having issues with the update manager. In the top right hand side of the screen instead of it's regular icon there is a big red circle with a white line through it and when I try to find packaged to update I receive this pop up notification:

Could Not Initialize the package information

An unresolvable problem occurred while initializing the package information

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)'


Does anyone know how I can fix this. Any help would be great. Thank you.


Open a terminal (Ctrl+Alt+T) and post output for ```
cat /etc/apt/sources.list
```

---

### Post by thechad90000 on 2012-05-01
```

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/precise partner
deb-src http://archive.canonical.com/precise partner

```

---

### Post by philinux on 2012-05-01
Line 59,

deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner

Should be,

deb [http://archive.canonical.com/](http://archive.canonical.com/)**ubuntu** precise partner

use gksu gedit /etc/apt/sources.list to change it.

---

### Post by plucky on 2012-05-01
> **philinux said:**
> Line 59,

deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner

Should be,

deb [http://archive.canonical.com/](http://archive.canonical.com/)**ubuntu** precise partner

use gksu gedit /etc/apt/sources.list to change it.

Also the same for line 60 > deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner

Good Luck

---

### Post by Sidewinder1 on 2012-05-01
WADR, I believe that it should be:
 ```
gksudo gedit
```
Please correct me if I'm wrong (happens all the time) as I'm still learning the many nuances..

Side

---

### Post by thechad90000 on 2012-05-01
Just wanted to say thank you. Everything is working fine now.

---

