---
title: "Cannot install updates"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by joeedit on 2013-07-10
Hello,

I just cannot install updates via Update Manager

error message> The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details:
The following packages have unmet dependencies:

build-essential: Depends: gcc (>= 4:4.4.3) but 4:4.6.3-1ubuntu5 is installed
                 Depends: g++ (>= 4:4.4.3) but it is not installed
                 Depends: dpkg-dev (>= 1.13.5) but it is not installed
libc6: Depends: libc-bin (= 2.15-0ubuntu10.4) but 2.15-0ubuntu10.2 is installed
libc6-dev: Depends: libc6 (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.4 is installed
           Depends: libc-dev-bin (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.3 is installed


So I tried to run terminal:

> joe @ G580: ~ $ apt-get install-f
E: It was not open lock file / var / lib / dpkg / lock - open (13: Permission denied)
E: Unable to lock the administration directory (/ var / lib / dpkg /). Are you root?
joe @ G580: ~ $ sudo sh
[sudo] password for joe:
# Apt-get install-f
Reading package lists ... Done
Building dependency tree
I read state information ... Done
Correcting dependencies ... Done
The following extra packages will be installed:
   dpkg-dev fakeroot g+ + g+ + -4.6 libalgorithm-diff-perl
   libalgorithm-diff-xs-perl libalgorithm-merge-perl libc-bin libc-dev-bin
   libdpkg libc6-dev-perl libstdc + +6-4.6-dev-perl libtimedate
Suggested packages:
   debian-keyring g+ +-multilib g+ +-4.6-multilib gcc-4.6-doc libstdc + +6-4.6-dbg
   glibc-doc libstdc + +6-4.6-doc
The following NEW packages will be installed:
   dpkg-dev fakeroot g+ + g+ + -4.6 libalgorithm-diff-perl
   libalgorithm-diff-xs-perl libalgorithm-merge-perl-perl libdpkg
   libstdc + +6-4.6-dev-perl libtimedate
The following packages will be upgraded:
   libc-bin libc-dev-bin libc6-dev
3 upgraded, 10 newly installed, 0 to remove and 293 not upgraded.
9 not fully installed or removed.
Need to get 0 B/13, 7 MB of archives.
After this operation will be used to drive additional 28.8 megabytes
Do you want to continue [Y / n]? y
E: Internal Error, No file name for libc6
W: Unable to start immediate configuration package 'multiarch-support: amd64'. Refer to man 5 apt.conf in parts APT :: Immediate-Configure. (2)
E: Internal Error, No file name for libgcc1
E: Internal Error, No file name for libgcc1

I already tried to install some packages via this help:
[HTML]http://ubuntuforums.org/showthread.php?t=2050126&p=12206899#post12206899[/HTML]

So can anyone please help me to fix it? I am beginer...

THANKS!

---

### Post by dino99 on 2013-07-10
please post the output of :

> cat /etc/apt/sources.list

---

### Post by joeedit on 2013-07-10
output of "cat /etc/apt/sources.list"

> # 
cat /etc/apt/sources.list
# #deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

#deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise universe
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

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



---

### Post by joeedit on 2013-07-10
May be, that this is the problem:

UBUNTU SOFTWARE CENTER

> The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details:

The following packages have unmet dependencies:

build-essential: Depends: gcc (>= 4:4.4.3) but 4:4.6.3-1ubuntu5 is installed
                 Depends: g++ (>= 4:4.4.3) but it is not installed
                 Depends: dpkg-dev (>= 1.13.5) but it is not installed
libc6: Depends: libc-bin (= 2.15-0ubuntu10.4) but 2.15-0ubuntu10.2 is installed
libc6-dev: Depends: libc6 (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.4 is installed
           Depends: libc-dev-bin (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.3 is installed

Can you tell me how to fix it, please?

---

### Post by Cheesehead on 2013-07-10
You added a PPA or some other third-party repository.
You need to remove it.
Do you remember what you added?
Do you remember how you added it?
Do you know how to remove it?

If you do not know what you added, look in /etc/apt/sources.list.d/
Better yet, post the results of 'ls /etc/apt/sources.list.d/' here.

---

### Post by edb66083 on 2013-07-10
If the problem is broken packages, perhaps this will help --> [http://askubuntu.com/a/182872](http://askubuntu.com/a/182872) , which points back to this page --> [http://www.iasptk.com/ubuntu-fix-broken-package-best-solution](http://www.iasptk.com/ubuntu-fix-broken-package-best-solution)

I know that the command, 'sudo dpkg --configure -a', has helped me in the past.

---

### Post by joeedit on 2013-07-10
the problem seems to be fixed for now by reinstalling packages manualy one by one.

thanks to all of you!

---

