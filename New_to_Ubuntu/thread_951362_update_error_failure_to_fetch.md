---
title: "update error failure to fetch"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by natewhipple on 2008-10-18
I recently updated and had to reboot, after the computer came back up an update notification popped up indicating that I had more updates available.

the following error occured:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008e-1ubuntu0.8.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008e-1ubuntu0.8.04_all.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal-info/hal-info_20080508+git20080601-0ubuntu0.8.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal-info/hal-info_20080508+git20080601-0ubuntu0.8.04_all.deb)
  404 Not Found [IP: 91.189.88.31 80]


Im not sure how to even approach this any help would be appreciated.

---

### Post by eternalnewbee on 2008-10-18
> **natewhipple said:**
> I recently updated and had to reboot, after the computer came back up an update notification popped up indicating that I had more updates available.

the following error occured:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008e-1ubuntu0.8.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008e-1ubuntu0.8.04_all.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal-info/hal-info_20080508+git20080601-0ubuntu0.8.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal-info/hal-info_20080508+git20080601-0ubuntu0.8.04_all.deb)
  404 Not Found [IP: 91.189.88.31 80]


Im not sure how to even approach this any help would be appreciated.

I wouldn't worry too much about this. Could be that they are temporarily unavailable.

---

### Post by Nepherte on 2008-10-18
You can try another mirror to update rightaway.

---

### Post by natewhipple on 2008-10-18
I will try again later, if problem persists how do I choose a different location?


u

---

### Post by Ryadt on 2008-10-18
Can you post the output of your sources list.```
cat /etc/apt/sources.list
```

---

### Post by natewhipple on 2008-10-18
> **Ryadt said:**
> Can you post the output of your sources list.```
cat /etc/apt/sources.list
```
here is what was output


#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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

---

### Post by Ryadt on 2008-10-18
Can you confirm which version of Ubuntu you are using.

---

### Post by natewhipple on 2008-10-18
I think that it is 8.4 hardy heron and I am using a thinkpad t61

---

### Post by Ryadt on 2008-10-19
It might be that there is a problem with the server. Try changing to a better one. Go in Software Sources and from the 'Download from' drop-list, select other. Then click on 'Select Best Server.

---

### Post by natewhipple on 2008-10-19
that seems to have done the trick.  thanks for all the help

---

