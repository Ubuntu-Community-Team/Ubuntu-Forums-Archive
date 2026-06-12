---
title: "Problem with gnome-icon-theme-full upgrade"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by Cristobal:gallardo on 2012-07-28
Hello everyone!

Yesterday I updated my Ubuntu 12.04 but suddenly, while I was installing the updates, it appeared this problem:


The following packages have unmet dependencies:

gnome-icon-theme-full: Depends: gnome-icon-theme (= 3.4.0-0ubuntu1.1) but 3.4.0-0ubuntu1 is installed

After this, each time that I start Ubuntu, it appear an error notification



At the same time, when I try to install any sofware from the Ubuntu Center Software, the system doesn't let me do it, and invite me to repare the package, but after trying it, it shows me this message:

installArchives() failed: dpkg: dependency problems prevent configuration of gnome-icon-theme: 
 gnome-icon-theme-full (3.4.0-0ubuntu1.1) breaks gnome-icon-theme (<< 3.4.0-0ubuntu1.1) and is unpacked but not configured. 
  Version of gnome-icon-theme to be configured is 3.4.0-0ubuntu1. 
dpkg: error processing gnome-icon-theme (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of gnome-icon-theme-full: 
 gnome-icon-theme-full depends on gnome-icon-theme (= 3.4.0-0ubuntu1.1); however: 
  Version of gnome-icon-theme on system is 3.4.0-0ubuntu1. 
dpkg: error processing gnome-icon-theme-full (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgtkhtml-4.0-common: 
 libgtkhtml-4.0-common depends on gnome-icon-theme (>= 2.22.0); however: 
No apport report written because MaxReports is reached already
  Package gnome-icon-theme is not configured yet. 
dpkg: error processing libgtkhtml-4.0-common (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgtkhtml-4.0-0: 
 libgtkhtml-4.0-0 depends on libgtkhtml-4.0-common (= 4.2.2-1ubuntu1.2); however: 
  Package libgtkhtml-4.0-common is not configured yet. 
dpkg: error processing libgtkhtml-4.0-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgtkhtml-editor-4.0-0: 
 libgtkhtml-editor-4.0-0 depends on libgtkhtml-4.0-0 (= 4.2.2-1ubuntu1.2); however: 
  Package libgtkhtml-4.0-0 is not configured yet. 
 libgtkhtml-editor-4.0-0 depends on libgtkhtml-4.0-common (= 4.2.2-1ubuntu1.2); however: 
  Package libgtkhtml-4.0-common is not configured yet. 
dpkg: error processing libgtkhtml-editor-4.0-0 (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 gnome-icon-theme 
 gnome-icon-theme-full 
 libgtkhtml-4.0-common 
 libgtkhtml-4.0-0 
 libgtkhtml-editor-4.0-0 
Error in function:  
dpkg: dependency problems prevent configuration of gnome-icon-theme: 
 gnome-icon-theme-full (3.4.0-0ubuntu1.1) breaks gnome-icon-theme (<< 3.4.0-0ubuntu1.1) and is unpacked but not configured. 
  Version of gnome-icon-theme to be configured is 3.4.0-0ubuntu1. 
dpkg: error processing gnome-icon-theme (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-icon-theme-full: 
 gnome-icon-theme-full depends on gnome-icon-theme (= 3.4.0-0ubuntu1.1); however: 
  Version of gnome-icon-theme on system is 3.4.0-0ubuntu1. 
dpkg: error processing gnome-icon-theme-full (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgtkhtml-4.0-common: 
 libgtkhtml-4.0-common depends on gnome-icon-theme (>= 2.22.0); however: 
  Package gnome-icon-theme is not configured yet. 
dpkg: error processing libgtkhtml-4.0-common (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgtkhtml-4.0-0: 
 libgtkhtml-4.0-0 depends on libgtkhtml-4.0-common (= 4.2.2-1ubuntu1.2); however: 
  Package libgtkhtml-4.0-common is not configured yet. 
dpkg: error processing libgtkhtml-4.0-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgtkhtml-editor-4.0-0: 
 libgtkhtml-editor-4.0-0 depends on libgtkhtml-4.0-0 (= 4.2.2-1ubuntu1.2); however: 
  Package libgtkhtml-4.0-0 is not configured yet. 
 libgtkhtml-editor-4.0-0 depends on libgtkhtml-4.0-common (= 4.2.2-1ubuntu1.2); however: 
  Package libgtkhtml-4.0-common is not configured yet. 
dpkg: error processing libgtkhtml-editor-4.0-0 (--configure): 
 dependency problems - leaving unconfigured



Thank you so much!

---

### Post by NikTh on 2012-07-28
Hi  , 
please open a terminal and give the output of ```
ls /etc/apt/sources.list.d/ 
cat /etc/apt/sources.list
```

**Put the results inside [CODE] tags , by highlighting the text and click # symbol on top of message pane.**

Thanks

---

### Post by Cristobal:gallardo on 2012-07-28
I have just done it:

cristobal@cristobal-R540-R580-R780-SA41-E452-E852:~$ ls /etc/apt/sources.list.d/ 
google-earth.list                          precise-partner.list.save
google-earth.list.save                     ubun-tor-ppa-precise.list
otto-kesselgulasch-gimp-precise.list       ubun-tor-ppa-precise.list.save
otto-kesselgulasch-gimp-precise.list.save  voria-ppa-precise.list
precise-partner.list                       voria-ppa-precise.list.save


cristobal@cristobal-R540-R580-R780-SA41-E452-E852:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by NikTh on 2012-07-28
Hi , 
open a terminal and run 
```
gksudo software-properties-gtk
```
when window opens , go to "updates" an UN-Tick "(precise-proposed)" . Close window , and go to terminal again and do ```
sudo apt-get update 
sudo apt-get dist-upgrade
```
Thanks

---

### Post by Cristobal:gallardo on 2012-08-09
Sorry for responsing too late;

I did it, and this is the response:

cristobal@cristobal-R540-R580-R780-SA41-E452-E852:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gnome-icon-theme-full : Depends: gnome-icon-theme (= 3.4.0-0ubuntu1.1) but 3.4.0-0ubuntu1 is installed
                         Breaks: gnome-icon-theme (< 3.4.0-0ubuntu1.1) but 3.4.0-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.
cristobal@cristobal-R540-R580-R780-SA41-E452-E852:~$


And after running the command "apt-get -f install", this is the response:

cristobal@cristobal-R540-R580-R780-SA41-E452-E852:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  torsocks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-icon-theme
The following packages will be upgraded:
  gnome-icon-theme
1 upgraded, 0 newly installed, 0 to remove and 94 not upgraded.
5 not fully installed or removed.
Need to get 0 B/659 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of gnome-icon-theme:
 gnome-icon-theme-full (3.4.0-0ubuntu1.1) breaks gnome-icon-theme (<< 3.4.0-0ubuntu1.1) and is unpacked but not configured.
  Version of gnome-icon-theme to be configured is 3.4.0-0ubuntu1.
dpkg: error processing gnome-icon-theme (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of gnome-icon-theme-full:
 gnome-icon-theme-full depends on gnome-icon-theme (= 3.4.0-0ubuntu1.1); however:
  Version of gnome-icon-theme on system is 3.4.0-0ubuntu1.
dpkg: error processing gnome-icon-theme-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml-4.0-common:
 libgtkhtml-4.0-common depends on gnome-icon-theme (>= 2.22.0); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing libgtkhtml-4.0-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml-4.0-0:
 libgtkhtml-4.0-0 depends on libgtkhtml-4.0-common (= 4.2.2-1ubuntu1.2); however:
  Package libgtkhtml-4.0-common is not configured yet.
dpkg: error processing libgtkhtml-4.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml-editor-4.0-0:
 libgtkNo apport report written because the error message indicates its a followup error from a previous failure.
                                 No apport report written because the error message indicates its a followup error from a previous failure.
                                                           No apport report written because the error message indicates its a followup error from a previous failure.
     No apport report written because the error message indicates its a followup error from a previous failure.
                               html-editor-4.0-0 depends on libgtkhtml-4.0-0 (= 4.2.2-1ubuntu1.2); however:
  Package libgtkhtml-4.0-0 is not configured yet.
 libgtkhtml-editor-4.0-0 depends on libgtkhtml-4.0-common (= 4.2.2-1ubuntu1.2); however:
  Package libgtkhtml-4.0-common is not configured yet.
dpkg: error processing libgtkhtml-editor-4.0-0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-icon-theme
 gnome-icon-theme-full
 libgtkhtml-4.0-common
 libgtkhtml-4.0-0
 libgtkhtml-editor-4.0-0
E: Sub-process /usr/bin/dpkg returned an error code (1)
cristobal@cristobal-R540-R580-R780-SA41-E452-E852:~$

---

