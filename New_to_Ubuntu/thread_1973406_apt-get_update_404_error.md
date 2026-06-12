---
title: "apt-get update 404 error"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-04
Hi All
When I run:
```

sudo apt-get update

```most of the updates read ok, but I get the following error:
```

...
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_NZ
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_NZ
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_NZ
Ign http://ppa.launchpad.net precise/main Translation-en
Fetched 12.7 MB in 34s (366 kB/s)
W: Failed to fetch http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```Can someone please tell my update is failing to get some packages while getting others?

---

### Post by jonedney on 2012-05-04
Hello

What does your '/etc/apt/sources.list' look like?

---

### Post by Senior_Buckethead on 2012-05-04
Here is my apt sources.list
```

glenn@acer:~$ cd /etc/apt
glenn@acer:/etc/apt$ ls
apt.conf.d     sources.list   sources.list.d     trustdb.gpg  trusted.gpg~
preferences.d  sources.list~  sources.list.save  trusted.gpg  trusted.gpg.d

glenn@acer:/etc/apt$ cat sources.list
# 

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423.2)]/ precise main restricted

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423.2)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise universe
deb http://nz.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nz.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://nz.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
glenn@acer:/etc/apt$ 

```

---

### Post by Senior_Buckethead on 2012-05-05
```

glenn@acer:~$sudo apt-get update
...
Err http://ppa.launchpad.net precise/main Sources                                 
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
...
W: Failed to fetch http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
glenn@acer:~$

```
I cant find any trace of ppa.launchpad.net in my sources.list, sources.list~ or sources.list.save files. Here is the contents of my /etc/apt directory
```

glenn@acer:/etc/apt$ ls
apt.conf.d     sources.list   sources.list.d     trustdb.gpg  trusted.gpg~
preferences.d  sources.list~  sources.list.save  trusted.gpg  trusted.gpg.d
glenn@acer:/etc/apt$

```
How do I remove the launchpad references If I cant find reference to them?

---

### Post by plucky on 2012-05-05
> How do I remove the launchpad references If I cant find reference to them? 

PPAs are put in the /etc/apt/sources.list.d/ directory

From a terminal ```
cat /etc/apt/sources.list.d/*.list
```

You can also use Repository Settings in Synaptic Package Manager to remove the repository.

The 404 errors are because there is no PPA for precise on the server.

See [Here](http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/dists/)

Good Luck

---

### Post by Senior_Buckethead on 2012-05-05
Problem solved:
```

glenn@acer:/etc/apt$ cd sources.list.d
glenn@acer:/etc/apt/sources.list.d$ ls
emesene-team-emesene-stable-precise.list
google-earth.list
gwendal-lebihan-dev-cinnamon-stable-precise.list
gwendal-lebihan-dev-cinnamon-stable-precise.list.save
librecad-dev-librecad-daily-precise.list
librecad-dev-librecad-daily-precise.list.save
opera.list
opera.list.save
glenn@acer:/etc/apt/sources.list.d$ cat emesene-team-emesene-stable-precise.list 
deb http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu precise main
deb-src http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu precise main
glenn@acer:/etc/apt/sources.list.d$ sudo rm -f emesene-team-emesene-stable-precise.list
[sudo] password for glenn: 
glenn@acer:/etc/apt/sources.list.d$ ls
google-earth.list
gwendal-lebihan-dev-cinnamon-stable-precise.list
gwendal-lebihan-dev-cinnamon-stable-precise.list.save
librecad-dev-librecad-daily-precise.list
librecad-dev-librecad-daily-precise.list.save
opera.list
opera.list.save
glenn@acer:

```

Thank you for your help
Glenn

---

