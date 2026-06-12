---
title: "Failed to download repository information"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by cressrt2 on 2013-12-31
Hi,
I have an issue with updates, I have looked at all similar threads ans actioned where it seemed similar, but to no avail. I get the following message that appears to be linked to an old package I no longer use. It is not showing in the Software Sources and I can see no sign of any old files. Any suggestions?


```
W:Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/master-pdf-editor/ubuntu/dists/precise/main/binary-i386/Packages  
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by claracc on 2013-12-31
Could you please post the contents of your sources.list file?

The sources.list file is in /etc/apt/

---

### Post by cressrt2 on 2013-12-31
I believe this is it.

```
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

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
```

I just saw tha there was a folder called /etc/apt/sources.list.d, which when I looked in had 2 files referencing the PDF Editor, I have now deleted and all is OK again.
Many thanks for pointing the right direction.

---

### Post by claracc on 2013-12-31
You are welcome. 

Glad you got fixed your problem

---

