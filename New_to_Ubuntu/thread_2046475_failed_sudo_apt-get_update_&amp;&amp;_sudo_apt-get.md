---
title: "failed sudo apt-get update &amp;&amp; sudo apt-get upgrade"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by 007casper on 2012-08-23
I checked /etc/apt/sources.list
> # 
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release amd64 (20081028.1)]/ intrepid main restricted

# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release amd64 (20081028.1)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner


it fails... what is the url for the repo?

thank you

---

### Post by plucky on 2012-08-23
> **007casper said:**
> I checked /etc/apt/sources.list


it fails... what is the url for the repo?

thank you

What is the failure?

Better to use the terminal and post output for ```
sudo apt-get update && sudo apt-get upgrade
``` and you might get a response.

Good Luck

---

### Post by Linux_junkie on 2012-08-23
Your using Ubuntu server 8.10? If so, support for that version ended in 2011 thats the reason you cannot update.

I think you need an upgrade.

---

### Post by Frogs Hair on 2012-08-23
You may have to edit the sources list remove the unsupported 8.10 repositories. I see the lucid sources also so guessing this is upgrade ?

---

### Post by 007casper on 2012-08-23
I am using 
2.6.32-33-server #72-Ubuntu SMP Fri Jul 29 21:21:55 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.3 LTS

> 
sudo apt-get update && sudo apt-get upgrade



Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Temporary failure resolving 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
  Temporary failure resolving 'archive.canonical.com'
Err [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US
  Temporary failure resolving 'archive.canonical.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US   
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US 
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                  
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/dists/lucid/Release.gpg](http://archive.canonical.com/dists/lucid/Release.gpg)  Temporary failure resolving 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/dists/lucid/partner/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.canonical.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by IWantFroyo on 2012-08-23
I'm using Lucid as well, and I haven't tampered with my sources.list file.

Feel free to try using mine:

```
#deb cdrom:[Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by 007casper on 2012-08-24
what is deb-src?

did you add it, or yours came with it?  I am just curious. 

Thank you.

---

### Post by plucky on 2012-08-24
> **007casper said:**
> what is deb-src?

did you add it, or yours came with it?  I am just curious. 

Thank you.

deb-src repositories are for the source code files,which you don't need unless you want to examine the source code for any installed package.

Your problem could be because the repositories are being hammered as 12.04.1 has just been released and there might be a lot of peoples upgrading from 10.04.4 to 12.04.1

Try searching for a faster repository in Software Sources and see if that fixes the problem,or give it a week or so before trying the upgrade.

Good luck

---

### Post by Wirephire on 2012-08-24
Your sources.list looks fine to me and I think you're having some connection problems, apparently DNS issue.
Are you able to ping us.archive.ubuntu.com on this machine? Refer to [this thread](http://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error).


*~wph*

---

