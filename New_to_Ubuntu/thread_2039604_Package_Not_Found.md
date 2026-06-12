---
title: "Package Not Found"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by Keshav2050 on 2012-08-09
When I typed 'sudo apt-get update && sudo apt-get upgrade' in terminal 

'Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libfreerdp-plugins-standard libfreerdp1 software-center
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 949 kB of archives.
After this operation, 31.7 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main libfreerdp1 i386 1.0.1-1ubuntu2.1 [251 kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main libfreerdp-plugins-standard i386 1.0.1-1ubuntu2.1 [74.1 kB]
Get:3 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main software-center all 5.2.5 [624 kB]
Fetched 949 kB in 8s (117 kB/s)                                                
(Reading database ... 345595 files and directories currently installed.)
Preparing to replace libfreerdp1 1.0.1-1ubuntu2 (using .../libfreerdp1_1.0.1-1ubuntu2.1_i386.deb) ...
Unpacking replacement libfreerdp1 ...
Preparing to replace libfreerdp-plugins-standard 1.0.1-1ubuntu2 (using .../libfreerdp-plugins-standard_1.0.1-1ubuntu2.1_i386.deb) ...
Unpacking replacement libfreerdp-plugins-standard ...
Preparing to replace software-center 5.2.4 (using .../software-center_5.2.5_all.deb) ...
Unpacking replacement software-center ...
Processing triggers for lubuntu-software-center ...
Creating package database in /var/cache/lsc_packages.db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aee: package not found
[B]jlgui: package not found
keysafe: package not found
galan: package not found
live-magic: package not found
qtodo: package not found
wesnoth-1.8: package not found
easydiff.app: package not found
scenic: package not found
omaque: package not found
gtkwhiteboard: package not found
genesis: package not found
jcgui: package not found
pino: package not found
streamtuner: package not found
seamonkey: package not found
mined: package not found
qgis: package not found
pouetchess: package not found
gmameui: package not found
xdx: package not found[/B]
Creating table utils
Creating table universalaccess
Creating table audiovideo
Creating table games
Creating table graphic
Creating table network
Creating table education
Creating table scienze
Creating table system
Creating table devel
Creating table tweaks
Creating table fonts
Creating table office
Creating table packages
Done
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up libfreerdp1 (1.0.1-1ubuntu2.1) ...
Setting up libfreerdp-plugins-standard (1.0.1-1ubuntu2.1) ...
Setting up software-center (5.2.5) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place'

Why am I getting package not found can I do something?
Or can it be because 'Medibuntu(source)' is not selected in other sources of software center? Can I do anything at all?

I have also recently installed edubuntu, kubuntu, lubuntu, xubuntu to see how they work.

---

### Post by ubudog on 2012-08-11
Could you post the output of: 
```
cat /etc/apt/sources.list
```

Best,
ubudog

---

### Post by Keshav2050 on 2012-08-11
Sure, thanks for replying.

[B]# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
[/B]

---

### Post by ubudog on 2012-08-11
Did you get any errors when you ran apt-get update?

---

### Post by Keshav2050 on 2012-08-13
No, there were no errors.

---

