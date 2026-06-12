---
title: "Authentication Error"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-07-04
These days every time i try to install any package, through synaptic, on Ubuntu 12.04 it says 

[B]Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.[/B]

Even update of the following packages gave this error :

compiz compiz-core compiz-gnome compiz-plugins-default compiz-plugins-main-default libdecoration0 libdrm-intel1 libdrm-nouveau1a libdrm-nouveau2 libdrm-radeon1 libdrm2 linux-generic-pae linux-headers-3.2.0-49 linux-headers-3.2.0-49-generic-pae linux-headers-generic-pae linux-image-3.2.0-49-generic-pae linux-image-generic-pae linux-libc-dev unity-greeter

It never happened earlier. What is going wrong and how can i solve it ?

---

### Post by Cheesehead on 2013-07-04
The warning usually means you have added an unsigned PPA or non-Ubuntu repository.
It means that verifying the safety and security of that repository is your problem, the Ubuntu project won't do it for you.
It means that updating from that repository (instead of the Ubuntu repos) carries a risk of breaking your system.

If you don't know what you added that may be causing the warning, then post the contents of your /etc/apt/sources.list file.

---

### Post by 3dmatrix on 2013-07-05
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130309)]/ raring main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

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

### Post by Cheesehead on 2013-07-05
Well, nothing seems unusual there, so it's not a PPA from that list....

Please use apt-get to try to upgrade (sudo apt-get update && sudo apt-get upgrade), and copy-and-paste the entire session here. Context of the message can give us some good clues.

---

### Post by dannyboy79 on 2013-07-05
please show us the contents of your  /etc/apt/sources.list.d/ directory by issuing
```
ls -la  /etc/apt/sources.list.d/
```

---

### Post by 3dmatrix on 2013-07-05
> **dannyboy79 said:**
> please show us the contents of your  /etc/apt/sources.list.d/ directory by issuing
```
ls -la  /etc/apt/sources.list.d/
```


ls -la  /etc/apt/sources.list.d/
total 16
drwxr-xr-x 2 root root 4096 Mar 10 07:24 .
drwxr-xr-x 6 root root 4096 Apr  5 13:03 ..
-rw-r--r-- 1 root root  416 Mar 10 07:24 opera.list
-rw-r--r-- 1 root root  416 Mar 10 07:24 opera.list.save

---

### Post by dannyboy79 on 2013-07-05
ok, and now what are the contents of that opera file?
```
cat /etc/apt/sources.list.d/opera.list
```

i am guessing that's why you're getting the confirm of authentification, because you installed a PPA to get opera web browser installed in your Ubuntu.

---

### Post by 3dmatrix on 2013-07-06
> **Cheesehead said:**
> Well, nothing seems unusual there, so it's not a PPA.

Please use apt-get to try to upgrade (sudo apt-get update && sudo apt-get upgrade), and copy-and-paste the entire session here. Context of the message can give us some good clues.

with Update and Upgrade there was no error message.
Is the problem solved ?
How do i check ?

---

