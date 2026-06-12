---
title: "[SOLVED] All installations failing!"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Java Geek on 2008-08-11
Every time i run synaptic, apt-get, or add/remove programs, i get the following...

This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

I have followed the instructions with chown and everything it just doesn't work!

---

### Post by rockerphil on 2008-08-11
ok, the first thing that pops to mind is to run this:

sudo apt-get update

also could you please post the content of your /etc/apt/sources.list file?

Phil

---

### Post by Java Geek on 2008-08-11
sudo apt-get update yields this, which gives me my first message.

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

/etc/apt/sources.list

deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Crafty Kisses on 2008-08-11
Then run:
```
sudo dpkg --configure -a
```

---

### Post by mc4100 on 2008-08-11
When you run,
```
sudo dpkg --configure -a
```
do you get the same message as in your first post?

---

### Post by Java Geek on 2008-08-11
> **mc4100 said:**
> When you run,
```
sudo dpkg --configure -a
```
do you get the same message as in your first post?

yes

---

### Post by Java Geek on 2008-08-11
aha i finally got synaptic up and running and found the cause: sun-java6-doc is installed. Its description matches that of the first post

---

### Post by rockerphil on 2008-08-11
are you behind any proxies? i had a brain fart moment a while back where i had misconfigured anon-proxy and it wouldn't allow me to install anything since my machine was basically looping and trying to connect locally

---

### Post by Java Geek on 2008-08-11
> **rockerphil said:**
> are you behind any proxies? i had a brain fart moment a while back where i had misconfigured anon-proxy and it wouldn't allow me to install anything since my machine was basically looping and trying to connect locally

no i don't think so.. I think i found the problem, I keep you posted

---

### Post by rockerphil on 2008-08-11
cool, just remember that if you've solved your problem to mark the thread as solved.

Phil

---

### Post by Java Geek on 2008-08-11
> **rockerphil said:**
> cool, just remember that if you've solved your problem to mark the thread as solved.

Phil
 umm how...*embarrased* ive been wondering how. I am SOLVED

---

### Post by Java Geek on 2008-08-11
nmd

---

