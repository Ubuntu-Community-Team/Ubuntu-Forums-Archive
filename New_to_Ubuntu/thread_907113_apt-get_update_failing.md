---
title: "apt-get update failing?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by scurlaruntings on 2008-09-01
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


The above is the result of the apt-get update command. Im using an old version of Ubuntu 6.10. Iv done so much work on it and refuse to upgrade incase it breaks something else!!:) Last time i did some much needed updates and lost functionality for my Belkin54G card because the newer version of Ndiswrapper wasnt supported! Anyway presumably by sources list is way out of date and hence the reason why the apt-get is failing? Is there a work around for this? Can i simply modify my sources.list with the new IP address for the correct repository? Bear in mind im a relative Linux newbie and a Windows system admin so i may be a bit slow on the uptake:(

---

### Post by annatar on 2008-09-01
Well...support for Edgy/6.10 has been ended  - no more updates. Additionally, packages of 6.10 have been removed from the repository.    I think, it's time for you to update.

---

### Post by rjrenjian on 2008-09-06
Nurse: How do you feel after your operation? Patient: Quite alright, only I can feel two hearts beating inside me. Nurse: No wonder the doctor who operated on you was looking for his [replica rolex](http://www.cheap-replica-rolex.com/) everywhere just now.

---

### Post by Sef on 2008-09-13
Moved to absolute beginners.

---

### Post by crazypenguin2008 on 2008-09-13
you need to upgrade. dowload and burn or request a live cd of hardy heron and do a fresh install. that would be the best route to go in my opinion

---

### Post by Matyos on 2008-09-13
do the following ;

sudo gedit /etc/apt/sources.list

then the gedit window will pop up with the list of the repository site addresses .
If your version is edgy 6.10  edit the source addresses form "edgy" to "fiesty"

example see below wherever you see "edgy" replace with "fiesty"

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
 deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) edgy free non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

---

### Post by Gannon8 on 2008-09-13
> **Matyos said:**
> do the following ;

sudo gedit /etc/apt/sources.list

then the gedit window will pop up with the list of the repository site addresses .
If your version is edgy 6.10  edit the source addresses form "edgy" to "fiesty"

example see below wherever you see "edgy" replace with "fiesty"

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
 deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) edgy free non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

DONT DO THAT! It may ruin your system after updating. Burn a new Hardy CD and do a fresh install.

---

