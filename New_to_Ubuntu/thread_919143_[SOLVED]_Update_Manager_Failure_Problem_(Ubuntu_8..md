---
title: "[SOLVED] Update Manager Failure Problem (Ubuntu 8.04)"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by yizuman on 2008-09-13
I got a icon that shows a red down arrow with an exclamation mark in the middle, when I click on it, it brings up a Update Manager window. I then clicked on the "Install Updates" button, typed in my password and then get this error message...

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.3_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_9.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_9.3_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-dev_2.6.31.dfsg-2ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-dev_2.6.31.dfsg-2ubuntu1.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.22.3.1-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.22.3.1-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6-dev_2.3.5-1ubuntu4.8.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6-dev_2.3.5-1ubuntu4.8.04.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.5-1ubuntu4.8.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.5-1ubuntu4.8.04.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.31.dfsg-2ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.31.dfsg-2ubuntu1.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-main/compiz-fusion-plugins-main_0.7.4-0ubuntu6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-main/compiz-fusion-plugins-main_0.7.4-0ubuntu6_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

What's wrong? Why can't I update?

---

### Post by ptn107 on 2008-09-13
Update via the command line and see what happens.

```
sudo apt-get update && sudo apt-get dist-upgrade -y
```

---

### Post by yizuman on 2008-09-13
Tried it...

> Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/adnarim/ubuntu/dists/hardy/Release.gpg](http://ppa.launchpad.net/adnarim/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/adnarim/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/adnarim/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://packages.medibuntu.org/dists/feisty/Release.gpg](http://packages.medibuntu.org/dists/feisty/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://packages.medibuntu.org/dists/feisty/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/feisty/free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://packages.medibuntu.org/dists/feisty/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/feisty/non-free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  app-install-data-commercial compiz-fusion-plugins-main deskbar-applet
  libfreetype6 libfreetype6-dev libxml2 libxml2-dev libxml2-utils
  python-libxml2 sudo
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4512kB of archives.
After this operation, 32.8kB of additional disk space will be used.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main sudo 1.6.9p10-1ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main app-install-data-commercial 9.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main libxml2-dev 2.6.31.dfsg-2ubuntu1.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main libxml2 2.6.31.dfsg-2ubuntu1.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main deskbar-applet 2.22.3.1-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main libfreetype6-dev 2.3.5-1ubuntu4.8.04.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main libfreetype6 2.3.5-1ubuntu4.8.04.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main libxml2-utils 2.6.31.dfsg-2ubuntu1.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main python-libxml2 2.6.31.dfsg-2ubuntu1.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main compiz-fusion-plugins-main 0.7.4-0ubuntu6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_9.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_9.3_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-dev_2.6.31.dfsg-2ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-dev_2.6.31.dfsg-2ubuntu1.2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.22.3.1-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.22.3.1-0ubuntu1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6-dev_2.3.5-1ubuntu4.8.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6-dev_2.3.5-1ubuntu4.8.04.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.5-1ubuntu4.8.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.5-1ubuntu4.8.04.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.31.dfsg-2ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.31.dfsg-2ubuntu1.2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-main/compiz-fusion-plugins-main_0.7.4-0ubuntu6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-main/compiz-fusion-plugins-main_0.7.4-0ubuntu6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


---

### Post by yizuman on 2008-09-13
help?

---

### Post by ptn107 on 2008-09-13
post output of 
```
cat /etc/hosts
```

---

### Post by jemate18 on 2008-09-13
> **yizuman said:**
> help?

that's strange the output of you command (apt-get update) seems trying to connect not to the repositories but into your own machine (127.0.0.1)

Would you mind pasting your sources.list file?

it is located at /etc/apt/sources.list

---

### Post by yizuman on 2008-09-13
> **ptn107 said:**
> post output of 
```
cat /etc/hosts
```

> # The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Yiz

---

### Post by yizuman on 2008-09-13
> **jemate18 said:**
> that's strange the output of you command (apt-get update) seems trying to connect not to the repositories but into your own machine (127.0.0.1)

Would you mind pasting your sources.list file?

it is located at /etc/apt/sources.list

Is this it?

> # deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) hardy main

---

### Post by yizuman on 2008-09-13
help?

---

### Post by jemate18 on 2008-09-13
> **yizuman said:**
> help?

Yes. this is it.

try to uncomment this
> ## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="Red"]# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse[/COLOR]

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
[COLOR="Red"]# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner[/COLOR]

by removing the #

so it will be like this


> ## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="Red"]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse[/COLOR]

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
[COLOR="Red"]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner[/COLOR]

then run 
```
sudo apt-get update
```

---

### Post by yizuman on 2008-09-13
> **jemate18 said:**
> Yes. this is it.

try to uncomment this


by removing the #

so it will be like this




then run 
```
sudo apt-get update
```

I got this error when I clicked on "Save" on the text editor...

> **Could not save the file /etc/apt/sources.list.**

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

I may have screwed something up and I don't know what. But I am gonna guess it was "Tork" for Tor that did it? It's the only recent software that I installed last.

---

### Post by jemate18 on 2008-09-13
> **yizuman said:**
> I got this error when I clicked on "Save" on the text editor...



I may have screwed something up and I don't know what. But I am gonna guess it was "Tork" for Tor that did it? It's the only recent software that I installed last.

You should run it with rooth privileges.

If you will use gedit
```
sudo gksu gedit /etc/apt/sources.list
```
edit/uncomment and click save and exit, then type > sudo apt-get update

if you will use pico
```
sudo pico /etc/apt/sources.list
``` uncomment/and edit then type
CTRL + O for save and CTRL + X for exit, then type
> sudo apt-get update

---

### Post by yizuman on 2008-09-13
> **jemate18 said:**
> You should run it with rooth privileges.

If you will use gedit
```
sudo gksu gedit /etc/apt/sources.list
```
edit/uncomment and click save and exit, then type 

if you will use pico
```
sudo pico /etc/apt/sources.list
``` uncomment/and edit then type
CTRL + O for save and CTRL + X for exit, then type

Ok I uncommented and saved it...

then did the sudo apt-get update like you asked, the result was...

> sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/adnarim/ubuntu/dists/hardy/Release.gpg](http://ppa.launchpad.net/adnarim/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/adnarim/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/adnarim/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://packages.medibuntu.org/dists/feisty/Release.gpg](http://packages.medibuntu.org/dists/feisty/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://packages.medibuntu.org/dists/feisty/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/feisty/free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://packages.medibuntu.org/dists/feisty/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/feisty/non-free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


Now what?

---

### Post by jemate18 on 2008-09-13
OK..... make sure you back up your existing sources.list

This is MY sources.list

If you want, you can copy this and save it as you sources.list 

and then run apt-get update..

But be sure YOU have a backup of your existing so that if things get worst, you can roll back...

the difference is that, I use server PH and you use server US..



> #deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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

---

### Post by yizuman on 2008-09-13
> **jemate18 said:**
> OK..... make sure you back up your existing sources.list

This is MY sources.list

If you want, you can copy this and save it as you sources.list 

and then run apt-get update..

But be sure YOU have a backup of your existing so that if things get worst, you can roll back...

the difference is that, I use server PH and you use server US..

Ok I did just that...here's the results below...

> sudo apt-get update
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-backports/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-backports/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-backports/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_US.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://packages.medibuntu.org/dists/feisty/Release.gpg](http://packages.medibuntu.org/dists/feisty/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://packages.medibuntu.org/dists/feisty/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/feisty/free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://packages.medibuntu.org/dists/feisty/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/feisty/non-free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


Any ideas?

---

### Post by ptn107 on 2008-09-13
> 
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


You are missing some infomation from your /etc/hosts file.  For example mine reads:
```
[B]127.0.0.1 localhost
127.0.1.1 phil-desktop[/B]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

You are missing the top two lines (in bold above).  You can add them by typing or copy/pasting the following in a terminal:
```
sudo su
echo "127.0.0.1 localhost" >> /etc/hosts
echo "127.0.1.1 $HOSTNAME" >> /etc/hosts
```

Follow this by a:
```
sudo apt-get update
```
and try updating again.  Post your progress.

---

### Post by yizuman on 2008-09-13
> **ptn107 said:**
> You are missing some infomation from your /etc/hosts file.  For example mine reads:
```
[B]127.0.0.1 localhost
127.0.1.1 phil-desktop[/B]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

You are missing the top two lines (in bold above).  You can add them by typing or copy/pasting the following in a terminal:
```
sudo su
echo "127.0.0.1 localhost" >> /etc/hosts
echo "127.0.1.1 $HOSTNAME" >> /etc/hosts
```

Follow this by a:
```
sudo apt-get update
```
and try updating again.  Post your progress.

Sorry I didn't add the first two on top because I thought I wasn't supposed to for security reason....

> cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	anonymous

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.0.1 localhost
127.0.1.1 anonymous


Ok that previous post is confusing me, what is it exactly you want me to do?

---

### Post by ptn107 on 2008-09-13
You can ignore my last post.  Your /etc/hosts file is correct.

---

### Post by yizuman on 2008-09-13
> **ptn107 said:**
> You can ignore my last post.  Your /etc/hosts file is correct.
Ok what's the next step?

---

### Post by SunnyRabbiera on 2008-09-13
maybe you can try another mirror, its possible that mirror is down right now.
Under synaptic you can go to settings> repositories
you can try changing the source of where you are downloading from with the little pulldown menu at the bottom.
Try other mirrors, heck even other nations.
It might just be a server issue.

---

### Post by yizuman on 2008-09-13
> **SunnyRabbiera said:**
> maybe you can try another mirror, its possible that mirror is down right now.
Under synaptic you can go to settings> repositories
you can try changing the source of where you are downloading from with the little pulldown menu at the bottom.
Try other mirrors, heck even other nations.
It might just be a server issue.

Tried to click "Select Best Server" and got a "No suitable server found" message.

Is it possible my root access is messed up?

---

### Post by SunnyRabbiera on 2008-09-13
> **yizuman said:**
> Tried to click "Select Best Server" and got a "No suitable server found" message.

Is it possible my root access is messed up?

well maybe the best server really isnt the best server.
one time I had to take a canadian server to make my system workable.
usually its best to choose a server closest to you but with a highspeed connection international distances wont matter.
I once used a server from the UK that worked great.

---

### Post by unutbu on 2008-09-13
Perhaps go to System>Preferences>Network Proxy and select "Direct internet connection".

According to [https://answers.launchpad.net/ubuntu/+question/4834](https://answers.launchpad.net/ubuntu/+question/4834)
the error has to do with corrupt proxy settings.

---

### Post by yizuman on 2008-09-14
> **unutbu said:**
> Perhaps go to System>Preferences>Network Proxy and select "Direct internet connection".

According to [https://answers.launchpad.net/ubuntu/+question/4834](https://answers.launchpad.net/ubuntu/+question/4834)
the error has to do with corrupt proxy settings.

Yep, that it was, it was that "anon-proxy" that was the cause of the problem, when I removed it from the synaptic manager and rebooted. Then apt-get update, it worked like a charm.

Thanks a mill!

Yiz

---

### Post by marcin.kondera on 2008-09-15
> **unutbu said:**
> Perhaps go to System>Preferences>Network Proxy and select "Direct internet connection".

According to [https://answers.launchpad.net/ubuntu/+question/4834](https://answers.launchpad.net/ubuntu/+question/4834)
the error has to do with corrupt proxy settings.

That is great, but how to do that under Ubuntu Server? Under Terminal?

---

### Post by unutbu on 2008-09-15
marcin.kondera, welcome to the forums.

I think the answer depends on what proxy server is being used.

By default, no proxy server is used.
In yizuman's case, he had the anon-proxy package installed. He solved his problem by uninstalling the anon-proxy package. 

If you know what proxy server package/program is running on the Ubuntu Server, then you could either uninstall that package, or perhaps shut it off like this:

Look inside /etc/init.d for the name of the proxy server. 

If you are using anon-proxy, for example, to shut it off type```


sudo /etc/init.d/anon-proxy stop
```

Another proxy server is called squid ([http://www.debianhelp.co.uk/squid.htm](http://www.debianhelp.co.uk/squid.htm)).
If you are using squid, then you could try
```

sudo /etc/init.d/squid stop
```

To restart it, type
```

sudo /etc/init.d/squid start
```

---

### Post by CheshireMac on 2008-09-15
I know this reads as solved, but I'm having the same issue, and the solution isn't posted. Could anyone tell me what that solution was, exactly? I'm using a fresh sources list from a new install, and I'm stumped as to why I can't update. Arg and such.

---

