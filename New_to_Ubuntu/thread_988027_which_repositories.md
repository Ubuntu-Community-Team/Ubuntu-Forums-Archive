---
title: "which repositories?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by DustofDust on 2008-11-20
[https://help.ubuntu.com/8.10/add-applications/C/extra-repositories.html](https://help.ubuntu.com/8.10/add-applications/C/extra-repositories.html)
[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)
[https://help.ubuntu.com/8.10/keeping-safe/C/updates.html](https://help.ubuntu.com/8.10/keeping-safe/C/updates.html)

a lot of marketing blahblah but no info on repositories available, written how it is necessary to write into software sources like "deb http://..."

where do i find this info?

---

### Post by hyper_ch on 2008-11-20
(1) what marketing blahblah?
(2) what info do you need on available repos?
(3) what don't you know bout "writeing into software sources"?

---

### Post by DustofDust on 2008-11-20
1. a lot of text but no hard facts

2. which official repositories are available in the form "deb ..."

3. which "deb ..." from ubuntu i can write into the software sources > third-party application?

i reported a bug in yelp i also have "deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) ..." in my repositories

i have also some from launchpad like "deb [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) intrepid main" and i want to find out which one gives me the error on updates
> Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release](http://archive.canonical.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  universe/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid-updates/Release](http://archive.canonical.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

so if i have the info about the official "deb ..." i can delete the wrong "deb http://archive.canonical.com..."

---

### Post by philinux on 2008-11-20
This is my sources list from a default install but adding partner,backports and medibuntu.
```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

---

### Post by k3lt01 on 2008-11-20
> **DustofDust said:**
> 2. which official repositories are available in the form "deb ..."deb is a file format. When adding extra repositories the line must start with deb or deb-src so apt know its the right type of file.

There are only 2 official repositories, Ubuntu and Canonical. The Ubuntu one is the first tab in software sources, and the Canonical one should by default be listed in the 2nd tab (third party software) in Software Sources.

> **DustofDust said:**
> 3. which "deb ..." from ubuntu i can write into the software sources > third-party application?from Ubuntu? the answer is none that I know of, unless you are downloading the complete repository to keep locally. Canonical should already be listed in that tab.

> **DustofDust said:**
> i reported a bug in yelp i also have "deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) ..." in my repositories

i have also some from launchpad like "deb [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) intrepid main" and i want to find out which one gives me the error on updatesWhy do you have these two? if they are not needed you could delete them, and possibly fix your problem.

> **DustofDust said:**
> so if i have the info about the official "deb ..." i can delete the wrong "deb http://archive.canonical.com..."Is there more to this code? something like "intrepid partner" should be on the end. Please post the complete line.

---

### Post by hyper_ch on 2008-11-20
> **DustofDust said:**
> 1. a lot of text but no hard facts
Like?

> **DustofDust said:**
> 
2. which official repositories are available in the form "deb ..."
all


> **DustofDust said:**
> 
3. which "deb ..." from ubuntu i can write into the software sources > third-party application?
3rd party repos are not official repos and hence not from canonical... please rephrase.

---

### Post by k3lt01 on 2008-11-20
> **hyper_ch said:**
> 3rd party repos are not official repos and hence not from canonical... please rephrase.He is actually half correct. Canonical's own repository is in the 3rd party repo list.

---

### Post by philinux on 2008-11-20
The only apps in 3rd party canonical parter repo's are adobe-flashplugin and opera.

---

### Post by k3lt01 on 2008-11-20
These are the apps available from Canonical for Hardy through the Canonical repos. I would assume Intrepid is similar.

adobe-flashplugin_10.0.12.36-1hardy2_i386
db2exc_9.5.0-2-1hardy1_i386
gstreamer0.10-fluendo-plugins-doc_0.10.6-1hardy1_i386
gstreamer0.10-fluendo-plugins-wmv-doc_0.10.6-1hardy1_i386
opera_9.27-20080331.6hardy1_i386
parallels_2.2.2232-1hardy4_i386
parallels-modules_2.2.2232-1hardy4_i386
parallels-modules-2.6.24-18-generic_2.2.2232-1hardy3_i386
parallels-modules-2.6.24-18-server_2.2.2232-1hardy3_i386
parallels-modules-2.6.24-19-generic_2.2.2232-1hardy4_i386
parallels-modules-2.6.24-19-server_2.2.2232-1hardy4_i386
zdesktop_0.90.1249beta-hardy1_i386

---

### Post by DustofDust on 2008-11-23
> **philinux said:**
> This is my sources list from a default install but adding partner,backports and medibuntu.
```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

thanks, that i wanted to know! ):P

---

