---
title: "CUPS error with hplip-2.8.4"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by DamonChyld on 2008-04-23
I have been trying to get my HP printer setup on my laptop using hplip-2.8.4 but am having all kinds of issues ;)

The installer is now telling me that I need to install cups:
```
RUNNING PRE-INSTALL COMMANDS
----------------------------


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 1 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups (cups - Common Unix Printing System)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 1 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes libcupsys2'
Please wait, this may take several minutes...
Running 'sudo apt-get install --yes --force-yes libsane'
Please wait, this may take several minutes...
 

RUNNING POST-PACKAGE COMMANDS
-----------------------------


RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'cups (cups - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.

:~/Desktop$ sudo apt-get install --yes --force-yes libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcupsys2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Libcups2 seems to be installed, both here when I ran apt-get and in synaptic. I have tried reinstalling (through synaptic) and running the installer again but receive the same error. The first problem with python2.5 was solved by manually uncommenting some deb's in sources.list (synaptic showed them as in use) so I don't know if this problem may be there as well but here is my sources.list just in case:

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
deb http://www.virtualbox.org/debian gutsy non-free
deb http://wine.sourceforge.net/apt/ binary/
```

Any help is appreciated, this is getting tiresome!

---

### Post by ZabiGG on 2008-05-16
Hi there and thanks for your question...

Sorry it took so long. Posts pile up pretty fast in this section of the forum.

Are you still trying to solve this issue? If you have, we'd love to know the outcome.

Maybe you could try the Hardware & Laptops section of the forum? I'm sure the most knowledgeable users on this topic are there :)

If you still need help, I can help you find some, so just post back.

Thanks,

ZabiGG

---

