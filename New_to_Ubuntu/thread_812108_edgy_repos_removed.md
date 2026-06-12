---
title: "edgy repos removed?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by zebutron on 2008-05-29
Have some of the edgy repos been removed, or are are they probably just down?

I just installed edgy recently and would like to start using it however I am unable to install some packages using apt-get, synaptic, or add/remove programs. 

This is what I get from apt (and the same from synaptic)

```
:~$ sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Ign cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1) dapper/main Translation-en_US
Ign cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1) dapper/restricted Translation-en_US
Get:1 http://packages.medibuntu.org edgy Release.gpg [189B]                    
Ign http://packages.medibuntu.org edgy/free Translation-en_US                  
Ign http://packages.medibuntu.org edgy/non-free Translation-en_US              
Ign http://security.ubuntu.com edgy-security Release.gpg                       
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://archive.ubuntu.com edgy Release.gpg                       
Ign http://archive.ubuntu.com edgy/main Translation-en_US            
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US      
Hit http://packages.medibuntu.org edgy Release                       
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security Release                 
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US      
Ign http://archive.ubuntu.com edgy/universe Translation-en_US
Ign http://archive.ubuntu.com edgy/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-updates Release.gpg               
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US    
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Hit http://packages.medibuntu.org edgy/free Packages                 
Ign http://security.ubuntu.com edgy-security/main Packages           
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-proposed Release.gpg
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US   
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US
Hit http://packages.medibuntu.org edgy/non-free Packages             
Ign http://security.ubuntu.com edgy-security/restricted Packages
Ign http://security.ubuntu.com edgy-security/multiverse Packages
Ign http://security.ubuntu.com edgy-security/universe Packages
Ign http://archive.ubuntu.com edgy-backports Release.gpg
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com edgy Release     
Ign http://archive.ubuntu.com edgy-updates Release
Ign http://security.ubuntu.com edgy-security/main Sources
Ign http://security.ubuntu.com edgy-security/restricted Sources
Ign http://security.ubuntu.com edgy-security/multiverse Sources
Ign http://security.ubuntu.com edgy-security/universe Sources
Err http://security.ubuntu.com edgy-security/main Packages
  404 Not Found
Ign http://archive.ubuntu.com edgy-proposed Release
Ign http://archive.ubuntu.com edgy-backports Release
Err http://security.ubuntu.com edgy-security/restricted Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/multiverse Packages
  404 Not Found
Ign http://archive.ubuntu.com edgy/main Packages
Ign http://archive.ubuntu.com edgy/restricted Packages
Ign http://archive.ubuntu.com edgy/multiverse Packages
Ign http://archive.ubuntu.com edgy/universe Packages
Ign http://archive.ubuntu.com edgy/main Sources
Ign http://archive.ubuntu.com edgy/restricted Sources
Ign http://archive.ubuntu.com edgy/multiverse Sources
Ign http://archive.ubuntu.com edgy/universe Sources
Err http://security.ubuntu.com edgy-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/main Sources
  404 Not Found
Err http://security.ubuntu.com edgy-security/restricted Sources
  404 Not Found
Err http://security.ubuntu.com edgy-security/multiverse Sources
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Sources
  404 Not Found
Ign http://archive.ubuntu.com edgy/universe Packages
Ign http://archive.ubuntu.com edgy-updates/main Packages
Ign http://archive.ubuntu.com edgy-updates/restricted Packages
Ign http://archive.ubuntu.com edgy-updates/multiverse Packages
Ign http://archive.ubuntu.com edgy-updates/universe Packages
Ign http://archive.ubuntu.com edgy-updates/main Sources
Ign http://archive.ubuntu.com edgy-updates/restricted Sources
Ign http://archive.ubuntu.com edgy-updates/multiverse Sources
Ign http://archive.ubuntu.com edgy-updates/universe Sources
Ign http://archive.ubuntu.com edgy-proposed/restricted Packages
Ign http://archive.ubuntu.com edgy-proposed/main Packages
Ign http://archive.ubuntu.com edgy-proposed/multiverse Packages
Ign http://archive.ubuntu.com edgy-proposed/universe Packages
Ign http://archive.ubuntu.com edgy-proposed/restricted Sources
Ign http://archive.ubuntu.com edgy-proposed/main Sources
Ign http://archive.ubuntu.com edgy-proposed/multiverse Sources
Ign http://archive.ubuntu.com edgy-proposed/universe Sources
Ign http://archive.ubuntu.com edgy-backports/restricted Packages
Ign http://archive.ubuntu.com edgy-backports/main Packages
Ign http://archive.ubuntu.com edgy-backports/multiverse Packages
Ign http://archive.ubuntu.com edgy-backports/universe Packages
Ign http://archive.ubuntu.com edgy-backports/restricted Sources
Ign http://archive.ubuntu.com edgy-backports/main Sources
Ign http://archive.ubuntu.com edgy-backports/multiverse Sources
Ign http://archive.ubuntu.com edgy-backports/universe Sources
Err http://archive.ubuntu.com edgy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-proposed/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-proposed/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-proposed/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-proposed/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-proposed/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-proposed/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-proposed/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-proposed/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Fetched 1B in 2s (0B/s)  
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

And here is my sources.list...list

```

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe

```

I have had no problem connecting to the Internet or using other repos such as medibuntu.

Any help would be greatly apprciated. 

Also can't upgrade to fiesty using update manager.

---

### Post by Oldsoldier2003 on 2008-05-29
> **zebutron said:**
> Have some of the edgy repos been removed, or are are they probably just down?

I just installed edgy recently and would like to start using it however I am unable to install some packages using apt-get, synaptic, or add/remove programs. 

This is what I get from apt (and the same from synaptic)

<snipped>
And here is my sources.list...list

<snipped>

I have had no problem connecting to the Internet or using other repos such as medibuntu.

Any help would be greatly apprciated. 

Also can't upgrade to fiesty using update manager.

Edgy reached its end of lifespan last month and is no longer supported. You *should be able* to use the feisty alternate install cd to upgrade to feisty from edgy

---

