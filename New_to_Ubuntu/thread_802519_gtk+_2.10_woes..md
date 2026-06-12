---
title: "gtk+ 2.10 woes."
date: 2008-05-21
forum: New to Ubuntu
---

### Post by chinchilla2392 on 2008-05-21
ive recently tried installing the Aurora engine. but it says GTK+ 2.10 is missing.
so i have tried to install libgtk2.0-dev..
this is what i get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.12.9-3ubuntu4) but 2.12.9-4ubuntu3 is to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
E: Broken packages


anyone else had this problem?
someone help me out.

---

### Post by civillian on 2008-05-21
Basically, the important bit of the error message is this bit > libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.12.9-3ubuntu4) but 2.12.9-4ubuntu3 is to be installed
Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed

What the problem is is that where libgtk2.0-dev needs > 2.12.9-3ubuntu4, a newer version is to installed (> 2.12.9-4ubuntu3 is to be installed).

It may be that you are using software repos for a version of ubuntu that is newer than the one you are running and as such is installing some dependancies that are newer than the actual library you want to install.

In order to check this, could you post your /etc/apt/sources.list?

Open it in a text editor, for exmaple gedit, as root, ```
sudo gedit
``` and paste it into the forum post, and also what version of ubuntu you are using.

This is just my hunch, and please feel free to correct me!

---

### Post by chinchilla2392 on 2008-05-21
im using 8.04 ...# 


deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

thats my sources.list

---

### Post by civillian on 2008-05-21
I tried installing it on my system (it turns out it was already installed) but i would assume that it should work with 8.04 (what I'm also using-from fresh install).

I reinstalled it on my system (up to date 8.04, as I say) and it went fine...

I notice that you have some universe/multiverse repos disabled because it failed to verify, which may be the problem.

Here is my sources.list

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse

```

You might try using mine (which works fine on my pc), pasting mine over what yours is now (making a backup first, of course) and trying then, let us know how it goes, any error messages etc.

---

### Post by chinchilla2392 on 2008-05-21
i get exactly the same result as before

---

### Post by civillian on 2008-05-21
The only thing I can recommend is that you update your repos using ```
sudo apt-get update
``` then using synaptic reinstall the package after marking all upgrades and applying changes which will refresh your list of available packages, and if the newer version of libgtk2.0 is available, it will install that after which you should be able to install the dev package

---

### Post by chinchilla2392 on 2008-05-21
i updated immediately after i changed my sources.list
and if i go into synaptip i get the same dependency error message

---

### Post by civillian on 2008-05-21
If, as I assume, you upgraded as well, then I'm afraid I lack the expertise to help. and we need to appeal to some more knowledgeable forumites.
If not, try it, but I'm afraid I can only think about uninstalling libgtk2.0 and then reinstalling it and its -dev component which would onvolve removing a lot of applications, which isn't a road I want to go down really.

I'm sorry I can't help you more than I already have.

*edit*
Give the post a day, and I usually find they get answered by smart fols ;)

---

### Post by chinchilla2392 on 2008-05-21
ok. i doubt it. but we'll see..

---

