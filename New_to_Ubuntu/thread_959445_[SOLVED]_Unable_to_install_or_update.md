---
title: "[SOLVED] Unable to install or update"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by mity on 2008-10-26
I am unable to update. when i try updating through terminal, i receive the following error message. 

"Reading package lists... Error!
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_non-free_binary-i386_Packages)
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened."

---

### Post by Xiong Chiamiov on 2008-10-26
Well, it looks like you've got the medibuntu repos in you /etc/apt/sources.list twice.  Go ahead and edit it (as root) and remove those, then update and see if you still get the error about btnx.

---

### Post by mity on 2008-10-26
here are the files in that folder. 

as you could see i only have one set of medibuntu ( unless i should delete list.save file).

i appreciate any help provided.

---

### Post by Xiong Chiamiov on 2008-10-26
I was referring to the sources.list file, but... when did Ubuntu start using sources.list.d?

Do you still have a sources.list (it's a text file)?  If so, could I have a look at it, as well as medibuntu.lst?

---

### Post by mity on 2008-10-26
here you go:

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

## Medibuntu - Ubuntu 8.04 "hardy"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

#ULTAMATIX REPOS START

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all
#ULTAMATIX REPOS END

---

### Post by mity on 2008-10-26
and here is medibuntu:

## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

---

### Post by mister_pink on 2008-10-26
You only want one or the other I think. Go into System, Admin, Software sources, 3rd Party to correct it.

---

### Post by Xiong Chiamiov on 2008-10-26
Or, I suppose, delete the medibuntu file.

---

### Post by mity on 2008-10-26
I removed medibintu. 

when i tried to update i recieved the follwing error:

'E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Xiong Chiamiov on 2008-10-26
In this part:
```

#ULTAMATIX REPOS START

deb http://repoubuntusoftware.info harty all

deb http://repoubuntusoftware.info harty all
#ULTAMATIX REPOS END

```
those "harty"s should probably say "hardy".

---

### Post by mity on 2008-10-26
thank you. 

i changed the misspelled words and now i am all cool. 

i owe you a cookie.

---

