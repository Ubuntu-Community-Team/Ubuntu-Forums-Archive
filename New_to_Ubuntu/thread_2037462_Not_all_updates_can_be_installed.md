---
title: "Not all updates can be installed?"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by d4m1r on 2012-08-04
Hey guys, so Update Manager is showing I have several updates to do but along with the usual window, I get another one saying "Not all updates can be installed" :confused:

Looks like the majority of the updates are already selected but some aren't, nor can I select them manually. Specifcally, it seems it does not want to update VLC and nautilus even though (as shown below) I have now outdated versions installed.

Nautilus:
Installed version: 1:3.4.2-0ubuntu3
Available version: 1:3.4.2-0ubuntu4

VLC
Installed version: 2.0.1-4
Available version: 2.0.3-0ubuntu0.12.04.1

[IMG]http://i47.tinypic.com/suvakg.png[/IMG]


I have never seen this message before so why is it giving it to me now and what are my options?

---

### Post by snafu006 on 2012-08-04
Post the Spec of your computer and the ppa you have installed to do that it is in software
source. need more info to help you.

---

### Post by snafu006 on 2012-08-04
> **snafu006 said:**
> Post the Spec of your computer and the ppa you have installed to do that it is in software
source. need more info to help you.

NVM i see your system try disabling some ppa go back  to default ppa's

---

### Post by Bufeu on 2012-08-04
What version of Ubuntu do you have?

---

### Post by d4m1r on 2012-08-04
Using Ubuntu 12.04 LTS (x64) and below is my sources.list file:

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

Any other files/info you guys need?

---

### Post by d4m1r on 2012-08-05
Any suggestions on how to proceed? :confused:

---

### Post by NikTh on 2012-08-05
Hi , 
yes we need little more info . 

Open a terminal and post the output of 
```
sudo apt-get update 
sudo apt-get dist-upgrade
ls /etc/apt/sources.list.d/
```
also run in terminal below command 
```
gksudo software-properties-gtk
``` 
and look at "Updates" and tell us if "precise-proposed" are enabled.
Thanks

---

### Post by d4m1r on 2012-08-05
```

damir@damir-ubuntu:~$ ls /etc/apt/sources.list.d/
emesene-team-emesene-stable-precise.list
emesene-team-emesene-stable-precise.list.save
google-talkplugin.list
google-talkplugin.list.save
jd-team-jdownloader-precise.list
jd-team-jdownloader-precise.list.save
jfi-ppa-precise.list
jfi-ppa-precise.list.save
leolik-leolik-precise.list
leolik-leolik-precise.list.save
narfss-proyectobs-precise.list
narfss-proyectobs-precise.list.save
nilarimogard-webupd8-precise.list
nilarimogard-webupd8-precise.list.save
pinta-maintainers-pinta-stable-precise.list
pinta-maintainers-pinta-stable-precise.list.save
pmcenery-ppa-precise.list
pmcenery-ppa-precise.list.save
skype.list
skype.list.save
tikhonov-misc-precise.list
tikhonov-misc-precise.list.save
tualatrix-ppa-precise.list
tualatrix-ppa-precise.list.save
venerix-blug-precise.list
venerix-blug-precise.list.save
webupd8team-gnome3-precise.list
webupd8team-gnome3-precise.list.save
webupd8team-java-precise.list
webupd8team-java-precise.list.save
webupd8team-y-ppa-manager-precise.list
webupd8team-y-ppa-manager-precise.list.save

```

And no, precise-proposed is not checked (I don't want pre-official release stuff).

---

### Post by NikTh on 2012-08-05
Hi , 
you didn't run these commands 
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Thanks

---

### Post by d4m1r on 2012-08-05
Because I thought they would go ahead with the upgrades but then I remembered I could abort :tongue: Sorry and thanks for the response!

```
damir@damir-ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  nautiluspatch
The following NEW packages will be installed:
  libcrystalhd3
The following packages will be upgraded:
  accountsservice gir1.2-accountsservice-1.0 gir1.2-gudev-1.0 initscripts
  libaccountsservice0 libcups2 libcups2:i386 libcupsimage2 libcupsimage2:i386
  libgudev-1.0-0 libgudev-1.0-0:i386 libldap-2.4-2 libldap-2.4-2:i386
  libnautilus-extension1a libudev0 libudev0:i386 libvlc5 libvlccore5 nautilus
  nautilus-data resolvconf sysv-rc sysvinit-utils udev vlc vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse
29 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 16.2 MB of archives.
After this operation, 2,732 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by NikTh on 2012-08-05
Hi , 
don't you want the updates ? I don't understand. Sorry. 

Sometimes Update manager(GUI) cannot handle correct the updates-upgrades. At this situation is good to run apt-get from terminal , and see detailed errors. Maybe apt-get will handle successfully the updates and your problem will be solved just as simple. 

Try to accept the updates and see if any errors occur. 

If you want to see what dist-upgrade does , then open a terminal and ```
man apt-get
```and search for **dist-upgrade** to read. 

Thanks

---

### Post by d4m1r on 2012-08-05
Thanks for the info! Went ahead with the updates so looks like the issue is resolved...

---

