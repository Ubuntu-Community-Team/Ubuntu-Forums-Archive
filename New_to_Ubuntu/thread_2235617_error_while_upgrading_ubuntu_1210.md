---
title: "error while upgrading ubuntu 12:10"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by pon2 on 2014-07-22
Hi friends.

i am new to ubuntu i am using 12.10, while i tried to $sudo apt-get update : i got error like 404:not found.

then i cleared that by editing the sourcefile.list. now my source file.list as follows:


#deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal universe
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal universe
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal multiverse
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) quantal-security universe
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main



****************

after this step , while updating 404:found has cleared. but now it is showing GPG error
E: GPG error: [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) quantal Release: The following signatures were invalid: NODATA 1 NODATA 2


how to fix this bug,



Appropriate ideas would be Appreciated,...........


Thanks

---

### Post by coffeecat on 2014-07-22
It is not a bug. There is no in.old-releases.ubuntu.com subdomain, only old-releases.ubuntu.com . You have a mixture of the two. You should have only old-releases.ubuntu.com . See here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Even if you get that right, I'm not sure what will happen next. I believe an upgrade directly from 12.10 to 14.04 was possible, but you may be offered the upgrade from 12.10 to 13.04, which will get you stuck in an unsupported release upgrade path all the way from 12.10 to 14.04. 13.04 and 13.10 are now also end-of-life.

Since you are new to Ubuntu and since there is the possibility of a chain of three unsupported upgrades before you get to a currently supported version, I strongly advise you to re-install with the current LTS (long term support) 14.04.

---

### Post by pon2 on 2014-07-31
Thanks I replaced it with old-releases.ubuntu.com , now it is upgrading ,

Thanks A Lottttttt

---

### Post by pon2 on 2014-08-08
how to mark it as solved thread , so that it ll be used to others and save their time

---

### Post by Impavidus on 2014-08-08
Click "Thread tools" (near the top of the page), then click "mark as solved".

---

