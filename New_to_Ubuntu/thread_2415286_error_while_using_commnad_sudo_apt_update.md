---
title: "error while using commnad sudo apt update"
date: 2019-03-23
forum: New to Ubuntu
---

### Post by pratap73 on 2019-03-23
```
sudo apt update
[sudo] password for user: 
Ign:1 cdrom://Ubuntu-Studio 16.04 LTS _Xenial Xerus_ - Alpha amd64 (20151225) xenial InRelease
Err:2 cdrom://Ubuntu-Studio 16.04 LTS _Xenial Xerus_ - Alpha amd64 (20151225) xenial Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:3 [http://ppa.launchpad.net/webu8tme/jupiter/ubuntu](http://ppa.launchpad.net/webu8tme/jupiter/ubuntu) oneiric InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease                                                                                              
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]                                                                          
Err:6 [http://ppa.launchpad.net/webu8tme/jupiter/ubuntu](http://ppa.launchpad.net/webu8tme/jupiter/ubuntu) oneiric Release                                                                    
  403  Forbidden
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]                                                                 
Hit:8 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                                                                                 
Hit:9 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic InRelease                                                                                 
Hit:10 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                                                                                
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]                                          
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [109 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]           
Hit:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease             
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [107 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed InRelease [242 kB]
Ign:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety InRelease
Err:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety Release
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Reading package lists... Done                                                                                                                        
E: The repository 'cdrom://Ubuntu-Studio 16.04 LTS _Xenial Xerus_ - Alpha amd64 (20151225) xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/webu8tme/jupiter/ubuntu oneiric Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu yakkety Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details
```

---

### Post by sisco311 on 2019-03-23
Which version of Ubuntu are you using?

Your sources.list has xenial, yakkety, bionic and a xenial cdrom :confused:

Please post the output of:
```
lsb_release -a
```

```
cat /etc/apt/sources.list
```

and

```
head -n-0 /etc/apt/sources.list.d/*
```

---

### Post by pratap73 on 2019-03-24
output of :lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:    16.04
Codename:    xenial
```

output of cat /etc/apt/sources.list:

```
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb cdrom:[Ubuntu-Studio 16.04 LTS _Xenial Xerus_ - Alpha amd64 (20151225)]/ xenial main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```

head -n-0 /etc/apt/sources.list.d/*
```
==> /etc/apt/sources.list.d/videolan-ubuntu-master-daily-xenial.list <==
deb [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) xenial main

==> /etc/apt/sources.list.d/videolan-ubuntu-master-daily-xenial.list.save <==
deb [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) xenial main
```

---

