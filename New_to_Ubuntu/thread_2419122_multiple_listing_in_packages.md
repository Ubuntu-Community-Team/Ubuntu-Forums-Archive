---
title: "multiple listing in packages"
date: 2019-05-16
forum: New to Ubuntu
---

### Post by newblank25 on 2019-05-16
I get this information in terminal & I wish to correct it. It interferes with running package updater. can someone give me step by step ways to fix this? thx here is message from terminal
Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:49
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:49

---

### Post by #&amp;thj^% on 2019-05-16
This should be an easy fix, you have more than one entry for the two of those Repo's so remove one of each of those, and things should sort them self out.
In other words you should have only one of each showing in>>>"/etc/apt/sources.list" 
If your unsure post back this:
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by newblank25 on 2019-05-17
```
/etc/apt/sources.list:# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in
/etc/apt/sources.list:## universe WILL NOT receive any review or updates from the Ubuntu security
/etc/apt/sources.list:## team.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates universe
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports restricted main universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main'
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) disco-security multiverse main universe restricted main'
/etc/apt/sources.list:# deb [arch=amd64,i386] [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main # disabled on upgrade to disco
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main universe restricted multiverse #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main universe restricted multiverse
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main universe restricted multiverse #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main universe restricted multiverse
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates main universe restricted multiverse #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates main universe restricted multiverse
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports main universe restricted multiverse #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports main universe restricted multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security restricted main universe multiverse #deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security main universe restricted multiverse
/etc/apt/sources.list:# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security main universe restricted multiverse #deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security main universe restricted multiverse
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main universe restricted multiverse #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main universe restricted multiverse
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) disco main
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) disco main
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) disco main
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) disco main
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco partner
/etc/apt/sources.list:# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco partner
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main universe restricted multiverse #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main universe restricted multiverse
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates main universe restricted multiverse #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates main universe restricted multiverse
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports main universe restricted multiverse #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports main universe restricted multiverse
/etc/apt/sources.list:# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security main universe restricted multiverse #deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security main universe restricted multiverse
/etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-bionic.list.distUpgrade:deb [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) cosmic main # disabled on upgrade to cosmic
/etc/apt/sources.list.d/clipgrab-team-ubuntu-ppa-bionic.list.distUpgrade:deb [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) cosmic main # disabled on upgrade to cosmic
/etc/apt/sources.list.d/google-chrome.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/mikhailnov-ubuntu-pulseeffects-cosmic.list.distUpgrade:deb [http://ppa.launchpad.net/mikhailnov/pulseeffects/ubuntu](http://ppa.launchpad.net/mikhailnov/pulseeffects/ubuntu) cosmic main
/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-cosmic.list.distUpgrade:deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) cosmic main
/etc/apt/sources.list.d/noobslab-ubuntu-apps-bionic.list.distUpgrade:deb [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) bionic main
/etc/apt/sources.list.d/noobslab-ubuntu-apps-bionic.list.distUpgrade:# deb-src [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) bionic main
/etc/apt/sources.list.d/oguzhaninan-ubuntu-stacer-disco.list:deb [http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu](http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu) disco main
/etc/apt/sources.list.d/oguzhaninan-ubuntu-stacer-disco.list:# deb-src [http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu](http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu) disco main
/etc/apt/sources.list.d/opera-stable.list.save:# This file makes sure that Opera Browser is kept up-to-date
/etc/apt/sources.list.d/opera-stable.list.save:# as part of regular system upgrades
/etc/apt/sources.list.d/opera-stable.list.save:
/etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-audacity-bionic.list.distUpgrade:deb [http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu) cosmic main # disabled on upgrade to cosmic
/etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-audacity-cosmic.list:deb-src [http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu) cosmic main
/etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-audacity-cosmic.list.distUpgrade:# deb-src [http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu) cosmic main
/etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-audacity-cosmic.list.save:deb-src [http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu) cosmic main
/etc/apt/sources.list.d/vivaldi.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/vivaldi.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/vivaldi.list:deb [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main
/etc/apt/sources.list.d/vivaldi.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/vivaldi.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/vivaldi.list.distUpgrade:#deb [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main
/etc/apt/sources.list.d/vivaldi.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/vivaldi.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/vivaldi.list.save:deb [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main
```


This is what i got. So how to fix this now. Thx

---

### Post by dino99 on 2019-05-17
You run Disco, so remove all the other entries not related to Disco (i'm seeing xenial, cosmic at least) from /etc/apt/sources.list
Then clean the system with clean/autoclean/autoremove/gtkorphan

---

### Post by #&amp;thj^% on 2019-05-17
In order to fix this in a timely manner I'm just going to show you how to set it right again,** providing your system is stable currently.** (Outside of what we are trying to fix here.)
Open a terminal and enter:
```
sudoedit /etc/apt/sources.list
```
And just remove all you have in yours, and replace with the below:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu disco main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu disco-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu disco universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco universe
deb http://archive.ubuntu.com/ubuntu disco-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu disco multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco multiverse
deb http://archive.ubuntu.com/ubuntu disco-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu disco-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu disco partner
# deb-src http://archive.canonical.com/ubuntu disco partner

deb http://archive.ubuntu.com/ubuntu disco-security main restricted
# deb-src http://security.ubuntu.com/ubuntu disco-security main restricted
deb http://archive.ubuntu.com/ubuntu disco-security universe
# deb-src http://security.ubuntu.com/ubuntu disco-security universe
deb http://archive.ubuntu.com/ubuntu disco-security multiverse
# deb-src http://security.ubuntu.com/ubuntu disco-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
#deb http://archive.ubuntu.com/ubuntu disco-proposed multiverse universe main restricted
# see the sources.list(5) manual.
deb http://archive.canonical.com/ disco partner
```
This is a default source list only, **so any PPA's you think you need you will have to add them back at your own risk.**
EDIT: One other thing we need to do is get this out of the way and back it up:
```
sudo cp /etc/apt/sources.list.d/* /etc/apt/sources.list.d/*.bk
```
You will see this for now, only temporary:
```
N: Ignoring file '*.bk' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```
We'll fix that after you post back. ;)
Now try again with:
```
sudo apt update
```

---

### Post by newblank25 on 2019-05-17
```
sudo cp /etc/apt/sources.list.d/* /etc/apt/sources.list.d/*.bk
```
and result was this ```
cp: target '/etc/apt/sources.list.d/*.bk' is not a directory
```
I also removed and xerial or cosmic from software updater. after update I got this```
Get:1 http://security.ubuntu.com/ubuntu disco-security InRelease [97.5 kB]
Hit:2 http://archive.ubuntu.com/ubuntu disco InRelease                         
Hit:3 http://archive.canonical.com/ubuntu disco InRelease                      
Hit:4 http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu disco InRelease       
Get:5 http://archive.ubuntu.com/ubuntu disco-updates InRelease [97.5 kB]       
Ign:6 http://dl.google.com/linux/chrome/deb stable InRelease                   
Ign:7 http://repo.vivaldi.com/stable/deb stable InRelease                      
Hit:8 http://repo.vivaldi.com/stable/deb stable Release                        
Hit:9 http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu cosmic InRelease
Hit:10 http://dl.google.com/linux/chrome/deb stable Release                    
Get:11 http://archive.ubuntu.com/ubuntu disco-backports InRelease [88.8 kB]    
Get:12 http://archive.ubuntu.com/ubuntu disco-security InRelease [97.5 kB]
Fetched 381 kB in 2s (229 kB/s)      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Skipping acquire of configured file 'main'/binary-amd64/Packages' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/binary-i386/Packages' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/i18n/Translation-en_US' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/i18n/Translation-en' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/Components-amd64.yml' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/icons-48x48.tar' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/icons-64x64.tar' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/cnf/Commands-amd64' as repository 'http://archive.ubuntu.com/ubuntu disco InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Skipping acquire of configured file 'main'/binary-amd64/Packages' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/binary-i386/Packages' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/i18n/Translation-en_US' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/i18n/Translation-en' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/Components-amd64.yml' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/icons-48x48.tar' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/dep11/icons-64x64.tar' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'main'/cnf/Commands-amd64' as repository 'http://security.ubuntu.com/ubuntu disco-security InRelease' doesn't have the component 'main'' (component misspelt in sources.list?)
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:46
```

---

### Post by newblank25 on 2019-05-17
thx for help

---

### Post by #&amp;thj^% on 2019-05-17
You did not follow me with my instructions:
Now plainly put:
```
sudo -H gedit /etc/apt/sources.list
```
When it opens remove all>>everything shown, and replace with (Just copy and paste)
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu disco main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu disco-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu disco universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco universe
deb http://archive.ubuntu.com/ubuntu disco-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu disco multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco multiverse
deb http://archive.ubuntu.com/ubuntu disco-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu disco-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu disco partner
# deb-src http://archive.canonical.com/ubuntu disco partner

deb http://archive.ubuntu.com/ubuntu disco-security main restricted
# deb-src http://security.ubuntu.com/ubuntu disco-security main restricted
deb http://archive.ubuntu.com/ubuntu disco-security universe
# deb-src http://security.ubuntu.com/ubuntu disco-security universe
deb http://archive.ubuntu.com/ubuntu disco-security multiverse
# deb-src http://security.ubuntu.com/ubuntu disco-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# deb http://archive.ubuntu.com/ubuntu disco-proposed multiverse universe main restricted
# see the sources.list(5) manual.
deb http://archive.canonical.com/ disco partner
```
Save the file, and run again:
```
sudo apt update
```

---

### Post by DuckHook on 2019-05-17
@OP

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by newblank25 on 2019-05-18
I might be a little slow but I followed instructions. I rebooted system after updates. The computer came on & all packages are now up to date. I still have a problem that package updater is just stuck. I can use the terminal to get package updates with sudo apt-get update but it is just easier with the package updater. how can i fix this? any help would be appreciated.

---

### Post by #&amp;thj^% on 2019-05-20
> **newblank25 said:**
> I might be a little slow but I followed instructions.

If you are refering to me, then I can see the possibility my words may have been seen with a negative tone, but that's not how I'm built, merely pointing out with clear instructions is all. ;)
If your refering to Duck Hook, again not meant to be a bashing but merely pointing out how important using code tags is to keep the format from a terminal out put. **(Sorry Duck Hook for speaking in your behalf hope I did not misspeak)**
We were all new to this at one time.
Now this might give us a clue for your software-updater please run:
```
sudo apt clean
```
Now to be sure, reboot now, or "before" running the below:
```
sudo apt update
``` 
**BTW: using and learning the terminal at every opportunity is good, it will soon become your best friend. :)**

---

