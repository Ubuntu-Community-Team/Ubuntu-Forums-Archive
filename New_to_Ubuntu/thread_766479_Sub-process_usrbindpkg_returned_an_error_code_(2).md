---
title: "Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by mokkai on 2008-04-25
mon@peek-UBUNTU-710:~$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgtkmm-2.4-1c2a: Depends: libgcc1 (>= 1:4.2.1-status at line %d: %.250s) but 1:4.2.1-5ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mon@peek-UBUNTU-710:~$

mon@peek-UBUNTU-710:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgtkmm-2.4-1c2a
The following packages will be upgraded:
  libgtkmm-2.4-1c2a
1 upgraded, 0 newly installed, 0 to remove and 109 not upgraded.
20 not fully installed or removed.
Need to get 0B/1202kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 6035 package `libgtkmm-2.4-1c2a':
 `Depends' field, reference to `libgcc1': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
mon@peek-UBUNTU-710:~$

mon@peek-UBUNTU-710:~$ sudo apt-get update
...
...
...
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                                                                      
Fetched 5731B in 14s (398B/s)                                                                                               
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
mon@peek-UBUNTU-710:~$

my version 7.10

any idea ?

---

### Post by tzulberti on 2008-04-25
Try using "sudo apt-get clean" which would force apt to download de deb package again.

---

### Post by az on 2008-04-25
You have mixed repositories.  Remove any packages that it is trying to install, remove any entries in your sources.list that are not from the same release (hardy) and then dist-upgrade your system to hardy and then try again.

---

### Post by mokkai on 2008-04-28
> **az said:**
> You have mixed repositories.  Remove any packages that it is trying to install, remove any entries in your sources.list that are not from the same release (hardy) and then dist-upgrade your system to hardy and then try again.

mon@peek-UBUNTU-710:~$ vim  /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main
# Line commented out by installer because it failed to verify:
mon@peek-UBUNTU-710:~$

after trying "sudo apt-get clean" the same error coming 

and i don't know how to Remove any packages that it is trying to install, remove any entries in your sources.list

thanks for your reply..

---

