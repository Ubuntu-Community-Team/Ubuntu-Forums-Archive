---
title: "how to fix this error message"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-11-10
note spm says i have no broken packages
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xubuntu-desktop : Depends: thunar but it is not going to be installed
                   Depends: thunar-volman but it is not going to be installed
                   Depends: xfce4-panel but it is not going to be installed
                   Depends: xfdesktop4 but it is not going to be installed
                   Recommends: orage but it is not going to be installed
                   Recommends: thunar-archive-plugin but it is not going to be installed
                   Recommends: thunar-media-tags-plugin but it is not going to be installed
                   Recommends: xfce4-cpugraph-plugin but it is not going to be installed
                   Recommends: xfce4-dict but it is not going to be installed
                   Recommends: xfce4-indicator-plugin but it is not going to be installed
                   Recommends: xfce4-mailwatch-plugin but it is not going to be installed
                   Recommends: xfce4-netload-plugin but it is not going to be installed
                   Recommends: xfce4-notes-plugin but it is not going to be installed
                   Recommends: xfce4-places-plugin but it is not going to be installed
                   Recommends: xfce4-quicklauncher-plugin but it is not going to be installed
                   Recommends: xfce4-systemload-plugin but it is not going to be installed
                   Recommends: xfce4-terminal but it is not going to be installed
                   Recommends: xfce4-verve-plugin but it is not going to be installed
                   Recommends: xfce4-weather-plugin but it is not going to be installed
                   Recommends: xfce4-xkb-plugin but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by rburkartjo on 2012-11-10
so if i have held broken packages what would be the command to remove them and reinstall xubuntu. dont care about lost data i have backed up

---

### Post by Bashing-om on 2012-11-11
rburkartjo; Hi !

 For such an "old hand" I presume you are testing for a reason. Any way the response !
------------
oldfred's methology for restoring:
Then try ( all the # are comments do not type anything after a #)
#if not chroot use: /chroot not to be used by new users/
```
sudo -i
```#houseclean
```
apt-get autoclean
``` # only removes files that cannot be downloaded anymore (obsolete)
```
apt-get clean
```#refresh
```
apt-get update
``` #resync package index
```
apt-get upgrade
``` #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
```
apt-get dist-upgrade
``````
apt-get -f install
``````
dpkg --configure -a
```All that does is update it again.
#log-out from super user
```
exit
```[INDENT]suffice ?? <== BDQ
 
[/INDENT]

---

### Post by rburkartjo on 2012-11-12
bas tks for the help but didnt fix my problem with xubuntu but very nice of you to list those commands. tks

---

### Post by Toz on 2012-11-12
What do the following commands return?
```
apt-cache policy xubuntu-desktop
apt-cache policy thunar
```

---

### Post by rburkartjo on 2012-11-12
toz
ray@ray-GC660AA-ABA-SR5123WM:~$ apt-cache policy xubuntu-desktop
xubuntu-desktop:
  Installed: (none)
  Candidate: 2.162
  Version table:
     2.162 0
        500 [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal/universe amd64 Packages
     2.152 0
        500 [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise/universe amd64 Packages
ray@ray-GC660AA-ABA-SR5123WM:~$ 

and

ray@ray-GC660AA-ABA-SR5123WM:~$ apt-cache policy thunar
thunar:
  Installed: (none)
  Candidate: 1.4.0-1ubuntu2.1
  Version table:
     1.4.0-1ubuntu2.1 0
        500 [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-proposed/universe amd64 Packages
     1.4.0-1ubuntu2 0
        500 [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal/universe amd64 Packages
     1.2.3-3ubuntu2 0
        500 [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise/universe amd64 Packages
ray@ray-GC660AA-ABA-SR5123WM:~$

---

### Post by Toz on 2012-11-12
> **rburkartjo said:**
> toz
ray@ray-GC660AA-ABA-SR5123WM:~$ apt-cache policy xubuntu-desktop
xubuntu-desktop:
  Installed: (none)
  Candidate: 2.162
  Version table:
     2.162 0
        500 [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal/universe amd64 Packages
     2.152 0
        500 [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise/universe amd64 Packages
ray@ray-GC660AA-ABA-SR5123WM:~$ 

and

ray@ray-GC660AA-ABA-SR5123WM:~$ apt-cache policy thunar
thunar:
  Installed: (none)
  Candidate: 1.4.0-1ubuntu2.1
  Version table:
     1.4.0-1ubuntu2.1 0
        500 [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-proposed/universe amd64 Packages
     1.4.0-1ubuntu2 0
        500 [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal/universe amd64 Packages
     1.2.3-3ubuntu2 0
        500 [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise/universe amd64 Packages
ray@ray-GC660AA-ABA-SR5123WM:~$

You have both quantal (regular and proposed) and precise repositories listed. What version of Ubuntu are you actually running? 12.10 (quantal)?

If so, you might want to try removing reference to both the quantal-proposed (for now) and precise sources from your Software Sources (UbuntuSoftwareCentre->Edit->SoftwareSources).

---

### Post by rburkartjo on 2012-11-12
toz should i disable remove or purge what would be best

---

### Post by rburkartjo on 2012-11-12
yes running 12.10

---

### Post by rburkartjo on 2012-11-12
toz did that and still get the same output as previously posted also now get this error message when try to update

W:Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.team-cymru.org_ubuntu_dists_precise-proposed_main_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.team-cymru.org_ubuntu_dists_precise-proposed_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by rburkartjo on 2012-11-12
this might help here is a complete output of my sources. i like to add a bunch of things and if i have a problem in 99% of the time i can fix it myself. if i should # some the the below or delete no problem


# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal main restricted multiverse
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-updates main restricted multiverse
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal universe
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal universe
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-updates universe
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-backports main universe restricted multiverse
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-backports main universe restricted multiverse

deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-security main restricted multiverse
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-security main restricted multiverse
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-security universe
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb [http://archive.canonical.com/](http://archive.canonical.com/) quantal partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) quantal partner
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib

# deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main
# deb-src [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-proposed restricted main multiverse universe
deb [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise main universe restricted multiverse
deb-src [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security universe main multiverse restricted
deb-src [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise-security universe main multiverse restricted #Added by software-properties
deb [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise-proposed universe main multiverse restricted
deb-src [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise-proposed universe main multiverse restricted #Added by software-properties
deb [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise-updates universe main multiverse restricted
deb-src [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise-updates universe main multiverse restricted #Added by software-properties
deb [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise-backports universe main multiverse restricted
deb-src [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) precise-backports universe main multiverse restricted #Added by software-properties
deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) quantal main
deb-src [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) quantal main
deb [http://repo.mate-desktop.org/ubuntu](http://repo.mate-desktop.org/ubuntu) quantal main
deb-src [http://repo.mate-desktop.org/ubuntu](http://repo.mate-desktop.org/ubuntu) quantal main

---

### Post by rburkartjo on 2012-11-12
or would this just be easy way to fix using the link below
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)


###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

replace my source list with this
###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

---

### Post by Toz on 2012-11-12
> **rburkartjo said:**
> toz did that and still get the same output as previously posted also now get this error message when try to update

W:Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.team-cymru.org_ubuntu_dists_precise-proposed_main_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.team-cymru.org_ubuntu_dists_precise-proposed_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Try removing those partial files:
```
sudo rm -R /var/lib/apt/lists/partial/*
```
...and re-reading the lists:
```
sudo apt-get update
```
Does this take care of the error messages?

---

### Post by Bashing-om on 2012-11-12
is it time to look at the source: /etc/apt/sources.list ?
do what repairs are needed:
Then try to remove -- purge -> re-install the desktop ?

[INDENT]just think'n ==> BDQ

[/INDENT]

---

### Post by Toz on 2012-11-12
I would comment out quantal-proposed:
> deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) quantal-proposed restricted main multiverse universe
...and try again.

What do you have in /etc/apt/sources.list.d?
```
ls -l /etc/apt/sources.list.d/
```

---

### Post by rburkartjo on 2012-11-12
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.team-cymru.org_ubuntu_dists_precise-proposed_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.team-cymru.org_ubuntu_dists_precise-proposed_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
ray@ray-GC660AA-ABA-SR5123WM:~$ ls -l /etc/apt/sources.list.d/
total 780
-rw-r--r-- 1 root root 212 Nov 12 14:05 askubuntu-tools-ppa-precise.list
-rw-r--r-- 1 root root 212 Oct 13 05:47 askubuntu-tools-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 212 Nov 12 14:05 askubuntu-tools-ppa-precise.list.save
-rw-r--r-- 1 root root 134 Nov 12 14:05 atareao-atareao-quantal.list
-rw-r--r-- 1 root root 134 Nov 12 14:05 atareao-atareao-quantal.list.save
-rw-r--r-- 1 root root 136 Nov 12 14:05 atareao-lenses-precise.list
-rw-r--r-- 1 root root 136 Oct 13 05:47 atareao-lenses-precise.list.distUpgrade
-rw-r--r-- 1 root root 136 Nov 12 14:05 atareao-lenses-precise.list.save
-rw-r--r-- 1 root root 214 Nov 12 14:05 audience-members-ppa-precise.list
-rw-r--r-- 1 root root 214 Oct 13 05:47 audience-members-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 214 Nov 12 14:05 audience-members-ppa-precise.list.save
-rw-r--r-- 1 root root  98 Nov 12 14:05 banshee-team-banshee-daily-precise.list
-rw-r--r-- 1 root root  98 Oct 13 05:47 banshee-team-banshee-daily-precise.list.distUpgrade
-rw-r--r-- 1 root root  98 Nov 12 14:05 banshee-team-banshee-daily-precise.list.save
-rw-r--r-- 1 root root 220 Nov 12 14:05 caffeine-developers-ppa-precise.list
-rw-r--r-- 1 root root 220 Oct 13 05:47 caffeine-developers-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 220 Nov 12 14:05 caffeine-developers-ppa-precise.list.save
-rw-r--r-- 1 root root 105 Nov 12 14:05 chromium-daily-beta-precise.list
-rw-r--r-- 1 root root 105 Oct 13 05:47 chromium-daily-beta-precise.list.distUpgrade
-rw-r--r-- 1 root root 105 Nov 12 14:05 chromium-daily-beta-precise.list.save
-rw-r--r-- 1 root root 109 Nov 12 14:05 chromium-daily-stable-precise.list
-rw-r--r-- 1 root root 109 Oct 13 05:47 chromium-daily-stable-precise.list.distUpgrade
-rw-r--r-- 1 root root 109 Nov 12 14:05 chromium-daily-stable-precise.list.save
-rw-r--r-- 1 root root 146 Oct 28 08:14 cooperjona-stormcloud-quantal.list.save
-rw-r--r-- 1 root root 104 Nov 12 14:05 danielrichter2007-grub-customizer-precise.list
-rw-r--r-- 1 root root 104 Oct 13 05:47 danielrichter2007-grub-customizer-precise.list.distUpgrade
-rw-r--r-- 1 root root 104 Nov 12 14:05 danielrichter2007-grub-customizer-precise.list.save
-rw-r--r-- 1 root root 144 Nov 12 14:05 davidc3-books-lens-precise.list
-rw-r--r-- 1 root root 144 Oct 13 05:47 davidc3-books-lens-precise.list.distUpgrade
-rw-r--r-- 1 root root 144 Nov 12 14:05 davidc3-books-lens-precise.list.save
-rw-r--r-- 1 root root 134 Nov 12 14:05 deluge-team-ppa-precise.list
-rw-r--r-- 1 root root 134 Oct 13 05:47 deluge-team-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 134 Nov 12 14:05 deluge-team-ppa-precise.list.save
-rw-r--r-- 1 root root 202 Nov 12 14:05 diesch-testing-precise.list
-rw-r--r-- 1 root root 202 Oct 13 05:47 diesch-testing-precise.list.distUpgrade
-rw-r--r-- 1 root root 202 Nov 12 14:05 diesch-testing-precise.list.save
-rw-r--r-- 1 root root 158 Nov 12 14:05 gloobus-dev-gloobus-preview-precise.list
-rw-r--r-- 1 root root 158 Oct 13 05:47 gloobus-dev-gloobus-preview-precise.list.distUpgrade
-rw-r--r-- 1 root root 158 Nov 12 14:05 gloobus-dev-gloobus-preview-precise.list.save
-rw-r--r-- 1 root root 226 Nov 12 14:05 gnome-shell-extensions-ppa-precise.list
-rw-r--r-- 1 root root 226 Oct 13 05:47 gnome-shell-extensions-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 226 Nov 12 14:05 gnome-shell-extensions-ppa-precise.list.save
-rw-r--r-- 1 root root 176 Nov 12 14:05 google-chrome.list
-rw-r--r-- 1 root root 176 Oct 13 05:47 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 176 Nov 12 14:05 google-chrome.list.save
-rw-r--r-- 1 root root 175 Nov 12 14:05 google-earth.list
-rw-r--r-- 1 root root 177 Nov 12 14:05 google-earth.list.save
-rw-r--r-- 1 root root 111 Nov 12 14:05 gwendal-lebihan-dev-cinnamon-nightly-quantal.list
-rw-r--r-- 1 root root 111 Nov 12 14:05 gwendal-lebihan-dev-cinnamon-nightly-quantal.list.save
-rw-r--r-- 1 root root 174 Nov 12 14:05 gwendal-lebihan-dev-cinnamon-stable-quantal.list
-rw-r--r-- 1 root root 174 Nov 12 14:05 gwendal-lebihan-dev-cinnamon-stable-quantal.list.save
-rw-r--r-- 1 root root 222 Nov 12 14:05 hakermania-format-junkie-precise.list
-rw-r--r-- 1 root root 222 Oct 13 05:47 hakermania-format-junkie-precise.list.distUpgrade
-rw-r--r-- 1 root root 222 Nov 12 14:05 hakermania-format-junkie-precise.list.save
-rw-r--r-- 1 root root 170 Nov 12 14:05 hannes-janetzek-enlightenment-svn-quantal.list
-rw-r--r-- 1 root root 170 Nov 12 14:05 hannes-janetzek-enlightenment-svn-quantal.list.save
-rw-r--r-- 1 root root 188 Nov 12 14:05 jfi-ppa-precise.list
-rw-r--r-- 1 root root 188 Oct 13 05:47 jfi-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 188 Nov 12 14:05 jfi-ppa-precise.list.save
-rw-r--r-- 1 root root 224 Nov 12 14:05 kevin-mehall-pithos-daily-precise.list
-rw-r--r-- 1 root root 224 Oct 13 05:47 kevin-mehall-pithos-daily-precise.list.distUpgrade
-rw-r--r-- 1 root root 224 Nov 12 14:05 kevin-mehall-pithos-daily-precise.list.save
-rw-r--r-- 1 root root 200 Nov 12 14:05 leolik-leolik-precise.list
-rw-r--r-- 1 root root 200 Oct 13 05:47 leolik-leolik-precise.list.distUpgrade
-rw-r--r-- 1 root root 200 Nov 12 14:05 leolik-leolik-precise.list.save
-rw-r--r-- 1 root root  82 Nov 12 14:05 libreoffice-ppa-precise.list
-rw-r--r-- 1 root root  82 Oct 13 05:47 libreoffice-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  82 Nov 12 14:05 libreoffice-ppa-precise.list.save
-rw-r--r-- 1 root root 202 Nov 12 14:05 markjtully-ppa-precise.list
-rw-r--r-- 1 root root 202 Oct 13 05:47 markjtully-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 202 Nov 12 14:05 markjtully-ppa-precise.list.save
-rw-r--r-- 1 root root 222 Nov 12 14:05 marlin-devs-marlin-daily-precise.list
-rw-r--r-- 1 root root 222 Oct 13 05:47 marlin-devs-marlin-daily-precise.list.distUpgrade
-rw-r--r-- 1 root root 222 Nov 12 14:05 marlin-devs-marlin-daily-precise.list.save
-rw-r--r-- 1 root root 104 Nov 12 14:05 me-davidsansome-clementine-dev-precise.list
-rw-r--r-- 1 root root 104 Oct 13 05:47 me-davidsansome-clementine-dev-precise.list.distUpgrade
-rw-r--r-- 1 root root 104 Nov 12 14:05 me-davidsansome-clementine-dev-precise.list.save
-rw-r--r-- 1 root root 283 Nov 12 14:05 medibuntu.list
-rw-r--r-- 1 root root 349 Oct 13 05:47 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root 283 Nov 12 14:05 medibuntu.list.save
-rw-r--r-- 1 root root 101 Nov 12 14:05 mozillateam-firefox-next-precise.list
-rw-r--r-- 1 root root 101 Oct 13 05:47 mozillateam-firefox-next-precise.list.distUpgrade
-rw-r--r-- 1 root root 101 Nov 12 14:05 mozillateam-firefox-next-precise.list.save
-rw-r--r-- 1 root root 109 Nov 12 14:05 mozillateam-thunderbird-next-precise.list
-rw-r--r-- 1 root root 109 Oct 13 05:47 mozillateam-thunderbird-next-precise.list.distUpgrade
-rw-r--r-- 1 root root 109 Nov 12 14:05 mozillateam-thunderbird-next-precise.list.save
-rw-r--r-- 1 root root 196 Nov 12 14:05 mrpouit-ppa-precise.list
-rw-r--r-- 1 root root 196 Oct 13 05:47 mrpouit-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 196 Nov 12 14:05 mrpouit-ppa-precise.list.save
-rw-r--r-- 1 root root 198 Nov 12 14:05 nae-team-ppa-precise.list
-rw-r--r-- 1 root root 198 Oct 13 05:47 nae-team-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 198 Nov 12 14:05 nae-team-ppa-precise.list.save
-rw-r--r-- 1 root root 144 Nov 12 14:05 nilarimogard-webupd8-precise.list
-rw-r--r-- 1 root root 144 Oct 13 05:47 nilarimogard-webupd8-precise.list.distUpgrade
-rw-r--r-- 1 root root 144 Nov 12 14:05 nilarimogard-webupd8-precise.list.save
-rw-r--r-- 1 root root 204 Nov 12 14:05 nowrep-qupzilla-precise.list
-rw-r--r-- 1 root root 204 Oct 13 05:47 nowrep-qupzilla-precise.list.distUpgrade
-rw-r--r-- 1 root root 204 Nov 12 14:05 nowrep-qupzilla-precise.list.save
-rw-r--r-- 1 root root 146 Oct 13 05:47 opera-beta.list.distUpgrade
-rw-r--r-- 1 root root 146 Oct 13 05:46 opera-beta.list.save
-rw-r--r-- 1 root root  70 Jun  4 22:46 opera.list.save
-rw-r--r-- 1 root root  76 Nov 12 14:05 osd-lyrics-ppa-precise.list
-rw-r--r-- 1 root root  76 Oct 13 05:47 osd-lyrics-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  76 Nov 12 14:05 osd-lyrics-ppa-precise.list.save
-rw-r--r-- 1 root root  86 Nov 12 14:05 otto-kesselgulasch-gimp-precise.list
-rw-r--r-- 1 root root  86 Oct 13 05:47 otto-kesselgulasch-gimp-precise.list.distUpgrade
-rw-r--r-- 1 root root  86 Nov 12 14:05 otto-kesselgulasch-gimp-precise.list.save
-rw-r--r-- 1 root root 138 Sep 25 08:59 pcf-miro-releases-precise.list.save
-rw-r--r-- 1 root root 130 Nov 12 14:05 peterlevi-ppa-quantal.list
-rw-r--r-- 1 root root 130 Nov 12 14:05 peterlevi-ppa-quantal.list.save
-rw-r--r-- 1 root root 146 Nov 12 14:05 pydave-unity-lenses-precise.list
-rw-r--r-- 1 root root 146 Oct 13 05:47 pydave-unity-lenses-precise.list.distUpgrade
-rw-r--r-- 1 root root 146 Nov 12 14:05 pydave-unity-lenses-precise.list.save
-rw-r--r-- 1 root root 220 Nov 12 14:05 ralf_hersel-rhersel-ppa-precise.list
-rw-r--r-- 1 root root 220 Oct 13 05:47 ralf_hersel-rhersel-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 220 Nov 12 14:05 ralf_hersel-rhersel-ppa-precise.list.save
-rw-r--r-- 1 root root 198 Nov 12 14:05 razor-qt-ppa-precise.list
-rw-r--r-- 1 root root 198 Oct 13 05:47 razor-qt-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 198 Nov 12 14:05 razor-qt-ppa-precise.list.save
-rw-r--r-- 1 root root 236 Nov 12 14:05 recoll-backports-recoll-1_15-on-precise.list
-rw-r--r-- 1 root root 236 Oct 13 05:47 recoll-backports-recoll-1_15-on-precise.list.distUpgrade
-rw-r--r-- 1 root root 236 Nov 12 14:05 recoll-backports-recoll-1_15-on-precise.list.save
-rw-r--r-- 1 root root  72 Nov 12 14:05 rvm-smplayer-precise.list
-rw-r--r-- 1 root root  72 Oct 13 05:47 rvm-smplayer-precise.list.distUpgrade
-rw-r--r-- 1 root root  72 Nov 12 14:05 rvm-smplayer-precise.list.save
-rw-r--r-- 1 root root 136 Nov 12 14:05 sgringwe-beatbox-quantal.list
-rw-r--r-- 1 root root 136 Nov 12 14:05 sgringwe-beatbox-quantal.list.save
-rw-r--r-- 1 root root 218 Nov 12 14:05 silver-fox-myshortcuts-precise.list
-rw-r--r-- 1 root root 218 Oct 13 05:47 silver-fox-myshortcuts-precise.list.distUpgrade
-rw-r--r-- 1 root root 218 Nov 12 14:05 silver-fox-myshortcuts-precise.list.save
-rw-r--r-- 1 root root 154 Nov 12 14:05 stolowski-manpages-lens-precise.list
-rw-r--r-- 1 root root 154 Oct 13 05:47 stolowski-manpages-lens-precise.list.distUpgrade
-rw-r--r-- 1 root root 154 Nov 12 14:05 stolowski-manpages-lens-precise.list.save
-rw-r--r-- 1 root root  69 Nov 12 14:05 swiftfox.list
-rw-r--r-- 1 root root  69 Oct 13 05:47 swiftfox.list.distUpgrade
-rw-r--r-- 1 root root  69 Nov 12 14:05 swiftfox.list.save
-rw-r--r-- 1 root root  84 Nov 12 14:05 synapse-core-ppa-precise.list
-rw-r--r-- 1 root root  84 Oct 13 05:47 synapse-core-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  84 Nov 12 14:05 synapse-core-ppa-precise.list.save
-rw-r--r-- 1 root root 148 Nov 12 14:05 team-xbmc-ppa-precise.list
-rw-r--r-- 1 root root 146 Oct 13 05:47 team-xbmc-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 148 Nov 12 14:05 team-xbmc-ppa-precise.list.save
-rw-r--r-- 1 root root 210 Nov 12 14:05 ted-bookmarks-lens-precise.list
-rw-r--r-- 1 root root 210 Oct 13 05:47 ted-bookmarks-lens-precise.list.distUpgrade
-rw-r--r-- 1 root root 210 Nov 12 14:05 ted-bookmarks-lens-precise.list.save
-rw-r--r-- 1 root root 180 May 18 18:19 the-warl0ck-1989-xfce-appmenu-plugin-precise.list.save
-rw-r--r-- 1 root root  95 Nov 12 14:05 transmissionbt-beta-precise.list
-rw-r--r-- 1 root root  95 Oct 13 05:47 transmissionbt-beta-precise.list.distUpgrade
-rw-r--r-- 1 root root  95 Nov 12 14:05 transmissionbt-beta-precise.list.save
-rw-r--r-- 1 root root 140 Nov 12 14:05 tualatrix-personal-quantal.list
-rw-r--r-- 1 root root 140 Nov 12 14:05 tualatrix-personal-quantal.list.save
-rw-r--r-- 1 root root 178 Jul  6 00:53 tualatrix-ppa-precise.list.save
-rw-r--r-- 1 root root 121 Nov 12 14:05 ubuntu-mozilla-daily-firefox-aurora-precise.list
-rw-r--r-- 1 root root 121 Oct 13 05:47 ubuntu-mozilla-daily-firefox-aurora-precise.list.distUpgrade
-rw-r--r-- 1 root root 121 Nov 12 14:05 ubuntu-mozilla-daily-firefox-aurora-precise.list.save
-rw-r--r-- 1 root root 111 Nov 12 14:05 ubuntu-mozilla-daily-ppa-precise.list
-rw-r--r-- 1 root root 111 Oct 13 05:47 ubuntu-mozilla-daily-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 111 Nov 12 14:05 ubuntu-mozilla-daily-ppa-precise.list.save
-rw-r--r-- 1 root root 103 Nov 12 14:05 ubuntu-tweak-testing-ppa-precise.list
-rw-r--r-- 1 root root 103 Oct 13 05:47 ubuntu-tweak-testing-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 103 Nov 12 14:05 ubuntu-tweak-testing-ppa-precise.list.save
-rw-r--r-- 1 root root  87 Nov 12 14:05 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  87 Oct 13 05:47 ubuntu-wine-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  87 Nov 12 14:05 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root  84 Nov 12 14:05 ubuntu-x-swat-x-updates-precise.list
-rw-r--r-- 1 root root  84 Oct 13 05:47 ubuntu-x-swat-x-updates-precise.list.distUpgrade
-rw-r--r-- 1 root root  84 Nov 12 14:05 ubuntu-x-swat-x-updates-precise.list.save
-rw-r--r-- 1 root root 206 Nov 12 14:05 upubuntu-com-ext-precise.list
-rw-r--r-- 1 root root 206 Oct 13 05:47 upubuntu-com-ext-precise.list.distUpgrade
-rw-r--r-- 1 root root 206 Nov 12 14:05 upubuntu-com-ext-precise.list.save
-rw-r--r-- 1 root root 198 Nov 12 14:05 venerix-blug-precise.list
-rw-r--r-- 1 root root 198 Oct 13 05:47 venerix-blug-precise.list.distUpgrade
-rw-r--r-- 1 root root 198 Nov 12 14:05 venerix-blug-precise.list.save
-rw-r--r-- 1 root root 150 Nov 12 14:05 videolan-stable-daily-precise.list
-rw-r--r-- 1 root root 150 Oct 13 05:47 videolan-stable-daily-precise.list.distUpgrade
-rw-r--r-- 1 root root 150 Nov 12 14:05 videolan-stable-daily-precise.list.save
-rw-r--r-- 1 root root  99 Nov 12 14:05 weather-indicator-team-ppa-precise.list
-rw-r--r-- 1 root root  99 Oct 13 05:47 weather-indicator-team-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  99 Nov 12 14:05 weather-indicator-team-ppa-precise.list.save
-rw-r--r-- 1 root root  92 Nov 12 14:05 xorg-edgers-ppa-precise.list
-rw-r--r-- 1 root root  92 Oct 13 05:47 xorg-edgers-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  92 Nov 12 14:05 xorg-edgers-ppa-precise.list.save
-rw-r--r-- 1 root root 150 Oct 13 05:47 xubuntu-dev-xfce-4_10-precise.list.distUpgrade
-rw-r--r-- 1 root root 149 Nov  1 08:33 xubuntu-dev-xfce-4_10-precise.list.save
-rw-r--r-- 1 root root 148 Oct 23 06:59 xubuntu-dev-xfce-4_10-precise.list.save~
-rw-r--r-- 1 root root 146 Nov 12 14:05 xubuntu-dev-xfce-4_10-quantal.list
-rw-r--r-- 1 root root 146 Nov 12 14:05 xubuntu-dev-xfce-4_10-quantal.list.save
-rw-r--r-- 1 root root 150 Nov 12 14:05 xubuntu-dev-xfce-4_12-quantal.list
-rw-r--r-- 1 root root 150 Nov 12 14:05 xubuntu-dev-xfce-4_12-quantal.list.save
-rw-r--r-- 1 root root 107 Nov 12 14:05 yannubuntu-boot-repair-precise.list
-rw-r--r-- 1 root root 107 Oct 13 05:47 yannubuntu-boot-repair-precise.list.distUpgrade
-rw-r--r-- 1 root root 107 Nov 12 14:05 yannubuntu-boot-repair-precise.list.save
-rw-r--r-- 1 root root 192 Nov 12 14:05 yorba-ppa-precise.list
-rw-r--r-- 1 root root 192 Oct 13 05:47 yorba-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 192 Nov 12 14:05 yorba-ppa-precise.list.save
ray@ray-GC660AA-ABA-SR5123WM:~$

---

### Post by Toz on 2012-11-13
Wow!

First, you seem to have 32 and 64 bit PPAs intermixed:
> W: Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.team-cymru.org_ubuntu_dists_precise-proposed_main_binary-amd64_Packages Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.team-cymru.org_ubuntu_dists_precise-proposed_main_binary-i386_Packages Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
...this is generally not a good thing.

Second, you have multiple Xfce PPAs installed through an upgrade:
```
-rw-r--r-- 1 root root 150 Oct 13 05:47 xubuntu-dev-xfce-4_10-precise.list.distUpgrade
-rw-r--r-- 1 root root 149 Nov 1 08:33 xubuntu-dev-xfce-4_10-precise.list.save
-rw-r--r-- 1 root root 148 Oct 23 06:59 xubuntu-dev-xfce-4_10-precise.list.save~
-rw-r--r-- 1 root root 146 Nov 12 14:05 xubuntu-dev-xfce-4_10-quantal.list
-rw-r--r-- 1 root root 146 Nov 12 14:05 xubuntu-dev-xfce-4_10-quantal.list.save
-rw-r--r-- 1 root root 150 Nov 12 14:05 xubuntu-dev-xfce-4_12-quantal.list
-rw-r--r-- 1 root root 150 Nov 12 14:05 xubuntu-dev-xfce-4_12-quantal.list.save
```

Although I don't like suggesting this, you might want to consider backing up your important data and re-installing the version of Ubuntu that you want to run. It might be __significantly__ quicker than trying to fix these inconsistencies.

---

### Post by rburkartjo on 2012-11-14
tks toz afraid i might have to do that way too much playing. will backup my important stuff to flash drive and then do a clean install making sure i dont delete my windows partition. should go smoothly since i actually installed windows after i had linux installed. really appreciate your help. i just might wait until 13.04 comes out think this time just keep with xubuntu.

---

