---
title: "libplymouth2 error"
date: 2018-05-29
forum: New to Ubuntu
---

### Post by rburkartjo on 2018-05-29
running 18.04. any idea how to fix

The following packages will be upgraded:
  libplymouth2
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 76.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) trusty-updates/main amd64 libplymouth2 amd64 0.8.8-0ubuntu17.2 [76.6 kB]
Fetched 76.6 kB in 1s (152 kB/s)      
Reading changelogs... Done
(Reading database ... 512575 files and directories currently installed.)
Preparing to unpack .../libplymouth2_0.8.8-0ubuntu17.2_amd64.deb ...
Unpacking libplymouth2:amd64 (0.8.8-0ubuntu17.2) over (0.8.8-0ubuntu17.1) ...
dpkg: error processing archive /var/cache/apt/archives/libplymouth2_0.8.8-0ubuntu17.2_amd64.deb (--unpack):
 trying to overwrite '/usr/share/apport/package-hooks/source_plymouth.py', which is also in package plymouth 0.9.3-1ubuntu7
Errors were encountered while processing:
 /var/cache/apt/archives/libplymouth2_0.8.8-0ubuntu17.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ray@nightmare:~$ 

/tks

---

### Post by #&amp;thj^% on 2018-05-29
This has been a problem since 16.04 Bug: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1531070](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1531070)
give this a try then:
```

sudo dpkg -i --force-overwrite libplymouth2_0.8.8-0ubuntu17.1_amd64.deb
```

Followed by:
```
sudo apt-get -f install
```

---

### Post by rburkartjo on 2018-05-30
1fallen no luck
and did notice from research that this is an ongoing issue

ray@nightmare:~$ sudo dpkg -i --force-overwrite libplymouth2_0.8.8-0ubuntu17.1_amd64.deb
[sudo] password for ray: 
dpkg: error: cannot access archive 'libplymouth2_0.8.8-0ubuntu17.1_amd64.deb': No such file or directory


also tried to do force override install from spm and no luck

---

### Post by #&amp;thj^% on 2018-05-30
This I just now seen " Get:1 [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/)**ubuntu trusty-updates**/main amd64 libplymouth2 amd64 0.8.8-0ubuntu17.2 [76.6 kB]"
So is this a clean install or an upgraded from trusty to bionic?
Might be worth looking into you sources and/or PPA's
what dose this show:
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```
Please help me out and use Code Tags for this or even [https://paste.ubuntu.com/](https://paste.ubuntu.com/).
Thanks. :)

---

### Post by rburkartjo on 2018-05-30
it was an upgrade
here is output

ray@nightmare:~$ 
ray@nightmare:~$ grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*grep 
/etc/apt/sources.list:# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic restricted main multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates restricted main multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security restricted main multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security universe
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Ubuntu's
/etc/apt/sources.list:## 'extras' repository.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports universe restricted main multiverse
/etc/apt/sources.list:# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-proposed multiverse restricted universe main #Added by software-propertiesNot for humans during development stage of release yakkety
/etc/apt/sources.list:deb [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main # disabled on upgrade to zesty
/etc/apt/sources.list:# deb-src [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed universe restricted main multiverse #Not for humans during development stage of release bionic
/etc/apt/sources.list:# deb [arch=amd64] [https://downloads.iridiumbrowser.de/deb/](https://downloads.iridiumbrowser.de/deb/) stable main
/etc/apt/sources.list:# deb-src [https://downloads.iridiumbrowser.de/deb/](https://downloads.iridiumbrowser.de/deb/) stable main
/etc/apt/sources.list:# deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main
/etc/apt/sources.list:# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main
/etc/apt/sources.list:# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main
/etc/apt/sources.list:# deb [http://dl.winehq.org/wine-builds/ubuntu/](http://dl.winehq.org/wine-builds/ubuntu/) xenial main
/etc/apt/sources.list:# deb-src [http://dl.winehq.org/wine-builds/ubuntu/](http://dl.winehq.org/wine-builds/ubuntu/) xenial main
grep: /etc/apt/sources.list.d/*grep: No such file or directory
ray@nightmare:~$

---

### Post by #&amp;thj^% on 2018-05-30
Well I see a few problems that could/would confuse the package-manager
Try to remove these:
```
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb http://security.ubuntu.com/ubuntu trusty-security main restricted
# deb http://dl.winehq.org/wine-builds/ubuntu/ xenial main
# deb-src http://dl.winehq.org/wine-builds/ubuntu/ xenial main
# deb-src http://archive.ubuntu.com/ubuntu yakkety-proposed multiverse restricted universe main
```
And use:
```
sudo apt autoremove
sudo apt clean
sudo apt update
sudo apt -f install
```
Then we can see what else needs our attention.

---

### Post by rburkartjo on 2018-05-30
1fallen that seems to have solved the problem./tks

---

### Post by #&amp;thj^% on 2018-05-30
Great! :) Glad to be of help.

---

