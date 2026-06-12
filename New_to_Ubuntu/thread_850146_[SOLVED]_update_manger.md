---
title: "[SOLVED] update manger"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by tadcan on 2008-07-05
I have trued to update but I get this 

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

and this

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  main'./source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

I can download 3rd party app updates. How can I solve this?

---

### Post by hyper_ch on 2008-07-05
post your sources.lis

---

### Post by billgoldberg on 2008-07-05
> **hyper_ch said:**
> post your sources.lis

Open up a terminal, and copy/paste this code.

```
sudo gedit /etc/apt/sources.list
```

Copy/paste the text from the file that will open here.

---

### Post by ZabiGG on 2008-07-05
Actually, I'm not 100% sure it is, but it might be a problem with the repository. When in Synaptic > Settings > Repositories, Update tab, the Important security updates box is unchecked and stays unchecked even if I try to activate it.

Can anyone repeat this on their system?

Kernel .19
All repos activated, including proposed and backports, excluding source.

---

### Post by tadcan on 2008-07-06
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://ie.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe main multiverse main'. restricted #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy main'.
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse main'. restricted
deb-src http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse main'. restricted #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse main'. restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse main'. restricted #Added by software-properties
```

---

### Post by tadcan on 2008-07-06
@ZabiGG

I have both important and recommended updates ticked. I can untick and tick them without a problem.

---

### Post by ZabiGG on 2008-07-06
Hi again, ;)

If you remove the ' . 

in all instances of 

main' . restricted and elsewhere it's been inserted, it should work.

Mine looks in the Canadian repos, and looks like this

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe

There are no apostrophes or periods. Your # comments should not affect the file, though. You can keep those.

Hope this helps,

Z.

---

### Post by tadcan on 2008-07-16
I changed the mirror to Ireland and it solved the problem.

---

